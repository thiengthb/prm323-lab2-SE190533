# Flutter handoff

> v1.3 · 29/10/2026: thêm GV-A01..A03, SV-000, GV-001 .E2/.N, GV-003 .D2 (vòng đời). v1.2: mục 1 theo DESIGN.md v3.0. v1.0 · 20/10/2026. Hai bảng ánh xạ toàn cục (mục 1, 2) và đặc tả 6 mục cho từng màn (mục 3): bố cục, component, trạng thái, tương tác, điều hướng, ràng buộc. Tên khung Figma trang 03 trùng mã màn và trạng thái, ví dụ `GV-102 · Phiên điểm danh .D2`.
>
> **Giả định dữ liệu (Assumed, E-12):** app đọc lịch, lớp, danh sách và ảnh sinh viên từ FAP, ghi kết quả điểm danh về cùng nguồn đó. Bài lab không làm backend.

## 1. Token → Flutter

Theme: `ThemeData(useMaterial3: true, colorScheme: AppColors.scheme, textTheme: AppText.theme, fontFamily: 'Nunito')` (gói `google_fonts` hoặc font nhúng trong `pubspec.yaml`). Giá trị theo [DESIGN.md](../design/DESIGN.md) v3.0, khớp biến Figma ngày 29/10.

### Màu

| Token | Hex | Flutter |
|---|---|---|
| `color/bg`, `color/surface` | `#FFFFFF` | `ColorScheme.surface`, `surfaceContainerLowest` (Scaffold, Card, sheet, NavigationBar) |
| `color/muted-surface` | `#F4F4F4` | `ColorScheme.surfaceContainerHighest` (SegmentedButton nền, skeleton, ô ghi chú) |
| `color/border` = `color/edge` | `#E5E5E5` | `ColorScheme.outlineVariant` (viền 2 và gờ đáy thẻ) |
| `color/border-control` | `#8F8F8F` | `ColorScheme.outline` |
| `color/fg-strong` | `#1F1F1F` | `AppColors.fgStrong` (số lớn, tiêu đề) |
| `color/fg` | `#3C3C3C` | `ColorScheme.onSurface` |
| `color/fg-muted` | `#6B6B6B` | `ColorScheme.onSurfaceVariant` |
| `color/fg-disabled` | `#AFAFAF` | `AppColors.fgDisabled` |
| `color/primary` | `#B9551F` | `ColorScheme.primary` |
| `color/primary-pressed` = `color/edge-primary` | `#8A3D14` | `AppColors.primaryEdge` (gờ đáy nút chính, overlay khi nhấn) |
| `color/primary-soft` / `-soft-edge` | `#FBEFE8` / `#F9B98F` | `ColorScheme.primaryContainer` / `AppColors.primarySoftEdge` (chip chọn) |
| `color/on-primary-soft` | `#9A4518` | `ColorScheme.onPrimaryContainer` |
| `color/on-primary` | `#FFFFFF` | `ColorScheme.onPrimary` |
| `color/brand` | `#F26F21` | `AppColors.brand` (chỉ icon ứng dụng) |
| `color/success` / `-soft` | `#15803D` / `#ECFDF3` | `AppColors.success` / `successSoft` (ThemeExtension `StatusColors`) |
| `color/warning` / `-soft` | `#A15C00` / `#FFF6DD` | `AppColors.warning` / `warningSoft` (ThemeExtension) |
| `color/danger` / `-soft` | `#B42318` / `#FEF0EF` | `ColorScheme.error` / `ColorScheme.errorContainer` |
| `color/scrim` | `#1F1F1F` 50% | `ColorScheme.scrim` |

### Chữ (Nunito, 9 kiểu)

