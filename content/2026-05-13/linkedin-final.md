# LinkedIn Post — 2026-05-13

**Topic:** Why I shipped zero code today — and why that was the most productive thing I did.

---

I shipped zero lines of code today.

But I read 10 articles on agent harnesses, services-as-software, and generative UI. I saved 7 new entities to my wiki. I ran two Reddit research sessions to find tire shop and auto repair software pain points.

Sometimes the most productive build day looks like nothing on a commit graph.

The best piece I read was from Kartik at mem0ai. LangChain took the same underlying model — GPT-5.2-Codex — from outside the Top 30 to Top 5 on Terminal-Bench 2.0. The model never changed. Only the harness did. 52.8% to 66.5%.

That single result captures the shift happening right now: the model is commoditizing, but the harness is where the moat lives.

This maps directly to how I work. I'm one founder running 4 production SaaS products — TireManagerPro, OttoManagerPro, CleanBuddyPro, and FieldAgent AI. My stack is Next.js + Supabase + Twilio, but the real engine is a custom agent harness built on Hermes Agent and OpenClaw. It routes between Claude, GPT, and Kimi. It runs scheduled jobs, manages skills, and handles memory across sessions.

The harness is what lets one person ship like a team.

Other saves today that reinforced the same pattern:

- Alex Vacca built a $7M services-as-software agency, bootstrapped, no VC, 70 clients, 30+ people across 10 countries. The contract says agency. The margins say software.
- Atai Barkai on the split between headless software (for agents) and generative UI (for humans). Salesforce just announced "No Browser Required. Our API is the UI." The interface is no longer the product.
- Khairallah AL-Awady's $10K/mo AI automation playbook and 30-day Claude Code curriculum. The builders making money aren't the ones using AI as a search engine. They're the ones building systems that run without them.

I also ran two Reddit research hunts today — "tire shop owner software frustrated alternatives" and "auto repair shop management system terrible." Extracted URLs, pain points, and buying signals. That research feeds directly into product positioning for TireManagerPro V2 and OttoManagerPro.

Research is product work. It just doesn't show up in green squares.

One concrete lesson I took away: context engineering has fully replaced prompt engineering. Rohit put it well — the agent's behavior is an emergent property of what you put in the window. I now spend more time on CLAUDE.md, AGENTS.md, and skill files than on individual prompts. That shift is what made my agents reliable enough to run in production without babysitting.

If you're building with AI agents in 2026, my advice: stop obsessing over which model is "best" this week. Start obsessing over your harness — your evals, your context management, your tool dispatch, your progressive disclosure. That's where the compounding happens.

What does your invisible work look like?

---

*Written from raw material: 0 git commits, 10 wiki article saves, 2 Reddit lead-hunt sessions, 7 new entities/concepts created.*
