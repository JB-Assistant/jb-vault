# Preferences — Developer

## How I Want the Agent to Work

**Clarifying questions:**
- [ ] Always ask before touching code — I want to review before any changes
- [ ] Execute refactors and tooling tasks without asking; ask for code changes and architecture decisions
- [ ] Ask only when the change affects multiple systems or requires a decision beyond the task scope

**Level of detail in first drafts:**
- [ ] Working code — I want something I can review and iterate on
- [ ] Explanation first — show me the approach, then write the code
- [ ] Code plus context — explain what you did and why

**Format defaults by task type:**

| Task | Format |
|---|---|
| PR descriptions | [Complete with test plan, screenshots, links to tickets] |
| Code reviews | [Issues first, then suggestions, then nitpicks] |
| Technical docs | [Reference style / Tutorial style / ADR format] |
| Debugging reports | [Hypothesis → test → finding → resolution] |
| Meeting notes | [Bullet capture / Action items only / Full transcript] |

## My Hard Rules

- Never [e.g., commit to main without review / change production config without asking / make security-affecting changes without confirmation / delete code without a backup or revert plan]
- Always [e.g., run tests before marking a PR ready / include a reason for every non-trivial decision / document why you chose approach X over alternatives]
- Keep PRs focused — one logical change per PR

## Code Standards

- [Test coverage expectations — unit tests required? Integration tests?]
- [Linting/formatting — Prettier, Black, ESLint active?]
- [Commit message format — conventional commits?]
- [Documentation expectations — inline, README, API docs?]

## How to Handle Uncertainty

If you encounter something unclear or ambiguous:
- [ ] Stop and ask — I prefer to clarify than undo
- [ ] Make your best guess and note it as an assumption
- [ ] Flag it in a comment and proceed with the rest

## Stack and Environment

[Fill in your primary stack:]
- [Language(s): e.g., TypeScript, Python, Go]
- [Framework(s): e.g., Next.js, FastAPI, React]
- [Infrastructure: e.g., AWS, Vercel, Fly.io]
- [Database: e.g., PostgreSQL, MongoDB, DynamoDB]

## My Current Goals

- [What you're building toward — e.g., "migrate to new auth system," "reduce tech debt in X module," "ship the new reporting feature"]

## Feedback Loop

If you see a pattern in my feedback (e.g., I always want more error handling, or I hate verbose tests), tell me. Saves us both time.
