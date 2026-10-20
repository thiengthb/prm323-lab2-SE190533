---
name: Academic Attendance System
colors:
  surface: '#fbf8fc'
  surface-dim: '#dcd9dd'
  surface-bright: '#fbf8fc'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f6f2f7'
  surface-container: '#f0edf1'
  surface-container-high: '#eae7eb'
  surface-container-highest: '#e4e1e6'
  on-surface: '#1b1b1e'
  on-surface-variant: '#4a4455'
  inverse-surface: '#303033'
  inverse-on-surface: '#f3f0f4'
  outline: '#7b7487'
  outline-variant: '#ccc3d8'
  surface-tint: '#732ee4'
  primary: '#630ed4'
  on-primary: '#ffffff'
  primary-container: '#7c3aed'
  on-primary-container: '#ede0ff'
  inverse-primary: '#d2bbff'
  secondary: '#006d30'
  on-secondary: '#ffffff'
  secondary-container: '#92f5a4'
  on-secondary-container: '#007233'
  tertiary: '#823900'
  on-tertiary: '#ffffff'
  tertiary-container: '#a84b00'
  on-tertiary-container: '#ffdfcf'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#eaddff'
  primary-fixed-dim: '#d2bbff'
  on-primary-fixed: '#25005a'
  on-primary-fixed-variant: '#5a00c6'
  secondary-fixed: '#95f8a7'
  secondary-fixed-dim: '#79db8d'
  on-secondary-fixed: '#00210a'
  on-secondary-fixed-variant: '#005323'
  tertiary-fixed: '#ffdbca'
  tertiary-fixed-dim: '#ffb68e'
  on-tertiary-fixed: '#331200'
  on-tertiary-fixed-variant: '#763300'
  background: '#fbf8fc'
  on-background: '#1b1b1e'
  surface-variant: '#e4e1e6'
typography:
  display-stat:
    fontFamily: Inter
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 38px
  headline-lg:
    fontFamily: Inter
    fontSize: 22px
    fontWeight: '600'
    lineHeight: 28px
  headline-md:
    fontFamily: Inter
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 24px
  title-sm:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '600'
    lineHeight: 22px
  body-default:
    fontFamily: Inter
    fontSize: 15px
    fontWeight: '400'
    lineHeight: 22px
  body-medium:
    fontFamily: Inter
    fontSize: 15px
    fontWeight: '500'
    lineHeight: 22px
  body-sm:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  label-default:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 20px
  label-code:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 18px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 0.75rem
  margin: 1.25rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 0.75rem
  space-lg: 1rem
  space-xl: 1.25rem
---

## Brand & Style

This design system targets higher-education faculty and lecturers conducting fast, high-stakes attendance tracking, schedule management, and academic intervention on mobile devices. Designed specifically for Android viewports (calibrated to a base resolution of 360×800dp), the aesthetic translates the precision and structural restraint of modern web UI toolkits (specifically shadcn/ui) into an ergonomic, native mobile experience.

### Aesthetic Principles
- **Utilitarian Clarity**: High visual contrast without excessive decoration. The interface recedes to make dense operational data—such as attendance lists, student roll calls, and percentage thresholds—immediately scannable in high-glare classroom environments.
- **Structural Separation over Shadows**: Hierarchy is reinforced through hairline boundaries (1px solid zinc borders) and deliberate spatial padding, eliminating ambient fuzziness or blurred elevation models.
- **Strict Anti-Patterns**: No gradients under any circumstances. No cards nested inside cards ("card-in-card" nesting is strictly banned to prevent visual clutter). Touch surfaces respect an absolute minimum physical envelope of 48×48dp.
- **Language & Tone**: All UI strings and microcopy are set in institutional yet direct Vietnamese (e.g., "Tổng quan", "Điểm danh", "Vắng có phép", "Cấm thi").

## Colors

The color palette enforces deliberate functional clarity using a neutral zinc foundation paired with an authoritative violet primary accent and strict, tri-state semantic tokens.