| Token | Cỡ / dòng / độ đậm | Flutter `TextTheme` |
|---|---|---|
| `type/display` | 28 / 34 / w700 | `displaySmall` (ghi đè cỡ 28) |
| `type/title-lg` | 22 / 28 / w700 | `titleLarge` |
| `type/title` | 17 / 24 / w700 | `titleMedium` (ghi đè cỡ 17) |
| `type/section` | 16 / 22 / w700 | `titleSmall` (ghi đè cỡ 16) |
| `type/body` | 15 / 22 / w500 | `bodyLarge` (ghi đè cỡ 15) |
| `type/body-strong` | 15 / 22 / w600 | `bodyLarge.copyWith(fontWeight: w600)` |
| `type/label` | 14 / 20 / w600 | `labelLarge` |
| `type/body-sm` | 13 / 18 / w500 | `bodyMedium` (ghi đè cỡ 13) |
| `type/caption` | 12 / 16 / w600 | `labelSmall` (nhãn NavigationBar) |

### Khoảng cách, bo góc, viền, kích thước

| Token | Giá trị | Flutter |
|---|---|---|
| `space/4..32` | 4, 8, 12, 16, 20, 24, 32 | `AppSpace.s4 … s32`; lề màn `EdgeInsets.symmetric(horizontal: 12)` |
| `radius/sm, md, lg, xl, full` | 6, 8, 8, 10, 999 | `AppRadius.*` → `BorderRadius.circular`, `StadiumBorder` |
| Viền và gờ thẻ | viền 2 `edge` + gờ đáy 2 | `Container(decoration: BoxDecoration(border: Border.all(width: 2, color: edge), borderRadius: r8, boxShadow: [BoxShadow(offset: Offset(0, 2), color: edge)]))` |
| Gờ nút chính | đáy 2 `edge-primary` | `FilledButton` bọc `DecoratedBox` có `BoxShadow(offset: Offset(0, 2), blurRadius: 0, color: primaryEdge)`; khi nhấn dịch xuống 2 và bỏ gờ |
| Bóng mờ | chỉ snackbar: 0 2, 35% đen | `SnackBar(elevation: 2)` |
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
| QR panel | — | `Card` + `QrImageView` (gói `qr_flutter`) + Status chip Neutral đếm lùi + `Text` |
| Status icons, Browser bar | — | Không dựng: là thanh hệ thống và thanh địa chỉ trình duyệt, chỉ có trên Figma để khung trông như máy thật |
| Icon (Lucide) | 29 icon | gói `lucide_icons_flutter`, `size 20/24` |

## 3. Đặc tả từng màn

Quy ước chung cho mọi màn:
- `Scaffold(backgroundColor: bg)`; thân là `ListView` padding ngang 20, khoảng cách nhóm 24, giữa thẻ 12. App bar và nút đáy cố định, thân cuộn.
- Nút đáy: `SafeArea` + `Padding(20)` + `FilledButton` cao 48 rộng hết.
- Mọi nút icon có `tooltip` (đọc màn hình); chip trạng thái bọc `Semantics(label: 'Vắng')`.
- **≥ 600 dp (tablet, xoay ngang):** thân giới hạn `ConstrainedBox(maxWidth: 560)` căn giữa; `NavigationBar` đổi thành `NavigationRail`. Không đổi bố cục khác.
- Ảnh sinh viên: `CircleAvatar(foregroundImage: NetworkImage(url))`, lỗi tải thì hiện chữ viết tắt; cache bằng `cached_network_image`.

