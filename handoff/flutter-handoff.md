# Flutter handoff

> v2.0 · 30/10/2026, khớp Final UI sau lượt duyệt cuối. Hai bảng ánh xạ toàn cục (mục 1 token, mục 2 component) và đặc tả 6 mục cho từng màn (mục 3): bố cục, component, trạng thái, tương tác, điều hướng, ràng buộc. Tên khung Figma trang 03 trùng mã màn, ví dụ `GV-102 · Phiên điểm danh .D2`. Thay đổi so với v1.3: mã GV-090..094, SV-090/091, SV-002; nhập lớp bằng file; Lịch Hôm nay / Tuần / Tháng; chip bo 8 không viền; thông báo nền `color/fg`.
>
> **Nguồn dữ liệu:** Cloud Firestore (dữ liệu của chính giảng viên: lớp, lịch, sinh viên nhập từ file Excel/CSV; phiên điểm danh; yêu cầu sửa; lời nhắc). Không gọi FAP.

## 1. Token → Flutter

Theme: `ThemeData(useMaterial3: true, colorScheme: AppColors.scheme, textTheme: AppText.theme, extensions: [StatusColors.light])`, font Nunito (gói `google_fonts`). Mọi giá trị nằm trong `lib/theme/`; màn hình không ghi mã màu, cỡ chữ, khoảng đệm.

### Màu (khớp biến Figma `Color`)

| Token | Hex | Flutter |
|---|---|---|
| `color/bg`, `color/surface` | `#FFFFFF` | `ColorScheme.surface` |
| `color/muted-surface` | `#F4F4F4` | `ColorScheme.surfaceContainerHighest` (nền tab, chip chưa chọn, skeleton) |
| `color/border` = `color/edge` | `#E5E5E5` | `ColorScheme.outlineVariant` (viền 2 và gờ đáy thẻ) |
| `color/border-control` | `#8F8F8F` | `ColorScheme.outline` (viền ô nhập, nút outline) |
| `color/fg-strong` | `#1F1F1F` | `AppColors.fgStrong` (số lớn, tiêu đề) |
| `color/fg` | `#3C3C3C` | `ColorScheme.onSurface`; nền thông báo (toast) |
| `color/fg-muted` | `#6B6B6B` | `ColorScheme.onSurfaceVariant` |
| `color/fg-disabled` | `#AFAFAF` | `AppColors.fgDisabled` |
| `color/primary` | `#B9551F` | `ColorScheme.primary` |
| `color/primary-pressed` = `color/edge-primary` | `#8A3D14` | `AppColors.primaryEdge` |
| `color/primary-soft` / `-soft-edge` | `#FBEFE8` / `#F9B98F` | `ColorScheme.primaryContainer` / `AppColors.primarySoftEdge` |
| `color/on-primary-soft` | `#9A4518` | `ColorScheme.onPrimaryContainer` |
| `color/on-primary` | `#FFFFFF` | `ColorScheme.onPrimary` |
| `color/brand` | `#F26F21` | `AppColors.brand` (chỉ icon ứng dụng) |
| `color/success` / `-soft` | `#15803D` / `#ECFDF3` | `StatusColors.success` / `successSoft` |
| `color/warning` / `-soft` | `#A15C00` / `#FFF6DD` | `StatusColors.warning` / `warningSoft` |
| `color/danger` / `-soft` | `#B42318` / `#FEF0EF` | `ColorScheme.error` / `errorContainer` |
| `color/scrim` | `#1F1F1F` 50% | `ColorScheme.scrim` |
| `color/camera` | `#000000` | `AppColors.camera` (nền khung quét) |

### Chữ (Nunito, 9 kiểu)

