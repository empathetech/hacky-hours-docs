# Two-tier design templates

**Status:** Prototype (v3.0.0, ARCHITECTURE only)
**Pattern owner:** ADR `2026-05-06-migrate-to-skill-format.md`

Each design doc has two files:

| File | Audience | Purpose | Length |
|---|---|---|---|
| `<DOC>-summary.md` | The human | The artifact they sign off on, share, and remember | One screen, no scrolling |
| `<DOC>-deep.md` | The engineer / the AI doing the build | The full technical expansion | As long as it needs to be |

## Why two tiers

Demo sessions with non-engineers showed the framework's single-tier docs were experienced as "walls of text." Users either skimmed and rubber-stamped, or relied on Claude to summarize back what they had supposedly written. The thinking was happening in the conversation, but it wasn't landing in the artifact in a form the human would internalize.

The summary-first approach inverts the cognitive load:

- **The summary is primary.** The human commits to it. It must be short, visual (diagram-led), and unambiguous about decisions and tradeoffs.
- **The deep doc expands from the summary.** It's AI's working notes for build time. The human doesn't have to read it cover-to-cover — only the parts that are relevant to a given task.
- **If the summary changes, the deep doc updates.** Not the inverse. The summary is the source of intent.

## Standard summary shape

Every summary file should follow the same structure so the user internalizes the *shape*, not just the contents:

1. **Diagram** — leads the doc. The picture is the headline.
2. **What this does** — one sentence.
3. **Key decisions** — three bullets max. Choice + reason, in plain language.
4. **What this rules out** — one paragraph. Honest about tradeoffs.
5. **What's next** — links to the deep doc and related summaries.

The "three bullets max" is a forcing function. If a fourth decision matters, it goes in the deep doc.

## Length

Summary files target **one screen, no scrolling at typical reader settings**. ~30 lines of filled-in content. If a summary is growing past that, the answer is to push detail into the deep doc, not to expand the summary.

## Status of this prototype

ARCHITECTURE is the first design doc using this pattern. Once it has been used in at least one real project session and feedback is in, the pattern will be applied to the remaining design docs (DATA_MODEL, USER_JOURNEYS, SECURITY_PRIVACY, etc.) in a follow-up.
