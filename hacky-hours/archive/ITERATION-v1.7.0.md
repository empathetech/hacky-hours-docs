# ITERATION.md

Post-release brain-dump for the next cycle.

---

## Captured Items

### Non-developer UX gap

**Concern:** The framework may be inaccessible to non-technical users due to engineer blind spots in how comparisons and tradeoffs are presented. A non-engineer won't know why React vs. Vue, or FastAPI vs. Flask — and needs those comparisons grounded in something that makes sense to them (consequences, analogies, plain language) rather than technical specs.

**Proposed:** A `/hacky-hours mode` command (or similar mechanism) that switches between an "engineer" conversation style and a "non-technical user" conversation style. Both modes still communicate consequences of planning decisions — the difference is in framing, vocabulary, and how tradeoffs are explained.

**Decisions:**
- Default voice: **non-technical**. Comparisons are grounded in outcomes, analogies, and consequences — not specs.
- Engineer mode: opt-in via `/hacky-hours mode engineer`. Toggle back with `/hacky-hours mode` (no argument = toggle) or `/hacky-hours mode default`.
- Persistence: mode is written to `CLAUDE.md` at set time so it survives across sessions.
- Scaffold behavior: the scaffold step sets non-technical mode in `CLAUDE.md` by default. The `/hacky-hours mode` command updates it.
- Scope: mode affects *conversation style only* — not which documents get created, not the rigor of design decisions. Both modes explain consequences; only the vocabulary and framing differ.
