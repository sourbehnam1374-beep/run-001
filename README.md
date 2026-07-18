# SHIVA Design System

**A provenance-first visual language and static HTML component library for inspectable knowledge artifacts.**

> **Status:** Active design specification and reference implementation. The examples are research and interface artifacts; they are not validated medical devices and must not be used for autonomous clinical decisions.

Every visual choice carries meaning: color encodes family, thickness encodes quantity, opacity encodes confidence, dash encodes polarity, and jitter encodes instability. Motion is semantic rather than decorative.

## Entry points

- [Design tokens](colors_and_type.css)
- [Component and motion primitives](shiva.css)
- [Capsule UI kit](ui_kits/capsule/)
- [Explorer UI kit](ui_kits/explorer/)
- [Component previews](preview/)
- [Iconography](ICONOGRAPHY.md)
- [Reference artifact](reference/SHIVA_design_starter.html)

The deployed Cloudflare surface is intentionally built only from `site/`. Repository documentation, source references, and development files must never be exposed as web assets.

---

## Conceptual layers (the SHIVA six)

| Layer    | Glyph | Role |
|----------|-------|------|
| Kernel   | —     | laws & invariants |
| String   | 〰️    | atomic primitives |
| Rope     | ➰    | composed modules |
| Sheet    | —     | visualizations |
| Snake    | —     | adaptive agents |
| Infinity | ♾️    | recursive scaling |

The three-glyph sequence **〰️ ➰ ♾️** is the canonical signature. It appears as a footer mark on every capsule, as a section terminator, and as mantra punctuation. Do not stylize, color, replace, or animate.

---

## Content fundamentals

SHIVA's copy is **technical-precise**, written from the system's point of view, not the user's. It treats every UI element as a claim with provenance, and prefers exact technical terms over marketing softening.

### Tone

- **Register:** technical, declarative, low-affect. Statements of fact, not promises. Short clauses joined by middots (·) or arrows (→).
- **Person:** third-person system voice ("the capsule seals…", "the ledger records…"). Second-person ("you") is acceptable only in onboarding flows. First-person plural ("we") is rarely used and never in product UI.
- **Casing:** Sentence case for prose, sentence case for buttons. Uppercase letterspaced (`tracking: 0.14em–0.18em`) for kickers, section numbers, and labels above hash blocks. Never use ALL CAPS for prose.
- **Cadence:** mantra-style enumeration is encouraged. `Locked palette · crisp edges · CSS-only motion · zero external calls.`
- **Emoji:** none in UI affordances. **Only** the three-glyph signature `〰️ ➰ ♾️`. Treat these as textual atoms — never colored, animated, replaced, or used as decoration anywhere else.
- **Unicode:** `·` (middot) and `→` (arrow) are the canonical separators. `∝` for proportionality. `∞` standalone where the recursive-scaling concept is invoked without the full signature. Em-dashes (`—`) for parentheticals.

### Preferred / avoided terminology

| Prefer | Avoid |
|---|---|
| provenance | tracking |
| attestation | verification (verification is the act, attestation is the artifact) |
| capsule | document |
| anchor | save |
| seal | lock |
| claim | statement |
| ledger | log |
| kernel | core |
| sheet | dashboard / report |
| snake | bot / agent (in product copy; "snake" is the SHIVA term) |

### Forbidden words

`empower · unlock · seamless · revolutionary · leverage` (as verb) `· synergy · robust` (use the actual property instead) `· best-in-class · cutting-edge`

### Example copy

```
Clinical Integrity Capsule
Pelvic Shape Ratio (R) — Reliability Sub-study
Single-rater test–retest across 29 lateral radiographs and 6 measurement sessions.
Average-of-6 ICC reaches 0.815 (95% CI 0.60–0.90).
                                            〰️ ➰ ♾️
```

```
Locked palette · crisp edges · CSS-only motion
Strings → Ropes → Sheets → Snakes → ∞
```

```
[JCS] [SHA-256] [Merkle] [DSSE]   ← integrity pills
sealed · pending · violation       ← badge text
```

The vibe: a research notebook attested by a cryptographer. Quiet, exact, structural. Never enthusiastic. Never performative.

---

## Visual foundations

### Color

Color is **never** ordinal or quantitative. Color encodes **family or category**; quantity uses thickness or opacity. The full token table lives in `colors_and_type.css`.

- **Four UTS families** drive accent color: Static `#2563eb` (blue), Dynamic `#ea580c` (orange), Relational `#16a34a` (green), Vital `#9333ea` (purple).
- **Ten domain accents** are reserved for taxonomic stripes only: data, scitech, code, images, media, archive, docs, security, sim, web/ai. Hues are canonical — never reassign.
- **Three status hues** (`--ok #22c55e`, `--warn #f59e0b`, `--bad #ef4444`) only ever appear in badges, tier markers, and the equivalent semantic UI atoms.
- **Surface ladder** is two stops: `--bg → --panel → --panel-2 → --chip → --surface`. Light and dark are full mirrors; the *only* allowed gradient outside the capsule background and the domain stripes is `var(--capsule-bg)`, a radial-gradient.

