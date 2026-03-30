# Command Reference

Full list of every Git command and scenario included in the cheat sheet, grouped by category. All examples use the placeholder tokens `[branch]`, `[file]`, and `[type]`, which the **Parameter Builder** in the UI replaces with your actual values at runtime.

---

## 🛠️ Setup

Initial configuration commands — run these once when starting a new project or on a fresh machine.

| Command | Description | Example |
|---------|-------------|---------|
| `git init` | Initialize a new local repository | `git init` |
| `git clone <url>` | Clone an existing remote project | `git clone https://github.com/user/project.git` |
| `git config --global user.name 'Name'` | Set your global identity name | `git config --global user.name 'John Doe'` |

---

## ⚡ Daily

The commands you reach for every working session.

| Command | Description | Example |
|---------|-------------|---------|
| `git status` | Check project status | `git status` |
| `git add <file>` | Stage a specific file | `git add [file]` |
| `git add .` | Stage all modifications | `git add .` |
| `git commit -m 'msg'` | Commit staged work | `git commit -m '[type]: update [file]'` |
| `git log --oneline` | View a compact history log | `git log --oneline` |

---

## 🌿 Branching

Create, switch, and integrate branches.

| Command | Description | Example |
|---------|-------------|---------|
| `git switch -c <name>` | Create a new branch and switch to it | `git switch -c [branch]` |
| `git switch <name>` | Switch to an existing branch | `git switch [branch]` |
| `git branch` | List all local branches | `git branch` |
| `git merge <branch>` | Merge a branch into the current branch | `git merge [branch]` |

---

## 🧹 Cleanup

Keep your repository tidy by removing stale local and remote branches.

| Command | Description | Example |
|---------|-------------|---------|
| `git branch --merged` | List branches already merged into the current branch | `git branch --merged` |
| `git fetch --prune` | Sync remote branch deletions to your local list | `git fetch --all --prune` |
| `git push origin --delete <name>` | Delete a branch on the remote | `git push origin --delete [branch]` |
| `git clean -fd` | Remove untracked files and directories | `git clean -fd` |

---

## 🚑 Rescue

Undo, fix, and recover — without losing work.

| Command | Description | Example |
|---------|-------------|---------|
| `git restore <file>` | Discard unstaged changes to a file | `git restore [file]` |
| `git reset --soft HEAD~1` | Undo the last commit, keep changes staged | `git reset --soft HEAD~1` |
| `git commit --amend` | Rewrite the most recent commit message or content | `git commit --amend -m '[type]: fixed [file] issue'` |
| `git stash` | Save work-in-progress without committing | `git stash push -m 'WIP: working on [file]'` |
| `git stash pop` | Restore the most recently stashed work | `git stash pop` |

---

## 💡 Scenarios

Multi-step workflows for common situations that trip people up.

### Committed to the wrong branch

```bash
git reset HEAD~1 --soft        # undo the commit, keep changes staged
git stash                      # stash the staged changes
git switch [branch]            # move to the correct branch
git stash pop                  # reapply your work
```

### Forgot to include a file in the last commit

```bash
git add [file]
git commit --amend --no-edit
```

### Stop tracking a file without deleting it locally

```bash
git rm --cached [file]
```
> After this, add the file to `.gitignore` to prevent it from being re-tracked.

### Quickly save everything as a save-point

```bash
git add . && git commit -m 'chore: [branch] save point'
```

---

## Standard Workflow

The interactive workflow diagram at the top of the cheat sheet represents the standard daily loop:

```
1. Pull    →  git pull
2. Code    →  (make your edits)
3. Add     →  git add .
4. Commit  →  git commit -m '[type]: ...'
5. Push    →  git push
```

Click any step in the UI to copy the corresponding command and jump to the relevant category tab.
