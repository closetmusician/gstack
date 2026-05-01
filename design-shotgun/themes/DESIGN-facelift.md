# Diligent Boards Facelift Design System

**Theme:** Facelift Light — Warm institutional with modern roundness. Cool grey-blue backgrounds, muted navy actions, generous card radii, translucent top bar.
**Source:** Reverse-engineered from director.diligentboards.com/home/homepage computed styles and CSS custom properties.
**Token version:** Angular Material (mat/mdc tokens) with `.facelift-theme` overrides. Spacing base: 4px.

---

## Typography

**Font family:** `'Source Sans Pro', Avenir, Calibri, Helvetica, 'Droid Sans', sans-serif`
(from body computed style)

| Scale | Size | Line height | Weight | Use for |
|-------|------|-------------|--------|---------|
| Section heading | 1rem (16px) | 1.5rem (24px) | 600 | Section headers ("Awaiting review", "Books and reports") |
| Body | 1rem (16px) | 1.5rem (24px) | 400 | Default text, nav items, org name |
| Active nav label | 1rem (16px) | 1.25rem (20px) | 600 | Active sidebar nav item ("Home") |
| Nav label | 1rem (16px) | 1.25rem (20px) | 400 | Inactive sidebar nav items |
| Book title | 1rem (16px) | 1.5rem (24px) | 600 | Card title links (book names) |
| Secondary text | 0.875rem (14px) | 1.375rem (22px) | 400 | Meeting metadata, article source, dates |
| Button text | 0.875rem (14px) | 1.5rem (24px) | 600 | Outlined buttons ("Open book", "Load more") |
| News body | 0.875rem (14px) | 1.1rem (17.6px) | 400 | Article excerpt paragraphs |
| Announcement body | 0.8125rem (13px) | normal | 400 | Announcement detail text |
| Badge count | 0.75rem (12px) | 1.125rem (18px) | 600 | Notification count badges |
| Small text | 0.75rem (12px) | 1.125rem (18px) | 400 | Overflow counts ("+6"), fine print |

**Weights:** Regular 400 / Semibold 600 (only two weights observed in use).

**Note:** Unlike Atlas (which has a Billboard/Display/Title hierarchy), the facelift theme is flat — almost everything is 16px or 14px, differentiated by weight alone. No large display or heading sizes observed on the homepage.

---

## Color Palette

### Backgrounds

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Page | `--mat-sidenav-content-background-color` | `#f5f8f9` | Main content area background |
| Side nav | (computed) | `#edf2f3` | Side navigation panel |
| Surface | (computed) | `#ffffff` | Cards, panels, active nav item, top bar |
| Top bar | (computed) | `#ffffff70` | Top navigation bar (70% opacity white) |
| Announcement | (computed) | `#e4eef6` | Announcement banner background |
| AI chip | (computed) | `#f3f3f3` | "Articles summarized by AI" chip |
| New badge bg | (computed) | `#f7f9fb` | "New" badge background on book cards |
| Stay ahead | (computed) | `#faf9f5` | "Stay ahead" education section background |
| App fallback | `--mat-app-background-color` | `#fafafa` | Material app-level fallback |

### Text

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Primary | (computed) | `#1e1e1e` | Body text, section headings |
| Material default | `--mat-app-text-color` | `rgba(0,0,0,0.87)` | Material default text, nav links |
| Secondary | (computed) | `#676767` | Org name subtitle, dates, metadata |
| Muted | (computed) | `#949494` | Placeholder text |
| Disabled | (computed) | `#b3b3b3` | Disabled text |
| Inverse | (computed) | `#ffffff` | Text on badge backgrounds, tooltips |

### Actions / Interactive

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Default | (computed) | `#455d82` | Icons, outlined button text/border, active tab, chevrons |
| Secondary | `--mat-option-selected-state-label-text-color` | `#5d7599` | Form field caret, progress indicator, selected option |
| Brand dark | `--mat-full-pseudo-checkbox-selected-icon-color` | `#2f3b4d` | Checkbox fill, brand color |

### Links

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Default | (computed) | `#385f99` | Article titles, book titles, inline links, inactive tabs |
| Announcement | (computed) | `#2162e4` | Announcement heading text (bright blue) |

### Brand

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Red | (computed) | `#d3222a` | Notification badges, active "Home" icon tint |
| Gradient start | (computed) | `#d3222a` | News section gradient (red) |
| Gradient mid | (computed) | `#b646f6` | News section gradient (purple) |
| Gradient end | (computed) | `#4d1dd5` | News section gradient (deep purple) |

