# Build Agents that never forget

**Source:** Akshay 🚀 (@akshay_pachaar)  
**Date:** 2026-04-13  
**Link:** https://x.com/akshay_pachaar/status/2043745099792953508

---

## Full Article

*[NOTE: Article was partially captured before session expired. Full text may require re-fetching.]*

A first-principles walk through agent memory: from Python lists to markdown files to vector search to graph-vector hybrids, and finally, a clean, open-source solution for all of this.

An LLM is stateless by design. Every API call starts fresh. The "memory" you feel when chatting with ChatGPT is an illusion created by re-sending the entire conversation history with every request. That trick works for casual chat. It falls apart the moment you try to build a real agent. Here are 7 failure modes show up the instant you skip memory:

- Context amnesia: the agent asks for information you already gave it
- Zero personalization: every interaction feels generic
- Multi-step task failure: intermediate state silently drops mid-task
- Repeated mistakes: no episodic recall means the same errors, forever
- No knowledge accumulation: every session starts from scratch
- Hallucination from gaps: when context overflows, the model invents
- Identity collapse: no continuity, no trust

The obvious response is "throw more context at it." That's why 128K and 200K token windows feel like they should solve everything. They don't. Accuracy drops over 30% when relevant information sits in the middle of a long context. This is the well-documented "lost in the middle" effect. Context is a shared budget: system prompts, retrieved docs, conversation history, and output all fight for the same tokens. Even at 100K tokens, the absence of persistence, prioritization, and salience makes raw context length insufficient.

Memory isn't about cramming more text into the prompt. It's about structuring what the agent remembers so it can find what matters.

## The cognitive science frame that actually helps

Lilian Weng's 2023 formulation has become the default framework: Agent = LLM + Memory + Planning + Tool Use. The four co-equal pillars. Her taxonomy borrows from cognitive science, where human memory splits into three systems:

- Sensory memory captures raw perceptual input and holds it for a fraction of a second. Only the portions you pay attention to get passed forward.
- Working memory is where active thinking happens. It holds roughly 7±2 items at a time (Miller's 1956 finding). Lose focus, and the contents disappear.
- Long-term memory is durable storage with no practical capacity limit. Retrieval is the bottleneck: you can store millions of things and still fail to recall the one you need.

Each maps directly to a component in modern agent architectures:

Long-term memory itself splits further:

- Episodic: specific past events ("on Tuesday, the PostgreSQL cluster went down")
- Semantic: facts and concepts ("PostgreSQL is a relational database")
- Procedural: skills and workflows ("when a user asks for a refund, first check the purchase date")

The bridge between episodic and semantic is memory consolidation: repeated specific events distilling into general knowledge. An agent that notices "users consistently prefer executive summaries" across dozens of interactions should turn that into a reusable rule. Without consolidation, your agent replays individual events rather than learning from them.

## The minimal agent, and what breaks first

Strip away the frameworks and an agent is a loop: perceive, think, act. python

```python
class Agent:
    """Minimal AI agent: perceive, think, act"""
    def __init__(self):
        self.client = anthropic.Anthropic()
        self.model = "claude-sonnet-4-20250514"

    def run(self, user_input: str) -> str:
        response = self.client.messages.create(
            model=self.model,
            max_tokens=1024,
            messages=[{"role": "user", "content": user_input}],
        )
        return response.content[0].text
```

Tell it "I have 4 apples," then ask "I ate one, how many left?" and it has no idea what apples you're talking about. Each call exists in isolation.

## Layer 1: The Python list

The first fix everyone reaches for: Multi-turn works now. The apples question gets answered correctly because the full conversation re-ships with every call. Two problems show up fast:

- The list grows unbounded. Around turn 200, you hit the context ceiling and the oldest messages silently drop. The user's name from turn 1 disappears long before yesterday's throwaway joke. No prioritization, just strict chronological order.
- Everything lives in RAM. The moment the Python process ends, your agent has no idea who you are.

## Layer 2: Markdown files for persistence

*[Article continues: Layer 3 (vector search), Layer 4 (graph-vector hybrids), and open-source solution — content truncated due to session expiry. Re-fetch from source if full text is needed.]*

---

## Summary

A deep-dive into agent memory architecture from first principles. LLMs are stateless by default — every API call starts fresh, and "memory" is just re-sent conversation history. The author walks through 7 failure modes that appear when you skip memory design, explains why bigger context windows (128K+) don't solve the problem (the "lost in the middle" effect drops accuracy 30%+), and maps human memory science (sensory → working → long-term, with episodic/semantic/procedural subdivisions) onto agent architecture components. Then walks through 4+ evolution layers: Python list (multi-turn but unbounded, RAM-only), markdown files (persistent, searchable), vector search (semantic retrieval), and graph-vector hybrids (relationships + semantics). Ends with an open-source solution.

---

## Key Takeaways

1. **LLMs are stateless by design** — conversation "memory" is just re-sent history, not true persistence
2. **7 failure modes without memory:** context amnesia, zero personalization, multi-step failure, repeated mistakes, no knowledge accumulation, hallucination from gaps, identity collapse
3. **"Lost in the middle" effect:** accuracy drops 30%+ when relevant info is in the middle of a long context — bigger windows don't fix this
4. **Lilian Weng's 4 pillars:** Agent = LLM + Memory + Planning + Tool Use
5. **Human memory maps to agent components:** Sensory → input processing; Working memory → context window; Long-term → episodic + semantic + procedural storage
6. **Memory consolidation:** episodic events → semantic facts. Repeated patterns should become reusable rules, not replayed memories
7. **Layer 1 (Python list):** fixes statelessness but grows unbounded and dies with the process
8. **Article still covers:** Layer 2 (markdown files), Layer 3 (vector search), Layer 4 (graph-vector hybrids) — truncated in this capture
