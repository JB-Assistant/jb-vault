# How to Get 10x More from AI Agents by Giving Them Less

**Source:** Startup Ideas Podcast / Rasmic  
**Date:** 2026-04-09  
**Link:** https://x.com/startupideaspod/status/2041958382870077930

---

## Full Article

When it breaks, ask the agent: "Why did you fail? What error did you get?" It will tell you. A 505 error. Insufficient credits. A wrong API call.
Pass that failure back. Tell it to fix the issue. Once it fixes it, say: "Update the skill so this does not happen again."
Each loop makes the skill tighter. Ras went through five of these cycles on his report generator before it became bulletproof.
The recursive loop:
Run the skill
It fails at some point
Ask the agent what went wrong
Tell it to fix the failure
Tell it to update the skill
Repeat
Step 06: Scale with Sub-Agents (Only When Ready)
Ras started with one agent. It handled everything: spreadsheets, sponsor emails, reports.
Once he had predefined workflows with battle-tested skills, he split into sub-agents. One for marketing. One for business. One for personal.
He has five sub-agents now. Each one has its own skills and context. He built up to that point over weeks.
The mistake most people make: spinning up 15 sub-agents and 30 skills on day one with zero tested workflows. Ras calls this "scaling for what looks cool" versus "scaling for productivity."
His take on tools like Paperclip: they look awesome. He used it. He loved it. But he believes if people spent two to three weeks building their own version from scratch (prompting Claude or OpenAI to handle what they actually need) their productivity would outperform any off-the-shelf tool.
Step 07: Shift Your Expectations
Most people expect this trajectory: a straight line from setup to results.
Reality looks more like a dip before the climb. There is an early investment period, roughly two weeks, where things feel broken. The agent calls APIs wrong. It misses steps. It feels like garbage.
Push through it. Work with the agent. Correct it. Build the skills. The payoff curve bends upward fast once the foundation is solid.
What the Models Need From You
The models are trained on enormous amounts of data. They already know React. They already know how to format a financial report. They already know the dollar sign.
What they lack: your specific workflow, your specific taste, your specific strategy.
Those are what you codify in skills. That is the only context that matters.
Build your own. Do not download someone else's. Your agent needs the context of your successful runs, not a stranger's template.
Action Checklist
Delete or minimize your agent.md file (keep only proprietary info)
Identify one workflow you want to automate
Walk the agent through the workflow step by step
Complete one successful run together
Tell the agent to create a skill from what it just did
Run the skill. When it fails, fix and update
Repeat until the skill runs clean
Only then consider adding sub-agents
Final Thoughts
Ras built this system around one principle: less is more.
The models are good. They will get better. But the harness, the tools, and the context you wrap around them will matter even more with each iteration.
A viewer who watched a previous Ras Mic episode got into coding, started a cake business, and now earns $150,000 a year. The information works when people act on it.
Your agent.md file is probably a waste of tokens. Skills are the move. Build them yourself. Build them iteratively. Build them from real workflows, not templates.
The one thing you have that the model will never have is your workflow, your taste, and your strategy. Codify that. Everything else, the model already knows.
How to get 10x more from AI agents by giving them less
@Rasmic  has been building AI agents for his YouTube channel, sponsor outreach, and content workflow. Most people overload their agents with massive configuration files. Ras stripped his down to almost nothing.
His agents got better.
This guide breaks down his system: why agent.md files are a trap for 95% of users, how skills work as a superior alternative, and how to build them through iterative runs instead of downloading someone else's.
Step 01: Accept That the Models Are Good
Previous episodes of this podcast challenged this point. That era is over.
Opus 4.6 is exceptional. GPT 5.4 is exceptional. The models have reached a level where the quality of output depends on what you feed them, not on the model itself.
The difference between quality and slop? Context.
Context is the information the model assembles to execute an action. It includes the system prompt, your configuration files, skills, tools, the codebase, and your conversation. All of it competes for space inside a finite context window.
The more junk you stuff in, the worse the output gets.
Step 02: Ditch the Agent.md File
Here's the hot take: 95% of people do not need an agent.md or claude.md file.
The reason is simple. These files get added into the context at every single turn. A 1,000-line claude.md file burns roughly 7,000 tokens per run. Every run.
Ras compared it to telling your podcast co-host "you need a microphone" before every single episode. He already knows. The model already knows too.
If you're building a website with Claude Code and you write "this codebase uses React" in your agent.md: unnecessary. The agent has the codebase in context. It can check.
The 5% exception: proprietary information specific to your company or a methodology that must be referenced in every conversation. If you have that, keep it. Everyone else: delete the file.
Step 03: Use Skills Instead
Skills use a concept called progressive disclosure.
A skill file has three parts: a name, a description, and a body of detailed instructions. When you create a skill, only the name and description get added to context. The full body stays out until the agent decides it needs it.
The math:
Agent.md file (1,000 lines): ~7,000 tokens every turn
Skill name + description: ~53 tokens every turn
Full skill body: loaded only when triggered
That difference compounds. The closer your context window fills to capacity, the worse the agent performs. Ras compared it to cramming for an exam the night before: you shove everything in, and nothing sticks.
Keep the context window lean. Save it for the conversation that matters.
Step 04: Build Skills the Right Way
Most people create skills wrong. They either write them from scratch or ask AI to generate one cold. Both approaches fail because the agent has zero context on what a successful run looks like.
Ras's method:
Identify the workflow. Pick one task you want the agent to handle. Ras chose sponsor email evaluation.
Do the workflow together. Walk the agent through it step by step. Forward the sponsor email. Tell it: research this company. Check their Twitter, YouTube, TrustPilot, funding history. If two of these sources are missing or in bad standing, automatic rejection.
Correct mistakes in real time. The agent will miss things. When it skipped TrustPilot reviews, Ras asked "why didn't you check this?" The agent course-corrected.
Complete a successful run. Once the full workflow executes correctly, tell the agent: "Review what you just did. Create a skill from this." Now it has real context from a real success.
This is the key insight: the agent mimics you perfectly, but you have to give it something to mimic.
Ras built a report generator that pulls from eight data sources (Notion, Dub Analytics, YouTube Analytics, Twitter Analytics, and more). It runs flawlessly in 10 minutes. It took five iterations of this build-correct-update loop to get there.
Step 05: Recursively Improve Skills
The skill will still fail sometimes. That is the opportunity.