### GV-A01 · Đăng nhập, GV-A02 · Đăng ký, GV-A03 · Xác nhận email
| Mục | Nội dung |
|---|---|
| Bố cục | Không app bar, không NavigationBar · hàng tiêu đề: App icon 48 + “Đăng nhập” / “Đăng ký” / “Xác nhận email” · [dòng phụ “Dùng email @fe.edu.vn”] · các Text field · nút đáy primary + dòng “Chưa có tài khoản? **Đăng ký**” |
| Component | App icon, Text field (Filled, Error), Button primary, `TextButton` cho link; A03: 6 ô `TextField` maxLength 1 hoặc gói `pinput` |
| Trạng thái | A01 .D · A01 .X lỗi dưới ô mật khẩu “Sai email hoặc mật khẩu”, giữ email · A02 .D · A02 .X lỗi dưới ô email “Chỉ nhận email @fe.edu.vn” · A03 .D nút tắt tới khi đủ 6 số, “Gửi lại mã sau 28 giây” |
| Tương tác | Bàn phím `TextInputType.emailAddress`; mật khẩu `obscureText`; kiểm đuôi email ngay khi rời ô; A03 tự chuyển ô khi gõ, dán được cả mã |
| Điều hướng | A01 → GV-001 (`pushReplacement`); A02 → A03 → GV-001 .E2 nếu kỳ hiện tại chưa có lớp; GV-004 “Đăng xuất” → A01 (xóa stack) |
| Ràng buộc | Chỉ email @fe.edu.vn (D-16); không lưu mật khẩu trên máy, lưu token bằng `flutter_secure_storage` |

### GV-100 · Thiết lập lần đầu
| Mục | Nội dung |
|---|---|
| Bố cục | Icon tải về trong vòng tròn 48 · tiêu đề “Nhập từ FAP” · danh sách lớp kỳ này (ô chọn) · nút đáy “Nhập 4 lớp” |
| Component | Empty-style header, `CheckboxListTile` × 4, Button primary, Error state |
| Trạng thái | .D chọn lớp · .L “Đã nhập 2/4 lớp”, nút loading “Đang xử lý” · .X giữ icon và tiêu đề “Nhập từ FAP”, Error state “FAP không phản hồi” + Thử lại ở giữa phần còn lại · .S “Đã nhập 4 lớp” + nút “Vào Tổng quan” |
| Tương tác | Bỏ chọn lớp thì số trên nút đổi theo (“Nhập 3 lớp”); 0 lớp thì nút tắt |
| Điều hướng | Chỉ hiện lần đầu; .S → GV-001 (`pushReplacement`) |
| Ràng buộc | Không cho tạo lớp tay (D-10) |

### GV-001 · Tổng quan
| Mục | Nội dung |
|---|---|
| Bố cục | App bar top-level “Tổng quan” + chuông · hàng ngày + “1/3 slot đã chốt” và thanh 3 đoạn cao 6 (`Row` các `Expanded(Container)` bo 3, khe 4; màu theo trạng thái slot: success / warning / primary / border) · [thẻ Chốt ngay nếu có] · thẻ slot đang diễn ra · nhóm “Cần chú ý” 2 hàng + “Xem tất cả” · nhóm “Còn lại hôm nay” · NavigationBar tab 1 |
| Component | App bar, Slot card (Unclosed, Live, Upcoming), Attention row, Bottom navigation, Skeleton, Empty state, Error state |
| Trạng thái | .D · .D1 slot chưa chốt lên đầu, viền hổ phách 2 · .L 3 skeleton theo hình thẻ · .E “Hôm nay không có slot” + Xem lịch · .E2 kỳ hiện tại chưa có lớp: chỉ Empty state “Fall 2026 chưa có lớp” + nút primary “Nhập lớp” · .N kỳ mới: băng primary-soft “Kỳ mới Spring 2027” + Empty state “Spring 2027 chưa có lớp” + “Nhập lớp” · .X mất mạng + Thử lại |
| Tương tác | Kéo xuống để tải lại; chạm thẻ → GV-101; nút trên thẻ đi thẳng vào GV-102 |
| Điều hướng | Chuông → GV-105; “Xem tất cả” → GV-104; hàng sinh viên → GV-201 |
| Ràng buộc | Một nút primary trên màn: nếu có thẻ Chốt ngay thì nút “Mở điểm danh” của thẻ live đổi sang outline. Kỳ hiện tại tính từ ngày máy: tháng 1–4 Spring, 5–8 Summer, 9–12 Fall + năm (D-18); kỳ chưa có lớp thì luôn hiện .E2 / .N |

