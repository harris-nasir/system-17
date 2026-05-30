<p align="center">
  <img src="https://github.com/harris-nasir/system-17/raw/main/assets/banner.png" alt="system-17" />
</p>

<p align="center">
  <strong>A dark, monochrome-base theme with a warm orange accent.</strong>
</p>

<p align="center">
  <a href="https://github.com/harris-nasir/system-17/blob/main/system-17.md">Spec</a> ·
  <a href="#implementation">Implementation</a> ·
  <a href="#palette">Palette</a> ·
  <a href="#porting">Porting</a>
</p>

---

## Preview

<p align="center">
  <img src="https://github.com/harris-nasir/system-17/raw/main/assets/preview-zed.png" alt="system-17 in Zed" width="900" />
</p>

## Design

system-17 is built on three rules:

- **Achromatic base.** Every surface uses a pure, neutral gray base. We avoid transparent or alpha-based overlays in favor of pre-blended solid colors to ensure consistent performance and appearance across all terminals and editors.
- **One accent, used with discipline.** Orange (`#d97c2b`) is the single UI accent — cursor, focus rings, active borders, search highlights. It never bleeds into syntax.
- **Syntax as a fire gradient.** Language tokens follow a warm ramp — red → orange → amber → yellow — with teal and green as cool counterweights for types and strings. Hotter = closer to the metal.

## Palette

### Surfaces

| | `base-00` | `base-01` | `base-02` | `base-03` | `base-04` | `base-05` | `base-06` | `base-07` |
|---|---|---|---|---|---|---|---|---|
| | ![#141414](https://placehold.co/32/141414/141414) | ![#181818](https://placehold.co/32/181818/181818) | ![#1c1c1c](https://placehold.co/32/1c1c1c/1c1c1c) | ![#232323](https://placehold.co/32/232323/232323) | ![#282828](https://placehold.co/32/282828/282828) | ![#2c2c2c](https://placehold.co/32/2c2c2c/2c2c2c) | ![#363636](https://placehold.co/32/363636/363636) | ![#404040](https://placehold.co/32/404040/404040) |
| | `#141414` | `#181818` | `#1c1c1c` | `#232323` | `#282828` | `#2c2c2c` | `#363636` | `#404040` |

### Syntax — Warm Ramp

| | `red` | `preproc` | `orange` | `amber` | `yellow` |
|---|---|---|---|---|---|
| | ![#f08090](https://placehold.co/32/f08090/f08090) | ![#e8623a](https://placehold.co/32/e8623a/e8623a) | ![#ff9668](https://placehold.co/32/ff9668/ff9668) | ![#c8993a](https://placehold.co/32/c8993a/c8993a) | ![#e8cc8c](https://placehold.co/32/e8cc8c/e8cc8c) |
| | `#f08090` | `#e8623a` | `#ff9668` | `#c8993a` | `#e8cc8c` |

### Syntax — Cool Pair

| | `teal` | `green` | `green-dim` | `mint` |
|---|---|---|---|---|
| | ![#64d1a9](https://placehold.co/32/64d1a9/64d1a9) | ![#63d68a](https://placehold.co/32/63d68a/63d68a) | ![#48b06f](https://placehold.co/32/48b06f/48b06f) | ![#80edc5](https://placehold.co/32/80edc5/80edc5) |
| | `#64d1a9` | `#63d68a` | `#48b06f` | `#80edc5` |

### Accent & Markup

| | `accent` | `blue` | `rose` | `gold` | `strong` |
|---|---|---|---|---|---|
| | ![#d97c2b](https://placehold.co/32/d97c2b/d97c2b) | ![#74ade8](https://placehold.co/32/74ade8/74ade8) | ![#d07277](https://placehold.co/32/d07277/d07277) | ![#dfc184](https://placehold.co/32/dfc184/dfc184) | ![#bf956a](https://placehold.co/32/bf956a/bf956a) |
| | `#d97c2b` | `#74ade8` | `#d07277` | `#dfc184` | `#bf956a` |

> Full palette with token mappings, ANSI colors, diagnostics, and UI details → **[system-17.md](system-17.md)**

## Implementation

system-17 is spec-first. Please refer to the [theme spec](system-17-spec.md) for detailed implementation instructions, including specific surface mappings, syntax token tables, and our pre-blended solid color guidelines for every editor.

## Porting

When bringing system-17 to a new app:

1. **Map surfaces by depth** : `base-00` (deepest) through `base-07` (shallowest).
2. **One accent** : `#d97c2b` for every interactive element.
3. **Match syntax tokens** : the spec uses Tree-sitter/LSP standard names.
4. **Don't invent new accents** : use `syn-teal` (`#64d1a9`) for secondary UI elements.
5. **Avoid Alpha/Transparency** : Use the pre-blended solid hex codes provided in the [spec](system-17-spec.md) to guarantee color accuracy across all platforms.

## License

[MIT](LICENSE) — © 2026 Harris N.