**Decorative gradient:** `linear-gradient(65.28deg, #d3222a, #b646f6 54.97%, #4d1dd5 80.25%)` — used as a 30px strip above the News and Insights card. The strongest visual flourish in the UI.

### Borders

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Default | (computed) | `#e6e6e6` | Card borders, sidenav edge, top bar bottom, rules |
| Emphasis | (computed) | `#b7cce1` | Outlined button border ("Open book", "Load more") |
| Checkbox | (computed) | `#a0a2a5` | Unchecked checkbox border |

### Status

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Focus | `--strong-focus-color` | `#0774ee` | Strong keyboard focus indicator |

### Tooltip

| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Background | `--mdc-plain-tooltip-container-color` | `#282e37` | Tooltip background |
| Text | `--mdc-plain-tooltip-supporting-text-color` | `#ffffff` | Tooltip text |

---

## Spacing

4px base unit (`--spacing-base: 4`). Variables follow `--s{N}` pattern where value = N x 4px.

| Token | Value | Common use |
|-------|-------|-----------|
| --s1 | 4px | Hairline gaps, top bar vertical padding |
| --s2 | 8px | Tight padding |
| --s3 | 12px | Announcement internal padding, top bar horizontal, button padding |
| --s4 | 16px | Card padding, tab horizontal padding |
| --s5 | 20px | Generous padding |
| --s6 | 24px | Section spacing |
| --s7 | 28px | — |
| --s8 | 32px | Large section breaks |
| ... | ... | Continues to --s30 (120px) |

**Note:** Atlas uses an 8px base. This theme uses 4px, giving finer-grained control but also more tokens in the spacing scale.

---

## Borders & Radius

| Token | Value | Use |
|-------|-------|-----|
| Cards | 16px | Book cards, announcement banner, news section, todo card |
| Buttons | 8px | Outlined buttons, search wrapper, GovernAI chip |
| Search field | 5px | Search form field wrapper |
| Nav active item | 4px | Active sidebar link background |
| Tooltip | 4px | Plain tooltip container |
| Material card | 4px | `--mdc-elevated-card-container-shape`, `--mdc-outlined-card-container-shape` |
| Badge | 50% (circle) | Notification count badges |
| Border width | 1px | Card borders, sidenav edge, top bar border-bottom |

**KEY DIFFERENCE from Atlas Light:** Atlas uses tight 2-4px radii (conservative, professional). This facelift theme uses generous **16px radii on cards** and **8px on buttons**, creating a significantly more modern, friendly appearance. This is the single biggest visual differentiator between the two themes.

---

## Shadows

| Level | CSS | Use |
|-------|-----|-----|
| Card | `rgb(237, 242, 243) 0px 4px 6px 0px` | Book cards, todo card — soft cool-grey |
| Material Level 0 | `0px 0px 0px 0px rgba(0,0,0,.2), ...` | No elevation |
| Material Level 1 | `0px 2px 1px -1px rgba(0,0,0,.2), 0px 1px 1px 0px rgba(0,0,0,.14), 0px 1px 3px 0px rgba(0,0,0,.12)` | Standard Material elevation 1 |
| Material Level 2 | `0px 3px 1px -2px rgba(0,0,0,.2), 0px 2px 2px 0px rgba(0,0,0,.14), 0px 1px 5px 0px rgba(0,0,0,.12)` | Material elevation 2 |

Shadows are **subtle and tinted with cool grey** (`#edf2f3`) rather than pure black, creating a soft, lifted effect. The card shadow is particularly distinctive — a single diffuse cool-grey wash, not the multi-layer approach in Atlas.

---

## Layout

| Component | Value | Notes |
|-----------|-------|-------|
| Top bar height | 55px | Translucent white (`#ffffff70`), 1px solid `#e6e6e6` bottom border |
| Side nav width | 300px (expanded) | Background `#edf2f3`, right border 1px solid `#e6e6e6` |
| Content area | Fills remaining width | Background `#f5f8f9`, no padding (sections handle own) |
| Left column | ~60% of content width | Announcement, todos, book cards |
| Right column | ~40% of content width | News and insights, education, stay ahead |

---

## Raw CSS Custom Properties

The key custom properties powering this theme. Inject via `<style>` or CSS import.

