---
title: "Claude Schedules vs Routines (What's the difference)"
source: "https://x.com/NickSpisak_/status/2044142814942961880"
author:
  - "[[@NickSpisak_]]"
published: 2026-04-14
created: 2026-04-14
description: "Claude Code now has three different ways to run work automatically. --> Routines run in the cloud. --> Schedules run on your machine--> /..."
tags:
  - "clippings"
---
![Image](https://pbs.twimg.com/media/HF4_d59W4AESmpR?format=jpg&name=large)

Claude Code now has three different ways to run work automatically. --> Routines run in the cloud. --> Schedules run on your machine --> /loop runs inside your current session. Most people don't know the difference. Here's the clear breakdown so you pick the right one every time.

In under 5 minutes you'll learn:

1. What each scheduling option actually does (in plain language)
2. The key difference between cloud and local execution
3. When to use Routines, Desktop Schedules, or /loop
4. How to set up each one step by step
5. A simple decision matrix you can screenshot and reference

Real Quick...

Follow [@NickSpisak\_](https://x.com/@NickSpisak_) for practitioner-level AI implementation and join the Build With AI newsletter for weekly guides like this one: [Join Here](https://return-my-time.kit.com/db5f932e4e)

Alright lets dive in...

## 1\. Routines - Your Agent in the Cloud

Routines are the newest option. They run on Anthropic's managed cloud infrastructure. That means your laptop can be closed, powered off, or on a plane. The routine still runs.

A routine is a saved configuration: a prompt, one or more GitHub repositories, a model selection, and connectors to external services like Gmail, Slack, or Linear. Every run spins up a fresh cloud session with the same tools Claude Code has locally.

Three trigger types:

- **Schedule** - hourly, daily, weekdays, or weekly. Minimum interval is one hour.
- **API** - a dedicated HTTP endpoint with a bearer token. POST to it from any external system.
- **GitHub Events** - pull requests, pushes, issues, releases. 17 event types with filters for author, branch, and labels.

You can stack multiple triggers on the same routine. Create them at [claude.ai/code/routines](https://claude.ai/code/routines), from the Desktop app, or with /schedule in the CLI.

The trade-off: routines don't have access to your local files. Every run starts from a fresh clone of your repository. If your workflow depends on local data that isn't in a repo, routines aren't the right fit.

Available on Pro, Max, Team, and Enterprise plans. Currently in research preview.

## 2\. Desktop Scheduled Tasks - Your Agent on Your Machine

Desktop scheduled tasks run locally. They have direct access to your files, your local tools, and your MCP servers. The catch is your computer needs to be on and the Desktop app needs to be running.

Create them from the Schedule page in the Desktop app. Click New Task, choose New Local Task, set a name, prompt, and frequency.

Frequency options: manual, hourly, daily, weekdays, or weekly. The minimum interval is one minute - much more granular than routines.

What makes these different from routines:

- **Local file access.** The task runs against your actual working directory, including uncommitted changes. A routine gets a fresh clone.
- **Permission prompts.** You can configure whether the task asks for approval before running commands. Routines are fully autonomous.
- **Missed run catch-up.** If your computer was asleep, the Desktop app runs one catch-up when it wakes. But it only catches the most recent miss - not every missed run.

Pro tip: after creating a task, click Run Now and watch for permission prompts. Select "always allow" for each one so future runs don't stall waiting for your approval.

If your laptop lid is closed, the task doesn't run. Enable "Keep computer awake" in Settings to prevent idle sleep - but closing the lid still stops everything.

## 3\. /loop - Quick Polling in a Live Session

/loop is the simplest option. Type it in any Claude Code session and your prompt runs on repeat. It's session-scoped - when you close the terminal, the loop dies.

Three ways to use it:

- /loop 5m check the deploy - fixed interval with your prompt
- /loop check the deploy - Claude picks the interval based on what it observes
- /loop - runs a built-in maintenance prompt (or your custom loop.md)

Best for: watching a build finish, babysitting a PR, polling CI status. Anything where you're actively working and want Claude to keep checking something in the background.

/loop tasks expire after 7 days automatically. They don't survive restarts. They can run as frequently as every minute. (You can help this survive with tmux sessions locally)

## 4\. The Decision Matrix

Here's when to use each one. Screenshot this.

![Image](https://pbs.twimg.com/media/HF5A8xaXgAAWl9G?format=jpg&name=large)

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

## 5\. Quick Setup for Each Option

**Routines:** Go to [claude.ai/code/routines](https://claude.ai/code/routines). Click New Routine. Write your prompt, pick a repo, select your model (Opus 4.6 for complex tasks, Sonnet 4.6 for simpler ones), choose an environment, add triggers, review connectors. Click Create. Click Run Now to test.

**Desktop Schedules:** Open the Desktop app. Click Schedule in the sidebar. Click New Task, then New Local Task. Set your name, prompt, and frequency. Click Run Now to test permissions.

**/loop:** Open any Claude Code session. Type /loop 5m your prompt here. Done.

## The Bottom Line

Three tools, three use cases. Routines give you always-on cloud automation that works while you sleep. Desktop schedules give you local access with persistent scheduling. /loop gives you instant, temporary polling.

Most people will use routines for their core workflows and /loop for everything else. Desktop schedules fill the gap when you need local file access on a recurring basis.

Pick the right tool. Set it up once. Let Claude do the rest.

If you want more guides like this one, join the Build With AI newsletter: [Join Here](https://return-my-time.kit.com/db5f932e4e)