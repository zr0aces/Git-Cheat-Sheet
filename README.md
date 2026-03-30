# Git Cheat Sheet

An interactive, browser-based Git command reference with a live parameter builder and one-click copy-to-clipboard for every snippet.

🌐 **[Live Demo](https://zr0aces.github.io/Git-Cheat-Sheet/)**

---

## Overview

The cheat sheet is a single-page web application (`index.html`) that groups the most common Git commands into focused categories. A **Parameter Builder** at the top of the page lets you enter your branch name, file path, and commit type once; every code snippet on the page updates in real time to reflect those values, so you can copy a command that is already tailored to your current task.

## Features

| Feature | Description |
|---------|-------------|
| **Interactive Workflow** | Five-step visual guide (Pull → Code → Add → Commit → Push) with click-to-copy |
| **Parameter Builder** | Set branch, file, and commit-type once; all snippets update live |
| **Global Search** | Filter commands across all categories; press `/` to focus the search bar |
| **Category Tabs** | Browse All commands or jump to a specific category |
| **Copy to Clipboard** | Click any command or snippet to copy it instantly |
| **Persistent Preferences** | Branch, file, and commit-type values are saved in `localStorage` |

## Command Categories

| Category | Commands covered |
|----------|-----------------|
| 🛠️ **Setup** | `git init`, `git clone`, `git config` |
| ⚡ **Daily** | `git status`, `git add`, `git commit`, `git log` |
| 🌿 **Branching** | `git switch`, `git branch`, `git merge` |
| 🧹 **Cleanup** | Pruning stale branches, `git clean` |
| 🚑 **Rescue** | `git restore`, `git reset`, `git stash`, `git commit --amend` |
| 💡 **Scenarios** | Common multi-step recovery workflows |

For the full command list with examples, see **[docs/commands.md](docs/commands.md)**.

## Usage

No build step or server is required. Open `index.html` directly in any modern browser:

```bash
# Clone the repository
git clone https://github.com/zr0aces/Git-Cheat-Sheet.git
cd Git-Cheat-Sheet

# Open in your default browser (macOS)
open index.html

# Open in your default browser (Linux)
xdg-open index.html

# Open in your default browser (Windows)
start index.html
```

Or simply visit the [hosted version](https://zr0aces.github.io/Git-Cheat-Sheet/).

## Project Structure

```
Git-Cheat-Sheet/
├── index.html        # Single-page application (UI + data + logic)
├── LICENSE           # MIT License
├── README.md         # This file — high-level overview
└── docs/
    ├── commands.md   # Full command reference with examples
    └── features.md   # UI architecture and feature details
```

## Documentation

| Document | Purpose |
|----------|---------|
| `README.md` | Project overview, quick-start, and structure |
| [`docs/commands.md`](docs/commands.md) | Detailed reference for every command and scenario |
| [`docs/features.md`](docs/features.md) | UI feature guide and architecture notes |

## License

[MIT](LICENSE) © 2026 S
