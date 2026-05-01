# Atlas Lens Design System

**Theme:** Atlas Lens — Product-focused deep navy. Optimized for long working sessions and dense dashboards.
**Source:** Generated from atlas-lens.json + DESIGN.md editorial content.

---

## Typography

**Font family:** `'Plus Jakarta Sans', 'Source Sans 3', system-ui, sans-serif` (from `--font-sans`)

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

**Weights:** Light 300 · Regular 400 · Emphasis 600 · Bold/Link 700

**Labels:** Uppercase, 1px letter-spacing, 0.75rem size, 0.8125rem line-height.

---

## Color Palette

### Backgrounds — Deep navy spectrum

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Base | `--bg-base` | `#1a1f2e` | Page background (deep navy) |
| Surface | `--bg-surface` | `#242a3a` | Card/panel surfaces |
| Elevated | `--bg-elevated` | `#2e3548` | Elevated panels, hover surfaces |
| Overlay | `--bg-overlay` | `#242a3a` | Modal/dialog overlays |
| Inset | `--bg-inset` | `#141825` | Inset areas, scrollbar tracks |
| Top | `--bg-top` | `#141825` | Top nav bar |

### Text

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Primary | `--text-primary` | `#f0f2f5` | Body text, headings |
| Secondary | `--text-secondary` | `#b6b8b9` | Descriptions, supporting text |
| Muted | `--text-muted` | `#8c8e92` | Placeholders, metadata |
| Disabled | `--text-disabled` | `#6f7377` | Disabled elements |
| Inverse | `--text-inverse` | `#1a1f2e` | Text on bright backgrounds (buttons) |

### Actions — Diligent red as primary CTA

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Default | `--action-default` | `#e5252e` | Primary buttons, CTAs |
| Hover | `--action-hover` | `#cc2028` | Button hover state |
| Muted | `--action-muted` | `#e5252e20` | Ghost button bg (12.5% opacity) |

### Links

| State | CSS Variable | Hex |
|-------|-------------|-----|
| Default | `--link-default` | `#7da3d4` |
| Hover | `--link-hover` | `#a0bfe0` |

### Status

| Status | CSS Variable | Hex | Muted variant |
|--------|-------------|-----|---------------|
| Success | `--status-success` | `#4ead6b` | `#4ead6b22` |
| Warning | `--status-warning` | `#EAA14B` | `#EAA14B22` |
| Error | `--status-error` | `#e5252e` | `#e5252e22` |
| Info | `--status-info` | `#7da3d4` | `#7da3d422` |

### Brand

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Primary | `--brand-primary` | `#e5252e` | Brand strip, logo bg |
| Color | `--brand-color` | `#7da3d4` | Secondary brand accent |

### Borders

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Default | `--border-default` | `#3a4158` | Card borders, table rows |
| Muted | `--border-muted` | `#2e3548` | Subtle dividers |
| Emphasis | `--border-emphasis` | `#464e53` | Active/focus borders, scrollbar hover |

### UI

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Divider | `--ui-divider` | `#3a4158` | Horizontal/vertical rules |

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
| 7 | 56px | — |
| 8 | 64px | Maximum spacing |

---

## Borders & Radius

| Token | CSS Variable | Value |
|-------|-------------|-------|
| Radius sm | `--radius-sm` | 4px |
| Radius md | `--radius-md` | 8px |
| Radius lg | `--radius-lg` | 12px |
| Radius full | `--radius-full` | 9999px |

Atlas Lens uses **softer radii** (4/8/12px) compared to Atlas Light/Dark (2/4/8px). The rounder corners suit the dark theme's more immersive feel — surfaces read as distinct layers rather than hard-edged tiles.

---

## Shadows

| Level | CSS Variable | CSS Value | Use |
|-------|-------------|-----------|-----|
| Low | `--shadow-low` | `0px 4px 24px -8px rgba(0,0,0,0.5), 0px 1px 6px -2px rgba(0,0,0,0.6)` | Cards, dropdowns |
| Medium | `--shadow-medium` | `0px 6px 16px -4px rgba(0,0,0,0.6), 0px 5px 8px -8px rgba(0,0,0,0.4)` | Popovers, floating panels |
| High | `--shadow-high` | `0px 10px 32px -6px rgba(0,0,0,0.7), 0px 4px 4px -2px rgba(0,0,0,0.5)` | Modals, overlays, theme switcher |

Shadows in Lens are **heavier than Light/Dark** (0.5-0.7 alpha vs 0.06-0.12). On dark backgrounds, shadows need higher opacity to register visually — the same values from Light would be invisible here.

