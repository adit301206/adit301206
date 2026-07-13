# NOVA Engineering Intelligence Console — Design System

## 1. Brand Philosophy

NOVA is an engineering intelligence console: calm, capable, and precise. It should feel like a thoughtful operating layer around technical work, not a decorative sci-fi theme. Every visual treatment must improve orientation, hierarchy, or system feedback.

Core principles:

- **Intelligence over spectacle:** prioritise legibility and signal over ornament.
- **Quiet confidence:** use restrained surfaces, deliberate whitespace, and low-noise motion.
- **Technical warmth:** human-readable language and approachable structure balance the machine aesthetic.
- **Composable by default:** every asset should work alone and as part of a larger console.

## 2. Visual Language

The NOVA language combines dark translucent panels, thin luminous signal lines, rounded geometry, and sparse HUD details. Visual density increases only where information density increases.

- Base surfaces are dark blue-black with translucent glass layers.
- Cyan communicates focus, system activity, and primary connection.
- Purple communicates intelligence, orchestration, and secondary structure.
- Green communicates healthy or successful states.
- Warm amber is reserved for learning, caution, or work in progress.
- Decorative circuits, grids, and brackets belong at the perimeter; they must not compete with content.

## 3. Color Palette

| Token | Value | Use |
|---|---|---|
| `nova-bg` | `#0D1117` | Base dark canvas when a background is needed |
| `nova-surface` | `#101827` | Primary panel surface |
| `nova-surface-raised` | `#111C2B` | Raised glass cards and terminal panels |
| `nova-cyan` | `#00E5FF` | Primary actions, active signals, focus |
| `nova-purple` | `#7C3AED` | Secondary emphasis and intelligence states |
| `nova-mint` | `#00FFA3` | Success, online, healthy status |
| `nova-amber` | `#F6C453` | Learning, caution, in-progress status |
| `nova-text` | `#EAF7FF` | Primary text on dark surfaces |
| `nova-text-muted` | `#8FA1BA` | Supporting labels and metadata |
| `nova-border` | `#41546E` | Low-contrast structural borders |

Use opacity before adding new colors. Cyan at low opacity is preferred for subtle dividers and grids.

## 4. Typography

Use a system-first sans-serif stack for portable SVG and GitHub rendering:

```text
Inter, Segoe UI, Arial, sans-serif
```

Use a monospace stack only for terminal output:

```text
ui-monospace, SFMono-Regular, Consolas, monospace
```

| Role | Size | Weight | Tracking |
|---|---:|---:|---:|
| Display / project name | 27–60 px | 700 | -2.7 to -0.8 px |
| Section title | 22–30 px | 700 | 0–2 px |
| Panel title | 13–16 px | 700 | 1–2 px |
| HUD label | 10–11 px | 700 | 1.4–2 px |
| Body copy | 12–18 px | 400–500 | normal |

Uppercase labels are for concise system metadata only. Never uppercase paragraphs or primary narrative copy.

## 5. Spacing System

Use a four-point base unit. Prefer these increments:

`4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80`

- Minimum internal panel padding: `24 px`.
- Standard card padding: `32 px`.
- Major section separation: `48–80 px`.
- Keep at least `16 px` between a label and its value.
- Use consistent vertical rhythm; do not compensate for weak hierarchy with arbitrary gaps.

## 6. Border Radius

| Element | Radius |
|---|---:|
| Main console shell | 28 px |
| Large panel / card | 20–22 px |
| Standard module | 14–16 px |
| Pill / status control | 999 px or half of height |
| Small token / chip | 12–13 px |
| Signal line | half of stroke width |

Rounded corners should feel controlled, not soft or playful. Avoid mixing more than two radius scales in one component.

## 7. Stroke Thickness

| Use | Stroke |
|---|---:|
| Outer frame | 1.25 px |
| Panel boundary | 1 px |
| Divider / grid | 1 px |
| Active signal | 2 px |
| Icon detail | 2–4 px |
| Progress fill | 5–6 px |

Use `stroke-linecap="round"` for signals, circuits, and icon paths. Keep all passive borders below full opacity.

## 8. Glow Rules

Glows are feedback, not decoration.

- Apply glow only to active endpoints, focused borders, progress fills, and live status dots.
- Use a `3–4 px` Gaussian blur for normal elements.
- Keep static glow opacity low; a strong glow should be temporary or tied to an active state.
- Do not glow large text blocks, complete panels, or every line in a composition.
- One cyan glow source and one secondary accent glow are sufficient per component.

## 9. Shadow Rules

Shadows establish elevation against dark backgrounds. Use cool black shadows, never pure black borders.

- Standard elevated card: `0 14–16 px 16–18 px` with `#020617` at `0.55–0.65` opacity.
- Large console: `0 20 px 22 px` with `#030712` at `0.7` opacity.
- Use one shadow filter per parent group where possible for SVG efficiency.
- Do not combine heavy shadows with strong glows on every element.

