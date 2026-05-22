# UI Kit · Capsule

> A SHIVA **capsule** is a single-file HTML deliverable — self-contained, offline-viewable, iOS-safe, and structured to a fixed grammar.

## Anatomy

A capsule is built as a vertical stack of:

1. **Sticky brand row** — `<header class="capsule-top">` with the conic disc, the wordmark, a breadcrumb of where the capsule lives in the Vault, and a theme toggle. Only piece of JS in the file.
2. **Cover sheet** — `<section class="sheet">` carrying the radial-gradient capsule background. Wordmark lockup → kicker → title → one-sentence summary → meta strip (family tag + status badge + integrity pills).
3. **KPI strip** — 3–4 `<div class="kpi" data-family="...">` cards. The KPI value picks up the family accent; `data-family` cascades `--accent`.
4. **Doc sections** — each opens with a `.num` section number, an `<h2>`, and a `.lead` paragraph. Bodies are figures, tier tables, hash blocks, and `<details>` collapsibles.
5. **Footer** — divider, version + seal date, `〰️ ➰ ♾️` glyph at letterspacing 12, mantra line.

## Recreated screen

[`index.html`](./index.html) — *Pelvic Shape Ratio (R) · Reliability Sub-study*. A clinical-integrity capsule reporting an ICC sub-study across 29 lateral radiographs. Demonstrates:

- the cover sheet pattern
- a 4-up KPI strip with family-coded accents
- a variance-partition bar figure with the canonical breathe-pulse on the stability column and a dashed clinical threshold
- a 2-up provenance pane (tier table + integrity pills + Merkle hash block)
- the **Observe → Hypothesize → Model → Check → Decide** ladder as a horizontal SVG with annotated step copy
- the dark + light theme toggle wired through `data-theme` on `<html>`

## What this kit doesn't do

Because the original product has no codebase or Figma file attached, no interactive behaviors are recreated beyond the theme toggle. A capsule is intentionally **static**: it's a sealed artifact, not an app. Future versions might add a search/filter UI, but that's out of scope until product code is available.

## Sources

Patterns lifted directly from `reference/SHIVA_design_starter.html` (the user-provided starter) and the v2 design spec. Components are restyled inline — they all use the canonical classes from `shiva.css` and tokens from `colors_and_type.css`.

〰️ ➰ ♾️
