# Hero Use Case Design System

**Theme:** Hero Use Case template -- Marketing/showcase template with Diligent red brand accent.
**Source:** Generated from hero-usecase.json + DESIGN.md editorial content.

---

## Typography

**Font family:** `'Source Sans 3', system-ui, sans-serif` (from `--font-sans` token)

Note: The JSON specifies "Source Sans 3" (the variable-font rebrand of Source Sans Pro). Both resolve to the same typeface family. Use whichever is loaded in the project; they are interchangeable for design purposes.

| Scale | Size | Line height | Use for |
|-------|------|-------------|---------|
| Billboard | 4rem (64px) | 5rem | Hero headers, landing |
| Display | 2.5rem (40px) | 3rem | Page titles |
| Title lg | 1.75rem (28px) | 2rem | Section headers |
| Title md | 1.375rem (22px) | 1.625rem | Card headers |
| Title sm | 1.125rem (18px) | 1.5rem | Subsection headers |
| Body | 1rem (16px) | 1.25rem | Default text |
| Text md | 0.875rem (14px) | 1.125rem | Secondary text, descriptions |
| Text sm | 0.8125rem (13px) | 1rem | Captions, metadata |
| Text xs | 0.75rem (12px) | 0.875rem | Fine print, badges |

**Weights:** Light 300 | Regular 400 | Emphasis 600 | Bold/Link 700

**Labels:** Uppercase, 1px letter-spacing, 0.75rem size, 0.8125rem line-height.

---

## Color Palette

All 16 tokens from the Hero Use Case theme. The key differentiator from Atlas themes is `--brand-primary: #EE312E` (Diligent red), used for hero CTAs and marketing emphasis.

### Backgrounds

| Token | Hex | Use |
|-------|-----|-----|
| `--bg-base` | `#f4f6f8` | Page background |
| `--bg-surface` | `#ffffff` | Card/panel surfaces |
| `--bg-elevated` | `#eef2f6` | Elevated panels, hover tints |

### Text

| Token | Hex | Use |
|-------|-----|-----|
| `--text-primary` | `#1e1e1e` | Body text, headings |
| `--text-secondary` | `#676767` | Muted text, placeholder |
| `--text-muted` | `#949494` | Captions, metadata, disabled text |

### Actions

| Token | Hex | Use |
|-------|-----|-----|
| `--action-default` | `#455D82` | Functional UI buttons, secondary CTAs |
| `--action-hover` | `#364262` | Hover state for action-default buttons |

### Brand

| Token | Hex | Use |
|-------|-----|-----|
| `--brand-primary` | `#EE312E` | Hero CTAs, marketing emphasis, brand accent |

### Status

| Token | Hex | Use |
|-------|-----|-----|
| `--status-success` | `#05704B` | Confirmations, completed states |
| `--status-warning` | `#935206` | Warning text (higher contrast) |
| `--status-error` | `#AF292E` | Errors, destructive indicators |
| `--status-info` | `#385F99` | Info banners, notification badges |

### Borders & Dividers

| Token | Hex | Use |
|-------|-----|-----|
| `--border-default` | `#e6e6e6` | Container borders, input borders |
| `--ui-divider` | `#e6e6e6` | Horizontal/vertical rules, separators |

### Font

| Token | Value | Use |
|-------|-------|-----|
| `--font-sans` | `'Source Sans 3', system-ui, sans-serif` | All UI text |

---

## Spacing

8px base unit. Use multiples consistently.

| Token | Value | Common use |
|-------|-------|-----------|
| 0.25 | 2px | Hairline gaps |
| 0.5 | 4px | Tight padding (badges, chips) |
| 1 | 8px | Default gap, inline spacing |
| 1.5 | 12px | Comfortable internal padding |
| 2 | 16px | Card padding, section gaps |
| 2.5 | 20px | Generous padding |
| 3 | 24px | Section spacing |
| 4 | 32px | Large section breaks |
| 5 | 40px | Page-level spacing |
| 6 | 48px | Major section dividers |
| 7 | 56px | -- |
| 8 | 64px | Maximum spacing |

---

## Borders & Radius

| Token | Value |
|-------|-------|
| Radius sm | 2px |
| Radius md | 4px |
| Border thin | 1px |
| Border thick | 2px |
| Focus width | 2px |
| Focus offset | 1px |

Atlas uses **tight radii** (2-4px). This is a conservative, professional aesthetic -- avoid rounded corners beyond 4px unless intentionally breaking the pattern for emphasis.

