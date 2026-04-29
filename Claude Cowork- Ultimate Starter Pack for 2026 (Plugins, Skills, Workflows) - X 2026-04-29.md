# Claude Cowork: Ultimate Starter Pack for 2026 (Plugins, Skills, Workflows)

**Source:** Corey Ganim (@coreyganim)  
**Date:** 2026-04-29  
**Original date:** Tue Mar 31 18:32:12 +0000 2026  
**Link:** https://x.com/coreyganim/status/2039048127961874705  
**Stats at capture:** 199,443 views, 390 likes, 1,286 bookmarks, 29 reposts

---

## Full Article

Most people set up Claude Cowork backwards.

They install plugins, run a few prompts, get mediocre results, and assume Cowork is overhyped.

The problem is with their order of operations.

I found the ideal Cowork setup sequence that actually sticks. Get these 7 things right, in this order, and Cowork goes from "interesting chatbot" to "I can't run my business without this."

***PS: doors are open to Build With AI. Founding member spots are filling.***

***$799/yr locks in forever. After 100 members it jumps to $999.***

***Everything in this article (and a lot more) is inside Build With AI: https://skool.com/buildwithai***

***-----------------------------------------------------***

## **Context files before plugins**

Everyone starts with plugins. That's backwards.

Cowork doesn't know who you are, what you do, or how you communicate. Without context, every plugin output is generic slop.

Create three markdown files first:

- about-me.md — name, role, company, communication style, timezone

- brand-voice.md — words you use, words you avoid, example sentences that sound like you, topics you cover

- current-projects.md — active work with deadlines, blockers, and links

Point Cowork to a folder with these files inside. Now every response is personalized before you install a single plugin.

Time investment: 30 minutes. Payoff: every interaction from this point forward.

## **The meta-prompt that prevents 90% of mistakes**

Before running any task, prime Cowork with this:

```
"You are my executive assistant. You have access to my computer and 
all connected tools. Always show me your plan before executing. Ask 
clarifying questions if anything is ambiguous. Never delete, move, or 
modify files without explicit approval."
```

This one paragraph stops Cowork from going rogue on your filesystem. It also forces plan-first execution, which means you catch errors before they happen instead of after.

Save this as a global instruction so you never have to type it again.

## **One workflow, not five**

The mistake I see every week: someone installs Cowork and tries to automate everything on day one. They build a morning dashboard, a meeting prep workflow, a content system, and an email summarizer all in the same afternoon.

Two days later they've abandoned all of them.

Pick ONE recurring task that takes you 20+ minutes and build that workflow first. Run it for a full week. Refine it. Then add the second one.

My recommendation for your first workflow: meeting prep.

```
"I have a meeting with [NAME] from [COMPANY] in 30 minutes. 
Research them, find recent news, pull any previous email 
conversations, and give me a one-page briefing."
```

This one workflow saved me more time than the other four combined. And it's the one that makes you look prepared in every call without doing any of the prep yourself.

## **The folder structure that scales**

Flat folders break at scale. Use this structure:

```
cowork-workspace/
├── context/ (about-me, brand-voice, projects)
├── successful-examples/ (your best emails, posts, proposals)
├── current-tasks/ (active deliverables)
└── references/ (SOPs, style guides, templates)
```

The "successful-examples" folder is the one most people miss. Drop your best 5-10 emails, your highest-performing LinkedIn posts, your best client proposals. Cowork reverse-engineers your wins and patterns instead of guessing your style.

## **Plugins in priority order**

Now that your context is set, plugins actually work. Install in this order:

1. Productivity — task management, scheduling, workflow automation. Foundation layer.

1. Your industry-specific plugin — marketing, sales, data, or whatever matches your daily work.

1. A custom plugin you build yourself — tell Cowork "I want to create a plugin for [your most repetitive task]. Interview me about the workflow, then build the plugin file." This takes 15 minutes and saves hours.

Skip everything else until these three are running smoothly.

## **Scheduled tasks (huge unlock)**

Plugins and workflows run when you tell them to. Scheduled tasks run whether you remember or not.

Start with one: a daily morning briefing that checks your calendar, flags important emails, and lists your top priorities.

Set it to run at 6am. By the time you sit down with coffee, your day is already organized. You didn't open Gmail. You didn't check Slack. Cowork already triaged everything.

This is where Cowork stops being a tool and starts being an employee.

## **The review loop that makes it better**

Here's what separates people who use Cowork for a week from people who use it permanently:

Every Friday, spend 10 minutes reviewing what worked and what didn't. Update your context files. Tweak your workflows. Add new examples to your successful-examples folder.

Cowork gets better the more it knows about you. But it only learns if you feed it.

## **Bottom line**

The prompting era is over. We're in the context era now.

The difference between "Cowork is a toy" and "Cowork runs half my business" is 30 minutes of setup done in the right order.

Context files first. Then the meta-prompt. Then one workflow. Then plugins. Then scheduled tasks.

Stop installing plugins and hoping for the best. Build the foundation and everything else works.

***PS: doors are open to Build With AI. Founding member spots are filling.***

***$799/yr locks in forever. After 100 members it jumps to $999.***

***Everything in this article (and a lot more) is inside Build With AI:***

***https://skool.com/buildwithai***

---

## Summary

Corey Ganim argues that people get poor results from Claude Cowork because they start with plugins instead of context. His recommended setup sequence is: create personal/business context files, install a safety-oriented meta-prompt, build one recurring workflow first, organize a scalable workspace, then add plugins and scheduled tasks.

The core idea is that AI tools become useful when they inherit durable context and examples, not when they are treated like prompt boxes. The article frames Cowork less as a chatbot and more as an operational employee that improves through weekly review loops and better context.

---

## Key Takeaways

1. Start with context files before plugins: `about-me.md`, `brand-voice.md`, and `current-projects.md`.
2. Use a global instruction/meta-prompt that forces plan-first execution, clarifying questions, and explicit approval before file modifications.
3. Pick one recurring 20+ minute workflow first, run it for a week, refine it, then expand.
4. Keep a `successful-examples/` folder so the agent can learn from high-performing emails, posts, proposals, and templates.
5. Install plugins only after context is in place: productivity first, then industry-specific, then one custom plugin for a repetitive workflow.
6. Scheduled tasks are the unlock: daily briefings and recurring automations turn the agent from a tool into an operating layer.
7. A weekly review loop is how the system compounds: update context, tweak workflows, and add new examples.

---

## Hermes-Related Interest

Highly relevant to Hermes/OpenClaw/JB Vault. It validates the 4-layer memory approach already in use here: durable markdown context, examples, scheduled jobs, and review/checkpoint loops. The strongest immediate angle for Junaid is productizing this pattern into practical workflows for TireManagerPro/OttoManagerPro: context files per shop, successful-example libraries for SMS/scripts, scheduled morning briefings, and one workflow at a time instead of broad generic automation.