```css
:root, .facelift-theme {
  /* Spacing base */
  --spacing-base: 4;
  --s1: calc(var(--spacing-base) * 1px);  /* 4px */
  --s2: calc(var(--spacing-base) * 2px);  /* 8px */
  --s3: calc(var(--spacing-base) * 3px);  /* 12px */
  --s4: calc(var(--spacing-base) * 4px);  /* 16px */
  --s5: calc(var(--spacing-base) * 5px);  /* 20px */
  --s6: calc(var(--spacing-base) * 6px);  /* 24px */
  --s8: calc(var(--spacing-base) * 8px);  /* 32px */

  /* Backgrounds */
  --bg-base: #f5f8f9;
  --bg-surface: #ffffff;
  --bg-sidenav: #edf2f3;
  --bg-topbar: #ffffff70;
  --bg-announcement: #e4eef6;
  --bg-ai-chip: #f3f3f3;
  --bg-new-badge: #f7f9fb;
  --bg-stay-ahead: #faf9f5;

  /* Text */
  --text-primary: #1e1e1e;
  --text-secondary: #676767;
  --text-muted: #949494;
  --text-disabled: #b3b3b3;
  --text-inverse: #ffffff;

  /* Actions */
  --action-default: #455d82;
  --action-secondary: #5d7599;
  --action-brand: #2f3b4d;

  /* Links */
  --link-default: #385f99;
  --link-announcement: #2162e4;

  /* Brand */
  --brand-red: #d3222a;
  --brand-gradient: linear-gradient(65.28deg, #d3222a, #b646f6 54.97%, #4d1dd5 80.25%);

  /* Borders */
  --border-default: #e6e6e6;
  --border-emphasis: #b7cce1;
  --border-checkbox: #a0a2a5;

  /* Focus */
  --strong-focus-color: #0774ee;

  /* Material overrides */
  --mat-app-background-color: #fafafa;
  --mat-app-text-color: rgba(0, 0, 0, .87);
  --mat-sys-on-surface: #0e0e0e;
  --mat-sidenav-content-background-color: #f5f8f9;
  --mat-list-active-indicator-color: white;
  --mdc-filled-text-field-caret-color: #5d7599;
  --mdc-filled-text-field-focus-active-indicator-color: #5d7599;
  --mat-option-selected-state-label-text-color: #5d7599;
  --mat-option-label-text-color: rgba(0, 0, 0, .87);
  --mat-full-pseudo-checkbox-selected-icon-color: #2f3b4d;
  --mat-full-pseudo-checkbox-selected-checkmark-color: #1e1e1e;
  --mat-full-pseudo-checkbox-unselected-icon-color: #a0a2a5;
  --mdc-checkbox-selected-focus-icon-color: #2f3b4d;
  --mdc-plain-tooltip-container-color: #282e37;
  --mdc-plain-tooltip-supporting-text-color: #fff;
  --mdc-plain-tooltip-container-shape: 4px;
  --mdc-plain-tooltip-supporting-text-line-height: 1.6rem;
  --mdc-elevated-card-container-shape: 4px;
  --mdc-outlined-card-container-shape: 4px;
  --mdc-outlined-card-outline-width: 1px;
  --mat-ripple-color: rgba(0, 0, 0, .1);

  /* Shadows */
  --shadow-card: rgb(237, 242, 243) 0px 4px 6px 0px;
  --mat-app-elevation-shadow-level-0: 0px 0px 0px 0px rgba(0,0,0,.2), 0px 0px 0px 0px rgba(0,0,0,.14), 0px 0px 0px 0px rgba(0,0,0,.12);
  --mat-app-elevation-shadow-level-1: 0px 2px 1px -1px rgba(0,0,0,.2), 0px 1px 1px 0px rgba(0,0,0,.14), 0px 1px 3px 0px rgba(0,0,0,.12);
  --mat-app-elevation-shadow-level-2: 0px 3px 1px -2px rgba(0,0,0,.2), 0px 2px 2px 0px rgba(0,0,0,.14), 0px 1px 5px 0px rgba(0,0,0,.12);

  /* Radius */
  --radius-card: 16px;
  --radius-button: 8px;
  --radius-search: 5px;
  --radius-nav-active: 4px;
  --radius-tooltip: 4px;
  --radius-badge: 50%;
}
```

---

## Component Patterns

### Top Bar
Translucent white bar with bottom border. Contains search, notification/messenger icons, account menu.
- Background: `rgba(255, 255, 255, 0.7)`
- Height: 55px
- Padding: 4px 12px
- Border bottom: 1px solid `#e6e6e6`

