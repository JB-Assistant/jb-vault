---
title: Claude Managed Agents
created: 2026-04-09
updated: 2026-04-09
type: entity
tags: [claude-managed-agents, anthropic, platform, agentic-ai]
sources: [raw/articles/how-to-set-up-claude-managed-agents-sharbel-2026-04-09.md, raw/articles/ultimate-beginners-guide-claude-managed-agents-corey-ganem-2026-04-09.md, raw/articles/claude-managed-agents-how-to-deploy-nick-spisak-2026-04-09.md]
---

# Claude Managed Agents

## Overview
Anthropic's hosted agent platform that handles all infrastructure (sandboxing, tool execution, session persistence, checkpointing, error recovery) so developers can deploy production AI agents by describing what they want — no DevOps required. Public beta launched April 2026.

## Key Facts
- **Launched:** April 2026 (public beta)
- **Platform:** platform.claude.com
- **CLI tool:** `ant` (installed via Homebrew)
- **Pricing:** $0.08/session-hour + standard token rates; ~$0.02-0.05 per 10-minute session

## 4 Core Concepts

### Agent
Configuration defining model (Sonnet 4.6 for speed, Opus 4.6 for reasoning), system prompt, available tools, and MCP server connections. Created once, reused across sessions.

### Environment
The container where the agent runs. Pre-install packages via pip, npm, etc. Set networking rules (unrestricted or domain-locked). Each session gets its own isolated container. Packages cached — new sessions start with everything pre-installed.

### Session
A running agent instance. Maintains conversation history, persists files across interactions. Survives disconnects — close your laptop, come back later, the agent kept working. Checkpointing means container failures auto-recover from last checkpoint.

### Events
Messaging between app and agent via server-sent events. User sends messages in; Claude streams back responses, tool calls, and status updates.

## Tools (Built-in)
All enabled via `agent_toolset_20260401`:
- bash/file read/write
- web search and fetch
- grep and glob

## MCP Integration
Connect external tools (GitHub, Slack, Linear, Notion, CRM) via MCP servers. Auth handled through Anthropic's vault system — secrets never touch agent config. MCP tools default to `always_ask` permission.

## Permission System
Per-tool permission scoping — a standout feature compared to open-source frameworks:

| Mode | Behavior | Use Case |
|------|----------|----------|
| `always_allow` | Tool runs automatically | Trusted internal agents |
| `always_ask` | Pauses, waits for approval | User-facing, sensitive actions |

Can mix per tool: auto-run file reads + web search, approval-required for bash and email sends.

> **Hot take (Nick Spisak):** Per-tool permission scoping alone makes Managed Agents more production-ready than LangGraph, CrewAI, and AutoGen — none ship with this out of the box.

## Templates (10+ Pre-built)
- Deep researcher
- Support agent
- Data analyst
- Incident commander
- Feedback miner
- Field monitor
- Structured extractor
- Sprint retro facilitator

## Real-World Adopters
Notion, Asana, Rakuten, Sentry, Vibecode — all shipping production agents on Managed Agents.

## Business Model Angle
Barrier to entry for AI services business dropped from "hire a dev team" to "describe the problem." Service pricing: $1,500-5,000 setup + $500/month recurring.

## Related
[[claude-managed-agents-vs-other-frameworks]] | [[4-layer-memory-architecture]] | [[plain-text-persistence]] | [[per-tool-permissions]]
