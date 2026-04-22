# The Ultimate Guide to Prompting AI Agents

**Source:** Matt Shumer (@mattshumer_)  
**Date:** 2026-04-22  
**Link:** https://x.com/mattshumer_/status/2046738742161949135

---

## Full Article

I've spent the last seven years prompting AI systems, and I've tried just about every approach you can imagine.

Today, I'm sharing my framework for getting the most out of AI agents.

Prompting an AI agent isn't the same as prompting a chatbot. A chatbot answers. An agent works. It can read your files, write code, run tests, open a browser, take screenshots, and iterate on its own output until it's perfect. It can spend an hour on a task and come back with something real.

But only if you tell it what "real" means.

The biggest mistake I see is people prompting agents the way they used to prompt chatbots: they give it a sentence-long instruction, and out comes a generic answer. But agents don't need a sentence. They need a brief.

In this post I'll walk you through the framework I use to write briefs that actually get good work out of an agent. I call it the 3 C's: context, constraints, and composition.


## 1. Context

Context is everything the agent needs to know to do the job, plus everything it needs access to. That includes the situation, the goal, the audience, and what success looks like. But it also includes the actual materials. The deck. The data file. The brand guidelines. The previous version. The repo. The relevant documentation. Whatever the agent will be touching, it should know it exists and where to find it.

Most people dramatically under-context their agents. They'll ask one to "make a deck about Q3" without sharing last quarter's deck for reference. They'll ask it to "analyze the user feedback" without specifying which file, what segment, or what decision the analysis is supposed to inform. They'll ask it to "refactor the auth module" without pointing it at the existing tests, the team's style guide, or the design doc the module is supposed to follow.

So the agent guesses. And when an agent guesses, you usually don't notice until it's an hour deep into the wrong thing.

Compare these two prompts:

The second prompt does two things. It tells the agent what the job is, and it tells the agent where to find everything it needs to do the job. Both matter.

The intern test. I use a simple test to check whether I've given enough context. Imagine an intern shows up on their first day and you hand them this prompt as their assignment. Could they get to work without coming back to ask you anything? If yes, the brief is probably complete. If no, your agent has the same questions the intern would. The agent just won't ask them. It'll likely guess.


## 2. Constraints

This is where prompting agents diverges most from prompting chatbots. Constraints aren't just rules about the answer. They're the verification approach. They describe how the agent should check its own work as it goes, and what counts as actually being done.

Agents can run code. They can open files. They can take screenshots. They can re-read their own output and notice mistakes. So your constraints should make them do those things.

A weak constraint is "don't make things up." A real constraint says:

These aren't suggestions. They're stopping conditions. The agent is allowed to declare itself done when, and only when, those conditions are met.

This matters because of how agents tend to fail. They rarely produce obviously wrong work. They can produce plausible-looking work and confidently announce they're done (though this gets less and less likely every month as models improve). The slide deck opens to nine slides of overflowing text. The research summary has three citations that don't say what the agent claims they say. The refactor compiles and broke three tests the agent never re-ran. In every case the agent told you it was finished. It just hadn't actually verified anything.

You prevent that by making verification part of the work, not an optional afterthought.

A few patterns worth stealing:

The shift here is from "follow these rules while you write" to "complete this work, including the verification, and then tell me what you did and didn't check."


## 3. Composition

Composition is how you want the deliverable structured, and it's the most underrated of the three. Agents can produce great work, but if you don't tell them what shape it should take, they'll usually default to whatever the model has seen most often. That's almost never what you actually want.

Specify the shape, for example:

Format matters because format changes thinking. An agent told to produce "an analysis" will write paragraphs. An agent told to produce "a one-page memo with a recommendation, three supporting reasons, and the strongest counterargument" will actually structure the work that way as it goes.

Instead of asking "what should I do?", ask for the answer in a specific shape, like:


## A reusable template

Here's a template you can adapt to almost any agent task:

And here's a real version, filled in:

That brief will get you a real board deck. "Make me a Q3 deck" will get you twelve slides of disconnected charts and a narrative that quietly avoids the misses.


## Why this matters more for agents

Chatbots could be sloppy and you'd notice in the answer, within a few seconds. Agents can be sloppy and you might not notice until the deck is sent, the report is in front of your boss, or the change is merged. They take real actions. Their mistakes have real surface area.

So the prompt has to do more work. It has to give the agent enough context to do the job, enough verification to trust the result, and enough structure that the deliverable comes out shaped the way you can actually use it.

The skill is shifting from "prompt engineering" to "task specification." You're writing a brief for someone who can do real work but doesn't know your team's standards, your previous decisions, or what "done" looks like to you. That brief is the lever.


