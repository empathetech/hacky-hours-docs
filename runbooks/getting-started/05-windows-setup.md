# Runbook: Windows Setup

This runbook installs the minimum tooling needed on Windows to use the Hacky Hours workflow: a terminal, Node.js, git, and Claude Code.

---

## 1. Install Windows Terminal (recommended)

Windows Terminal is a modern terminal app that supports multiple shells. Download it from the [Microsoft Store](https://aka.ms/terminal) or [GitHub](https://github.com/microsoft/terminal/releases).

Alternatively, use **PowerShell** (already installed on Windows 10/11) or **Git Bash** (installed with Git in step 3).

---

## 2. Install Node.js

Node.js is required to install Claude Code.

1. Go to [nodejs.org](https://nodejs.org) and download the **LTS** version
2. Run the installer — accept the defaults
3. Verify the install by opening a terminal and running:

```powershell
node --version
npm --version
```

Both should print a version number.

---

## 3. Install Git

1. Download [Git for Windows](https://git-scm.com/download/win)
2. Run the installer. On the "Choosing the default editor" step, select **Visual Studio Code** if you have it installed, or keep the default
3. On the "Adjusting your PATH environment" step, select **Git from the command line and also from 3rd-party software**
4. Accept the remaining defaults
5. Verify:

```powershell
git --version
```

---

## 4. Install VS Code

Download and install from [code.visualstudio.com](https://code.visualstudio.com). See [04-ide-setup.md](./04-ide-setup.md) for recommended extensions.

---

## 5. Install Claude Code

In your terminal:

```powershell
npm install -g @anthropic-ai/claude-code
```

Then follow [02-claude-code.md](./02-claude-code.md) to authenticate.

---

## Troubleshooting

**"npm is not recognized as a command"** — Node.js isn't in your PATH. Try restarting your terminal, or reinstall Node.js.

**Permission errors during npm install** — Open your terminal as Administrator (right-click → Run as administrator) and retry.

**Git Bash vs PowerShell** — Either works. Git Bash behaves more like a Unix shell (recommended if commands in other runbooks use `ls`, `cat`, etc.).

---

## Related

- [01-github.md](./01-github.md)
- [02-claude-code.md](./02-claude-code.md)
- [03-git-basics.md](./03-git-basics.md)
- [04-ide-setup.md](./04-ide-setup.md)
