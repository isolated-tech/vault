---
title: "Streaming"
source: "https://openai.github.io/openai-agents-js/guides/streaming/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "Stream agent output in real time using the Runner"
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/guides/streaming/#_top)

The Agents SDK can deliver output from the model and other execution steps incrementally. Streaming keeps your UI responsive and avoids waiting for the entire final result before updating the user.

Pass a `{ stream: true }` option to `Runner.run()` to obtain a streaming object rather than a full result:

```typescript
import { Agent, run } from '@openai/agents';

const agent = new Agent({
  name: 'Storyteller',
  instructions:
    'You are a storyteller. You will be given a topic and you will tell a story about it.',
});

const result = await run(agent, 'Tell me a story about a cat.', {
  stream: true,
});
```

When streaming is enabled the returned `stream` implements the `AsyncIterable` interface. Each yielded event is an object describing what happened within the run. The stream yields one of three event types, each describing a different part of the agent’s execution. Most applications only want the model’s text though, so the stream provides helpers.

Call `stream.toTextStream()` to obtain a stream of the emitted text. When `compatibleWithNodeStreams` is `true` the return value is a regular Node.js `Readable`. We can pipe it directly into `process.stdout` or another destination.

```typescript
import { Agent, run } from '@openai/agents';

const agent = new Agent({
  name: 'Storyteller',
  instructions:
    'You are a storyteller. You will be given a topic and you will tell a story about it.',
});

const result = await run(agent, 'Tell me a story about a cat.', {
  stream: true,
});

result
  .toTextStream({
    compatibleWithNodeStreams: true,
  })
  .pipe(process.stdout);
```

The promise `stream.completed` resolves once the run and all pending callbacks are completed. Always await it if you want to ensure there is no more output.

You can use a `for await` loop to inspect each event as it arrives. Useful information includes low level model events, any agent switches and SDK specific run information:

```typescript
import { Agent, run } from '@openai/agents';

const agent = new Agent({
  name: 'Storyteller',
  instructions:
    'You are a storyteller. You will be given a topic and you will tell a story about it.',
});

const result = await run(agent, 'Tell me a story about a cat.', {
  stream: true,
});

for await (const event of result) {
  // these are the raw events from the model
  if (event.type === 'raw_model_stream_event') {
    console.log(\`${event.type} %o\`, event.data);
  }
  // agent updated events
  if (event.type === 'agent_updated_stream_event') {
    console.log(\`${event.type} %s\`, event.agent.name);
  }
  // Agent SDK specific events
  if (event.type === 'run_item_stream_event') {
    console.log(\`${event.type} %o\`, event.item);
  }
}
```

See [the streamed example](https://github.com/openai/openai-agents-js/tree/main/examples/agent-patterns/streamed.ts) for a fully worked script that prints both the plain text stream and the raw event stream.

The stream yields three different event types:

```ts
type RunRawModelStreamEvent = {
  type: 'raw_model_stream_event';
};
```

Example:

```json
{
  "type": "raw_model_stream_event",
  "data": {
    "type": "output_text_delta",
    "delta": "Hello"
  }
}
```

```ts
type RunItemStreamEvent = {
  type: 'run_item_stream_event';
  name: RunItemStreamEventName;
  item: RunItem;
};
```

Example handoff payload:

```json
{
  "type": "run_item_stream_event",
  "name": "handoff_occurred",
  "item": {
    "type": "handoff_call",
    "id": "h1",
    "status": "completed",
    "name": "transfer_to_refund_agent"
  }
}
```

```ts
type RunAgentUpdatedStreamEvent = {
  type: 'agent_updated_stream_event';
  agent: Agent<any, any>;
};
```

Example:

```json
{
  "type": "agent_updated_stream_event",
  "agent": {
    "name": "Refund Agent"
  }
}
```

Streaming is compatible with handoffs that pause execution (for example when a tool requires approval). The `interruption` field on the stream object exposes the interruptions, and you can continue execution by calling `state.approve()` or `state.reject()` for each of them. Executing again with `{ stream: true }` resumes streaming output.

```typescript
import { Agent, run } from '@openai/agents';

const agent = new Agent({
  name: 'Storyteller',
  instructions:
    'You are a storyteller. You will be given a topic and you will tell a story about it.',
});

let stream = await run(
  agent,
  'What is the weather in San Francisco and Oakland?',
  { stream: true },
);
stream.toTextStream({ compatibleWithNodeStreams: true }).pipe(process.stdout);
await stream.completed;

while (stream.interruptions?.length) {
  console.log(
    'Human-in-the-loop: approval required for the following tool calls:',
  );
  const state = stream.state;
  for (const interruption of stream.interruptions) {
    const approved = confirm(
      \`Agent ${interruption.agent.name} would like to use the tool ${interruption.rawItem.name} with "${interruption.rawItem.arguments}". Do you approve?\`,
    );
    if (approved) {
      state.approve(interruption);
    } else {
      state.reject(interruption);
    }
  }

  // Resume execution with streaming output
  stream = await run(agent, state, { stream: true });
  const textStream = stream.toTextStream({ compatibleWithNodeStreams: true });
  textStream.pipe(process.stdout);
  await stream.completed;
}
```

A fuller example that interacts with the user is [`human-in-the-loop-stream.ts`](https://github.com/openai/openai-agents-js/tree/main/examples/agent-patterns/human-in-the-loop-stream.ts).

- Remember to wait for `stream.completed` before exiting to ensure all output has been flushed.
- The initial `{ stream: true }` option only applies to the call where it is provided. If you re-run with a `RunState` you must specify the option again.
- If your application only cares about the textual result prefer `toTextStream()` to avoid dealing with individual event objects.

With streaming and the event system you can integrate an agent into a chat interface, terminal application or any place where users benefit from incremental updates.