# system-17

**A dark, monochrome-base theme with a warm orange accent.**

---

## Design Philosophy

system-17 is built on three principles:

1. **Near-zero chroma backgrounds.** All surface and UI colors are pure achromatic grays. No blue-tinted or warm-tinted dark backgrounds. The editor feels like a dark room, not a tinted one.
2. **One accent color, used with discipline.** Orange (`#d97c2b`) is the single UI accent — used for focus rings, cursors, active borders, and search highlights. It never appears in syntax highlighting.
3. **Syntax as a fire gradient.** The five syntax hues form a warm ramp — red → orange → amber → yellow — with teal and green as the cool counterweights for types and strings. Every color sits at roughly the same perceptual luminance so no token dominates.

---

## Palette

### Surfaces (Backgrounds)

These are achromatic. No tint of any kind.

| Name      | Hex       | Usage                                                                             |
|-----------|-----------|-----------------------------------------------------------------------------------|
| `base-00` | `#141414` | Editor background, title bar, status bar, terminal background — the deepest layer |
| `base-01` | `#181818` | Panel background                                                                  |
| `base-02` | `#1c1c1c` | Main UI chrome, toolbar, active tab background, surface                           |
| `base-03` | `#232323` | Elevated surfaces (dropdowns, popovers)                                           |
| `base-04` | `#282828` | Borders, dividers                                                                 |
| `base-05` | `#2c2c2c` | Element backgrounds, highlighted lines, active menu items                         |
| `base-06` | `#363636` | Hover states, selected elements                                                   |
| `base-07` | `#404040` | Active/pressed states                                                             |

### Text

| Name             | Hex       | Usage                                         |
|------------------|-----------|-----------------------------------------------|
| `text-primary`   | `#f2f2f2` | Main text, editor foreground                  |
| `text-icon`      | `#c0c0c0` | Icons                                         |
| `text-muted`     | `#8a8a8a` | Secondary text, active line numbers, muted UI |
| `text-subtle`    | `#6a6a6a` | Hovered line numbers, icon muted              |
| `text-faint`     | `#555555` | Placeholder text, disabled icons              |
| `text-ghost`     | `#4a4a4a` | Disabled text                                 |
| `text-invisible` | `#444444` | Disabled icons (darkest readable)             |

### Accent — Orange

The single UI accent. Used for focus, cursor, selection glow, search highlights, active borders.
**Never use for syntax tokens.** Orange in the syntax space belongs to keywords only.

| Name           | Hex       | Usage                                                             |
|----------------|-----------|-------------------------------------------------------------------|
| `accent`       | `#d97c2b` | Primary accent — cursor, focused borders, active badges, player 1 |
| `accent-hover` | `#e8891a` | Hovered links and accent elements                                 |

---

## Syntax Colors

The syntax palette is designed as two groups: a **warm ramp** for language-owned tokens, and a **cool pair** for data and structure.

### Warm Ramp — Language Tokens

These belong to things the *language itself* defines. They form a fire gradient from red-orange to amber-yellow.

| Name          | Hex       | Tokens                                                                                                                           |
|---------------|-----------|----------------------------------------------------------------------------------------------------------------------------------|
| `syn-red`     | `#f08090` | `error`, `deleted`, `diff.minus` — diagnostics and deletions                                                                     |
| `syn-preproc` | `#e8623a` | `preproc` — preprocessor directives (`#ifdef`, `#pragma`)                                                                        |
| `syn-orange`  | `#ff9668` | `keyword`, `keyword.control`, `boolean`, `number`, `type.builtin`, `label`, `function.builtin` — everything the language *owns* |
| `syn-amber`   | `#c8993a` | `warning`, `modified` — diagnostic warnings, modified file indicators                                                            |
| `syn-yellow`  | `#e8cc8c` | `function`, `function.method`, `function.special.definition`, `constructor` — things *you* define and call                       |

> **Gradient logic:** preproc → orange → yellow reads as: compiler-level → language-level → user-level. Warmer = closer to the metal.

### Cool Pair — Data and Structure

These belong to data containers and structural/categorical tokens.

