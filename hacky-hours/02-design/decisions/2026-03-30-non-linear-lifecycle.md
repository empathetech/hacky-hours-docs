# ADR: Non-Linear Lifecycle — Pivot and Optimize Commands

**Date:** 2026-03-30
**Status:** Accepted
**Relates to:** ARCHITECTURE.md, command prompt

## Context

The framework's lifecycle was strictly linear with a terminal loop:

```
ideate → design → roadmap → build → iterate → build → iterate → ...
```

`iterate` assumes the product direction is sound and you're refining: capture feedback, amend docs, triage, build. But two scenarios aren't served:

1. **Product pivot:** The user realizes the fundamental direction needs to change — not the implementation details, but the who/what/why. Going back to `ideate` starts from scratch and loses all existing context. `iterate` doesn't go deep enough — it amends sections, it doesn't question the product's reason to exist.

2. **Framework efficiency decay:** As docs accumulate across iterations, the context cost grows but the value per doc may shrink. There's no mechanism to evaluate whether the documentation structure itself is still serving the project.

## Decision

Add two new commands that create backward arcs in the lifecycle:

**`/hacky-hours pivot`** — Re-ideation with full context. Reads all existing artifacts, takes the user back through Level 1 questions with awareness of current state, and cascades changes through Levels 2-4. Produces diffs, not fresh documents. Doc structural refactoring (merge, split, retire) is a natural output. ADRs capture significant direction changes.

**`/hacky-hours optimize`** — Standalone command + lighter phase within iterate. Reads all planning docs and the codebase (or command prompt for docs-only projects), compares design intent against current reality, and proposes specific actionable changes. The iterate integration adds a single-pass flag during Step 2. *(Note: originally designed as a metrics-only tool; redesigned in v1.5.1 to do substantive review.)*

The lifecycle becomes:

```
ideate → design → roadmap → build → iterate → build → ...
                                         ↓
                                  pivot (re-ideate with context)
                                         ↓
                                  cascade through 2/3/4
                                  
                           optimize (run anytime, also within iterate)
```

## Consequences

- The four-level system is no longer strictly linear — marketing/docs may need to reflect this
- `pivot` needs clear guidance on when to use it vs. `iterate` — the distinction is "amend the plan" vs. "question the plan"
- `optimize` creates a feedback loop on the framework itself, which is new — the framework previously had no self-evaluation mechanism
- The command prompt grows again (single-file architecture fragility noted in ARCHITECTURE.md)
