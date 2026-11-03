# Final UI v2 · Hereby: những gì thay bản v3.1

> v1.0 · 03/11/2026. Figma trang `03 Final UI · v2` (`239:4208`), luồng ở `01 User Flow · v2` (`317:2`), đường bấm ở `06 Prototype · v2` (`284:2`).
>
> **Ưu tiên:** chỗ nào file này khác [DESIGN.md](DESIGN.md) v3.1, [screen-spec.md](screen-spec.md) v2.0, [flutter-handoff.md](../handoff/flutter-handoff.md) v2.0 hay [user-flow.md](../ux/user-flow.md) v1.0, thì theo file này. Phần không nhắc tới thì giữ như bản cũ.
>
> Bản dựng Flutter nằm ở repo Lab 3 [PRM393_Lab03_SE190533](https://github.com/thiengthb/PRM393_Lab03_SE190533), nhánh `ui-v2`. Bảng truy vết từng màn sang route, widget và id khung Figma ở `docs/design-traceability.md`. Khác biệt chỉ do lúc dựng (D-L3-xx) ghi ở mục 4 của file đó, không ghi ở đây.
>
> Lý do của từng thay đổi nằm trong `lessons/LAB2-ban-giao.md` đến `-5`. Các file này chưa có trên GitHub.

## 1. Tên và logo

- Tên app: **Hereby**, thay Quick Attend. Mã ứng dụng Android giữ `vn.edu.fpt.quick_attend`.
- Logo: người giơ tay, component `App icon v2 · Hereby` (`262:2800`). Dùng cho icon launcher, favicon và logo trên màn đăng nhập.

## 2. Màu

Mặc định là mẫu **A Biển sâu**. Giá trị lấy từ bộ biến `Color` trên Figma, mode `Mẫu A Biển sâu`. Mode `Light` là bảng cam cũ, nay là mẫu Cam FPT.

| Token | Biển sâu (mặc định) | Cam FPT (bản v3.1) |
|---|---|---|
| `color/primary`, `color/brand` | `#0B4F71` | `#B9551F`, brand `#F26F21` |
| `color/primary-pressed` = `color/edge-primary` | `#07354E` | `#8A3D14` |
| `color/primary-soft` | `#DCEDF5` | `#FBEFE8` |
| `color/on-primary-soft` | `#0A4664` | `#9A4518` |
| `color/primary-soft-edge` | `#9CC9DF` | `#F9B98F` |
| `color/warning-soft-edge` (mới) | `#E8CB7F` | `#E8CB7F` |

Các token còn lại không đổi so với DESIGN.md mục 3: nền, chữ, viền, success, warning, danger, scrim, camera.

Tương phản của Biển sâu, đều trên mức 4,5 mà chữ thường cần:

| Cặp màu | Tương phản |
|---|---|
| Chữ trắng trên primary | 8,86 |
| on-primary-soft trên primary-soft | 8,43 |
| warning trên warning-soft | 4,81 |
| fg-muted trên muted-surface | 4,85 |
| danger trên danger-soft | 5,92 |
| success trên success-soft | 4,76 |

Viền `warning-soft-edge` chỉ đạt 1,47. Vì vậy, dải vàng luôn phải có chữ, không chỉ dựa vào màu.

**Chọn màu** (GV-004, khung `301:4751`) có 8 mẫu: Biển sâu, Cam FPT, Hải quân, Đại dương, Mòng két, Chàm, Mận, Than.

- Hải quân và Đại dương có đủ giá trị ở mode `Mẫu B Hải quân` và `Mẫu C Đại dương`.
- Bốn mẫu còn lại trên Figma chỉ có màu chính.

Chỉ các token primary đổi theo mẫu. Màu trạng thái giữ nguyên ở mọi mẫu.

## 3. Luật chung thay đổi

| Phần | v3.1 | v2 |
|---|---|---|
| Thẻ | Một kiểu: viền 2 + gờ đáy 2 | **Hai kiểu.** Thẻ bấm được thì nổi, có viền 2 và gờ đáy 2. Thẻ chỉ để xem thì chìm: nền `muted-surface`, không viền |
| Ô số | Stat tile một kiểu | `Stat card v2` (`248:2306`). Loại **Thông tin** là thẻ chìm, có ô icon primary-soft. Loại **Bấm được** có nền primary-soft, gờ primary-soft-edge và mũi tên |
| Thanh tab | Tổng quan · Lịch · Lớp · Tài khoản, icon 24 | `Bottom navigation v2` (`266:4185`), cao 72, chỉ có icon 26 trong ô 52 bo 8. Bốn tab: Tổng quan · **Điểm danh** (icon QR) · Lớp · Tài khoản (icon bánh răng). Nhãn tab không hiện, nhưng vẫn có cho trình đọc màn hình |
| Công tắc có mặt | Material | Rãnh 44 × 26 bo 8, xanh success khi bật, xám `fg-disabled` khi tắt. Núm trắng 20 × 20 bo 6, cách mép 3 |
| Chữ | “cấm thi”, “Chú ý” | “fail”, “Vắng nhiều” |

## 4. Màn hình

**Thêm**

| Mã | Màn | Khung |
|---|---|---|
| TV-001 | Màn chiếu trên máy chiếu phòng học, mở bằng link, không đăng nhập. Ba trạng thái: .E chưa mở điểm danh, .D đang chiếu mã, .D1 đã đóng mã | `259:2954`, `256:2890`, `307:4538` |
| GV-102 sheet | Chiếu lên TV: link màn chiếu kèm nút Chép link | `339:5337` |
| GV-OV6 | Danh sách slot chưa chốt, mở từ dải quên chốt ở Tổng quan | `307:4982` |
| SV-101 Nhập mã | Sinh viên gõ mã 6 số đang hiện trên TV | `259:3108` |
| GV-004 Chọn màu | Sheet chọn 1 trong 8 mẫu màu | `301:4751` |

**Bỏ**

| Mã | Thay bằng |
|---|---|
| GV-101 Chi tiết slot | Chạm thẻ slot mở thẳng GV-102. Slot chưa chốt mở .D2, slot đã chốt mở .S. Slot sắp tới không chạm được |
| GV-OV1 hộp xác nhận chốt | Chốt một lần, không hỏi lại. Vẫn có Hoàn tác |
| GV-OV2 hộp lỗi mạng | Dải vàng .X ở đầu màn, có Thử lại |

**Đổi**

| Màn | Thay đổi chính |
|---|---|
| GV-001 Tổng quan | Ngày và kỳ đổi chỗ; ô số có icon; ô yêu cầu sửa là ô bấm được. Thêm lịch tháng có chấm (chạm ngày sang tab Điểm danh), thẻ chưa chốt, dải quên chốt .D3, dải nhiều slot .D4. .X mất mạng giữ dữ liệu cũ kèm dải vàng. Nhóm Chú ý đổi tên thành Vắng nhiều |
| GV-002 Điểm danh (tab 2, trước là Lịch) | Bỏ Hôm nay / Tuần / Tháng. Thay bằng hàng chuyển tuần, chip tuần và dải T2 đến CN; chạm ngày để xem slot |
| GV-102 Phiên điểm danh | Tách nút: **Đóng mã** khi đang mở (.D1), **Chốt** khi đã đóng (.D2). Dưới QR có mã số 6 chữ và chip Đổi mã. Thêm nút Chiếu lên TV. Danh sách đã quét gộp thành hàng **Có mặt (n)** mở ra được. “Mở lại” đổi thành “Mở lại mã”. .D3 hết giờ thì báo đã đóng mã |
| GV-003 Lớp | Chọn kỳ bằng nút nền xám; ô icon lớp xanh nhạt; thêm .E |
| GV-103 Chi tiết lớp | Ô số có icon, số vắng đổi màu theo mức. Tab Buổi học dùng thẻ chìm, vẫn mở được buổi đã chốt để sửa |
| GV-104 Vắng nhiều (trước là Chú ý), GV-201, GV-OV3 | Chip Đã fail. Em đã fail không có nút Nhắc nhở. Lời nhắc nói rõ còn được vắng bao nhiêu buổi. Nút đổi thành “Đã nhắc · ngày” |
| GV-100 Nhập lớp | Khung chọn file thấp hơn. Màn lỗi có nút chính Chọn file khác và nút “Bỏ n dòng lỗi” |
| GV-004 Tài khoản | Hồ sơ là thẻ chìm, nhóm hàng nằm trong một thẻ. Thêm nhóm Giao diện (Chọn màu). Đăng xuất tách riêng |
| SV-001 Buổi vắng của tôi | Mỗi môn đếm buổi vắng trên số buổi được vắng, thay cho số có mặt. Dải hổ phách hoặc đỏ theo mức. Bỏ nút Báo sai ở danh sách. Thêm .D3 |
| SV-002 Chi tiết môn | Icon tick hoặc x ở đầu hàng. Buổi vắng là thẻ nổi có Báo sai. .D1 ghi kết quả báo sai. Buổi bị từ chối không báo lại được |
| SV-101 Quét mã | Nền camera, nút Nhập mã. .S có dải còn được vắng theo ba mức. .X2 chặn camera có lối Nhập mã |
| SV-102 Gửi báo sai | Thẻ chìm, nút Gửi ở thanh đáy, màn Đã gửi có dòng buổi |

## 5. Luồng thay đổi

| Luồng | v1.0 | v2 |
|---|---|---|
| FL-1 Điểm danh một slot | GV-001 → GV-101 → GV-102 → OV1 → .S | GV-001 (thẻ slot đang diễn ra) → GV-102 .D1 → Đóng mã → .D2 → Chốt → .S. Có thể bấm Chiếu lên TV để mở TV-001 trên máy chiếu |
| FL-2 Không quên chốt | GV-001 .D1, GV-002 .D2 Lịch tuần | Dải quên chốt ở GV-001 (một slot mở thẳng GV-102, nhiều slot mở GV-OV6) và tab Điểm danh, đều vào GV-102 .D2 |
| FL-4 Sinh viên quét mã | SV-101 quét | SV-101 quét QR, hoặc **Nhập mã** 6 số đang hiện trên TV |
