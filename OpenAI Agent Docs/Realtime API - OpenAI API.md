---
title: "Realtime API - OpenAI API"
source: "https://platform.openai.com/docs/guides/realtime"
author:
published:
created: 2025-09-06
description: "Learn how to build low-latency, multimodal LLM applications with the Realtime API."
tags:
  - "clippings"
---
Build low-latency, multimodal LLM applications with the Realtime API.

The OpenAI Realtime API enables low-latency communication with [models](https://platform.openai.com/docs/models) that natively support speech-to-speech interactions as well as multimodal inputs (audio, images, and text) and outputs (audio and text). These APIs can also be used for [realtime audio transcription](https://platform.openai.com/docs/guides/realtime-transcription).

## Voice agents

One of the most common use cases for the Realtime API is building voice agents for speech-to-speech model interactions in the browser. Our recommended starting point for these types of applications is the [Agents SDK for TypeScript](https://openai.github.io/openai-agents-js/guides/voice-agents/), which uses a [WebRTC connection](https://platform.openai.com/docs/guides/realtime-webrtc) to the Realtime model in the browser, and [WebSocket](https://platform.openai.com/docs/guides/realtime-websocket) when used on the server.

```js
1



import { RealtimeAgent, RealtimeSession } from "@openai/agents/realtime";

const agent = new RealtimeAgent({
    name: "Assistant",
    instructions: "You are a helpful assistant.",
});

const session = new RealtimeSession(agent);

// Automatically connects your microphone and audio output
await session.connect({
    apiKey: "<client-api-key>",
});
```

Follow the voice agent quickstart to build Realtime agents in the browser.
[Voice Agent Quickstart](https://openai.github.io/openai-agents-js/guides/voice-agents/quickstart/)

To use the Realtime API directly outside the context of voice agents, check out the other connection options below.

## Connection methods

While building [voice agents with the Agents SDK](https://openai.github.io/openai-agents-js/guides/voice-agents/) is the fastest path to one specific type of application, the Realtime API provides an entire suite of flexible tools for a variety of use cases.

There are three primary supported interfaces for the Realtime API:

[

WebRTC connection

Ideal for browser and client-side interactions with a Realtime model.

](https://platform.openai.com/docs/guides/realtime-webrtc)[

WebSocket connection

Ideal for middle tier server-side applications with consistent low-latency network connections.

](https://platform.openai.com/docs/guides/realtime-websocket)[

SIP connection

Ideal for VoIP telephony connections.

](https://platform.openai.com/docs/guides/realtime-sip)

Depending on how you'd like to connect to a Realtime model, check out one of the connection guides above to get started. You'll learn how to initialize a Realtime session, and how to interact with a Realtime model using client and server events.

## API Usage

Once connected to a realtime model using one of the methods above, learn how to interact with the model in these usage guides.

- **[Prompting guide](https://platform.openai.com/docs/guides/realtime-models-prompting):** learn tips and best practices for prompting and steering Realtime models.
- **[Managing conversations](https://platform.openai.com/docs/guides/realtime-conversations):** Learn about the Realtime session lifecycle and the key events that happen during a conversation.
- **[Webhooks and server-side controls](https://platform.openai.com/docs/guides/realtime-server-controls):** Learn how you can control a Realtime session on the server to call tools and implement guardrails.
- **[Realtime audio transcription](https://platform.openai.com/docs/guides/realtime-transcription):** Transcribe audio streams in real time over a WebSocket connection.

There are a few key differences between the interfaces in the Realtime beta API and the recently released GA API. Expand the topics below for more information about migrating from the beta interface to GA.

Beta header

Generating ephemeral API keys

New URL for WebRTC SDP data

New event names and shapes

New conversation item events

Input and output item changes