---

## Summary

Rasmic breaks down why most people sabotage their AI agents with overloaded configuration files. His core argument: the models are already excellent — what distinguishes quality output from slop is context management. He advocates ditching the agent.md file (burns ~7,000 tokens per run unnecessarily) in favor of skills, which use progressive disclosure to keep the context window lean. The key insight is building skills iteratively through real workflows, not downloading templates.

---

## Key Takeaways

1. **Ditch agent.md** — 95% of users don't need it. It burns tokens every turn on info the model already knows. Keep only proprietary company/methodology info.
2. **Skills > agent.md** — Progressive disclosure means only name/description (~53 tokens) in context until triggered. Full body loads on demand.
3. **Build skills through real runs** — Don't write them cold. Walk the agent through the workflow step by step, correct mistakes live, then have it create the skill from a successful run.
4. **Recursive improvement loop** — Run skill → fails → ask why → fix → update skill → repeat. Ras did 5 cycles on his report generator before it was bulletproof.
5. **Scale sub-agents only when ready** — Start with one agent handling everything. Split into specialized agents only after you have battle-tested workflows.
6. **2-week dip is normal** — Early period feels broken. Push through. Correct the agent. Build the skills. Payoff curve bends fast once foundation is solid.
7. **Build your own, not templates** — Your workflow/taste/strategy is what the model lacks. Codify that. The model already knows everything else.
8. **Less is more** — The harness you build matters more than the model itself. Keep context window lean.

---

## Hermes-Related Interest

This post is essentially a meta-guide for how to use agents like me more effectively — directly applicable to how you work with Hermes. The key principle: **codify your specific workflow in skills rather than relying on generic prompts or configuration files**. The recursive improvement loop (run → fail → ask why → fix → update skill → repeat) mirrors exactly the cycle Ras used to get his report generator to run flawlessly.

The token math on skills vs agent.md is also a useful frame: keeping context lean makes every conversation better. Worth considering whether the Hermes setup could benefit from a similar progressive disclosure approach.
