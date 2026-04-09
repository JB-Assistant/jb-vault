# Claude Managed Agents: How to Deploy your First One Today

**Source:** Nick Spisak @NickSpisak_  
**Date:** April 09, 2026  
**Link:** https://x.com/nickspisak_/status/2041949191887262164

---

## Full Article

** Article will be updated as we learn more and experiment ** Updates as of 4.8.26 @ 5:12pm --> Run "start onboarding for managed agents in Claude API" in claude code --> the docs are a gold mine --> can upload all your skills, mcp servers, etc in the platform console --> API usage only will be expensive

Anthropic just gave every developer a shortcut. Claude Managed Agents handles the infrastructure, sandboxing, and tool execution so you can ship production agents in days instead of months. It's in public beta right now on the Claude Platform.

In under 5 minutes you'll learn:
- What Managed Agents actually is and why it matters
- The 4 concepts you need to understand before you start
- How to deploy your first agent in under 10 minutes
- 6 real use cases companies "could" use it for
- The one command that gets you started from Claude Code

---

### 1. What Managed Agents actually is

Think of it this way. Right now, if you want Claude to do real work (run code, read files, browse the web, execute bash commands) you need to build the infrastructure yourself. Sandboxing, state management, error recovery, credential handling. That's months of engineering before your agent does anything useful.

Managed Agents is Anthropic saying: we'll handle all of that. You define what your agent does. They run it on their cloud infrastructure. You get secure containers, long-running sessions that persist for hours, built-in tool execution, and event streaming. The agent can write code, run it, search the web, and edit files without you building any of that plumbing.

---

### 2. The 4 core concepts

Every Managed Agent runs on four building blocks:

**Agent** - Your configuration. The model (Claude Sonnet 4.6, Opus 4.6), the system prompt, the tools it can use, and any MCP servers it connects to. Create it once, reuse it across every session.

**Environment** - The container where your agent runs. Pre-install Python, Node.js, Go, whatever packages you need. Set networking rules. Each session gets its own isolated container.

**Session** - A running agent instance. It references your agent config and your environment, maintains conversation history, and persists files across interactions. Sessions can run for hours.

**Events** - Messages between your app and the agent. You send user messages in. Claude streams back responses, tool calls, and status updates via server-sent events.

That's it. Four concepts. Agent, environment, session, events.

---

### 3. How to deploy your first agent

You need an API key and three API calls. That's the whole setup.

**Step 1: Install the CLI**

```bash
brew install anthropic-cli
ant --version
```

**Step 2: Create an agent**

```bash
curl https://api.anthropic.com/v1/agents \
  -H "x-api-key: $ANTHROPIC_API_KEY" \
  -H "anthropic-beta: managed-agents-2026-04-01" \
  -d '{"name": "My Agent", "model": "claude-sonnet-4-6", "tools": [{"type": "agent_toolset_20260401"}]}'
```

That agent_toolset_20260401 enables everything: bash, file read/write, web search, web fetch, grep, glob. All built in.

**Step 3: Create an environment**

```bash
curl https://api.anthropic.com/v1/environments \
  -d '{"name": "dev-env", "config": {"type": "cloud", "networking": {"type": "unrestricted"}}}'
```

You can pre-install packages here too. Need pandas and numpy? Add "packages": {"pip": ["pandas", "numpy"]} to the config.

**Step 4: Start a session and send work**

Create a session referencing your agent and environment, then send a message. Claude takes over from there. It decides which tools to use, executes them in the container, and streams results back to you.

The whole thing takes under 10 minutes. No Docker setup. No orchestration code. No tool execution layer.

---

### 4. What you can actually build with this today

Notion, Asana, Rakuten, Sentry, and Vibecode are already shipping on Managed Agents. Here's what the use cases look like for the rest of us:

**Coding agents** - Clone a repo, read the codebase, plan a fix, write the code, run tests, and open a PR. Sentry does exactly this. Their debugging tool Seer finds the bug, then a Claude agent writes the patch and opens the pull request.

**Document processors** - Take raw files, extract structured data, and output clean results. Finance teams at Rakuten use specialist agents for each department (product, sales, marketing, finance) each deployed in under a week.

**Productivity agents** - Join your project management tool and pick up tasks like a team member. Asana built AI Teammates on this exact infrastructure. The agent works inside Asana alongside humans.

**Data analysis agents** - Take a CSV, write Python scripts on the fly, run them, and return insights. The environment comes with Python, Node.js, Go, and more pre-installed.

**Internal tools** - Answer any question about your codebase, docs, or internal systems. A living knowledge base that actually works.

---

## Summary

Claude Managed Agents is Anthropic's new beta service that handles all the infrastructure headache of deploying AI agents — sandboxing, tool execution, session management, file persistence — so developers can focus purely on defining what their agent does. It runs on four concepts: Agent (config), Environment (container), Session (running instance), and Events (messaging). With just three API calls and under 10 minutes, you can have a production agent running that can write/execute code, browse the web, and handle files. Companies like Sentry, Notion, Asana, and Rakuten are already shipping on this — from autonomous coding agents that open PRs to finance specialist agents per department.

## Key Takeaways

1. **Managed Agents = infrastructure handled by Anthropic** — sandboxing, containers, tool execution, session persistence all built-in
2. **4 core concepts only** — Agent (config), Environment (container), Session (instance), Events (messaging)
3. **Deploy in <10 minutes with 3 API calls** — no Docker, no orchestration code
4. **Built-in toolset** — bash, file read/write, web search, web fetch, grep, glob all included
5. **Long-running sessions** — persists for hours, maintains conversation history
6. **Pre-install packages** — need pandas/numpy? Add to environment config
7. **Real companies already shipping** — Sentry (debugging → PR), Asana (AI Teammates), Rakuten (finance agents per department), Notion, Vibecode
8. **Public beta** — available now on Claude Platform, API usage billing only

## Hermes-Related Interest

This is directly relevant to Hermes:

- **Similar architecture** — Hermes also runs agents (via delegate_task), manages tool execution, sandboxing, and session persistence. Anthropic's approach validates the "agent = config + environment + session + events" model
- **MCP servers integration** — Managed Agents supports MCP servers, just like Hermes's skill system. The article mentions uploading skills and MCP servers in the platform console
- **Tool execution layer** — This is exactly what Hermes does with its function calling and tool execution. The article's "no tool execution layer needed" for Claude mirrors Hermes's built-in tools
- **Autonomous coding agents** — The Sentry example (find bug → write patch → open PR) is exactly what Hermes can do with the `github-pr-workflow` skill and subagent delegation
- **Multi-agent orchestration** — The Rakuten use case (specialist agents per department) mirrors Hermes's approach of spawning specialized subagents for different tasks
- **Event streaming** — Managed Agents use server-sent events for real-time streaming. Hermes could leverage this pattern for cron job output delivery
