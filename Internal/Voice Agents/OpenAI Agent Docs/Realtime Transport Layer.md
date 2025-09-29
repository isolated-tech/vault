---
title: "Realtime Transport Layer"
source: "https://openai.github.io/openai-agents-js/guides/voice-agents/transport/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "Learn about the different transport layers that can be used with Realtime Agents."
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/guides/voice-agents/transport/#_top)

The default transport layer uses WebRTC. Audio is recorded from the microphone and played back automatically.

To use your own media stream or audio element, provide an `OpenAIRealtimeWebRTC` instance when creating the session.

```typescript
import { RealtimeAgent, RealtimeSession, OpenAIRealtimeWebRTC } from '@openai/agents/realtime';

const agent = new RealtimeAgent({
  name: 'Greeter',
  instructions: 'Greet the user with cheer and answer questions.',
});

async function main() {
  const transport = new OpenAIRealtimeWebRTC({
    audioElement: document.createElement('audio'),
  });

  const customSession = new RealtimeSession(agent, { transport });
}
```

Pass `transport: 'websocket'` or an instance of `OpenAIRealtimeWebSocket` when creating the session to use a WebSocket connection instead of WebRTC. This works well for server-side use cases, for example building a phone agent with Twilio.

```typescript
import { RealtimeAgent, RealtimeSession } from '@openai/agents/realtime';

const agent = new RealtimeAgent({
  name: 'Greeter',
  instructions: 'Greet the user with cheer and answer questions.',
});

const myRecordedArrayBuffer = new ArrayBuffer(0);

const wsSession = new RealtimeSession(agent, {
  transport: 'websocket',
  model: 'gpt-realtime',
});
await wsSession.connect({ apiKey: process.env.OPENAI_API_KEY! });

wsSession.on('audio', (event) => {
  // event.data is a chunk of PCM16 audio
});

wsSession.sendAudio(myRecordedArrayBuffer);
```

Use any recording/playback library to handle the raw PCM16 audio bytes.

If you want to use a different speech-to-speech API or have your own custom transport mechanism, you can create your own by implementing the `RealtimeTransportLayer` interface and emit the `RealtimeTransportEventTypes` events.

If you want to use the OpenAI Realtime API but have more direct access to the Realtime API, you have two options:

If you still want to benefit from all of the capabilities of the `RealtimeSession` you can access your transport layer through `session.transport`.

The transport layer will emit every event it receives under the `*` event and you can send raw events using the `sendEvent()` method.

```typescript
import { RealtimeAgent, RealtimeSession } from '@openai/agents/realtime';

const agent = new RealtimeAgent({
  name: 'Greeter',
  instructions: 'Greet the user with cheer and answer questions.',
});

const session = new RealtimeSession(agent, {
  model: 'gpt-realtime',
});

session.transport.on('*', (event) => {
  // JSON parsed version of the event received on the connection
});

// Send any valid event as JSON. For example triggering a new response
session.transport.sendEvent({
  type: 'response.create',
  // ...
});
```

If you don’t need automatic tool execution, guardrails, etc. you can also use the transport layer as a “thin” client that just manages connection and interruptions.

```typescript
import { OpenAIRealtimeWebRTC } from '@openai/agents/realtime';

const client = new OpenAIRealtimeWebRTC();
const audioBuffer = new ArrayBuffer(0);

await client.connect({
  apiKey: '<api key>',
  model: 'gpt-4o-mini-realtime-preview',
  initialSessionConfig: {
    instructions: 'Speak like a pirate',
    voice: 'ash',
    modalities: ['text', 'audio'],
    inputAudioFormat: 'pcm16',
    outputAudioFormat: 'pcm16',
  },
});

// optionally for WebSockets
client.on('audio', (newAudio) => {});

client.sendAudio(audioBuffer);
```