| Token | Cỡ / dòng / độ đậm | Flutter `TextTheme` |
|---|---|---|
| `type/display` | 28 / 34 / w700 | `displaySmall` |
| `type/title-lg` | 22 / 28 / w700 | `headlineSmall` |
| `type/title` | 17 / 24 / w700 | `titleMedium` |
| `type/section` | 16 / 22 / w700 | `titleSmall` |
| `type/body` | 15 / 22 / w500 | `bodyLarge` |
| `type/body-strong` | 15 / 22 / w600 | `titleLarge` (dùng làm “body-strong”, cỡ 15) |
| `type/label` | 14 / 20 / w600 | `labelLarge` |
| `type/body-sm` | 13 / 18 / w500 | `bodyMedium` |
| `type/caption` | 12 / 16 / w600 | `labelSmall` |

### Khoảng cách, bo góc, viền, kích thước

| Token | Giá trị | Flutter |
|---|---|---|
| `space/4..32` | 4, 8, 12, 16, 20, 24, 32 | `AppSpace.s4 … s32`; lề màn **12** (`AppSpace.screen`) |
| `radius/sm, md, lg, xl, full` | 6, 8, 8, 10, 999 | `AppRadius.sm/md/lg/xl/full` |
| Viền và gờ thẻ | viền 2 `edge` + gờ đáy 2 | `QaCard`: `Border.all(width: 2)` + `BoxShadow(offset: Offset(0, 2), blurRadius: 0)` |
| Gờ nút | đáy 2 `edge-primary` (nút chính), `edge` (nút outline) | `AppButton` tự vẽ gờ, khi nhấn dịch xuống 2 |
| `size/touch` | 48 | nút chính cao 48; nút trong thẻ và ô trống 40; nút trong hộp thoại 36 |
| `size/icon-20/24`, `size/avatar` | 20, 24, 40 | `AppSize.icon20/icon24/avatar` |

## 2. Component → Widget (mỗi component một widget trong `lib/widgets/`)

