# Level 4: Build

Level 4 is where the product gets built — incrementally, with review at each step, and always in alignment with the design decisions made in Levels 1–3.

This is not "vibe and ship." Every task is traceable to a design decision. Every change is reviewed before it merges. Every release is versioned and documented.

---

## How This Level Works

### The Task Cycle

1. Pick the next task from `BACKLOG.md`
2. Create a branch named for the task (e.g., `feat/user-signup` or `fix/login-error`)
3. Work with Claude to implement the task — referencing the relevant design documents
4. Before marking complete, verify against `design/SECURITY_PRIVACY.md` and any other relevant constraints
5. Commit with a clear message, push, and open a pull request for human review
6. Merge to main, update `CHANGELOG.md`, and tag a release when a milestone is complete

### Semantic Versioning

Releases follow [semantic versioning](https://semver.org/): `MAJOR.MINOR.PATCH`

| Version bump | When to use |
|-------------|------------|
| `PATCH` (0.0.x) | Bug fixes and small corrections |
| `MINOR` (0.x.0) | New features, backwards-compatible |
| `MAJOR` (x.0.0) | Breaking changes or major milestones |

The MVP release is `0.1.0`. V1 is `1.0.0`.

---

## Before Merging Any Task

Claude should verify these before considering a task complete:

- [ ] The implementation matches the relevant design document(s)
- [ ] No secrets, API keys, or credentials are in the code or commit history
- [ ] All user input that crosses a trust boundary is validated
- [ ] Error messages don't expose internal system state
- [ ] The change has been manually tested against the relevant user journey

---

## Done Enough to Move On?

A milestone is complete when:
- All tasks for that milestone are merged and the product behaves as described in the milestone outcome
- `CHANGELOG.md` has been updated
- A tagged release has been cut on GitHub

---

## Claude Guidance for This Level

When helping a user at Level 4:
- Before starting any task, re-read the relevant sections of Level 2 design documents. Decisions made there constrain implementation.
- When the design document doesn't address something you need to implement, surface it to the user rather than guessing — it may need to be added to the design doc first
- Remind the user to review each PR before merging, even if they're the only contributor — a moment of human review catches things that code review by Claude misses
- When a task is complete, proactively suggest the `CHANGELOG.md` entry
- Never mark a task complete if the security checklist in `SECURITY_PRIVACY.md` has unresolved items

---

## Related

- [Level 3: Roadmap](../03-roadmap/README.md)
- [BACKLOG.md](./BACKLOG.md)
- [CHANGELOG.md](./CHANGELOG.md)
- [design/SECURITY_PRIVACY.md](../02-design/SECURITY_PRIVACY.md)
