# Atlas Light Design System

**Theme:** Atlas Light -- Clean, institutional light theme. White backgrounds, sea-palette actions, Source Sans Pro.
**Source:** Generated from atlas-light.json + DESIGN.md editorial content.
**Token version:** @diligentcorp/atlas-design-tokens v0.29.20

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

**Weights:** Light 300 / Regular 400 / Emphasis 600 / Bold 700

**Labels:** Uppercase, 1px letter-spacing, 0.75rem size, 0.8125rem line-height.

---

## Color Palette

### Backgrounds

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Base | `--bg-base` | `#f4f6f8` | Page background |
| Surface | `--bg-surface` | `#ffffff` | Cards, panel surfaces |
| Elevated | `--bg-elevated` | `#eef2f6` | Raised surfaces, hover fills |
| Overlay | `--bg-overlay` | `#ffffff` | Modal/popover background |
| Inset | `--bg-inset` | `#e4eef6` | Recessed areas, well backgrounds |
| Top | `--bg-top` | `#2F3B4D` | Top navigation bar |
| Status bar | `--bg-status-bar` | `#202935` | Status bar (darkest) |

### Text

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Primary | `--text-primary` | `#1e1e1e` | Body text, headings |
| Secondary | `--text-secondary` | `#676767` | Muted text, descriptions |
| Muted | `--text-muted` | `#949494` | Placeholder, captions |
| Disabled | `--text-disabled` | `#b3b3b3` | Disabled elements |
| Inverse | `--text-inverse` | `#ffffff` | Text on dark backgrounds |

### Actions

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Default | `--action-default` | `#455D82` | Primary buttons, CTAs |
| Hover | `--action-hover` | `#364262` | Button hover state |
| Active | `--action-active` | `#252C44` | Button pressed state |
| Disabled | `--action-disabled` | `#D5E3F1` | Disabled buttons |
| Muted | `--action-muted` | `#455D8218` | Ghost button background |

### Links

| Token | Variable | Hex |
|-------|----------|-----|
| Default | `--link-default` | `#385F99` |
| Hover | `--link-hover` | `#294772` |

### Status

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Success | `--status-success` | `#05704B` | Confirmations, completed |
| Success muted | `--status-success-muted` | `#05704B18` | Success badge background |
| Warning | `--status-warning` | `#935206` | Warning text (high contrast) |
| Warning muted | `--status-warning-muted` | `#EAA14B20` | Warning badge background |
| Error | `--status-error` | `#AF292E` | Errors, validation failures |
| Error muted | `--status-error-muted` | `#AF292E15` | Error badge background |
| Info | `--status-info` | `#385F99` | Informational banners |
| Info muted | `--status-info-muted` | `#385F9918` | Info badge background |
| New | `--status-new` | `#E71613` | Notification badges |

### Destructive

| Token | Variable | Hex |
|-------|----------|-----|
| Default | `--destructive-default` | `#AF292E` |
| Hover | `--destructive-hover` | `#821F22` |

### Brand

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Primary | `--brand-primary` | `#EE312E` | Diligent red accent, brand strip |
| Secondary | `--brand-secondary` | `#AF292E` | Secondary brand touches |
| Color | `--brand-color` | `#2F3B4D` | Brand text, nav background |

### Accents (decorative, soft fills)

| # | Variable | Hex | Name |
|---|----------|-----|------|
| 01 | `--accent-01` | `#a5ccec` | Sail |
| 02 | `--accent-02` | `#c0dbd1` | Sea Green |
| 03 | `--accent-03` | `#efb5b5` | Jaguar Rose |
| 04 | `--accent-04` | `#f1c189` | Italian Sunset |
| 05 | `--accent-05` | `#c1c1c1` | Stonewall Grey |

### Borders

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Default | `--border-default` | `#e6e6e6` | Standard border |
| Muted | `--border-muted` | `#e4eef6` | Subtle border, inset edges |
| Emphasis | `--border-emphasis` | `#b7cce1` | Emphasized or active borders |

### UI

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Divider | `--ui-divider` | `#e6e6e6` | Horizontal/vertical rules |
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

| Token | Variable | Value |
|-------|----------|-------|
| Radius sm | `--radius-sm` | 2px |
| Radius md | `--radius-md` | 4px |
| Radius lg | `--radius-lg` | 8px |
| Radius full | `--radius-full` | 9999px |
| Border thin | -- | 1px |
| Border thick | -- | 2px |
| Focus width | -- | 2px |
| Focus offset | -- | 1px |

Atlas uses **tight radii** (2-4px). This is a conservative, professional aesthetic -- avoid rounded corners beyond 4px unless intentionally breaking the pattern for emphasis.