### Type

System stack only. **No web fonts, no Google Fonts, no `@import`, no network calls.**

```
--font-sans: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, Arial, sans-serif;
--font-mono: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
```

Headings sit at weight `650` with `letter-spacing: -0.02em`. Kickers and section numbers are uppercase mono at `11px` with `letter-spacing: 0.14em–0.18em`. Capsule prose is `0.95rem / 1.6`. Tag pills are `11px`. Hash blocks and integrity pills use mono. Inter renders consistently across macOS/iOS/Linux when present; the fallback ladder keeps the system stack legible everywhere it isn't.

> **Font note** — Inter is referenced by name but never bundled. Many systems (iOS, recent macOS, modern Linux distros) have it installed; older systems will fall through to the system sans-serif. If you need pixel-stable Inter rendering across machines, drop an Inter `.woff2` set into `fonts/` and add a single `@font-face` block — but the system explicitly **prohibits external font requests**.

### Spacing & shape

- **Spacing scale** is a 4 px grid: `4 · 6 · 8 · 10 · 12 · 14 · 18 · 22 · 28 · 36 · 44`.
- **Corner radii encode forgiveness:** sharp = hard rule, rounded = soft guidance.
  - Pills `999px` (tags, badges, tabs, buttons)
  - Card `12px`
  - Section `14px`
  - Hash block / capsule body `16px`
  - Hero / capsule outer `18px`
- **Borders** are always `1px solid var(--border)` — `#1e293b` dark, `#e5e7eb` light. Dashed and dotted borders carry semantic load (tier markers: solid = confirmed, dashed = context, dotted = inferred).

### Backgrounds, imagery, gradients

- **No background photos.** No stock imagery. No hero photography. Ever.
- **No gradients** outside two allowed cases: the `radial-gradient(circle at top, …)` capsule background, and the `linear-gradient(90deg, …)` domain stripes.
- **Texture vocabulary** (18 patterns: `bg-grid`, `bg-dots`, `bg-wave`, `bg-radial`, `bg-rings`, `bg-lattice`, `bg-check`, `bg-cells`, `bg-cone`, etc.) are very light overlays at rgba `.02–.04`. Texture and family must be coherent: vital cards use `bg-cells / bg-radial / bg-cone`; relational uses `bg-lattice / bg-rings / bg-check`; static uses `bg-grid / bg-tiles / bg-hatch-thin`; dynamic uses `bg-wave / bg-pulse / bg-bars`.

### Animation

Motion is a semantic layer, not decoration. The kit is **closed** — eight keyframes, fixed durations, no new ones:

| Class | Keyframe | Duration | Encodes |
|---|---|---|---|
| `.anim-dash` | stroke-dashoffset → -120 | 10 s linear | flow direction |
| `.anim-flow` | stroke-dashoffset → -2600 | 18 s linear | long-range flow |
| `.anim-pulse` | opacity 0.3 ↔ 1 | 1.6 s ease-in-out | attention / activity |
| `.anim-wobble` | translateX 0 ↔ 4 px | 1.8 s ease-in-out | mild instability |
| `.anim-drift` | translate(0,0) ↔ (6,−4) | 3 s ease-in-out | slow change |
| `.anim-jitter` | translate(0,0) ↔ (−1,1) | 2.4 s linear | noise / entropy |
| `.anim-spin-slow` | rotate(0→360) | 18 s linear | orbit / cycle |
| `.anim-breathe` | scale 1 ↔ 1.04 | 4 s ease-in-out | coupled rhythm |

**Easing is ease-in-out, linear, or none.** No bouncy / elastic / spring easings, ever. Animation speed ∝ urgency. All animations **must** be disabled under `@media (prefers-reduced-motion: reduce)` and `@media print` — `shiva.css` already wraps the canonical classes; new keyframes must match.

### Hover, focus, press

- **Hover (links, buttons, tabs):** the border tints to `var(--accent)`. No fill change, no underline. Buttons subtly raise `filter: brightness(1.06)` only when they're primary-filled.
- **Focus-visible:** `outline: 2px solid var(--accent); outline-offset: 2px`.
- **Press:** `transform: translateY(0.5px)`. No scale-down. No color flash.
- **Figures** follow a dedicated **three-state model** (see below): rest, hover/focus, print. On hover/focus the shadow lifts from `0 4px 18px` to `0 14px 45px`, edges brighten from `--muted` to `var(--accent)`, and ropes brighten to `--c-code`.

### Shadows

Two-step elevation only:
- `--shadow: 0 4px 18px rgba(0,0,0,.28)` (panel, default lift)
- `--shadow-hover: 0 14px 45px rgba(0,0,0,.45)` (figure on hover/focus)

