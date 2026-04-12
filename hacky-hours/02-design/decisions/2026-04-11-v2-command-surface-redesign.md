# ADR: v2.0.0 Command Surface Redesign

**Date:** 2026-04-11
**Status:** Accepted
**Deciders:** bjamba (Chris Ling), Claude Code

---

## Context

As of v1.8.0, the hacky-hours command had 30 routing entries — 19 top-level commands with no clear grouping, plus variants and flags. Adding each new capability since v1.0.0 had been additive, which kept individual releases simple but produced a command surface that was growing unwieldy. A new user scanning the help message faced 19 top-level choices with no obvious organizing principle.

v2.0.0 is a major version because it introduces breaking changes to the command surface: existing commands are renamed, removed, or moved under new parent commands. Users who have the v1.x command muscle-memorized will need to relearn the entry points.

---

## Decisions

### 1. Five parent commands replace the flat list

**Before (v1.8.0):** 19 top-level commands in a flat list.

**After (v2.0.0):** One bare command + five parent groups:

| Parent | What it contains |
|--------|-----------------|
| `step` | The five framework steps (ideate → design → roadmap → build → iterate) |
| `review` | Three evaluation modes (audit, optimize, pivot) |
| `learn` | Three onboarding modes (tour, onboard, quiz) |
| `update` | Two shipping/tracking operations (publish release, sync issues) |
| `tools` | Framework meta-commands (upgrade, mode, walkthrough, help) |

**Rationale:** A new user scanning the help message now faces five words, not nineteen. Each parent word carries its own semantic weight: `step` = navigate the framework, `review` = evaluate it, `learn` = onboard to it, `update` = ship it, `tools` = manage it. The cognitive load drops dramatically even though the total surface area is roughly unchanged.

**Tradeoff accepted:** Users familiar with v1.x commands (`/hacky-hours audit`, `/hacky-hours iterate`, etc.) will encounter errors after updating. This is a breaking change. The help message and subcommand help entries call out the new paths explicitly.

---

### 2. Numbered aliases alongside named aliases

Every subcommand has both a number and a name:
- `step 1` | `step ideate`
- `review 1` | `review audit`
- `learn 2` | `learn onboard`
- etc.

**Rationale:** Numbers enable fast navigation once the user knows the structure. Names serve discoverability for first-time users. The numbered pattern is consistent across all five parent commands — one mental model applies everywhere.

**Special case — step 0:** `step 0` is the dry-run mode (explore without writing files). Zero means "before you begin" — it fits naturally before step 1 and carries the right connotation.

---

### 3. "Level" language replaced with "Step" throughout

All references to "Level 1/2/3/4" in the command prompt, help text, scaffold templates, CLAUDE.md, and ARCHITECTURE.md are updated to "Step 1/2/3/4/5".

**Rationale:** "Level" implies a one-way hierarchy you ascend. "Step" implies a cycle you revisit — which is what this actually is. The iterate cycle (now Step 5) reinforces this: there is no "Level 5" you graduate to; iteration is a loop you run after every release.

**Tradeoff:** Any user-generated artifacts (their own CLAUDE.md, design docs, etc.) that reference "Level 1/2/3/4" are not automatically updated. The `tools upgrade` command (Flow C) detects and offers to update CLAUDE.md references.

---

### 4. Review commands grouped under `review`

**Before:** `audit`, `optimize`, and `pivot` were standalone top-level commands.

**After:** `review 1 | audit`, `review 2 | optimize`, `review 3 | pivot`

**Rationale:** These three commands answer three distinct but related questions:
- `review 1` — did we follow best practices? (tactical, pre-release)
- `review 2` — did we build it well? (mid-cycle quality review)
- `review 3` — should we build something else? (strategic direction)

They share a parent because they're all evaluative — you run them when stepping back from building to assess. The numbering carries implicit meaning: 1 is most immediate, 3 is most consequential.

**Tradeoff:** `review` with no argument now runs `review 1` (audit) by default. Users who previously ran `/hacky-hours audit` can run `/hacky-hours review` and get the same behavior. Users who want optimize or pivot must be explicit.

