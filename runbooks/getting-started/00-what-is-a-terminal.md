# What Is a Terminal?

If you've never used a terminal before, this page is for you. It's a 5-minute read, and it will make every other runbook in this folder make a lot more sense.

---

## The Short Version

A terminal is a text-based way to give your computer instructions. Instead of clicking icons and menus, you type commands and press Enter.

That's it. It's just another way to talk to your computer — one that happens to be much more powerful for certain tasks, like installing software and working with code.

---

## Why Do We Need It?

Most of the tools in this framework (git, Node.js, Claude Code) are designed to be used from the terminal. They don't have a visual interface with buttons — you interact with them by typing. This feels strange at first, but you'll get used to it quickly.

---

## How to Open a Terminal

### macOS
Press **Cmd + Space** to open Spotlight, type `Terminal`, and press Enter. You can also find it in **Applications → Utilities → Terminal**.

> **Screenshot:** Terminal.app icon in macOS Spotlight search

### Windows
Press the **Windows key**, type `Windows Terminal`, and press Enter. If it's not installed, search for **PowerShell** instead — it works for everything in these runbooks.

> **Screenshot:** Windows Terminal in the Start menu search

### Linux
Press **Ctrl + Alt + T** on most distributions, or search for "Terminal" in your app launcher.

---

## What You'll See

When you open a terminal, you'll see something like this:

```
yourname@computer ~ %
```

This is called the **prompt**. It's the terminal waiting for you to type a command. The `~` means you're in your home folder (the equivalent of your Documents/Desktop area).

---

## How to Run a Command

1. Click inside the terminal window so it's focused
2. Type the command exactly as shown in the runbook
3. Press **Enter**
4. Wait for it to finish — some commands take a few seconds, others a few minutes

The terminal will print output as it runs. When it shows the prompt again (`%` or `$`), the command is done.

---

## Reading Command Blocks

Throughout these runbooks, commands appear in grey boxes like this:

```bash
brew install node
```

**Copy it exactly** — spacing, dashes, and capitalization all matter. Most commands are safe to copy and paste directly.

When you see something in a command that looks like a placeholder — like `YOUR-USERNAME` or `your@email.com` — replace it with your actual information before pressing Enter.

---

## If Something Goes Wrong

Error messages in the terminal look alarming but are usually helpful. They tell you exactly what went wrong. When you hit an error:

1. Read the last line of the error message — that's usually the key detail
2. Copy the error message and paste it into a Claude Code session or a web search
3. Check the **Troubleshooting** section at the bottom of the runbook you're following

---

## You're Ready When...

You can open a terminal, see the prompt, and type `echo hello` and press Enter — and it prints `hello` back. That means your terminal is working and you know how to run a command.

---

## Related

- [Getting Started README](./README.md)
- [06-macos-setup.md](./06-macos-setup.md)
- [05-windows-setup.md](./05-windows-setup.md)
- [07-linux-setup.md](./07-linux-setup.md)