## Bad prompting vs. good prompting

A few side-by-side examples make it concrete.

For a deck, the bad version is "make me a deck about Q3 results." The good version is: "Build a deck on Q3 results for our exec team meeting next Tuesday. Source data is in /data/q3_metrics.csv. Last quarter's deck is at /decks/q2_review.pptx. Match its style and structure. After generating, open every slide, screenshot it, and confirm the layout looks clean. Flag any slide where the data is ambiguous or the chart doesn't tell a clear story."

For a research task, the bad version is "research what our top three competitors are doing on pricing." The good version is: "Research current pricing pages for [Competitor A], [Competitor B], and [Competitor C]. For each, capture the tier names, prices, included seats, and any notable add-ons or restrictions. Visit each site directly and screenshot the pricing page as evidence. Don't include anything you couldn't verify on the live page. Output a single comparison table plus a short paragraph on what's different from our current pricing."

For a content draft, the bad version is "write me a launch announcement." The good version is: "Draft a launch announcement for the new export-to-CSV feature, aimed at existing customers on the Pro plan. Tone should match the last three posts on our blog (linked). Keep it under 300 words. Lead with the user benefit, not the feature. After drafting, re-read it once and cut anything that sounds like marketing fluff. Give me the final version plus a one-line summary of what you cut and why."

For a code change, the bad version is "fix the bug in the checkout flow." The good version is: "There's a bug in the checkout flow where the cart total doesn't update when a coupon is removed. Repro is in ticket #4421. The relevant code is in /src/cart. Existing tests are in /tests/cart. Add a failing test that reproduces the bug, fix it, and don't finish until the full cart test suite passes. Open a PR with the test, the fix, and a one-paragraph explanation of the root cause."


## The most important phrase

The single highest-leverage phrase in agent prompting is don't finish until. Use it constantly.

Don't finish until you've opened the file and confirmed it looks right. Don't finish until every cited source has been verified. Don't finish until you've listed what you didn't check. Don't finish until the tests pass. Don't finish until the linter is green.

It works because it changes what "done" means. Without it, the agent is done when it has produced a thing. With it, the agent is done when it has produced a thing and confirmed the thing is correct. Those are very different stopping conditions, and the gap between them is where almost all agent failure lives.


## Pulling it together

The 3 C's aren't really a formula. They're a checklist for being specific. Have you given the agent the situation and the materials? Have you told it how to verify its own work and what counts as done? Have you described what the deliverable should look like? If yes, the output is usually good. If no, it usually isn't.

Working with agents has started to feel less like typing into a chatbot and more like briefing a contractor who can do the job but has never met you. The thing that pays off is being able to write that brief well: clear enough that the work gets done, specific enough that you can trust the result. Most of what people now call prompt engineering is really just that.

If you've made it this far, try https://agent-s.app, which does most of this automatically. It's the most powerful agent in the world, but it's so simple that my mom uses it daily.

And send this to a friend who might find it useful!

---

## Summary

Matt Shumer shares a comprehensive framework for prompting AI agents based on seven years of experience. He distinguishes between chatbot prompting and agent prompting, emphasizing that agents need different instructions since they can perform complex, multi-step tasks autonomously. His approach focuses on being specific about goals, providing context, setting constraints, and defining success criteria clearly.

The guide covers essential principles like starting with clear objectives, providing necessary context without overwhelming the agent, and setting appropriate boundaries. Shumer emphasizes the importance of iterative refinement and testing prompts to achieve optimal results.

---

## Key Takeaways

1. **Agent vs Chatbot Distinction**: AI agents require different prompting strategies than chatbots since they can perform complex, multi-step tasks autonomously
2. **Specificity is Critical**: Vague instructions lead to poor results; agents need clear, specific goals and success criteria
3. **Context Matters**: Provide relevant background information and constraints to guide the agent's decision-making
4. **Iterative Refinement**: Test and refine prompts based on actual results rather than theoretical perfection
5. **Practical Framework**: Use structured approaches with clear objectives, context, constraints, and success metrics

---

## Hermes-Related Interest

This is highly relevant to Hermes and AI agent development! Shumer's framework aligns with best practices for autonomous agent prompting, particularly the emphasis on:

- **Multi-step task execution** - exactly what Hermes does with tool calling and complex workflows
- **Context management** - crucial for Hermes's memory and session handling
- **Iterative improvement** - key for developing better agent behaviors and skills
- **Constraint setting** - important for safe and effective agent operation

The practical insights from someone with 7+ years of AI prompting experience, including time as CEO of HyperWriteAI, provide valuable guidance for improving Hermes's own prompt engineering and agent orchestration capabilities.