### GV-002 · Lịch
| Mục | Nội dung |
|---|---|
| Bố cục | App bar “Lịch” · SegmentedButton Hôm nay / Ngày mai / Tuần · nhóm theo ngày, mỗi nhóm là các Slot card |
| Component | Segmented control, Slot card, Empty state |
| Trạng thái | .D1 hôm nay · .D2 ngày mai · .D3 tuần (cuộn) · .E không có slot |
| Tương tác | Đổi đoạn giữ vị trí cuộn về đầu; vuốt ngang giữa các đoạn (tùy chọn) |
| Điều hướng | Chạm thẻ → GV-101 |
| Ràng buộc | Lịch chỉ đọc, sửa lịch vẫn ở FAP |

### GV-003 · Lớp
| Mục | Nội dung |
|---|---|
| Bố cục | App bar “Lớp” · hàng chip chọn kỳ (kỳ hiện tại đứng đầu) · dòng “4 lớp đang dạy” · danh sách hàng lớp: môn · lớp · sĩ số · chip số em cần chú ý |
| Component | List row, Status chip (Warning, Over), Empty state |
| Trạng thái | .D · .D2 kỳ cũ: dòng “4 lớp · đã kết thúc, chỉ xem”, mở được chi tiết nhưng không có nút điểm danh · .E “Chưa có lớp nào” + nút “Nhập lớp” |
| Tương tác | Chạm hàng |
| Điều hướng | → GV-103; .E → GV-100 |
| Ràng buộc | Chip chỉ hiện khi có em cần chú ý |

### GV-004 · Tài khoản
| Mục | Nội dung |
|---|---|
| Bố cục | Thẻ giảng viên (avatar, tên, email) · nhóm “Nhắc nhở” 2 công tắc · Nhập lại từ FAP · Đăng xuất |
| Component | Card, `SwitchListTile` × 2, List row, Button ghost destructive |
| Trạng thái | .D |
| Tương tác | Công tắc lưu ngay, không cần nút Lưu; Đăng xuất có hộp xác nhận |
| Điều hướng | Nhập lại → GV-100 |
| Ràng buộc | Nhắc mặc định bật (D-03) |

### GV-101 · Chi tiết slot
| Mục | Nội dung |
|---|---|
| Bố cục | App bar nested · giờ (title-lg) · chip trạng thái · hàng icon + giá trị (môn, lớp, phòng, sĩ số) · [kết quả nếu đã chốt] · nút đáy |
| Component | App bar nested, Status chip, List row có icon, Stat, Button |
| Trạng thái | .D1 sắp tới: nút “Mở điểm danh” disabled · .D2 đang diễn ra: nút bật · .D3 đã chốt: “34 có mặt · 1 vắng” + nút outline “Sửa điểm danh” |
| Tương tác | Nút disabled vẫn có `tooltip` “Chưa tới giờ” |
| Điều hướng | Mở điểm danh → GV-102; Back → màn trước |
| Ràng buộc | Không hiện số có mặt khi chưa chốt (F7); sửa chỉ trong ngày |

### GV-102 · Phiên điểm danh (+ GV-OV1, GV-OV2)
| Mục | Nội dung |
|---|---|
| Bố cục | App bar nested “Điểm danh” · thẻ QR (`QrImageView` 200) + chip Neutral “Đổi mã sau 12s” (đếm lùi 15 → 1) + số “31/35” display + “đã quét”; .D2 thu thẻ QR thành một hàng “32/35 đã quét” + nút ghost “Mở lại” · nhóm “Chưa quét (3)” · nút đáy “Chốt điểm danh” |
| Component | QR panel, Student row (Exception, Marked present, Marked absent), Dialog (Confirmation, Destructive), Snackbar, Button loading |
| Trạng thái | .D1 mã đang mở · .D2 đã xử lý ngoại lệ · OV1 xác nhận “34 có mặt · 1 vắng” · .L nút loading · .X / OV2 “Chưa gửi được · Mất mạng · đã lưu trên máy” + Để sau / Thử lại · .S kết quả + Snackbar “Đã chốt” Hoàn tác 10 giây |
| Tương tác | ✓ / ✕ trên từng hàng, chạm lại để đổi; QR làm mới mỗi 15 giây (`Timer.periodic`); bộ đếm cập nhật qua stream |
| Điều hướng | Chốt → OV1 (`showDialog`) → .L → .S hoặc OV2; .S Back → GV-001 (slot thành Closed) |
| Ràng buộc | Không có ô nhập sĩ số (D-02); mất mạng thì giữ kết quả trong bộ nhớ máy, không xóa; người chưa quét và chưa đánh dấu tính là Vắng ở hộp xác nhận |

