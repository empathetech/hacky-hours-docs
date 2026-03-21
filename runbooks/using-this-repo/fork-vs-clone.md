# Fork vs Clone

When starting a new project with the Hacky Hours framework, you have two options for getting your own copy of this repo. Choosing the right one depends on your goal.

---

## Fork (recommended for new projects)

**What it does:** Creates a copy of `hacky-hours-docs` under your GitHub account. Your copy is independent — you can modify it freely, and you can optionally pull in future updates from the original if you want them.

**Use this when:** You want to use this framework as the starting point for your own project's documentation.

### How to fork

1. Go to the `hacky-hours-docs` repository on GitHub
2. Click the **Fork** button in the top right
3. Choose your account as the destination
4. Clone your fork locally:

```bash
git clone https://github.com/YOUR-USERNAME/hacky-hours-docs.git my-project-docs
cd my-project-docs
```

5. Rename the remote so it's clear this is your project:

```bash
git remote rename origin mine
```

6. (Optional) Add the original as an upstream remote to pull future updates:

```bash
git remote add upstream https://github.com/empathetech/hacky-hours-docs.git
```

To pull in updates from the original later:

```bash
git fetch upstream
git merge upstream/main
```

---

## Clone (for contributing or referencing)

**What it does:** Creates a local copy of the repo that stays connected to the original. Changes you push go back to the original (if you have permission).

**Use this when:**
- You want to contribute improvements back to the Hacky Hours framework itself
- You want to use this repo as a read-only reference without modifying it

### How to clone

```bash
git clone https://github.com/empathetech/hacky-hours-docs.git
cd hacky-hours-docs
```

---

## Renaming Your Fork

After forking, rename the repo in GitHub to match your project:

1. Go to your forked repo → **Settings**
2. Change the **Repository name** to something like `my-project-docs`
3. Update your local remote URL:

```bash
git remote set-url mine https://github.com/YOUR-USERNAME/my-project-docs.git
```

---

## Related

- [01-github.md](../getting-started/01-github.md)
- [03-git-basics.md](../getting-started/03-git-basics.md)
- [import-as-resource.md](./import-as-resource.md)
