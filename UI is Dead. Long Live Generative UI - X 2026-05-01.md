# UI is Dead. Long Live Generative UI

**Source:** Atai Barkai (@ataiiam) / X Article  
**Date:** 2026-05-01  
**Original Published:** 2026-04-22T17:29:15.000Z  
**Link:** https://x.com/ataiiam/status/2049883896444055978

---

## Full Article

UI is Dead, SaaS is Dead. These are half-truths.

Two forces are quietly reshaping the entire landscape of how we interact with technology — simultaneously, and in different directions.

**The Headless Web.** Software is losing the traditional UI layer. Complex SaaS can now expose core capabilities to agents and humans via CLIs and APIs — without needing an interface at all. This is the "UI is dead" thesis, and it's real.

**Agent Generated Interfaces.** At the same time, UI is becoming more important than ever — as the surface where users interact with agents that can compose and generate interfaces on the fly.

One force kills UI. The other makes it the most valuable surface in software. Both are happening right now. In the same products. In the same week.

If you zoom out, the split looks something like this:

**CLI for agents. Generative UI for humans.**

Two surfaces. Two "users." Same product. Actually, most teams are only building one, which is why most AI products just feel broken.

---

## What's Actually Dying

In many senses, AI will "kill" a lot of UI. And it's for good reason.

Functionality hidden behind 7 button clicks. Docs with 1,000 pages of text and code. Dashboards nobody opens. Settings pages nobody touches.  Forms that turn you into a data entry clerk for software that should be helping you.

For 70 years, the interface shipped with the app. Mainframe. CLI. GUI. Touch. Web. Every era, same deal: the vendor decides what you see, you learn where to click. You adapted to the software. Not the other way around.

That contract is now broken.

Agents aren’t supposed click buttons or navigate dashboards- They call APIs and execute intent.

UI was built for users. But today, there are really two types: humans AND agents.

So what's actually dying is the idea that the vendor decides the interface and the user adapts.

---

## What's Being Born

UI itself is not dying. It's splitting, aggressively.

The **Headless Web** and **Agent Generated Interfaces** aren't competing — they're two sides of the same shift. Software is simultaneously going headless and becoming more visual than ever.

Just look at what was announced recently...

**Salesforce**

Marc Benioff said: **"No Browser Required. Our API is the UI."**

Read that line twice. Salesforce. The king of the SaaS dashboard. The company whose entire empire was built on clicking through pages just told the world the browser is optional. With 60 MCP tools, the whole platform is callable by any agent.

If Salesforce is saying the API is the UI, what do you think that means for yours?

[Media: 2046625483538706432]

**Slack**

Not even 24 hours prior, Slack went agent-native. MCP in Slackbot. Rich agent UIs in Block Kit. The entire platform is rebuilt around agents working AND presenting back to humans.

[Media: 2046625431005089792]

**And Anthropic too...**

Most engineering teams are already running Claude Code in a terminal every day. There’s no dashboard and no UI. Just a conversation and code gets shipped. That's the Headless Web side — the CLI for agents — already live in thousands of teams today.

Then recently, they launched interactive Generative UI artifacts. Agents don't just respond with text — they can generate the UI in real time. So you, the human, can understand by seeing, not just reading. That's the Agent Generated Interface side.

[Media: 2046844556038049792]

That's a company with one tool that kills UI and another tool that generates UI. On purpose. In the same week.

That's not a product strategy. That's proof of a split happening across the entire industry in real time.

If you just pay attention, that's three companies pointing to the same signal in the same week: **the interface is no longer one thing for one user.**

---

## The Generative UI Spectrum

"Generative UI" is thrown around hastily lately. Sure, we all got excited and many used it as another meaningless phrase bolded in a post. But let me explain what it really is (as someone building on the forefront of it all @CopilotKit.)

It's a **spectrum**. The dial runs from **more control to more flexibility.**

[Media: 2049880893955645440]

One end: your existing components, surfaced by an agent at the right moment. Same design system, radically smarter.

Other end: interfaces generated entirely on demand. Layout, content, interactions. No page a human designed in advance. Built for you, this exact moment, then thrown away.

I split Generative UI into 3 main sections: **Controlled - Declarative - Open.**

**C**heck out this article for more practical breakdowns on each one and where to start: https://x.com/CopilotKit/status/2047327612163293286

[Media: 2049880995139084289]

---

Most teams will land somewhere in the middle. That's fine. Nobody needs to build the future by Q3.

The point is that most teams aren't building anywhere on this spectrum. They're shipping a chatbox where the agent just returns text. Nobody wants this anymore. It's not exciting, it feels old, and most importantly- it doesn’t reflect the models output.