### GV-103 · Chi tiết lớp
| Mục | Nội dung |
|---|---|
| Bố cục | App bar nested “SE1801” · dòng “PRM393 · Fall 2026” · 3 thẻ số (sĩ số, buổi đã học, cần chú ý) · nhóm “Cần chú ý” · nhóm “Buổi gần nhất” |
| Component | Stat, Attention row, List row |
| Trạng thái | .D |
| Tương tác | Chạm hàng |
| Điều hướng | Sinh viên → GV-201; buổi → GV-101 .D3 |
| Ràng buộc | — |

### GV-104 · Cần chú ý
| Mục | Nội dung |
|---|---|
| Bố cục | App bar nested “Cần chú ý” · nhóm “Đã chạm ngưỡng (n)” · nhóm “Sắp chạm ngưỡng (n)” |
| Component | Attention row (Over, Near), Empty state |
| Trạng thái | .D · .E “Không có ai cần chú ý” + Về Tổng quan |
| Tương tác | Chạm hàng |
| Điều hướng | → GV-201 |
| Ràng buộc | Ngưỡng = 20% số buổi (E-22); “sắp” = còn 1 buổi; tên không bị cắt (xuống 2 dòng) |

### GV-105 · Yêu cầu sửa
| Mục | Nội dung |
|---|---|
| Bố cục | App bar nested · thẻ yêu cầu: avatar, tên, slot, lý do, 2 nút Từ chối (outline) / Duyệt (primary) |
| Component | Card, Avatar, Button, Empty state |
| Trạng thái | .D 2 yêu cầu · .D còn 1 sau khi duyệt · .E “Không có yêu cầu nào” + Về Tổng quan |
| Tương tác | Duyệt: thẻ biến mất + Snackbar Hoàn tác; Từ chối: hộp xác nhận |
| Điều hướng | Từ chuông GV-001 hoặc thông báo đẩy |
| Ràng buộc | Chỉ nhận yêu cầu trong ngày của slot |

### GV-OV4 · Thông báo nhắc chốt
| Mục | Nội dung |
|---|---|
| Bố cục | Thông báo hệ thống: icon app · “Điểm danh” · tiêu đề “PRM393 · SE1801 chưa chốt” · dòng “Slot 1 đã hết giờ” · một nút hành động “Chốt ngay” |
| Component | Không dựng UI: gói `flutter_local_notifications` (Android `AndroidNotificationAction('chot', 'Chốt ngay', showsUserInterface: true)`) |
| Trạng thái | .D duy nhất; slot đã chốt thì huỷ thông báo (`cancel(id)`) |
| Tương tác | Lên lịch `zonedSchedule` đúng giờ hết slot khi bật “Slot chưa chốt” ở GV-004; chạm thông báo hoặc nút → mở app |
| Điều hướng | Mở thẳng GV-102 .D2 của slot đó (payload là mã slot) |
| Ràng buộc | Tối đa một thông báo mỗi slot; không gửi nếu đã chốt |

