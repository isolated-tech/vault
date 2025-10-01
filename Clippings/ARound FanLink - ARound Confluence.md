---
title: "ARound FanLink - ARound Confluence"
source: "https://aroundar.atlassian.net/wiki/spaces/fanlink/pages/422150148/MatchState+API+Variables"
author:
published:
created: 2025-09-20
description:
tags:
  - "clippings"
---
## ✅ VARIABLES FROM GENIUS SPORTS (MATCHSTATE V1 / GAMEEVENT)

These are **directly ingested** from Genius and normalized via GameState or GameEvent.

<table><tbody><tr><th rowspan="1" colspan="1"><div><p><strong>Variable</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>✅ Definition</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>🎯 FanLink Use</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>💡 Example</strong></p><figure></figure></div></th></tr></tbody></table>

<table><tbody><tr><th rowspan="1" colspan="1"><div><p><strong>Variable</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>✅ Definition</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>🎯 FanLink Use</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>💡 Example</strong></p><figure></figure></div></th></tr><tr><td rowspan="1" colspan="1"><p>fixtureId</p></td><td rowspan="1" colspan="1"><p>Unique game ID</p></td><td rowspan="1" colspan="1"><p>Route all data/modules</p></td><td rowspan="1" colspan="1"><p>"abc123"</p></td></tr><tr><td rowspan="1" colspan="1"><p>period</p></td><td rowspan="1" colspan="1"><p>Current quarter</p></td><td rowspan="1" colspan="1"><p>Prompt tone, endgame logic</p></td><td rowspan="1" colspan="1"><p>4</p></td></tr><tr><td rowspan="1" colspan="1"><p>clock</p></td><td rowspan="1" colspan="1"><p>Time in quarter</p></td><td rowspan="1" colspan="1"><p>Commentary, sync, 2-minute logic</p></td><td rowspan="1" colspan="1"><p>"03:17"</p></td></tr><tr><td rowspan="1" colspan="1"><p>downNumber</p></td><td rowspan="1" colspan="1"><p>Current down</p></td><td rowspan="1" colspan="1"><p>Module triggers (3rd/4th down)</p></td><td rowspan="1" colspan="1"><p>3</p></td></tr><tr><td rowspan="1" colspan="1"><p>yardsToGo</p></td><td rowspan="1" colspan="1"><p>Yards to 1st</p></td><td rowspan="1" colspan="1"><p>Pressure context</p></td><td rowspan="1" colspan="1"><p>9</p></td></tr><tr><td rowspan="1" colspan="1"><p>scrimmageYard</p></td><td rowspan="1" colspan="1"><p>Yard line of play</p></td><td rowspan="1" colspan="1"><p>Field position logic</p></td><td rowspan="1" colspan="1"><p>42</p></td></tr><tr><td rowspan="1" colspan="1"><p>yardsToEndzone</p></td><td rowspan="1" colspan="1"><p>Distance to goal</p></td><td rowspan="1" colspan="1"><p>Red zone logic</p></td><td rowspan="1" colspan="1"><p>58</p></td></tr><tr><td rowspan="1" colspan="1"><p>score.home / score.away</p></td><td rowspan="1" colspan="1"><p>Current score</p></td><td rowspan="1" colspan="1"><p>Drives urgency, game state</p></td><td rowspan="1" colspan="1"><p>13-20</p></td></tr><tr><td rowspan="1" colspan="1"><p>possessionTeamId</p></td><td rowspan="1" colspan="1"><p>Team with ball</p></td><td rowspan="1" colspan="1"><p>Controls voice &amp; direction</p></td><td rowspan="1" colspan="1"><p>"home"</p></td></tr><tr><td rowspan="1" colspan="1"><p>timeoutsRemaining</p></td><td rowspan="1" colspan="1"><p>Per team</p></td><td rowspan="1" colspan="1"><p>Strategy-aware commentary</p></td><td rowspan="1" colspan="1"><p>{ home: 2, away: 1 }</p></td></tr><tr><td rowspan="1" colspan="1"><p>isPlayUnderReview</p></td><td rowspan="1" colspan="1"><p>Boolean flag</p></td><td rowspan="1" colspan="1"><p>Triggers trivia/sponsor fallback</p></td><td rowspan="1" colspan="1"><p>true</p></td></tr><tr><td rowspan="1" colspan="1"><p>eventId</p></td><td rowspan="1" colspan="1"><p>Unique per play</p></td><td rowspan="1" colspan="1"><p>Deduplication, traceability</p></td><td rowspan="1" colspan="1"><p>"evt-4567"</p></td></tr><tr><td rowspan="1" colspan="1"><p>timestampUtc</p></td><td rowspan="1" colspan="1"><p>UTC of event</p></td><td rowspan="1" colspan="1"><p>Ordering, sync, logs</p></td><td rowspan="1" colspan="1"><p>"2025-09-18T20:15:30Z"</p></td></tr><tr><td rowspan="1" colspan="1"><p>type</p></td><td rowspan="1" colspan="1"><p>Event type (touchdown, pass_complete, etc.)</p></td><td rowspan="1" colspan="1"><p>Used in moment detection</p></td><td rowspan="1" colspan="1"><p>"touchdown"</p></td></tr><tr><td rowspan="1" colspan="1"><p>result.yards</p></td><td rowspan="1" colspan="1"><p>Yards gained</p></td><td rowspan="1" colspan="1"><p>Commentary tone/milestones</p></td><td rowspan="1" colspan="1"><p>12</p></td></tr><tr><td rowspan="1" colspan="1"><p>result.outcome</p></td><td rowspan="1" colspan="1"><p>Play result (first_down, no_gain)</p></td><td rowspan="1" colspan="1"><p>Summary or stat trigger</p></td><td rowspan="1" colspan="1"><p>"first_down"</p></td></tr><tr><td rowspan="1" colspan="1"><p>players[]</p></td><td rowspan="1" colspan="1"><p>Players involved</p></td><td rowspan="1" colspan="1"><p>Stat highlights, name refs</p></td><td rowspan="1" colspan="1"><p>[<span><span><span>QB</span></span></span> Joe, <span><span><span>WR</span></span></span> Max]</p></td></tr></tbody></table>

