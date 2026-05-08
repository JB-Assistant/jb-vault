# Using Claude Code: The Unreasonable Effectiveness of HTML

**Author:** Thariq (@trq212)  
**Role:** Claude Code @anthropicai | prev YC W20, @southpkcommons, @medialab  
**Published:** 2026-05-08  
**Source:** https://x.com/trq212/status/2052809885763747935  
**Engagement:** 1.2M views | 3,740 likes | 252 replies  
**Demo Gallery:** https://thariqs.github.io/html-effectiveness/

---

## Core Thesis

Markdown has become the dominant file format for agent communication, but Thariq argues it's becoming a *restricting* format as agents grow more powerful. He's switched to **HTML as the default output format** — and increasingly sees this pattern across the Claude Code team.

> "I find it difficult to read a markdown file of more than a hundred lines. I want richer visualizations, color and diagrams and I want to be able to share them easily."

---

## Why HTML Over Markdown

### 1. Information Density
HTML can represent almost any information Claude can read:
- **Tabular data** using tables
- **Design data** with CSS
- **Illustrations** with SVG
- **Code snippets** with script tags
- **Interactions** via HTML elements + JS + CSS
- **Workflows** using SVG and HTML
- **Spatial data** using absolute positions and canvases
- **Images** using image tags

> "There is almost no set of information that Claude can read that you cannot fairly efficiently represent with HTML."

In the absence of HTML, Claude falls back to inefficient markdown hacks: ASCII diagrams or estimating colors with unicode characters.

### 2. Visual Clarity & Ease of Reading
- Markdown files >100 lines go unread — even by the author
- HTML documents are easier to navigate with tabs, illustrations, links
- Can be **mobile responsive**
- Higher chance colleagues actually read your spec/report/PR writeup

### 3. Ease of Sharing
- Markdown = email attachment hell
- HTML = upload to S3, share link, open anywhere

### 4. Two-Way Interaction
HTML allows interactive documents:
- Sliders/knobs to adjust designs
- Tweak algorithm parameters and see results live
- Copy changes back into a prompt to paste into Claude Code
- Reference: Thariq's "playgrounds" post: https://x.com/trq212/status/2017024445244924382

### 5. Data Ingestion (Claude Code Advantage)
Why use Claude Code specifically for HTML vs Claude.ai or Claude Design?
- **Filesystem access:** Ask it to scan your code folder, find all HTML files, categorize them, generate diagrams
- **MCP integrations:** Slack, Linear, etc.
- **Browser context:** Claude in Chrome
- **Git history** for context

> "The diagrams you see in this article are a direct result of [Claude Code scanning my code folder]."

### 6. It's Joyful
> "Making HTML documents with Claude is just more fun and makes me feel more involved and invested in the creation, and that by itself is enough."

---

## How to Get Started

Thariq explicitly warns against turning this into a `/html` skill immediately:

> "You don't need to do much to get Claude to do this. You can just ask it to 'make a HTML file' or 'make a HTML artifact'."

The trick is **knowing what you want the artifact to do** and how you'll use it. Build skills later, but start by prompting from scratch.

---

## Use Cases

### A. Specs, Planning & Exploration
HTML is a rich canvas for Claude to dive into a problem. Workflow:
1. Ask Claude to brainstorm → create HTML explorations of different options
2. Expand into one direction → mockups, code snippets
3. Write implementation plan in HTML
4. New session → pass all files for implementation
5. Verification agent reads the same files for broader context

**Example Prompt:**
> "I'm not sure what direction to take the onboarding screen. Generate 6 distinctly different approaches — vary layout, tone, and density — and lay them out as a single HTML file in a grid so I can compare them side by side. Label each with the tradeoff it's making."

**Example Prompt:**
> "Create a thorough implementation plan in a HTML file, be sure to make some mockups, show data flow and add important code snippets I might want to review. Make it easy to read and digest."

**Use for:**
- Exploring implementation options
- Exploring multiple visual designs

---

### B. Code Review & Understanding
- Render diffs, annotations, flowcharts, modules
- Better than GitHub diff view for complex PRs
- Thariq attaches an HTML code explainer to **every PR he makes**

**Example Prompt:**
> "Help me review this PR by creating an HTML artifact that describes it. I'm not very familiar with the streaming/backpressure logic so focus on that. Render the actual diff with inline margin annotations, color-code findings by severity and whatever else might be needed to convey the concept well."

**Use for:**
- Creating a PR
- Reviewing a PR
- Understanding a topic in code

---