### GV-201 · Hồ sơ sinh viên (+ GV-OV3)
| Mục | Nội dung |
|---|---|
| Bố cục | App bar nested “Hồ sơ” · header avatar 56 + tên + “SE190155 · PRM393 · SE1801” · thẻ số “3/4 buổi vắng” + thanh 4 ô + chip · nhóm “Buổi vắng” · nút đáy “Nhắc sinh viên” |
| Component | Avatar, Card, Status chip, List row, Bottom sheet, Snackbar |
| Trạng thái | .D · OV3 sheet tin nhắn mẫu có thể sửa + “Gửi” · .S nút thành “Đã gửi nhắc” (disabled) |
| Tương tác | Nhắc → `showModalBottomSheet`; Gửi → đóng sheet, Snackbar |
| Điều hướng | Back → GV-104 / GV-103 / GV-001 |
| Ràng buộc | Mỗi sinh viên nhắc tối đa 1 lần mỗi ngày |

### SV-000 · Đăng nhập (web)
| Mục | Nội dung |
|---|---|
| Bố cục | Thanh trình duyệt · giữa màn: App icon 64, “Quick Attend”, “Xem buổi vắng, quét mã điểm danh” · nút đáy “Đăng nhập tài khoản FPT” |
| Component | App icon, Button primary |
| Trạng thái | .D |
| Tương tác | Nút mở đăng nhập tài khoản FPT (@fpt.edu.vn) của trường, quay về SV-001 |
| Điều hướng | → SV-001; mở link quét mã khi chưa đăng nhập thì qua SV-000 trước rồi về SV-101 |
| Ràng buộc | Không có đăng ký riêng cho sinh viên (D-17) |

### SV-001 · Buổi vắng của tôi (web)
| Mục | Nội dung |
|---|---|
| Bố cục | Header “Buổi vắng” + “Lê Gia Huy · SE190601” · [băng cảnh báo] · danh sách môn: mã môn, lớp, “3/4 buổi” · 2 nút đáy “Báo sai” (outline) / “Quét mã” |
| Component | Banner, List row, Button |
| Trạng thái | .D mọi môn ổn · .D1 băng hổ phách “PRM393 còn 1 buổi được vắng” · .D2 băng đỏ “đã chạm ngưỡng 4/4” |
| Tương tác | Chạm môn mở danh sách buổi vắng (ngoài phạm vi lab) |
| Điều hướng | Quét mã → SV-101; Báo sai → SV-102 |
| Ràng buộc | Web (Flutter web hoặc web thường), một cột, không thanh điều hướng; đăng nhập ở SV-000. Bản laptop (.W): tiêu đề “Buổi vắng · Fall 2026”, tên và MSSV ở góc phải cạnh ảnh đại diện |

### SV-101 · Quét mã (web)
| Mục | Nội dung |
|---|---|
| Bố cục | Khung camera 320 × 400 + khung quét 220 · dòng “Đưa mã vào khung” |
| Component | Camera (`mobile_scanner`), hero kết quả, Status chip, Button |
| Trạng thái | .D camera · .S “Đã ghi nhận” + “PRM393 · Slot 1 · 07:01” + chip Có mặt + “Còn được vắng 2 buổi” · .X “Mã đã hết hạn · Mã đổi sau mỗi 15 giây” + Quét lại |
| Tương tác | Quét xong tự chuyển trạng thái, rung nhẹ |
| Điều hướng | Xong → SV-001 |
| Ràng buộc | Cần quyền camera; từ chối quyền thì hiện Error state “Cần quyền camera” |

### SV-102 · Gửi báo sai (web)
| Mục | Nội dung |
|---|---|
| Bố cục | Hàng slot đang ghi Vắng · ô “Lý do” · nút đáy “Gửi” |
| Component | List row + chip Absent, Text field, Button |
| Trạng thái | .D · .S “Đã gửi” |
| Tương tác | Lý do bắt buộc, trống thì Text field ở trạng thái Error |
| Điều hướng | .S → SV-001 |
| Ràng buộc | Chỉ gửi trong ngày của slot; yêu cầu tới GV-105 |
