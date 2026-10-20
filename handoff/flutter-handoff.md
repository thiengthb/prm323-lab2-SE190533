# Flutter handoff

> Bản nháp v0.1 · 20/10/2026: đã có hai bảng ánh xạ toàn cục. Đặc tả 6 mục cho từng màn sẽ viết sau khi chốt final UI ở Figma trang 03.

## 1. Token → Flutter

Theme: `ThemeData(useMaterial3: true, colorScheme: AppColors.scheme, textTheme: AppText.theme, fontFamily: 'Inter')`.

### Màu

| Token | Hex | Flutter |
|---|---|---|
| `color/bg` | `#FAFAFA` | `ColorScheme.surface` (nền Scaffold) |
| `color/surface` | `#FFFFFF` | `ColorScheme.surfaceContainerLowest` (Card, sheet, NavigationBar) |
| `color/muted-surface` | `#F4F4F5` | `ColorScheme.surfaceContainerHighest` (SegmentedButton nền, skeleton) |
| `color/border` | `#E4E4E7` | `ColorScheme.outlineVariant` |
| `color/border-control` | `#71717A` | `ColorScheme.outline` |
| `color/fg` | `#18181B` | `ColorScheme.onSurface` |
| `color/fg-muted` | `#52525B` | `ColorScheme.onSurfaceVariant` |
| `color/fg-disabled` | `#A1A1AA` | `onSurface.withOpacity` không dùng; hằng `AppColors.fgDisabled` |
| `color/primary` | `#7C3AED` | `ColorScheme.primary` |
| `color/primary-pressed` | `#6D28D9` | `AppColors.primaryPressed` (overlay khi nhấn) |
| `color/primary-soft` | `#F5F3FF` | `ColorScheme.primaryContainer` |
| `color/on-primary-soft` | `#5B21B6` | `ColorScheme.onPrimaryContainer` |
| `color/on-primary` | `#FFFFFF` | `ColorScheme.onPrimary` |
| `color/success` / `-soft` | `#15803D` / `#F0FDF4` | `AppColors.success` / `successSoft` (ThemeExtension `StatusColors`) |
| `color/warning` / `-soft` | `#B45309` / `#FFFBEB` | `AppColors.warning` / `warningSoft` (ThemeExtension) |
| `color/danger` / `-soft` | `#B91C1C` / `#FEF2F2` | `ColorScheme.error` / `ColorScheme.errorContainer` |

### Chữ (Inter)

| Token | Cỡ / dòng / độ đậm | Flutter `TextTheme` |
|---|---|---|
| `type/display` | 32 / 40 / w600 | `displaySmall` |
| `type/title-lg` | 22 / 28 / w600 | `titleLarge` |
| `type/title` | 18 / 24 / w600 | `titleMedium` (ghi đè cỡ 18) |
| `type/body` | 16 / 24 / w400 | `bodyLarge` |
| `type/body-strong` | 16 / 24 / w500 | `bodyLarge.copyWith(fontWeight: w500)` |
| `type/label` | 14 / 20 / w500 | `labelLarge` |
| `type/body-sm` | 14 / 20 / w400 | `bodyMedium` |

### Khoảng cách, bo góc, đổ bóng, kích thước

| Token | Giá trị | Flutter |
|---|---|---|
| `space/4..32` | 4, 8, 12, 16, 20, 24, 32 | `AppSpace.s4 … s32` (const double) |
| `radius/sm, md, lg, full` | 8, 12, 16, 999 | `AppRadius.sm/md/lg` → `BorderRadius.circular`, `StadiumBorder` |
| `elevation/0` | viền 1 `outlineVariant` | `Card(elevation: 0, shape: RoundedRectangleBorder(side: …))` |
| `elevation/1` | 0 1 2, 6% | `NavigationBar(elevation: 1)` |
| `elevation/2` | 0 8 24, 12% | `Dialog`, `SnackBar`, `BottomSheet` elevation 6 + `shadowColor` |
| `size/touch` | 48 | `MaterialTapTargetSize.padded`, `minimumSize: Size(48, 48)` |
| `size/avatar` | 40 | `CircleAvatar(radius: 20)` |

## 2. Component → Widget

| Component Figma | Variant | Widget Flutter |
|---|---|---|
| Button | Primary / Outline / Ghost / Destructive × Default, Pressed, Disabled, Loading | `FilledButton` / `OutlinedButton` / `TextButton` / `FilledButton` với `backgroundColor: error`; Loading: `child: Row(CircularProgressIndicator(strokeWidth 2, size 20), Text)`, `onPressed: null` |
| Text field | Default, Focused, Filled, Error, Disabled | `TextFormField` + `InputDecoration(border: OutlineInputBorder(radius 12), focusedBorder width 2 primary, errorText)` |
| Card | Default, Pressed | `Card` + `InkWell` |
| Status chip | Present, Absent, Pending, Warning, Over, Neutral | `Chip(avatar: Icon(16), label, backgroundColor: *Soft, labelStyle color)` |
| Avatar | — | `CircleAvatar` (ảnh FAP, dự phòng chữ viết tắt) |
| Student row | Scanned, Exception, Marked present, Marked absent | `ListTile(leading: CircleAvatar, title, subtitle, trailing: Chip hoặc Row(IconButton.outlined ×2))` |
| Attention row | Near, Over | `ListTile(trailing: Column(Text số, Text “buổi vắng”))` |
| Slot card | Upcoming, Live, Unclosed, Closed | `Card(shape side: primary/warning 2)` + `Column` + `FilledButton` |
| App bar | Top-level, Nested, Nested with action | `SliverAppBar` / `AppBar(leading: BackButton, actions)` |
| Bottom navigation | 4 tab được chọn | `NavigationBar` + 4 `NavigationDestination`, `indicatorColor: primaryContainer` |
| Segmented control | Hôm nay, Ngày mai, Tuần | `SegmentedButton<int>` |
| Dialog | Confirmation, Destructive | `AlertDialog` (2 action) |
| Snackbar | with action | `SnackBar(action: SnackBarAction('Hoàn tác'), duration 10s)` |
| Loading / Skeleton card | — | `Container` màu `surfaceContainerHighest` (hoặc gói `shimmer`) |
| Empty state | — | `Column(CircleAvatar(Icon), Text, OutlinedButton)` |
| Error state | — | `Column(CircleAvatar(Icon wifi_off), Text, FilledButton('Thử lại'))` |
| QR panel | — | `Card` + `QrImageView` (gói `qr_flutter`) + `Text` |
| Icon (Lucide) | 29 icon | gói `lucide_icons_flutter`, `size 20/24` |