No inset shadows. No multi-layer shadows. No colored shadows.

### Transparency & blur

- The sticky header uses `backdrop-filter: blur(8px)` against a 97% → 85% opacity gradient of the page background. This is the **only** place backdrop blur is used.
- Tag pills, badges, status colors use **rgba at 0.12** for their tinted backgrounds — full saturation only in text.

### Layout rules

- **Sticky two-layer header** at `z:40` (brand) + `z:35` (tabs at top:56px).
- **Container widths:** prose capsules cap at `720–900 px`; explorer/encyclopedia surfaces at `1180–1380 px`. Never full-bleed body text.
- Page is fully usable with **JS disabled**. JS is limited to local interactions (theme toggle, tab activation). No JS-dependent layout, no scroll-jacking, no parallax, no fixed-positioned popups.

### Cards

`border: 1px solid var(--border) · border-radius: 12px · background: var(--chip) · padding: 12px · box-shadow: var(--shadow)`. Card titles `13px / 650 / −0.01em`. Card meta `11px / muted`. A `.rule` line at the bottom is a `1px dashed` separator above an `11px mono / muted` caption.

### Figure — the three-state interaction model

Every figure is a first-class document object (not a passive image). It carries `tabindex="0"`, `role="img"`, and `aria-label`.

- **REST** — edges in `var(--muted)`, no animation, full information visible.
- **HOVER / FOCUS-WITHIN** — edges → `var(--accent)`, ropes → accent-2, shadow lifts.
- **PRINT** — animations disabled, pure vector, legible at 100 % on paper.

---

## Iconography

See [`ICONOGRAPHY.md`](./ICONOGRAPHY.md). Short version: **inline SVG only**, semantic classes, no icon font, no Lucide/Heroicons/Font Awesome, no emoji except `〰️ ➰ ♾️`.

---

## Index — what's in this repo

| Path | Purpose |
|---|---|
| `README.md` | This file. Brand context, content fundamentals, visual foundations. |
| `ICONOGRAPHY.md` | Approach to icons + glyphs. |
| `SKILL.md` | Agent skill entry point — read this if you're an LLM picking up the brand. Cross-compatible with Claude Code skill discovery. |
| `colors_and_type.css` | Canonical tokens — colors, type, spacing, radii. Light + dark themes via `data-theme` on `<html>`. |
| `shiva.css` | Animation kit, component atoms (tags / badges / pills / hash-block / button / tab / card / capsule / figure), canonical SVG diagram classes, 18 background textures, domain stripes. |
| `reference/SHIVA_design_starter.html` | The original v1 starter from the user — the source of truth to diff against. |
| `assets/` | 22 inline-SVG files — conic-disc logo, glyph signature, six layer icons (kernel/string/rope/sheet/snake/infinity), eight product icons (anchor/seal/ledger/vault/graph/studio/search/settings), six UI atoms (theme/chevron/arrow/plus/check/warning). |
| `preview/*.html` | 34 Design System tab cards — small specimens grouped by Brand / Colors / Type / Spacing / Components. |
| `ui_kits/capsule/` | Capsule surface — single-file HTML report. `index.html` is a sealed *Pelvic Shape Ratio · Reliability Sub-study* deliverable with cover sheet, 4-up KPI strip, variance-partition figure, tier table, hash block, and Observe→Decide ladder. |
| `ui_kits/explorer/` | Explorer / Studio shell — `index.html` is the multi-section navigator with sticky 2-layer header, sidebar (Surfaces + Domains), main column (encyclopedia grid + provenance graph + tuners + ledger), right rail (Selection + Activity). |

---

## Contributing and security

See [`CONTRIBUTING.md`](CONTRIBUTING.md) before proposing design changes. Report vulnerabilities privately using [`SECURITY.md`](SECURITY.md).

Do not commit patient information, clinical images, buyer identities, payment records, private messages, credentials, tokens, wallet addresses, or live integration URLs. Public examples must be synthetic or clearly public and redistributable.

## Absolute constraints (binding)

- **No external fonts, scripts, CDNs, or network calls.** Inline everything.
- **No JS-dependent layouts.** Page must be fully usable with JS disabled.
- **No Google Fonts, Font Awesome, or icon fonts.** Use inline SVG icons.
- **No background photos or stock imagery.**
- **No bouncy/elastic easings.** Motion is ease-in-out, linear, or none.
- **No scroll-jacking, parallax, or fixed-positioned popups.**
- **No gradients** outside the radial-gradient capsule background and domain stripes.
- **No new accent hues** beyond the canonical 10 domain colors + 4 family colors.
- **No emoji** in UI affordances. Only `〰️ ➰ ♾️` as signature.
- **Always provide both** dark and light variants of any artifact.
- **Always make text selectable**, even in diagrams.
- **Always respect** `prefers-reduced-motion`.
- **Always include** `tabindex` and `aria-label` on figures.

〰️ ➰ ♾️
