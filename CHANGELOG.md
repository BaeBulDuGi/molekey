# Changelog

User-facing changes per released version. Versions not listed were internal
iterations. Dates are release dates.

## 0.38.2 — 2026-10-01

- Restore shortcuts preserves keys that already existed before the profile was
  applied, including factory shortcuts, and verifies the resulting bindings.
- Back up nameless extension commands under distinct command IDs. Ambiguous
  entries in older backups are skipped during restore instead of assigning
  another command's shortcuts.

## 0.38.1 — 2026-10-01

- Fix Korean arrow-key bindings failing when the shortcut profile is reapplied.
  Convert localized arrow names to the accepted write format when applying,
  restoring, or resolving shortcut conflicts, while retaining localized scopes.

- Resolve Text Editor shortcut scopes from editor bindings rather than the first
  available scope. Korean installations with missing default bindings use the
  localized editor scope, and Quick Actions no longer selects a XAML scope first.

- Navigation finders keep status and key hints on separate lines, and shrink a
  large preview to keep results and controls visible in a small window.
- Long member names and parameter lists use separate trimmed lines with full
  tooltips. Member group headers keep counts visible. Line-number columns reserve
  space for six digits; search hints and keyboard-focus indicators are clearer.
- Reference/tag file groups display their directories. Narrow file/symbol paths
  keep the distinguishing suffix, with the full path in tooltips and accessibility names.
- Jump History marks the current file/line and explains its previous-location
  selection. Browsing previews leaves the editor in place; Esc restores its
  window focus, and selecting Current preserves the caret column and selection.
  Open-buffer previews include unsaved edits. Repeated invocation reuses the
  open dialog; failed navigation shows a retry/cancel hint.
- File Finder records the departure location before opening files. Jump History
  selects the newest location different from the current file/line instead of
  blindly skipping the first entry; displayed return targets remain stable when
  nearby history entries are updated.
- File/history refreshes and member sort/group changes retain surviving selections
  and preview scroll positions. File refresh also retains multiple selections by
  full path. Failed member/history jumps leave the finder open, and navigation
  checks the active document before moving its caret.
- Replacing a reference search or closing its tab now cancels the previous scan;
  solution closure and pane disposal cancel tab searches as well. Late results
  remain suppressed, and cancellation is not reported as an unreadable file.
- Reference searches capture only open C/C++ documents and log separate capture,
  scan and result-layout times locally. A reproducible index-only performance
  script and synthetic baseline document the measurement scope and limitations.
- References handle bare F5 in the focused pane's keyboard preprocessing stage
  and provide a Refresh results context-menu action. Modified F5 shortcuts pass
  through; holding F5 does not repeatedly start scans. Verified in the current VS environment.
- Reference list keyboard focus follows the selected row. Empty Enter in the
  shortcut capture dialog no longer creates an Enter binding. Jump History uses
  Ctrl+Shift+Delete to clear the trail; plain Delete edits the search text.
- C/C++ reference results now disclose name-based matching, scanned/collected file
  counts, skipped files and hits omitted by the 2,000-result limit. Tooltips
  explain size/read exclusions and combined same-name symbols. Empty searches
  distinguish no collected files from no matches in a partially scanned scope.
- UI consistency pass across file/symbol/member finders, jump history, hashtags,
  references, query/key dialogs and the MoleKey settings panel. Search fields
  expose their localized hints to accessibility tools; layout rounding, readable
  secondary text, path tooltips and visible preview splitter grips improve use
  at smaller window sizes.
- References and hashtag locations share compact file headers with disclosure
  arrows, result counts and full-path tooltips. Line numbers keep a compact width
  while code fills the remainder; the reference filter adapts to pane width.
- Hashtag tag/results columns can be resized. Dialogs and settings controls have
  explicit keyboard-focus outlines; default dialog actions are highlighted.
  Reference tab close targets are larger and have accessible search names.
- The settings navigation is narrower and scrollable in short panes. Content
  keeps a readable minimum width with horizontal scrolling in narrow docks;
  the title tagline trims with a tooltip instead of overflowing.
- Reference result groups use pixel scrolling that includes file headers, and
  file names come from the group path rather than its first result row. This
  addresses headers disappearing after scrolling down and back to the top;
  verified in the current Visual Studio environment.
