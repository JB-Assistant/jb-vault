# Imran's Real-World Hermes Setup — SIP Podcast Breakdown
**Source:** [The Startup Ideas Podcast @startupideaspod](https://x.com/startupideaspod/status/2046310040207016342) | 2.3K views
**Date:** April 2026

*Imran breaks down what he runs, how he installed it, and the exact ideas he's building with it.*

---

## Why He Left OpenClaw

Three problems kept stacking up:
1. **No built-in memory** — kept telling it the same things over and over
2. **Gateway needed restarting** — once a day, once an hour
3. **Token spend with no visibility** — had no idea what was burning money

He tried Nebula first. Good for an AI coworker. Wrong fit for personalized workflows that learn over time.

Then Hermes.

---

## What Hermes Does Differently

- **Built-in memory** — every task completed successfully gets written to its own memory. Gets better the longer you use it.
- **Searchable history** — SQLite database. If it forgot to save something (like an API key), it can search logs and find it.
- **Stability** — hasn't restarted in over a week.
- **40+ tools pre-installed** — Browser, web search, cron jobs, image generation, home assistant. No hunting for tools.
- **Skills pre-installed** — On Mac: Apple Notes, Apple Reminders, Find My, iMessage. Ready on install.

---

## Install (Mac, Linux, or WSL)

One line from the Hermes Agent docs. On Mac, you may need Xcode tools first:
```
xcode-select --install
```

Paste the install command. You can skip the onboarding.

**The one command to learn:** `hermes model` — shows every provider and every model available out of the box.

---

## How He Dropped Token Spend by 90%

**Two moves:**

1. **Use OpenRouter** — shows every model with clear per-token pricing. Rotates free models weekly.
2. **Turn repeat tasks into code** — if you run the same task daily, have the agent write the code once. After that the task is deterministic. No agent in the loop. No tokens spent.

> "His numbers: around $130 every five days down to around $10 every five days. Same capabilities."

---

## Security Setup

Ask Hermes to audit its own setup:
> "Is this secure? Tell me why or why not."

It'll check for keys in plain text, weak firewall config, exposed secrets.

**Three run modes:**
- **Bare metal** (what Imran uses, with daily updates)
- **Docker container** (isolated from your files)
- **Modal** (serverless)

---

## The Android Install

Install with a script. Two extra apps needed:
- **Termux** — terminal inside Android
- **Termux API** (F-Droid) — gives the agent access to phone sensors: battery, Wi-Fi, volume, camera, brightness, vibration

**Why bother?** A cheap Android with a SIM card becomes an always-on, low-power dedicated agent device. No sold-out Mac Mini required.

**What it unblocks:**
- Post to social from a real device (not through a scheduler API that nerfs reach)
- Read SMS directly
- Automate 2FA codes via text

> "Imran runs one on a Solana Seeker Android phone. He named it Cookie Monster. (All his agents are named after Muppets.)"

---

## How to Actually Use It (The Part Most People Skip)

**Imran's pattern:** Solve personal problems first. That's how you learn the paradigm.

**His first real win:** Dinner. He recorded an 8-minute Telegram voice note walking through every ingredient in his pantry. The agent sends him three recipes a day based on what's there and his fitness goals.

> "Small problem. Big mental-load reduction."

**Other things already running for him:**
- Morning Gmail triage (deletes junk, unsubscribes from useless lists, returns digest of what matters)
- Expense reports
- An Obsidian vault the agent organizes itself

> "On Obsidian: he wasn't a user before. Now it's his home dashboard. Markdown files the agent manipulates every morning. Today's tasks, this week's priorities, upcoming travel, work, personal. All organized by the agent."
>
> "He didn't design this. The agent built it after about 20 days of use. Imran thinks 7 days of consistent use gets you most of the way there."

---

## The Prompts He Runs on Himself

Meta-prompt at the end of each day:
1. What have I been procrastinating on?
2. What's the most important thing to work on today?
3. What tasks am I doing every day that I should automate?
4. What's one tool you can build me tonight that would make my life easier tomorrow?
5. Is there anything important today that I missed?

> "These feel obvious once you read them. Most people never ask them."

---

## One vs Many Agents

Imran runs four. He's a tinkerer. Thinks the real answer is **one or two**: one personal, one work.

**Reason:** If you work at a Fortune 500, they won't let you run a personal agent stuffed with private data on a work machine. Splitting keeps it clean — same way a to-do app splits personal and work lists.

**Cron jobs vs sub-agents:** He runs recurring tasks as cron jobs, not sub-agents. Sub-agents let you assign cheaper models to cheaper tasks (a Gmail triage sub-agent can run on a small model). Both work. The field is still figuring it out.

---

## Skills Worth Installing

| Skill | Notes |
|-------|-------|
| **Obsidian skill** | Even if you don't use the Obsidian CLI |
| **G-Stack by Gary Tan** | Originally for Cloud Code. Takes YC startup process and bolts it onto your agent. Free. |
| **Honcho dev memory skill** | Helps because Hermes has memory limits — smaller context helps |
| **Your own** | Bank statements, personal finance, fitness. Build for what you already pay for. |

---

## Two Non-Negotiables

1. **Update it every night.** It's still beta. Imran was 535 commits behind after nine days without updating.
2. **Lock it down.** Set up Telegram or WhatsApp access. Install Tailscale so your phone and computers sit on the same virtual network, then SSH in from anywhere.

---

## The Bigger Idea

> "Learning to use a personal agent isn't the skill. It's becoming the requirement."

Imran works at a fund. Because his agent handles the background work, he talks to **20–30% more founders.** Better signal. Better deal flow. Better returns.

> "The point isn't the tool. It's what the tool clears off your plate."
>
> "Customizing your agent isn't the skill. Getting work done with it is."

---

## Closing

> "Hermes Agent is like 90s tuner car culture. Find the parts. Bolt them on. Make it yours."
>
> "But remember what you're optimizing for. Not the car. The place you're driving to."

**Follow Imran:** [@imranye](https://x.com/imranye)
**Original thread:** https://x.com/startupideaspod/status/2046310040207016342
