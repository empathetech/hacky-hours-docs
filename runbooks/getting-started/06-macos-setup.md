# Runbook: macOS Setup

This runbook installs the minimum tooling needed on macOS to use the Hacky Hours workflow: Homebrew, Node.js, git, and Claude Code.

---

## 1. Install Homebrew

Homebrew is a package manager for macOS that makes installing developer tools straightforward. Open **Terminal** (find it in Applications → Utilities, or search with Spotlight) and run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the prompts. When it finishes, run the two commands it shows you under "Next steps" to add Homebrew to your PATH.

Verify:

```bash
brew --version
```

---

## 2. Install Node.js

```bash
brew install node
```

Verify:

```bash
node --version
npm --version
```

---

## 3. Install Git

macOS includes an older version of git. Install the current version via Homebrew:

```bash
brew install git
```

Verify:

```bash
git --version
```

---

## 4. Install VS Code

```bash
brew install --cask visual-studio-code
```

Or download directly from [code.visualstudio.com](https://code.visualstudio.com). See [04-ide-setup.md](./04-ide-setup.md) for recommended extensions.

To open a project from the terminal:

```bash
cd path/to/your-project
code .
```

---

## 5. Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Then follow [02-claude-code.md](./02-claude-code.md) to authenticate.

---

## Troubleshooting

**"command not found: brew"** — The Homebrew installer may not have updated your PATH. Close and reopen Terminal, or run the PATH commands shown at the end of the install output.

**Permission errors** — Do not use `sudo` with Homebrew. If you get permission errors, check that your user owns `/usr/local` or `/opt/homebrew` (the location varies by chip).

**Apple Silicon (M1/M2/M3) vs Intel** — Homebrew installs to `/opt/homebrew` on Apple Silicon and `/usr/local` on Intel. The commands above work on both; Homebrew handles the difference.

---

## Related

- [01-github.md](./01-github.md)
- [02-claude-code.md](./02-claude-code.md)
- [03-git-basics.md](./03-git-basics.md)
- [04-ide-setup.md](./04-ide-setup.md)
