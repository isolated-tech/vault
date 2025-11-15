---
Status: Not started
tags:
  - content
---
I launched Voicescript, Humanizers, Pullrequest, and Instareply and made ...

## Voicescri.pt

**Why:**
I want to be able to program completely handsfree.

Living out of an RV full-time, traveling around the western states of the United States with my wife. Long hours on the road made my mind wander often with fun ideas, and I wanted the ability to build them while driving. 

**How:**
OpenAI released their [realtime voice agent](https://openai.com/index/introducing-gpt-realtime/), allowing programmers to bring OpenAI's Voice Agent into their own application.

This + Claude Code's Github Action + Tools for out Voice Agent enabled my vision - completely hands free coding.

**Amount made:**
$0. I did some basic Reddit, Hackernews, and Youtube marketing but in the end, I only got a few hundred visitors and 0 sales.

**Where I went wrong:**
I believe the application had far too complicated of an onboarding.
1. Github OAuth + Repository permissions
2. OpenAI API Key for Voice Agent
3. Claude Code Max Subscription for Github Action
4. Github Action .yml file committed into codebase

These 4 steps are highly sensitive and technical. You must **really** want to use this application and I don't believe my landing page, docs, and onboarding did enough to convince users to do this.

**Future:**
I've recently learned how to cut the onboarding down significantly.

I'll still need Github permissions to get access to code if we want to push code to a user's Github. Just writing this makes me think even this step is optional - I can have the agent write code and only if the user wants the code to persist can we create the permissions needed to push to their repository.

The other steps can be completely eliminated now that I know how to run Claude Code in my own secure and private sandboxes. Instead, just opting for a simpler credit-based system that users can buy into.