# Runbook: Choose and Install an IDE

An IDE (Integrated Development Environment) is the editor where you write and view code and documents. For the Hacky Hours workflow, you'll primarily be working in Markdown files, a terminal, and Claude Code — so the IDE doesn't need to be fancy.

---

## Recommended: Visual Studio Code (VS Code)

VS Code is free, widely used, and works well with Claude Code and Markdown. It's a good default for anyone without a strong preference.

**Install:** [code.visualstudio.com](https://code.visualstudio.com) — download the version for your OS.

### Recommended Extensions

Install these from the VS Code Extensions panel (Ctrl+Shift+X / Cmd+Shift+X):

| Extension | Why |
|-----------|-----|
| **Markdown Preview Enhanced** | Renders Mermaid diagrams and Markdown side-by-side |
| **GitLens** | Shows git history and blame inline |
| **Prettier** | Auto-formats Markdown for consistency |

### Opening Your Project

In your terminal, navigate to your project folder and type `code .` — the dot means "open this folder":

```bash
cd ~/Documents/my-project-docs
code .
```

Replace `~/Documents/my-project-docs` with the actual path to your project. VS Code will open the entire folder as a workspace.

> **Screenshot:** VS Code open with a project folder visible in the left Explorer panel

---

## Alternatives

| Editor | Good for |
|--------|---------|
| **Cursor** | VS Code fork with built-in AI features; good if you want AI help outside of Claude Code |
| **Zed** | Fast, minimal, growing AI support |
| **Neovim / Vim** | Experienced developers who prefer keyboard-driven editing |
| **Any text editor** | If you're primarily editing Markdown and using Claude Code in the terminal, even Notepad works |

---

## Working with Markdown

Markdown is plain text with simple formatting syntax. GitHub and Claude Code both render it natively. You don't need to learn all of it — the basics are enough:

```markdown
# Heading 1
## Heading 2

**bold text**
*italic text*

- Bullet item
- Another item

| Column 1 | Column 2 |
|----------|----------|
| Cell     | Cell     |
```

---

## You're Done When...

You can open your project folder in VS Code, see the files listed in the left panel, and click on a `.md` file to view its contents. If you have the Markdown Preview Enhanced extension, press **Cmd+Shift+V** (macOS) or **Ctrl+Shift+V** (Windows/Linux) to see it rendered.

---

## Related

- [02-claude-code.md](./02-claude-code.md)
- [05-windows-setup.md](./05-windows-setup.md)
- [06-macos-setup.md](./06-macos-setup.md)
- [07-linux-setup.md](./07-linux-setup.md)
