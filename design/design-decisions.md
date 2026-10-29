# Quyết định thiết kế và checklist accessibility

> v1.1 · 29/10/2026 (thêm D-13..D-15; checklist tương phản theo bảng màu v3.0 ở [DESIGN.md](DESIGN.md) mục 3). v1.0 · 20/10/2026. Mỗi quyết định có lý do truy về bằng chứng (E-xx trong [ma trận](../research/02-evidence-matrix.md)), phản biện AI (F-xx, A-xx trong [AI-04](../ai/critique/AI-04-critique-IT-0.md)) hoặc heuristic Nielsen (H1–H10). Tối đa 10 quyết định.

## 1. Quyết định

| Mã | Quyết định | Vì sao | Phương án đã bỏ | Màn bị ảnh hưởng |
|---|---|---|---|---|
| D-01 | *(Đã thay bằng D-11 ngày 22/10)* Bảng màu **Đen trắng** (shadcn mặc định): primary `#18181B`, còn lại trung tính; chỉ 3 màu trạng thái | IT-0 có 5 họ màu, không ra chất shadcn (F3); thầy chê bảng màu FAP. thien chọn trong 3 phương án ngày 20/10 | Indigo `#4F46E5` (gần xanh FAP), Teal (lẫn với xanh “Có mặt”), Violet `#7C3AED` (v1.0) | Mọi màn; [DESIGN.md](DESIGN.md) v1.1 |
| D-02 | **Không đếm sĩ số.** Lớp tự quét QR, bộ đếm tự chạy, giảng viên chỉ xử lý người chưa quét | Thầy nhớ mặt khoảng 35 sinh viên (E-04); sai sót nằm ở ngoại lệ (E-06); giữ A3, A4 của Stitch | Bước đếm và đối chiếu sĩ số của v1 | GV-102 |
| D-03 | Slot chưa chốt hiện thẻ **Chốt ngay** đầu Tổng quan (GV-001 .D1) và có nhắc đẩy | Quên điểm danh bị trừ lương (E-01); giảng viên quên thật và phát hiện muộn 1–2 ngày (E-09, E-10); giữ A2 của Stitch | Chỉ có danh sách lịch, để giảng viên tự nhớ | GV-001, GV-101, GV-004, GV-OV4 |
| D-04 | Chốt có **hộp xác nhận** kèm kết quả, xong có **Hoàn tác**; mất mạng thì giữ kết quả trên máy và **Thử lại** | Ngăn lỗi (H5), phục hồi (H9), người dùng làm chủ (H3); E-06 | Chốt một chạm không xác nhận | GV-102, GV-OV1, GV-OV2 |
| D-05 | “Cần chú ý” dẫn tới hành động **Nhắc sinh viên**, không xuất báo cáo | Thầy muốn chăm sóc sinh viên, không chỉ xem số (E-05); bỏ “Xuất báo cáo” của Stitch (F9) | Báo cáo % chuyên cần, nút xuất file | GV-104, GV-201, GV-OV3 |
| D-06 | **Ảnh đại diện** trên mọi hàng sinh viên | Nhận mặt nhanh hơn đọc mã (E-04); giữ A1 của Stitch | Chữ viết tắt (chỉ dùng khi thiếu ảnh) | GV-102, GV-104, GV-201 |
| D-07 | **Không câu giải thích trên màn**; giải thích để ở chú thích Figma ngoài khung | Thầy chê nhiều chữ; Stitch lặp lại lỗi này (F4, F7, F9); luật T1, T5 | Đoạn hướng dẫn ngắn dưới tiêu đề | Mọi màn |
| D-08 | Sinh viên dùng **web 3 màn**, không cài app; web chủ động báo khi sắp chạm ngưỡng | Theo hướng thầy (E-20); sinh viên hiếm khi tự xem và không nhớ chắc số buổi được vắng (E-25, E-26) | App sinh viên đầy đủ | SV-001, SV-101, SV-102 |
| D-09 | **Mã màn kèm trạng thái**: `GV-<cấp><số> · Tên .D/.D1/.L/.E/.X/.S`; lớp phủ là `GV-OV<n>` | Thầy chê mã màn v1 không phân biệt trạng thái | Một mã cho mọi trạng thái | Mọi khung trên Figma trang 03 |
| D-10 | Lần đầu dùng: **nhập lớp và lịch từ FAP** (GV-100), không tạo lớp tay | Lớp và lịch đã có ở FAP (E-12); giảm việc nhập | Màn tạo lớp, nhập danh sách tay | GV-100, GV-003 |
| D-11 | Bảng màu **Xanh đại dương**: primary petrol `#0B6283`, nền và chữ ngả lạnh; thẻ slot đang diễn ra nền primary, chữ trắng; thay D-01 | thien thấy bản Đen trắng chưa đẹp: cả màn chỉ có xám, không có điểm nhìn (22/10). Một màu nhấn đậm cho đúng một thẻ quan trọng nhất mỗi màn; chữ trắng trên primary 6,8:1 | Cam thương hiệu FPT (lẫn với hổ phách “Sắp chạm ngưỡng”); giữ Đen trắng, chỉ bớt chữ | Mọi màn qua biến `color/*`; Slot card .Live; [DESIGN.md](DESIGN.md) v2.0 |
| D-12 | **Bớt chữ lần hai** (60 lớp chữ ẩn trên trang 03 và 06): hàng Cần chú ý chỉ còn tên + icon + “3/4”; bỏ mã SV trong danh sách điểm danh và yêu cầu sửa; bỏ “Tự động có mặt”, “Ngưỡng: 4 buổi vắng”, “Slot 1” ở chi tiết slot, “Vắng” dưới ngày ở hồ sơ, “buổi” ở web SV; “0/3 slot đã chốt” thành “0/3 đã chốt” | Thầy chê nhiều chữ; luật T4, T5 và “không lặp một thông tin hai chỗ”: chip “Sắp chạm ngưỡng” lặp tiêu đề nhóm, chữ “buổi vắng” lặp số | Giữ chip và nhãn đơn vị | GV-001, GV-101, GV-102, GV-103, GV-104, GV-105, GV-201, SV-001 |
| D-13 | Hướng **C · Nổi khối, cam FPT**: viền 2 + gờ đáy 2, Nunito, primary cam đất `#B9551F`; thay D-11 | Chọn trong 3 hướng thử ngày 26/10 (trang Figma `00 Hướng`: A Đại dương mềm, B Gọn dòng thời gian, C Nổi khối). Cam đất (không phải cam FPT gốc `#F26F21`) để chữ trắng trên nút đạt 4,79:1 | A (thẻ nổi, bo 20–24, lời chào); B (trục giờ, viền mảnh); giữ Xanh đại dương | Mọi màn qua biến `color/*`, 9 kiểu `type/*`; [DESIGN.md](DESIGN.md) v3.0 |
| D-14 | **Luật chung sau 4 vòng duyệt từng màn** (27–29/10): chữ chỉ 9 kiểu, lề màn 12, icon 20/24; ngày luôn ghi đủ thứ (“Thứ Ba, 20/10”); trạng thái trống, xong, lỗi cùng một bố cục icon trên chữ dưới; lý do từ chối là chip chung; bỏ màn thông báo và nút chuông (nhắc là thông báo đẩy của điện thoại); nhập lớp bằng file Excel/CSV có file mẫu | thien chấm từng màn trên trang duyệt (OK / Cần sửa / Chưa chắc); nhất quán (H4), ít chữ (T5) | Mỗi màn một kiểu chữ, một kiểu trạng thái riêng; màn thông báo trong app | Mọi màn; GV-100, GV-004, GV-105, GV-OV5, SV-* |
| D-15 | Vòng 4 nhóm E: bỏ nút đèn trên camera quét mã; cảnh báo 4/4 rút còn “PRM393: vắng thêm 1 buổi là cấm thi”; **MSSV mẫu là mã giả, mỗi sinh viên một mã** (SE190601 cho Lê Gia Huy thay MSSV thật của thien) | Mã QR chiếu trên màn sáng, đèn chỉ gây lóa; một câu thay hai câu (T5); dữ liệu mẫu trùng mã (Lê Gia Huy, Đặng Minh Tú cùng một mã; Hoàng Minh Đức trùng Lê Thu Trang) làm người chấm nghi dữ liệu sai | Giữ nút đèn; giữ hai câu | SV-101, SV-001, GV-102, GV-103, 05 Components |

