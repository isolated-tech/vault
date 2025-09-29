---
title: "Tools"
source: "https://openai.github.io/openai-agents-js/guides/tools/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "Provide your agents with capabilities via hosted tools or custom function tools"
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/guides/tools/#_top)

Tools let an Agent **take actions** – fetch data, call external APIs, execute code, or even use a computer. The JavaScript/TypeScript SDK supports four categories:

1. **Hosted tools** – run alongside the model on OpenAI servers. *(web search, file search, computer use, code interpreter, image generation)*
2. **Function tools** – wrap any local function with a JSON schema so the LLM can call it.
3. **Agents as tools** – expose an entire Agent as a callable tool.
4. **Local MCP servers** – attach a Model Context Protocol server running on your machine.

---

When you use the `OpenAIResponsesModel` you can add the following built‑in tools:

| Tool | Type string | Purpose |
| --- | --- | --- |
| Web search | `'web_search'` | Internet search. |
| File / retrieval search | `'file_search'` | Query vector stores hosted on OpenAI. |
| Computer use | `'computer'` | Automate GUI interactions. |
| Code Interpreter | `'code_interpreter'` | Run code in a sandboxed environment. |
| Image generation | `'image_generation'` | Generate images based on text. |

```typescript
import { Agent, webSearchTool, fileSearchTool } from '@openai/agents';

const agent = new Agent({
  name: 'Travel assistant',
  tools: [webSearchTool(), fileSearchTool('VS_ID')],
});
```

The exact parameter sets match the OpenAI Responses API – refer to the official documentation for advanced options like `rankingOptions` or semantic filters.

---

You can turn **any** function into a tool with the `tool()` helper.

```typescript
import { tool } from '@openai/agents';
import { z } from 'zod';

const getWeatherTool = tool({
  name: 'get_weather',
  description: 'Get the weather for a given city',
  parameters: z.object({ city: z.string() }),
  async execute({ city }) {
    return \`The weather in ${city} is sunny.\`;
  },
});
```

| Field | Required | Description |
| --- | --- | --- |
| `name` | No | Defaults to the function name (e.g., `get_weather`). |
| `description` | Yes | Clear, human-readable description shown to the LLM. |
| `parameters` | Yes | Either a Zod schema or a raw JSON schema object. Zod parameters automatically enable **strict** mode. |
| `strict` | No | When `true` (default), the SDK returns a model error if the arguments don’t validate. Set to `false` for fuzzy matching. |
| `execute` | Yes | `(args, context) => string                                                                                               \| Promise<string>` – your business logic. The optional second parameter is the `RunContext`. |
| `errorFunction` | No | Custom handler `(context, error) => string` for transforming internal errors into a user-visible string. |

If you need the model to *guess* invalid or partial input you can disable strict mode when using raw JSON schema:

```typescript
import { tool } from '@openai/agents';

interface LooseToolInput {
  text: string;
}

const looseTool = tool({
  description: 'Echo input; be forgiving about typos',
  strict: false,
  parameters: {
    type: 'object',
    properties: { text: { type: 'string' } },
    required: ['text'],
    additionalProperties: true,
  },
  execute: async (input) => {
    // because strict is false we need to do our own verification
    if (typeof input !== 'object' || input === null || !('text' in input)) {
      return 'Invalid input. Please try again';
    }
    return (input as LooseToolInput).text;
  },
});
```

---

Sometimes you want an Agent to *assist* another Agent without fully handing off the conversation. Use `agent.asTool()`:

```typescript
import { Agent } from '@openai/agents';

const summarizer = new Agent({
  name: 'Summarizer',
  instructions: 'Generate a concise summary of the supplied text.',
});

const summarizerTool = summarizer.asTool({
  toolName: 'summarize_text',
  toolDescription: 'Generate a concise summary of the supplied text.',
});

const mainAgent = new Agent({
  name: 'Research assistant',
  tools: [summarizerTool],
});
```

Under the hood the SDK:

- Creates a function tool with a single `input` parameter.
- Runs the sub‑agent with that input when the tool is called.
- Returns either the last message or the output extracted by `customOutputExtractor`.

---

You can expose tools via a local [Model Context Protocol](https://modelcontextprotocol.io/) server and attach them to an agent. Use `MCPServerStdio` to spawn and connect to the server:

```typescript
import { Agent, MCPServerStdio } from '@openai/agents';

const server = new MCPServerStdio({
  fullCommand: 'npx -y @modelcontextprotocol/server-filesystem ./sample_files',
});

await server.connect();

const agent = new Agent({
  name: 'Assistant',
  mcpServers: [server],
});
```

See [`filesystem-example.ts`](https://github.com/openai/openai-agents-js/tree/main/examples/mcp/filesystem-example.ts) for a complete example.

---

Refer to the [Agents guide](https://openai.github.io/openai-agents-js/guides/agents#forcing-tool-use) for controlling when and how a model must use tools (`tool_choice`, `toolUseBehavior`, etc.).

---

- **Short, explicit descriptions** – describe *what* the tool does *and when to use it*.
- **Validate inputs** – use Zod schemas for strict JSON validation where possible.
- **Avoid side‑effects in error handlers** – `errorFunction` should return a helpful string, not throw.
- **One responsibility per tool** – small, composable tools lead to better model reasoning.

---

- Learn about [forcing tool use](https://openai.github.io/openai-agents-js/guides/agents#forcing-tool-use).
- Add [guardrails](https://openai.github.io/openai-agents-js/guides/guardrails) to validate tool inputs or outputs.
- Dive into the TypeDoc reference for [`tool()`](https://openai.github.io/openai-agents-js/openai/agents/functions/tool) and the various hosted tool types.