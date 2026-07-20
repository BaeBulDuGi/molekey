<img src="images/icon.png" width="64" align="right" alt="MoleKey icon" />

# MoleKey

**Keyboard-first navigation and comfort pack for Visual Studio 2022 / 2026.**

If your fingers remember `Alt+Shift+O`, `Alt+M`, `Shift+Alt+H` from other
productivity tools, MoleKey gives that muscle memory a home — dig through
your code and pop up exactly where you meant to, with every change backed
up first and restorable in one click.

## Install

Download **MoleKey.vsix** from the
[latest release](https://github.com/BaeBulDuGi/molekey/releases/latest) and
double-click it. The installer detects every Visual Studio 2022 / 2026
instance on the machine (amd64 and ARM64) and lets you pick where to install.

## Navigation

| Key | Window |
|---|---|
| `Alt+Shift+O` | **Open File in Solution** — every solution file, filtered as you type (space = AND terms) |
| `Alt+M` | **List Methods in File** — the active document's functions/fields/types, Enter jumps |
| `Alt+Shift+S` | **Find Symbol in Solution** — every type & member defined in your code |
| `Alt+Shift+F` | **Find All References** — C/C++ gets a call-site list grouped by file; other languages keep the VS window |
| `Ctrl+Shift+G` | **Open File Under Caret** — resolves the `#include` or path at the caret across the whole solution |
| `Shift+Alt+H` | **Hashtags** — browse every `#tag` written in comments across the solution |
| `Shift+Alt+G` | **Goto Hashtag** — locations of the `#tag` under the caret, Enter = next |
| `Ctrl+F12` | **Toggle Declaration/Definition** — C/C++ functions jump between the `.h` prototype and the `.cpp` body |

All finders share one flow: type to filter → arrows to pick (without leaving
the search box) → Enter to jump → Esc to close. Filter tokens work everywhere:
`/src` narrows results to paths containing `src`, and `.cpp` (file finder)
filters by extension.

## Hashtags — bookmarks that move with your code

Write `#likeThis` (3+ chars, Unicode/Korean OK) in any comment:

```cpp
// #renderLoop frame starts here
/* #refactor split this class */
```

- Tags render **underlined in link-blue** right in the editor
- Typing `#` in a comment **autocompletes** existing tags
- Preprocessor directives (`#include`, `#region`) are never mistaken for tags
- Solution-wide index with per-file caching; unsaved edits included

## C/C++ references

- `Alt+Shift+F` on a C/C++ symbol lists its call sites grouped by file, with
  syntax-colored previews — including on VS 2026's new C++ editor
- An inline **"N references"** count next to each function definition (the
  CodeLens C++ never got); click it to open the same list
- `Alt+O` toggles header/source even when the counterpart lives in another
  folder or project — the whole solution is searched
- `Ctrl+F12` toggles between a function's declaration and its definition
  (and cycles through overload lines) — no browse database required

## Shortcut profile & custom keys

- **MoleKey profile**: a curated navigation key set (`Alt+G` go to definition,
  `Alt+O` toggle header/code, `Alt+←/→` navigate back/forward, …) applied only
  **with your consent**, merged next to the VS defaults — never replacing them.
  Original bindings are backed up on first touch; **Restore** brings them back exactly.
- **My Keys**: bind any of Visual Studio's ~10,000 commands to your own shortcut —
  search the command, capture the key in a dialog (even combinations VS already
  uses), pick Global or Text Editor scope, Apply. Conflict scanning included.

## Enhanced syntax coloring

Presets that give fields, parameters, statics and macros distinct colors
(dark & light variants), or build your own per-item scheme with a color picker.
Works on Visual Studio 2022 and 2026 (including the 2026 C++ editor rework).

## Trust

- Every destructive operation (key bindings, colors) snapshots the original first — restore anytime
- All data stays local in `%APPDATA%\VsMasterKey` — nothing is transmitted
- Every editor decoration can be turned off

## Feedback

Bug reports and feature requests:
[Issues](https://github.com/BaeBulDuGi/molekey/issues). Release history:
[CHANGELOG](CHANGELOG.md).

---

*MoleKey (formerly VsMasterKey) is an independent extension and is not
affiliated with or endorsed by the vendors of any other product.*
