---
title: "Introducing gpt-realtime and Realtime API updates for production voice agents"
source: "https://openai.com/index/introducing-gpt-realtime/"
author:
  - "[[OpenAI]]"
published: 2025-09-02
created: 2025-09-06
description: "We’re releasing a more advanced speech-to-speech model and new API capabilities including MCP server support, image input, and SIP phone calling support."
tags:
  - "clippings"
---
Introducing gpt-realtime and Realtime API updates for production voice agents | OpenAI

We’re releasing a more advanced speech-to-speech model and new API capabilities including MCP server support, image input, and SIP phone calling support.

![Stylized interface showing a voice interaction. Centered is a rounded rectangular audio player with a waveform visualization, play/pause button, “Agent online” status indicator, and timestamp of 00:35. White curved lines with dots flow across the image, suggesting live audio or signal movement. The background is a vivid blue with blurred flower shapes in pink and purple tones.](https://images.ctfassets.net/kftzwdyauwt9/2P07oLbgCw1M528pOZGvBn/e47130e97d7d0481f0c58c74c4cdeed3/oai_realtime-api-ga_blog-header.png?w=3840&q=90&fm=webp)

Today we’re making the Realtime API generally available with new features that enable developers and enterprises to build reliable, production-ready voice agents. The API now supports remote MCP servers, image inputs, and phone calling through Session Initiation Protocol (SIP), making voice agents more capable through access to additional tools and context.

We’re also releasing our most advanced speech-to-speech model yet— `gpt-realtime`. The new model shows improvements in following complex instructions, calling tools with precision, and producing speech that sounds more natural and expressive. It’s better at interpreting system messages and developer prompts—whether that’s reading disclaimer scripts word-for-word on a support call, repeating back alphanumerics, or switching seamlessly between languages mid-sentence. We’re also releasing two new voices, Cedar and Marin, which are available exclusively in the Realtime API starting today.

Since we first introduced the Realtime API in public beta last October, thousands of developers have built with the API and helped shape the improvements we’re releasing today—optimized for reliability, low latency, and high quality to successfully deploy voice agents in production. Unlike traditional pipelines that chain together multiple models across speech-to-text and text-to-speech, the Realtime API processes and generates audio directly through a single model and API. This reduces latency, preserves nuance in speech, and produces more natural, expressive responses.

<iframe src="https://player.vimeo.com/video/1113635977?h=c655cfd2c6&amp;amp%3Bbadge=0&amp;amp%3Bautopause=0&amp;amp%3Bplayer_id=0&amp;amp%3Bapp_id=58479&amp;controls=0&amp;autopause=0" width="100%" height="100%" title=" from OpenAI on Vimeo" allow="autoplay; fullscreen; picture-in-picture; clipboard-write"></iframe>

“The new speech-to-speech model in OpenAI's Realtime API shows stronger reasoning and more natural speech—allowing it to handle complex, multi-step requests like narrowing listings by lifestyle needs or guiding affordability discussions with tools like our BuyAbility score. This could make searching for a home on Zillow or exploring financing options feel as natural as a conversation with a friend, helping simplify decisions like buying, selling, and renting a home.”

– Josh Weisberg, Head of AI at **Zillow**

## Introducing gpt-realtime

The new speech-to-speech model— `gpt-realtime` —is our most advanced, production-ready voice model. We trained the model in close collaboration with customers to excel at real-world tasks like customer support, personal assistance, and education—aligning the model to how developers build and deploy voice agents. The model shows improvements across audio quality, intelligence, instruction following, and function calling.

<iframe src="https://player.vimeo.com/video/1112437623?h=6948f02daf&amp;amp%3Bbadge=0&amp;amp%3Bautopause=0&amp;amp%3Bplayer_id=0&amp;amp%3Bapp_id=58479&amp;controls=0&amp;autopause=0" width="100%" height="100%" title=" from OpenAI on Vimeo" allow="autoplay; fullscreen; picture-in-picture; clipboard-write"></iframe>

#### Audio quality

Natural-sounding conversation is critical for deploying voice agents in the real world. Models need to speak with the intonation, emotion, and pace of a human to create an enjoyable experience and encourage continuous conversation with users. We trained `gpt-realtime` to produce higher-quality speech that sounds more natural and can follow fine-grained instructions, such as “speak quickly and professionally” or “speak empathetically in a French accent.”

We’re releasing two new voices in the API, Marin and Cedar, with the most significant improvements to natural-sounding speech. We’re also updating our existing eight voices to benefit from these improvements.

Voice sample - Marin

<audio><source src="https://assets.ctfassets.net/kftzwdyauwt9/40rfGH7POKs56f3I6cbcHi/5c3bf8dc9461679fe5e98748f34e681a/Marin2.m4a"></audio>

Voice sample - Cedar

<audio><source src="https://assets.ctfassets.net/kftzwdyauwt9/4azJCry5dT5qhhBarVRDeJ/06fcb54c0c704494746ab33d1dd5448f/Cedar.m4a"></audio>

#### Intelligence and comprehension

`gpt-realtime` shows higher intelligence and can comprehend native audio with greater accuracy. The model can capture non-verbal cues (like laughs), switch languages mid-sentence, and adapt tone (“snappy and professional” vs. “kind and empathetic”). According to internal evaluations, the model also shows more accurate performance in detecting alphanumeric sequences (such as phone numbers, VINs, etc) in other languages, including Spanish, Chinese, Japanese, and French. On the Big Bench Audio eval measuring reasoning capabilities, `gpt-realtime` scores 82.8% accuracy—beating our previous model from December 2024, which scores 65.6%.

The [Big Bench Audio ⁠ (opens in a new window)](https://huggingface.co/datasets/ArtificialAnalysis/big_bench_audio) benchmark is an evaluation dataset for assessing the reasoning capabilities of language models that support audio input. This dataset adapts questions from Big Bench Hard—chosen for its rigorous testing of advanced reasoning—into the audio domain.

#### Instruction following

When building a speech-to-speech application, developers give a set of instructions to the model on how to behave, including how to speak, what to say in a certain situation, and what to do or not do. We’ve focused our improvements on the adherence to these instructions, so that even minor directions carry more signal for the model. On the MultiChallenge audio benchmark measuring instruction following accuracy, `gpt-realtime` scores 30.5%, a significant improvement over our previous model from December 2024, which scores 20.6%.

[MultiChallenge ⁠ (opens in a new window)](https://arxiv.org/abs/2501.17399) evaluates how well LLMs handle multi-turn conversations with humans. It focuses on four categories of realistic challenges that current frontier models struggle with. These challenges require models to combine instruction-following, context management, and in-context reasoning simultaneously. We converted an audio-friendly subset of the test questions from text-to-speech to create an audio version of this evaluation.

#### Function calling

To build a capable voice agent with a speech-to-speech model, the model needs to be able to call the right tools at the right time to be useful in production. We’ve improved function calling on three axes: calling relevant functions, calling functions at the appropriate time, and calling functions with appropriate arguments (resulting in higher accuracy). On the ComplexFuncBench audio eval measuring function calling performance, `gpt-realtime` scores 66.5%, while our previous model from December 2024 scores 49.7%.

We’ve also made improvements to [asynchronous function calling⁠ (opens in a new window)](http://platform.openai.com/docs/guides/realtime-function-calling). Long-running function calls will no longer disrupt the flow of a session—the model can continue a fluid conversation while waiting on results. This feature is available natively in `gpt-realtime`, so developers do not need to update their code.

[ComplexFuncBench ⁠ (opens in a new window)](https://github.com/zai-org/ComplexFuncBench) measures how well models handle challenging function calling tasks. It evaluates performance across scenarios like multi-step calls, reasoning about constraints or implicit parameters, handling very long inputs. We converted the original text prompts into speech to build this evaluation for our model.

## New in the Realtime API

You can enable MCP support in a Realtime API session by passing the URL of a remote MCP server into the session configuration. Once connected, the API automatically handles the tool calls for you, so there’s no need to wire up integrations manually.

This setup makes it easy to extend your agent with new capabilities—just point the session to a different MCP server, and those tools become available right away. To learn more about configuring MCP with Realtime, check out [this guide⁠ (opens in a new window)](http://platform.openai.com/docs/guides/realtime-mcp).

#### JavaScript

`  ``` 1// POST /v1/realtime/client_secrets2{3  "session": {4    "type": "realtime",5    "tools": [6      {7        "type": "mcp",8        "server_label": "stripe",9        "server_url": "https://mcp.stripe.com",10        "authorization": "{access_token}",11        "require_approval": "never"12      }13    ]14  }15}16 ```  `

#### Image input

With image inputs now supported in `gpt-realtime`, you can add images, photos, and screenshots alongside audio or text to a Realtime API session. Now the model can ground the conversation in what the user is actually seeing, enabling users to ask questions like “what do you see?” or “read the text in this screenshot.”

Instead of treating an image like a live video stream, the system treats it more like adding a picture into the conversation. Your app can decide which images to share with the model and when to share them. This way, you stay in control of what the model sees and when it responds.

Check out our [docs ⁠ (opens in a new window)](http://platform.openai.com/docs/guides/realtime-inputs-outputs) to get started with image input.

#### JavaScript

`  ``` 1{2    "type": "conversation.item.create",3    "previous_item_id": null,4    "item": {5        "type": "message",6        "role": "user",7        "content": [8            {9                "type": "input_image",10                "image_url": "data:image/{format(example: png)};base64,{some_base64_image_bytes}"11            }12        ]13    }14}15 ```  `

#### Additional capabilities

We’ve added several other features to make the Realtime API easier to integrate and more flexible for production use.

The Realtime API incorporates multiple layers of safeguards and mitigations to help prevent misuse. You can learn more about our safety approach and system card details in the [beta announcement blog⁠](https://openai.com/index/introducing-the-realtime-api/). We employ active classifiers over Realtime API sessions, meaning certain conversations can be halted if they are detected as violating our harmful content guidelines. Developers can also easily add their own additional safety guardrails using the [Agents SDK⁠ (opens in a new window)](https://openai.github.io/openai-agents-js/guides/guardrails/).

Our [usage policies⁠](https://openai.com/policies/usage-policies/) prohibit repurposing or distributing outputs from our services for spam, deception, or other harmful purposes. Developers must also make it clear to end users when they’re interacting with AI, unless it’s already obvious from the context. The Realtime API uses preset voices to help prevent malicious actors from impersonating others.

## Pricing & availability

The generally available Realtime API and new `gpt-realtime` model are available to all developers starting today. We’re reducing prices for `gpt-realtime` by 20% compared to `gpt-4o-realtime-preview` —$32 / 1M audio input tokens ($0.40 for cached input tokens) and $64 / 1M audio output tokens (see [detailed pricing⁠ (opens in a new window)](https://platform.openai.com/docs/pricing#audio-tokens)). We’ve also added fine-grained control for conversation context to let developers set intelligent token limits and truncate multiple turns at a time, significantly reducing cost for long sessions.

To get started, visit our [Realtime API documentation⁠ (opens in a new window)](https://platform.openai.com/docs/guides/realtime), test the new model in the [Playground⁠ (opens in a new window)](https://platform.openai.com/audio/realtime), and view our [Realtime API prompting guide⁠ (opens in a new window)](https://platform.openai.com/docs/guides/realtime-models-prompting).

## Livestream replay

<iframe frameborder="0" allowfullscreen="" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" title="Introducing gpt-realtime in the API" width="100%" height="100%" src="https://www.youtube-nocookie.com/embed/nfBbmtMJhX0?autoplay=0&amp;mute=0&amp;controls=1&amp;origin=https%3A%2F%2Fopenai.com&amp;playsinline=1&amp;showinfo=0&amp;rel=0&amp;iv_load_policy=3&amp;modestbranding=1&amp;enablejsapi=1&amp;hl=en-US&amp;widgetid=1"></iframe>![](https://images.ctfassets.net/kftzwdyauwt9/6zxA3gcnfP5b578cfwuqdb/b91f8c80dde5777526f62122b3584b58/realtime-api-ga-livestream-thumbnail.png?w=3840&q=50&fm=webp)

- [2025](https://openai.com/news/?tags=2025)

## Author

## Keep reading

[View all](https://openai.com/news/product/)

![more helpful ChatGPT experiences for everyone > cover image](https://images.ctfassets.net/kftzwdyauwt9/14NVHnRCEUPSGOP9IOQCPW/91f440d58ae528eb4bc23e99ec33ad0a/oai_GA_Stories_1.1.png?w=3840&q=90&fm=webp)[

Building more helpful ChatGPT experiences for everyone

Product

](https://openai.com/index/building-more-helpful-chatgpt-experiences-for-everyone/)

![Helping people when they need it most > cover image](https://images.ctfassets.net/kftzwdyauwt9/4SrBiwNvYq4hW3JbqDW28O/7ead0f78030643e91c7304d82f387bb0/oai_GA_Stories_1.1-alt.png?w=3840&q=90&fm=webp)[

Helping people when they need it most

Product

](https://openai.com/index/helping-people-when-they-need-it-most/)

![GPT-5 Enterprise > Cover Image](https://images.ctfassets.net/kftzwdyauwt9/6aFpkPOhGqKgVQeh8uYJdv/722e57ac262e25fb79f4018651f5574d/GPT-5_EntBlog_ArtCard_1x1.png?w=3840&q=90&fm=webp)[

GPT-5 and the new era of work

Product

](https://openai.com/index/gpt-5-new-era-of-work/)