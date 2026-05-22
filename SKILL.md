---
name: shiva-design
description: Use this skill to generate well-branded interfaces and assets for SHIVA — a provenance-first, graph-native knowledge operating system — either for production or for throwaway prototypes, mocks, capsules, and explorer screens. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for prototyping.
user-invocable: true
---

# SHIVA — design skill

> **Strings → Ropes → Sheets → Snakes → ∞**   〰️➰♾️
> Determinism · Provenance · Governance · Inspectable Structure

## Read these first

1. [`README.md`](./README.md) — brand context, content fundamentals (voice/tone/casing/forbidden words), visual foundations (color/type/spacing/animation/hover/layout), and the absolute constraints list.
2. [`ICONOGRAPHY.md`](./ICONOGRAPHY.md) — inline-SVG-only icon grammar.
3. [`colors_and_type.css`](./colors_and_type.css) and [`shiva.css`](./shiva.css) — the canonical tokens, animation kit, component atoms, textures, and diagram classes. Always link both; don't reinvent them.
4. [`reference/SHIVA_design_starter.html`](./reference/SHIVA_design_starter.html) — the user-provided v1 starter; the source of truth for tokens, motion kit, and structural patterns.

## Then explore

- `preview/*.html` — atomic design specimens (cards in the Design System tab).
- `ui_kits/capsule/` — single-file integrity capsule recreation; the canonical deliverable shape.
- `ui_kits/explorer/` — Studio shell (sticky header + sidebar + main + rail) recreation.
- `assets/` — inline-SVG icons + brand atoms. Copy these out when building new artifacts.

## How to use this skill

If creating visual artifacts (capsules, slides, mocks, throwaway prototypes), **copy the assets you need into your output** and produce static HTML files for the user to view. Every artifact must:

- inline all CSS, JS, and fonts (no network calls — capsules are self-contained, offline-viewable, iOS-safe)
- ship both dark and light variants, with the theme toggle wired through `data-theme` on `<html>`
- respect `prefers-reduced-motion` (the canonical `.anim-*` classes already do)
- include `tabindex="0"`, `role="img"`, and `aria-label` on every figure
- end with `〰️ ➰ ♾️` as the footer mark — the three-glyph signature, never stylized

If working on production code, copy assets and read the rules to become an expert in designing with the brand. The rule set is binding.

## Pre-flight checklist before shipping

- [ ] Color = family or category, never quantity. Quantity uses thickness or opacity.
- [ ] No gradients outside `var(--capsule-bg)` and domain stripes.
- [ ] No emoji except `〰️ ➰ ♾️`. No `✓ / ✗ / ⚠️` — use the SVG icon set.
- [ ] No new accent hues beyond the 4 family colors + 10 domain colors + 3 status colors.
- [ ] No bouncy / elastic easings. Motion is `ease-in-out`, `linear`, or none.
- [ ] Voice avoids: empower, unlock, seamless, revolutionary, leverage, synergy, robust, best-in-class, cutting-edge.
- [ ] Voice prefers: provenance · attestation · capsule · anchor · seal · claim · ledger · kernel.
- [ ] Page is fully usable with JavaScript disabled.

## If the user invokes this skill without other guidance

Ask what they want to build or design. Likely options: **a capsule** (single-file sealed deliverable), **a Studio surface** (multi-section navigator), **a slide deck** (use the visual foundations + signature glyph), **a diagram** (pick one of FLOW / STACK / GRAPH / LADDER), or **an explainer** of the SHIVA system itself (use the layer ladder).

Ask 4–8 focused questions before building. Confirm:

- artifact type (capsule, dashboard surface, slide deck, diagram, explainer)
- which UTS family is dominant (Static, Dynamic, Relational, or Vital)
- which domain stripe applies (data, scitech, code, …) if a stripe is wanted
- dark / light / both
- whether the artifact will be printed (if yes, every animation must degrade)
- how many tiered claims and integrity pills to surface
- whether to wire a theme toggle and any other minimal JS

Then build static HTML, copy the assets into the output folder, and end the file with `〰️ ➰ ♾️`.

〰️ ➰ ♾️
