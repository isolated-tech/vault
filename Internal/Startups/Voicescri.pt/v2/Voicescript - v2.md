With the release of [Elevanlabs UI](https://elevenlabs.io/blog/elevenlabs-ui) and [Vercel Sandbox](https://vercel.com/docs/vercel-sandbox) I think it's now a good time to build a second iteration of this application. 

Key points that I want it to have that v1 did not:
1. Beautiful, voice-driven UI
2. MVP - Minimal fluff, only code for voice-driven coding agents
3. Credit-based system
4. No free-tier
## MVP

> The MVP is what I personally want out of this, not what I think others may want.

User flow:
1. Login w/ Github giving access to repos
2. Start call with/without Github repo selected
	1. If not selected, generated code can be published to a new repository
3. Vercel Sandbox spawns with repository code with Claude Code
4. Voice Agent can:
	1. Send prompts to Claude Code
	2. Check status of Claude Code
	3. Trigger Pull Requests with latest code changes
	4. Spawn new conversations with fresh context
		1. This one may require a multi-agent architecture. The top-level agent can:
			1. Look into specific conversations. i.e. "Check the status of our changes relating to auth", the top-level agent will call a tool that finds the conversation relating to auth