## 2. Checklist accessibility

Kiểm bằng script đọc thuộc tính node trên Figma trang 03 (20/10/2026) và công thức tương phản WCAG 2.x.

| # | Tiêu chí | Ngưỡng | Kết quả | Bằng chứng |
|---|---|---|---|---|
| A-1 | Tương phản chữ thường | ≥ 4,5:1 | Đạt | Bảng màu v3.0 (29/10): `fg` 11,03; `fg-strong` 16,48; `fg-muted` 5,33 trên trắng, 4,85 trên `muted-surface`; chữ trắng trên nút primary 4,79, khi nhấn 7,61; `on-primary-soft` 5,75 |
| A-2 | Tương phản chữ trạng thái | ≥ 4,5:1 | Đạt | Có mặt 4,76; cảnh báo 4,81 (5,19 trên trắng); vắng 5,92 (trên nền soft); chữ trắng trên nút destructive 6,57 |
| A-3 | Tương phản thành phần điều khiển | ≥ 3:1 (WCAG 1.4.11) | Đạt | Viền ô nhập, radio `#8F8F8F` 3,23; nút primary `#B9551F` 4,79 trên trắng |
| A-4 | Cỡ chữ tối thiểu | ≥ 14 | Đạt | 653 lớp chữ hiển thị trên trang 03, nhỏ nhất 14 (đo lại 22/10 sau khi bớt chữ lần hai, D-12) |
| A-5 | Vùng chạm | ≥ 48 × 48 dp | Đạt | 53 Button cao ≥ 48; Segmented 48; nút icon app bar 48 × 48 (41 app bar); Student row ≥ 64; Attention row ≥ 80; 63 hàng danh sách ≥ 64; Bottom navigation 72 |
| A-6 | Không truyền tin chỉ bằng màu | Icon + chữ kèm màu | Đạt | Mọi Status chip có icon 16 + chữ (luật T3) |
| A-7 | Bề rộng khác | 360 và 412 dp không vỡ | Đạt | 4 khung clone ở 412 dp (GV-001 .D, GV-102 .D2, GV-104 .D, SV-001 .D1): Auto Layout fill, không tràn, không chữ đè |
| A-8 | Nội dung không chồng lấn | Không đè ở 360 dp | Đạt, 1 ghi chú | Chip đè ở Stitch IT-0 (F2) đã sửa bằng Slot card. GV-002 .D3 (Tuần) dài hơn 800 khoảng 25 px: cuộn tự nhiên, app bar và thanh dưới cố định |
| A-9 | Tiếng Việt có dấu | Mọi chữ có dấu | Đạt | Lỗi “Tong Quan” ở IT-0 (F1) đã sửa |
| A-10 | Nhãn cho nút icon | Có nhãn đọc màn hình | Giao cho dev | Nút chuông, quay lại cần `tooltip` / `Semantics(label)`; ghi ở [flutter-handoff.md](../handoff/flutter-handoff.md) |
