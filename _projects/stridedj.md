---
layout: page
title: "StrideDJ: A Tool-Calling Running Agent"
description: AI Engineering · 2026
importance: 1
category: Personal
---

StrideDJ is a running assistant in a Telegram chat. You write what you want to run, such as _"10k Z2 tonight"_ or _"intervals tomorrow evening"_. It estimates how long the run will take from your own Garmin history, finds a free time in your Google Calendar and puts together a Spotify playlist whose tempo matches your running cadence. You get a proposal with an Approve button, and the calendar event and the playlist are only created when you tap it.

[![Architecture of StrideDJ](/assets/img/stridedj-architecture.svg){: .img-fluid .rounded }](/assets/img/stridedj-architecture.svg)

### How it works

A language model (OpenAI's Responses API) interprets your message and plans the run with eight read-only tools, for example to estimate the duration, find free slots, suggest interval sessions or draft a playlist. Ordinary code does everything that has to be exact or safe: it fills in the numbers, checks the model's answer against the plan and, after you approve, creates the calendar event and the playlist. The model itself cannot write anything.

The model only sees aggregated numbers, never GPS data, song titles or calendar event titles. Titles are written by other people and could contain hidden instructions (prompt injection), so they never reach the model.

### Components

- **Durations** from your own comparable runs, or from a personal log-log model (Riegel's law) for distances you haven't run recently. The calendar slot is sized so that at least 4 out of 5 runs fit.
- **Interval sessions** detected in per-second Garmin data, with target paces that adapt after each session.
- **Playlists** from your own library, tempo-matched to your cadence and filtered by a style model learned from your running music.
- **Evals:** 45 scripted conversations, including prompt-injection attacks, graded by code.

The [documentation on GitHub](https://github.com/szekerbalazs/stridedj/tree/main/docs) covers the architecture, the agent harness, the evals and the threat model in detail.

[Code on GitHub](https://github.com/szekerbalazs/stridedj)
