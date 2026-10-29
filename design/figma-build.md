# Nhật ký dựng Figma

File: [PRM323 Lab 2 v2 · SE190533 · Điểm danh cho giảng viên](https://www.figma.com/design/1qIZVpL0Q7bD9UzT5TVBRy). Dựng bằng Figma MCP (Plugin API) từ Claude Code, thien duyệt. Thứ tự dựng theo trình tự thầy yêu cầu: style guide → component → wireframe → (Stitch) → final UI → prototype.

| Ngày | Trang | Việc | Kết quả |
|---|---|---|---|
| 20/10 | Cả file | Tạo 6 trang đúng thứ tự đề | 01 User Flow · 02 Wireframe · 03 Final UI · 04 Design System · 05 Components · 06 Prototype |
| 20/10 | 04 | Biến token từ DESIGN.md v1.0 | Collection Color (20 biến, mode Light), Spacing (7), Radius (4), Size (4); 7 text style Inter; 2 effect style elevation. Mọi biến có scope riêng |
| 20/10 | 05 | 29 icon Lucide (nét 2) làm component, nét gắn biến `color/fg` | `Icon/*` |
| 20/10 | 05 | Component có Auto Layout và variant, mọi màu, padding, gap, bo góc gắn biến | Button (4 kiểu × 4 trạng thái), Status chip (6), Text field (5), Card (2), Avatar, Student row (4), Attention row (2), Slot card (4), App bar (3), Bottom navigation (4), Segmented control (3), Dialog (2), Snackbar, Loading/Skeleton, Empty state, Error state, QR panel |
| 20/10 | 04 | Trang mẫu token | Màu, chữ, khoảng cách, bo góc, đổ bóng, tất cả gắn biến |
| 20/10 | 02 | Wireframe lo-fi thang xám | 14 màn (11 app giảng viên, 3 web sinh viên) |
| 20/10 | 01 | 4 flow, mỗi flow có đường chính, nhánh khác, lỗi và phục hồi | FL-1..FL-4, mỗi bước ghi mã màn |
| 20/10 | 04 | Đổi bảng màu sang Đen trắng (D-01, DESIGN.md v1.1) | 5 biến `color/primary*` đổi giá trị; mọi component và màn đổi theo vì đều gắn biến |
| 20/10 | 03 | Final UI 360 × 800, mỗi màn một Section, trạng thái đặt cạnh nhau, chú thích ngoài khung | 14 màn, 41 khung trạng thái (kể cả GV-OV1..3); Section “Kiểm tra 412 dp” với 4 khung clone. Kiểm bằng script: chữ nhỏ nhất 14, mọi điều khiển cao ≥ 48 ([design-decisions.md](design-decisions.md) mục 2) |
| 20/10 | 06 | Prototype | 4 flow, 5 điểm bắt đầu (FL-1, FL-2, FL-3, FL-4, FL-4b), 73 điểm chạm, lớp phủ GV-OV1..3 có nền mờ chạm để đóng. Khung đặt trên cùng trang (Plugin API không cho nối tới khung nằm trong Section) |
| 20/10 | 03, 04, 06 | Soi ảnh từng khung (xuất qua Figma MCP) và sửa lỗi hiển thị | Lớp phủ tối đặc thành mờ 50% để thấy màn phía sau; chữ viết tắt avatar khớp tên (72 chỗ); GV-001 .X ngày về đầu màn; GV-002 .D3 chip “Đã chốt” xuống dòng, hết cắt chữ; GV-102 bỏ icon QR ở thẻ đếm cho “đã quét” không bị cắt; GV-102 .D1 thành 31/35 với 4 hàng chưa quét cho khớp số; trang 04 đổi tiêu đề và mã màu sang Đen trắng. Ảnh lưu ở [assets/figma/](../assets/figma/) |
| 20/10 | 03, 06 | Soát ngày khi phản biện IT-1, IT-2 (F15) | 24 lớp chữ ghi “Thứ Hai, 20/10” sửa thành “Thứ Ba, 20/10” (20/10/2026 là thứ Ba), kéo theo 21/10 Thứ Tư, 22/10 Thứ Năm; xuất lại 12 ảnh GV-001, GV-002, GV-101 |
| 22/10 | 03, 05, 06 | Đợt hoàn thiện sau khi soi lại 41 khung | Component mới Status icons (sóng, wifi, pin; 88 thanh trạng thái) và Browser bar (16 khung web SV-*); GV-001 .D, .D1 thêm “x/3 slot đã chốt” + thanh 3 đoạn; QR panel thêm chip “Đổi mã sau 12s”, padding 16 để danh sách GV-102 .D1 không bị thanh đáy che; GV-100 .X giữ tiêu đề “Nhập từ FAP” |
| 22/10 | 03, 06 | Thêm GV-OV4 thông báo nhắc chốt trên màn khoá (D-03 trước đây chỉ có chữ, chưa có khung) | Section mới trên trang 03; trang 06 thêm khung, nút “Chốt ngay” và thẻ thông báo dẫn tới GV-102 .D2, điểm bắt đầu mới FL-2b |
| 22/10 | 03, 05, 06 | Ảnh đại diện thật theo D-06 (trước đó là chữ viết tắt) | 7 ảnh chân dung cắt từ ảnh render Stitch IT-3 ([assets/stitch/IT-3/avatars/](../assets/stitch/IT-3/avatars/)), nạp vào khung “Avatar photos” trang 05, gắn vào 40 avatar trang 03 và 53 avatar trang 06; Bùi Lan Anh (GV-105) và giảng viên (GV-004) giữ chữ viết tắt làm mẫu dự phòng khi thiếu ảnh. Xuất lại 19 ảnh |
| 22/10 | 03, 04, 05, 06 | Làm đẹp lại theo góp ý của thien (D-11, D-12) | 14 biến màu đổi sang Xanh đại dương (scrim giữ 50%); Slot card .Live thành thẻ nền primary, nút trắng; Attention row bỏ chip và “buổi vắng”, thêm icon trạng thái cạnh số; Student row ẩn mã SV; 60 lớp chữ phụ ẩn trên trang 03 và 06; thẻ đếm “32/35” nền primary-soft; trang 04 đổi tiêu đề và mã màu. Xuất lại 53 ảnh |
| 29/10 | 01, 02, 03, 05, 06 | Vòng 4 nhóm D, E và vòng đời app (D-15..D-19) | 03: 9 khung mới (GV-A01 .D/.X, GV-A02 .D/.X, GV-A03, SV-000, GV-001 .E2/.N, GV-003 .D2), sửa nhóm E, MSSV mẫu; 02: 6 wireframe mới (18 màn); 01: khối FL-0 và SV-000 vào FL-4; 05: App icon dùng `color/primary`; 06: 8 khung mới, 7 điểm bắt đầu, 95 điểm chạm, Đăng xuất về Đăng nhập |
