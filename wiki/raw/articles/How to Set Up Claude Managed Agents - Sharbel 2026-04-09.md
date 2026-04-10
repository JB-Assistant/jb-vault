# How to Set Up Claude Managed Agents in Under 10 Minutes

**Source:** Sharbel (@sharbel)  
**Date:** 2026-04-09  
**Link:** https://x.com/sharbel/status/2042270482712412258

---

## Full Article

Anthropic just shipped something that changes the entire agent game. Go to platform.claude.com right now. You'll see a dashboard with one question: "What do you want to build?" Type a description. Or pick a template. Your agent is live in 4 steps. No infrastructure. No code. No DevOps. Just a dashboard.

### What Claude Managed Agents actually is

Before yesterday, building an AI agent meant months of engineering. You needed an agent loop, tool execution, sandboxing, state management, error recovery. Most teams never shipped. Managed Agents handles all of that. You define what the agent does. Anthropic runs everything else. Your agent gets its own sandboxed container in the cloud. It can run bash commands, read and write files, search the web, fetch URLs, and execute code. It survives disconnects. It recovers from failures automatically. And it launched in public beta yesterday. For everyone.

### Step 1: Create your agent

Go to platform.claude.com. You'll see two options:

**Option A: Pick a template.** Anthropic ships 10+ pre-built agent templates:
- Deep researcher - multi-step web research with source synthesis and citations
- Support agent - answers customer questions from your docs and knowledge base
- Data analyst - load, explore, and visualize data, build reports
- Incident commander - triages a Sentry alert, opens a Linear ticket, runs the Slack war room
- Feedback miner - clusters raw feedback from Slack and Notion into themes
- Field monitor - scans software blogs for a topic and writes a weekly brief
- Structured extractor - parses unstructured text into typed JSON
- Sprint retro facilitator - pulls a closed sprint from Linear, synthesizes themes, writes the retro doc

Pick one. It comes pre-configured with the right model, tools, and system prompt.

**Option B: Describe what you want.** Type a plain-English description: "An agent that monitors my competitors' pricing pages daily and sends me a Slack summary of any changes." Claude builds the agent config for you.

Either way, you'll land on the agent setup screen where you configure:
- Model - Claude Sonnet 4.6 for speed, Opus 4.6 for complex reasoning
- System prompt - what the agent knows and how it behaves
- Tools - bash, file operations, web search, web fetch, grep, glob (all on by default)
- MCP servers - connect external tools like Slack, Linear, GitHub, Notion
- Skills - pre-built workflows for xlsx, pptx, docx, and pdf files

### Step 2: Configure the environment

This is the container your agent runs in. Set up:
- Packages - pre-install anything: Python libraries (pandas, numpy), Node packages, system tools (ffmpeg, imagemagick), even Rust or Go modules
- Networking - unrestricted by default, or lock it down to specific domains
- File mounts - give your agent access to specific files or datasets

The packages get cached. Every new session starts with them already installed. No waiting.

### Step 3: Start a session

Hit start. Your agent is now live in its own sandboxed container on Anthropic's cloud. Send it a message. Watch it think, decide which tools to use, execute commands, and stream results back to you in real time.

A few things most people won't realize:
- Sessions survive disconnects. Close your laptop. Come back tomorrow. The agent kept working. You'll see everything it did.
- Built-in prompt caching. Context management happens automatically. Cache hits cost 10x less.
- Checkpointing. If the container fails, the agent recovers from its last checkpoint. No lost work.

### Step 4: Integrate

Once your agent works, deploy it:
- Copy the agent ID and embed it in your product via the API
- Connect it to webhooks so it triggers on events
- Use the SDK (Python, TypeScript, Java, Go, C#, Ruby, PHP) to build a custom frontend
- Or just keep using it from the console

Anthropic gives you full session tracing in the dashboard. Every tool call, every decision, every failure. You can debug production agents without guessing.

### What this costs

Three things:
- Session runtime: $0.08 per hour. Metered to the millisecond. Idle time is free.
- Tokens: Standard Claude pricing. Sonnet = $3/M input, $15/M output.
- Web search: $10 per 1,000 searches.

Real numbers: a 20-minute coding session costs about $0.40. A customer support agent handling a ticket in 3 minutes costs $0.05. For context: the engineering time to build this infrastructure yourself would cost you months and six figures minimum.

---

## Summary

Anthropic launched Managed Agents in public beta — a fully hosted agent platform where you define what the agent does and Anthropic handles the entire infrastructure: sandboxed containers, tool execution, session persistence, checkpointing, and error recovery. You can start from a template (10+ options covering research, support, data analysis, incident response, etc.) or describe your agent in plain English. The four-step setup (create, configure environment, start session, integrate via API/webhooks/SDK) is designed to get agents live in minutes. Pricing is pay-per-use at $0.08/hr runtime plus token costs, making it accessible to individuals and teams who can't justify building this infrastructure from scratch.

---

## Key Takeaways

1. **No-code agent deployment** — platform.claude.com lets anyone spin up a working AI agent in minutes without managing infrastructure
2. **10+ pre-built templates** — deep researcher, support agent, data analyst, incident commander, feedback miner, field monitor, structured extractor, sprint retro facilitator, and more
3. **Plain-English agent creation** — describe what you want and Claude builds the config automatically
4. **Session persistence & checkpointing** — agents survive disconnects and recover from failures automatically
5. **MCP server integration** — connect Slack, Linear, GitHub, Notion and other tools out of the box
6. **SDK support** — Python, TypeScript, Java, Go, C#, Ruby, PHP for custom frontend integration
7. **Competitive pricing** — ~$0.40 for a 20-minute coding session, ~$0.05 per support ticket; months of engineering equivalent for cents
8. **Public beta now available** — launched yesterday for everyone

---

## Hermes-Related Interest

This is directly relevant to Hermes/agent workflows. The managed agents platform is essentially what a production Claude Code setup could evolve into — hosted execution, session persistence, and built-in tool scaffolding. The plain-English agent description feature (Option B) is conceptually similar to how Hermes interprets user tasks. The MCP server integration pattern (connecting to Slack, Linear, GitHub) is exactly the kind of external toolchain integration that could enhance Hermes's capabilities. Worth watching as Anthropic iterates on this platform.