---

### 5. `iterate` absorbed as `step 5`

**Before:** `iterate` was a standalone post-release command, separate from the four levels.

**After:** `step 5 | iterate` — iteration is promoted as a first-class step in the cycle.

**Rationale:** Iteration is not optional maintenance after the "real" work. It is the main loop once a project has shipped. Making it Step 5 communicates that the development cycle doesn't end at Step 4 — it loops through Step 5 back to Step 4.

---

### 6. `sync` renamed to `update`, with two numbered modes

**Before:** `sync` (publish release), `sync --issues` (BACKLOG ↔ GitHub Issues sync)

**After:** `update 1 | update version` (publish release), `update 2 | update project` (issues sync)

**Rationale:** `sync` only accurately described `sync --issues` (a two-way reconciliation). Publishing a release is not a sync operation. `update` covers both: you're updating the published version, or you're updating the project tracking state.

---

### 7. `link` command removed

**Before:** `link` and `link --sync` connected two repos and generated `RELATED_REPOS.md` in both.

**After:** Removed. Guidance updated to recommend a monorepo with `--root` for multi-service projects, or an org-level platform repo for the framework artifacts.

**Rationale:** The primary target audience for hacky-hours (first-time builders, community projects, indie developers) rarely has genuine multi-repo requirements. The `--root` flag already supports the monorepo pattern natively. Users with genuine cross-repo needs can manage `RELATED_REPOS.md` manually — it's just Markdown.

**Tradeoff:** Users who have established links via `link` will lose the re-sync flow. Their existing `RELATED_REPOS.md` files remain valid; only the automated re-sync is gone.

---

### 8. `migrate` and `adopt` absorbed into `tools upgrade`

**Before:** `migrate` (v0.x → v1.0 folder migration), `adopt` (bring existing codebase into framework), and `upgrade` (gap detection for existing projects) were three separate commands.

**After:** `tools upgrade` detects context and runs the appropriate flow:
- No `hacky-hours/` → adoption flow (reads codebase, generates stubs)
- Root-level `01-ideate/` etc. → migration flow (git mv, path updates)
- Existing `hacky-hours/` with gaps → gap detection and fill

**Rationale:** All three commands operate on "the user's project artifacts vs. the current version's expectations." The detection logic is straightforward and the three cases are mutually exclusive in practice. Absorbing them reduces the command surface without losing any capability.

**Tradeoff:** The adoption flow is now less prominent — a first-time adopter has to know to run `tools upgrade` rather than a dedicated `adopt` command. This is offset by `tools walkthrough`, which surfaces `tools upgrade` as the entry point for new codebase adoption.

---

### 9. `dry-run` subcommand replaced by `step 0`

**Before:** `/hacky-hours dry-run` ran the guided session without writing files.

**After:** `/hacky-hours step 0` — the dry-run is a step, not a separate command.

**Rationale:** `step 0` is more intuitive — it's "before you begin, look around safely." It fits the numbering model and removes a separate subcommand from the top-level list.

---

### 10. `status`, `version`, and `checklist` removed as standalone commands

**Before:** `status` (report current level), `version` (print installed version), `checklist` (print pre-merge checklist) were standalone subcommands.

**After:**
- `status` behavior is incorporated into the bare `/hacky-hours` command (survey + orient)
- `version` is included in the help message header
- `checklist` is documented in `help step 4`

**Rationale:** These were metadata/utility commands that didn't belong in the main workflow. The information they provided is surfaced through more natural entry points.

---

### 11. `mode default` renamed to `mode builder`

**Before:** `mode default` (plain language), `mode engineer` (technical)

**After:** `tools mode 1 | tools mode builder`, `tools mode 2 | tools mode engineer`

**Rationale:** "Default" is a technical non-word — it doesn't describe who you are. "Builder" says who you are in the context of this framework: someone building something. It's inclusive and warm, consistent with the hacky-hours ethos. Engineers are the opt-in variant, not the implicit baseline.

---

### 12. Global Values section added to the command prompt

A new "Global Values" section appears near the top of the command prompt, before any routing logic. It declares the values that govern every recommendation:

