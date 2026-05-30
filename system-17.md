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

| Name       | Hex       | Usage |
|------------|-----------|-------|
| `base-00`  | `#141414` | Editor background, title bar, status bar, terminal background — the deepest layer |
| `base-01`  | `#181818` | Panel background |
| `base-02`  | `#1c1c1c` | Main UI chrome, toolbar, active tab background, surface |
| `base-03`  | `#1f1f1f` | Elevated surfaces (dropdowns, popovers) |
| `base-04`  | `#222222` | Borders, dividers |
| `base-05`  | `#252525` | Element backgrounds, highlighted lines |
| `base-06`  | `#2e2e2e` | Hover states, selected elements, active line |
| `base-07`  | `#353535` | Active/pressed states |

### Text

| Name            | Hex       | Usage |
|-----------------|-----------|-------|
| `text-primary`  | `#f2f2f2` | Main text, editor foreground |
| `text-icon`     | `#c0c0c0` | Icons |
| `text-muted`    | `#8a8a8a` | Secondary text, active line numbers, muted UI |
| `text-subtle`   | `#6a6a6a` | Hovered line numbers, icon muted |
| `text-faint`    | `#555555` | Placeholder text, disabled icons |
| `text-ghost`    | `#4a4a4a` | Disabled text |
| `text-invisible`| `#444444` | Disabled icons (darkest readable) |

### Accent — Orange

The single UI accent. Used for focus, cursor, selection glow, search highlights, active borders.  
**Never use for syntax tokens.** Orange in the syntax space belongs to keywords only.

| Name          | Hex       | Usage |
|---------------|-----------|-------|
| `accent`      | `#d97c2b` | Primary accent — cursor, focused borders, active badges, player 1 |
| `accent-link` | `#e8891a` | Hovered links |
| `accent-glow` | `#d97c2b33` | Selection highlight, search match background (12% opacity) |
| `accent-match`| `#d97c2b66` | Active search match (40% opacity) |

---

## Syntax Colors

The syntax palette is designed as two groups: a **warm ramp** for language-owned tokens, and a **cool pair** for data and structure.

### Warm Ramp — Language Tokens

These belong to things the *language itself* defines. They form a fire gradient from red-orange to amber-yellow.

| Name          | Hex       | Tokens |
|---------------|-----------|--------|
| `syn-red`     | `#f08090` | `error`, `deleted`, `diff.minus` — diagnostics and deletions |
| `syn-preproc` | `#e8623a` | `preproc` — preprocessor directives (`#ifdef`, `#pragma`) |
| `syn-orange`  | `#ff9668` | `keyword`, `keyword.control`, `boolean`, `number`, `type.builtin`, `label`, `function.builtin` — everything the language *owns* |
| `syn-amber`   | `#c8993a` | `warning`, `modified` — diagnostic warnings, modified file indicators |
| `syn-yellow`  | `#e8cc8c` | `function`, `function.method`, `function.special.definition`, `constructor` — things *you* define and call |

> **Gradient logic:** preproc → orange → yellow reads as: compiler-level → language-level → user-level. Warmer = closer to the metal.

### Cool Pair — Data and Structure

These belong to data containers and structural/categorical tokens.

| Name        | Hex       | Tokens |
|-------------|-----------|--------|
| `syn-teal`  | `#64d1a9` | `type`, `enum`, `namespace` — structural/categorical tokens |
| `syn-green` | `#63d68a` | `string` — string literals |
| `syn-green-dim` | `#48b06f` | `string.escape`, `string.special`, `string.special.symbol`, `diff.plus` — string variants and additions |
| `syn-mint`  | `#80edc5` | `string.regex` — regex patterns |

### Neutral — Variables and Punctuation

These are the workhorse tokens. Low chroma, high readability.

| Name           | Hex       | Tokens |
|----------------|-----------|--------|
| `syn-gray-hi`  | `#cbcccd` | `variable`, `constant`, `property`, `attribute`, `operator`, `text.literal` — neutral code body |
| `syn-gray-mid` | `#9a9aaa` | `punctuation.bracket` |
| `syn-gray-lo`  | `#7a7a8a` | `punctuation`, `punctuation.delimiter` |

