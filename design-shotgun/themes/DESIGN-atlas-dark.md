# Atlas Dark Design System

**Theme:** Atlas Dark -- Dark variant with sea-800/900 backgrounds. High-contrast, optimized for data-rich interfaces.
**Source:** Generated from `atlas-dark.json` + `DESIGN.md` editorial content.
**Token version:** `@diligentcorp/atlas-design-tokens` v0.29.20

---

## Typography

**Font family:** `'Source Sans 3', 'Source Sans Pro', ui-sans-serif, system-ui, sans-serif`
(from `--font-sans` token)

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

**Weights:** Light 300 / Regular 400 / Emphasis 600 / Bold-Link 700

**Labels:** Uppercase, 1px letter-spacing, 0.75rem size, 0.8125rem line-height.

---

## Color Palette

### Backgrounds

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Base | `--bg-base` | `#161B2B` | Page background (sea-900) |
| Surface | `--bg-surface` | `#1e2538` | Card/panel surfaces |
| Elevated | `--bg-elevated` | `#252C44` | Elevated panels, modals |
| Overlay | `--bg-overlay` | `#1e2538` | Overlay/backdrop surfaces |
| Inset | `--bg-inset` | `#111620` | Recessed areas, input fields |
| Top | `--bg-top` | `#111620` | Top nav bar |
| Status bar | `--bg-status-bar` | `#0d1018` | Status bar (deepest dark) |

### Text

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Primary | `--text-primary` | `#F5F8F9` | Body text, headings |
| Secondary | `--text-secondary` | `#B7CCE1` | Descriptions, supporting text |
| Muted | `--text-muted` | `#8AA8C7` | Placeholders, captions |
| Disabled | `--text-disabled` | `#455D82` | Disabled labels |
| Inverse | `--text-inverse` | `#161B2B` | Text on light/action backgrounds |

### Actions

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Default | `--action-default` | `#8AA8C7` | Primary buttons, CTAs |
| Hover | `--action-hover` | `#B7CCE1` | Button hover state |
| Active | `--action-active` | `#D5E3F1` | Button pressed state |
| Disabled | `--action-disabled` | `#364262` | Disabled buttons |
| Muted | `--action-muted` | `#8AA8C722` | Ghost/subtle action fills |

### Links

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Default | `--link-default` | `#8AA8C7` | Inline links |
| Hover | `--link-hover` | `#B7CCE1` | Link hover state |

### Status

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Success | `--status-success` | `#4ead6b` | Confirmations, completed |
| Success muted | `--status-success-muted` | `#4ead6b22` | Success background fill |
| Warning | `--status-warning` | `#EAA14B` | Alerts, attention |
| Warning muted | `--status-warning-muted` | `#EAA14B22` | Warning background fill |
| Error | `--status-error` | `#e05458` | Errors, failures |
| Error muted | `--status-error-muted` | `#e0545822` | Error background fill |
| Info | `--status-info` | `#6790cc` | Informational banners |
| Info muted | `--status-info-muted` | `#6790cc22` | Info background fill |
| New | `--status-new` | `#E71613` | Notification badges |

### Destructive

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Default | `--destructive-default` | `#e05458` | Delete buttons, danger actions |
| Hover | `--destructive-hover` | `#c94040` | Destructive hover state |

### Brand

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Primary | `--brand-primary` | `#EE312E` | Diligent red, brand strip |
| Secondary | `--brand-secondary` | `#e05458` | Secondary brand accent |
| Color | `--brand-color` | `#B7CCE1` | Brand-tinted text/icons |

### Accents (decorative, charts)

| # | CSS Variable | Hex | Use |
|---|-------------|-----|-----|
| 01 | `--accent-01` | `#6790cc` | Bashful Blue -- primary data color |
| 02 | `--accent-02` | `#4ead6b` | Green accent |
| 03 | `--accent-03` | `#e05458` | Red accent |
| 04 | `--accent-04` | `#EAA14B` | Warm accent |
| 05 | `--accent-05` | `#8AA8C7` | Cool neutral accent |

### Borders

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Default | `--border-default` | `#364262` | Card borders, table rules |
| Muted | `--border-muted` | `#252C44` | Subtle dividers |
| Emphasis | `--border-emphasis` | `#455D82` | High-contrast borders |

### UI

| Token | CSS Variable | Hex | Use |
|-------|-------------|-----|-----|
| Divider | `--ui-divider` | `#364262` | Horizontal/vertical rules |
| Focus ring | `--ui-focus-ring` | `#3e95fa` | Keyboard focus indicator |

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

| Token | CSS Variable | Value |
|-------|-------------|-------|
| Radius sm | `--radius-sm` | 2px |
| Radius md | `--radius-md` | 4px |
| Radius lg | `--radius-lg` | 8px |
| Radius full | `--radius-full` | 9999px |
| Border thin | -- | 1px |
| Border thick | -- | 2px |
| Focus width | -- | 2px |
| Focus offset | -- | 1px |