| Component Figma (trang 05) | Biến thể, trạng thái | Widget Flutter |
|---|---|---|
| Button 3:42 | Style primary / outline / ghost / destructive / onPrimary (nút trắng trên thẻ cam) × State default, pressed, disabled, loading; Icon trái, Mũi tên phải; cỡ 48 / 40 / 36 | `AppButton(label, style, size, icon, trailingArrow, loading, onPressed)` |
| Text field | default, focused, error, disabled | `AppTextField(label, errorText, obscure, keyboard)` |
| Card (thẻ nổi khối) | default, pressed, accent (viền hổ phách) | `QaCard(child, onTap, tone)` |
| Stat tile (ô số Tổng quan) | có số, “—” | `StatTile(value, label, onTap)` |
| Status chip 3:74 | Present (nền success-soft), Absent (nền danger-soft); bo 8, đệm 4/8, không icon, không viền | `StatusChip.present()` / `StatusChip.absent()` |
| Status badge 96:3177 | Closed (tick xanh), Upcoming (đồng hồ xám), Live (không hiện), Unclosed (tam giác hổ phách), Error (x đỏ); tròn đặc 20 | `StatusBadge(kind)` |
| Slot card 4:165 | upcoming, live (nền cam, nút trắng), unclosed, closed | `SlotCard(slot, action, onTap)` |
| Segmented control 5:242 | nền muted-surface bo 10 đệm 4; tab chọn ô trắng bo 8 có bóng nhẹ, chữ cam đậm | `AppSegmented<T>(options, value, onChanged)` (dùng cả cho tab Sinh viên / Buổi học) |
| Chip 91:156 | on / off; bo 8; off nền muted-surface | `AppChip(label, selected, onTap)` |
| Empty state 5:274 | Message “Trống”, “Chưa có lịch”, “Chưa có lớp”; nút 40 tùy chọn | `EmptyState(icon, message, actionLabel, onAction)` |
| Error state | “Mất kết nối mạng” + Thử lại | `ErrorState(message, onRetry)` |
| Skeleton (.L) | khối xám theo hình thẻ | `SkeletonBox(height)` |
| Dialog 5:259 | confirmation, error; bo 8, nút 36, lề 14 | `AppDialog.show(context, title, message, cancel, confirm)` |
| Sheet (OV3, OV5) | tay nắm 32×4, dính đáy | `AppSheet.show(context, title, child)` |
| Snackbar 5:260 | nền `color/fg` bo 12, tick đặc, chữ trắng, “Hoàn tác” trắng | `AppToast.show(context, message, undo)` |
| Date header 91:189 | kỳ trái, thứ ngày phải | `DateHeader(left, right)` |
| App bar 5:95 | Top (icon đặc + tiêu đề), Nested (chevron-left + Title + Icon) | `QaAppBar.top(title, icon)` / `QaAppBar.nested(title, icon)` |
| Bottom navigation 5:220 | 4 tab; tab chọn icon đặc trong ô primary-soft không viền | `QaBottomNav(index, onTap)` |
| Student row | avatar chữ viết tắt, tên, MSSV, công tắc có mặt | `StudentRow(student, present, onChanged)` |
| Attention row | near (hổ phách), over (đỏ); số chính Bold, “/4” Regular | `AttentionRow(student, absent, limit, onTap)` |
| Ratio text (“7/10”, “5/4”) | — | `RatioText(value, total, color)` |
| Avatar | chữ viết tắt trên primary-soft, không viền | `InitialsAvatar(name)` |
| Icon đặc / nét | bộ “Icon đặc/*” tự vẽ (134:175) và Lucide nét | `lucide_icons_flutter` cho icon nét; icon đặc dùng biến thể `Icons.*` Material đặc gần nhất (ghi ở design-traceability) |

## 3. Đặc tả từng màn

Quy ước chung:
- `Scaffold(backgroundColor: surface)`; thân là `ListView` lề ngang 12; nhóm cách nhau 24, thẻ cách nhau 8–12. App bar và nút đáy cố định, thân cuộn.
- Màn có ô nhập: nút chính ngay dưới ô, cao 48. Màn thông báo, kết quả: nút ghim đáy (thanh đáy đệm 12).
- Mỗi màn một nút primary. Mỗi nút icon có `tooltip`; chip và số trạng thái bọc `Semantics(label: …)`.
- Mọi màn tải dữ liệu có .L (skeleton), .E (EmptyState), .X (ErrorState + Thử lại).
- Kiểm ở 360 và 412 dp; ≥ 600 dp (web laptop) nội dung kéo hết ngang trong lề 24.

### GV-090 Đăng nhập · GV-091 Đăng ký · GV-092 Xác nhận email · GV-094 Quên mật khẩu
| Mục | Nội dung |
|---|---|
| Bố cục | Không app bar, không thanh tab · logo + “Quick Attend” · ô nhập · nút chính ngay dưới ô · dải “hoặc” · nút outline Google · link chuyển Đăng nhập ↔ Đăng ký |
| Component | AppTextField, AppButton (primary, outline với icon Google), TextButton link |
| Trạng thái | 090 .D, .X lỗi dưới ô mật khẩu “Sai email hoặc mật khẩu” · 092 .D đếm ngược gửi lại · 094 .D, .S “Đã gửi link · Kiểm tra hộp thư …” |
| Tương tác | Email `TextInputType.emailAddress`; mật khẩu che; nút loading khi đang gửi; hủy chọn tài khoản Google → toast “Đã hủy đăng nhập” |
| Điều hướng | Đăng nhập → GV-001 (thay stack); Đăng ký → 092 → 093 → GV-100 hoặc GV-001 .E2; Google lần đầu → 093 |
| Ràng buộc | Không lưu mật khẩu trên máy; phiên do Firebase Auth giữ |

### GV-093 Bắt đầu
| Mục | Nội dung |
|---|---|
| Bố cục | “Chào thầy Quân” · 3 thẻ bước B1–B3 (ô vuông bo 8 chứa nhãn) · nút đáy “Nhập lớp ngay” · TextButton “Để sau” |
| Component | QaCard, AppButton |
| Trạng thái | .D |
| Tương tác | — |
| Điều hướng | Nhập lớp ngay → GV-100; Để sau → GV-001 .E2 |
| Ràng buộc | Chỉ hiện sau đăng ký lần đầu |

### GV-001 Tổng quan
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.top(icon tổng quan đặc) · DateHeader(“Fall 2026”, “Thứ Ba, 20/10”) · lưới 2×2 StatTile (lớp đang dạy, sinh viên, có mặt tuần này, yêu cầu sửa) · SlotCard live/unclosed · tiêu đề “Chú ý” + tam giác hổ phách + “Xem tất cả ›” · 2 AttentionRow · QaBottomNav tab 0 |
| Component | StatTile, SlotCard, AttentionRow, EmptyState, ErrorState, SkeletonBox |
| Trạng thái | .D · .D1 thẻ chưa chốt (badge tam giác, nút Chốt ngay) · .L · .E không slot hôm nay · .E2 ô số “—” + EmptyState “Chưa có lịch / Hãy nhập danh sách lớp” + Nhập · .X ErrorState |
| Tương tác | Kéo để tải lại; nút trên thẻ đi thẳng GV-102 |
| Điều hướng | thẻ → GV-101; Điểm danh / Chốt ngay → GV-102; ô yêu cầu sửa → GV-105; Xem tất cả → GV-104; hàng → GV-201 |
| Ràng buộc | Thẻ ưu tiên: slot chưa chốt sớm nhất, rồi slot đang diễn ra; kỳ tính từ ngày máy (D-18) |

### GV-002 Lịch
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.top · AppSegmented Hôm nay / Tuần / Tháng · (Tuần) dòng “19/10 – 25/10”, nhóm theo ngày, nhãn “Hôm nay” · (Tháng) lưới 7 cột, chấm dưới ngày có slot, danh sách slot ngày chọn · SlotCard |
| Component | AppSegmented, DateHeader, SlotCard, StatusBadge, EmptyState |
| Trạng thái | .D1 · .D2 · .D3 · .E “Lịch trống” · .E2 “Chưa có lịch” + Nhập |
| Tương tác | Đổi tab giữ vị trí cuộn về đầu; chạm ngày trong tháng đổi danh sách |
| Điều hướng | thẻ → GV-101; nút thẻ → GV-102 |
| Ràng buộc | Đồng hồ xám chỉ cho slot sắp tới gần nhất; lịch chỉ đọc (lịch đến từ file nhập) |

### GV-003 Lớp · GV-103 Chi tiết lớp
| Mục | Nội dung |
|---|---|
| Bố cục | 003: hàng AppChip kỳ (cách danh sách 24) · thẻ lớp: “PRM393 · SE1801”, “35 sinh viên”, ô số hổ phách số em cần chú ý, mũi tên › · 103: QaAppBar.nested(“SE1801”) · “PRM393 · Fall 2026” · 2 StatTile (35 sinh viên, 6/20 buổi đã học) · AppSegmented Sinh viên / Buổi học · ô tìm · danh sách |
| Component | AppChip, QaCard, StatTile, AppSegmented, AppTextField (tìm), AttentionRow, RatioText |
| Trạng thái | 003 .D, .D2 kỳ mới đầu danh sách, .E “Chưa có lớp” + Nhập · 103 .D, .D1 |
| Tương tác | Tìm theo tên hoặc MSSV lọc ngay |
| Điều hướng | thẻ lớp → GV-103; hàng sinh viên → GV-201 |
| Ràng buộc | Kỳ cũ chỉ xem |

### GV-004 Tài khoản
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.top · avatar + tên + email · nhóm Nhắc nhở: Trước slot (10 phút), Slot chưa chốt (Khi hết giờ) với công tắc · nhóm Dữ liệu: Nhập danh sách lớp (Lần cuối 20/10) · nút Đăng xuất |
| Component | InitialsAvatar, QaCard, `Switch`, AppButton, AppDialog |
| Trạng thái | .D · .C hộp thoại “Đăng xuất?” + email, Hủy / Đăng xuất |
| Tương tác | Công tắc lưu ngay |
| Điều hướng | Nhập danh sách lớp → GV-100; Đăng xuất → GV-090 (xóa stack) |
| Ràng buộc | Nhắc mặc định bật (D-03) |

### GV-100 Nhập lớp
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.nested(“Nhập lớp”) · .D: ô chọn file (icon, “File Excel hoặc CSV từ phòng đào tạo”), nút Chọn file 40, “.xlsx hoặc .csv, tối đa 5 MB”, Tải file mẫu · .D1: tên file, “Fall 2026 · 4 lớp · 12 slot mỗi tuần”, 4 thẻ lớp · nút Nhập |
| Component | QaCard, AppButton, EmptyState-style header, ErrorState-style danh sách lỗi |
| Trạng thái | .D · .D1 · .L “Đã nhập 2/4 lớp”, nút loading “Đang xử lý” · .X “2 dòng lỗi, chưa nhập” + từng dòng lỗi, Bỏ qua / Chọn file khác · .S “Đã nhập 4 lớp · 12 slot tuần này”, 2 công tắc nhắc, nút Tổng quan |
| Tương tác | Kiểm tra file trước khi ghi (thiếu MSSV, trùng MSSV, sai cột); “Bỏ qua” nhập các dòng hợp lệ |
| Điều hướng | quay lại về nơi mở; .S → GV-001 |
| Ràng buộc | Tối đa 5 MB; nhập lại cùng kỳ thì thay lớp trùng mã |

### GV-101 Chi tiết slot
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.nested · thẻ thông tin: giờ, “PRM393 · SE1801”, ngày, phòng, sĩ số · (.D2/.D3) 2 ô số có mặt / vắng · (.D3) “Vắng” + StudentRow · nút đáy |
| Component | QaCard, StatTile, StudentRow, AppButton |
| Trạng thái | .D1 sắp tới · .D2 đang diễn ra (“—”) · .D3 đã chốt, nút Sửa (bút) |
| Tương tác | — |
| Điều hướng | Điểm danh / Sửa → GV-102 |
| Ràng buộc | Không hiện số có mặt khi chưa chốt |

### GV-102 Phiên điểm danh (+ GV-OV1, GV-OV2)
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.nested(“Điểm danh”, icon QR) · thẻ đếm “32/35” + thanh tiến độ hết ngang · (.D1) QR + “Còn 04:12” + chip “Đổi mã 12s” · (.D2) nút Mở lại · “Chưa quét (n)” · “Đã quét (n)” · StudentRow có công tắc · nút đáy Chốt (tick nét) |
| Component | QaCard, `QrImageView` (gói `qr_flutter`), AppChip, StudentRow, AppButton, AppDialog, AppToast |
| Trạng thái | .D1 · .D2 · OV1 · .L · .X / OV2 · .S kết quả + toast “Đã chốt” Hoàn tác, nút Xong |
| Tương tác | Mã QR đổi mỗi 12 giây; đếm cập nhật thời gian thực khi sinh viên quét; công tắc đánh dấu tay; Chốt lần đầu ở .D1 đóng mã (sang .D2), lần hai hỏi OV1 |
| Điều hướng | Xong → GV-001; Hoàn tác → .D2; Để sau → GV-001, slot vẫn chưa chốt |
| Ràng buộc | Không có ô nhập sĩ số (E-04); mất mạng thì giữ kết quả trên máy, không xóa; người chưa quét và chưa bật tính là Vắng |

### GV-104 Chú ý
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.nested(“Chú ý”) · ô tìm · AppChip Tất cả / Vượt / Sắp chạm / Lớp · AttentionRow |
| Component | AppTextField, AppChip, AttentionRow, EmptyState |
| Trạng thái | .D · .E “Trống” |
| Tương tác | Lọc tức thì |
| Điều hướng | hàng → GV-201 |
| Ràng buộc | Ngưỡng 20% số buổi; “sắp chạm” = còn ≤ 1 buổi; vượt = quá ngưỡng |

### GV-105 Yêu cầu sửa (+ GV-OV5)
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.nested(“Yêu cầu sửa”) · QaCard: avatar, tên, StatusChip.absent, “PRM393 · Thứ Ba, 20/10 · Slot 1”, lời sinh viên, Từ chối (outline 40) / Duyệt (primary 40) |
| Component | QaCard, StatusChip, AppButton, AppSheet, AppChip, AppTextField, AppToast |
| Trạng thái | .D · .S toast “Đã duyệt” + Hoàn tác · .E “Trống” · OV5 |
| Tương tác | Duyệt: thẻ biến mất, toast Hoàn tác; Từ chối: sheet chọn lý do bắt buộc |
| Điều hướng | quay lại GV-001 |
| Ràng buộc | Duyệt đổi buổi của sinh viên từ Vắng sang Có mặt |

### GV-201 Hồ sơ sinh viên (+ GV-OV3)
| Mục | Nội dung |
|---|---|
| Bố cục | QaAppBar.nested(“Hồ sơ”) · avatar, tên, “SE190155 · PRM393 · SE1801” · RatioText lớn “3/4” + “buổi vắng” · (.D1) “Sinh viên đã bị cấm thi” · “Buổi vắng” danh sách · nút đáy Nhắc nhở (chuông) |
| Component | InitialsAvatar, RatioText, QaCard, AppButton, AppSheet, AppToast |
| Trạng thái | .D · .D1 · .S nút “Đã nhắc” tắt + toast “Đã gửi” · OV3 nội dung soạn sẵn, email người nhận, Gửi |
| Tương tác | Nhắc → sheet; Gửi → đóng sheet, toast |
| Điều hướng | quay lại nơi mở |
| Ràng buộc | Mỗi sinh viên nhắc tối đa 1 lần mỗi ngày |

### SV-090 Đăng nhập · SV-091 Đăng ký (web)
| Mục | Nội dung |
|---|---|
| Bố cục | Như GV-090/091; 091 thêm ô MSSV |
| Component | AppTextField, AppButton |
| Trạng thái | .D (lỗi dùng chung kiểu GV-090 .X) |
| Tương tác | Google mở cửa sổ chọn tài khoản |
| Điều hướng | → SV-001 |
| Ràng buộc | Một tài khoản = một MSSV |

### SV-001 Buổi vắng của tôi · SV-002 Chi tiết môn (web)
| Mục | Nội dung |
|---|---|
| Bố cục | Điện thoại: logo + “Quick Attend” · avatar, tên, MSSV · băng cảnh báo hổ phách · DateHeader(“Fall 2026”, “Có mặt”) · thẻ môn (mã môn, lớp, RatioText “7/10”, ›) · thanh đáy Báo sai + Quét mã. Laptop (.W): đầu trang logo trái, avatar + tên phải; danh sách kéo hết ngang; gợi ý mờ “Quét mã trên điện thoại” ở chân · SV-002: “PRM393 · SE1801”, “7/10 buổi có mặt”, danh sách buổi + StatusChip, nút Báo sai |
| Component | InitialsAvatar, QaCard, RatioText, StatusChip, AppButton |
| Trạng thái | SV-001 .D, .D1, .D2, .W, .L, .E, .X · SV-002 .D, .W |
| Tương tác | Chạm môn → SV-002; chạm buổi Vắng → SV-102 |
| Điều hướng | Quét mã → SV-101; Báo sai → SV-102 |
| Ràng buộc | Ghi có mặt / đã học theo lịch; màu số: xanh (bình thường), hổ phách (còn 1 buổi), đỏ (vắng thêm 1 là cấm thi hoặc đã quá) |

### SV-101 Quét mã · SV-102 Gửi báo sai (web)
| Mục | Nội dung |
|---|---|
| Bố cục | 101: khung camera nền đen + khung ngắm, “Quét mã trên màn chiếu”, lớp đang quét · 102: môn, ngày, slot, chip Vắng, danh sách lý do (radio), ô Ghi thêm, nút Gửi |
| Component | `MobileScanner` (gói `mobile_scanner`), AppButton, AppTextField, EmptyState-style kết quả |
| Trạng thái | 101 .D, .S, .X mã hết hạn, .X2 cần quyền camera · 102 .D, .S |
| Tương tác | Quét xong tự chuyển .S; lý do bắt buộc |
| Điều hướng | Xong → SV-001 |
| Ràng buộc | Mã chỉ hợp lệ trong 12 giây và khi phiên còn mở; mỗi sinh viên ghi 1 lần mỗi phiên |