---

## ➕ FANLINK-ADDED VARIABLES (DERIVED OR ATTACHED)

These are **added by FanLink** via internal logic: context graph, module engine, config.

<table><tbody><tr><th rowspan="1" colspan="1"><div><p><strong>Variable</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>➕ Source</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>✅ Definition</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>🎯 Use</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>💡 Example</strong></p><figure></figure></div></th></tr></tbody></table>

<table><tbody><tr><th rowspan="1" colspan="1"><div><p><strong>Variable</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>➕ Source</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>✅ Definition</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>🎯 Use</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>💡 Example</strong></p><figure></figure></div></th></tr><tr><td rowspan="1" colspan="1"><p>teamPossession</p></td><td rowspan="1" colspan="1"><p>Derived</p></td><td rowspan="1" colspan="1"><p>"home" or "away"shorthand</p></td><td rowspan="1" colspan="1"><p>Simplifies voice logic</p></td><td rowspan="1" colspan="1"><p>"home"</p></td></tr><tr><td rowspan="1" colspan="1"><p>tone</p></td><td rowspan="1" colspan="1"><p>AltCast + system config</p></td><td rowspan="1" colspan="1"><p>Style of commentary</p></td><td rowspan="1" colspan="1"><p>Adjusts language and verbs</p></td><td rowspan="1" colspan="1"><p>"hype"</p></td></tr><tr><td rowspan="1" colspan="1"><p>altCast</p></td><td rowspan="1" colspan="1"><p>Stream config</p></td><td rowspan="1" colspan="1"><p>Stream mode override</p></td><td rowspan="1" colspan="1"><p>Changes tone: "coachMode"</p></td><td rowspan="1" colspan="1"><p>"fanMode"</p></td></tr><tr><td rowspan="1" colspan="1"><p>videoDelayOffset</p></td><td rowspan="1" colspan="1"><p>Config</p></td><td rowspan="1" colspan="1"><p>Delay between stream &amp; data</p></td><td rowspan="1" colspan="1"><p>Sync render to video</p></td><td rowspan="1" colspan="1"><p>7 seconds</p></td></tr><tr><td rowspan="1" colspan="1"><p>momentTags[]</p></td><td rowspan="1" colspan="1"><p>Context Graph</p></td><td rowspan="1" colspan="1"><p>Tags like red_zone, fourth_down</p></td><td rowspan="1" colspan="1"><p>Triggers specific modules</p></td><td rowspan="1" colspan="1"><p>["red_zone"]</p></td></tr><tr><td rowspan="1" colspan="1"><p>momentHash</p></td><td rowspan="1" colspan="1"><p>FanLink hash</p></td><td rowspan="1" colspan="1"><p>Unique play fingerprint</p></td><td rowspan="1" colspan="1"><p>Avoid duplicate commentary</p></td><td rowspan="1" colspan="1"><p>"P4-D3-YTG9-YL42"</p></td></tr><tr><td rowspan="1" colspan="1"><p>promptId</p></td><td rowspan="1" colspan="1"><p>LangSmith registry</p></td><td rowspan="1" colspan="1"><p>Prompt template used</p></td><td rowspan="1" colspan="1"><p>QA, version trace</p></td><td rowspan="1" colspan="1"><p>"fanlink.commentary.v1"</p></td></tr><tr><td rowspan="1" colspan="1"><p>promptVersion</p></td><td rowspan="1" colspan="1"><p>LangSmith</p></td><td rowspan="1" colspan="1"><p>Prompt version (semver)</p></td><td rowspan="1" colspan="1"><p>Output tracking</p></td><td rowspan="1" colspan="1"><p>"1.3.0"</p></td></tr><tr><td rowspan="1" colspan="1"><p>moduleId</p></td><td rowspan="1" colspan="1"><p>UUID</p></td><td rowspan="1" colspan="1"><p>Module instance ID</p></td><td rowspan="1" colspan="1"><p><span><span><span>MQTT</span></span></span> + logs</p></td><td rowspan="1" colspan="1"><p>"cmtry-xyz789"</p></td></tr><tr><td rowspan="1" colspan="1"><p>moduleType</p></td><td rowspan="1" colspan="1"><p>Trigger rule</p></td><td rowspan="1" colspan="1"><p>Commentary, poll, trivia, etc.</p></td><td rowspan="1" colspan="1"><p>Renders correct UI</p></td><td rowspan="1" colspan="1"><p>"commentary"</p></td></tr><tr><td rowspan="1" colspan="1"><p>renderWindow</p></td><td rowspan="1" colspan="1"><p>UI config</p></td><td rowspan="1" colspan="1"><p>Time (sec) module should live</p></td><td rowspan="1" colspan="1"><p>Expiry and fade-out</p></td><td rowspan="1" colspan="1"><p>15</p></td></tr><tr><td rowspan="1" colspan="1"><p>sponsor</p></td><td rowspan="1" colspan="1"><p>Attached from <span><span><span>CMS</span></span></span> or event</p></td><td rowspan="1" colspan="1"><p>Active sponsor, if any</p></td><td rowspan="1" colspan="1"><p>Branding + tone modifiers</p></td><td rowspan="1" colspan="1"><p>"UnderArmour"</p></td></tr></tbody></table>