| Name            | Hex       | Tokens                                                                                                  |
|-----------------|-----------|---------------------------------------------------------------------------------------------------------|
| `syn-teal`      | `#64d1a9` | `type`, `enum`, `namespace` — structural/categorical tokens                                             |
| `syn-green`     | `#63d68a` | `string` — string literals                                                                              |
| `syn-green-dim` | `#48b06f` | `string.escape`, `string.special`, `string.special.symbol`, `diff.plus` — string variants and additions |
| `syn-mint`      | `#80edc5` | `string.regex` — regex patterns                                                                         |

### Neutral — Variables and Punctuation

These are the workhorse tokens. Low chroma, high readability. All values are true achromatic grays.

| Name           | Hex       | Tokens                                                                                          |
|----------------|-----------|-------------------------------------------------------------------------------------------------|
| `syn-gray-hi`  | `#cbcccd` | `variable`, `constant`, `property`, `attribute`, `operator`, `text.literal` — neutral code body |
| `syn-gray-mid` | `#9a9a9a` | `punctuation.bracket`                                                                           |
| `syn-gray-lo`  | `#7a7a7a` | `punctuation`, `punctuation.delimiter`                                                          |

### Embedded and Predictive

| Name             | Hex       | Tokens                                                                          |
|------------------|-----------|---------------------------------------------------------------------------------|
| `syn-embedded`   | `#dce0e5` | `embedded` — embedded language content (e.g. JS inside HTML)                    |
| `syn-predictive` | `#5a6a87` | `predictive` — ghost text from autocomplete/copilot suggestions. Low prominence |

### Accent in Syntax — Markup and UI

These appear in markup, CSS, and prose contexts rather than general code.

| Name           | Hex       | Tokens                                                                          |
|----------------|-----------|---------------------------------------------------------------------------------|
| `syn-blue`     | `#74ade8` | `tag`, `emphasis`, `selector.pseudo`, `link_text`, `link_uri`, `variant`        |
| `syn-strong`   | `#bf956a` | `emphasis.strong` — bold markup. Weight 700                                     |
| `syn-rose`     | `#d07277` | `variable.special`, `title`, `punctuation.list_marker`, `punctuation.markup`    |
| `syn-rose-dim` | `#b1574b` | `punctuation.special`                                                           |
| `syn-gold`     | `#dfc184` | `selector`                                                                      |

### Comments — Three Tiers

Comments use a tiered sage-green system. The dimmer the tone, the less important.

| Name              | Hex       | Usage                                                            |
|-------------------|-----------|------------------------------------------------------------------|
| `comment-regular` | `#4e7a62` | `// regular comments` — low visual weight, stays out of the way  |
| `comment-doc`     | `#72b396` | `/// doc comments` — elevated, clearly distinct                  |

The third tier is **task-tag highlighting** — TODO, FIXME, BUG, and NOTE keywords inside comments. These use existing syntax colors applied as an editor-level highlight layer on top of `comment-regular`:

| Tag     | Highlight color | Source token   |
|---------|-----------------|----------------|
| `TODO`  | `#e8cc8c`       | `syn-yellow`   |
| `FIXME` | `#ff9668`       | `syn-orange`   |
| `BUG`   | `#f08090`       | `syn-red`      |
| `NOTE`  | `#64d1a9`       | `syn-teal`     |

> Comment hue is shifted toward sage (blue-green) to separate from string green (`#63d68a`). Both are green-family but occupy different hue angles.

### Inlay Hints

| Name      | Hex       | Usage                                                                                                           |
|-----------|-----------|-----------------------------------------------------------------------------------------------------------------|
| `hint`    | `#7a6a55` | Inlay hint text — warm brown-gray, warm enough to feel intentional but dim enough not to compete with real code |
| `hint-bg` | `#1e1b16` | Inlay hint background (when enabled)                                                                            |

---

## Diagnostic Colors

All diagnostic backgrounds are pre-blended against `base-00` (`#141414`) to ensure solid, bug-free rendering across all terminals and platforms. 

| Severity | Foreground | Solid Background |
|----------|------------|------------------|
| Error    | `#f08090`  | `#2a1f20`        |
| Warning  | `#c8993a`  | `#44371e`        |
| Info     | `#74ade8`  | `#1e2329`        |
| Hint     | `#7a6a55`  | `#1e1b16`        |

---

## Version Control Colors

| State           | Solid Color | Notes                             |
|-----------------|-------------|-----------------------------------|
| Added           | `#48b06f`   | Green family                      |
| Modified        | `#d97c2b`   | Accent orange                     |
| Deleted         | `#f08090`   | Red family                        |
| Conflict ours   | `#19241d`   | Green tint blended over `base-00` |
| Conflict theirs | `#1e2329`   | Blue tint blended over `base-00`  |

