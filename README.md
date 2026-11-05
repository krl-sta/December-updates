<div align="center">

# December

**A dual-pane file manager for macOS, built for people who move files all day.**

Two panes, real keyboard control, a terminal where you need it, and nothing
between you and the disk.

`macOS 15+` · `Apple silicon` · `notarized`

</div>

---

## Why another file manager

Finder is fine until you have to compare two folders, rename forty files, ship
a build somewhere and clean up after it. Then you want the other kind of tool:
two panes side by side, every action on a keyboard, and an undo button that
actually puts things back.

December is that tool, written natively in Swift and AppKit — no Electron, no
web view pretending to be a file list.

## What it does

### Two panes, one keyboard

- Independent panes, each with its own tabs, history and selection.
- Back and forward per pane — on the toolbar, on `⌘←` / `⌘→`, or on the side
  mouse buttons.
- Open in Other Pane, Enclosing Folder, Go to Folder, Home, Root — one chord
  each, with your own drive letters for the left and right pane.
- Branch View flattens a whole subtree into one list when you need to see every
  file at once.

### A directory tree that follows you

One tree per window, folders only, collapsed by default. It tracks whichever
pane has the keyboard, opens a folder in that pane on a double-click, and loads
one level at a time — a deep path costs nothing until you open it.

### File operations you can take back

- Copy, move, duplicate, compress, rename, new file and new folder — all with
  `⌘Z`, and `⌘⇧Z` to redo. Undo restores what a move overwrote, not just the
  fact that you moved something.
- Paste as Move for the times you copied but meant to move.
- Real progress, a queue that behaves when one item fails, and no silent
  partial deletes.
- Folder sizes on demand, not on every keystroke.

### Look before you open

- Quick View previews images, PDFs and text in place, and hands everything
  else to Quick Look.
- The Inspector shows permissions, dates, size, line endings and the Git diff
  for the selection — and can make a file executable without a terminal.
- Git status badges in the list, so a dirty file is obvious before you touch it.
- Markdown files open in a built-in editor with formatting commands and a live
  preview — `⌘S` saves, and the file list stays where it was.

### A terminal in the pane

A real terminal tab next to your files: `Toggle Terminal`, focus switching, its
own font size, sessions across windows, and a command that syncs the shell to
the pane's current directory. Coding agents can be launched straight from there.

### Built to be lived in

- Eight settings panes instead of one long scroll — General, Appearance,
  Terminal, Markdown, Cloud Storage, Coding Agents, AI, Shortcuts.
- Every shortcut is remappable, and conflicts are reported rather than ignored.
- Light and dark themes that follow the system, with the accent colour you pick.
- Remembers window size, tabs and pane paths between launches.

## Install

**Homebrew** (recommended — updates itself afterwards):

```bash
brew trust krl-sta/tap
brew tap krl-sta/tap
brew install --cask december
```

**Direct download:** grab the latest DMG from
[Releases](https://github.com/krl-sta/December-updates/releases/latest), open it
and drag December to Applications. The app is signed with a Developer ID and
notarized by Apple, so it launches without a warning.

## Updates

December checks its own feed and offers new builds in-app. Release notes appear
in the update alert, and nothing installs without your click.

- Latest version: [Releases](https://github.com/krl-sta/December-updates/releases/latest)
- Feed: [appcast.xml](https://raw.githubusercontent.com/krl-sta/December-updates/main/appcast.xml)

That update check is the only network traffic the app makes for itself — there
is no analytics SDK and no telemetry.

## Requirements

- macOS 15 (Sequoia) or later
- Apple silicon

## About this repository

Release artifacts and the Sparkle appcast live here so that December can fetch a
feed and a DMG without authentication. The application source is private; issues
and feedback are welcome in this repository.
