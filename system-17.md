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
| `base-05` | `#2c2c2c` | Element backgrounds, highlighted lines                                            |
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

| Name           | Hex           | Usage                                                             |
|----------------|---------------|-------------------------------------------------------------------|
| `accent`       | `#d97c2b`     | Primary accent — cursor, focused borders, active badges, player 1 |
| `accent-link`  | `#e8891a`     | Hovered links                                                     |
| `accent-glow`  | `#d97c2b33`   | Selection highlight, search match background (20% opacity)        |
| `accent-match` | `#d97c2b66`   | Active search match (40% opacity)                                 |

---

## Syntax Colors

The syntax palette is designed as two groups: a **warm ramp** for language-owned tokens, and a **cool pair** for data and structure.

### Warm Ramp — Language Tokens

These belong to things the *language itself* defines. They form a fire gradient from red-orange to amber-yellow.

| Name          | Hex       | Tokens                                                                                                                           |
|---------------|-----------|----------------------------------------------------------------------------------------------------------------------------------|
| `syn-red`     | `#f08090` | `error`, `deleted`, `diff.minus` — diagnostics and deletions                                                                     |
| `syn-preproc` | `#e8623a` | `preproc` — preprocessor directives (`#ifdef`, `#pragma`)                                                                        |
| `syn-orange`  | `#ff9668` | `keyword`, `keyword.control`, `boolean`, `number`, `type.builtin`, `label`, `function.builtin` — everything the language *owns*  |
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

| Name             | Hex       | Tokens                                                                                        |
|------------------|-----------|-----------------------------------------------------------------------------------------------|
| `syn-embedded`   | `#dce0e5` | `embedded` — embedded language content (e.g. JS inside HTML)                                  |
| `syn-predictive` | `#5a6a87` | `predictive` — ghost text from autocomplete/copilot suggestions. Italic, stays out of the way |

### Accent in Syntax — Markup and UI

These appear in markup, CSS, and prose contexts rather than general code.

| Name              | Hex       | Tokens                                                                          |
|-------------------|-----------|---------------------------------------------------------------------------------|
| `syn-blue`        | `#74ade8` | `tag`, `emphasis`, `selector.pseudo`, `link_text`, `link_uri`, `variant`        |
| `syn-strong`      | `#bf956a` | `emphasis.strong` — bold markup. Weight 700                                     |
| `syn-rose`        | `#d07277` | `variable.special`, `title`, `punctuation.list_marker`, `punctuation.markup`    |
| `syn-rose-dim`    | `#b1574b` | `punctuation.special`                                                           |
| `syn-gold`        | `#dfc184` | `selector`                                                                      |

### Comments — Three Tiers

Comments use a tiered sage-green system. The dimmer the tone, the less important.

| Name              | Hex       | Usage                                                            |
|-------------------|-----------|------------------------------------------------------------------|
| `comment-regular` | `#4e7a62` | `// regular comments` — low visual weight, stays out of the way  |
| `comment-doc`     | `#72b396` | `/// doc comments` — elevated, italic, clearly distinct          |

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

All diagnostic backgrounds use the same base color at `1a` hex opacity (~10%) so they don't overpower the editor. Borders use a darker solid tint.

| Severity | Foreground | Background    | Border        |
|----------|------------|---------------|---------------|
| Error    | `#f08090`  | `#f080901a`   | `#3a1820`     |
| Warning  | `#c8993a`  | `#c8993a44`   | `#c8993a66`   |
| Info     | `#74ade8`  | `#74ade81a`   | `#1a2e3a`     |
| Hint     | `#7a6a55`  | `#1e1b16`     | `#2e2518`     |

---

## Version Control Colors

| State           | Color         | Word-level alpha | Notes         |
|-----------------|---------------|------------------|---------------|
| Added           | `#48b06f`     | `59` (35%)       | Green family  |
| Modified        | `#d97c2b`     | —                | Accent orange |
| Deleted         | `#f08090`     | `99` (60%)       | Red family    |
| Conflict ours   | `#48b06f1a`   | —                | Green tint    |
| Conflict theirs | `#74ade81a`   | —                | Blue tint     |