---

## Shadows

| Level | CSS | Use |
|-------|-----|-----|
| Low | `0px 4px 24px -8px #00000010, 0px 1px 6px -2px #00000038` | Cards, dropdowns |
| Medium | `0px 6px 16px -4px #00000020, 0px 5px 8px -8px #00000008` | Popovers, floating panels |
| High | `0px 10px 32px -6px #00000020, 0px 4px 4px -2px #00000008` | Modals, overlays |
| Tooltip | `0px 8px 16px 0px #0000001F, 0px 0px 4px 0px #00000029` | Tooltips |
| Focus | `0 0 0 1px #ffffff, 0 0 0 3px #3e95fa` | Focus ring (double-ring pattern) |

Shadows are **subtle and diffuse** -- not heavy drop shadows. The aesthetic is clean and lifted, not skeuomorphic.

---

## Raw CSS Custom Properties

```css
:root {
  --bg-base: #f4f6f8;
  --bg-surface: #ffffff;
  --bg-elevated: #eef2f6;
  --text-primary: #1e1e1e;
  --text-secondary: #676767;
  --text-muted: #949494;
  --action-default: #455D82;
  --action-hover: #364262;
  --status-success: #05704B;
  --status-warning: #935206;
  --status-error: #AF292E;
  --status-info: #385F99;
  --brand-primary: #EE312E;
  --border-default: #e6e6e6;
  --ui-divider: #e6e6e6;
  --font-sans: 'Source Sans 3', system-ui, sans-serif;
}
```

---

## Design Principles

1. **Professional and restrained** -- Muted blue-grey palette. Avoid high saturation except for status colors.
2. **Dense but readable** -- Board management UIs show lots of data. Favor compact layouts with clear hierarchy.
3. **Contrast through weight, not color** -- Use font weight and size to create hierarchy. Reserve color for actions and status.
4. **Dark top, light content** -- The `#2F3B4D` top nav anchors the page. Content area is `#f4f6f8` with `#ffffff` cards.
5. **Minimal elevation** -- Use subtle shadows sparingly. Flat surfaces with thin dividers are preferred.

**Hero Use Case adaptation:** `--brand-primary` (`#EE312E`) should be used for hero CTAs and marketing emphasis, while `--action-default` (`#455D82`) remains the correct choice for functional UI buttons. The Diligent red draws the eye to conversion-oriented elements without overwhelming the professional blue-grey palette.

---

## Gaps & Fallbacks

This theme defines only **16 tokens** -- a minimal marketing-focused subset. The following categories present in Atlas Light (DESIGN.md) are absent and should fall back to DESIGN.md values:

| Missing category | Fallback source | Notes |
|------------------|----------------|-------|
| Shadows | DESIGN.md shadow table | No `--shadow-*` tokens in JSON |
| Border radii | DESIGN.md radius table (2px, 4px) | No `--radius-*` tokens in JSON |
| Border widths | DESIGN.md border table (1px, 2px) | No `--border-width-*` tokens in JSON |
| Link states | DESIGN.md links (default/hover/active/disabled) | Only `--status-info` overlaps with link default |
| Destructive action states | DESIGN.md destructive table | `--status-error` covers default only; no hover/active |
| Accent colors | DESIGN.md accent palette (5 decorative fills) | No accent tokens in JSON |
| Disabled states | DESIGN.md disabled bg/text | `--text-muted` approximates disabled text; no disabled bg token |
| Data visualization | DESIGN.md chart palette (8 colors) | No dataviz tokens in JSON |
| Focus ring | DESIGN.md focus ring (`#3e95fa`) | No focus token in JSON |
| Action active/pressed | DESIGN.md sea-800 (`#252C44`) | Only default and hover states present |
| Dark nav background | DESIGN.md Brand (`#2F3B4D`) | No nav/topbar tokens in JSON |
| Icon sizes | DESIGN.md icon scale (16-48px) | No icon tokens in JSON |
| Muted status variants | DESIGN.md (warning bg `#EAA14B`, notification badge `#E71613`) | Only text-contrast status values present |

When building components with this theme, apply the 16 JSON tokens first, then inherit everything else from DESIGN.md / Atlas Light defaults.

---

## Component API

No `design_instructions` provided in the JSON template (`null`). Component-level guidance should be sourced from DESIGN.md's Available Component Tokens section and Atlas component documentation.
