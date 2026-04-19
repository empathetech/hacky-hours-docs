# ITERATION.md

**Post-v2.0.0 iteration log** | hacky-hours-docs

---

## Captured Items

### Research: Skill format vs. slash command format

**Captured:** 2026-04-14

The Claude Code `SKILL.md` format exists alongside the slash command format (`.claude/commands/`). This repo currently uses slash commands exclusively. A `hacky-hours` skill and `hacky-hours-dev` skill also exist in the session environment — unclear whether these were created separately or are auto-derived.

**Questions to answer:**
- What does the SKILL.md format provide that the slash command format doesn't?
- Are skills the forward-looking mechanism for this kind of framework assistant?
- Is there meaningful overlap between the two, or do they serve distinct purposes?
- If skills are the preferred format, what would a migration look like and what version would it warrant?

**Triage:** Research spike — no implementation until the above is answered.

---

### Documentation update: README and all docs to v2.0.0 terminology

**Captured:** 2026-04-18

**Completed:** 2026-04-18

README.md was out of date with v2.0.0. Identified and fixed across 20+ files:
- Level → Step language throughout all template docs, runbooks, and README
- Diagram updated to show five steps including Step 5 — Iterate with loop-back
- Stale v1.x command references replaced with v2.0.0 equivalents (`step 1–5`, `review 1–3`, `update 1–2`, `tools upgrade`, etc.)
- Inclusive language: "paralyzed" → "stuck in endless planning" (follow-up to PR #2)
- `hacky-hours/` self-documentation intentionally left as-is (historical record)

**Triage:** ✅ Complete — no backlog items needed.

---

## Status

*In progress — items being captured. Skill format research not yet triaged.*
