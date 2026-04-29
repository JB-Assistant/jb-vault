---
title: Agentic Backend
created: 2026-04-29
updated: 2026-04-29
type: concept
tags: [ai-agents, backend, harness, infrastructure, workers, triggers, functions]
sources: [raw/articles/The Harness Is the Backend - X 2026-04-29.md]
---

# Agentic Backend

An agentic backend treats agents as first-class backend participants instead of separate harness processes that call into backend services. Agents, services, queues, state handlers, cron jobs, sandboxes, and edge devices share common primitives.

## Primitive Model

- **Worker:** any process/device/runtime that connects to the system and registers capabilities.
- **Function:** a stable unit of work with an identifier, input, and optional output.
- **Trigger:** the event, schedule, HTTP call, queue message, or state change that invokes a function.

## Why It Matters

- Agents can discover live system capabilities instead of relying on stale context.
- Agent tool calls and backend work share traces/logs/observability.
- New capabilities can be added as workers without redefining architecture.
- Thin vs thick harness becomes a composition choice, not a separate platform choice.

## Related

[[agent-harness]] | [[mike-piccolo]] | [[iii-dev]] | [[hermes]]
