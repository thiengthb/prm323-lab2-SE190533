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
