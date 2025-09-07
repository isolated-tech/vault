---
title: "Agents"
source: "https://openai.github.io/openai-agents-js/guides/agents/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "Learn more about how to define agents in the OpenAI Agents SDK for JavaScript / TypeScript"
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/guides/agents/#_top)

Agents are the main building‑block of the OpenAI Agents SDK. An **Agent** is a Large Language Model (LLM) that has been configured with:

- **Instructions** – the system prompt that tells the model *who it is* and *how it should respond*.
- **Model** – which OpenAI model to call, plus any optional model tuning parameters.
- **Tools** – a list of functions or APIs the LLM can invoke to accomplish a task.

```typescript
import { Agent } from '@openai/agents';

const agent = new Agent({
  name: 'Haiku Agent',
  instructions: 'Always respond in haiku form.',
  model: 'o4-mini', // optional – falls back to the default model
});
```

The rest of this page walks through every Agent feature in more detail.

---

The `Agent` constructor takes a single configuration object. The most commonly‑used properties are shown below.

| Property        | Required | Description                                                                                                                                         |
| --------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`          | yes      | A short human‑readable identifier.                                                                                                                  |
| `instructions`  | yes      | System prompt (string **or** function – see [Dynamic instructions](https://openai.github.io/openai-agents-js/guides/agents/#dynamic-instructions)). |
| `model`         | no       | Model name **or** a custom [`Model`](https://openai.github.io/openai-agents-js/openai/agents/interfaces/model/) implementation.                     |
| `modelSettings` | no       | Tuning parameters (temperature, top\_p, etc.).                                                                                                      |
| `tools`         | no       | Array of [`Tool`](https://openai.github.io/openai-agents-js/openai/agents/type-aliases/tool/) instances the model can call.                         |

```typescript
import { Agent, tool } from '@openai/agents';
import { z } from 'zod';

