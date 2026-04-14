# Everything You Need to Know About Claude Managed Agents

**Author:** J.B. (@VibeMarketer_)
**Source:** X/Twitter
**Link:** https://x.com/vibemarketer_/status/2043676607970242691
**Date:** April 2026
**Tags:** #AI #Claude #Agents #Anthropic #Managed-Agents #vibe

---

## Summary

J.B. breaks down Anthropic's Claude Managed Agents — what they are, how they work, how much they cost, and 5 specific agents you could build today. 116K views, 276 likes, 1,122 bookmarks.

---

## What It Is

Claude Managed Agents = AI agents that run on Anthropic's cloud. Handles all the backend: servers, security, error handling, sandboxing. You just describe what you want. Before this, shipping a production agent = months of engineering. Now = an afternoon.

---

## Architecture: 4 Pieces

1. **Agent** — the job description (model, task, tools)
2. **Environment** — sandboxed workspace pre-loaded with software, can write code/read files/search web/connect to external tools
3. **Session** — persistent conversation, agent remembers everything, works for hours, files persist between interactions. If connection drops, session keeps running
4. **Events** — how you talk to it. Send tasks in, get streamed results + status updates + approval requests

---

## Permission Modes

- **Auto-run** — agent handles everything itself. Good for internal trusted workflows
- **Approval-required** — agent pauses before certain actions (drafts email but waits for you to send, writes code but waits for you to push)
- Can **mix** within the same agent (auto for research/drafting, approval for external actions)

---

## Cost

- Standard Claude API token rates (same as normal)
- **$0.08/session-hour** for active runtime
- Web search: **$10/1,000 searches**
- A 10-minute session = a few cents
- Most people: well under **$100/month** even with daily usage

---

## 5 Agents You Could Build This Week

### 1. Meeting Prep Agent
- Before every calendar meeting: pulls context on who you're meeting, checks CRM/notes for history, generates one-page briefing with talking points + follow-ups
- Tools: calendar (MCP), CRM, notes, web search
- Run on schedule every morning

### 2. Client Intake Agent
- New client signs up → sends welcome email, collects docs, follows up if missing, sets up account, notifies you when ready
- Tools: email, project management, file storage
- Approval-required for initial outreach; auto-run for follow-ups once trusted

### 3. Content Research Agent
- Monitors sources (competitor blogs, newsletters, X accounts, RSS feeds)
- Sends weekly summary: what's new, trending, relevant
- Tools: web search, output delivery (email/Slack/vault markdown)
- Run weekly on schedule

### 4. Document Processing Agent
- Takes raw files (contracts, invoices, reports, transcripts) → extracts data → structured format → flags what needs human review
- Tools: file access, code execution, output format (spreadsheet/DB/structured summary)
- Agent writes code to parse PDFs, extract tables, reformat data

### 5. Code Review Agent
- Reads PRs against team conventions, checks for issues, writes tests for uncovered paths, posts review
- Runs on every PR automatically
- Tools: git repo access, style guide/coding standards as reference docs
- Approval-required before pushing changes

---

## How to Get Started

1. Open Claude Code
2. Type: "start onboarding for managed agents in Claude API"
3. It walks you through creating your first agent, setting up environment, running a test session

Or: go to **platform.claude.com**

---

## Hermes Angle

- The **MCP** (Model Context Protocol) tool access pattern maps directly to how Hermes tools work
- The **approval-required** permission model is similar to Hermes CLI's dangerous command approval
- Hermes could act as a **local wrapper** for Claude Managed Agents — the content research agent and meeting prep agent are especially aligned with Hermes capabilities
- The session persistence concept (session keeps running if connection drops) is interesting — Hermes cron jobs could complement this for scheduled tasks
