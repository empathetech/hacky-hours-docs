# hacky-hours-docs

A community framework for building apps with LLMs — the Hacky Hour way — created by [Empathetech](https://www.empathetech.net).

This repo is two things at once:

1. **A documentation framework** — explains the Hacky Hours philosophy, four-level system, and best practices for LLM-assisted development
2. **A fork-able project template** — fork it, fill in the templates for your own project, and use the resulting docs as in-session context for Claude Code

---

## The Core Idea

You are the C-suite of your product. Claude and other LLMs are a highly capable implementation team — but they need alignment, not just instructions. This framework gives you the artifacts to provide that alignment: who you are, what you're building, how it should work, and what values it should uphold.

The goal is not to vibe-code blindly, and not to be paralyzed by fear. It's to build with confidence, ownership, and growing expertise.

---

## Four Levels

| Level | Folder | What happens here |
|-------|--------|-------------------|
| 1 — Ideation | [`01-ideate/`](./01-ideate/) | Capture raw ideas → synthesize into a product overview |
| 2 — Design | [`02-design/`](./02-design/) | Define the product in detail: architecture, data, UX, security |
| 3 — Roadmap | [`03-roadmap/`](./03-roadmap/) | Prioritize features into MVP / V1 / V2 milestones |
| 4 — Build | [`04-build/`](./04-build/) | Track tasks, manage releases, maintain a changelog |

Work through these levels in order. Each level's `README.md` explains what "done enough to move on" looks like.

---

## Getting Started

**New to all of this?** Start with the runbooks:
- [Set up your tools](./runbooks/getting-started/) — GitHub, Claude Code, git, IDE, Windows/macOS/Linux
- [Fork vs clone this repo](./runbooks/using-this-repo/fork-vs-clone.md)

**Ready to build something?** Start at Level 1:
1. Open [`01-ideate/IDEATION.md`](./01-ideate/IDEATION.md) and start writing down your ideas
2. When you have enough, work with Claude to synthesize them into [`01-ideate/PRODUCT_OVERVIEW.md`](./01-ideate/PRODUCT_OVERVIEW.md)
3. Move to Level 2 and let Claude help you decide which design documents your project needs

---

## Using This Repo as a Resource in Another Project

You can import this framework into any project so Claude can reference it as in-session context. See [`runbooks/using-this-repo/import-as-resource.md`](./runbooks/using-this-repo/import-as-resource.md) for three approaches:
- Git submodule (recommended)
- CLAUDE.md reference snippet
- Manual copy

---

## Contributing

All contributions are Markdown files. See [`runbooks/using-this-repo/contributing.md`](./runbooks/using-this-repo/contributing.md) for guidelines.

This is a living document base — it grows as the community learns. If you find a pattern that works or a gap that needs filling, contribute it back.