### Side Navigation
Cool grey panel with white active-item highlight and red icon accent for the active route.
- Background: `#edf2f3`
- Width: 300px (expanded)
- Right border: 1px solid `#e6e6e6`
- Active item background: `#ffffff` with border-radius: 4px
- Active icon color: `#d3222a` (brand red)
- Inactive icon color: `#455d82`
- Nav item font: 16px / 400, color `rgba(0,0,0,0.87)`
- Active nav item font: 16px / 600

### Cards (Book cards, Todo card)
White surface cards with soft cool-grey shadow and generous radius.
- Background: `#ffffff`
- Border: 1px solid `#e6e6e6`
- Border radius: 16px
- Shadow: `rgb(237, 242, 243) 0px 4px 6px 0px`
- Padding: 16px

### Announcement Banner
Light blue inset banner for system announcements.
- Background: `#e4eef6`
- Border radius: 16px
- Padding: 12px
- Title color: `#2162e4` (bright blue), 16px / 600

### Outlined Buttons ("Open book", "Load more")
Ghost/outlined style with navy text and blue-grey border.
- Background: transparent
- Color: `#455d82`
- Border: 1px solid `#b7cce1`
- Border radius: 8px
- Padding: 0px 16px
- Font: 14px / 600, text-transform: none

### Notification Badges
Small red circular badges for unread counts.
- Background: `#d3222a`
- Text: `#ffffff`
- Font: 12px / 600
- Border radius: 50%

### Tabs
Flat tab bar with color-differentiated active/inactive labels.
- Active tab label: color `#455d82`, weight 600
- Inactive tab label: color `#385f99`, weight 400
- Active indicator: `#455d82` underline
- Tab padding: 0px 16px

### News and Insights Card
White card with a decorative gradient strip above it.
- Gradient element: 30px tall, border-radius: 16px, positioned above the card
- Gradient: `linear-gradient(65.28deg, #d3222a, #b646f6 54.97%, #4d1dd5 80.25%)`
- Card: white, border-radius: 16px, padding: 16px
- Article title links: `#385f99`, 14px
- Source text: `#1e1e1e`, 14px / 400
- Date text: `#676767`, 14px / 400

### Search Field
White input field embedded in the top bar.
- Wrapper background: `#ffffff`
- Border radius: 8px (outer), 5px (form field)
- Height: 40px
- Font: 16px

---

## Design Principles

1. **Warm institutional with modern roundness** — Cool blue-grey base palette with generous 16px card radii, a departure from sharp corporate edges.
2. **Flat with soft shadows** — Cards use a single diffuse cool-grey shadow (`#edf2f3`), not heavy Material drop shadows. Lifted but not dramatic.
3. **Translucent top bar** — Top navigation uses 70% opacity white, allowing content to softly show through when scrolled.
4. **Color-coded interactivity** — Navy (`#455d82`) for interactive elements, medium blue (`#385f99`) for links, brand red (`#d3222a`) for active state highlights and notifications.
5. **4px spacing grid** — All spacing derives from a 4px base unit, used consistently across padding, margins, and gaps.
6. **Light side nav, not dark** — Unlike Atlas Light (dark `#2F3B4D` top nav), this theme uses a light grey (`#edf2f3`) side nav with white active item highlights.
7. **Brand gradient as accent** — The red-to-purple gradient on the News card is the strongest visual flourish; the rest of the UI is restrained.

---

## Key Differences from Atlas Light

| Dimension | Atlas Light | Facelift |
|-----------|------------|----------|
| Card radius | 2-4px (tight, conservative) | **16px** (generous, modern) |
| Button radius | 2-4px | **8px** |
| Spacing base | 8px | **4px** (finer-grained) |
| Top nav | Dark `#2F3B4D` solid bar | **Translucent white** (`#ffffff70`) |
| Side nav | — | Light grey `#edf2f3` with white active items |
| Shadows | Multi-layer, semi-transparent black | **Single cool-grey wash** (`#edf2f3` tinted) |
| Typography scale | Billboard → Display → Title hierarchy | **Flat** — mostly 16px/14px, weight-differentiated |
| Brand accent | Thin `#EE312E` strip at top | **Red-purple gradient** on News card |
| Brand red | `#EE312E` | `#d3222a` |
| Font family | Source Sans 3 | Source Sans Pro (older family name) |
