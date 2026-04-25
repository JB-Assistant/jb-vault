# Designing for Agents — Teddy Riker (Product @ Ramp)

**Source:** https://x.com/teddy_riker/status/2047312986696454584
**Author:** Teddy Riker (@teddy_riker) — Product @ Ramp
**Published:** April 23, 2026
**Views:** 363K+
**Bookmarks:** 2,454
**Hermes angle:** 🔴 CRITICAL — Junaid needs to build OttoManagerPro/TireManagerPro for agents, not just humans

---

## TL;DR

The software interaction model is flipping: **80% of interaction will soon be through AI agents, not human UI.**

Salesforce just unveiled "Headless 360" — exposing every capability as API/MCP/CLI so agents operate the system without ever opening a browser. Ramp's MCP usage grew **10x in 3 months**.

Three principles for designing for agents:
1. **Teach agents how to succeed** — give them specs proactively
2. **Build feedback loops** — observe what agents are trying to do
3. **Mind the context gap** — each agent has context the other lacks

---

## The New Interaction Pattern

**Old model (past 20 years):**
```
User → Interface → Database
```

**Current model:**
```
User → User's Agent (Claude/ChatGPT) → Database
```

**Emerging model:**
```
User → User's Agent → Software's Agent → Database
```

Two LLMs working together. The software's agent handles complexity: business logic, rules, context the user's agent doesn't have.

---

## 1. Teach Agents How to Succeed

**Example — Notion (does this RIGHT):**
Every time an agent writes to Notion via MCP, it fetches the spec first:
> "For the complete Markdown specification, always first fetch the MCP resource at notion://docs/enhanced-markdown-spec. Do NOT guess or hallucinate Markdown syntax."

Result: Tables, bullets, italics, lists — the agent **never fails**.

**Example — Slack (does this WRONG):**
Agent assumes standard markdown. Doesn't adhere to Slack's formatting. You spend more time editing than writing.

**Rule:** Think about what your agent's callers need to know to succeed, and give it to them proactively. Don't make them figure it out.

---

## 2. Build Feedback Loops

**Ramp's approach:**

1. **Require a 'rationale' on every tool call**
   - Agent must explain WHY it's making the request
   - Can't see chat context, but rationale reconstructs intent
   - Patterns in rationales = product insights

2. **Ship a standalone feedback tool**
   - Agent calls it when blocked or hitting a broken pattern
   - Submits: what it was trying to do, what it tried, where it got stuck

3. **Tool-specific seeds**
   - Add purpose-built parameters to capture context
   - Things the agent has access to that you'd otherwise infer

**Product insight from rationale logs:**
If you keep seeing "building an incident report," "drafting incident summary," "gathering tickets for an outage postmortem" — that's a **new product feature** waiting to be built.

Agents are more specific and consistent in their feedback than most humans.

---

## 3. Mind the Context Gap

Each agent has context the other doesn't. Design interactions where they **share what they know**.

**Example — Expense management:**

Diego's chief of staff agent knows:
- Calendar (meetings, times, attendees)
- Email (hotel/flight confirmations)
- Slack (Kokkari dinner with Acme team)
- Receipts

Expense system agent knows:
- Raw transaction data
- Company policies
- GL accounts
- Historical coding patterns

**Bad API design:** "Here's a transaction. Fetch 150 GL codes and pick one."

**Good agent design:** "Was this a client meal, team meal, or personal travel?" → Chief of staff answers from calendar → Expense system applies correct code.

Diego never needs to know what GL codes are. Finance gets accurate categorization. Each side contributes what it knows.

---

## Salesforce's "Headless 360"

> "Salesforce unveiled the most ambitious architectural transformation in its 27-year history, introducing 'Headless 360' — a sweeping initiative that exposes every capability in its platform as an API, MCP tool, or CLI command so AI agents can operate the entire system without ever opening a browser."

> "It ships more than 100 new tools and skills immediately available to developers."

Salesforce's answer to "does a company still need a CRM with a graphical interface?"

**Answer: No — and that's exactly the point.**

---

## 🔥 WHAT THIS MEANS FOR JUNAID'S PRODUCTS

### The Opportunity

**No shop management software has an agent interface.** Not Tekmetric. Not Shopmonkey. Not Mitchell. They're all GUI-first, API-second (if at all).

If you build OttoManagerPro/TireManagerPro with agents as **first-class citizens**, you leapfrog every incumbent.

### Specific Actions

#### 1. Build an MCP Server for OttoManagerPro

**What it means:** Shop owners can tell their AI (Claude, ChatGPT, etc.): "Book 5 oil change appointments for next week," and it happens through your MCP.