---

## UI Details

Editor-level tokens for interactive highlights, selection, scrollbar, indent guides, and multiplayer cursors. **All values are solid hex codes.**

### Editor

| Element                        | Hex       | Notes                                             |
|--------------------------------|-----------|---------------------------------------------------|
| Selection background           | `#432d1a` | Pre-blended accent tint                           |
| Selection background (primary) | `#543a21` | Pre-blended stronger accent tint                  |
| Active line background         | `#212121` | Solid equivalent to avoid transparency overlap    |
| Highlighted line background    | `#2c2c2c` | `base-05`                                         |
| Line number                    | `#444444` | `text-invisible`                                  |
| Active line number             | `#8a8a8a` | `text-muted`                                      |
| Hovered line number            | `#6a6a6a` | `text-subtle`                                     |
| Invisible characters           | `#333333` |                                                   |
| Indent guide                   | `#2a2a2a` |                                                   |
| Indent guide (active)          | `#424242` |                                                   |
| Active menu item / popover     | `#2c2c2c` | `base-05` — keeps popovers subtle                 |

### Document Highlights & Search

| Element              | Hex       | Notes                          |
|----------------------|-----------|--------------------------------|
| Document read        | `#281f16` | Solid subtle glow              |
| Document write       | `#3b2919` | Solid stronger glow            |
| Bracket match        | `#363636` | `base-06` — solid background   |
| Search match bg      | `#3b2919` | Pre-blended accent tint        |
| Search active match  | `#633e1d` | Pre-blended strong accent tint |

### Scrollbar

| Element              | Hex           | Notes     |
|----------------------|---------------|-----------|
| Thumb background     | `#2c2c2c`     | `base-05` |
| Thumb hover          | `#363636`     | `base-06` |
| Thumb active         | `#404040`     | `base-07` |
| Track background     | `transparent` |           |
| Track border         | `#1c1c1c`     | `base-02` |

### Player Cursors (Multiplayer)

Eight player slots. Player 1 uses the accent color; the rest are drawn from the syntax palette to avoid introducing new hues.

| Player | Cursor Hex | Solid Selection Hex | Source color    |
|--------|------------|---------------------|-----------------|
| 1      | `#d97c2b`  | `#432d1a`           | `accent`        |
| 2      | `#f08090`  | `#3b2126`           | `syn-red`       |
| 3      | `#64d1a9`  | `#213129`           | `syn-teal`      |
| 4      | `#74ade8`  | `#242f3a`           | `syn-blue`      |
| 5      | `#c586c0`  | `#322532`           | ANSI magenta    |
| 6      | `#e8cc8c`  | `#3c3525`           | `syn-yellow`    |
| 7      | `#48b06f`  | `#1e2f23`           | `syn-green-dim` |
| 8      | `#d07277`  | `#352023`           | `syn-rose`      |

---

## Terminal ANSI Palette

| ANSI    | Dim       | Normal    | Bright    |
|---------|-----------|-----------|-----------|
| Black   | `#141414` | `#1c1c1c` | `#555555` |
| Red     | `#b06070` | `#f08090` | `#f598a4` |
| Green   | `#2d7a4a` | `#48b06f` | `#63d68a` |
| Yellow  | `#a08840` | `#e8cc8c` | `#f0d49a` |
| Blue    | `#4a7aa0` | `#74ade8` | `#90c8ff` |
| Magenta | `#885080` | `#c586c0` | `#e0a0da` |
| Cyan    | `#3a9070` | `#64d1a9` | `#80edc5` |
| White   | `#888888` | `#c0c0c0` | `#f2f2f2` |

---

## Porting Guidelines

1. **Map surfaces by depth.** Find the app's background layer hierarchy and assign `base-00` through `base-07` from deepest to shallowest.
2. **One accent.** Use `#d97c2b` for every interactive highlight.
3. **Syntax maps.** Match token names to the colors in the Syntax section.
4. **Diagnostic colors are semantic.** Red = broken, amber = suspicious, blue = informational.
5. **Strictly 6-digit Hexes.** Do NOT use 8-digit RGBA hex codes. 
6. **No Italics.** Differentiate tokens purely through color and syntax weight.
