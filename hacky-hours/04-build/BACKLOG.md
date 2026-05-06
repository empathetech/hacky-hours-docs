# BACKLOG.md

**Step 4 — Build** | hacky-hours-docs

---

## Next Milestone

*No milestone assigned yet.*

---

## Backlog (unscheduled)

### Research: Skill format vs. slash command format

**Type:** Research spike
**Branch:** `research/skill-vs-slash-command`

The Claude Code `SKILL.md` format exists alongside the slash command format (`.claude/commands/`). This repo currently uses slash commands exclusively. A `hacky-hours` skill and `hacky-hours-dev` skill also exist in the session environment — unclear whether these were created separately or are auto-derived.

**Questions to answer:**
- What does the SKILL.md format provide that the slash command format doesn't?
- Are skills the forward-looking mechanism for this kind of framework assistant?
- Is there meaningful overlap between the two, or do they serve distinct purposes?
- If skills are the preferred format, what would a migration look like and what version would it warrant?

**Output:** Short writeup. Either dies, or spawns an ADR + migration task.

---

### Design spike: Two-tier design artifacts (human summary + deep doc)

**Type:** Design exploration → ADR
**Branch:** `design/two-tier-artifacts`

Live demos with non-engineers reveal that the framework's comprehensive design docs feel like "walls of text" to non-technical stakeholders. Risk: users rubber-stamp AI-generated content rather than internalizing it. Hypothesis: each design doc could have a short, visual, human-facing summary (the artifact the user signs off on) plus a deeper technical expansion (AI's working notes for build time).

**Design questions:**
- Separate file (`SUMMARY.md`) or capped top section of the existing doc?
- Standard shape for a summary? Candidate: problem / decision / tradeoff / diagram / what's next.
- How is length enforced? ("One screen, no scrolling" as a forcing function.)
- Diagrams (Mermaid) lead the summary instead of being buried inline?
- Summary generated *from* the deep doc, or deep doc expanded *from* a human-signed-off summary? (The latter resists the AI-rubber-stamp trap.)
- Which Step 2 docs benefit most? Probably ARCHITECTURE, DATA_MODEL, USER_JOURNEYS.

**Output:** ADR proposing the two-tier shape, plus a small prototype on one design doc to test the pattern.
