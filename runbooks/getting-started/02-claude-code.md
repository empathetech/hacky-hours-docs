# Runbook: Set Up Claude Code

Claude Code is Anthropic's CLI (command-line interface) for working with Claude directly inside your project. It reads your files, understands your context, and helps you build — all within your terminal and editor.

---

## What You'll Need

- An Anthropic account (or access through Claude.ai)
- Node.js installed (version 18 or higher — see your OS setup runbook)
- A terminal (built into macOS and Linux; on Windows, use Windows Terminal or PowerShell)

---

## Steps

### 1. Create an Anthropic account

Go to [claude.ai](https://claude.ai) and sign up. A Claude Pro subscription gives you access to Claude Code.

### 2. Install Claude Code

In your terminal, run:

```bash
npm install -g @anthropic-ai/claude-code
```

### 3. Authenticate

Run:

```bash
claude
```

On first launch, Claude Code will open a browser window to authenticate with your Anthropic account. Follow the prompts.

### 4. Start a session in your project

Navigate to your project folder in the terminal:

```bash
cd path/to/your-project
claude
```

Claude Code will read any `CLAUDE.md` file in the directory and use it as context. This is the mechanism the Hacky Hours framework uses to keep Claude aligned with your project.

### 5. Verify it works

Try asking Claude something about your project:

```
What files are in this directory?
```

If Claude responds with an accurate list, you're set up correctly.

---

## Tips

- **Keep your CLAUDE.md updated** — Claude reads it at the start of every session. The more context it has, the better aligned it will be.
- **Use `/help`** in the Claude Code session to see available commands.
- **Press Ctrl+C** to exit a session.

---

## Related

- [01-github.md](./01-github.md)
- [04-ide-setup.md](./04-ide-setup.md)
- [import-as-resource.md](../using-this-repo/import-as-resource.md)