### Base Surfaces & Ink
- **Canvas / Background**: `#FAFAFA` (Zinc 50) establishes a clean, non-glare slate across the entire mobile screen viewport.
- **Card / Surface**: `#FFFFFF` provides crisp focus for operational containers.
- **Border**: `#E4E4E7` (Zinc 200) renders crisp 1px structural outlines for all cards, table cells, and dividers.
- **Primary Text**: `#18181B` (Zinc 900) ensures AAA compliance across surfaces.
- **Secondary / Subdued Text**: `#52525B` (Zinc 600) for metadata, timestamps, and secondary captions.
- **Muted Elements**: `#71717A` (Zinc 500) for placeholders and inactive iconography.

### Semantic & Accent Colors
- **Primary Accent (`#7C3AED`)**: Deep violet deployed selectively for primary submit actions, active bottom navigation tabs, focused inputs, and critical confirmation CTAs.
- **Present / Success**: 
  - Text: `#15803D`
  - Fill: `#F0FDF4`
  - Border: `#BBF7D0`
- **Warning / Pending**:
  - Text: `#B45309`
  - Fill: `#FFFBEB`
  - Border: `#FDE68A`
- **Absent / Danger / Banned Threshold**:
  - Text: `#B91C1C`
  - Fill: `#FEF2F2`
  - Border: `#FECACA`

## Typography

The typography system relies exclusively on **Inter** to ensure maximum legibility for Vietnamese diacritics and compact alphanumeric university codes (e.g., `PRN211`, `SE1608`).

### Rules & Hierarchy
- **Strict Size Floor**: Font size must never dip below `14px` (`body-sm`, `label-default`). Micro-labels below 14px are strictly prohibited to ensure rapid readability on moving, handheld mobile devices.
- **Metric Presentation (`display-stat`)**: Numerical metrics—such as total present count, total absences, and percentage indicators—are set at `32px` with weight `600` (SemiBold) and a tight `38px` line height.
- **Headings**: Use `headline-lg` (`22px`) for top-level screen titles and modal headers; `headline-md` (`18px`) for key section divisions.
- **Labels & Identification**: Student registration IDs and course codes use `label-code` (`14px`, SemiBold) with standard tracking for instant verification.

## Layout & Spacing

Layout configuration is engineered around a single-column fluid mobile grid structured specifically for 360dp-wide displays, scaling outward gracefully to wider Android screens.

### Grid & Margins
- **Screen Margins**: Uniform `20px` (`1.25rem`) horizontal margins on left and right borders of the viewport. Content elements never bleed past this margin unless they are full-bleed separators or bottom action sheets.
- **Grid Gutters**: Internal multi-column layouts (e.g., two-column status metric grids) employ a fixed `12px` (`0.75rem`) gutter.

### Spacing Scales
- **`space-xs` (4px)**: Micro distance between badges and accompanying label text.
- **`space-sm` (8px)**: Internal horizontal padding for tags, spacing between list icons and titles.
- **`space-md` (12px)**: Default gap between form input labels and input fields; gap between adjacent list items.
- **`space-lg` (16px)**: Standard internal card padding; gap between standalone interactive modules.
- **`space-xl` (20px)**: Vertical separation between major functional sections on a screen.

### Touch Target Standard
All touch targets must guarantee a minimum bounding area of `48×48dp`. If a visible icon is 20×20dp, its tap container must be padded to at least 48dp.

## Elevation & Depth

In alignment with modern flat, boundary-led design systems (inspired by shadcn/ui), this system eschews multi-layer drop shadows and physical skeuomorphism in favor of **crisp outlines and tonal separation**.

### Elevation Hierarchy
1. **Level 0 (Canvas)**: Background surface tinted to `#FAFAFA`. No border, zero elevation.
2. **Level 1 (Card & Section Containers)**: `#FFFFFF` fill with a mandatory `1px solid #E4E4E7` border. Shadows are completely omitted or, if hardware rendering requires depth demarcation, restricted to a hairline ambient stamp: `box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05)`.
3. **Level 2 (Modals, Bottom Sheets & Popovers)**: `#FFFFFF` with `1px solid #E4E4E7` border, coupled with a backdrop scrim (`rgba(24, 24, 27, 0.4)`). A subtle diffused elevation of `0 10px 15px -3px rgba(0, 0, 0, 0.08)` separates dynamic interactive sheets from the canvas.

