# Everything you need to know about Claude Managed Agents (and how to build your first one today)

**Source:** J.B. (@VibeMarketer_)  
**Date:** 2026-04-13  
**Link:** https://x.com/vibemarketer_/status/2043676607970242691

---

## Full Article

everything you need to know about claude managed agents (and how to build your first one today)

anthropic recently launched Claude Managed Agents. here's what it is and how to start building with it. if you've ever wanted to build an AI agent that actually does work (reads emails, generates reports, processes documents, updates your CRM) but got stuck on the infrastructure side, this is for you. managed agents handles all the backend stuff. the servers, the security, the error handling and the sandboxing. you just describe what you want the agent to do and anthropic runs it on their cloud. before this, shipping a production agent could mean months of engineering. now it takes an afternoon.

how it works

every managed agent has four pieces:

- agent -> the job description. you tell it what model to use, what it should do, and what tools it has access to.
- environment -> the workspace. a sandboxed computer pre-loaded with the software your agent needs. it can write code, read files, search the web, and connect to external tools.
- session -> a conversation that persists. the agent remembers everything within a session, can work for hours, and keeps files around between interactions. if your connection drops, the session keeps running.
- events -> how you talk to the agent. you send tasks in. it streams back results, status updates, and asks for approval when needed.

that's the whole architecture. one thing worth understanding: you control how much autonomy the agent has. there are two permission modes. auto-run means the agent handles everything on its own. good for internal stuff where you trust the workflow. approval-required means the agent pauses before taking certain actions. it'll draft the email but won't send it until you say go. it'll write the code but won't push it until you review. you can mix these in the same agent. let it research and draft automatically, but require your approval before it touches anything external.

what it costs

standard claude API token rates (same as using claude normally) plus $0.08 per session-hour for active runtime. web search is $10 per 1,000 searches if your agent needs it. a 10-minute session costs a few cents. most people will spend well under $100/month even with daily usage.

what you can actually build

here are five agents you could have running this week. i'm being specific on purpose so you can see what "agent" actually means in practice.

1. meeting prep agent
what it does: before every meeting on your calendar, it pulls context on who you're meeting with, checks your notes and CRM for history, and generates a one-page briefing with talking points and follow-up items from last time.
how to build it: create an agent with access to your calendar (via MCP), your CRM or notes tool, and web search. set it to auto-run on a schedule. every morning it checks your calendar, runs the research, and drops briefings into a folder or sends them to slack.

2. client intake agent
what it does: when a new client signs up, it sends the welcome email, collects the required documents, follows up if anything's missing, sets up their account in your system, and notifies you when everything's ready.
how to build it: agent with access to email, your project management tool, and file storage. use approval-required for the initial outreach emails (so you can review the tone), then auto-run for the follow-ups and account setup once you trust the workflow.

3. content research agent
what it does: monitors a list of sources you care about (competitor blogs, industry newsletters, X accounts, RSS feeds). every week it sends you a summary of what's new, what's trending, and what's relevant to your work. flags anything that might be worth writing about.
how to build it: agent with web search enabled and access to wherever you want the output delivered (email, slack, a markdown file in your vault). define your sources and your criteria for "relevant" in the agent instructions. run it weekly on a schedule.

4. document processing agent
what it does: takes raw files (contracts, invoices, reports, transcripts) and extracts the important data. organizes it into a structured format. flags anything that needs human review.
how to build it: agent with file access and whatever output format you need (spreadsheet, database entry, structured summary). upload the files as part of the session. the sandboxed environment means the agent can write code to parse PDFs, extract tables, and reformat data without you building any of that tooling.

5. code review agent
what it does: reads pull requests against your team's conventions, checks for common issues, writes tests for uncovered paths, and posts the review. runs on every PR automatically.
how to build it: agent with access to your git repo and your style guide / coding standards as reference docs. auto-run for the review and test writing. approval-required before it pushes any changes.

how to get started right now

the fastest path:
- open claude code
- type: "start onboarding for managed agents in Claude API"
- it walks you through creating your first agent, setting up the environment, and running a test session

if you don't use claude code, go to platform.claude.com

---

## Summary

Anthropic's Claude Managed Agents is a hosted agent platform that handles all the infrastructure (servers, security, error handling, sandboxing) so you can focus on describing what you want the agent to do. Every agent has four core components: the agent itself (job description + tools), the environment (sandboxed workspace), the session (persistent conversation), and events (how you communicate with it). Two permission modes give you control over autonomy: auto-run for trusted workflows, and approval-required for anything external-facing. At ~$0.08/session-hour plus standard API rates, most users will spend under $100/month with daily usage.

---

## Key Takeaways

1. **Four components define every agent:** agent (instructions + tools), environment (sandboxed workspace), session (persistent, keeps files), events (streaming input/output)
2. **Dual permission modes:** auto-run for internal automation; approval-required before external actions (sending emails, pushing code)
3. **Can mix modes in one agent:** let it research + draft automatically, but gate external-facing actions
4. **Real cost:** ~$0.08/session-hour + standard API tokens. A 10-minute session = a few cents. Most people under $100/month
5. **Five production-ready agent ideas:** meeting prep (calendar + CRM + web search), client intake (email + PM + file storage), content research (web search + RSS + vault), document processing (file parsing + structured output), code review (git + style guide)
6. **Fastest onboarding:** Type "start onboarding for managed agents in Claude API" in Claude Code — walks you through everything
