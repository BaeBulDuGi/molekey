# Changelog

User-facing changes per released version. Versions not listed were internal
iterations. Dates are release dates.

## 0.36.13 — 2026-07-26
- **Hashtags** no longer require 3 characters — any `#tag` that starts with a
  letter now counts (`#a`, `#가`, `#ui`), in comments, English or Korean. Issue
  refs like `#1` / `#123` still stay out of the index.
- **My Keys** is now under an **Advanced** section in the nav — the finders and
  the MoleKey profile cover the everyday cases, and custom key rebinding is a
  power-user extra. Its page now opens by saying so, with a concrete example
  (put Ctrl+D on Edit.Duplicate) instead of jumping straight into the mechanics.
- The **My Keys** page is redrawn as the same Visual-Assist-style checker list as
  the Colors page: a bordered card with a column header and clean rows instead of
  a grid. Each row shows its command, the key you're adding, the command's current
  bindings and any conflicts, with a status pill (green when applied, red when the
  command rejected the key) and an inline **×** to remove it — no more "select the
  row, then click Remove". A filter box narrows the list.

## 0.36.11 — 2026-07-24
- Clicking (or pressing Enter on) a result in **Find References** (Shift+Alt+F),
  the **symbol finder**, and the **member list** now lands the caret **on the
  symbol name** and selects it, instead of dropping to the start of the line.
  Leading tabs no longer skew the position, and whole-word matching keeps `foo`
  from landing inside `foobar`.

## 0.36.10 — 2026-07-23
- The **Colors & theme** page is redrawn as a Visual-Assist-style checker list.
  Instead of a "Preset vs. Custom" radio split, there is one grid: pick a
  starting **Set** (VA Dark / VA Light / Colorblind Dark / Colorblind Light),
  then tick the classifications you want and click a swatch to recolor. Rows are
  grouped (types & namespaces / members / variables / C++), each with its own
  color, a hex box, and Bold / Italic toggles.
- Editing any color turns the set into **Custom**; **Duplicate & edit** copies a
  preset so you can tweak from it, and **Reset to set** discards your edits.
  Unticked rows are left at the Visual Studio default, so you can color just a
  subset. A filter box narrows the list.
- The MoleKey window is **retoned to a deep-emerald brand on slate neutrals**
  (both light and dark), and its controls are now **custom-drawn** instead of
  the stock Visual Studio / WPF chrome: rounded checkboxes with an emerald
  check, on/off **switches** for settings, a styled dropdown, inputs, toggles,
  buttons, and a thin scrollbar — all sharing the one accent.

## 0.36.7 — 2026-07-23
- The MoleKey window (Ctrl+Alt+K) is redesigned around a left-hand category
  navigation instead of top tabs — grouped nav rows with an accent-marked
  selection, in the same green palette.
- The main page is now a **how-to-use guide**: each feature MoleKey adds,
  grouped by purpose (jump around code / search the solution / always-on),
  with its key and a one-line description. The old usage-stats cheat sheet —
  counts, "muscle memory", export, reset — is gone; a programmer wants to know
  what's here and how to reach it, not how many times a key was pressed.
- Fixed: the window could open with a nav row highlighted but the pane blank
  until a second click.

## 0.36.5 — 2026-07-23
- The Find References window (Alt+Shift+F) now has a filter box: type to narrow
  the results by code line or file name (space = AND). The file grouping and the
  reference/decl/def count both follow the filter, and ↑↓ · Ctrl+Home/End step
  through the narrowed list.

## 0.36.4 — 2026-07-23
- Ctrl+Home / Ctrl+End jump to the first / last result in the file, member and
  symbol finders (plain Home/End still move the caret inside the search box).

## 0.36.3 — 2026-07-22
- The file (Alt+Shift+O), member (Alt+M) and symbol (Alt+Shift+S) finders now
  keep a persistent key legend on the bottom bar — ↑↓ move · Enter · Tab
  preview · Esc, plus each finder's own key (F5 refresh/rescan, F8 sort). It no
  longer scrolls away behind the result count as you type.
- The three finders now share one implementation of their common keyboard and
  selection behaviour, so they stay consistent with each other.

## 0.36.1 — 2026-07-21
- Fixed: the MoleKey shortcut profile could silently fail to apply on a
  second Visual Studio instance of the same version (a side-by-side
  install, or an Experimental/rootSuffix hive) — it shared an
  "already applied" marker with the first instance and skipped writing
  its own key bindings while still reporting itself as up to date. The
  marker is now keyed per VS instance instead of per version.

## 0.36.0 — 2026-07-19
- Tools → Options → MoleKey gains a **Navigation** section: C++ Find All
  References routing, the C++ declaration/definition toggle, the
  solution-wide header/source toggle and status-bar shortcut tips can all be
  switched off there now (previously settings.txt only)
- The cheatsheet opens with the search box focused — Ctrl+Alt+K and type
- Removed the quiz for good (hidden since 0.9.0; the code is gone too)
- GitHub Releases are now titled "MoleKey vX.Y.Z" with the asset named
  MoleKey.vsix

## 0.35.4 — 2026-07-18
- The cheatsheet header now shows a weekly mini-dashboard: shortcut uses over
  the last 7 days as a sparkline, plus a rough "menu time saved" estimate.
  Daily counts live in usage_daily.txt next to the other local data and are
  cleared by the same Reset-stats button

## 0.35.3 — 2026-07-18
- Column guide is now **off by default** (new installs) — it was mistaken for
  a broken splitter; turn it on in the cheatsheet or Tools → Options
