# LinkedIn Post — May 11, 2026

LangChain changed nothing but the harness around GPT-5.2-Codex and jumped 13.7 points on Terminal-Bench — same model, Top 30 to Top 5.

The model didn’t get smarter. The scaffolding did.

That single result captures the most important shift in applied AI right now: the model is no longer the product. The harness is.

I’ve been running 4 production SaaS products on custom harnesses built in Hermes Agent + OpenClaw. TireManagerPro, OttoManagerPro, CleanBuddyPro, FieldAgent AI. Not because the models are bad. Because the harness is where the moat lives.

What’s in the harness? Tool dispatch across 50+ tools. A 4-layer memory stack (Soul.md → AGENTS.md → session → context). Sub-agent orchestration. Sandboxed terminal and file operations. Evals tied to real product outcomes, not generic benchmarks.

Kartik’s recent article — 91K views, 2,299 bookmarks — names Hermes alongside Claude Code, Cursor, Devin, Factory Droid, Replit Agent, Vercel v0, and OpenClaw as "opinionated, custom, and tuned to its specific domain." That’s not marketing. That’s the architecture winning in public.

Andrej Karpathy retired "vibe coding" in February and renamed it "agentic engineering." Writing code stopped being the bottleneck. Designing the environment — the harness — became the hard problem. Every failure I fix becomes a permanent lint rule, hook, or sub-agent that improves all future runs with all future models. Harness investment compounds. Model releases reset the playing field.

My harness runs 24/7 on a VPS, orchestrates cron jobs, reads my Obsidian vault, writes content, and pushes to Git while I sleep. The human layer is judgment, relationships, taste, and accountability. Everything else is systematized. That’s the services-as-software model Alex Vacca used to bootstrap ColdIQ to $7M ARR with zero VC.

If you’re still treating the LLM as the product, you’re building on sand.

The teams winning in 2026 are the ones investing in the scaffolding around the model.

What does your harness look like?

---

*Sources: Kartik’s "Why Everyone Is Suddenly Building Their Own Agent Harness" (May 2), Khairallah AL-Awady’s 30-day Claude Code curriculum (May 4), Alex Vacca’s $7M services-as-software playbook (May 1). All saved and annotated in my JB Vault.*