- Reported issue: F5 in the docked references pane invoked Visual Studio's
  build/debug command. Pane keyboard preprocessing is implemented and verified
  in the current VS environment. Refresh results in the context menu is also available.
- Find References uses the MoleKey title-bar icon and themed Find/Cancel buttons.
  The docked pane omits the New search/Close all toolbar to leave more room for
  results; individual search tabs still have close buttons.
- Submitting a reference search focuses its result row for immediate arrow-key
  navigation. A completed background scan does not steal focus from the editor
  or the result filter.
- Reference searches show a searching state instead of an empty-results message
  while running, and a retry hint on failure. F5 keeps existing results visible,
  preserves selection by file and line, and restores scroll offsets (clamped if
  results shrink). If the selected result disappears, a nearby row is selected.
- Alt+Shift+F opens a separate search dialog, including from whitespace in a
  C/C++ editor. The docked pane now contains compact result tabs and a result
  filter; entering a new search no longer takes space away from the results.
- C/C++ references now open in a dockable tool window beside Output. Each search
  keeps its own tab, results and filter while navigating code. Repeating a name
  refreshes its tab; F5 reads the latest buffers. Tabs can be closed individually
  and are cleared when the solution closes.
- Find References accepts a typed function or variable name. The caret word is
  an optional starting query; press Enter or Find to search, and use the separate
  filter to narrow results by code or file name.
- C/C++ Find All References now includes variable declarations, reads and writes,
  plus function addresses. Results match exact names across scopes and show one
  row per line, excluding comments and literals. Function reference lenses keep
  their call-only counts.

- Switching finder modes with an empty query keeps the query empty instead of
  recalling an older search. Footer key labels stay together when wrapping.
- Dialog centring now happens before the first native display, avoiding a
  briefly visible frame at the old position. Clicking the active finder tab
  keeps it selected; shortcut legends wrap in narrower windows.
- Shortcut-opened windows are centred precisely on the Visual Studio frame,
  including mixed-DPI and multi-monitor setups.
- Finder windows have a cleaner, more responsive layout: adjustable remembered
  previews, mode tabs, compact key legends, adaptive columns, quieter selection,
  role-based typography, and useful empty/indexing states.
- Repeated MoleKey logos were removed from result rows; semantic file and symbol
  icons remain.

## 0.38.0 — 2026-08-31

A trust and recovery release before the clean-install gate.

- **Health & Restore is now a first-class page** in the MoleKey window. It
  shows shortcut-profile state, shortcut and color backup availability,
  command-hook health and the local data folder in one place.
- **Recovery actions are together and visible.** Run Self-Diagnose, restore
  shortcuts, restore colors and return stolen keys without hunting through
  separate settings pages. The page also explains what remains after
  uninstalling and what to restore first.
- **Restoring shortcuts now turns profile auto-apply off.** A restored setup
  stays restored after restart instead of presenting an ambiguous applied
  state or being reapplied by a future profile change.
- **Color presets have neutral names:** the vivid dark and light presets are
  now `Rich Dark` and `Rich Light`. Existing settings from earlier versions
  continue to load the matching renamed preset.
- User-facing terminology is now product-neutral. Product documentation now
  includes the clean install/restore gate and the staged monetization plan.

## 0.37.0 — 2026-08-01

A navigation cycle: the finders got the matching and the handoffs they were
missing, and two new browsers cover ground Visual Studio leaves open — where
your TODOs are, and where you have been.

- **Fuzzy matching in every finder.** Typing `mkap` to reach
  `MasterKeyApplier` already worked in Open File in Solution; Find Symbol
  (`Alt+Shift+S`) and List Methods (`Alt+M`) only did substring matching, so
  the same query came back empty there. All three now share one matcher.
  Exact hits are unaffected — prefix and substring results still sort above
  fuzzy ones, so nothing you already type reshuffles.
- **Switch finders without retyping.** In any of the three finders, `Ctrl+Tab`
  cycles file → member → symbol (`Ctrl+Shift+Tab` backwards, `Ctrl+1/2/3`
  jumps straight to one) and your query comes along. Reaching for `Alt+M`
  when the symbol was in another file no longer means Esc, another chord and
  typing it again.