---

## Raw CSS Custom Properties

Inject this block directly via `<style>` or CSS-in-JS. This is the full `theme_css` from atlas-lens.json.

```css
:root {
  /* Backgrounds — Atlas Lens deep navy spectrum */
  --bg-base: #1a1f2e;
  --bg-surface: #242a3a;
  --bg-elevated: #2e3548;
  --bg-overlay: #242a3a;
  --bg-inset: #141825;
  --bg-top: #141825;

  /* Borders */
  --border-default: #3a4158;
  --border-muted: #2e3548;
  --border-emphasis: #464e53;

  /* Text */
  --text-primary: #f0f2f5;
  --text-secondary: #b6b8b9;
  --text-muted: #8c8e92;
  --text-disabled: #6f7377;
  --text-inverse: #1a1f2e;

  /* Actions — Diligent red as primary action */
  --action-default: #e5252e;
  --action-hover: #cc2028;
  --action-muted: #e5252e20;
  --link-default: #7da3d4;
  --link-hover: #a0bfe0;

  /* Status */
  --status-success: #4ead6b;
  --status-success-muted: #4ead6b22;
  --status-warning: #EAA14B;
  --status-warning-muted: #EAA14B22;
  --status-error: #e5252e;
  --status-error-muted: #e5252e22;
  --status-info: #7da3d4;
  --status-info-muted: #7da3d422;

  /* Brand */
  --brand-primary: #e5252e;
  --brand-color: #7da3d4;

  /* UI */
  --ui-divider: #3a4158;

  /* Shape — from Figma: md=8px, lg=12px */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-full: 9999px;

  /* Typography — Plus Jakarta Sans from Figma */
  --font-sans: 'Plus Jakarta Sans', 'Source Sans 3', system-ui, sans-serif;

  /* Shadows */
  --shadow-low: 0px 4px 24px -8px rgba(0,0,0,0.5), 0px 1px 6px -2px rgba(0,0,0,0.6);
  --shadow-medium: 0px 6px 16px -4px rgba(0,0,0,0.6), 0px 5px 8px -8px rgba(0,0,0,0.4);
  --shadow-high: 0px 10px 32px -6px rgba(0,0,0,0.7), 0px 4px 4px -2px rgba(0,0,0,0.5);
}

@import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap');

body {
  font-family: var(--font-sans);
  background-color: var(--bg-base);
  color: var(--text-primary);
  -webkit-font-smoothing: antialiased;
}

::-webkit-scrollbar { width: 8px; height: 8px; }
::-webkit-scrollbar-track { background: var(--bg-inset); }
::-webkit-scrollbar-thumb { background: var(--border-default); border-radius: var(--radius-full); }
::-webkit-scrollbar-thumb:hover { background: var(--border-emphasis); }
```

---

## Design Principles

1. **Professional and restrained** — Muted blue-grey palette. Avoid high saturation except for status colors.
2. **Dense but readable** — Board management UIs show lots of data. Favor compact layouts with clear hierarchy.
3. **Contrast through weight, not color** — Use font weight and size to create hierarchy. Reserve color for actions and status.
4. **Depth through luminance steps** — Darker surfaces recede, lighter surfaces elevate. The background stack (`#141825` -> `#1a1f2e` -> `#242a3a` -> `#2e3548`) creates spatial depth without relying on shadows alone.
5. **Minimal elevation** — Use subtle shadows sparingly. Flat surfaces with thin dividers are preferred.

---

## Known Issues

- **Action/error color collision:** Action color (`#e5252e`) is identical to error color (`#e5252e`). CTA buttons and error states are visually indistinguishable. Flag this in designs and use contextual cues (icons, placement, copy) to disambiguate.
- **Font family divergence:** Plus Jakarta Sans Variable, different from Atlas Light/Dark which use Source Sans 3. Cross-theme font switching will cause layout reflow.
- **Border radii divergence:** Softer radii (4/8/12px) vs Light/Dark (2/4/8px). Components that hardcode radius values will look inconsistent across themes.
- **Warning text contrast:** Warning color `#EAA14B` on dark backgrounds may be difficult to read at small sizes. Consider using it only for icons/badges and using `--text-primary` for warning text labels.

---

## Component API

From the `design_instructions` field in atlas-lens.json. This documents the Atlas React component library used with this theme.

### App Shell

#### AppLayout
Top-level layout wrapper. Provides sidebar navigation and org header.

```tsx
<AppLayout navigation={<Navigation />} orgName="Connected Compliance">
  <Outlet />
</AppLayout>
```