---

## 🔄 MAPPING SUMMARY

<table><tbody><tr><th rowspan="1" colspan="1"><div><p><strong>Category</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>Fields</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>Source</strong></p><figure></figure></div></th></tr></tbody></table>

<table><tbody><tr><th rowspan="1" colspan="1"><div><p><strong>Category</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>Fields</strong></p><figure></figure></div></th><th rowspan="1" colspan="1"><div><p><strong>Source</strong></p><figure></figure></div></th></tr><tr><td rowspan="1" colspan="1"><p><strong>Live Game Data</strong></p></td><td rowspan="1" colspan="1"><p>downNumber, yardsToGo, score, possessionTeamId, clock, period, etc.</p></td><td rowspan="1" colspan="1"><p>✅ Genius Sports</p></td></tr><tr><td rowspan="1" colspan="1"><p><strong>Game Events</strong></p></td><td rowspan="1" colspan="1"><p>eventId, type, result, players[], timestampUtc</p></td><td rowspan="1" colspan="1"><p>✅ Genius Sports</p></td></tr><tr><td rowspan="1" colspan="1"><p><strong>Moment Context</strong></p></td><td rowspan="1" colspan="1"><p>momentTags, momentHash, teamPossession</p></td><td rowspan="1" colspan="1"><p>➕ FanLink (Context Graph)</p></td></tr><tr><td rowspan="1" colspan="1"><p><strong>Prompt Metadata</strong></p></td><td rowspan="1" colspan="1"><p>promptId, promptVersion, tone, altCast</p></td><td rowspan="1" colspan="1"><p>➕ FanLink (LangSmith/Prompt Engine)</p></td></tr><tr><td rowspan="1" colspan="1"><p><strong>Delivery Metadata</strong></p></td><td rowspan="1" colspan="1"><p>moduleId, moduleType, renderWindow, videoDelayOffset, sponsor</p></td><td rowspan="1" colspan="1"><p>➕ FanLink (Content Server + <span>CMS</span>)</p></td></tr></tbody></table>

