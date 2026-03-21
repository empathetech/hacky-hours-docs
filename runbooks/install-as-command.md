# Install /hacky-hours as a Global Claude Code Command

The `/hacky-hours` command is a Claude Code slash command that guides you through the Hacky Hours framework — detecting where your project is and helping you move forward. Once installed globally, it works in **any repo you open**, not just this one.

---

## What This Enables

Without global install, `/hacky-hours` only works inside the `hacky-hours-docs` repo itself (where the command file lives). With global install, you can open any project — a new app you're building, an existing codebase, anything — type `/hacky-hours`, and get the guided framework workflow immediately.

---

## Install

### macOS / Linux

```bash
mkdir -p ~/.claude/commands
cp /path/to/hacky-hours-docs/.claude/commands/hacky-hours.md ~/.claude/commands/hacky-hours.md
```

Replace `/path/to/hacky-hours-docs` with the actual path to your clone of this repo. For example:

```bash
cp ~/Documents/hacky-hours-docs/.claude/commands/hacky-hours.md ~/.claude/commands/hacky-hours.md
```

### Windows

Open PowerShell and run:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\commands"
Copy-Item "C:\path\to\hacky-hours-docs\.claude\commands\hacky-hours.md" "$env:USERPROFILE\.claude\commands\hacky-hours.md"
```

Replace `C:\path\to\hacky-hours-docs` with the actual path to your clone.

---

## Verify It Works

1. Open a terminal and navigate to **any project** — something unrelated to hacky-hours-docs
2. Start a Claude Code session: `claude`
3. Type `/hacky-hours` and press Enter
4. Claude should respond by surveying the project and offering options

If the command isn't found, check that the file exists:

```bash
# macOS/Linux
ls ~/.claude/commands/hacky-hours.md

# Windows PowerShell
Test-Path "$env:USERPROFILE\.claude\commands\hacky-hours.md"
```

---

## Updating

When a new version of `hacky-hours-docs` is released with an updated command, re-run the install step. The command file is a plain Markdown file — copying the new version over the old one is all that's needed.

```bash
# macOS/Linux — pull the latest and re-copy
cd /path/to/hacky-hours-docs
git pull
cp .claude/commands/hacky-hours.md ~/.claude/commands/hacky-hours.md
```

---

## Uninstalling

```bash
# macOS/Linux
rm ~/.claude/commands/hacky-hours.md

# Windows PowerShell
Remove-Item "$env:USERPROFILE\.claude\commands\hacky-hours.md"
```

---

## Using the Command

| Command | What it does |
|---------|-------------|
| `/hacky-hours` | Auto-detects your project's state and presents options |
| `/hacky-hours ideate` | Jump directly to Level 1 — Ideation |
| `/hacky-hours design` | Jump directly to Level 2 — Design |
| `/hacky-hours roadmap` | Jump directly to Level 3 — Roadmap |
| `/hacky-hours build` | Jump directly to Level 4 — Build |

---

## Related

- [README.md](../../README.md)
- [import-as-resource.md](./import-as-resource.md) — use this repo as context in another project
- [starter-prompts/](../starter-prompts/) — copy-paste prompts for each level
