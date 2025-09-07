---
title: "OpenAI Agents SDK TypeScript"
source: "https://openai.github.io/openai-agents-js/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "The OpenAI Agents SDK for TypeScript enables you to build agentic AI apps in a lightweight, easy-to-use package with very few abstractions."
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/#_top)

## Quickstart

Build your first agent in minutes.

- [Text Agent](https://openai.github.io/openai-agents-js/#tab-panel-4)
- [Voice Agent](https://openai.github.io/openai-agents-js/#tab-panel-5)

```typescript
import { RealtimeAgent, RealtimeSession } from '@openai/agents/realtime';

const agent = new RealtimeAgent({
  name: 'Assistant',
  instructions: 'You are a helpful assistant.',
});

// Automatically connects your microphone and audio output in the browser via WebRTC.
const session = new RealtimeSession(agent);
await session.connect({
  apiKey: '<client-api-key>',
});
```

The [OpenAI Agents SDK for TypeScript](https://github.com/openai/openai-agents-js) enables you to build agentic AI apps in a lightweight, easy-to-use package with very few abstractions. It’s a production-ready upgrade of our previous experimentation for agents,[Swarm](https://github.com/openai/swarm/tree/main), that’s also [available in Python](https://github.com/openai/openai-agents-python). The Agents SDK has a very small set of primitives:

- **Agents**, which are LLMs equipped with instructions and tools
- **Handoffs**, which allow agents to delegate to other agents for specific tasks
- **Guardrails**, which enable the inputs to agents to be validated

In combination with TypeScript, these primitives are powerful enough to express complex relationships between tools and agents, and allow you to build real-world applications without a steep learning curve. In addition, the SDK comes with built-in **tracing** that lets you visualize and debug your agentic flows, as well as evaluate them and even fine-tune models for your application.

The SDK has two driving design principles:

1. Enough features to be worth using, but few enough primitives to make it quick to learn.
2. Works great out of the box, but you can customize exactly what happens.

Here are the main features of the SDK:

- **Agent loop**: Built-in agent loop that handles calling tools, sending results to the LLM, and looping until the LLM is done.
- **TypeScript-first**: Use built-in language features to orchestrate and chain agents, rather than needing to learn new abstractions.
- **Handoffs**: A powerful feature to coordinate and delegate between multiple agents.
- **Guardrails**: Run input validations and checks in parallel to your agents, breaking early if the checks fail.
- **Function tools**: Turn any TypeScript function into a tool, with automatic schema generation and Zod-powered validation.
- **Tracing**: Built-in tracing that lets you visualize, debug and monitor your workflows, as well as use the OpenAI suite of evaluation, fine-tuning and distillation tools.
- **Realtime Agents**: Build powerful voice agents including automatic interruption detection, context management, guardrails, and more.

```bash
npm install @openai/agents zod@3
```

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

(*If running this, ensure you set the `OPENAI_API_KEY` environment variable*)

```bash
export OPENAI_API_KEY=sk-...
```