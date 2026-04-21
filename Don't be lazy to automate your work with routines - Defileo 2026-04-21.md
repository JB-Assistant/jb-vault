# Don't be lazy to automate your work with routines

**Source:** Defileo (Leo) (@defileo)  
**Date:** 2026-04-21  
**Link:** https://x.com/defileo/status/2045466421036007527

---

## Full Article

Most people think Claude is something you talk to, tho it is now something you deploy.

Anthropic quietly shipped something that changes how you think about AI entirely, it is called Routines.

And if you build things, run a team, or manage any kind of recurring work, this is the most important thing Claude has shipped this year.

Here is what it does:

You define a task once, a prompt, a repo, a trigger, claude runs it automatically on Anthropic's cloud infrastructure.

Your laptop can be closed -> Claude is still working, not a chatbot, not a copilot a deployed worker.

## The three triggers

Every routine needs a trigger, there are three types, you can combine them on the same routine.

### Schedule
Runs on a recurring cadence. Hourly, daily, weekdays, weekly, or a custom cron expression. You set the time in your local timezone and Claude converts it automatically.

Use this for anything that needs to happen on a clock. Daily standups. Weekly doc reviews. Nightly backlog maintenance. Morning digests.

### API
Gives your routine a dedicated HTTP endpoint. You POST to it with a bearer token and Claude starts a run immediately. You can pass extra context in the request body using a text field.

Use this to wire Claude into anything that can make an HTTP request. Alerting tools. Deploy pipelines. Internal dashboards. Anywhere you want Claude to react to something your system detected.

### GitHub
Runs automatically when something happens in a repository. Pull request opened. Commit pushed. Issue created. Workflow completed. You pick the event and optionally add filters so it only triggers on exactly what you care about.

Use this for code review, PR triage, changelog generation, or anything that should happen every time code moves.

## Five routines you can set up today

These are real use cases from the docs, each one has the trigger type, the prompt structure, and what Claude actually does.

### Routine 1: Morning backlog digest
**Trigger:** schedule, every weekday at 7am

**What happens:** You wake up, open Slack, and your backlog is already groomed. Nobody had to touch it. No Monday morning surprise of 30 unlabeled tickets from the weekend.

### Routine 2: Auto PR reviewer
**Trigger:** GitHub, pull_request.opened

**What happens:** Every new PR gets reviewed before a human looks at it. The mechanical stuff is already caught, your team spends review time on architecture and logic, not missing semicolons.

You can add filters too: only trigger on PRs targeting main, only trigger on non-draft PRs, only trigger on PRs from forks. You control exactly what fires the routine.

### Routine 3: Alert Triage Bot
**Trigger:** API (called by your monitoring tool)

**What happens:** Your monitoring tool fires an alert at 3am -> Claude wakes up, finds the relevant commits, opens a draft PR with a proposed fix, and posts it to Slack. Your on-call engineer reviews a PR instead of staring at a blank terminal at 3am.

### Routine 4: Docs Drift Checker
**Trigger:** schedule, every Monday at 9am

**What happens:** Documentation stays current automatically. The most hated maintenance task on any engineering team runs itself every week without anyone asking for it.

### Routine 5: Deploy Verification
**Trigger:** API (called by your CD pipeline after deploy)

**What happens:** Every deploy gets verified automatically. Your team gets a go or no-go in Slack before anyone has to manually check anything. The deploy window does not close with everyone hoping nothing broke.

## How to Set Up Your First Routine

Ten minutes, here is the exact path, from the web:

1. Give it a name, write the prompt — the prompt is the most important part. Claude runs autonomously so it needs to be specific, not "review PRs" but "review PRs targeting main, check for missing error handling and security issues, leave inline comments, post a summary verdict."
2. Select your GitHub repository — Claude clones it at the start of every run starting from the default branch.
3. Pick an environment. The default one works for most cases. Custom environments let you set API keys, install dependencies, or control network access.
4. Choose your trigger: Schedule, API, or GitHub event, add filters if needed.
5. Review your connectors. All your connected MCP connectors are included by default. Remove any the routine does not need, click create.

**From the CLI:**
Run `/schedule` in any Claude Code session, Claude walks you through everything conversationally and saves the routine to your account.

**To manage existing routines from the CLI:**
```
/schedule list
/schedule update
/schedule run
```

## What You Need to Know About Limits:

- Routines use your subscription quota like interactive sessions.
- There's a daily cap on routine runs per account, check usage at `/routines` or settings/usage.
- If you hit the cap: with extra usage, runs continue as metered overage, without it, new runs are rejected until reset.
- By default, Claude can only push to claude/* branches to avoid protected branches. To push anywhere, enable "Allow unrestricted branch pushes" when creating the routine.
- Routines are per-user, not shared. All actions via your GitHub identity (commits, PRs, Slack, Linear) show up as you.
- During the research preview, GitHub triggers also have per-routine and per-account hourly caps; extra events are dropped until reset.

---

## Summary

This X Article by @defileo breaks down Anthropic's Claude Code Routines — a feature that turns Claude from an interactive chatbot into a deployed worker that runs autonomously on Anthropic's cloud infrastructure. You define a task once with a prompt, connect a repo, pick a trigger (Schedule, API webhook, or GitHub event), and Claude executes it automatically even with your laptop closed.

The article walks through three trigger types and five concrete use cases: morning backlog digest, auto PR reviewer, alert triage bot, docs drift checker, and deploy verification. Setup takes 10 minutes via web UI or conversationally via `/schedule` command in Claude Code.

## Key Takeaways

1. **Claude is now deployable, not just interactive** — Routines run on Anthropic's cloud, not your machine
2. **Three trigger types can be combined** — Schedule (cron), API (webhook), GitHub (repo events)
3. **Specific prompts are critical** — Autonomous Claude needs detailed instructions, not vague ones
4. **Uses your subscription quota** — Daily caps apply, overage is metered pricing
5. **MCP connectors included by default** — All your connected tools (Slack, Linear, etc.) work automatically
6. **Per-user, per-GitHub-identity** — All actions show up as you, not a service account
7. **Research preview limitations** — GitHub triggers have hourly caps during preview period

## Hermes-Related Interest

**High relevance.** This directly applies to Junaid's multi-product stack (OttoManagerPro, TireManagerPro, CleanBuddyPro, FieldAgent AI). Potential use cases:
- Auto PR reviewer for all four repos before merging
- Nightly health check routines across Supabase instances
- Scheduled Stripe/SMS metric digests via API triggers
- Deploy verification for VPS-hosted apps (like PDF TTS app)
- Could integrate with Hermes' own cron job system for orchestration decisions

This is also relevant to the multi-agent architecture — Routines could serve as the "trigger layer" for spawning field agents in FieldAgent AI based on GitHub events or external API signals.
