---
title: "Running agents"
source: "https://openai.github.io/openai-agents-js/guides/running-agents/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "Configure and execute agent workflows with the Runner class"
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/guides/running-agents/#_top)

Agents do nothing by themselves – you **run** them with the `Runner` class or the `run()` utility.

```typescript
import { Agent, run } from '@openai/agents';

const agent = new Agent({
  name: 'Assistant',
  instructions: 'You are a helpful assistant',
});

const result = await run(
  agent,
  'Write a haiku about recursion in programming.',
);
console.log(result.finalOutput);

// Code within the code,
// Functions calling themselves,
// Infinite loop's dance.
```

When you don’t need a custom runner, you can also use the `run()` utility, which runs a singleton default `Runner` instance.

Alternatively, you can create your own runner instance:

```typescript
import { Agent, Runner } from '@openai/agents';

const agent = new Agent({
  name: 'Assistant',
  instructions: 'You are a helpful assistant',
});

// You can pass custom configuration to the runner
const runner = new Runner();

const result = await runner.run(
  agent,
  'Write a haiku about recursion in programming.',
);
console.log(result.finalOutput);

// Code within the code,
// Functions calling themselves,
// Infinite loop's dance.
```

After running your agent, you will receive a [result](https://openai.github.io/openai-agents-js/guides/results) object that contains the final output and the full history of the run.

When you use the run method in Runner, you pass in a starting agent and input. The input can either be a string (which is considered a user message), or a list of input items, which are the items in the OpenAI Responses API.

The runner then runs a loop:

1. Call the current agent’s model with the current input.
2. Inspect the LLM response.
	- **Final output** → return.
	- **Handoff** → switch to the new agent, keep the accumulated conversation history, go to 1.
	- **Tool calls** → execute tools, append their results to the conversation, go to 1.
3. Throw [`MaxTurnsExceededError`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/maxturnsexceedederror) once `maxTurns` is reached.

Create a `Runner` when your app starts and reuse it across requests. The instance stores global configuration such as model provider and tracing options. Only create another `Runner` if you need a completely different setup. For simple scripts you can also call `run()` which uses a default runner internally.

The input to the `run()` method is an initial agent to start the run on, input for the run and a set of options.

The input can either be a string (which is considered a user message), or a list of [input items](https://openai.github.io/openai-agents-js/openai/agents-core/type-aliases/agentinputitem), or a [`RunState`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/runstate) object in case you are building a [human-in-the-loop](https://openai.github.io/openai-agents-js/guides/human-in-the-loop) agent.

The additional options are:

| Option | Default | Description |
| --- | --- | --- |
| `stream` | `false` | If `true` the call returns a `StreamedRunResult` and emits events as they arrive from the model. |
| `context` | – | Context object forwarded to every tool / guardrail / handoff. Learn more in the [context guide](https://openai.github.io/openai-agents-js/guides/context). |
| `maxTurns` | `10` | Safety limit – throws [`MaxTurnsExceededError`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/maxturnsexceedederror) when reached. |
| `signal` | – | `AbortSignal` for cancellation. |

Streaming allows you to additionally receive streaming events as the LLM runs. Once the stream is started, the `StreamedRunResult` will contain the complete information about the run, including all the new outputs produces. You can iterate over the streaming events using a `for await` loop. Read more in the [streaming guide](https://openai.github.io/openai-agents-js/guides/streaming).

If you are creating your own `Runner` instance, you can pass in a `RunConfig` object to configure the runner.

| Field | Type | Purpose |
| --- | --- | --- |
| `model` | `string \| Model` | Force a specific model for **all** agents in the run. |
| `modelProvider` | `ModelProvider` | Resolves model names – defaults to the OpenAI provider. |
| `modelSettings` | `ModelSettings` | Global tuning parameters that override per‑agent settings. |
| `handoffInputFilter` | `HandoffInputFilter` | Mutates input items when performing handoffs (if the handoff itself doesn’t already define one). |
| `inputGuardrails` | `InputGuardrail[]` | Guardrails applied to the *initial* user input. |
| `outputGuardrails` | `OutputGuardrail[]` | Guardrails applied to the *final* output. |
| `tracingDisabled` | `boolean` | Disable OpenAI Tracing completely. |
| `traceIncludeSensitiveData` | `boolean` | Exclude LLM/tool inputs & outputs from traces while still emitting spans. |
| `workflowName` | `string` | Appears in the Traces dashboard – helps group related runs. |
| `traceId` / `groupId` | `string` | Manually specify the trace or group ID instead of letting the SDK generate one. |
| `traceMetadata` | `Record<string, any>` | Arbitrary metadata to attach to every span. |

Each call to `runner.run()` (or `run()` utility) represents one **turn** in your application-level conversation. You choose how much of the `RunResult` you show the end‑user – sometimes only `finalOutput`, other times every generated item.

```typescript
import { Agent, AgentInputItem, run } from '@openai/agents';

let thread: AgentInputItem[] = [];

const agent = new Agent({
  name: 'Assistant',
});

async function userSays(text: string) {
  const result = await run(
    agent,
    thread.concat({ role: 'user', content: text }),
  );

  thread = result.history; // Carry over history + newly generated items
  return result.finalOutput;
}

await userSays('What city is the Golden Gate Bridge in?');
// -> "San Francisco"

await userSays('What state is it in?');
// -> "California"
```

See [the chat example](https://github.com/openai/openai-agents-js/tree/main/examples/basic/chat.ts) for an interactive version.

The SDK throws a small set of errors you can catch:

- [`MaxTurnsExceededError`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/maxturnsexceedederror) – `maxTurns` reached.
- [`ModelBehaviorError`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/modelbehaviorerror) – model produced invalid output (e.g. malformed JSON, unknown tool).
- [`InputGuardrailTripwireTriggered`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/inputguardrailtripwiretriggered) / [`OutputGuardrailTripwireTriggered`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/outputguardrailtripwiretriggered) – guardrail violations.
- [`GuardrailExecutionError`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/guardrailexecutionerror) – guardrails failed to complete.
- [`ToolCallError`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/toolcallerror) – any of function tool calls failed.
- [`UserError`](https://openai.github.io/openai-agents-js/openai/agents-core/classes/usererror) – any error thrown based on configuration or user input.

All extend the base `AgentsError` class, which could provide the `state` property to access the current run state.

Here is an example code that handles `GuardrailExecutionError`:

```typescript
import {
  Agent,
  run,
  GuardrailExecutionError,
  InputGuardrail,
  InputGuardrailTripwireTriggered,
} from '@openai/agents';
import { z } from 'zod';

const guardrailAgent = new Agent({
  name: 'Guardrail check',
  instructions: 'Check if the user is asking you to do their math homework.',
  outputType: z.object({
    isMathHomework: z.boolean(),
    reasoning: z.string(),
  }),
});

const unstableGuardrail: InputGuardrail = {
  name: 'Math Homework Guardrail (unstable)',
  execute: async () => {
    throw new Error('Something is wrong!');
  },
};

const fallbackGuardrail: InputGuardrail = {
  name: 'Math Homework Guardrail (fallback)',
  execute: async ({ input, context }) => {
    const result = await run(guardrailAgent, input, { context });
    return {
      outputInfo: result.finalOutput,
      tripwireTriggered: result.finalOutput?.isMathHomework ?? false,
    };
  },
};

const agent = new Agent({
  name: 'Customer support agent',
  instructions:
    'You are a customer support agent. You help customers with their questions.',
  inputGuardrails: [unstableGuardrail],
});

async function main() {
  try {
    const input = 'Hello, can you help me solve for x: 2x + 3 = 11?';
    const result = await run(agent, input);
    console.log(result.finalOutput);
  } catch (e) {
    if (e instanceof GuardrailExecutionError) {
      console.error(\`Guardrail execution failed: ${e}\`);
      // If you want to retry the execution with different settings,
      // you can reuse the runner's latest state this way:
      if (e.state) {
        try {
          agent.inputGuardrails = [fallbackGuardrail]; // fallback
          const result = await run(agent, e.state);
          console.log(result.finalOutput);
        } catch (ee) {
          if (ee instanceof InputGuardrailTripwireTriggered) {
            console.log('Math homework guardrail tripped');
          }
        }
      }
    } else {
      throw e;
    }
  }
}

main().catch(console.error);
```

When you run the above example, you will see the following output:

```plaintext
Guardrail execution failed: Error: Input guardrail failed to complete: Error: Something is wrong!
Math homework guardrail tripped
```

---

- Learn how to [configure models](https://openai.github.io/openai-agents-js/guides/models).
- Provide your agents with [tools](https://openai.github.io/openai-agents-js/guides/tools).
- Add [guardrails](https://openai.github.io/openai-agents-js/guides/guardrails) or [tracing](https://openai.github.io/openai-agents-js/guides/tracing) for production readiness.