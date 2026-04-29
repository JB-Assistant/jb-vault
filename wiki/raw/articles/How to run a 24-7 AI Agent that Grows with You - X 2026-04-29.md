# How to run a 24/7 AI Agent that Grows with You

**Source:** Shubham Saboo (@Saboo_Shubham_)  
**Date:** 2026-04-29  
**Original date:** Wed Apr 15 02:27:24 +0000 2026  
**Link:** https://x.com/Saboo_Shubham_/status/2044241148794024293  
**Stats at capture:** 22,769 views, 188 likes, 390 bookmarks, 28 reposts

---

## Full Article

I've been running six agents on OpenClaw for months. They work. But the longer I ran them, the more I noticed a tax: I was maintaining the system more than the system was improving itself.

I kept updating SOUL.md files, pruning stale memory, and repeating the same corrections across agents. The agents were not getting better on their own. I was getting better at managing them.

Most agents can store context. Far fewer can turn completed work into reusable method. That is the difference I wanted to test.

If you haven't read my previous article about OpenClaw, read that here: 

[Embedded X post: https://x.com/i/status/2022014147450614038]

## The correction loop

I started calling my approach corrective prompt-engineering.

You watch the agent, notice a failure, explain the fix, update memory or instructions, and wait for the behavior to stick. Kelly's early drafts were full of emojis. I told her: no emojis, no hashtags, short punchy sentences. After a week, she got it. Dwight captured too much noise. I told him to focus on signal. He adjusted.

That loop works. But it has a hidden assumption: you are the learning system.

Every improvement depends on you noticing the problem, diagnosing it, and writing down the correction. The agents do not get better while you sleep. They get better when you pay attention.

## The experiment

I kept the OpenClaw squad running, but set up a second Monica on Hermes Agent. Same job. Same Mac Mini. Same access to Dwight's intel files. Not a replacement. Just a parallel test.

Hermes Agent is open-source from Nous Research. I was skeptical. Every agent tool claims some version of "memory" and "learning." Most of them mean "we store your chat history." That is not learning. That is hoarding.

Setup was simple. One command:

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

Then 'hermes setup'. It detected OpenClaw on the Mac Mini and offered to import settings, memories, and API keys. For Telegram, it walked me through BotFather setup. I sent the token and it connected. One tip: use a frontier model. The learning loop needs strong reasoning to work well.

## The first thing that felt different

The first time I checked '~/.hermes/skills/' and found files I did not create, something clicked.

The one that stood out was 'local-writing-canon-analysis/SKILL.md'. Monica had written a procedure for reading my published articles before drafting in my voice. Not "I know your style" in the abstract. More like: read the shipped work, then infer the voice from what actually survived editing.

The file captured concrete editorial rules: keep the compounding thesis, avoid framing new topics as product comparisons, center the piece on outcomes like memory and reuse rather than features.

I did not write it. She did. She watched what I kept, what I cut, and wrote down the pattern. Other skills showed up too: operational playbook, workflow procedures, reusable task patterns. Some were useful. Some were generic. But the default behavior, turning completed work into reusable procedure, was new.

The other thing that stood out was recall. When I searched for telegram OR gateway OR restart OR stuck, Hermes agent surfaced the exact troubleshooting arc from a previous session: the polling conflict, the lesson that gateway status alone is not proof of health, and the practical fix path. All from a conversation weeks earlier that nobody had manually promoted into memory.

The work leaves residue. Not just a memory of what happened, but a method for next time.

## Who owns the correction loop

OpenClaw Monica improves when I notice a problem and teach the fix. I notice a problem, give feedback, and she stores the correction for next time. The improvement depends on both of us.

Hermes Monica closes more of that loop herself. After a complex task, she evaluates what happened, decides what is worth keeping, and writes it into a skill file. I can inspect it, edit it, or delete it. But I did not have to initiate it.

That is the shift that matters. OpenClaw mostly stores what I explicitly teach. Hermes tries to turn finished work into future procedure.

The difference I cared about was not recall architecture. It was who owned the improvement loop.

## What still breaks

Agents still hallucinate confidence. Self-improvement is not self-verification.

During a migration session, Monica treated the Hermes migration archive as if it contained everything from OpenClaw. It did not. The actual source of truth was the live '~/.openclaw/' workspace. She inferred completeness from partial data and moved forward with confidence she had not earned.

The Telegram gateway was the other one. After a restart, the gateway reported as loaded, but the bot was not responding. launchd said the service was running. The live responder was dead. Status screens flatter you. Logs tell the truth.

Monica turned that failure into a recovery skill on her own. The file sits at ~/.hermes/skills/autonomous-ai-agents/hermes-telegram-gateway-recovery/SKILL.md. It includes a diagnostic sequence: check gateway status, inspect logs, run the safe restart script, verify a real process plus Telegram reconnect before declaring success.

That skill was not prompted. She hit the problem, solved it, and wrote the playbook (aka skill)

**Mistake goes in. Procedure comes out.**

This is not automatic perfection. Some generated skills were too generic. Some captured the wrong level of abstraction. I still had to inspect, prune, and occasionally delete them. The difference was not that supervision disappeared. The difference was that useful procedure started showing up without me authoring every improvement by hand.

## Running both

The OpenClaw squad handles research, content drafting, code review, and the newsletter on cron schedules. Hermes Monica runs as the chief of staff experiment on the same Mac Mini. She reads the same intel files Dwight produces on OpenClaw. Dwight writes DAILY-INTEL.md. Monica reads it. The handoff is a markdown file on disk.

OpenClaw gives me manual control and predictability. Hermes gives Monica a more self-maintaining improvement loop.

Both support the agentskills.io standard, so skills are portable across OpenClaw, Hermes, Claude Code, and Cursor. Nothing is locked to one platform.

I did not plan to run both long-term. But they complement each other. The agents I want full control over stay on OpenClaw. The agent I want to watch improve more autonomously runs on Hermes.

## How to test this yourself

Start the boring way: one agent, one job, one recurring workflow. Install Hermes with one command. Run 'hermes setup'. Pick a frontier model. Connect Telegram.

The question is not whether day one looks good. The question is whether day fourteen is better without you hand-tuning every session.

If you are already running OpenClaw, run Hermes alongside it. During setup, Hermes detects OpenClaw and offers to import your settings. Pick one agent. See what happens.

## Day 30 versus day 1

**The system that maintains itself compounds faster than the one that depends on you.**

OpenClaw is an agent you actively shape. Hermes is an agent that turns more of its own work into future procedure and improve itself. Not universally better. A different learning loop.

The best 24/7 agent is not the one that gives the best first answer. It is the one that gives a better answer on day 30 than day 1. Without you having to teach it every lesson by hand.

Start with one agent. One job. Let it run. Then check whether day 30 is better than day 1.

That is the test.

---

## Summary

Shubham Saboo describes running OpenClaw agents and comparing them with Hermes Agent as a 24/7 self-improving agent system. His core distinction is that many agents store context, but Hermes can turn completed work and mistakes into reusable skills/procedures, reducing the amount of manual correction needed over time.

The article frames the winning agent as the one that improves from day 1 to day 30, not the one with the best first answer. Hermes’ value is the correction loop: after complex work or failures, it can create/maintain skill files so the system leaves behind reusable method, not just chat history.

---

## Key Takeaways

1. Most agent systems make the human the learning loop: you notice failures, diagnose them, and write corrections.
2. Hermes shifts more of that loop onto the agent by turning completed work into reusable skill files.
3. Memory alone is not learning; storing chat history without extracting procedure is just hoarding.
4. The useful residue from agent work is a method/playbook that improves the next run.
5. Self-improvement still needs supervision: generated skills can be generic or capture the wrong abstraction.
6. Status screens are not verification; logs and real end-to-end behavior are the source of truth.
7. OpenClaw and Hermes can complement each other through shared markdown handoffs and portable agentskills.io skills.
8. Best test: run one agent, one job, one recurring workflow, then compare day 30 against day 1.

---

## Hermes-Related Interest

Directly relevant: this article is about Hermes Agent and the exact JB Vault/OpenClaw pattern. It reinforces the durable moat: not memory as storage, but skill creation as compounding procedure. For Junaid, the practical lesson is to design SaaS agents so every resolved customer workflow can become a reusable playbook: tire quote follow-ups, missed-call recovery, appointment confirmation, inventory cleanup, and shop-specific SOPs. Mistake goes in; procedure comes out.