Atlas uses **tight radii** (2-4px). This is a conservative, professional aesthetic -- avoid rounded corners beyond 4px unless intentionally breaking the pattern for emphasis. `--radius-lg` (8px) is available for larger containers like modals and panels.

---

## Shadows

Dark themes use **heavier shadow opacity** to maintain depth perception against dark backgrounds.

| Level | CSS Variable | CSS Value | Use |
|-------|-------------|-----------|-----|
| Low | `--shadow-low` | `0px 4px 24px -8px rgba(0,0,0,0.4), 0px 1px 6px -2px rgba(0,0,0,0.5)` | Cards, dropdowns |
| Medium | `--shadow-medium` | `0px 6px 16px -4px rgba(0,0,0,0.5), 0px 5px 8px -8px rgba(0,0,0,0.3)` | Popovers, floating panels |
| High | `--shadow-high` | `0px 10px 32px -6px rgba(0,0,0,0.6), 0px 4px 4px -2px rgba(0,0,0,0.4)` | Modals, overlays |

Note: compared to the light theme (`rgba(0,0,0,0.06-0.12)`), atlas-dark shadows use `rgba(0,0,0,0.3-0.6)` -- roughly 5x more opaque -- to remain visible against dark surfaces.

---

## Raw CSS Custom Properties

Inject this block directly via `<style>` or import. The `:root` selector applies atlas-dark as the default theme.

```css
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+3:ital,wght@0,300;0,400;0,600;0,700;1,400&display=swap');

:root {

  /* Backgrounds */
  --bg-base: #161B2B;
  --bg-surface: #1e2538;
  --bg-elevated: #252C44;
  --bg-overlay: #1e2538;
  --bg-inset: #111620;
  --bg-top: #111620;
  --bg-status-bar: #0d1018;

  /* Borders */
  --border-default: #364262;
  --border-muted: #252C44;
  --border-emphasis: #455D82;

  /* Text */
  --text-primary: #F5F8F9;
  --text-secondary: #B7CCE1;
  --text-muted: #8AA8C7;
  --text-disabled: #455D82;
  --text-inverse: #161B2B;

  /* Actions */
  --action-default: #8AA8C7;
  --action-hover: #B7CCE1;
  --action-active: #D5E3F1;
  --action-disabled: #364262;
  --action-muted: #8AA8C722;

  /* Links */
  --link-default: #8AA8C7;
  --link-hover: #B7CCE1;

  /* Status */
  --status-success: #4ead6b;
  --status-success-muted: #4ead6b22;
  --status-warning: #EAA14B;
  --status-warning-muted: #EAA14B22;
  --status-error: #e05458;
  --status-error-muted: #e0545822;
  --status-info: #6790cc;
  --status-info-muted: #6790cc22;
  --status-new: #E71613;

  /* Destructive */
  --destructive-default: #e05458;
  --destructive-hover: #c94040;

  /* Accents */
  --accent-01: #6790cc;
  --accent-02: #4ead6b;
  --accent-03: #e05458;
  --accent-04: #EAA14B;
  --accent-05: #8AA8C7;

  /* Brand */
  --brand-primary: #EE312E;
  --brand-secondary: #e05458;
  --brand-color: #B7CCE1;

  /* UI */
  --ui-divider: #364262;
  --ui-focus-ring: #3e95fa;

  /* Shadows */
  --shadow-low: 0px 4px 24px -8px rgba(0,0,0,0.4), 0px 1px 6px -2px rgba(0,0,0,0.5);
  --shadow-medium: 0px 6px 16px -4px rgba(0,0,0,0.5), 0px 5px 8px -8px rgba(0,0,0,0.3);
  --shadow-high: 0px 10px 32px -6px rgba(0,0,0,0.6), 0px 4px 4px -2px rgba(0,0,0,0.4);

  /* Radius */
  --radius-sm: 2px;
  --radius-md: 4px;
  --radius-lg: 8px;
  --radius-full: 9999px;

  /* Typography */
  --font-sans: 'Source Sans 3', 'Source Sans Pro', ui-sans-serif, system-ui, sans-serif;

}

/* Global styles */
body {
  font-family: var(--font-sans);
  background-color: var(--bg-base);
  color: var(--text-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Scrollbar styling */
::-webkit-scrollbar { width: 8px; height: 8px; }
::-webkit-scrollbar-track { background: var(--bg-inset); }
::-webkit-scrollbar-thumb { background: var(--border-default); border-radius: var(--radius-full); }
::-webkit-scrollbar-thumb:hover { background: var(--border-emphasis); }
```

---

## Design Principles