### C. Design & Prototypes
- Claude Design is HTML-based because HTML is incredibly expressive
- Prototype interactions (animations, actions)
- Use sliders/knobs to tune exactly what you're looking for

**Example Prompt:**
> "I want to prototype a new checkout button, when clicked it does a play animation and then turns purple quickly. Create a HTML file with several sliders and options for me to try different options on this animation, give me a copy button to copy the parameters that worked well."

**Use for:**
- Creating design system artifacts
- Adjusting components
- Visualizing component libraries
- Prototyping joyful animations

---

### D. Reports, Research & Learning
Claude Code synthesizes across multiple data sources (Slack, codebase, git history, internet) into readable HTML reports.

**Example Prompt:**
> "I don't understand how our rate limiter actually works. Read the relevant code and produce a single HTML explainer page: a diagram of the token-bucket flow, the 3–4 key code snippets annotated, and a 'gotchas' section at the bottom. Optimize it for someone reading it once."

**Use for:**
- Summarize how a feature works
- Explain a concept
- Weekly status reports
- Incident reports
- SVG illustrations, flowcharts, technical diagrams

---

### E. Custom Editing Interfaces
Throwaway editors for specific tasks — not products, not reusable tools, but **single HTML files purpose-built for one piece of data**.

**Critical pattern:** Always end with an export — "copy as JSON" or "copy as prompt" button that turns UI interactions back into something pasteable into Claude Code.

**Example Prompts:**
> "I need to reprioritize these 30 Linear tickets. Make me an HTML file with each ticket as a draggable card across Now / Next / Later / Cut columns. Pre-sort them by your best guess. Add a 'copy as markdown' button that exports the final ordering with a one-line rationale per bucket."

> "Here's our feature flag config. Build a form-based editor for it, group flags by area, show dependencies between them, warn me if I enable a flag whose prerequisite is off. Add a 'copy diff' button that gives me just the changed keys."

> "I'm tuning this system prompt. Make a side-by-side editor: editable prompt on the left with the variable slots highlighted, three sample inputs on the right that re-render the filled template live. Add a character/token counter and a copy button."

**Use for:**
- Reordering, triaging, bucketing anything
- Editing structured config (feature flags, env vars, JSON/YAML)
- Tuning prompts/templates with live preview
- Curating datasets (approve/reject, tag, export)
- Annotating documents/transcripts/diffs
- Picking values painful in text: colors, easing curves, crop regions, cron schedules, regexes

---

## FAQ

**Q: Isn't it less token efficient?**  
A: Markdown uses fewer tokens, but HTML's expressiveness + higher likelihood of being read = better overall output. With Opus 4.7's 1M context window, increased token usage is negligible.

**Q: When do you use markdown now?**  
A: "I have honestly stopped using markdown altogether for almost everything, but I'm probably far on the HTML maximalist side of things."

**Q: How do I view the HTML file?**  
A: Open locally in browser, or upload to S3 for shareable links.

**Q: Doesn't this take longer to generate?**  
A: Yes — 2-4x longer than Markdown. But results are worth it.

**Q: What about version control?**  
A: "This is honestly one of the biggest downsides of HTML, HTML diffs are noisy and hard to review compared to Markdown."

**Q: How do I get Claude to match my taste / not make it ugly?**  
A: Use the frontend design plugin. For company style matching, create a single design system HTML file by pointing Claude at your codebase, then use it as reference for other HTML files.

---

## Closing Insight

> "All of the above is to say that I think the real reason I use HTML is that I feel much more in the loop with Claude. I had begun to fear that because I had stopped reading plans in depth I would simply have to leave Claude to make its choices. But I am happy to say instead that I feel more in the loop than ever before when using HTML."

---

## Hermes Angle

**Relevance to our stack:**
- Hermes already supports HTML artifact generation via the `design-toolkit` skill
- Our landing page was built as a single HTML file — validates this approach
- The 4-layer memory system (AGENTS.md, Soul.md, vault, session search) could benefit from HTML dashboards instead of markdown logs
- The Lead Hunter cron could output HTML reports instead of text summaries
- TireManagerPro's admin dashboard specs could be prototyped in HTML before React implementation

**Action item:** Experiment with HTML artifacts for:
1. Weekly product status reports (instead of markdown logs)
2. Lead Hunter output (interactive lead cards instead of text tables)
3. Multi-agent coordination dashboards (visualizing Hermes + CortexClaw handoffs)
4. Customer onboarding flow prototypes (drag-and-drop HTML before Next.js build)

---

#article #claude-code #html #agent-harness #productivity #anthropic #thariq #ui-design #specs #code-review