const getWeather = tool({
  name: 'get_weather',
  description: 'Return the weather for a given city.',
  parameters: z.object({ city: z.string() }),
  async execute({ city }) {
    return \`The weather in ${city} is sunny.\`;
  },
});

const agent = new Agent({
  name: 'Weather bot',
  instructions: 'You are a helpful weather bot.',
  model: 'o4-mini',
  tools: [getWeather],
});
```

---

Agents are **generic on their context type** – i.e. `Agent<TContext, TOutput>`. The *context* is a dependency‑injection object that you create and pass to `Runner.run()`. It is forwarded to every tool, guardrail, handoff, etc. and is useful for storing state or providing shared services (database connections, user metadata, feature flags, …).

```typescript
import { Agent } from '@openai/agents';

interface Purchase {
  id: string;
  uid: string;
  deliveryStatus: string;
}
interface UserContext {
  uid: string;
  isProUser: boolean;

  // this function can be used within tools
  fetchPurchases(): Promise<Purchase[]>;
}

const agent = new Agent<UserContext>({
  name: 'Personal shopper',
  instructions: 'Recommend products the user will love.',
});

// Later
import { run } from '@openai/agents';

const result = await run(agent, 'Find me a new pair of running shoes', {
  context: { uid: 'abc', isProUser: true, fetchPurchases: async () => [] },
});
```

---

By default, an Agent returns **plain text** (`string`). If you want the model to return a structured object you can specify the `outputType` property. The SDK accepts:

1. A [Zod](https://github.com/colinhacks/zod) schema (`z.object({...})`).
2. Any JSON‑schema‑compatible object.

```typescript
import { Agent } from '@openai/agents';
import { z } from 'zod';

const CalendarEvent = z.object({
  name: z.string(),
  date: z.string(),
  participants: z.array(z.string()),
});

const extractor = new Agent({
  name: 'Calendar extractor',
  instructions: 'Extract calendar events from the supplied text.',
  outputType: CalendarEvent,
});
```

When `outputType` is provided, the SDK automatically uses [structured outputs](https://platform.openai.com/docs/guides/structured-outputs) instead of plain text.

---

An Agent can **delegate** to other Agents via the `handoffs` property. A common pattern is to use a *triage agent* that routes the conversation to a more specialised sub‑agent.

```typescript
import { Agent } from '@openai/agents';

const bookingAgent = new Agent({
  name: 'Booking Agent',
  instructions: 'Help users with booking requests.',
});

const refundAgent = new Agent({
  name: 'Refund Agent',
  instructions: 'Process refund requests politely and efficiently.',
});

// Use Agent.create method to ensure the finalOutput type considers handoffs
const triageAgent = Agent.create({
  name: 'Triage Agent',
  instructions: [
    'Help the user with their questions.',
    'If the user asks about booking, hand off to the booking agent.',
    'If the user asks about refunds, hand off to the refund agent.',
  ].join('\n'),
  handoffs: [bookingAgent, refundAgent],
});
```

You can read more about this pattern in the [handoffs guide](https://openai.github.io/openai-agents-js/guides/handoffs).

---

`instructions` can be a **function** instead of a string. The function receives the current `RunContext` and the Agent instance and can return a string *or* a `Promise<string>`.

```typescript
import { Agent, RunContext } from '@openai/agents';

interface UserContext {
  name: string;
}

function buildInstructions(runContext: RunContext<UserContext>) {
  return \`The user's name is ${runContext.context.name}.  Be extra friendly!\`;
}

const agent = new Agent<UserContext>({
  name: 'Personalized helper',
  instructions: buildInstructions,
});
```

Both synchronous and `async` functions are supported.

---

For advanced use‑cases you can observe the Agent lifecycle by listening on events

```typescript
import { Agent } from '@openai/agents';

const agent = new Agent({
  name: 'Verbose agent',
  instructions: 'Explain things thoroughly.',
});

agent.on('agent_start', (ctx, agent) => {
  console.log(\`[${agent.name}] started\`);
});
agent.on('agent_end', (ctx, output) => {
  console.log(\`[agent] produced:\`, output);
});
```

---

Guardrails allow you to validate or transform user input and agent output. They are configured via the `inputGuardrails` and `outputGuardrails` arrays. See the [guardrails guide](https://openai.github.io/openai-agents-js/guides/guardrails) for details.

---

Need a slightly modified version of an existing agent? Use the `clone()` method, which returns an entirely new `Agent` instance.

```typescript
import { Agent } from '@openai/agents';

const pirateAgent = new Agent({
  name: 'Pirate',
  instructions: 'Respond like a pirate – lots of “Arrr!”',
  model: 'o4-mini',
});

const robotAgent = pirateAgent.clone({
  name: 'Robot',
  instructions: 'Respond like a robot – be precise and factual.',
});
```

---

Supplying tools doesn’t guarantee the LLM will call one. You can **force** tool use with `modelSettings.tool_choice`:

1. `'auto'` (default) – the LLM decides whether to use a tool.
2. `'required'` – the LLM *must* call a tool (it can choose which one).
3. `'none'` – the LLM must **not** call a tool.
4. A specific tool name, e.g. `'calculator'` – the LLM must call that particular tool.

```typescript
import { Agent, tool } from '@openai/agents';
import { z } from 'zod';

const calculatorTool = tool({
  name: 'Calculator',
  description: 'Use this tool to answer questions about math problems.',
  parameters: z.object({ question: z.string() }),
  execute: async (input) => {
    throw new Error('TODO: implement this');
  },
});

const agent = new Agent({
  name: 'Strict tool user',
  instructions: 'Always answer using the calculator tool.',
  tools: [calculatorTool],
  modelSettings: { toolChoice: 'auto' },
});
```

After a tool call the SDK automatically resets `tool_choice` back to `'auto'`. This prevents the model from entering an infinite loop where it repeatedly tries to call the tool. You can override this behavior via the `resetToolChoice` flag or by configuring `toolUseBehavior`:

- `'run_llm_again'` (default) – run the LLM again with the tool result.
- `'stop_on_first_tool'` – treat the first tool result as the final answer.
- `{ stopAtToolNames: ['my_tool'] }` – stop when any of the listed tools is called.
- `(context, toolResults) => ...` – custom function returning whether the run should finish.

```typescript
const agent = new Agent({
  ...,
  toolUseBehavior: 'stop_on_first_tool',
});
```

---

- Learn how to [run agents](https://openai.github.io/openai-agents-js/guides/running-agents).
- Dive into [tools](https://openai.github.io/openai-agents-js/guides/tools), [guardrails](https://openai.github.io/openai-agents-js/guides/guardrails), and [models](https://openai.github.io/openai-agents-js/guides/models).
- Explore the full TypeDoc reference under **@openai/agents** in the sidebar.