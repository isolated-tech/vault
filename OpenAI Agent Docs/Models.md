---
title: "Models"
source: "https://openai.github.io/openai-agents-js/guides/models/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "Choose and configure language models for your agents"
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/guides/models/#_top)

Every Agent ultimately calls an LLM. The SDK abstracts models behind two lightweight interfaces:

- [`Model`](https://openai.github.io/openai-agents-js/openai/agents/interfaces/model) – knows how to make *one* request against a specific API.
- [`ModelProvider`](https://openai.github.io/openai-agents-js/openai/agents/interfaces/modelprovider) – resolves human‑readable model **names** (e.g. `'gpt‑4o'`) to `Model` instances.

In day‑to‑day work you normally only interact with model **names** and occasionally `ModelSettings`.

```typescript
import { Agent } from '@openai/agents';

const agent = new Agent({
  name: 'Creative writer',
  model: 'gpt-4.1',
});
```

When you don’t specify a model when initializing an `Agent`, the default model will be used. The default is currently [`gpt-4.1`](https://platform.openai.com/docs/models/gpt-4.1), which offers a strong balance of predictability for agentic workflows and low latency.

If you want to switch to other models like [`gpt-5`](https://platform.openai.com/docs/models/gpt-5), there are two ways to configure your agents.

First, if you want to consistently use a specific model for all agents that do not set a custom model, set the `OPENAI_DEFAULT_MODEL` environment variable before running your agents.

```bash
export OPENAI_DEFAULT_MODEL=gpt-5
node my-awesome-agent.js
```

Second, you can set a default model for a `Runner` instance. If you don’t set a model for an agent, this `Runner` ’s default model will be used.

```typescript
import { Runner } from '@openai/agents';

const runner = new Runner({ model: 'gpt‑4.1-mini' });
```

When you use any of GPT-5’s reasoning models ([`gpt-5`](https://platform.openai.com/docs/models/gpt-5), [`gpt-5-mini`](https://platform.openai.com/docs/models/gpt-5-mini), or [`gpt-5-nano`](https://platform.openai.com/docs/models/gpt-5-nano)) this way, the SDK applies sensible `modelSettings` by default. Specifically, it sets both `reasoning.effort` and `verbosity` to `"low"`. To adjust the reasoning effort for the default model, pass your own `modelSettings`:

```ts
import { Agent } from '@openai/agents';

const myAgent = new Agent({
  name: 'My Agent',
  instructions: "You're a helpful agent.",
  modelSettings: {
    reasoning: { effort: 'minimal' },
    text: { verbosity: 'low' },
  },
  // If OPENAI_DEFAULT_MODEL=gpt-5 is set, passing only modelSettings works.
  // It's also fine to pass a GPT-5 model name explicitly:
  // model: 'gpt-5',
});
```

For lower latency, using either [`gpt-5-mini`](https://platform.openai.com/docs/models/gpt-5-mini) or [`gpt-5-nano`](https://platform.openai.com/docs/models/gpt-5-nano) with `reasoning.effort="minimal"` will often return responses faster than the default settings. However, some built-in tools (such as file search and image generation) in Responses API do not support `"minimal"` reasoning effort, which is why this Agents SDK defaults to `"low"`.

If you pass a non–GPT-5 model name without custom `modelSettings`, the SDK reverts to generic `modelSettings` compatible with any model.

---

The default `ModelProvider` resolves names using the OpenAI APIs. It supports two distinct endpoints:

| API | Usage | Call `setOpenAIAPI()` |
| --- | --- | --- |
| Chat Completions | Standard chat & function calls | `setOpenAIAPI('chat_completions')` |
| Responses | New streaming‑first generative API (tool calls, flexible outputs) | `setOpenAIAPI('responses')` *(default)* |

```typescript
import { setDefaultOpenAIKey } from '@openai/agents';

setDefaultOpenAIKey(process.env.OPENAI_API_KEY!); // sk-...
```

You can also plug your own `OpenAI` client via `setDefaultOpenAIClient(client)` if you need custom networking settings.

---

`ModelSettings` mirrors the OpenAI parameters but is provider‑agnostic.

| Field | Type | Notes |
| --- | --- | --- |
| `temperature` | `number` | Creativity vs. determinism. |
| `topP` | `number` | Nucleus sampling. |
| `frequencyPenalty` | `number` | Penalise repeated tokens. |
| `presencePenalty` | `number` | Encourage new tokens. |
| `toolChoice` | `'auto' \| 'required' \| 'none' \| string` | See [forcing tool use](https://openai.github.io/openai-agents-js/guides/agents#forcing-tool-use). |
| `parallelToolCalls` | `boolean` | Allow parallel function calls where supported. |
| `truncation` | `'auto' \| 'disabled'` | Token truncation strategy. |
| `maxTokens` | `number` | Maximum tokens in the response. |
| `store` | `boolean` | Persist the response for retrieval / RAG workflows. |
| `reasoning.effort` | `'minimal' \| 'low' \| 'medium' \| 'high'` | Reasoning effort for gpt-5 etc. |
| `text.verbosity` | `'low' \| 'medium' \| 'high'` | Text verbosity for gpt-5 etc. |

Attach settings at either level:

```typescript
import { Runner, Agent } from '@openai/agents';

const agent = new Agent({
  name: 'Creative writer',
  // ...
  modelSettings: { temperature: 0.7, toolChoice: 'auto' },
});

// or globally
new Runner({ modelSettings: { temperature: 0.3 } });
```

`Runner` ‑level settings override any conflicting per‑agent settings.

---

Agents can be configured with a `prompt` parameter, indicating a server-stored prompt configuration that should be used to control the Agent’s behavior. Currently, this option is only supported when you use the OpenAI [Responses API](https://platform.openai.com/docs/api-reference/responses).

| Field | Type | Notes |
| --- | --- | --- |
| `promptId` | `string` | Unique identifier for a prompt. |
| `version` | `string` | Version of the prompt you wish to use. |
| `variables` | `object` | A key/value pair of variables to substitute into the prompt. Values can be strings or content input types like text, images, or files. |

```typescript
import { Agent, run } from '@openai/agents';

async function main() {
  const agent = new Agent({
    name: 'Assistant',
    prompt: {
      promptId: 'pmpt_684b3b772e648193b92404d7d0101d8a07f7a7903e519946',
      version: '1',
      variables: {
        poem_style: 'limerick',
      },
    },
  });

  const result = await run(agent, 'Write about unrequited love.');
  console.log(result.finalOutput);
}

if (require.main === module) {
  main().catch(console.error);
}
```

Any additional agent configuration, like tools or instructions, will override the values you may have configured in your stored prompt.

---

Implementing your own provider is straightforward – implement `ModelProvider` and `Model` and pass the provider to the `Runner` constructor:

```typescript
import {
  ModelProvider,
  Model,
  ModelRequest,
  ModelResponse,
  ResponseStreamEvent,
} from '@openai/agents-core';

import { Agent, Runner } from '@openai/agents';

class EchoModel implements Model {
  name: string;
  constructor() {
    this.name = 'Echo';
  }
  async getResponse(request: ModelRequest): Promise<ModelResponse> {
    return {
      usage: {},
      output: [{ role: 'assistant', content: request.input as string }],
    } as any;
  }
  async *getStreamedResponse(
    _request: ModelRequest,
    yield {
      type: 'response.completed',
      response: { output: [], usage: {} },
    } as any;
  }
}

class EchoProvider implements ModelProvider {
  getModel(_modelName?: string): Promise<Model> | Model {
    return new EchoModel();
  }
}

const runner = new Runner({ modelProvider: new EchoProvider() });
console.log(runner.config.modelProvider.getModel());
const agent = new Agent({
  name: 'Test Agent',
  instructions: 'You are a helpful assistant.',
  model: new EchoModel(),
  modelSettings: { temperature: 0.7, toolChoice: 'auto' },
});
console.log(agent.model);
```

---

When using the OpenAI provider you can opt‑in to automatic trace export by providing your API key:

```typescript
import { setTracingExportApiKey } from '@openai/agents';

setTracingExportApiKey('sk-...');
```

This sends traces to the [OpenAI dashboard](https://platform.openai.com/traces) where you can inspect the complete execution graph of your workflow.

---

- Explore [running agents](https://openai.github.io/openai-agents-js/guides/running-agents).
- Give your models super‑powers with [tools](https://openai.github.io/openai-agents-js/guides/tools).
- Add [guardrails](https://openai.github.io/openai-agents-js/guides/guardrails) or [tracing](https://openai.github.io/openai-agents-js/guides/tracing) as needed.