# ✅ CHECKIN-README.md

### Purpose

This repository (`bkitwing/dify`) is a **custom internal fork** of the original [langgenius/dify](https://github.com/langgenius/dify).
All local edits (like `docker/docker-compose.yaml`, custom Nginx configs, etc.) are committed **directly to the `main` branch** in this fork.

The goal is to keep our own Dify setup current with upstream updates while retaining our internal changes.

---

## 🔹 Repository Setup

| Remote       | Description                    | URL                                      |
| ------------ | ------------------------------ | ---------------------------------------- |
| **origin**   | Our fork (write access)        | `git@github.com:bkitwing/dify.git`       |
| **upstream** | Original Dify repo (read-only) | `https://github.com/langgenius/dify.git` |

---

## 🔸 Daily Workflow — Commit & Push Local Changes

```bash
cd ~/bkitwing/dify
git switch main               # ensure you’re on main branch
git status                    # check modified files
git add .                     # or specific files
git commit -m "Describe your change"
git push origin main
```

🔹 *This pushes changes directly to our fork’s main branch (`bkitwing/dify:main`).*

---

## 🔸 Updating from Upstream Dify

When a new Dify release or update is available, merge it into our fork:

```bash
cd ~/bkitwing/dify
git switch main
git fetch upstream
git merge upstream/main
```

If conflicts occur:

* Edit conflicting files (e.g. `docker/docker-compose.yaml`)
* Keep our required changes (ports, Nginx, environment variables)
* Then run:

```bash
git add <fixed files>
git commit
git push origin main
```

---

## 🔸 Checking Current Configuration

```bash
git branch          # should show: * main
git remote -v       # verify origin and upstream URLs
git status          # ensure working tree is clean before merging
```

---

## 🔸 Quick Reference Summary

| Task                       | Command                                         |
| -------------------------- | ----------------------------------------------- |
| Check current branch       | `git branch`                                    |
| Check remotes              | `git remote -v`                                 |
| Commit all changes         | `git commit -am "message"`                      |
| Push to fork               | `git push origin main`                          |
| Pull latest from upstream  | `git fetch upstream && git merge upstream/main` |
| Abort an in-progress merge | `git merge --abort`                             |

---

## 🔹 Troubleshooting & Recovery Commands

### Undo local uncommitted changes

```bash
git restore .
```

### Abort merge or rebase safely

```bash
git merge --abort
# or
git rebase --abort
```

### Re-align local main with upstream

```bash
git fetch upstream
git reset --hard upstream/main
git push --force origin main
```

### View last few commits

```bash
git log --oneline -5
```

### Check last commit differences

```bash
git show HEAD
```

---

## 🔸 Notes

* **Never push to upstream (langgenius)** — only to our fork (`bkitwing/dify`).
* **All internal customizations stay on `main`.**
* If future customization branches are needed (e.g., experimental Docker setup), use:

  ```bash
  git switch -c custom-branch-name
  git push -u origin custom-branch-name
  ```

---

### ✅ Final Setup Summary

* Default branch: **main**
* Push target: **[git@github.com](mailto:git@github.com):bkitwing/dify.git**
* Pull source for updates: **[https://github.com/langgenius/dify.git](https://github.com/langgenius/dify.git)**
* Merge strategy: **keep upstream base + our docker/nginx customizations**

---

**Maintained by:**
🔭 *BK IT Wing — Internal Dify Deployment Team*