- **Finders reopen with your last query**, selected — Enter repeats the jump
  you just made, typing starts a fresh search, so neither case costs a
  keystroke more than before. Remembered per finder, for the current Visual
  Studio session only. Off switch in Tools → Options → MoleKey → Navigation.
- **Open File in Solution: `Ctrl+Enter` and `Alt+Enter`.** Ctrl+Enter drops the
  file into a side-by-side tab group instead of on top of what you were
  reading; Alt+Enter opens its header/source counterpart, for when the list
  gave you `foo.h` and you meant `foo.cpp`. Both fall back to a plain open
  when they don't apply.
- **Self-Diagnose now reports who else holds MoleKey's own keys**, flagging a
  conflicting Text Editor scope binding — the kind that silently wins over
  ours whenever focus is in the editor.
- **Visual Studio editor settings** on the Colors & theme page: map mode for
  the vertical scroll bar, the map's source-preview tooltip, scroll bar marks
  and line numbers. These are VS's own settings, not MoleKey's — they're here
  because VS 2026 doesn't carry them over from 2022 either, and the pages they
  used to live on moved. Each switch reads VS's actual state, so it can't drift
  from what Tools → Options says.
- **Import colors from Visual Studio 2022** (Colors & theme → *Import from
  VS 2022…*). VS 2026 doesn't carry Fonts and Colors over, and importing the
  `.vssettings` through VS itself silently drops every C++ item because 2026
  renamed them (`cppType` → `CppTypeSemanticTokenFormat`, …). MoleKey already
  had that rename table for its presets, so it maps through and lands the C++
  colors too. Export from VS 2022 with Tools → Import and Export Settings →
  Fonts and Colors. Your current colors are backed up first, so *Restore
  Defaults* undoes an import.
- **Jump History (`Shift+Alt+J`)** — the trail of places you've been this
  session, as a filterable list with code previews. Navigate-backward
  (`Ctrl+-`) walks the same trail one blind step at a time, and overshooting
  loses the spot; here you can see it and go straight there. It opens with the
  *previous* location selected, so Enter means "back one". `F5` refreshes,
  `Del` empties it. Entries come from MoleKey navigations and from the caret
  position of each document as you visit it; nothing is written to disk.
- **Task markers browser (`Shift+Alt+K`)** — every `TODO`, `FIXME`, `HACK`,
  `BUG`, `XXX` and `UNDONE` written in comments across the solution, in the
  same two-panel browser as the hashtags: markers with counts on the left,
  their locations on the right, Enter jumps. Only uppercase markers inside
  comments count, so prose and string literals stay out. Unlike the built-in
  task list this covers the whole solution, not just open files. Edit the
  marker list with `task_markers` in `settings.txt`.
- **List Methods (`Alt+M`) groups members by their class**, with a collapsible
  header and a count, so a long file reads as its types instead of one run of
  names. Order inside a group is unchanged, so "file order" still reads
  top-to-bottom. `F7` turns grouping off (remembered), which brings the "In"
  column back.
- **Shortcuts inside the finders no longer leak to Visual Studio.** `Ctrl+Enter`
  ran the editor's line command instead of opening the file beside your work,
  and `Alt+Enter` brought a tool window forward — any chord VS itself binds was
  taken before the finder saw it, while keys VS doesn't bind (Enter, Esc, the
  arrows) arrived normally. The finders now announce themselves as modal, so
  they get their own keystrokes.
- **`Ctrl+Enter` reuses the side group instead of stacking another.** Pressing
  it with the caret already in the right-hand group used to grow a third tab
  group, then a fourth.
- **`Alt+Shift+W` jumps the caret across a split**, leaving every tab where it
  is. It returns to the document you last left on that side, so pressing it
  repeatedly is a back-and-forth between the two files you are actually
  reading, and switching tabs by hand on one side makes that the tab you come
  back to. (With several tabs open on the far side it can still arrive on the
  wrong one before that back-and-forth settles; being worked on.)
  `Ctrl+F6` gets there eventually but walks every open file on the
  way, and Visual Studio's own tab-group commands all *move* documents rather
  than following one with the caret.