Here is the **updated and complete list of variables FanLink should track and ingest** from **MatchState V1** into the **prompt context pipeline** and **module sync layer**.

It covers 3 layers:

1. ✅ **Prompt Context** – Variables passed to LangChain/LangSmith prompts
2. 🔁 **Sync & Timing** – Used for sequencing, deduping, render timing
3. 🎛️ **Operational Context** – For cooldown logic, fallback triggers, validation

---

## ✅ Prompt Context Variables (For AI Modules)

Used directly to generate **commentary, polls, stat highlights, trivia**.

`{   "fixtureId": "string",   "period": 1-4 or OT,   "clock": "MM:SS",   "downNumber": 1–4,   "yardsToGo": int,   "scrimmageYard": int,   "yardsToEndzone": int,   "score": {     "home": int,     "away": int   },   "possessionTeamId": "string",   "isPlayUnderReview": boolean,   "timeoutsRemaining": {     "home": int,     "away": int   },   "teamPossession": "home" | "away" | null,   "tone": "hype" | "chill" | "coach" | "standard" | "alt-cast",   "altCast": "fanMode" | "coachMode" | "broadcasterDefault" }`

Optional enrichments (if Stats V1 is available):

`{   "player": "string",   "statName": "string",   "statValue": number,   "team": "string" }`

---

## 🔁 Sync & Timing Variables (For Real-Time Delivery)

Used to **synchronize**, **de-dupe**, and **log module behavior**.

`{   "eventId": "string",                 // Unique per GameEvent   "timestampUtc": "ISO-8601",         // When the event happened   "videoDelayOffset": number,         // In seconds (e.g., 7)   "momentHash": "string",             // e.g., "P4-D3-YTG9-YL42"   "promptId": "string",               // LangSmith prompt template ID   "promptVersion": "semver",          // "1.2.0"   "moduleId": "uuid",                 // UUID of generated module   "renderWindow": number              // in seconds, e.g. 15 }`

---

## 🎛️ Operational & Context Tags (For Trigger Logic)

Used internally for **moment detection**, **cooldowns**, and module routing.

`{   "momentTags": [     "third_and_long",     "fourth_down",     "red_zone",     "scoring_play",     "turnover",     "two_minute_drill",     "under_review",     "milestone_alert"   ],   "contextSource": "MatchStateV1",   "triggerType": "GameEvent" | "GameState",   "moduleType": "commentary" | "poll" | "trivia" | "stat",   "sponsor": "string"  // Optional; used in rendering + tone }`

---

## 🧱 Final Structure (Flattened for LangChain input schema)

Here’s what a **flattened version** might look like for prompt injection:

`{   "fixtureId": "abc123",   "period": 4,   "clock": "03:17",   "down": 3,   "yardsToGo": 9,   "scrimmageYard": 42,   "yardsToEndzone": 58,   "scoreHome": 13,   "scoreAway": 20,   "possessionTeam": "home",   "timeoutsRemainingHome": 2,   "timeoutsRemainingAway": 1,   "isPlayUnderReview": false,   "tone": "hype",   "altCast": "coachMode",   "eventId": "evt-4567",   "timestampUtc": "2025-09-18T20:15:30Z",   "videoDelayOffset": 7,   "momentTags": ["third_and_long"],   "promptId": "fanlink.commentary.v1",   "promptVersion": "1.3.0",   "moduleType": "commentary",   "moduleId": "cmtry-xyz789",   "renderWindow": 15,   "sponsor": "UnderArmour" }`

---

Let me know if you want:

- YAML schema for validation
- LangChain input schema for all module types
- JSON Schema validator snippet for matchState ingestion

0