## 10. Animation Rules

Motion should feel like an operational signal, not a loading screen.

- Preferred duration: `2.8–12 s`.
- Use `ease-in-out` behaviour when CSS animation is available; SVG SMIL should use gentle value transitions.
- Blinking cursors: `1 s`, opacity only.
- Status pulse: `1.5–3 s`, opacity and small scale/radius only.
- Scan lines: `8–12 s`, one per major composition.
- Never animate more than two independent effects in a compact component.
- Respect `prefers-reduced-motion` in web implementations; provide static fallbacks for critical meaning.

## 11. Icon Style

NOVA icons are geometric, monoline, and recognizable at `32 × 32 px`.

- Build with simple paths, circles, and rounded linecaps.
- Default icon stroke: `2–3 px` at a `96 × 96` viewBox scale.
- Use a single primary accent with, at most, one status-node accent.
- Avoid filled illustration, gradients, emoji, stock glyphs, and intricate micro-detail.
- Preserve a clear silhouette before adding neural nodes or circuit paths.

## 12. Grid System

Use responsive viewBoxes and a 12-column conceptual layout for wide console compositions.

- Standard desktop canvas: `1600 px` wide with `72–96 px` outer gutters.
- Main dashboard panels should align to a consistent vertical baseline.
- Use 24–32 px panel gaps.
- HUD grids use `32–48 px` cells at `0.035–0.055` cyan opacity.
- Grids and circuit traces are ambient layers, never content containers.

## 13. Component Naming

Use lowercase kebab-case filenames and semantic IDs.

```text
assets/components/developer-console.svg
assets/components/status-pill.svg
assets/cards/neurocity.svg
```

Recommended SVG IDs:

```text
toolbar
identity-panel
workspace
status-indicator
content-placeholder
progress-60
```

Do not use visual-only IDs such as `blue-box`, `thing-1`, or `group2`.

## 14. SVG Export Rules

- Include a `viewBox` on every SVG; avoid fixed dimensions as the sole sizing mechanism.
- Keep background transparent unless an asset explicitly requires a surface.
- Prefer paths, circles, rects, and reusable `<g>` groups over embedded raster images.
- Include a concise `<title>` and accessible `aria-label` or `aria-labelledby` for meaningful assets.
- Use descriptive IDs for gradients, filters, and component groups.
- Keep filters local and minimal; avoid full-canvas blur effects.
- Remove editor metadata, unused defs, hidden layers, and redundant groups before export.
- Test XML validity before committing.

## 15. Accessibility Rules

- Maintain text contrast suitable for dark surfaces; use `nova-text` for primary reading content.
- Do not communicate status by color alone; pair it with a label, dot, or icon.
- Decorative SVGs should use `alt=""` when embedded in Markdown.
- Informative SVGs require meaningful alternative text.
- Keep body copy at or above `12 px` in SVG exports.
- Avoid rapid flashes, high-frequency pulses, and animation that obscures information.

## 16. Mobile Compatibility

- Design every asset from its `viewBox`; let consumers scale it proportionally.
- Preserve a readable single-column order below approximately `720 px`.
- On narrow screens, stack project cards and analytics widgets vertically.
- Do not rely on hover for essential information.
- Keep terminal controls and status pills visually distinct at reduced scale.
- Avoid text that is only readable at desktop width; split long labels or remove secondary metadata when necessary.

## 17. GitHub Compatibility

- Use relative asset paths such as `./assets/components/status-pill.svg`.
- Prefer standard SVG features supported by GitHub’s image rendering pipeline.
- Treat SMIL animation as progressive enhancement; every asset must remain useful when static.
- Do not rely on external fonts, CSS variables, JavaScript, or `foreignObject`.
- Use simple HTML alignment in README files: `<div align="center">`, `<img width="...">`, and accessible `alt` text.
- Keep README sections purposeful; hide reusable templates in `<details>` to prevent visual noise.

## 18. File Organization

```text
assets/
├── backgrounds/     # Ambient HUD textures and grid layers
├── banners/         # Hero and footer compositions
├── cards/           # Project-specific and reusable cards
├── components/      # Reusable interface primitives
├── dividers/        # Section separators
└── icons/           # NOVA mark and compact icons
```

- One visual responsibility per file.
- Keep project-specific assets in `cards/` and shared primitives in `components/`.
- Use the same palette tokens and spacing scales across every directory.
- Do not duplicate an existing primitive; extend it or create a clearly named variant.

## 19. Future Expansion Rules

Before adding a component, confirm that it supports a real information or interaction need.

- Extend the existing component family before inventing a new visual language.
- Add variants through named SVG groups or separate files only when they have a distinct use case.
- New color usage must map to a semantic state; do not add accent colors for novelty.
- New motion must communicate progress, status, or focus.
- Maintain the hierarchy: content first, system state second, decoration last.
- Review at `32 px`, card scale, and full-width README scale before release.
- Update this document whenever a new reusable token, state, or component convention is adopted.