### Accent in Syntax — Markup and UI

These appear in markup, CSS, and prose contexts rather than general code.

| Name          | Hex       | Tokens |
|---------------|-----------|--------|
| `syn-blue`    | `#74ade8` | `tag`, `emphasis`, `selector.pseudo`, `link_text`, `link_uri` |
| `syn-rose`    | `#d07277` | `variable.special`, `title`, `punctuation.list_marker`, `punctuation.markup` |
| `syn-rose-dim`| `#b1574b` | `punctuation.special` |
| `syn-gold`    | `#dfc184` | `selector` |

### Comments — Three Tiers

Comments use a tiered green system. The dimmer the green, the less important.

| Name             | Hex       | Usage |
|------------------|-----------|-------|
| `comment-regular`| `#4a7a52` | `// regular comments` — low visual weight, stays out of the way |
| `comment-doc`    | `#72b38a` | `/// doc comments` — elevated, italic, clearly distinct |

> For TODO/FIXME/BUG/NOTE highlights: use an editor-level task highlighting layer on top of `comment-regular`. Suggested colors: TODO → `syn-yellow`, FIXME → `syn-orange`, BUG → `syn-red`, NOTE → `syn-teal`.

### Inlay Hints

| Name           | Hex       | Usage |
|----------------|-----------|-------|
| `hint`         | `#7a6a55` | Inlay hint text — warm brown-gray, warm enough to feel intentional but dim enough not to compete with real code |
| `hint-bg`      | `#1e1b16` | Inlay hint background (when enabled) |

---

## Diagnostic Colors

All diagnostic backgrounds use the same base color at `1a` hex opacity (10%) so they don't overpower the editor. Borders use a darker solid tint.

| Severity | Foreground | Background | Border |
|----------|------------|------------|--------|
| Error    | `#f08090`  | `#f080901a` | `#3a1820` |
| Warning  | `#c8993a`  | `#c8993a44` | `#c8993a66` |
| Info     | `#74ade8`  | `#74ade81a` | `#1a2e3a` |
| Hint     | `#7a6a55`  | `#1e1b16`   | `#2e2518` |

---

## Version Control Colors

| State    | Color     | Word-level alpha | Notes |
|----------|-----------|-----------------|-------|
| Added    | `#48b06f` | `59` (35%)      | Green family |
| Modified | `#d97c2b` | —               | Accent orange |
| Deleted  | `#f08090` | `99` (60%)      | Red family |
| Conflict ours   | `#48b06f1a` | — | Green tint |
| Conflict theirs | `#74ade81a` | — | Blue tint |

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

### Pre-blended Solids (for apps without alpha support)

These are the alpha colors pre-composited over `base-00` (`#141414`):

| Alpha color   | Solid equivalent |
|---------------|-----------------|
| `#d97c2b33`   | `#1e1a15`       |
| `#d97c2b66`   | `#281f16`       |
| `#f080901a`   | `#1e1516`       |
| `#c8993a44`   | `#2a2118`       |
| `#48b06f1a`   | `#181e19`       |
| `#74ade81a`   | `#181d22`       |

---

## Quick Reference Card

```
SURFACES          SYNTAX — WARM          SYNTAX — COOL
#141414  base-00  #f08090  red           #64d1a9  teal
#181818  base-01  #e8623a  preproc       #63d68a  green
#1c1c1c  base-02  #ff9668  orange        #48b06f  green-dim
#252525  base-05  #c8993a  amber         #80edc5  mint
#2e2e2e  base-06  #e8cc8c  yellow
                                          NEUTRAL
TEXT              COMMENTS               #cbcccd  gray-hi
#f2f2f2  primary  #4a7a52  regular       #9a9aaa  gray-mid
#8a8a8a  muted    #72b38a  doc           #7a7a8a  gray-lo
#555555  faint
                  ACCENT                 MARKUP
                  #d97c2b  orange        #74ade8  blue
                                         #d07277  rose
```
