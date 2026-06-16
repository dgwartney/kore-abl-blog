---
title: "Welcome to the ABL Developer Blog"
date: 2026-06-16 09:00:00 -0700
categories: [ABL, Announcements]
tags: [abl, kore-ai, agents, getting-started]
---

Agent Blueprint Language (ABL) is the declarative language at the heart of the Kore AI Agent Platform (Artemis). If you've spent time building agents with it — or are just getting started — this blog is for you.

## What This Blog Covers

This isn't a rehash of the [ABL Developer Guide](https://github.com/dgwartney/kore-abl-developer-guide). That's the reference. This is where the field notes go: patterns that emerge from real projects, edge cases the spec glosses over, and design decisions worth thinking through out loud.

Topics you can expect:

- **Language patterns** — idiomatic ABL: when to use `decision` vs. `pipeline`, how to structure tool chains, guard clause patterns for intent routing
- **Tool & MCP integration** — connecting agents to real systems, handling auth, rate limits, and partial failures
- **Multi-agent orchestration** — supervisor agents, adaptive networks, handoff design, and avoiding the "telephone game" problem
- **Memory & state** — ephemeral vs. persistent memory, when state belongs in the agent vs. the tool vs. the caller
- **Safety & guardrails** — output validation, scope limiting, graceful degradation
- **Testing & debugging** — observable agents, transcript analysis, eval harnesses

## The Reference, Alongside the Practice

Good language documentation tells you what's possible. This blog tries to tell you what's worth doing — and occasionally what to avoid. The ABL Developer Guide lives next door; these posts assume you have it open.

Posts drop whenever there's something worth sharing. If you have a pattern, war story, or question worth exploring, the [GitHub repo](https://github.com/dgwartney/kore-abl-blog) is open.
