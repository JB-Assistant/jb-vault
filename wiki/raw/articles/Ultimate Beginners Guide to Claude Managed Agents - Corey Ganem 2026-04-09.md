# Ultimate Beginners Guide to Claude Managed Agents

**Source:** Corey Ganem (@coreyganim)  
**Date:** 2026-04-09  
**Link:** https://x.com/coreyganim/status/2042286607449874527

---

## Full Article

Most people saw Anthropic announce Claude Managed Agents yesterday and immediately tuned out. Too technical. Not for me.
Wrong.
This is the single biggest unlock for anyone who wants to sell AI services to businesses (or agentify your existing business).

And you don't need to be a developer to understand why.

Here's what it actually means, why it matters for your business, and how to get started even if you've never written a line of code.

PS: I made a Google Doc that walks Claude Code through deploying your first managed agent step by step. Hand it to Claude Code. It does the rest. Grab it here: return-my-time.kit.com/2872b904f5

---

## What Claude Managed Agents Actually Is (In Plain English)

Think of it like this: until yesterday, building a custom AI agent that could actually do real work for a client (read their emails, update their CRM, generate reports, send follow-ups) required you to set up servers, manage security, handle errors, and deal with infrastructure.

That's months of engineering work before your agent does anything useful.

Managed Agents is Anthropic saying: "We'll handle all of that. You just tell the agent what to do."

You define the job. They run it on their cloud. The agent gets a secure workspace where it can write code, search the web, read files, and connect to tools. All without you building any of the plumbing.

## Why Non-Technical People Should Care

This changes the math on starting an AI services business.

**Before Managed Agents:**
- Need to understand technical infrastructure
- Need to manage servers and security
- Extensive setup before you can sell anything

**After Managed Agents:**
- Anthropic handles the infrastructure
- Security and sandboxing built in
- Prototype to live agent in days
- Cost: API usage only (pay as you go)

The barrier to entry just dropped from "hire a dev team" to "describe what you want the agent to do."

## The 4 Building Blocks (All You Need to Know)

Every managed agent runs on four things:

1. **Agent** - The instructions. What model to use, what the agent should do, and what tools it has access to. Think of this as the job description you'd write for a human assistant.

2. **Environment** - The workspace. Pre-loaded with the software and tools your agent needs. Like setting up a new employee's laptop before their first day.

3. **Session** - A running conversation. The agent remembers everything within a session, can work for hours, and keeps files around between interactions.

4. **Events** - Messages back and forth. You send tasks in. The agent streams back results, status updates, and asks for approval when needed.

That's it. Four concepts. Everything else is details.

## What You Can Actually Build With This

**For your own business:**
- An agent that reads every client email and drafts responses in your voice
- A research agent that monitors competitors and sends you weekly briefings
- A content agent that takes your rough notes and produces finished blog posts, social copy, and newsletters

**As a service you sell to clients ($1,500-5,000 setup + $500/month):**
- Client onboarding agents that collect documents, send reminders, and set up new accounts automatically
- Report generators that pull data from multiple sources and create weekly summaries for executives
- Customer support agents that answer common questions, escalate edge cases, and log everything in the CRM
- Document processors that take raw files, extract the important data, and organize it. Finance teams are already using this.
- Project management agents that join Asana or Linear and pick up tasks like a team member

The key insight: you don't need to build these yourself. You need to understand the client's problem well enough to describe it to the agent.

## The Permission System (Why Clients Will Trust This)

Managed Agents has two modes:
- **Auto-run:** The agent handles everything automatically. Good for internal tools where you trust the workflow.
- **Approval required:** The agent pauses and asks before taking action. Good for anything client-facing or sensitive.

You can mix them. Let the agent read files and search the web automatically, but require approval before it sends an email or updates a database.

This is how you get risk-averse business owners to say yes. "The agent will draft the email, but it won't send anything without your approval."

## How to Get Started (Two Paths)

**Path 1: You already use Claude Code**
Open Claude Code and type one line: "start onboarding for managed agents in Claude API"

**Path 2: Non-technical and want help**
Build With AI community does live office hours walking through agent builds step by step.

## What This Costs

Pricing is usage-based:
- Standard Claude API token rates (same as using Claude normally)
- $0.08 per session-hour for active runtime
- Web search: $10 per 1,000 searches

A typical 10-minute agent session costs a few cents. Even heavy usage stays well under $100/month for most use cases.

## The Business Opportunity Nobody's Talking About

The businesses that need this most (law firms, accounting practices, real estate agencies, medical offices) will never set this up themselves. They don't want to. They want someone to do it for them.

That someone is you.

**The playbook:**
1. Run a $999 AI audit to identify their biggest time wasters
2. Build a managed agent that solves their top problem
3. Deploy it on Anthropic's infrastructure
4. Charge $500/month to maintain and improve it

4 clients = $2,000/month recurring. 10 clients = $5,000/month. And each agent takes less time to maintain than a single meeting.

---

## Summary

Claude Managed Agents is Anthropic's hosted agent platform that handles all infrastructure so non-technical users can deploy AI agents by simply describing what they want. The 4 core concepts are Agent (instructions), Environment (workspace), Session (persistent conversation), and Events (messaging). The key business insight: the barrier to entry for selling AI agent services dropped from "hire a dev team" to "describe the problem." This opens a $1,500-5,000 setup + $500/month recurring business model targeting clients who will never build this themselves.

---

## Key Takeaways

1. **No-code agent deployment** — describe what you want, Anthropic handles all infrastructure
2. **4 building blocks** — Agent (instructions), Environment (workspace), Session (persistent conversation), Events (messaging)
3. **Permission system** — auto-run vs approval-required modes, lets you mix and match per action type
4. **Non-technical friendly** — you don't need to understand APIs or write code, just understand business problems
5. **Business model** — AI services business: $1,500-5,000 setup + $500/month per client, 4-10 clients = $2-5K/month recurring
6. **Target clients** — law firms, accounting, real estate, medical offices (businesses that won't build it themselves)
7. **Cost** — a few cents per 10-min session, under $100/month for most use cases
8. **Permission-based trust** — approval-required mode is how you sell to risk-averse business owners

---

## Hermes-Related Interest

This is directly relevant to Hermes's architecture. The 4-layer memory system you're planning (Built-in Memory → Agents.md/Soul.md → Obsidian Vault → Session Search) mirrors the Managed Agents architecture: Agent (instructions/prompt) → Environment (workspace/vault files) → Session (context window) → Events (tool calls/messages). The permission system concept (auto-run vs approval-required) is also applicable — when Hermes executes high-stakes actions (writing files, git push, sending messages), an approval step could prevent mistakes. The AI services business model is also relevant if you ever consider offering agent-building services.