### The No Card-in-Card Rule
Surfaces must never be nested inside other surfaces. Content grouped inside a parent card must use hairline horizontal divider rules (`1px solid #E4E4E7`), alternating background fills, or whitespace to establish internal hierarchy.

## Shapes

Corner radii adhere to geometric consistency across macro and micro surfaces:

- **Cards & Primary Modules**: Fixed at `16px` (`rounded-xl` in this scale). Softens operational data while retaining structural discipline.
- **Buttons, Text Inputs, and Dropdown Triggers**: Fixed at `12px`. Distinguishes interactive controls from outer containment cards.
- **Pills & Status Badges**: Full radius (`9999px`) for compact state tags (e.g., "Có mặt", "Vắng").
- **Checkboxes & Segment Selectors**: `6px` radius for checkbox indicators; `8px` for inner segmented button toggles.

## Components

### Buttons
- **Primary Action**: Height `48px`, background `#7C3AED`, text `#FFFFFF`, radius `12px`, typography `label-default` (`14px, 500`). Active/Pressed state: `#6D28D9`. Full width (`100%`) on mobile forms.
- **Secondary / Outline**: Height `48px`, background `#FFFFFF`, border `1px solid #E4E4E7`, text `#18181B`. Active state: `#F4F4F5`.
- **Destructive**: Height `48px`, background `#FEF2F2`, border `1px solid #FECACA`, text `#B91C1C`.
- **Icon Actions**: Fixed bounding size of `48×48dp` with 20px centered Lucide icon.

### Cards
- **Specification**: Fill `#FFFFFF`, border `1px solid #E4E4E7`, border-radius `16px`, padding `16px`.
- **Prohibition**: Never embed another card inside. For student rows inside a class list card, use hairline dividers (`1px solid #E4E4E7`) without internal sub-cards.

### Status Chips & Badges
All badges have a height of `28px`, corner radius `9999px` (pill), horizontal padding `10px`, typography `body-sm` (`14px, 500`), and a `1px` solid border matching the status palette:
- **Có mặt (Present)**: `#F0FDF4` bg, `#BBF7D0` border, `#15803D` text.
- **Nghi ngờ / Chờ (Pending/Warning)**: `#FFFBEB` bg, `#FDE68A` border, `#B45309` text.
- **Vắng / Cấm thi (Absent/Banned)**: `#FEF2F2` bg, `#FECACA` border, `#B91C1C` text.

### Interactive Attendance Toggles (Tri-State Control)
- Segmented 3-way toggle per student row: "Có mặt" (P), "Vắng" (A), "Phép" (E).
- Container height: `40px`, background `#F4F4F5`, border radius `10px`, padding `2px`.
- Active segment: `#FFFFFF` fill with `1px solid #E4E4E7`, text colored according to semantic status state.

### Input Fields
- Container height `48px`, border `1px solid #E4E4E7`, border-radius `12px`, background `#FFFFFF`, horizontal padding `14px`, text `#18181B` (`15px`).
- Focus state: Border color changes to `#7C3AED` with an auxiliary `1px` outline ring.
- Label: Placed outside, top-aligned, `14px, 500`, `#52525B`, marginBottom `6px`.

### Bottom Navigation Bar
- Height: `64px` + Android system navigation inset. Background `#FFFFFF`, top border `1px solid #E4E4E7`.
- Layout: 4 tabs with uniform distribution:
  1. **Tổng quan** (LayoutDashboard icon)
  2. **Lịch** (CalendarDays icon)
  3. **Lớp** (Users icon)
  4. **Tài khoản** (UserCheck icon)
- Icon styling: Lucide icons rendered with exact `2px` stroke width, sizing `22×22dp`.
- States:
  - Active: Text and icon `#7C3AED` (SemiBold `14px`).
  - Inactive: Text and icon `#71717A` (Regular `14px`).