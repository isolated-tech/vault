---
title: "Handoffs"
source: "https://openai.github.io/openai-agents-js/guides/handoffs/"
author:
  - "[[OpenAI Agents SDK]]"
published:
created: 2025-09-06
description: "Delegate tasks from one agent to another"
tags:
  - "clippings"
---
[Skip to content](https://openai.github.io/openai-agents-js/guides/handoffs/#_top)

Handoffs let an agent delegate part of a conversation to another agent. This is useful when different agents specialise in specific areas. In a customer support app for example, you might have agents that handle bookings, refunds or FAQs.

Handoffs are represented as tools to the LLM. If you hand off to an agent called `Refund Agent`, the tool name would be `transfer_to_refund_agent`.

Every agent accepts a `handoffs` option. It can contain other `Agent` instances or `Handoff` objects returned by the `handoff()` helper.

```typescript
import { Agent, handoff } from '@openai/agents';

const billingAgent = new Agent({ name: 'Billing agent' });
const refundAgent = new Agent({ name: 'Refund agent' });

// Use Agent.create method to ensure the finalOutput type considers handoffs
const triageAgent = Agent.create({
  name: 'Triage agent',
  handoffs: [billingAgent, handoff(refundAgent)],
});
```

The `handoff()` function lets you tweak the generated tool.

- `agent` – the agent to hand off to.
- `toolNameOverride` – override the default `transfer_to_<agent_name>` tool name.
- `toolDescriptionOverride` – override the default tool description.
- `onHandoff` – callback when the handoff occurs. Receives a `RunContext` and optionally parsed input.
- `inputType` – expected input schema for the handoff.
- `inputFilter` – filter the history passed to the next agent.

```typescript
import { Agent, handoff, RunContext } from '@openai/agents';

function onHandoff(ctx: RunContext) {
  console.log('Handoff called');
}

const agent = new Agent({ name: 'My agent' });

const handoffObj = handoff(agent, {
  onHandoff,
  toolNameOverride: 'custom_handoff_tool',
  toolDescriptionOverride: 'Custom description',
});
```

Sometimes you want the LLM to provide data when invoking a handoff. Define an input schema and use it in `handoff()`.

```typescript
import { z } from 'zod';
import { Agent, handoff, RunContext } from '@openai/agents';

const EscalationData = z.object({ reason: z.string() });
type EscalationData = z.infer<typeof EscalationData>;

async function onHandoff(
  ctx: RunContext<EscalationData>,
  input: EscalationData | undefined,
) {
  console.log(\`Escalation agent called with reason: ${input?.reason}\`);
}

const agent = new Agent<EscalationData>({ name: 'Escalation agent' });

const handoffObj = handoff(agent, {
  onHandoff,
  inputType: EscalationData,
});
```

By default a handoff receives the entire conversation history. To modify what gets passed to the next agent, provide an `inputFilter`. Common helpers live in `@openai/agents-core/extensions`.

```typescript
import { Agent, handoff } from '@openai/agents';
import { removeAllTools } from '@openai/agents-core/extensions';

const agent = new Agent({ name: 'FAQ agent' });

const handoffObj = handoff(agent, {
  inputFilter: removeAllTools,
});
```

LLMs respond more reliably when your prompts mention handoffs. The SDK exposes a recommended prefix via `RECOMMENDED_PROMPT_PREFIX`.

```typescript
import { Agent } from '@openai/agents';

const billingAgent = new Agent({
  name: 'Billing agent',
Fill in the rest of your prompt here.\`,
});
```