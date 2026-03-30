# Features & Architecture

This document describes the UI features and internal architecture of the Git Cheat Sheet single-page application.

---

## Technology Stack

| Technology | Role |
|-----------|------|
| **HTML5 / Vanilla JS** | Application structure and logic — no framework or build step |
| **Tailwind CSS (CDN)** | Utility-first styling loaded from the Tailwind Play CDN |
| **Google Fonts (CDN)** | `Inter` for UI text; `Fira Code` for monospace command snippets |
| **`localStorage`** | Persists the user's branch, file, and commit-type preferences across page reloads |

The entire application is self-contained in a single file, `index.html`. There is no build step, no package manager, and no server-side logic required.

---

## UI Layout

```
┌─────────────────────────────────────────────────────┐
│  Header                                             │
│  ├─ Title & subtitle                                │
│  ├─ Parameter Builder  (branch / file / type)       │
│  ├─ Interactive Workflow  (5-step visual guide)      │
│  └─ Global Search bar                              │
├─────────────────────────────────────────────────────┤
│  Main                                               │
│  ├─ Category Tab bar                               │
│  └─ Commands Grid  (responsive 1 / 2 / 3 columns)  │
└─────────────────────────────────────────────────────┘
```

---

## Features

### Parameter Builder

Three inputs at the top of the page act as live variables:

| Input | Placeholder token | Default (if blank) |
|-------|-------------------|--------------------|
| Branch Name | `[branch]` | `main` |
| File / Path | `[file]` | `index.html` |
| Commit Type | `[type]` | `feat` |

Every command card has a **Live Snippet** section. As you type into these inputs, all snippets across the page update in real time via the `processExample` and `highlightParams` JavaScript functions. Placeholder tokens in the snippets are highlighted in orange.

The values are persisted to `localStorage` under the keys `gitBranch`, `gitFile`, and `gitType`, so they survive page reloads.

### Interactive Workflow

A horizontal five-step diagram shows the standard Git loop:

```
1. Pull → 2. Code → 3. Add → 4. Commit → 5. Push
```

The **Pull**, **Add**, **Commit**, and **Push** steps are clickable buttons. Clicking one copies the corresponding command to the clipboard and switches the tab to the relevant category (Daily for Add/Commit, Daily for Pull/Push).

The **Code** step is intentionally non-interactive — it represents local editing that happens outside of Git.

### Global Search

The search bar (or press `/` to focus it from anywhere) filters command cards in real time. A card is shown if the query matches the command syntax, the description, or the category name. When no results match, an inline message is displayed.

### Category Tabs

All commands are available under the **All** tab. Additional tabs let you focus on a single category:

- 🛠️ Setup
- ⚡ Daily
- 🌿 Branching
- 🧹 Cleanup
- 🚑 Rescue
- 💡 Scenarios

The active tab is persisted in `localStorage` under the key `gitTab`.

### Command Cards

Each card displays:

1. **Command syntax** (orange badge, top-left) — click to copy the raw command.
2. **Category icon** (top-right) — greyed out until hovered.
3. **Description** — plain English explanation.
4. **Category label** — shown only when the "All" tab is active.
5. **Live Snippet** — the full example with parameter tokens resolved; click the copy icon to copy.

Clicking anywhere on the command badge or the copy icon triggers the clipboard action and shows a toast notification at the bottom of the screen.

### Copy Toast

A non-blocking "Copied to clipboard" notification slides up from the bottom of the screen for 2 seconds after any copy action. The affected card also receives a brief orange pulse animation (`pulse-copy`).

---

## Data Structure

All command data lives in the `gitData` array inside `index.html`. Each entry has the following shape:

```js
{
  category: "CategoryName",   // displayed in the tab bar and on cards
  icon: '🔣',                 // emoji shown on cards
  commands: [
    {
      cmd:     "git example <arg>",   // syntax shown in the command badge
      desc:    "Plain description",   // human-readable explanation
      example: "git example [branch]" // snippet with optional [branch]/[file]/[type] tokens
    }
  ]
}
```

To add a new command, append an object to the `commands` array of the appropriate category, or create a new category object in `gitData`.

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `/` | Focus the global search bar (when not already in a text field) |