1. **Professional and restrained** -- Muted blue-grey palette. Avoid high saturation except for status colors.
2. **Dense but readable** -- Board management UIs show lots of data. Favor compact layouts with clear hierarchy.
3. **Contrast through weight, not color** -- Use font weight and size to create hierarchy. Reserve color for actions and status.
4. **Depth through luminance steps** -- Darker surfaces recede, lighter surfaces elevate. The luminance ladder runs from `--bg-status-bar` (#0d1018) through `--bg-base` (#161B2B) up to `--bg-elevated` (#252C44). Cards and modals float by being lighter than their background, not by shadow alone.
5. **Minimal elevation** -- Use subtle shadows sparingly. Flat surfaces with thin dividers are preferred. On dark themes, shadows need higher opacity to remain perceptible (see Shadows section).

---

## Component API

Reference for `@diligentcorp/atlas-react-bundle` with MUI. Only use the props documented here -- do not guess at undocumented props.

### App Shell

**AppLayout** -- Top-level layout wrapper with sidebar navigation and org header.
```tsx
<AppLayout navigation={<Navigation />} orgName="Connected Compliance">
  <Outlet />
</AppLayout>
```
Props: `navigation` (ReactNode), `orgName` (string), `children` (ReactNode).

**RoutedNavLink** -- Sidebar nav item. Import from `@diligentcorp/atlas-react-bundle/global-nav`.
```tsx
<RoutedNavLink to="/reports" label="Reports">
  <ReportsIcon slot="icon" />
</RoutedNavLink>
```
Props: `to` (string), `label` (string), `children` (icon with `slot="icon"`).

**Icons** -- Import from `@diligentcorp/atlas-react-bundle/icons/<IconName>`. Known: `Home`, `ComplianceEthics`, `Reports`, `Settings`, `Text`, `BoardGroup`.

### Page Components

**PageHeader** -- Page title with optional breadcrumbs and action buttons.
```tsx
<PageHeader
  pageTitle="Reports"
  pageSubtitle="Generated compliance reports"
  breadcrumbs={<OverflowBreadcrumbs ... />}
  buttonArray={<Button variant="contained">Create report</Button>}
/>
```
Props: `pageTitle` (string), `pageSubtitle` (string), `breadcrumbs` (ReactNode), `buttonArray` (ReactNode).
**DO NOT** use `actions` prop -- it does not exist. Use `buttonArray`.

**OverflowBreadcrumbs** -- Breadcrumb navigation inside PageHeader.
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
Props: `leadingElement` (ReactNode), `items` (`{ id, label, url }[]`), `hideLastItem` (boolean), `aria-label` (string), `children` (render function).

**StatusIndicator** -- Colored status badge.
```tsx
<StatusIndicator label="Stable" color="success" />
```
Props: `label` (string), `color` (`"success" | "warning" | "error" | "information" | "generic"`).

### AI Chat Components

All from `@diligentcorp/atlas-react-bundle`:

| Component | Key Props |
|-----------|-----------|
| `AIChatContextProvider` | `initialHasStartedChat` (boolean) |
| `AIChatUI` | `chatContent` (ReactNode) |
| `AIChatContent` | children = message components |
| `AIChatUserMessage` | `alignment="end"`, `message` (string), `header` (ReactNode) |
| `AIChatAIMessage` | `header` (ReactNode), children = text blocks or thinking indicator |
| `AIChatMessageHeader` | `name` (string), `time` (string), `avatar` (ReactNode) |
| `AIChatMessageAvatar` | `uniqueId` (string), `initials` (string) |
| `AIChatMessageTextBlock` | children = string |
| `AIChatThinkingIndicator` | `label` (string) |
| `AIChatBox` | Input box inside AIChatUI |

Hook: `useAIChatContext()` returns `{ sendMessage, isGenerating }`.

### MUI Typography Variants

| Variant | Use |
|---------|-----|
| `h1`, `h2`, `h3` | Headings |
| `body1` | Body text |
| `labelSm` | Small bold label (table headers, card titles) |
| `labelXs` | Extra-small label (deltas, metadata) |
| `textSm` | Small regular text (descriptions, secondary) |

### Layout Patterns

- `Container` with `sx={{ py: 3 }}` for page padding
- `Stack gap={3}` or `gap={4}` for vertical section spacing
- `Stack direction="row"` for horizontal layouts
- `Box` with `border: "1px solid", borderColor: "divider", borderRadius: 2, p: 2` for metric cards
- `Table size="small"` with custom cell padding via sx

### Do Nots

- **DO NOT** use `actions` prop on PageHeader -- use `buttonArray`
- **DO NOT** guess at component props -- only use what is documented above
- **DO NOT** hardcode colors -- use CSS custom properties (`var(--text-primary)`, etc.) or MUI theme palette
- **DO NOT** import components from paths not shown here
- **DO NOT** use `@mui/icons-material` -- use Atlas icons from `@diligentcorp/atlas-react-bundle/icons/<Name>`