**Props:**
- `navigation` (ReactNode) — sidebar nav content
- `orgName` (string) — organization name shown in the header
- `children` (ReactNode) — page content

#### RoutedNavLink
Sidebar navigation item. Import from `@diligentcorp/atlas-react-bundle/global-nav`.

```tsx
<RoutedNavLink to="/reports" label="Reports">
  <ReportsIcon slot="icon" />
</RoutedNavLink>
```

**Props:**
- `to` (string) — route path
- `label` (string) — nav item text
- `children` — icon element with `slot="icon"`

#### Icons
Import from `@diligentcorp/atlas-react-bundle/icons/<IconName>`. Known icons: `Home`, `ComplianceEthics`, `Reports`, `Settings`, `Text`, `BoardGroup`.

### Page Components

#### PageHeader
Page title with optional breadcrumbs and action buttons.

```tsx
<PageHeader
  pageTitle="Reports"
  pageSubtitle="Generated compliance reports"
  breadcrumbs={<OverflowBreadcrumbs ... />}
  buttonArray={<Button variant="contained">Create report</Button>}
/>
```

**Props:**
- `pageTitle` (string) — main heading
- `pageSubtitle` (string) — description below title
- `breadcrumbs` (ReactNode) — OverflowBreadcrumbs component
- `buttonArray` (ReactNode) — action buttons on the right

**DO NOT use `actions` prop — it does not exist. Use `buttonArray` for action buttons.**

#### OverflowBreadcrumbs
Breadcrumb navigation. Used inside PageHeader.

```tsx
<OverflowBreadcrumbs
  leadingElement={<NavLink to="/home">Home</NavLink>}
  items={[{ id: "reports", label: "Reports", url: "/reports" }]}
  hideLastItem
  aria-label="Breadcrumbs"
>
  {({ label, url }) => <NavLink to={url}>{label}</NavLink>}
</OverflowBreadcrumbs>
```

**Props:**
- `leadingElement` (ReactNode) — first breadcrumb
- `items` (array) — `{ id: string, label: string, url: string }[]`
- `hideLastItem` (boolean) — hide the last breadcrumb (current page)
- `aria-label` (string)
- `children` (render function) — `({ label, url }) => ReactNode`

#### StatusIndicator
Colored status badge with label.

```tsx
<StatusIndicator label="Stable" color="success" />
```

**Props:**
- `label` (string) — status text
- `color` — `"success" | "warning" | "error" | "information" | "generic"`

### AI Chat Components

All imported from `@diligentcorp/atlas-react-bundle`.

| Component | Key Props |
|-----------|-----------|
| `AIChatContextProvider` | `initialHasStartedChat` (boolean) |
| `AIChatUI` | `chatContent` (ReactNode) |
| `AIChatContent` | children = message components |
| `AIChatUserMessage` | `alignment="end"`, `message` (string), `header` (ReactNode) |
| `AIChatAIMessage` | `header` (ReactNode), children = text block or thinking indicator |
| `AIChatMessageHeader` | `name` (string), `time` (string), `avatar` (ReactNode) |
| `AIChatMessageAvatar` | `uniqueId` (string), `initials` (string) |
| `AIChatMessageTextBlock` | children = string content |
| `AIChatThinkingIndicator` | `label` (string) |
| `AIChatBox` | Input box for typing messages |

**Hook:** `useAIChatContext` returns `{ sendMessage, isGenerating }`.

### MUI Typography Variants

| Variant | Use |
|---------|-----|
| `h1`, `h2`, `h3` | Headings |
| `body1` | Body text |
| `labelSm` | Small bold label (table headers, card titles) |
| `labelXs` | Extra-small label (deltas, metadata) |
| `textSm` | Small regular text (descriptions, secondary content) |

### Layout Patterns

- Use `Container` with `sx={{ py: 3 }}` for page padding
- Use `Stack gap={3}` or `gap={4}` for vertical section spacing
- Use `Stack direction="row"` for horizontal layouts
- Use `Box` with border styling for metric cards: `border: "1px solid", borderColor: "divider", borderRadius: 2, p: 2`
- Tables: `Table size="small"` with custom cell padding via sx

### Don'ts

- **DO NOT** use `actions` prop on PageHeader — use `buttonArray`
- **DO NOT** guess at component props — only use what is documented above
- **DO NOT** hardcode colors — use CSS custom properties (`var(--text-primary)`, `var(--bg-surface)`, etc.) or MUI theme palette
- **DO NOT** import components from paths not shown here
- **DO NOT** use `@mui/icons-material` — use Atlas icons from `@diligentcorp/atlas-react-bundle/icons/<Name>`
