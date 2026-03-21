# ITERATION.md — Post v1.1.0

## Raw Capture

### Distribution & Cross-Tool Support
- The installed command (`hacky-hours.md`) is out of sync with the dev command (`hacky-hours-dev.md`) — installed version still says v1.0.0, missing all v1.1.0 features (subcommand help, audit scorecards, context preambles). The install script downloads from `main` but there's no `hacky-hours.md` at `.claude/commands/` — only `hacky-hours-dev.md`. The publish/distribution story needs clarification.
- Cursor doesn't support Claude Code slash commands — it has its own `.cursorrules` system. No argument routing, different format. Would need a separate adapter.
- No Claude plugin marketplace or skill registry exists today. Distribution is manual (curl | bash).
- MCP (Model Context Protocol) is the most portable cross-tool option but requires writing a server, not just a markdown file. Different paradigm (tools/resources vs prompt context).
- No auto-update mechanism — users must re-run install script manually.

### Artifact Consistency
- ARCHITECTURE.md Known Fragility section still says "this prompt needs harmonization" — that work was completed in v1.1.0 and the doc should be updated.
- Two CHANGELOGs exist: root `CHANGELOG.md` (the project's real changelog) and `hacky-hours/04-build/CHANGELOG.md` (dogfooding artifact). The relationship between them is unclear and they contain overlapping content.

### Design Gaps
- No versioning strategy documented for the command prompt itself — how to bump version strings, what constitutes a breaking change, how the dev → installed publish cycle works.
- The install script strips "(dev)" from the description but doesn't do any other transformation — the dev and installed versions should be identical in content after that strip. Currently the installed file name differs (`hacky-hours-dev.md` → `hacky-hours.md`).