So how can you elevate your agentic chat experience? I think that @CopilotKit is the best place to start. It’s entirely open source and gives you the entire suite of tools in one place, in just minutes. Controlled, Declarative, and Open Generative UI. AND you can plug and play practically any agent backend. CopilotKit has over 30k GitHub stars and 300k weekly npm downloads.

**Check it out** → https://github.com/CopilotKit/CopilotKit

---

## Your Agent Deserves a Real UI

This brings me to the thing that's been driving me insane.

Long-form agent text responses.

We are living through the most powerful moment in software in 40 years. Models that reason, plan, execute, recover from errors, chain tools, manage sub-agents. And most teams are forcing their agents to respond with text. A LOT of it.

[Media: 2049881270381903872]

Seriously?

A text-only responding agent is how you'd design software if you gave up on making it intuitive.

An agent knows what to do. But you, the user, still need to see it before you trust it. Edit it. Approve it. Own it. That's not a conversation. That's interface work.

Your agent deserves a real UI. Nobody wants to read long-form text anymore.

Run one line of code to get a starter app for inspiration: **npx copilotkit@latest create**

---

## The Moment

The interface used to ship with the app. Now it ships with the agent.

Salesforce is going headless. Slack is going agent-native. Anthropic shipping both sides of the split in five days. All downstream of that one shift — the Headless Web and Agent Generated Interfaces, running in parallel.

UI isn't (entirely) dead. The static era is.

The teams that get this will build the vocabulary their agent speaks. Components composed at runtime. Interfaces that show up at the moment of intent and vanish when they're done.

The teams that don't will ship a text-only chatbox, call it AI, give it a nice design, and wonder why nothing sticks. But just like Claude and Slack have shown, you can have a chat-interface that interacts with humans much more than just through text.

It's such a rare opportunity to be this far on the frontier of a technology wave. This moment is not coming back.

---

## Where Do You Start?

What type of generative UI fits your needs? Maybe you have an agent from ADK, or LangChain, or Mastra, and they need different tools with separate workflows and goals?

This is what we're building at @**CopilotKit**.

It's the horizontal, frontend stack for Agents and Generative UI. Infrastructure for AI-native apps: headless or prebuilt UI, any LLM, any agent framework, any flavor of generative UI — **AG-UI, MCP Apps, A2UI** — you name it.

Start giving your agent a real UI. And stop settling on a text-only chat interface and calling it a product.

If you are interested, you can book a meeting with our lead engineers.
No selling, just engineer-to-engineer discussion.

**Give your agent a UI 👉 https://www.copilotkit.ai/contact-us**

[Media: 2049881609470386176]

---

## Source Tweet Metadata

- Author: Atai Barkai (@ataiiam)
- Tweet ID: 2049883896444055978
- X Article ID: 2046625084782092289
- Published: 2026-04-22T17:29:15.000Z
- Captured: 2026-05-01
- Views at capture: 23932
- Likes: 35
- Bookmarks: 81
- Reposts: 12
- Replies: 1

---

## Summary

Atai Barkai argues that “UI is dead” and “SaaS is dead” are only half true. Software is splitting into two surfaces: a headless/API/CLI surface for agents, and generative UI for humans. Agents should call APIs and execute intent directly, while humans still need rich, contextual interfaces to inspect, trust, edit, approve, and own what agents are doing.

The article frames recent moves from Salesforce, Slack, and Anthropic as evidence that interfaces are no longer one static product surface for one user. The future product has two users — agents and humans — and the winning teams will expose agent-callable capabilities while also letting agents compose useful UI at runtime instead of dumping long text into chat boxes.

---

## Key Takeaways

1. UI is not fully dying; static, vendor-decided UI is dying.
2. Products now have two users: humans and agents.
3. Agents need headless access: APIs, CLIs, MCP tools, and executable intent rather than dashboards.
4. Humans need generative interfaces: contextual UI generated or composed by the agent at the moment of need.
5. A text-only chatbox is a weak default for serious agent products; trust, approval, editing, and ownership are interface problems.
6. Generative UI exists on a spectrum: controlled components, declarative UI, and open/on-demand interfaces.
7. Salesforce, Slack, and Anthropic are all signaling the same split: API/CLI for agents, richer generated UI for humans.
8. For AI-native apps, frontend infrastructure needs to support any agent backend, any LLM, and multiple generative UI modes.

---

## Hermes-Related Interest

Strong relevance for Hermes product thinking. Hermes itself is headless-first on Telegram and tools, but this article argues the next step is agent-generated UI surfaces: cards, dashboards, approval views, generated artifacts, and task-specific controls that appear only when needed. For Junaid's SaaS products, this maps directly to exposing business actions to agents through APIs while giving shop owners/cleaning pros/tire shops clean generated UI for quotes, schedules, inventory decisions, approvals, and exceptions instead of long chatbot responses.