---

## Shadows

| Level | Variable | CSS | Use |
|-------|----------|-----|-----|
| Low | `--shadow-low` | `0px 4px 24px -8px #00000010, 0px 1px 6px -2px #00000038` | Cards, dropdowns |
| Medium | `--shadow-medium` | `0px 6px 16px -4px #00000020, 0px 5px 8px -8px #00000008` | Popovers, floating panels |
| High | `--shadow-high` | `0px 10px 32px -6px #00000020, 0px 4px 4px -2px #00000008` | Modals, overlays |

Shadows are **subtle and diffuse** -- not heavy drop shadows. The aesthetic is clean and lifted, not skeuomorphic.

---

## Raw CSS Custom Properties

The complete `:root` / `[data-theme="atlas-light"]` block. Inject directly into your page via `<style>` or CSS import.

```css
[data-theme="atlas-light"], :root {
  --bg-base: #f4f6f8;
  --bg-surface: #ffffff;
  --bg-elevated: #eef2f6;
  --bg-overlay: #ffffff;
  --bg-inset: #e4eef6;
  --bg-top: #2F3B4D;
  --bg-status-bar: #202935;

  --border-default: #e6e6e6;
  --border-muted: #e4eef6;
  --border-emphasis: #b7cce1;

  --text-primary: #1e1e1e;
  --text-secondary: #676767;
  --text-muted: #949494;
  --text-disabled: #b3b3b3;
  --text-inverse: #ffffff;

  --action-default: #455D82;
  --action-hover: #364262;
  --action-active: #252C44;
  --action-disabled: #D5E3F1;
  --action-muted: #455D8218;

  --link-default: #385F99;
  --link-hover: #294772;

  --status-success: #05704B;
  --status-success-muted: #05704B18;
  --status-warning: #935206;
  --status-warning-muted: #EAA14B20;
  --status-error: #AF292E;
  --status-error-muted: #AF292E15;
  --status-info: #385F99;
  --status-info-muted: #385F9918;
  --status-new: #E71613;

  --destructive-default: #AF292E;
  --destructive-hover: #821F22;

  --accent-01: #a5ccec;
  --accent-02: #c0dbd1;
  --accent-03: #efb5b5;
  --accent-04: #f1c189;
  --accent-05: #c1c1c1;

  --brand-primary: #EE312E;
  --brand-secondary: #AF292E;
  --brand-color: #2F3B4D;

  --ui-divider: #e6e6e6;
  --ui-focus-ring: #3e95fa;

  --shadow-low: 0px 4px 24px -8px #00000010, 0px 1px 6px -2px #00000038;
  --shadow-medium: 0px 6px 16px -4px #00000020, 0px 5px 8px -8px #00000008;
  --shadow-high: 0px 10px 32px -6px #00000020, 0px 4px 4px -2px #00000008;

  --radius-sm: 2px;
  --radius-md: 4px;
  --radius-lg: 8px;
  --radius-full: 9999px;

  --font-sans: 'Source Sans 3', 'Source Sans Pro', ui-sans-serif, system-ui, sans-serif;
}
```

---

## Design Principles

1. **Professional and restrained** -- Muted blue-grey palette. Avoid high saturation except for status colors.
2. **Dense but readable** -- Board management UIs show lots of data. Favor compact layouts with clear hierarchy.
3. **Contrast through weight, not color** -- Use font weight and size to create hierarchy. Reserve color for actions and status.
4. **Dark top, light content** -- The `#2F3B4D` top nav anchors the page. Content area is `#f4f6f8` with `#ffffff` cards.
5. **Minimal elevation** -- Use subtle shadows sparingly. Flat surfaces with thin dividers are preferred.

---

## Component API

From `@diligentcorp/atlas-react-bundle` with MUI. Only use documented props below -- do not guess.

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
**WARNING:** Do NOT use an `actions` prop -- it does not exist. Use `buttonArray`.

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

All from `@diligentcorp/atlas-react-bundle`.

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
| `AIChatBox` | Input box inside AIChatUI |
| `useAIChatContext` | Returns `{ sendMessage, isGenerating }` |

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

### Common Mistakes to Avoid

- Do NOT use `actions` prop on PageHeader -- use `buttonArray`
- Do NOT guess at component props -- only use what is documented above
- Do NOT hardcode colors -- use MUI theme palette (`text.primary`, `text.secondary`, `divider`)
- Do NOT import from undocumented paths
- Do NOT use `@mui/icons-material` -- use Atlas icons from `@diligentcorp/atlas-react-bundle/icons/<Name>`