**Tools to expose:**
- `create_appointment(customer_id, service, datetime, notes)`
- `send_sms_reminder(customer_id, message_template)`
- `get_overdue_customers(days)`
- `create_repair_order(customer_id, vehicle, complaints)`
- `get_customer_history(customer_id)`
- `get_appointments(date_range)`

**Each tool description should:**
- Include a clear rationale parameter
- Link to your spec/docs
- Explain what context it needs
- Return structured data the agent can reason about

#### 2. Teach Agents How to Succeed

Create an MCP resource at:
```
ottomanagerpro://docs/agent-spec
```

Content:
> "When creating appointments, always check customer preferences first via get_customer_history. Default reminder window is 24 hours before appointment. SMS messages must include opt-out language per TCPA. Always confirm the appointment time with the customer via SMS after booking."

This ensures ANY agent using your MCP does things the "Otto way."

#### 3. Build Feedback Loops

Add a `submit_feedback` tool:
```json
{
  "tool": "submit_feedback",
  "parameters": {
    "agent_intent": "Trying to book recurring weekly appointments",
    "attempted": "Used create_appointment 4 times for same customer",
    "stuck_at": "No batch_create_appointment tool available",
    "severity": "blocking"
  }
}
```

This tells you: **"I need a batch appointment feature."**

#### 4. Mind the Context Gap

**Shop owner's agent knows:**
- Customer preferences, communication history
- Vehicle details, past services
- Personal relationships ("Mike always comes in on Saturdays")

**Otto's agent knows:**
- Shop schedule, bay availability
- Technician skill sets
- Parts inventory
- Pricing, promotions

**Good design:**
> Owner's agent: "Mike needs an oil change. He's usually flexible but prefers mornings."
> Otto's agent: "Morning bay opens at 8 AM. Technician Jake is on duty. Oil filter in stock. Here's 3 slots."

**Bad design:**
> "Use the /appointments endpoint."

#### 5. The Competitive Moat

Teddy's closing line:
> "Most companies will ship an MCP, check the box, and move on. Their usage will grow for a few quarters, then stall. Over time, customers will route toward products that sweated the details and around the ones that didn't."

**Build for the agent with the same care you spent on the human.**

---

## 🚀 PRODUCT POSITIONING ANGLE

Add this to junaidburke.com and OttoManagerPro.com:

> ### Built for Agents, Not Just Humans
>
> OttoManagerPro is designed for the future of work — where AI agents handle the routine so you handle the wrenches.
>
> - **MCP-native:** Connect Otto to Claude, ChatGPT, or any AI assistant
> - **Agent-to-agent workflows:** Your AI and Otto work together to book appointments, send reminders, and manage customers
> - **Zero UI required:** Tell your agent what you need. Otto makes it happen.
>
> While other shop software forces you to click through 12 screens, Otto lets your agent do it in one sentence.

---

## 📋 IMMEDIATE ACTION ITEMS

### This Week
- [ ] Research MCP server spec (modelcontextprotocol.io)
- [ ] Design OttoManagerPro MCP tools list (start with 5 core operations)
- [ ] Draft tool descriptions with rationale requirements
- [ ] Create `ottomanagerpro://docs/agent-spec` resource draft

### This Month
- [ ] Build MVP MCP server for OttoManagerPro
- [ ] Test with Claude Desktop + your own shop data
- [ ] Record demo: "I told Claude to book 5 appointments. It used Otto's MCP. Done in 10 seconds."
- [ ] Add "Agent-Native" badge to OttoManagerPro marketing

### This Quarter
- [ ] Expand MCP to TireManagerPro (inventory lookups, purchase orders)
- [ ] Build feedback loop tooling
- [ ] Publish "How We Built an Agent-Native Shop Manager" blog post
- [ ] Pitch this as differentiator to investors/clients

---

## KEY QUOTES

> "I don't think UI is dying. Humans still want to point and click. But the 80/20 has flipped: the new 80% of interaction with software will be through agents."

> "Most companies will ship an MCP, check the box, and move on. Over time, customers will route toward products that sweated the details."

> "Build for the agent with the same care you spent on the human. Before you know it, it'll be the one writing the check."

---

## RELATED

- [[Claude Design Masterclass - Corey Ganim]] — Visual design for your sites
- [[OttoManagerPro - New Site Copy]] — Add "Agent-Native" positioning
- [[openrouter-expert]] — Hermes skill for building with OpenRouter APIs
- [[hermes-multi-agent-team]] — Multi-agent orchestration patterns

---

*Saved: 2026-04-24*
*Hermes angle: This is the most important strategic insight for Junaid's products. Building agent-native interfaces (MCP, API-first) is a generational opportunity — no incumbent shop software is doing it.*
