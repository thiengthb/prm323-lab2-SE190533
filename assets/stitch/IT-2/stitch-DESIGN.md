---
name: Neutral Precision
colors:
  surface: '#f9f9f9'
  surface-dim: '#dadada'
  surface-bright: '#f9f9f9'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f3f3f3'
  surface-container: '#eeeeee'
  surface-container-high: '#e8e8e8'
  surface-container-highest: '#e2e2e2'
  on-surface: '#1a1c1c'
  on-surface-variant: '#47464b'
  inverse-surface: '#2f3131'
  inverse-on-surface: '#f0f1f1'
  outline: '#77767b'
  outline-variant: '#c8c5cb'
  surface-tint: '#5f5e61'
  primary: '#000000'
  on-primary: '#ffffff'
  primary-container: '#1b1b1e'
  on-primary-container: '#858387'
  inverse-primary: '#c8c5ca'
  secondary: '#5e5e67'
  on-secondary: '#ffffff'
  secondary-container: '#e0dee9'
  on-secondary-container: '#62626b'
  tertiary: '#000000'
  on-tertiary: '#ffffff'
  tertiary-container: '#1d1b16'
  on-tertiary-container: '#88837c'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#e4e1e6'
  primary-fixed-dim: '#c8c5ca'
  on-primary-fixed: '#1b1b1e'
  on-primary-fixed-variant: '#47464a'
  secondary-fixed: '#e3e1ec'
  secondary-fixed-dim: '#c7c5d0'
  on-secondary-fixed: '#1a1b23'
  on-secondary-fixed-variant: '#46464f'
  tertiary-fixed: '#e8e2d9'
  tertiary-fixed-dim: '#cbc6bd'
  on-tertiary-fixed: '#1d1b16'
  on-tertiary-fixed-variant: '#494640'
  background: '#f9f9f9'
  on-background: '#1a1c1c'
  surface-variant: '#e2e2e2'
typography:
  metric-num:
    fontFamily: Inter
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 38px
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Inter
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 30px
    letterSpacing: -0.015em
  headline-md:
    fontFamily: Inter
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 26px
    letterSpacing: -0.01em
  title-sm:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '600'
    lineHeight: 22px
  body-lg:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-default:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-medium:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 20px
  label-default:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 18px
  caption-strict:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 18px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1rem
  margin: 1rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 0.75rem
  space-lg: 1rem
  space-xl: 1.5rem
---

## Brand & Style
The design system embodies a distilled, utilitarian aesthetic rooted in the modern monochrome tradition of shadcn/ui. Tailored specifically for high-density mobile applications, it prioritizes clarity, structural honesty, and functional speed over ornament. 

The emotional signature is composed, objective, and dependable. By stripping away extraneous decorative accents and strictly eliminating violet or saturated hues, the interface acts as a silent canvas that accentuates user content and critical telemetry. Visual hierarchy is achieved entirely through typographic contrast, precise micro-spacing, and low-contrast surface differentiation.

## Colors
The palette is built strictly upon neutral zinc scales without any undertones of violet, indigo, or purple.

### Canvas & Surfaces
- **Canvas / Background**: `#FAFAFA` — Sets the core ground plane for viewport scroll areas.
- **Surface / Card Background**: `#FFFFFF` — Elevated base for interactive cards, sheets, and containers.
- **Border Default**: `#E4E4E7` — Structural 1px boundary separating surfaces, inputs, and list rows.
- **Subtle Surface / Tab Track**: `#F4F4F5` — Recessed background for tab bars, segmented tracks, and inactive chips.

### Typography & Content
- **Primary Text**: `#18181B` — Titles, active values, high-contrast labels, and primary glyphs.
- **Secondary Text / Muted**: `#52525B` — Supporting labels, inactive states, hints, and breadcrumbs.

### Actions & States
- **Primary Action (Default)**: `#18181B` fill with `#FAFAFA` typography and iconography.
- **Primary Action (Active / Pressed)**: `#3F3F46` fill.
- **Selected Tab Indicator**: `#F4F4F5` fill with `#18181B` active foreground.

### Semantic Status Pairs
Status indicators employ purposeful background tints with high-contrast text to meet strict legibility thresholds:
- **Present (Success)**: Foreground `#15803D` on Surface `#F0FDF4`, Border `#DCFCE7`.
- **Pending (Warning)**: Foreground `#B45309` on Surface `#FFFBEB`, Border `#FEF3C7`.
- **Absent / Critical (Danger)**: Foreground `#B91C1C` on Surface `#FEF2F2`, Border `#FEE2E2`.

## Typography
Typographic scale utilizes `Inter` exclusively across all viewport sizes. The system enforces an absolute minimum text size of 14px (14sp) across all metadata, utility text, captions, and form helpers to ensure instant readability in mobile contexts.

