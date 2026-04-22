# Claude Schedules vs Routines (What's the difference)

**Source:** Nick Spisak (@NickSpisak_)  
**Date:** 2026-04-22  
**Link:** https://x.com/nickspisak_/status/2044142814942961880  
**Stats:** 202 likes · 13 RTs · 467 bookmarks · 38K views

---

## Full Article

Claude Code now has three different ways to run work automatically.
--> Routines run in the cloud.
--> Schedules run on your machine
--> /loop runs inside your current session.

Most people don't know the difference. Here's the clear breakdown so you pick the right one every time.

In under 5 minutes you'll learn:
- What each scheduling option actually does (in plain language)
- The key difference between cloud and local execution
- When to use Routines, Desktop Schedules, or /loop
- How to set up each one step by step
- A simple decision matrix you can screenshot and reference

---

## 1. Routines - Your Agent in the Cloud

Routines are the newest option. They run on Anthropic's managed cloud infrastructure. That means your laptop can be closed, powered off, or on a plane. The routine still runs.

A routine is a saved configuration: a prompt, one or more GitHub repositories, a model selection, and connectors to external services like Gmail, Slack, or Linear. Every run spins up a fresh cloud session with the same tools Claude Code has locally.

Three trigger types:
- **Schedule** — hourly, daily, weekdays, or weekly. Minimum interval is one hour.
- **API** — a dedicated HTTP endpoint with a bearer token. POST to it from any external system.
- **GitHub Events** — pull requests, pushes, issues, releases. 17 event types with filters for author, branch, and labels.

You can stack multiple triggers on the same routine. Create them at claude.ai/code/routines, from the Desktop app, or with /schedule in the CLI.

The trade-off: routines don't have access to your local files. Every run starts from a fresh clone of your repository. If your workflow depends on local data that isn't in a repo, routines aren't the right fit.

Available on Pro, Max, Team, and Enterprise plans. Currently in research preview.

---

## 2. Desktop Scheduled Tasks - Your Agent on Your Machine

Desktop scheduled tasks run locally. They have direct access to your files, your local tools, and your MCP servers. The catch is your computer needs to be on and the Desktop app needs to be running.

Create them from the Schedule page in the Desktop app. Click New Task, choose New Local Task, set a name, prompt, and frequency.

Frequency options: manual, hourly, daily, weekdays, or weekly. The minimum interval is one minute — much more granular than routines.

What makes these different from routines:
- **Local file access.** The task runs against your actual working directory, including uncommitted changes. A routine gets a fresh clone.
- **Permission prompts.** You can configure whether the task asks for approval before running commands. Routines are fully autonomous.
- **Missed run catch-up.** If your computer was asleep, the Desktop app runs one catch-up when it wakes. But it only catches the most recent miss — not every missed run.

Pro tip: after creating a task, click Run Now and watch for permission prompts. Select "always allow" for each one so future runs don't stall waiting for your approval.

If your laptop lid is closed, the task doesn't run. Enable "Keep computer awake" in Settings to prevent idle sleep — but closing the lid still stops everything.

---

## 3. /loop - Quick Polling in a Live Session

/loop is the simplest option. Type it in any Claude Code session and your prompt runs on repeat. It's session-scoped — when you close the terminal, the loop dies.

Three ways to use it:
- `/loop 5m check the deploy` — fixed interval with your prompt
- `/loop check the deploy` — Claude picks the interval based on what it observes
- `/loop` — runs a built-in maintenance prompt (or your custom loop.md)

Best for: watching a build finish, babysitting a PR, polling CI status. Anything where you're actively working and want Claude to keep checking something in the background.

/loop tasks expire after 7 days automatically. They don't survive restarts. They can run as frequently as every minute.

(You can help this survive with tmux sessions locally)

---

## 4. The Decision Matrix

**Use Routines when:**
- The work should run whether your computer is on or not
- You're triggering from external events (webhooks, API calls, GitHub PRs)
- The task only needs repo access, not local files
- You want fully hands-off, autonomous execution

**Use Desktop Schedules when:**
- The task needs access to local files, local tools, or local MCP servers
- You need intervals shorter than one hour
- You want control over permissions
- Your computer is reliably on during scheduled times

**Use /loop when:**
- You're actively working and want to poll something
- The task is temporary (watching a build, monitoring a PR)
- You want Claude to adapt the interval based on what it sees
- You need it running in the next 10 seconds with zero setup

The simplest rule: if you'd set it and forget it, use a routine. If you need local access, use a Desktop schedule. If you need it right now for the next few hours, use /loop.

---

## 5. Quick Setup for Each Option

**Routines:** Go to claude.ai/code/routines. Click New Routine. Write your prompt, pick a repo, select your model (Opus 4.6 for complex tasks, Sonnet 4.6 for simpler ones), choose an environment, add triggers, review connectors. Click Create. Click Run Now to test.

**Desktop Schedules:** Open the Desktop app. Click Schedule in the sidebar. Click New Task, then New Local Task. Set your name, prompt, and frequency. Click Run Now to test permissions.

**/loop:** Open any Claude Code session. Type `/loop 5m your prompt here`. Done.

---

## The Bottom Line

Three tools, three use cases. Routines give you always-on cloud automation that works while you sleep. Desktop schedules give you local access with persistent scheduling. /loop gives you instant, temporary polling.

Most people will use routines for their core workflows and /loop for everything else. Desktop schedules fill the gap when you need local file access on a recurring basis.

---

## Summary

Nick Spisak breaks down Claude Code's three automation options: **Routines** (cloud-based, works with GitHub repos, triggers on schedule/API/GitHub events, no local file access), **Desktop Scheduled Tasks** (local execution, file access, 1-min minimum interval, needs computer on), and **/loop** (session-scoped polling, expires after 7 days, zero setup). Key decision: cloud = routine, local = desktop schedule, temporary = /loop.

---

## Key Takeaways

1. **Routines = cloud, Schedules = local** — the fundamental distinction; one needs your machine on, the other doesn't
2. **Routines get fresh repo clones every run** — no local file access, no uncommitted changes
3. **Desktop schedules need "always allow" permissions** — run once manually first to approve everything
4. **/loop survives with tmux** — if you need it longer than a session, wrap in tmux
5. **Routines support 17 GitHub event triggers** — PR, push, issue, release with author/branch/label filters
6. **Minimum intervals differ** — Routines: 1 hour, Desktop: 1 minute, /loop: 1 minute
7. **Decision rule: set-and-forget → routine, local files → desktop schedule, right now → /loop**

---

## Hermes Angle

This is directly relevant to the 4-layer memory system and multi-agent workflow. Key comparisons:
- **Hermes cron jobs** are analogous to Routines — cloud-based, scheduled, autonomous
- **/loop** is similar to a background process in a tmux session on the MacMini
- **Desktop Schedules** don't have a Hermes equivalent yet — could be worth exploring for local-file-dependent tasks
- The GitHub Events trigger on Routines is powerful — could auto-trigger code reviews or deploy checks
