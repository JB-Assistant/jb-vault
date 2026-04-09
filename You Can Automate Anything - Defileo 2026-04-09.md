# You Can Automate Anything

**Source:** Defileo (@defileo)  
**Date:** 2026-04-09  
**Link:** https://x.com/defileo/status/2041867260189434035

---

## Full Article

You can automate anything.

If you think you need to know how to code to automate your work, let me save you some time, you don't.

Claude Code is fully FREE now, runs on your machine, reads your files, writes its own scripts, executes them, fixes its own errors, and keeps going until the job is done.

The real use of Claude that many people don't even think about is handing it a task you'd normally spend hours on and walking away.

First discover your needs with 1 prompt and then, I'll show you prompts I used to automate my life as an example:

Simply paste it to Claude first and then answer questions being as honest as you can.

## My use cases / 7 easy prompts to automate your life

**1 / 7 | Organise an entire folder of messy files**

Point Claude Code at a chaotic downloads folder and tell it to sort everything.

**2 / 7 | Forward Telegram messages between two accounts**

You want a script that watches one Telegram account and forwards specific messages to another, tell Claude Code to build and run the whole thing.

Claude Code will install the dependency, write the script, and start it. If there's an error it fixes it and tries again.

You get a running Telegram relay without writing a line of code.

**3 / 7 | Audit an entire project for problems**

This is where Claude Code is genuinely unmatched. Drop it into any project folder and ask it to find everything that's broken.

It reads every file in the project, builds the full picture in context, and writes you a structured report. What would take a human an afternoon takes Claude Code 3 minutes.

**4 / 7 | Process a CSV and produce a report**

Claude reads the CSV, writes a Python script to crunch the numbers, runs it, and writes the formatted report.

You don't need to know pandas, you don't need to know anything. All you need is CSV.

**5 / 7 | Build a daily digest that runs every morning**

This is a two-step command. First you ask Claude Code to build the script, then you ask it to schedule it.

Claude writes the script, tests it, then edits your crontab to schedule it. The next morning it runs on its own.

**6 / 7 | Rewrite every file in a folder to a new format**

Claude loops through every file, processes each one, and saves the output. Twenty files takes maybe two minutes. This scales to hundreds.

**7 / 7 | Automated commit messages and changelogs**

Claude reads the diff, groups related changes, writes commit messages that actually describe what happened, commits them, and updates your changelog.

You will never write a commit message again my fren.

## Bonus prompts

**The CLAUDE.md file: How to give Claude persistent context**

Every time you run Claude Code in a folder, it reads a file called CLAUDE.md if one exists.

This is how you give it standing instructions that apply to every command you run in that project. Create one like this:

[Note: actual CLAUDE.md content not shown in article]

After that, every Claude Code command in that folder runs with full project context. You stop repeating yourself. Claude stops making assumptions.

**How to schedule any Claude Code command**

Any Claude Code command can be turned into a scheduled job. On Mac and Linux, use cron. Ask Claude Code to set it up for you:

Claude Code writes the cron entry, explains it, and adds it to your crontab. Now that audit runs every night without you doing anything.

**How to chain Claude Code commands into a pipeline**

You can wire Claude Code commands together in a bash script so one triggers the next. Ask Claude to build the whole pipeline:

You end up with a single script you can run or schedule that chains three Claude Code agents, each handing off to the next.

## The prompt formula that works every time

When you're writing a Claude Code command, this structure gets the best results consistently:

The --allowedTools list matters.

- Use Bash when it needs to run commands or scripts.
- Use Write when it needs to create or edit files.
- Use Read when it only needs to read.

The tighter you keep permissions, the more predictably it behaves in unattended mode.

And if a command half-works or errors out, just tell it what went wrong in the next message in interactive mode, or append the error to the -p prompt.

Claude Code reads the actual error output, fixes the actual problem, and tries again. Most things work within two attempts.

---

## Summary

Defileo makes the case that you don't need to know how to code to automate your work — Claude Code handles the technical heavy lifting. He shares 7 practical prompts for automating common tasks: organizing messy folders, Telegram relay bots, project audits, CSV processing + reports, scheduled daily digests, bulk file format conversion, and automated commit messages. He also covers the CLAUDE.md pattern for persistent context, cron scheduling, and chaining commands into pipelines.

---

## Key Takeaways

1. **No coding required** — Claude Code writes its own scripts, executes them, fixes its own errors, runs free on your machine
2. **7 automation prompts:** (1) sort messy folders, (2) Telegram message relay, (3) project audit, (4) CSV → report, (5) scheduled daily digest, (6) bulk file conversion, (7) auto commit messages + changelog
3. **CLAUDE.md for persistent context** — standing instructions that apply to every command in a project folder
4. **Cron scheduling** — ask Claude Code to set up a cron job; it writes the entry, explains it, adds it to crontab
5. **Pipeline chaining** — chain multiple Claude Code commands in a bash script; each hands off to the next
6. **Prompt formula** — use --allowedTools to restrict permissions (Bash/Write/Read); tighter permissions = more predictable in unattended mode
7. **Error handling** — paste the error back to Claude Code and it fixes and retries; most things work within 2 attempts
8. **"Walking away" is the goal** — hand a task to Claude Code and let it run to completion

---

## Hermes-Related Interest

This is directly about Claude Code — which is essentially what Hermes runs on your VPS. The same principles apply: CLAUDE.md is the equivalent of skills (persistent context that applies to every session). The "hand it a task and walk away" philosophy is what Hermes cron jobs enable. The prompt formula with --allowedTools is essentially the tools/permissions model. Worth noting: Hermes already does much of this (cron jobs, file operations, script execution) — the question is whether the workflows are documented as skills.
