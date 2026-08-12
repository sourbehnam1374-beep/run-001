# UI Kit · Explorer

> The **Explorer / Studio shell** — the multi-section navigator surface that fronts the Vault, Graph, Ledger, and Capsule index. Sticky two-layer header, sidebar of surfaces and domains, a main column of panels, and a right rail for the active selection.

## Anatomy

The layout is a 3-column grid: **220 / 1fr / 280**, all snapping to a single column under 1100 px. Both rails are `position: sticky` below the header.

### Sticky two-layer header (`<header class="top">` + `<nav class="tabs">`)

- Conic-disc logo, wordmark, subline, then a right-aligned action row: search input (icon-prefixed), Light/Dark toggle, primary "Anchor capsule" button.
- Tabs underneath (`top: 51px`) — Explorer · Capsules · Graph · Vault · Ledger · Studio. Active tab gets `aria-selected="true"` and the canonical outlined-pill style.

### Sidebar (`<aside class="sidenav">`)

Two nav-titled groups: **Surfaces** (mirrors the tab bar with counts), **Domains** (the 10 taxonomic stripes as inline mini-bars next to category names). Active item picks up the family accent and a chip background.

### Main column

Three stacked panels:

1. **Recent capsules** — Encyclopedia grid of 6 cards, each with a domain stripe at the top, a meta line (`cat · cap_id`), a title, a one-sentence summary, and a dashed-divided stats footer with a status badge.
2. **Provenance graph + Tuners** — a 1.5fr / 1fr row. The graph is a radial figure with animated edges and three secondary nodes annotated with their attestation roles. Tuners is a 2-column list of canonical perceptual-mapping rules with a `<details>` family note.
3. **Ledger** — append-only event log; 4-column rows (`time · message · status · hash`). Hover lifts the row to `var(--chip)`.

### Right rail (`<aside class="rail">`)

- **Selection** panel — what's currently focused (family tag + status badge, one-sentence description, Merkle root hash block, integrity pill row).
- **Activity** feed — five rows of snake-agent activity. Each row has a colored dot (ok / warn / acc), a sentence, and a `meta` line for time + context.

## Recreated screen

[`index.html`](./index.html) — *Explorer · Pelvic_R_v2 selected.* Demonstrates all of the above plus the canonical dark/light theme swap.

## What this kit doesn't do

- Search and filter inputs are decorative — no live filtering.
- Graph nodes aren't draggable; the figure is static SVG (per spec, no JS-dependent layout).
- The right-rail Selection panel doesn't update when you click a card — it's a single canonical state.

These are intentionally cosmetic. A production Studio would back them with the actual Vault index and Graph traversal API; without product code, the kit recreates the visual surface only.

〰️ ➰ ♾️