---

## UI Details

Editor-level tokens for interactive highlights, selection, scrollbar, indent guides, and multiplayer cursors. These are needed when porting to any editor that exposes fine-grained UI color slots.

### Editor

| Element                        | Color           | Notes                                       |
|--------------------------------|-----------------|---------------------------------------------|
| Selection background           | `#d97c2b3d`     | Accent at ~24% opacity                      |
| Active line background         | `#1e1e1ebf`     | Near-black at ~75% opacity                  |
| Highlighted line background    | `#2c2c2c`       | `base-05`                                   |
| Line number                    | `#444444`       | `text-invisible`                            |
| Active line number             | `#8a8a8a`       | `text-muted`                                |
| Hovered line number            | `#6a6a6a`       | `text-subtle`                               |
| Invisible characters           | `#333333`       |                                             |
| Indent guide                   | `#2a2a2a`       |                                             |
| Indent guide (active)          | `#424242`       |                                             |
| Wrap guide                     | `#2828280d`     | `base-04` at ~5% opacity                    |
| Wrap guide (active)            | `#3636361a`     | `base-06` at ~10% opacity                   |

### Document Highlights

| Element                 | Color         | Notes                        |
|-------------------------|---------------|------------------------------|
| Read highlight          | `#d97c2b1a`   | Accent at ~10% — subtle glow |
| Write highlight         | `#d97c2b33`   | Accent at 20% — stronger     |
| Bracket match           | `#363636`     | `base-06` — solid background |

### Search

| Element              | Color         | Notes              |
|----------------------|---------------|--------------------|
| Match background     | `#d97c2b33`   | Accent at 20%      |
| Active match         | `#d97c2b66`   | Accent at 40%      |

### Scrollbar

| Element              | Color         | Notes                          |
|----------------------|---------------|--------------------------------|
| Thumb background     | `#ffffff18`   | White at ~9% — barely visible  |
| Thumb hover          | `#ffffff28`   | White at ~16%                  |
| Thumb active         | `#ffffff38`   | White at ~22%                  |
| Thumb border         | `#ffffff10`   | White at ~6%                   |
| Track background     | `transparent` |                                |
| Track border         | `#1c1c1c`     | `base-02`                      |

### Player Cursors (Multiplayer)

Eight player slots. Player 1 uses the accent color; the rest are drawn from the syntax palette to avoid introducing new hues.

| Player | Cursor/Background  | Selection     | Source color   |
|--------|--------------------|--------------:|----------------|
| 1      | `#d97c2b`          | `#d97c2b3d`   | `accent`       |
| 2      | `#f08090`          | `#f080903d`   | `syn-red`      |
| 3      | `#64d1a9`          | `#64d1a93d`   | `syn-teal`     |
| 4      | `#74ade8`          | `#74ade83d`   | `syn-blue`     |
| 5      | `#c586c0`          | `#c586c03d`   | ANSI magenta   |
| 6      | `#e8cc8c`          | `#e8cc8c3d`   | `syn-yellow`   |
| 7      | `#48b06f`          | `#48b06f3d`   | `syn-green-dim`|
| 8      | `#d07277`          | `#d072773d`   | `syn-rose`     |

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

When porting system-17 to a new app:

1. **Map surfaces by depth.** Find the app's background layer hierarchy and assign `base-00` through `base-07` from deepest to shallowest. If the app only has one background level, use `base-02`.
2. **One accent.** Use `#d97c2b` for every interactive highlight — focused input borders, selected items, active tabs, cursor, progress bars. If the app has a "primary color" setting, that's the one.
3. **Syntax maps.** The token names above (`keyword`, `string`, `type`, etc.) are Tree-sitter/LSP standard names. Most editors expose these. Match them to the colors in the Syntax section above.
4. **Diagnostic colors are semantic.** Red = broken, amber = suspicious, blue = informational. Don't swap them.
5. **Don't invent new accent colors.** If you need a second accent for a specific app context, pull from `syn-teal` (`#64d1a9`) as a secondary. It's the coolest color in the palette and contrasts cleanly with orange.
6. **Alpha values.** When an app supports RGBA, use the alpha variants for backgrounds (selection, search match, diagnostic backgrounds). When it only supports hex, use the pre-blended solid equivalents listed below.
7. **UI details.** Consult the UI Details section for editor-specific tokens (scrollbar, indent guides, selections, player cursors). These vary by editor but the values above cover the common slots.

