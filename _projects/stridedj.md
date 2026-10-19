---
layout: page
title: "StrideDJ: A Tool-Calling Running Agent"
description: AI Engineering · 2026
importance: 1
category: Personal
---

StrideDJ is a running agent you message on Telegram. Text it something like _"10k Z2 tonight"_, and it estimates how long the run will take from your own Garmin history, finds a free slot in your Google Calendar and builds a Spotify playlist matched to your cadence. Nothing is booked until you approve the proposal.

- **Harness:** a tool-calling agent on the OpenAI Responses API in a hand-built harness, without an agent framework. Messages pass deterministic checks before the model sees them, the six read-only tools have strict JSON schemas, and every run has budgets for steps, tool calls, cost and time.
- **Approval and execution:** the model can only read. Its proposals are checked against the plans the tools actually created, approval tokens are bound to the plan's content hash, and a separate executor writes the calendar event and the playlist exactly once.
- **Prompt-injection defence:** untrusted text such as song titles and calendar invites never enters the model's context, and the model has no write channel.
- **Modelling:** run durations come from comparable personal runs, with a personal Riegel-law fit (log-log regression) for distances without recent data. The calendar slot uses the 80th percentile plus a buffer, and track tempos are folded (½×, 1×, 2×) to the cadence target.
- **Evals:** 32 tasks in regression, capability and security suites, graded programmatically on outcomes, with a reference solution for every task and pass@k and pass^k metrics. All suites pass, and none of the 18 attack attempts succeeds.

[Code on GitHub](https://github.com/szekerbalazs/stridedj)
