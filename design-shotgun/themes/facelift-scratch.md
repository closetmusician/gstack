# Diligent Boards Facelift Design System


Theme: Facelift Light -- Modern, institutional light theme. Cool grey-blue backgrounds, muted navy actions, Source Sans Pro.

Source: Reverse-engineered from director.diligentboards.com computed styles and .facelift-theme CSS overrides.

Token version: Angular Material (mat/mdc) with .facelift-theme class. Spacing base 4px.


---


## Typography


Font family: 'Source Sans Pro', Avenir, Calibri, Helvetica, 'Droid Sans', sans-serif

(from body computed style)


| Scale | Size | Line height | Use for |
|-------|------|-------------|---------|
| Section heading | 1rem (16px) | 1.5rem (24px) | Section headers ("Awaiting review", "Books and reports", "News and insights") |
| Body | 1rem (16px) | 1.5rem (24px) | Default text, nav items, org subtitle |
| Nav label | 1rem (16px) | 1.25rem (20px) | Sidebar navigation items |
| Book title | 1rem (16px) | 1.5rem (24px) | Card title links (book names) |
| Secondary | 0.875rem (14px) | 1.375rem (22px) | Meeting metadata, article source, dates, descriptions |
| Button | 0.875rem (14px) | 1.5rem (24px) | Button labels ("Open book", "Load more") |
| News body | 0.875rem (14px) | 1.1rem (17.6px) | Article excerpt paragraphs |
| Announcement body | 0.8125rem (13px) | normal | Announcement detail text |
| Badge / fine | 0.75rem (12px) | 1.125rem (18px) | Notification counts, overflow labels ("+6") |
| Table header | 0.875rem (14px) | 1.5rem (24px) | Table column headers |


Weights: Regular 400 / Semibold 600

Labels: No uppercase or letter-spacing transforms observed in current implementation.


---


## Color Palette


### Backgrounds


| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Page | --mat-sidenav-content-background-color | #f5f8f9 | Main content area background |
| Side nav | (computed) | #edf2f3 | Side navigation panel |
| Surface | (computed) | #ffffff | Cards, panels, active nav item |
| Top bar | (computed) | #ffffff70 | Top navigation bar (70% white) |
| Announcement | (computed) | #e4eef6 | Announcement banner background |
| Chip | (computed) | #f3f3f3 | "Articles summarized by AI" chip |
| Badge bg | (computed) | #f7f9fb | "New" badge background on book cards |
| Warm surface | (computed) | #faf9f5 | "Stay ahead" education section |
| App fallback | --mat-app-background-color | #fafafa | Material app-level fallback background |


### Text


| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Primary | (computed) | #1e1e1e | Body text, section headings, article source names |
| Material default | --mat-app-text-color | rgba(0,0,0,0.87) | Material default text, nav link text |
| Secondary | (computed) | #676767 | Org subtitle, date labels, meeting metadata |
| Muted | (computed) | #949494 | Placeholder text |
| Disabled | (computed) | #b3b3b3 | Disabled elements |
| Inverse | (computed) | #ffffff | Text on dark/colored backgrounds (badges, tooltips) |


### Actions


| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Default | --mdc-filled-button-container-color | #455d82 | Filled button bg, icon color, outlined button text, active tab label, chevrons |
| Hover/secondary | --mat-option-selected-state-label-text-color | #5d7599 | Form caret, progress bar, selected option, menu item text |
| Active/dark | --mdc-checkbox-selected-focus-icon-color | #2f3b4d | Checkbox fill, brand dark color |
| Disabled | --mdc-filled-button-disabled-container-color | rgba(93,117,153,0.4) | Disabled filled button |
| Muted | --mat-text-button-state-layer-color | #8c8e92 | Ghost button hover state |


### Links


| Token | Variable | Hex |
|-------|----------|-----|
| Default | (computed) | #385f99 |
| Hover | (computed from inactive tabs) | #385f99 |
| Announcement title | (computed) | #2162e4 |


### Brand


| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Red | (computed) | #d3222a | Notification badges, active nav icon |
| Ripple accent | --mat-text-button-ripple-color | rgba(210,44,44,0.1) | Button ripple effect |
| Dark | (computed) | #2f3b4d | Brand text, checkbox fill |
| Gradient | (computed) | linear-gradient(65.28deg, #d3222a, #b646f6 54.97%, #4d1dd5 80.25%) | News section decorative strip |


### Borders


| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Default | (computed) | #e6e6e6 | Card borders, sidenav edge, top bar bottom, dividers |
| Emphasis | (computed) | #b7cce1 | Outlined button borders |
| Checkbox | --mat-full-pseudo-checkbox-unselected-icon-color | #a0a2a5 | Unchecked checkbox/radio borders |


### Status


| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Focus ring | --strong-focus-color | #4a9dfc | Keyboard focus indicator |
| Error (form) | --mdc-filled-text-field-error-active-indicator-color | (standard red) | Form field validation error |


### Tooltip


| Token | Variable | Hex | Use |
|-------|----------|-----|-----|
| Background | --mdc-plain-tooltip-container-color | #282e37 | Tooltip background |
| Text | --mdc-plain-tooltip-supporting-text-color | #ffffff | Tooltip text |


---


## Spacing


4px base unit. Variables use --s{N} pattern where value = N × 4px.


| Token | Value | Common use |
|-------|-------|-----------|
| --s1 | 4px | Top bar vertical padding |
| --s2 | 8px | Tight gaps |
| --s3 | 12px | Announcement internal padding, top bar horizontal padding |
| --s4 | 16px | Card padding, tab horizontal padding, button horizontal padding |
| --s5 | 20px | Generous padding |
| --s6 | 24px | Section spacing, menu item spacing |
| --s7 | 28px | -- |
| --s8 | 32px | Large section breaks |
| --s10 | 40px | Page-level spacing |
| --s12 | 48px | Major section dividers |
| --s16 | 64px | Maximum spacing |


---


## Borders & Radius


| Token | Variable | Value |
|-------|----------|-------|
| Radius card | (computed) | 16px |
| Radius button | --mdc-filled-button-container-shape | 8px |
| Radius dialog | --mdc-dialog-container-shape | 1.6rem (~26px) |
| Radius search | (computed) | 8px |
| Radius nav active | (computed) | 4px |
| Radius tooltip | --mdc-plain-tooltip-container-shape | 4px |
| Radius menu | --mat-menu-container-shape | 4px |
| Radius mat card | --mdc-elevated-card-container-shape | 4px |
| Radius badge | (computed) | 50% |
| Border thin | (computed) | 1px |
| Focus width | (inferred) | 2px |


The Facelift theme uses generous radii on cards and buttons (16px / 8px), giving it a modern, friendly appearance. Material card/menu/tooltip shapes remain conservative at 4px. Dialogs use a distinctive 1.6rem radius.


---


## Shadows


| Level | Variable | CSS | Use |
|-------|----------|-----|-----|
| Card | (computed) | rgb(237, 242, 243) 0px 4px 6px 0px | Book cards, todo cards |
| Menu | --mat-menu-container-elevation-shadow | 0 6px 16px -4px rgba(0,0,0,.32), 0 5px 8px -8px rgba(0,0,0,.08) | Dropdown menus, popovers |
| Level 1 | --mat-app-elevation-shadow-level-1 | 0px 2px 1px -1px rgba(0,0,0,.2), 0px 1px 1px 0px rgba(0,0,0,.14), 0px 1px 3px 0px rgba(0,0,0,.12) | Slight elevation |
| Level 2 | --mat-app-elevation-shadow-level-2 | 0px 3px 1px -2px rgba(0,0,0,.2), 0px 2px 2px 0px rgba(0,0,0,.14), 0px 1px 5px 0px rgba(0,0,0,.12) | Moderate elevation |


Card shadows are tinted cool grey (#edf2f3) rather than black, producing a soft, diffused lift. Menu shadows are darker and more focused for clear separation.


---


## Raw CSS Custom Properties


The complete theme-defining variables. Inject via `<style>` or CSS import.
```css
.facelift-theme, :root {
  /* Spacing */
  --spacing-base: 4;
  --s1: calc(var(--spacing-base) * 1px);
  --s2: calc(var(--spacing-base) * 2px);
  --s3: calc(var(--spacing-base) * 3px);
  --s4: calc(var(--spacing-base) * 4px);
  --s5: calc(var(--spacing-base) * 5px);
  --s6: calc(var(--spacing-base) * 6px);
  --s7: calc(var(--spacing-base) * 7px);
  --s8: calc(var(--spacing-base) * 8px);
  --s10: calc(var(--spacing-base) * 10px);
  --s12: calc(var(--spacing-base) * 12px);
  --s16: calc(var(--spacing-base) * 16px);

  /* Focus */
  --strong-focus-color: #4a9dfc;

  /* App-level */
  --mat-app-background-color: #fafafa;
  --mat-app-text-color: rgba(0, 0, 0, .87);
  --mat-sys-on-surface: #0e0e0e;
  --mat-ripple-color: rgba(0, 0, 0, .1);

  /* Sidenav */
  --mat-sidenav-content-background-color: #f5f8f9;
  --mat-list-active-indicator-color: #ffffff;

  /* Toolbar */
  --mat-toolbar-container-background-color: rgba(255, 255, 255, 0.7);
  --mat-toolbar-container-text-color: #1e1e1e;

  /* Filled buttons */
  --mdc-filled-button-container-color: #455d82;
  --mdc-filled-button-label-text-color: #ffffff;
  --mdc-filled-button-container-shape: 8px;
  --mdc-filled-button-disabled-container-color: rgba(93, 117, 153, .4);
  --mdc-filled-button-disabled-label-text-color: rgba(255, 255, 255, .4);
  --mat-filled-button-state-layer-color: #8c8e92;
  --mat-filled-button-ripple-color: rgba(210, 44, 44, .1);

  /* Outlined buttons */
  --mdc-outlined-button-container-shape: 8px;
  --mdc-outlined-button-outline-color: #b7cce1;
  --mdc-outlined-button-label-text-color: #455d82;
  --mdc-outlined-button-disabled-outline-color: rgba(183, 204, 225, .4);
  --mdc-outlined-button-disabled-label-text-color: rgba(69, 93, 130, .4);

  /* Text buttons */
  --mdc-text-button-container-shape: 8px;
  --mat-text-button-state-layer-color: #8c8e92;
  --mat-text-button-ripple-color: rgba(210, 44, 44, .1);

  /* Tabs */
  --mdc-secondary-navigation-tab-container-height: 4rem;
  --mdc-tab-indicator-active-indicator-height: 4px;
  --mdc-tab-indicator-active-indicator-shape: 0;
  --mat-tab-header-divider-color: #5d7599;
  --mat-tab-header-divider-height: 1px;
  --mat-tab-header-active-label-text-color: #455d82;
  --mat-tab-header-inactive-label-text-color: #385f99;
  --mat-tab-header-active-focus-indicator-color: #455d82;

  /* Form fields */
  --mdc-filled-text-field-caret-color: #5d7599;
  --mdc-filled-text-field-focus-active-indicator-color: #5d7599;
  --mdc-filled-text-field-input-text-color: #1e1e1e;
  --mat-form-field-leading-icon-color: #1e1e1e;
  --mat-form-field-focus-select-arrow-color: rgba(93, 117, 153, .87);

  /* Options / Select */
  --mat-option-selected-state-label-text-color: #5d7599;
  --mat-option-label-text-color: rgba(0, 0, 0, .87);

  /* Checkboxes */
  --mdc-checkbox-selected-focus-icon-color: #2f3b4d;
  --mdc-checkbox-selected-hover-icon-color: #2f3b4d;
  --mdc-checkbox-selected-icon-color: #2f3b4d;
  --mdc-checkbox-selected-pressed-icon-color: #2f3b4d;
  --mat-full-pseudo-checkbox-selected-icon-color: #a0a2a5;
  --mat-full-pseudo-checkbox-selected-checkmark-color: #1e1e1e;
  --mat-full-pseudo-checkbox-unselected-icon-color: #a0a2a5;

  /* Cards */
  --mdc-elevated-card-container-shape: 4px;
  --mdc-outlined-card-container-shape: 4px;
  --mdc-outlined-card-outline-width: 1px;

  /* Menu */
  --mat-menu-container-shape: 4px;
  --mat-menu-container-elevation-shadow: 0 6px 16px -4px rgba(0, 0, 0, .32), 0 5px 8px -8px rgba(0, 0, 0, .08);
  --mat-menu-item-label-text-color: #5d7599;
  --mat-menu-item-icon-color: #5d7599;
  --mat-menu-item-spacing: 24px;
  --mat-menu-item-icon-size: 24px;

  /* Dialog */
  --mdc-dialog-container-shape: 1.6rem;
  --mdc-dialog-supporting-text-color: #1e1e1e;

  /* Tooltip */
  --mdc-plain-tooltip-container-color: #282e37;
  --mdc-plain-tooltip-supporting-text-color: #ffffff;
  --mdc-plain-tooltip-container-shape: 4px;
  --mdc-plain-tooltip-supporting-text-line-height: 1.6rem;

  /* Table */
  --mat-table-header-headline-font: 'Source Sans Pro', Avenir, Calibri, Helvetica, Droid Sans, sans-serif;
  --mat-table-header-headline-size: 14px;
  --mat-table-header-headline-weight: 500;
  --mat-table-header-headline-line-height: 24px;
  --mat-table-row-item-label-text-size: 14px;
  --mat-table-row-item-label-text-weight: 400;
  --mat-table-row-item-outline-width: 1px;
  --mat-table-header-container-height: 48px;
  --mat-table-row-item-container-height: 4.8rem;
  --mat-table-footer-container-height: 44px;

  /* Expansion panel */
  --mat-expansion-header-text-font: 'Source Sans Pro', Avenir, Calibri, Helvetica, Droid Sans, sans-serif;
  --mat-expansion-header-text-size: 15px;
  --mat-expansion-header-text-weight: 400;
  --mat-expansion-header-text-line-height: 24px;
  --mat-expansion-container-text-font: 'Source Sans Pro', Avenir, Calibri, Helvetica, Droid Sans, sans-serif;
  --mat-expansion-container-text-size: 14px;
  --mat-expansion-container-text-weight: 400;
  --mat-expansion-container-text-line-height: 20px;

  /* Shadows */
  --mat-app-elevation-shadow-level-0: 0px 0px 0px 0px rgba(0,0,0,.2), 0px 0px 0px 0px rgba(0,0,0,.14), 0px 0px 0px 0px rgba(0,0,0,.12);
  --mat-app-elevation-shadow-level-1: 0px 2px 1px -1px rgba(0,0,0,.2), 0px 1px 1px 0px rgba(0,0,0,.14), 0px 1px 3px 0px rgba(0,0,0,.12);
  --mat-app-elevation-shadow-level-2: 0px 3px 1px -2px rgba(0,0,0,.2), 0px 2px 2px 0px rgba(0,0,0,.14), 0px 1px 5px 0px rgba(0,0,0,.12);

  /* Font */
  --font-sans: 'Source Sans Pro', Avenir, Calibri, Helvetica, 'Droid Sans', sans-serif;
}
```


---


## Design Principles


1. Modern institutional with friendly radii -- Cool blue-grey base palette paired with generous 16px card radii and 8px button radii, softening the corporate feel.
2. Flat with cool-tinted shadows -- Cards use a single diffused shadow tinted with #edf2f3 rather than black. The aesthetic is lifted but not dramatic.
3. Translucent top bar -- The top navigation uses 70% opacity white, allowing subtle content bleed-through on scroll.
4. Light side nav, light content -- Unlike dark-header patterns, this theme uses a light grey (#edf2f3) sidebar with white active-item highlights against a #f5f8f9 content area.
5. Color-coded interactivity -- Navy #455d82 for interactive elements (buttons, icons, chevrons), medium blue #385f99 for links and inactive tabs, brand red #d3222a for notifications and active state highlights.
6. Contrast through weight, not color -- Uses font weight 400 vs 600 to create hierarchy. Color is reserved for actions and status.
7. Brand gradient as accent -- The red-to-purple gradient on the News card is the single strongest visual flourish; the rest of the UI is restrained.
8. 4px spacing grid -- All spacing derives from a 4px base unit (--spacing-base: 4) used consistently via --s{N} tokens.


---


## Component Patterns


### Top Bar

AppToolbar -- Top-level navigation bar with search, notifications, and account menu.

- Background: rgba(255, 255, 255, 0.7)
- Height: 55px
- Padding: 4px 12px
- Border bottom: 1px solid #e6e6e6
- Position: static (scrolls with content)

Contains: hamburger menu button, search field (mat-form-field, outlined, 8px radius, white bg, 40px height), notification/messenger/help icon buttons, account avatar button.


### Side Navigation

MatSidenav -- Left-side collapsible navigation panel.

- Background: #edf2f3
- Width: 300px (expanded)
- Right border: 1px solid #e6e6e6
- Box shadow: none

Navigation items:
- Font: 16px / 400, color rgba(0,0,0,0.87), line-height 20px
- Icon size: 22px, color #455d82
- Active item: background #ffffff, border-radius 4px, font-weight 600
- Active icon: color #d3222a (brand red)
- Hover state layer: rgba(0,0,0,0.04)


### Cards (Book cards, Todo cards)

Surface cards with soft shadow and generous radius.

- Background: #ffffff
- Border: 1px solid #e6e6e6
- Border radius: 16px
- Shadow: rgb(237, 242, 243) 0px 4px 6px 0px
- Padding: 16px


### Announcement Banner

Light blue inset panel for system announcements.

- Background: #e4eef6
- Border radius: 16px
- Padding: 12px
- No border, no shadow
- Title: #2162e4, 16px / 600
- Body: 13px / 400, color #385f99


### Outlined Buttons ("Open book", "Load more")

Ghost-style buttons with navy text and blue-grey stroke.

- Background: transparent
- Color: #455d82
- Border: 1px solid #b7cce1
- Border radius: 8px
- Padding: 0px 16px
- Font: 14px / 600, text-transform none


### Filled Buttons

Primary action buttons.

- Background: #455d82
- Color: #ffffff
- Border radius: 8px
- Disabled background: rgba(93, 117, 153, 0.4)
- Disabled text: rgba(255, 255, 255, 0.4)


### Notification Badges

Small red circular indicators for unread counts.

- Background: #d3222a
- Text: #ffffff
- Font: 12px / 600
- Border radius: 50%
- Min size: ~16px diameter


### Tabs

Flat tab bar with color-differentiated labels.

- Container height: 4rem
- Active tab label: color #455d82, weight 600
- Inactive tab label: color #385f99, weight 400
- Active indicator: 4px solid #455d82, shape 0 (square ends)
- Divider: 1px solid #5d7599
- Tab padding: 0px 16px


### News and Insights Card

White card with a decorative gradient strip.

Gradient element (above card):
- Height: 30px
- Border radius: 16px
- Background: linear-gradient(65.28deg, #d3222a, #b646f6 54.97%, #4d1dd5 80.25%)

Card:
- Background: #ffffff
- Border radius: 16px
- Padding: 16px
- Article title links: #385f99, 14px
- Source name: #1e1e1e, 14px / 400
- Date: #676767, 14px / 400


### Search Field

White input field embedded in the top bar.

- Wrapper background: #ffffff
- Outer border radius: 8px
- Form field border radius: 5px
- Height: 40px
- Input font: 16px / 400
- Search icon color: #1e1e1e
- Placeholder color: #949494


### Menus / Dropdowns

Elevated panels for contextual actions.

- Container shape: 4px
- Shadow: 0 6px 16px -4px rgba(0,0,0,.32), 0 5px 8px -8px rgba(0,0,0,.08)
- Item text color: #5d7599
- Item icon color: #5d7599
- Item spacing: 24px
- Item icon size: 24px


### Dialogs / Modals

Elevated overlay panels.

- Container shape: 1.6rem (~26px)
- Supporting text color: #1e1e1e


### Tooltips

Compact informational overlays.

- Background: #282e37
- Text: #ffffff
- Shape: 4px
- Line height: 1.6rem


### Tables

Data display with clear row delineation.

- Header font: Source Sans Pro, 14px / 500
- Row font: Source Sans Pro, 14px / 400
- Header height: 48px
- Row height: 4.8rem
- Row outline: 1px solid
- Footer height: 44px


### Expansion Panels

Collapsible content sections.

- Header font: Source Sans Pro, 15px / 400, line-height 24px
- Body font: Source Sans Pro, 14px / 400, line-height 20px


---


## Layout Patterns


- Top bar: fixed height 55px, full width, translucent white with bottom border
- Side nav: 300px width (expanded), light grey bg, right border
- Content area: fills remaining width, #f5f8f9 background
- Two-column homepage: left (~60%) for announcements/todos/books, right (~40%) for news/education/resources
- Card spacing: book cards stack vertically with consistent gap
- Page padding: handled by individual content sections, not a global wrapper
- Section gap: ~16-24px between major content blocks