### Pre-blended Solids (for apps without alpha support)

These are the alpha colors pre-composited over `base-00` (`#141414`):

| Alpha color   | Solid equivalent | Usage                             |
|---------------|------------------|-----------------------------------|
| `#d97c2b1a`   | `#281f16`        | Document highlight (read)         |
| `#d97c2b33`   | `#3b2919`        | Search match, accent glow         |
| `#d97c2b3d`   | `#432d1a`        | Editor selection                  |
| `#d97c2b66`   | `#633e1d`        | Active search match               |
| `#f080901a`   | `#2a1f21`        | Error background                  |
| `#c8993a44`   | `#44371e`        | Warning background                |
| `#48b06f1a`   | `#19241d`        | Added / conflict ours             |
| `#74ade81a`   | `#1e242a`        | Info background / conflict theirs |
| `#1e1e1ebf`   | `#1b1b1b`        | Active line                       |

---

## Quick Reference Card

```
SURFACES                        SYNTAX — WARM
#141414  base-00  deepest       #f08090  syn-red       error, deleted
#181818  base-01  panel         #e8623a  syn-preproc   preprocessor
#1c1c1c  base-02  chrome        #ff9668  syn-orange    keyword, number, builtin
#232323  base-03  elevated      #c8993a  syn-amber     warning, modified
#282828  base-04  border        #e8cc8c  syn-yellow    function, constructor
#2c2c2c  base-05  element bg
#363636  base-06  hover         SYNTAX — COOL
#404040  base-07  active        #64d1a9  syn-teal      type, enum, namespace
                                #63d68a  syn-green     string
TEXT                            #48b06f  syn-green-dim escape, special, diff+
#f2f2f2  text-primary           #80edc5  syn-mint      regex
#c0c0c0  text-icon
#8a8a8a  text-muted             NEUTRAL
#6a6a6a  text-subtle            #cbcccd  syn-gray-hi   variable, constant, operator
#555555  text-faint             #9a9a9a  syn-gray-mid  bracket
#4a4a4a  text-ghost             #7a7a7a  syn-gray-lo   punctuation, delimiter
#444444  text-invisible
                                MARKUP
ACCENT                          #74ade8  syn-blue      tag, emphasis, link, variant
#d97c2b  accent                 #bf956a  syn-strong    emphasis.strong
#e8891a  accent-link            #d07277  syn-rose      variable.special, title
#d97c2b33  accent-glow (20%)    #b1574b  syn-rose-dim  punctuation.special
#d97c2b66  accent-match (40%)   #dfc184  syn-gold      selector

COMMENTS                        EMBEDDED / PREDICTIVE
#4e7a62  comment-regular        #dce0e5  syn-embedded
#72b396  comment-doc            #5a6a87  syn-predictive

INLAY HINTS                     DIAGNOSTICS (foreground)
#7a6a55  hint                   #f08090  error
#1e1b16  hint-bg                #c8993a  warning
                                #74ade8  info
TASK TAGS (in comments)         #7a6a55  hint
#e8cc8c  TODO  (syn-yellow)
#ff9668  FIXME (syn-orange)     VERSION CONTROL
#f08090  BUG   (syn-red)        #48b06f  added
#64d1a9  NOTE  (syn-teal)       #d97c2b  modified
                                #f08090  deleted
ANSI (normal)
#1c1c1c  black    #74ade8  blue
#f08090  red      #c586c0  magenta
#48b06f  green    #64d1a9  cyan
#e8cc8c  yellow   #c0c0c0  white
```
