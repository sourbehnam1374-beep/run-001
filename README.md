# SHIVA Design System

> **Strings → Ropes → Sheets → Snakes → ∞**  
> Determinism · Provenance · Governance · Inspectable structure

SHIVA is a provenance-first, graph-native knowledge system for trusted knowledge and governed action. Its public visual language is built around self-contained capsules and a small set of product surfaces: Studio, Graph, Vault, Ledger, and Explorer.

This repository is the canonical public specification for SHIVA's visual, interaction, and tonal system. Every visual choice carries semantic load:

- color = family or category
- thickness = quantity
- opacity = confidence
- dash = polarity or status
- jitter = instability
- motion = state or directional change

Decorative elements that do not encode meaning are excluded.

## Conceptual layers

| Layer | Glyph | Role |
| --- | --- | --- |
| Kernel | — | laws and invariants |
| String | 〰️ | atomic primitives |
| Rope | ➰ | composed modules |
| Sheet | — | visualized structures |
| Snake | — | adaptive processes |
| Infinity | ♾️ | recursive scaling |

The canonical signature is `〰️ ➰ ♾️`. It is treated as a fixed textual mark rather than decoration.

## Public components

| Path | Purpose |
| --- | --- |
| `README.md` | Public design rationale and binding principles |
| `ICONOGRAPHY.md` | Inline-SVG icon grammar |
| `colors_and_type.css` | Canonical color, typography, spacing, radius, and theme tokens |
| `shiva.css` | Components, semantic motion, textures, and diagram classes |
| `assets/` | Logos, layer symbols, product icons, and interface atoms |
| `preview/` | Atomic design specimens |
| `ui_kits/capsule/` | Self-contained integrity-capsule reference implementation |
| `ui_kits/explorer/` | Explorer and Studio reference surface |
| `reference/` | Preserved public design reference material |

## Content system

SHIVA uses a technical, declarative, low-affect voice. Claims are stated with their status and provenance rather than softened through promotional language.

Preferred vocabulary:

`provenance · attestation · capsule · anchor · seal · claim · ledger · kernel · sheet`

Avoided promotional vocabulary:

`empower · unlock · seamless · revolutionary · synergy · best-in-class · cutting-edge`

## Visual foundations

### Color

Color identifies family or category; it never carries ordinal magnitude. Quantity is encoded through thickness or opacity.

The four primary families are:

- Static
- Dynamic
- Relational
- Vital

Status hues are reserved for confirmed, pending, and violation states. New accent families are not introduced ad hoc.

### Typography

The system uses a local system-font stack only. Text remains selectable, searchable, and printable. External font requests are prohibited.

### Shape and spacing

Spacing follows a four-pixel base rhythm. Shape carries meaning: sharp geometry indicates hard rules; rounded geometry indicates guidance or reversible interaction.

### Motion

Motion is semantic rather than ornamental. The motion vocabulary is closed, restrained, and disabled for reduced-motion preferences and print.

### Figures

Every figure is a first-class document object with three states:

1. Rest — full information visible without interaction
2. Hover or focus — semantic emphasis only
3. Print — static, vector-first, and legible at normal scale

## Absolute constraints

- No external fonts, scripts, content-delivery networks, or runtime network dependencies in capsules.
- No JavaScript-dependent layout.
- No stock photography or decorative background imagery.
- No unbounded animation vocabulary.
- No scroll-jacking, parallax, or fixed-position interruption layers.
- No gradients outside the canonical capsule background and domain stripes.
- No new accent hues outside the defined token system.
- No interface emoji except the canonical signature.
- Dark and light variants are both supported.
- Text remains selectable, including inside diagrams.
- Reduced-motion and print behavior are mandatory.
- Figures include keyboard focus and accessible labels.

## Release boundary

This repository contains the public design specification and inspectable reference implementations. Active clinical logic, unreleased research, private development workflows, and internal operating material are maintained outside the public release.

Nothing in this repository is presented as a clinical device or a substitute for independent validation.

〰️ ➰ ♾️