- **Opening a file that's already on the other side of a split takes you
  there.** Picking it in a finder used to leave the caret in the group you
  started from, looking at the file you already had.
- **`Alt+Shift+U` undoes a split**, from the editor — where you are when you
  want your layout back. Everything returns to a single group. It rides
  `Window.MoveAllToPreviousTabGroup`, a built-in command that ships without a
  shortcut, and comes with the MoleKey profile like the rest.
- **Jumps land on the symbol, not on a stale line number.** Find Symbol
  (`Alt+Shift+S`) builds its index once per session, so editing a file
  afterwards left every symbol below the edit pointing at the wrong line —
  Enter dropped the caret somewhere unrelated. Every MoleKey jump that names a
  symbol now checks that the line actually holds it and, if not, takes the
  nearest line that does. The preview pane shows the corrected line too, so
  what you see is where you land. This also covers C++ start points that
  Visual Studio 2026 reports off by a few lines. `F5` in the finder still
  rebuilds the index outright.
- **Surround With moves to `Alt+Shift+X`** in the shortcut profile. It was on
  `Alt+X, S`, which could never have worked — `Alt+X` is Insert Snippet, a
  complete shortcut, so nothing can follow it and Visual Studio dropped the
  binding without complaint. If you were reaching for it and getting nothing,
  that is why.
- **`Ctrl+Shift+G` works on Visual Studio 2026.** It had been declared the way
  an extension normally declares a key, which 2026 ignores, so the chord did
  nothing there. It now rides the C++ *Open Document* command that owns the key
  by default — the same technique `Alt+Shift+F` and `Ctrl+F12` already use — so
  the key never has to move. MoleKey searches the whole solution and offers the
  file finder when the name is ambiguous, where the built-in searches only your
  include directories; when the caret line holds no path at all, the built-in
  runs untouched. Switch it off in Tools → Options → MoleKey → Navigation to
  give the key back.
- `Shift+Alt+K` and `Shift+Alt+J` are part of the shortcut profile, like
  `Alt+M` and `Alt+Shift+S`. Visual Studio 2026 does not honor an extension's
  built-in key declarations, so on 2026 these two chords exist only once the
  profile has been applied — the MoleKey window's MasterKey page applies it,
  and *Restore* takes both keys back out again.

## 0.36.15 — 2026-07-28
- Listing fix: the extension description showed a corrupted character where
  "declaration/definition toggle" should have been.
- The Marketplace tags now cover what people actually search for (code
  navigation, go to definition, reference count, bookmarks, syntax
  highlighting, colorblind, keybindings, C++/C#, VS 2026).
- No changes to the extension itself.

## 0.36.14 — 2026-07-27
- Packaging-only release. No functional changes since 0.36.13 — this is the
  build that brings everything below to the Marketplace, which had been sitting
  at 0.36.1.

## 0.36.13 — 2026-07-26
- **Hashtags** no longer require 3 characters — any `#tag` that starts with a
  letter now counts (`#a`, `#가`, `#ui`), in comments, English or Korean. Issue
  refs like `#1` / `#123` still stay out of the index.
- **My Keys** is now under an **Advanced** section in the nav — the finders and
  the MoleKey profile cover the everyday cases, and custom key rebinding is a
  power-user extra. Its page now opens by saying so, with a concrete example
  (put Ctrl+D on Edit.Duplicate) instead of jumping straight into the mechanics.
- The **My Keys** page is redrawn as a compact checker list like
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
- The **Colors & theme** page is redrawn as a compact checker list.
  Instead of a "Preset vs. Custom" radio split, there is one grid: pick a
  starting **Set** (dark / light / colorblind variants),
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
  counts, promotional copy, export, reset — is gone; a programmer wants to know
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
- Selection match highlighting (works in comments/strings) with
  scrollbar marks and a match count
- Two-stroke chord capture ("Ctrl+R, Ctrl+R") in My Keys
- Key stealing with restore, .vskeys export/import, startup re-apply
- Hashtag hover previews, path filter tokens, colorblind color presets
- Korean UI throughout; file-list cache and streaming symbol scans

## 0.9 – 0.23 — 2026-07-05 · 06
- A keyboard-first navigation set: Open File in Solution (Alt+Shift+O), List
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
