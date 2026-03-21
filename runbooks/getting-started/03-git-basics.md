# Runbook: Git Basics

Git is the version control system that tracks changes to your project over time. Think of it as a detailed save history — you can always go back to a previous state, see exactly what changed, and collaborate without overwriting each other's work.

This runbook covers the commands you'll use in the Hacky Hours workflow.

---

## Install Git

**macOS:** Git may already be installed. Run `git --version` in your terminal. If not, install it via [Homebrew](https://brew.sh): `brew install git`

**Windows:** Download and install [Git for Windows](https://git-scm.com/download/win). Use "Git Bash" as your terminal for the commands in this guide.

**Linux:** `sudo apt install git` (Debian/Ubuntu) or `sudo dnf install git` (Fedora)

---

## One-Time Setup

Configure your identity — this appears in your commit history:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## The Core Workflow

### Clone a repository (get a copy of an existing repo)

```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

### Check what's changed

```bash
git status
```

### Stage changes (prepare them to be saved)

```bash
git add .          # stage all changes
git add file.md    # stage a specific file
```

### Commit (save a snapshot with a message)

```bash
git commit -m "Add initial product overview"
```

Write commit messages in present tense, describing what the change does: "Add user journey for sign-up", not "Added some stuff".

### Push (send your commits to GitHub)

```bash
git push
```

### Pull (get changes from GitHub)

```bash
git pull
```

---

## Working with Branches

Branches let you work on a feature without affecting the main codebase.

```bash
git checkout -b feat/user-signup     # create and switch to a new branch
git checkout main                    # switch back to main
git push -u origin feat/user-signup  # push the branch to GitHub
```

When your work is ready, open a Pull Request on GitHub to merge it into `main`.

---

## The Hacky Hours Branch Pattern

Each task in `BACKLOG.md` gets its own branch, named consistently:

| Type | Pattern | Example |
|------|---------|---------|
| New feature | `feat/description` | `feat/user-signup` |
| Bug fix | `fix/description` | `fix/login-error` |
| Documentation | `docs/description` | `docs/update-readme` |
| Chore / setup | `chore/description` | `chore/add-linting` |

---

## Related

- [01-github.md](./01-github.md)
- [build/README.md](../../04-build/README.md)
- [fork-vs-clone.md](../using-this-repo/fork-vs-clone.md)