- Human is the driver
- Free before paid
- Less infrastructure before more
- Privacy-preserving before data-rich
- Reduce attack surface
- Accessible by default
- Licensing hygiene from the start
- This is for everyone

**Rationale:** Previously, safety-first guidance was repeated inline in individual command sections (particularly Step 2 design guidance). A central declaration ensures these values govern all commands consistently, survives prompt compression, and makes them explicit enough that a reviewer can audit whether the prompt follows them. Individual sections no longer need to re-state them.

---

### 13. `tools walkthrough` added as a new command

A new `tools walkthrough` command provides a narrative overview of how all commands work together.

**Rationale:** The `help` message lists commands but doesn't explain how they relate. A new user knows that `step 1` exists but may not understand that `step 5` loops back to `step 4`, or that `review 1` is a gate before `update 1`. `walkthrough` tells the story. It's distinct from `learn 1` (tour of a specific project) — it's a tour of the framework itself.

---

## Breaking Changes Summary

| v1.8.0 command | v2.0.0 equivalent |
|----------------|------------------|
| `/hacky-hours dry-run` | `/hacky-hours step 0` |
| `/hacky-hours ideate` | `/hacky-hours step 1` (or `step ideate`) |
| `/hacky-hours design` | `/hacky-hours step 2` (or `step design`) |
| `/hacky-hours roadmap` | `/hacky-hours step 3` (or `step roadmap`) |
| `/hacky-hours build` | `/hacky-hours step 4` (or `step build`) |
| `/hacky-hours iterate` | `/hacky-hours step 5` (or `step iterate`) |
| `/hacky-hours audit` | `/hacky-hours review 1` (or `review audit`) |
| `/hacky-hours optimize` | `/hacky-hours review 2` (or `review optimize`) |
| `/hacky-hours pivot` | `/hacky-hours review 3` (or `review pivot`) |
| `/hacky-hours learn tour` | `/hacky-hours learn 1` (or `learn tour`) |
| `/hacky-hours learn onboard` | `/hacky-hours learn 2` (or `learn onboard`) |
| `/hacky-hours learn quiz` | `/hacky-hours learn 3` (or `learn quiz`) |
| `/hacky-hours sync` | `/hacky-hours update 1` (or `update version`) |
| `/hacky-hours sync --issues` | `/hacky-hours update 2` (or `update project`) |
| `/hacky-hours upgrade` | `/hacky-hours tools upgrade` |
| `/hacky-hours migrate` | `/hacky-hours tools upgrade` (detected automatically) |
| `/hacky-hours adopt` | `/hacky-hours tools upgrade` (detected automatically) |
| `/hacky-hours mode` | `/hacky-hours tools mode` |
| `/hacky-hours mode default` | `/hacky-hours tools mode 1` (or `tools mode builder`) |
| `/hacky-hours mode engineer` | `/hacky-hours tools mode 2` (or `tools mode engineer`) |
| `/hacky-hours status` | `/hacky-hours` (bare command surveys and reports) |
| `/hacky-hours version` | Listed in `/hacky-hours help` header |
| `/hacky-hours checklist` | Documented in `/hacky-hours help step 4` |
| `/hacky-hours link` | Removed — use monorepo + `--root` instead |
| `/hacky-hours link --sync` | Removed |

---

## Consequences

**Positive:**
- New users face five words, not nineteen, when scanning the help message
- Consistent numbered + named alias pattern across all parents
- "Step" language accurately reflects the cyclical nature of the framework
- Global Values section makes the framework's ethics explicit and auditable
- Prompt reduced from ~2,100 lines to ~1,470 lines (~30% reduction)

**Negative / accepted tradeoffs:**
- v1.x users must relearn command paths — no backward compatibility
- Adoption flow is less prominent under `tools upgrade`
- `link` functionality removed entirely — multi-repo users must manage manually

**Watch for:**
- User feedback on discoverability of `tools upgrade` for first-time adopters
- Whether `review` with no argument defaulting to audit creates confusion for users who want optimize or pivot
- Whether the `step 0` dry-run is as intuitive as the previous `dry-run` subcommand
