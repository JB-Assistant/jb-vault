# How to Build a Services-as-Software Agency: The 5-Layer Operating Stack

**Source:** Alex Vacca (@itsalexvacca)  
**Date:** 2026-04-30  
**Original published:** Wed Apr 29 20:14:09 +0000 2026  
**Link:** https://x.com/itsalexvacca/status/2049583033003765890?s=46&t=ub4QNKLqvh3yU44VgGVYlQ  
**Stats at capture:** 72 likes, 13 reposts, 155 bookmarks, 4926 views  

---

## Full Article

Two weeks ago I published the playbook for building a $7M services-as-software business. (https://x.com/itsalexvacca/status/2044502868556992937)

In this article, I'm putting together the entire operating system to run your own AI outbound service-as-a-software company. 

We've sent 23M+ cold emails across 2,000+ campaigns at ColdIQ for 400+ B2B clients. The system that ran every one of them is five layers:

- **Layer 1: Data and Intelligence**. Turn the universe into a tiered, scored, enriched account book.

- **Layer 2: Outreach and Execution**. Get the message in front of the buyer, tiered by prospect value.

- **Layer 3: Orchestration**. Claude Code as the runtime that connects every API and runs the actual work.

- **Layer 4: Reporting and Client Comms**. Make a service feel like a product to the client.

- **Layer 5: People and Knowledge**. Keep the operating system intact when the operator changes.

Underneath all five sits a feedback loop that turns every campaign into a training example for the next one. That's what I want to walk you through.

[Embedded media: 2049573815219593216]

## Layer 1: Data and Intelligence

The job of this layer is simple to state and hard to execute. Turn the addressable universe into a tiered, scored, enriched account book that knows who's worth touching, who's worth ignoring, and who's worth a personalized hand-written sequence from a senior AE.

The tools we run inside it:

- Apollo for the universe pull. 

- Clay as the data layer that sits on top, where one table runs across every client we work with and 3X's their useful TAM. ColdIQ is Clay's #1 partner globally and one of four Elite Studio Clay Experts, and the table we run inside Clay is the closest thing the agency has to a memory. 

- PredictLeads handles real-time firmographic signals like funding rounds and hiring triggers. 

- Common Room covers community and product-adjacent signals. 

- Apify and Exa handle anything the off-the-shelf tools don't.

For verified contact data we run a three-vendor waterfall. 

1. Wiza runs first against LinkedIn profiles. 

1. FullEnrich cascades through 20+ providers under the hood to catch what Wiza missed. 

1. Prospeo cleans up the residual at 98%+ verified accuracy. Run the full waterfall and email coverage lands at 90%+ even on harder ICPs.

The layer's policy file is scoring-criteria.md. It defines what counts as Tier 1, Tier 2, Tier 3, or DQ for a given client. Two non-negotiable rules sit inside it:

1. Stack at least five signals per tier. One signal is functionally a guess, and Tier 1 lists built on a single signal don't survive a manual sanity check.

1. Score by signal density, not company size. A 200-person company hitting four of our five intent signals is a stronger lead than a 2,000-person company hitting one.

When this layer runs cleanly, the numbers come out the way you want them to. In one recent campaign rebuild we ran inside Claude Code, an Apollo CSV turned into 153 contacts in 90 seconds, and 149 of them had verified emails attached by the time the script finished. Same output you'd get from a half-day in the Clay UI, in a fraction of the time, with the policy file controlling every threshold so the rule doesn't drift between operators on the team.

The layer outputs the tiered account book. Everything that happens after this point is downstream of how disciplined this layer was.

Learn more about tiering your ICP: 

[Embedded X post: https://x.com/i/status/2047046395111366726]

## Layer 2: Outreach and Execution

The job of this layer is to put the message in front of the buyer across email, LinkedIn, and phone, with the routing decided by what the prospect's tier was in Layer 1.

We run Instantly for primary email volume. The platform handles warmup, deliverability monitoring, and inbox rotation underneath every campaign. We send 500K+ cold emails per month across four ESPs simultaneously, and the reason for four ESPs and not one is that deliverability in 2026 is a hard gate, not a best practice.

As of today, Microsoft killed Basic Auth for outbound mail. That is the kind of change that breaks single-ESP setups quietly, until a campaign goes silent and nobody knows why for a week. Across 2026 the gatekeepers (Google and Microsoft) have been retraining the spam classifiers on billions of new examples per month. The spam complaint threshold sits at 0.1%, which means one to two complaints per thousand emails can cook a sender domain entirely. 

Instantly's 2026 benchmark report makes one thing clear about deliverability. The difference between hitting inbox and not hitting it is almost entirely sender infrastructure.

[Embedded media: 2049574286210523136]

The infrastructure rules that have to be in place before any of this works:

- Never send from your primary domain. Use sender domains spun up specifically for outbound.

- Warm inboxes for four weeks before sending real campaigns.

- SPF, DKIM, and DMARC configured on day one of the warmup.

- Cap each inbox at 20-30 emails per day. Scale by adding inboxes, never by raising the cap.

The layer's policy file is copy-frameworks.md. It holds the patterns we've trained on the same emails that have generated $10M+ for our clients, plus a master prompt that clones the buyer psychology of our best AE on a good day. Four operating rules inside it determine whether replies actually show up:

- Cap each email at 80 words. Longer copy reads less.

- Relevance beats personalization. Use the signal data already pulled in Layer 1 instead of relying on first-name interpolation.

- Exactly one CTA per email. "Worth a conversation?" still works after a decade.

- A/B test the offer, not the adjectives wrapping it.

Here's the complete GTM playbook to run in 2026 (goes deeper on the aspects mentioned in this section):

[Embedded X post: https://x.com/i/status/2032124171560583250]

## Layer 3: Orchestration. Claude Code as the Runtime.

The job of this layer is to connect every API and run the actual work.

For us, the runtime is Claude Code. The alternatives we tested (Cursor, Lovable, n8n positioned as the central layer) didn't survive the build. What survived was Claude Code with markdown files as the policy and a skills folder underneath as the memory.

Sitting at the bottom of every project is CLAUDE.md, the project-level operating system. Our Head of GTM has spent 600+ hours inside Claude Code across our build work, and the headline finding from that time has been simple. Without a clear, well-maintained CLAUDE.md, the model produces generic AI output regardless of the prompts. We keep ours under 200 lines, written in clear and direct language, and we update it whenever a convention or workflow shifts.

Sitting on top of that file, three policy markdown files get read at the top of every session:

- scoring-criteria.md from Layer 1.

- copy-frameworks.md from Layer 2.

- instantly-api-docs.md so the model stops guessing at endpoints when it builds the campaign payload.

And underneath everything sits .claude/skills/. Every time Claude Code makes a working API call, the script gets saved into that folder. Next campaign, the same script gets pulled out and run again, and the model only has to write a fresh script when something genuinely new is happening. Over time the folder fills with battle-tested code, and each next session opens with more of the plumbing already in place than the one before. Across the agency we currently run 58 Claude Code skills across 7 orchestrators, with 137 triggers wired underneath them.

On top of skills sit MCP servers for the live integrations the runtime needs to take real actions. We have one set wired in at the project level for Gmail, Sheets, Slack, the CRM, and the various databases the campaigns touch.

[Embedded media: 2049574700549013504]

The pipeline that runs through this layer end to end is five steps: score, source, enrich, write, push. Each step is a prompt to Claude Code, and each prompt assumes the previous step's output is already sitting in the project folder. A campaign that used to take a full afternoon at ColdIQ now ships in under an hour, and the workflow gets sharper every time we run it because the markdown files and the skills scripts improve with every campaign.

A few slash commands worth knowing for the day-to-day inside Claude Code:

- /init builds a starter CLAUDE.md from existing code in your project.

- /compact summarizes context when a session starts running long.

- /memory reveals what the project currently remembers about itself.

- /cost tracks token usage as a session runs.

The whole layer is forkable across clients, which is the section coming up after the loop.

You can find more information on setting up your project files and using Claude code to run outbound, here:

[Embedded X post: https://x.com/i/status/2049224354404389181]

## Layer 4: Reporting and Client Comms

The job of this layer is to make the service feel like a product to the client.

The cadence we run is the same across every account from day one:

- A live dashboard for every client, where every email sent, every reply, and every meeting booked shows up in real time. No monthly PDFs, no polish theater.

- A weekly Loom from the account owner covering wins, misses, and the next-week plan.

- A quarterly review with the decision-maker, not just the operator. That's where renewals happen.

The whole point of this layer is the experience asymmetry it creates. 

The contract on the table looks like a service. The dashboard, the telemetry, and the weekly recap make it feel like a product. Clients consume the work the way they consume SaaS, in real time, on their schedule, without needing to wait for a monthly report. 

Once a client has been inside that experience for two quarters, leaving feels like ripping out an internal tool, not switching agencies. The contract the client signed and the experience the client has are running in parallel, and the experience is the part that compounds into retention.

## Layer 5: People and Knowledge

The job of this layer is to keep the operating system intact when the operator changes.

This is the layer most agency founders never build, which is why most agency founders are still the bottleneck of their own business at $1M ARR. The work they did in year one lives in their head. The next hire learns the work by sitting next to them, which means the agency only scales as fast as the founder can clone themselves. That ceiling is real, and it doesn't need to be there.

The fix is a documentation library that turns the work into an asset. What we keep:

- **Workflow files** in markdown. One file per repeatable task, written as if you were handing it to someone who started Monday.

- **Loom videos** for anything involving a cursor, titled by client name and task.

- **Decision logs per client.** Every "why did we do it this way" note goes there, dated.

- **A failed-campaigns file.** What was tried, why it died. The most valuable artifact you'll produce in year one.

The hiring sequence sits on top of the documentation. Hire in this order, and don't skip:

1. **Delivery operator.** Someone who can run multiple accounts alone after a short shadowing period. The job is execution, not strategy.

1. **Technical automator** fluent in your stack. Their job is to turn workflow files into running agents.

1. **Head of delivery.** This is the person you were. They own quality and manage the first two hires.

Do not hire a marketer, a salesperson, or a COO before the delivery layer can run without you. Every early hire that isn't delivery is a rounding error at best and a burn-rate accelerator at worst. I replaced the last piece of work that still required my attention, and revenue went up the month after. The work was the ceiling.

The data moat sits underneath all of it. Every campaign produces inputs (enriched leads, technographic signals, tier assignments) and outputs (replies, meetings, booked deals, lost deals, the reasons each one went the way it did). Save both. The raw version and the cleaned version. 2,216 campaigns is the dataset that came out of doing the work by hand in year one. No SaaS competitor can buy, license, or ship around a dataset that deep, because nobody else ran the work for that long.

## How the 5 Layers Compose: The Compounding Loop

Most outbound stacks are funnels. A list goes in at the top, copy goes out the side, pipeline trickles out the bottom, and when the campaign ends, so does the data. Replies sit in Smartlead, bounces in Instantly, meeting notes in HubSpot, LinkedIn engagement in Sales Navigator, and enrichment output in Clay until the next pull overwrites it. Five data stores, zero feedback, and the next campaign starts from the same priors as the last one.

A real services-as-software stack is structurally different. Every output becomes an input somewhere else, which is why the system gets smarter every week instead of resetting every Monday.

There are four feedback edges that connect the five layers. Skip any one of them and the loop turns back into a fancier funnel.

**Edge 1: Reply and bounce data into Layer 1 targeting.** When a reply comes back saying "wrong contact" or "we don't buy from EU vendors," that's enrichment data your list missed, dressed up as a sales objection. A reply-classification step reads the reply, tags the reason, and writes it back to a "negative signal" column in the Clay table. The next list pull reads that column as an exclusion filter automatically.

**Edge 2: Meeting outcomes into Layer 2 copy and Layer 1 ICP.** Every disqualified meeting routes two ways. The stated objection feeds the next campaign's copy pass as a "do not promise this" constraint. The stated-need-we-don't-serve feeds the next list build as a lookalike input for who else might have the same need.

**Edge 3: Engagement signals into Layer 2 cold email recognition.** When a prospect reacts to a post from one of our team accounts, that engagement gets scraped, enriched, and written as a new column in the Clay table against the person's company. The next outbound that touches that company references what they engaged with, by name, in the first sentence of the email.

**Edge 4: Enrichment plus outcome into Layer 1 list-building priors.** Every campaign produces both an enrichment dataset and an outcome dataset. Both feed back into the next list build as priors, which means campaign two is seeded by everything campaign one learned.

The Clay table is the loop's memory. It accumulates state across every campaign, and that's what 3X's the useful TAM for every client we run. Funnels end at the bottom of the page. Loops keep paying for years.

## Forking the Whole Stack

The architecture survives client and campaign-type swaps cleanly. Onboarding a new client becomes mostly a writing exercise.

Each new client folder starts as a copy of the canonical template. Two voice-specific files get rewritten:

- scoring-criteria.md for the new ICP, with new signal definitions and new tier thresholds.

- copy-frameworks.md for the new tone of voice, with new templates and new cadence rules.

Everything else carries over. The API docs file stays. The .env configuration carries the same vendor keys. The .claude/skills/ folder carries the saved scripts that have been battle-tested across previous campaigns. The five layers' folder scaffolding (intelligence, outreach, orchestration, reporting, knowledge) all get inherited from the template without modification.

A new account spinning up in production looks like this. A delivery operator copies the template folder. They rewrite the two voice files for the new ICP and tone. They run the score-source-enrich-write-push pipeline through Claude Code, which pulls scripts out of the saved skills folder and only writes new ones for genuinely new edge cases. The first campaign goes live inside the same week the contract was signed.

That's the move that separates services-as-software from the agency model that came before it. In the old model, every new client meant every new piece of plumbing got rebuilt by hand. In the new model, every new client means a forked folder and two rewritten files. 

The work that compounds across clients lives in the template. The work that's specific to the client lives in the two voice files. Nothing in between.

## What I'm Building for the People Who Want to Do This

The same five-layer system I described above runs the agencies launched out of the AI Agency Accelerator. 155 of them so far. 12 weeks. Full access to the template library, the scoring and copy frameworks, the skills folder my team runs every day, and 11 AI agents handed over from internal ColdIQ ops.

The program isn't for everyone. It isn't for someone who wants passive income, doesn't want client work, or just wants to learn about AI. It's an operating system for operators who want to install this stack inside their own agency, ship the first campaign through it inside week one, and stay in the work long enough for the loop to compound. If that's you, head to aiagency.io.

---

## Summary

Alex Vacca lays out ColdIQ's five-layer operating stack for running a services-as-software AI outbound agency: data/intelligence, outreach/execution, orchestration, reporting/client comms, and people/knowledge. The core idea is that a service becomes software-like when the workflow is encoded into reusable markdown policy files, Claude Code skills, dashboards, feedback loops, and repeatable client templates.

The strongest part is the compounding loop: every campaign output — replies, bounces, meetings, outcomes, enrichment results, engagement signals — feeds the next campaign's scoring, copy, and targeting. Instead of a one-off agency funnel, the business becomes a system where process, scripts, templates, and data accumulate across clients.

---

## Key Takeaways

1. Services-as-software is an agency/service wrapped in product-like operations: live dashboards, standardized workflows, reusable automation, and repeatable delivery templates.
2. The data layer is the foundation: build tiered account books from multiple intent/firmographic/community signals, score by signal density, and enrich with a vendor waterfall.
3. Claude Code acts as the orchestration runtime: CLAUDE.md plus policy markdown files plus a .claude/skills folder for reusable scripts/API calls.
4. Outbound execution is tiered by prospect value and constrained by deliverability: separate sender domains, 4-week warmup, SPF/DKIM/DMARC, 20-30 emails per inbox/day, and infrastructure redundancy.
5. Client retention comes from making the service feel like internal software: real-time dashboard, weekly Loom, quarterly executive review, and operational telemetry.
6. The knowledge layer removes founder bottlenecks: markdown workflows, Looms, decision logs, failed-campaign files, and a hiring sequence focused on delivery first.
7. The compounding loop turns campaign outcomes into future priors, so each client/campaign improves the next instead of resetting from zero.
8. New clients should be forked from a canonical template; only scoring criteria and copy frameworks are rewritten while plumbing and skills carry over.

---

## Hermes-Related Interest

Very relevant to Hermes/JB. This is basically the same pattern as the shared-vault memory system: markdown policy files + reusable skills + live tools + feedback loops. For Junaid's products, the actionable translation is to turn TireManagerPro/Otto/CleanBuddy ops into services-as-software playbooks: one canonical delivery template, product dashboards, client-specific policy files, and reusable agents/scripts for lead sourcing, onboarding, follow-up, and reporting.

Specific TireManagerPro angle: this can become a lead-hunter + outbound engine for tire shops where Layer 1 scores shops by pain signals, Layer 2 writes relevant outreach, Layer 3 runs Hermes/Claude Code workflows, Layer 4 shows pipeline/results, and Layer 5 stores every script, objection, and winning message back into the vault.
