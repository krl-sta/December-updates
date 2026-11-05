# December

A dual-pane (two-panel) file manager for macOS: the Total Commander / Norton
Commander interaction model, rebuilt natively in Swift and AppKit.

Two independent panes with their own tabs and history, a directory tree, full
keyboard control, a Ghostty terminal in the pane, Git status in the file list,
and undo/redo for file operations.

`macOS 15+` · `Apple silicon` · `Developer ID signed and notarized` · `Sparkle updates`

**On this page:** [Install](#install) · [Feature map](#feature-map) ·
[Keyboard reference](#keyboard-reference) ·
[Coming from Total Commander](#coming-from-total-commander) ·
[Settings](#settings) · [Where state lives](#where-state-lives) ·
[Limits](#limits) · [Updates](#updates)

---

## Install

**Homebrew** — the cask keeps the app updated afterwards:

```bash
brew trust krl-sta/tap
brew tap krl-sta/tap
brew install --cask december
```

**Direct download:** take the DMG from the
[latest release](https://github.com/krl-sta/December-updates/releases/latest),
open it, drag **December** to `/Applications`. The bundle is signed with a
Developer ID and notarized by Apple — no Gatekeeper warning.

Requirements: **macOS 15 or later, Apple silicon**. There is no Intel build.

On first launch December asks for **Full Disk Access**. Without it, folders such
as `~/Library/Mail` and other apps' containers are invisible — the grant lives in
System Settings ▸ Privacy & Security ▸ Full Disk Access, and the app links
straight to that pane. Everything outside protected containers works without it.

## Feature map

| Area | What you get |
|---|---|
| **Panes** | Two independent panes, each with its own tabs, history and selection. `Tab` switches panes; `⌘⇧←` / `⌘⇧→` opens the selection in the other pane. |
| **Navigation** | Back/forward per pane (`⌘←` / `⌘→`, toolbar buttons, mouse buttons 3 and 4), `Backspace` up, `⌘⇧G` Go to Folder, `⌘/` root, `⌘⇧H` home, `⌘⌥L` Downloads. Each pane can be bound to a drive (`⌘F1` / `⌘F2`). |
| **Tabs** | Any number per pane: `⌘T` new, `⌘⌥T` reopen closed, `⌘Return` open in a new tab, `⌃Tab` / `⌃⇧Tab` cycle, `⌘1`–`⌘9` jump. |
| **Directory tree** | One tree per window on the left, folders only, collapsed by default. Follows the pane that has keyboard focus, opens a folder in that pane on double-click, loads one level at a time, and centres the revealed row. `⌘⇧E`. |
| **File operations** | Copy, move, rename, duplicate, compress to zip, new file, new folder, move to trash, delete permanently. A queue with progress, per-item failures that do not abort the batch, conflict prompts, and Paste as Move. |
| **Undo / redo** | `⌘Z` / `⌘⇧Z` for copy, move, delete, duplicate, compress, rename, new file and new folder. Undo restores what a move overwrote. Local files only; history is per window and in memory. |
| **Selection** | `⌥Space` toggles an item, `⌘A` all, `Esc` none, keypad `*` or `⌘⇧I` invert. |
| **Search** | `⌘F` (or `⌘P`) fuzzy-finds files in the current folder; inside a document or the terminal the same key means Find in Document. `⌃B` Branch View flattens a whole subtree into one list (`⌃⇧B` includes directories). |
| **Quick View** | `⌃Q` previews in place: text with wrapping, PDF, images, and anything else Quick Look can render. |
| **Inspector** | `⌘I` shows permissions, dates, size, location, line endings and the Git diff for the selection; can make a file executable and open the enclosing repository. |
| **Git** | Status badges in the file list, a repository watcher that refreshes them, and commit history plus diff for a selected file in the Inspector. |
| **Terminal** | Ghostty-based terminal tabs inside the pane: `⌘⌥O` toggle, `⌘O` toggle focus, `⌘⇧T` open in the other pane, `⌘⌥J` sessions, zoom with `⌘=` / `⌘-` / `⌘0`. It syncs the shell to the pane's directory; `⌃Enter` inserts the selection as arguments, `⌘⇧C` copies the last command, `⌘⇧M` turns the output into Markdown, `⌘⇧S` saves it. |
| **Coding agents** | `⌘E` launches Claude Code, Codex, Gemini CLI, Cursor, Aider or OpenCode in a terminal tab, scoped to the selection. |
| **Markdown** | A built-in editor for `.md`: formatting (`⌘B`, `⌘I`, `⌘K` for links, code, quote, strikethrough), `⌘S` to save, `⌘⇧V` to toggle the rendered preview. `⌘J` rewrites the selection with an AI provider (Anthropic or OpenAI key in Settings). |
| **Beyond the local disk** | S3-compatible object storage (AWS S3, Cloudflare R2, MinIO, Backblaze B2 and friends) mounts as a location you can browse, upload to and delete from. `.zip` archives open read-only, without unpacking first. |
| **Favourites** | `⌘⇧D` pins the current folder, `⌃1`–`⌃9` jumps to a pinned folder, and a favourites bar can sit above the panes. |
| **Command palette** | `⌘⇧P` runs any action by name; `⌘⇧/` shows the current keymap as a cheatsheet. |
| **Folder sizes** | "Calculate All Folder Sizes" computes on demand — the list never blocks on `du` while you scroll. |

## Keyboard reference

Everything below is remappable in **Settings ▸ Shortcuts**, including multi-key
chords; conflicts are reported instead of silently swallowing the second binding.

**Navigation**

| Key | Action |
|---|---|
| `Return` | Open selection |
| `Backspace` | Enclosing folder |
| `⌘←` / `⌘→` | Back / forward |
| `⌘⇧H` / `⌘/` / `⌘⌥L` | Home / root / Downloads |
| `⌘⇧G` | Go to Folder |
| `Tab` | Switch pane |
| `⌘⇧←` / `⌘⇧→` | Open selection in the other pane |
| `⌘F1` / `⌘F2` (`⌥⌘1` / `⌥⌘2`) | Left / right pane drive |

**Files**

| Key | Action |
|---|---|
| `F4` | Edit in external editor |
| `F5` | Copy to the other pane |
| `F6` | Move to the other pane |
| `⇧F6` | Rename |
| `F7` / `⇧F7` | New folder / new file |
| `F8` / `⌘⌫` | Move to trash |
| `⇧F8` | Delete permanently |
| `⌥F5` | Compress to zip |
| `⌘D` | Duplicate |
| `F12` / `⌘F12` | Copy folder path / file path |
| `⌘⇧R` | Reveal in Finder |
| `⌘Z` / `⌘⇧Z` | Undo / redo a file operation |

**Selection and view**

| Key | Action |
|---|---|
| `⌥Space` | Toggle item in selection |
| `⌘A` / `Esc` | Select all / deselect |
| `*` (keypad) or `⌘⇧I` | Invert selection |
| `⌘⇧.` | Show hidden files (panes and tree together) |
| `⌃B` / `⌃⇧B` | Branch view / branch view with directories |
| `⌃D` | Cycle date sorting |
| `⌃Q` | Quick View |
| `⌘I` | Inspector |
| `⌘⇧E` | Directory tree |

**Tabs, terminal, agents**

| Key | Action |
|---|---|
| `⌘T` / `⌘W` / `⌘⌥T` | New / close / reopen tab |
| `⌃Tab` / `⌃⇧Tab` | Next / previous tab |
| `⌘⌥O` / `⌘O` | Toggle terminal / toggle terminal focus |
| `⌃⌘T` / `⌘⇧T` | New terminal tab / terminal in the other pane |
| `⌘E` | Run a coding agent on the selection |
| `⌘J` | Rewrite the Markdown selection with AI |

The complete list is in Help ▸ Keyboard Shortcuts, or `⌘⇧/`.

## Coming from Total Commander

December keeps the Commander chords where macOS allows them, and offers a
Finder-friendly alias where it does not (`⌘H` is Hide, so Home is `⌘⇧H`).

| Total Commander | December |
|---|---|
| `Ctrl+T` new tab | `⌘T` |
| `F3` view | `⌃Q` Quick View |
| `F4` edit | `F4` |
| `F5` copy | `F5` |
| `F6` move | `F6` |
| `F7` new folder | `F7` |
| `F8` delete | `F8`, `⇧F8` for permanent |
| `Ctrl+B` branch view | `⌃B` |
| `Ctrl+Q` quick view panel | `⌃Q` (floating preview) |
| `Ctrl+Enter` insert name into the command line | `⌃Enter` inserts into the terminal |
| `Tab` switch panel | `Tab` |
| `Ctrl+F1` / `Ctrl+F2` change drive | `⌘F1` / `⌘F2`, or `⌥⌘1` / `⌥⌘2` |
| Separate tree | `⌘⇧E` — one tree per window, not one per pane |

## Settings

Eight panes, `⌘1`–`⌘8` to switch; window size and the last pane are remembered.

**General** (default folder, confirmation before delete, Full Disk Access) ·
**Appearance** (theme light/dark/system, file list font and size, Git badges,
status marks) · **Terminal** (shell path, font and size, scrollback, bell) ·
**Markdown** (editor font and size, default view) · **Cloud Storage**
(S3-compatible connections) · **Coding Agents** (which agents are offered) ·
**AI** (Anthropic / OpenAI keys for rewrite) · **Shortcuts** (the full keymap).

## Where state lives

- Settings and window state are stored in the app's `UserDefaults`, domain
  `com.kirillstashevsky.december` — no database, no sidecar config files.
- Window geometry, tabs, pane paths, tree width and visibility are restored on
  launch. `defaults delete com.kirillstashevsky.december` resets everything.
- Object storage credentials live in the same preferences and nowhere else.
- December keeps no index and no database inside the folders you browse.

## Limits

Stated plainly, because they decide whether this is the right app for you:

- **Apple silicon only**, macOS 15+. No Intel build.
- **No SFTP, FTP, WebDAV or SMB browsing.** Remote work means S3-compatible
  object storage; network shares are expected to be mounted by macOS.
- **No folder compare or directory sync** between the two panes.
- **Undo history is per window and in memory** — closing the window discards it.
- **Archive support is read-only** and covers `.zip`.
- **Source is private.** There is no build-from-source path; releases ship as
  signed, notarized binaries.

## Updates

December updates through Sparkle 2 with an EdDSA-signed feed:

- Feed: <https://december-feed.k-stashevsky.workers.dev/appcast.xml>
- Releases: <https://github.com/krl-sta/December-updates/releases>

The update check is the app's only background network request — no analytics
SDK, no telemetry, no account. Release notes appear in the update alert, and
nothing installs without a click.

## About this repository

Release artifacts and the Sparkle appcast live here so the app can fetch a feed
and a DMG without authentication. The source is private; bug reports and feature
requests are welcome in this repository's issues.
