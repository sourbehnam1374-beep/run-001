# Iconography

SHIVA does **not** ship an icon font, **not** a sprite sheet, and **not** any CDN-linked icon library. Every icon is **inline SVG**, written by hand against a fixed grammar, kept under a few dozen total. There are three reasons this is a constraint, not a preference:

1. **No network calls.** Capsules must be self-contained and offline-viewable.
2. **iOS-safe.** Icon fonts and external SVG sprites have rendering quirks on iOS WebKit; inline SVG avoids them entirely.
3. **Semantic, not decorative.** Each icon has to declare what it *is* — a string, a rope, an anchor, a ledger. An icon font's glyphs are anonymous; inline SVG keeps the meaning in the markup.

## The icon grammar

| Spec | Value |
|---|---|
| Canvas | `viewBox="0 0 24 24"` (UI icons) · `viewBox="0 0 64 64"` (logo) · `viewBox="0 0 120 24"` (signature) |
| Stroke weight | `1.6` (default) · `1.4` (secondary detail) · `1.8–2.0` (bold action like arrows / check) |
| Fill | `none` for outlines; `currentColor` for filled accents. Never a hex literal — color comes from the parent. |
| Linecap / linejoin | `round` |
| Stroke | `currentColor` — the icon inherits the surrounding text color. To tint, set `color: var(--accent)` on the parent. |
| `role` | `"img"` always |
| `aria-label` | always present, in lowercase |
| Animation | A small icon may opt into one of the canonical `.anim-*` classes (pulse for active, jitter for instability). Do not invent new motion. |

The conic-disc logo is the only icon that uses fixed brand hues rather than `currentColor`.

## The icon set

All files live in [`assets/`](./assets/). They split into three tiers:

### Brand atoms
- `logo-conic-disc.svg` — the wordmark anchor. 64×64. Five-wedge conic in `--c-data → --c-sci → --c-code → --c-img → --c-sec`.
- `signature-glyph.svg` — the 〰️ ➰ ♾️ sequence as static text inside an SVG, for places that want it as an image. Plain inline text is preferred wherever possible.

### Layer icons (the SHIVA six)
- `icon-kernel.svg` — laws & invariants
- `icon-string.svg` — atomic primitive (sine wave)
- `icon-rope.svg` — composed bundle (twisted strands)
- `icon-sheet.svg` — visualization (grid)
- `icon-snake.svg` — adaptive (sinuous path with head)
- `icon-infinity.svg` — recursive scaling

### Product / UI icons
- `icon-anchor.svg` — anchor a capsule to ledger
- `icon-seal.svg` — sealed / attested
- `icon-ledger.svg` — append-only record
- `icon-vault.svg` — sealed store
- `icon-graph.svg` — node + edge
- `icon-studio.svg` — workspace
- `icon-search.svg` · `icon-settings.svg` · `icon-theme.svg`
- `icon-chevron-down.svg` · `icon-arrow-right.svg` · `icon-plus.svg` · `icon-check.svg` · `icon-warning.svg`

This is a **deliberately small** library. New icons should only be added when an existing one cannot carry the meaning, and the new icon must follow the same grammar.

## Use of glyphs and unicode

Glyphs and unicode characters carry semantic load and are treated as part of the icon vocabulary, not decoration:

- **`〰️ ➰ ♾️`** — the only emoji allowed, only as the SHIVA signature, only in this exact 3-glyph order. Never colored, animated, or replaced.
- **`·`** (middot `U+00B7`) — separator in dense labels: `dark · light · print`
- **`→`** (rightward arrow `U+2192`) — sequence: `Strings → Ropes → Sheets`
- **`∝`** (proportional `U+221D`) — used in the tuner vocabulary: `thickness ∝ quantity`
- **`∞`** (infinity `U+221E`) — concept invocation: `Snakes → ∞`
- **`—`** (em-dash `U+2014`) — parenthetical asides

No other emoji. No `✓` / `✗` / `⚠️` — use the SVG icon set instead. No flag emoji, hand emoji, or any colored unicode.

## Substitutions used

**None.** Everything in `assets/` is hand-rolled to the SHIVA grammar. No icon was substituted from Lucide, Heroicons, Phosphor, or Material; no glyph was inlined from Font Awesome. The whole point of the constraint is that the iconography is part of the brand surface, not an off-the-shelf library.

If a designer is producing a brand-new artifact and needs an icon not in this set, the priority order is:

1. Re-purpose an existing icon (most UI affordances can be expressed with `anchor / seal / ledger / arrow-right / chevron-down / plus / check / warning`).
2. Add a new SVG to `assets/` following the grammar above.
3. Only if neither works, fall back to the Lucide stroke-1.6 set as the closest visual match — and **flag the substitution** in the README of whatever ships.

〰️ ➰ ♾️
