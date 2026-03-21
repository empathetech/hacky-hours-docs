# Contributing to hacky-hours-docs

This framework grows through community contributions. If you've found a pattern that works, a gap in the current docs, or a runbook that would help others get started, we'd love to have it.

---

## What Makes a Good Contribution

- **Patterns that worked in practice** — not hypothetical best practices, but things you've actually done and found valuable
- **Gaps in existing documents** — sections that are vague, missing, or out of date
- **New runbooks** — setup guides, tool walkthroughs, or process guides that aren't covered yet
- **Corrections** — anything factually wrong or outdated

---

## Contribution Workflow

1. **Fork the repo** (see [fork-vs-clone.md](./fork-vs-clone.md))
2. **Create a branch** for your change:
   ```bash
   git checkout -b docs/add-something-useful
   ```
3. **Make your changes** — follow the document format below
4. **Commit with a clear message:**
   ```bash
   git commit -m "docs: add runbook for deploying to Vercel"
   ```
5. **Push and open a Pull Request** on GitHub
6. **Describe what you added and why** in the PR description

---

## Document Format

All contributions should follow the skeleton format used throughout this repo:

```markdown
# Document Title

**Level N — [Level Name]** | Contributed by: [role(s)]

One paragraph explaining what this document is for and who should fill it in.

---

> **Claude Guidance:** Instructions for how Claude should behave when helping with this document.

---

## Section Name

*Italicized single sentence describing what goes here.*

---

## Related

- [Link to related doc](../path/to/doc.md)
```

Key rules:
- Use `*italicized text*` for placeholder content in template files
- Always include a `## Related` section with links to connected documents
- Always include a `> **Claude Guidance:**` block
- Keep language plain and jargon-free — this framework is for non-engineers too

---

## What Not to Contribute

- Generic "best practices" that aren't grounded in real experience
- Opinionated tool recommendations without clear reasoning
- Content that duplicates what's already well-covered
- Fabricated examples — if you use an example, make it realistic

---

## Related

- [fork-vs-clone.md](./fork-vs-clone.md)
- [README.md](../../README.md)