### Hierarchy Guidelines
- **Data & Metric Displays (`metric-num`)**: Dedicated to standalone telemetry, large numerical counters, and monetary displays (32px, Semibold). Set tabular figures (`tnum`) for animated or updating counters.
- **Headers (`headline-lg`, `headline-md`)**: Restricted to mobile screen headers and top app bars. Tight negative letter spacing is applied to maintain visual density.
- **Section & Card Titles (`title-sm`)**: High-contrast anchor text for modular cards and sheet headers (16px, Semibold).
- **Body & Controls (`body-default`, `label-default`)**: The core interaction size (14px). Employs Regular (400) for narrative copy and Medium (500) for control labels, button text, and active interactive elements.

## Layout & Spacing
The layout system is tailored for a single-column, fluid mobile architecture governed by an 8pt base grid with a 4pt micro-step.

### Screen Structure
- **Outer Canvas Margins**: Uniform 16px (`1rem`) on horizontal screen borders, providing edge safety while maximizing usable viewport width.
- **Vertical Rhythm**: 16px gap between stacked card modules. Sections of unrelated content separate at 24px (`1.5rem`).
- **Internal Container Padding**: Standard mobile cards use 16px horizontal and vertical padding; compact metric tiles collapse to 12px (`0.75rem`).
- **Touch Target Safeguard**: All interactive elements maintain a minimum physical touch footprint of 44x44 points, regardless of visual boundary dimensions.

## Elevation & Depth
This design system avoids skeuomorphic dropshadows, blurred color casts, and high-opacity black drop filters. Spatial depth is established via crisp, flat boundaries and calculated surface color steps.

### Surface Tiers
1. **Base Plane**: Screen backdrop `#FAFAFA`.
2. **Resting Tier**: Card elements, inputs, and structured list modules resting on `#FFFFFF`, framed with a deliberate 1px solid `#E4E4E7` border.
3. **Floating & Modal Elements**: Bottom sheets, sticky actions, and floating popovers remain `#FFFFFF` with a 1px `#E4E4E7` perimeter, complemented by an ultra-subtle directional ambient shadow: `0 8px 24px -4px rgba(24, 24, 27, 0.08)`.
4. **Recessed Wells**: Segmented pickers and secondary input groupings sit recessed into `#F4F4F5` fields without borders.

## Shapes
The shape language uses distinct, deterministic radius values mapped strictly to component size tiers:

- **Cards & Modal Containers**: Radius of exactly 16px (`1rem`). Matches outer screen curvature on edge-pinned surfaces.
- **Buttons, Inputs, & Interactive Controls**: Radius of exactly 12px (`0.75rem`). Provides proportional nesting when nested inside 16px card containers with 12px–16px internal padding.
- **Status Badges & Inline Tags**: Radius of 8px to 10px, or full pill (`9999px`) for quick-scan categorical indicators.
- **Dividers & Strokes**: Standardized 1px hairline thickness on all bordered geometries.

## Components

### Buttons
- **Primary Button**: Solid `#18181B` background, `#FAFAFA` text, 12px radius, height 44px minimum, 14px Medium typography. Pressed/active state transitions instantly to `#3F3F46`.
- **Secondary Button**: `#FFFFFF` background, 1px `#E4E4E7` border, `#18181B` text. Pressed state shifts background to `#F4F4F5`.
- **Destructive Button**: `#FEF2F2` background, 1px `#FEE2E2` border, `#B91C1C` text. Pressed state shifts to `#FEE2E2`.

### Cards & Content Containers
- Standardized container using `#FFFFFF` fill, 1px solid `#E4E4E7` border, and 16px corner radius.
- Padding is fixed at 16px. Internal section dividers inside cards span border-to-border using 1px `#E4E4E7`.

### Segmented Controls & Tab Bars
- **Container**: Track fill `#F4F4F5` with 12px radius and 4px internal padding.
- **Selected Tab Indicator**: Elevated `#FFFFFF` or high-contrast `#F4F4F5` pill with 8px radius, text color `#18181B` (Semibold 14px).
- **Unselected Tabs**: Transparent background, text color `#52525B` (Regular 14px).

### Input Fields
- Height 44px, `#FFFFFF` background, 1px solid `#E4E4E7`, 12px radius, 14px `#18181B` text.
- **Placeholder**: `#52525B`.
- **Focus State**: 1px `#18181B` outline (or 2px `#18181B` inner stroke) with zero blur rings.

### Checkboxes & Radio Controls
- Base dimension 20x20px with 1px `#E4E4E7` border on `#FFFFFF` ground.
- Checkboxes use 6px radius; Radio controls use full circular radius.
- **Checked State**: Solid `#18181B` background with `#FAFAFA` checkmark or interior dot.

### Status Badges
- Compact chips featuring 14px typography (Medium) and 4px vertical / 8px horizontal padding.
- **Present**: `#F0FDF4` fill, `#DCFCE7` border, `#15803D` label.
- **Pending**: `#FFFBEB` fill, `#FEF3C7` border, `#B45309` label.
- **Absent**: `#FEF2F2` fill, `#FEE2E2` border, `#B91C1C` label.

### Lists & Navigation Rows
- Grouped inside 16px rounded `#FFFFFF` card containers.
- List items have a minimum height of 48px, horizontal layout with 14px/16px titles, `#52525B` disclosure chevrons, separated by 1px `#E4E4E7` horizontal rules indented 16px to align with text start.