---
title: "Context management"
source: "https://openai.github.io/openai-agents-js/guides/context/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "Learn how to provide local data via RunContext and expose context to the LLM"
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/guides/context/#_top)

Context is an overloaded term. There are two main classes of context you might care about:

1. **Local context** that your code can access during a run: dependencies or data needed by tools, callbacks like `onHandoff`, and lifecycle hooks.
2. **Agent/LLM context** that the language model can see when generating a response.

Local context is represented by the `RunContext<T>` type. You create any object to hold your state or dependencies and pass it to `Runner.run()`. All tool calls and hooks receive a `RunContext` wrapper so they can read from or modify that object.

```typescript
import { Agent, run, RunContext, tool } from '@openai/agents';
import { z } from 'zod';

interface UserInfo {
  name: string;
  uid: number;
}

const fetchUserAge = tool({
  name: 'fetch_user_age',
  description: 'Return the age of the current user',
  parameters: z.object({}),
  execute: async (
    _args,
    runContext?: RunContext<UserInfo>,
  ): Promise<string> => {
    return \`User ${runContext?.context.name} is 47 years old\`;
  },
});

async function main() {
  const userInfo: UserInfo = { name: 'John', uid: 123 };

  const agent = new Agent<UserInfo>({
    name: 'Assistant',
    tools: [fetchUserAge],
  });

  const result = await run(agent, 'What is the age of the user?', {
    context: userInfo,
  });

  console.log(result.finalOutput);
  // The user John is 47 years old.
}

if (require.main === module) {
  main().catch(console.error);
}
```

Every agent, tool and hook participating in a single run must use the same **type** of context.

Use local context for things like:

- Data about the run (user name, IDs, etc.)
- Dependencies such as loggers or data fetchers
- Helper functions

When the LLM is called, the only data it can see comes from the conversation history. To make additional information available you have a few options:

1. Add it to the Agent `instructions` – also known as a system or developer message. This can be a static string or a function that receives the context and returns a string.
2. Include it in the `input` when calling `Runner.run()`. This is similar to the instructions technique but lets you place the message lower in the [chain of command](https://cdn.openai.com/spec/model-spec-2024-05-08.html#follow-the-chain-of-command).
3. Expose it via function tools so the LLM can fetch data on demand.
4. Use retrieval or web search tools to ground responses in relevant data from files, databases, or the web.