# Launching Claude Managed Agents

**Source:** Lance Martin (@RLanceMartin)  
**Date:** 2026-04-09  
**Link:** https://x.com/rlancemartin/status/2041927992986009773

---

## Full Article

TL;DR – Claude Managed Agents is a pre-built, configurable agent harness that runs in managed infrastructure. You define an agent as a template – tools, skills, files / repos, etc. The agent harness and the infrastructure are provided for you. The system is designed to keep pace with Claude's rapidly growing intelligence and support long horizon tasks.

**Why Claude Managed Agents:**
The Claude messages API is a direct gateway to the model: it accepts messages and returns content blocks. Agents built on the messages API use a harness to route Claude's tool calls to handlers and manage context. This poses a few challenges:

1. **Harnesses need to keep up with Claude** – Agent harnesses encode assumptions about what Claude can't do. These assumptions grow stale as Claude gets more capable and can bottleneck Claude's performance. Harnesses need to be continually updated to keep pace with Claude.

2. **Claude is running for longer** – Claude's task horizon is growing exponentially, already exceeding over 10 human-hours of work on the METR benchmark. This puts pressure on the infrastructure around an agent: it needs to be safe, resilient to infrastructure failures that happen over long horizon tasks, and support scaling.

**How to get started:**
Use the open source claude-api skill which works out of the box in Claude Code. Get the latest version of Claude Code and run the sub-command for Claude Managed Agents onboarding.

**Use cases:**
- **Event-triggered:** A service triggers the Managed Agent to do a task (e.g., bug flag → patch + PR). No human in the loop.
- **Scheduled:** Managed Agent scheduled for daily briefs (e.g., X or GitHub activity summaries).
- **Fire-and-forget:** Humans trigger the Managed Agent via Slack or Teams and get back deliverables.
- **Long-horizon tasks:** Claude runs over days/weeks/months on major challenges. Examples include forking karpathy's auto-research repo and exploring pretext library applications.

---

## Summary

Claude Managed Agents is Anthropic's managed infrastructure solution for running AI agents at scale. It provides a pre-built, configurable agent harness that handles tool orchestration, context management, and infrastructure so developers don't have to build and maintain these components themselves. The system is designed to handle long-running tasks (exceeding 10+ human-hours) with resilience and safety guarantees. Key use cases include event-triggered automation (bug → patch), scheduled reporting, fire-and-forget task assignment via Slack/Teams, and long-horizon autonomous research.

---

## Key Takeaways

1. Managed Agents solves the "harness staleness" problem — instead of building custom harnesses that constantly need updating as Claude improves, Anthropic provides and maintains the infrastructure.
2. The system is built for enterprise-scale long-horizon tasks — resilient to infrastructure failures, supports scaling to many agent teams, and designed for tasks running over days/weeks/months.
3. Easy onboarding via the open-source claude-api skill for Claude Code — run a subcommand and you're set up.
4. Multiple practical patterns: event-triggered (webhook → agent task), scheduled (daily briefs), fire-and-forget (Slack/Teams assignment), and long-horizon autonomous research.
5. Integration with tools like karpathy's auto-research repo and pretext library shows the flexibility for academic and research applications.

---

## Hermes-Related Interest

The managed infrastructure approach is relevant to Hermes — similar to how Claude Managed Agents offloads harness complexity, a well-designed agent system (like Hermes) needs robust infrastructure to handle long-horizon tasks, skill management, and context preservation. The event-triggered and scheduled patterns described are directly applicable to how Hermes could operate as a persistent, always-on agent. The "fire-and-forget" Slack/Teams integration model also maps to Hermes's multi-channel delivery (Telegram, cron jobs, etc.).
