# Claude Managed Agents: How to Deploy your First One Today

**Source:** Nick Spisak (@nickspisak_)  
**Date:** 2026-04-09  
**Link:** https://x.com/nickspisak_/status/2041949191887262164

**Note:** Article will be updated as we learn more and experiment. Updates as of 4.8.26 @ 5:12pm.

---

## Full Article

Anthropic just gave every developer a shortcut. Claude Managed Agents handles the infrastructure, sandboxing, and tool execution so you can ship production agents in days instead of months. It's in public beta right now on the Claude Platform.

In under 5 minutes you'll learn:
- What Managed Agents actually is and why it matters
- The 4 concepts you need to understand before you start
- How to deploy your first agent in under 10 minutes
- 6 real use cases companies "could" use it for
- The one command that gets you started from Claude Code

**Quick start:** Run "start onboarding for managed agents in Claude API" in Claude Code. The docs are a gold mine. You can upload all your skills, MCP servers, etc in the platform console. API usage only will be expensive.

---

## 1. What Managed Agents actually is

Right now, if you want Claude to do real work (run code, read files, browse the web, execute bash commands) you need to build the infrastructure yourself. Sandboxing, state management, error recovery, credential handling. That's months of engineering before your agent does anything useful.

Managed Agents is Anthropic saying: we'll handle all of that. You define what your agent does. They run it on their cloud infrastructure.

You get secure containers, long-running sessions that persist for hours, built-in tool execution, and event streaming. The agent can write code, run it, search the web, and edit files without you building any of that plumbing.

## 2. The 4 core concepts

Every Managed Agent runs on four building blocks:

1. **Agent** - Your configuration. The model (Claude Sonnet 4.6, Opus 4.6), the system prompt, the tools it can use, and any MCP servers it connects to. Create it once, reuse it across every session.

2. **Environment** - The container where your agent runs. Pre-install Python, Node.js, Go, whatever packages you need. Set networking rules. Each session gets its own isolated container.

3. **Session** - A running agent instance. It references your agent config and your environment, maintains conversation history, and persists files across interactions. Sessions can run for hours.

4. **Events** - Messages between your app and the agent. You send user messages in. Claude streams back responses, tool calls, and status updates via server-sent events.

That's it. Four concepts. Agent, environment, session, events.

## 3. How to deploy your first agent

You need an API key and three API calls. That's the whole setup.

**Step 1: Install the CLI**

The fastest path is Anthropic's new CLI tool called `ant`. Install it with Homebrew.

**Step 2: Create an agent**

One API call defines your agent's model, system prompt, and tools. The `agent_toolset_20260401` enables everything: bash, file read/write, web search, web fetch, grep, glob. All built in.

**Step 3: Create an environment**

```bash
curl https://api.anthropic.com/v1/environments \
  -d '{"name": "dev-env", "config": {"type": "cloud",
       "networking": {"type": "unrestricted"}}}'
```

You can pre-install packages here too. Need pandas and numpy? Add `"packages": {"pip": ["pandas", "numpy"]}` to the config.

**Step 4: Start a session and send work**

Create a session referencing your agent and environment, then send a message. Claude takes over from there. It decides which tools to use, executes them in the container, and streams results back to you.

The whole thing takes under 10 minutes. No Docker setup. No orchestration code. No tool execution layer.

## 4. What you can actually build with this today

Notion, Asana, Rakuten, Sentry, and Vibecode are already shipping on Managed Agents:

- **Coding agents** that clone a repo, read the codebase, plan a fix, write the code, run tests, and open a PR. Sentry's debugging tool Seer finds the bug, then a Claude agent writes the patch and opens the pull request.

- **Document processors** that take raw files, extract structured data, and output clean results. Finance teams at Rakuten use specialist agents for each department (product, sales, marketing, finance) each deployed in under a week.

- **Productivity agents** that join your project management tool and pick up tasks like a team member. Asana built AI Teammates on this exact infrastructure.

- **Data analysis agents** that take a CSV, write Python scripts on the fly, run them, and return insights. The environment comes with Python, Node.js, Go, and more pre-installed.

- **Internal tools** that answer any question by coding up the query on the fly. One company reported their agent can handle virtually any user query because it writes whatever tool it needs in the moment.

- **MCP-connected agents** that plug into your existing tools. Connect GitHub, Slack, your CRM, any MCP server. Managed Agents handles the auth through a vault system so secrets never touch your agent config.

## 5. The permission system you should know about

This matters if you're building for other people. Managed Agents has two permission modes:

- **always_allow** - Tools run automatically. Good for trusted, internal agents.
- **always_ask** - The session pauses and waits for your app to approve each tool call before executing. Good for anything user-facing.

You can mix them. Let the agent read files and search the web automatically, but require approval before it runs bash commands. That's one config change per tool.

MCP tools default to always_ask. Smart. You don't want a newly added third-party tool auto-executing without review.

**Hot take:** this permission system alone makes Managed Agents more production-ready than most open-source agent frameworks. LangGraph, CrewAI, AutoGen, none of them ship with per-tool permission scoping out of the box. You have to build it. Here, it's a config flag.

## 6. The fastest way to start right now

If you already use Claude Code, you don't even need to touch the API directly. Open Claude Code and say:

> "start onboarding for managed agents in Claude API"

Claude Code's built-in claude-api skill walks you through the setup. Or go to the Claude Console at platform.claude.com and use the visual agent builder. Configure your agent, test it inline, then copy the agent ID into your code.

**Pricing** is consumption-based. Standard Claude API token rates plus $0.08 per session-hour for active runtime. For context, a 10-minute coding agent session costs a few cents in compute.

---

## Summary

Nick Spisak walks through deploying Claude Managed Agents via the API in under 10 minutes using Anthropic's `ant` CLI tool. Four core concepts: Agent (config), Environment (container with pre-installed packages), Session (running instance), Events (messaging). Real-world adopters include Notion, Asana, Rakuten, Sentry, and Vibecode. The per-tool permission system (always_allow vs always_ask) is highlighted as a standout feature that most open-source frameworks lack out of the box. Pricing: standard token rates + $0.08/session-hour.

---

## Key Takeaways

1. **4 core concepts** — Agent (config), Environment (container), Session (running instance), Events (messaging)
2. **API-first deployment** — `ant` CLI + 3 API calls = agent live in under 10 minutes
3. **Pre-installed packages** — environment config supports pip, npm, etc. for instant stack setup
4. **Enterprise adopters** — Notion, Asana, Rakuten, Sentry, Vibecode already in production
5. **Per-tool permission scoping** — `always_allow` vs `always_ask` per tool; MCP tools default to `always_ask`
6. **Hot take** — permission system alone makes this more production-ready than LangGraph, CrewAI, AutoGen
7. **Pricing** — standard token rates + $0.08/session-hour; ~$0.02-0.05 per 10-min session
8. **Claude Code shortcut** — "start onboarding for managed agents in Claude API" kicks off setup automatically

---

## Hermes-Related Interest

The 4-layer vault architecture (Built-in Memory → Agents.md/Soul.md → Obsidian Vault → Session Search) maps directly to the Managed Agents 4 concepts. The per-tool permission model (always_allow vs always_ask) is directly applicable to Hermes — file writes, git pushes, and message sending could use always_ask mode while read-only operations use always_allow. The `ant` CLI approach (3 API calls = agent live) is conceptually similar to how a properly configured Hermes should be able to bootstrap a new project from context files.
