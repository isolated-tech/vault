In this article, we'll be exploring Vercel's latest toy - [AI Elements](https://vercel.com/changelog/introducing-ai-elements) - a component library and custom registry built on top of [shadcn/ui](ui.shadcn.com/) to help you build AI-native applications faster.

## Prerequisites

Before using AI Elements, ensure your project meets these requirements:

- **Node.js** 18 or later
- **Next.js** project with [AI SDK](https://ai-sdk.dev/) installed
- **shadcn/ui** initialized in your project (`npx shadcn@latest init`)
- **Tailwind CSS** configured (AI Elements supports CSS Variables mode only)

## Installation

First, set up a new Next.js repo and `cd` into it by running the following command:

```
npx create-next-app@latest ai-chatbot && cd ai-chatbot
```



## Available Components

AI Elements includes the following components:

| Component          | Description                                             |
| ------------------ | ------------------------------------------------------- |
| **Chatbot**        |                                                         |
| `actions`          | Interactive action buttons for AI responses             |
| `branch`           | Branch visualization for conversation flows             |
| `chain-of-thought` | Display AI reasoning and thought processes              |
| `code-block`       | Syntax-highlighted code display with copy functionality |
| `context`          | Display Context consumption                             |
| `conversation`     | Container for chat conversations                        |
| `image`            | AI-generated image display component                    |
| `inline-citation`  | Inline source citations                                 |
| `loader`           | Loading states for AI operations                        |
| `message`          | Individual chat messages with avatars                   |
| `open-in-chat`     | Open in chat button for a message                       |
| `plan`             | Plan and task planning display component                |
| `prompt-input`     | Advanced input component with model selection           |
| `queue`            | Message and todo queue with attachments                 |
| `reasoning`        | Display AI reasoning and thought processes              |
| `response`         | Formatted AI response display                           |
| `shimmer`          | Text shimmer animation effect                           |
| `sources`          | Source attribution component                            |
| `suggestion`       | Quick action suggestions                                |
| `task`             | Task completion tracking                                |
| `tool`             | Tool usage visualization                                |
| `confirmation`     | Tool execution approval workflows                       |
| **Vibe-Coding**    |                                                         |
| `artifact`         | Display a code or document                              |
| `web-preview`      | Embedded web page previews                              |
| **Workflow**       |                                                         |
| `canvas`           | ReactFlow canvas for workflow visualizations            |
| `connection`       | Connection line component for workflow edges            |
| `controls`         | Flow controls for canvas (zoom, fit view, etc.)         |
| `edge`             | Edge component for connections between workflow nodes   |
| `node`             | Node component for workflow graphs                      |
| `panel`            | Panel component for canvas overlays                     |
| `toolbar`          | Node toolbar for workflow elements                      |

[^1]:https://vercel.com/blog/introducing-the-vercel-ai-sdk
[^2]: https://vercel.com/blog/announcing-v0-generative-ui