- New options: column guide position (80/100/120…, default 120) and the
  minimum block height for "} // name" scope-end comments (default 24 lines)

## 0.35.2 — 2026-07-18
- The `/path` filter token now works in the file finder (Alt+Shift+O) and the
  symbol finder (Alt+Shift+S), not just the hashtag browser: `render /src`
  keeps only results whose file path contains `src`

## 0.35.1 — 2026-07-18
- C/C++: Ctrl+F12 (Go To Declaration) now toggles between a function's
  declaration and its definition — header ⇄ source in one keystroke, cycling
  through overload lines, powered by the same index as the reference lens
  (works on VS 2026 where the browse database is often stale). Non-C++
  files and unknown symbols keep the built-in behavior; opt out with
  cpp_goto_decldef=0 in settings.txt

## 0.35.0 — 2026-07-18
- The extension is now **MoleKey** (formerly VsMasterKey) — matching the mole
  logo. Every window title, menu, option page, dialog and Fonts-and-Colors
  entry shows the new name
- Nothing breaks on update: command names (VsMasterKey.*), your key bindings,
  colors and all saved data are untouched — the rename is display-only

## 0.34.1 — 2026-07-18
- Find Symbol index now warms up in the background after a solution loads —
  the first Alt+Shift+S opens against a ready cache instead of paying the
  whole scan interactively (CodeModel phase runs only at editor idle; opt
  out with symbol_warmup=0 in settings.txt)

## 0.34.0 — 2026-07-17
- Cheatsheet & Settings window (Ctrl+Alt+K) now follows the VS theme — dark
  surface on dark IDEs — and uses the brand green accent from the mole logo
- First test coverage for the key-binding merge/normalize engine (the code
  that touches your keyboard store); 50 unit tests total, run on every CI build
- Public changelog (this file) and automated GitHub Releases with the VSIX
  attached on every version tag

## 0.33.5 — 2026-07-17
- Fixed Ctrl+Alt+K (Cheatsheet) doing nothing on Visual Studio 2026
- New option: Finder window theme (Auto / Light / Dark) — force the finder
  windows light or dark independent of the VS theme (Tools → Options →
  VsMasterKey)

## 0.33.4 — 2026-07-17
- New simplified mole logo (third iteration — radically simple this time)
- The logo now sits in each finder window's title bar, and every result row
  carries a small mole mark
- Finder windows show a proper title-bar icon (window style switched; still
  no minimize/maximize clutter)

## 0.33.2 — 2026-07-17
- First mole logo: VSIX icon and marketplace preview replaced

## 0.33.1 — 2026-07-17
- New "Self-Diagnose (log)" command in the VsMasterKey menu: writes profile
  binding read-back, hook health and index cache state to nav_diag.log and
  opens it — attach it to any bug report

## 0.33.0 — 2026-07-17
- Reference lists now tell declarations/definitions apart from call sites:
  they are badged "decl/def", excluded from the reference counts (no more +1
  from a header prototype), and kept in the lists as a header↔source jump

## 0.32.x — 2026-07-16 · 17
- Alt+M member list: 3-tier collection (code model → Roslyn → text scan) with
  overload signatures — reliable on the VS 2026 C++ editor
- Find Symbol (Alt+Shift+S): text-scan fallback for C/C++ files the code
  model misses — full function coverage on VS 2026
- Reference lists: editor-palette syntax colors in previews
- Hashtag Goto grouped by file; arrow keys skip group headers

## 0.31.x — 2026-07-15 · 16
- C/C++ Find All References (Alt+Shift+F): solution-wide call-site list,
  grouped by file — works where the VS browse database is empty or stale
- CodeLens-style "N references" count on C++ function signatures (click for
  the list); C# keeps real CodeLens
- Smarter Alt+O header/source toggle: finds the counterpart anywhere in the
  solution, not just next to the current file

## 0.30.x — 2026-07-08 · 09
- Find Symbol indexes C# via Roslyn off the UI thread — large-solution scans
  no longer freeze the window
- Fixed Shift+Alt+O reliably opening the file finder on both VS 2022 and 2026
- MasterKey tab simplified to view-only; all key editing lives in My Keys

## 0.24 – 0.29 — 2026-07-07
- Open File Under Caret (Ctrl+Shift+G): resolves the #include or path at the
  caret across the whole solution
- Selection match highlighting (VA style, works in comments/strings) with
  scrollbar marks and a match count
- Two-stroke chord capture ("Ctrl+R, Ctrl+R") in My Keys
- Key stealing with restore, .vskeys export/import, startup re-apply
- Hashtag hover previews, path filter tokens, colorblind color presets
- Korean UI throughout; file-list cache and streaming symbol scans

## 0.9 – 0.23 — 2026-07-05 · 06
- The VA-style navigation set: Open File in Solution (Alt+Shift+O), List
  Methods in File (Alt+M), Find Symbol in Solution (Alt+Shift+S), comment
  #hashtags with browser/goto/highlighting/autocompletion (Shift+Alt+H/G)
- Finder UI: themed styles, match highlighting, kind icons, preview panes,
  window size memory, top-level VsMasterKey menu, Tools → Options page

## 0.5 – 0.8 — 2026-07-04
- Consent-based MasterKey shortcut profile with backup and one-click restore
- Custom key binding editor (My Keys) for any VS command
- Real current bindings shown in the cheatsheet; binding conflict scanning
- Enhanced syntax coloring presets (VS 2022 and 2026, including the 2026 C++
  editor rework)
