# AI-04 · Phản biện Stitch IT-0

- **Đầu vào:** 4 màn Stitch sinh từ prompt [AI-03](../prompts/AI-03-stitch-IT-0.md), lưu ở [assets/stitch/IT-0/](../../assets/stitch/IT-0/) (ảnh PNG và HTML Stitch xuất ra).
- **Ai làm:** Claude soi từng màn theo 10 heuristic của Nielsen (H1–H10), accessibility (WCAG 2.x, luật trong [DESIGN.md](../../design/DESIGN.md)) và persona [P-01, P-02](../../ux/persona.md); nhóm quyết định Accept / Modify / Reject.
- **Bằng chứng:** cỡ chữ và nội dung lấy từ HTML Stitch xuất ra (ví dụ `text-[11px]` ở `03-phien-diem-danh.html`), không đoán từ ảnh.

## Phát hiện

| # | Màn (file IT-0) | Vấn đề quan sát được | Căn cứ | Mức | Quyết định | Sửa ở đâu |
|---|---|---|---|---|---|---|
| F1 | GV-001 Tổng quan (`01-tong-quan`) | Tiêu đề “Tong Quan” mất dấu; app bar có thêm logo và avatar không ai yêu cầu | T7 (tiếng Việt có dấu); H8 tối giản | Vừa | **Modify**: giữ app bar, bỏ logo, avatar chuyển vào tab Tài khoản | IT-1, Figma GV-001 |
| F2 | GV-001 (`01-tong-quan`) | Chip “Chưa bắt đầu” đè lên chip phòng ở hàng slot sắp tới (lỗi bố cục) | H8; WCAG 1.4.10 (nội dung không chồng lấn) | Cao | **Modify**: dùng component Slot card, chip trạng thái ở hàng riêng | Figma component Slot card |
| F3 | Cả 4 màn | 5 họ màu (tím Material 3, xanh lá, cam, đỏ, nền ngả tím `#fbf8fc`); thẻ “1 slot chưa chốt” tô kín màu cam | Kỷ luật màu DESIGN.md mục 3; H8 | Cao | **Modify** → quyết định [D-01](../../design/design-decisions.md): đổi sang Đen trắng | DESIGN.md v1.1, token Figma, IT-1 |
| F4 | GV-102 Phiên điểm danh (`03-phien-diem-danh`) | Đoạn giải thích cách quét QR và câu “Giảng viên đối chiếu & chạm nhanh” | T1 (không câu giải thích); H8 | Vừa | **Reject** phần chữ đó | IT-1 |
| F5 | GV-102 (`03-phien-diem-danh`) | Chữ 11–12 px (“Bàn 03”, “Đổi mã sau 9s”, 18 chỗ `text-xs`) | Luật cỡ chữ ≥ 14 (DESIGN.md mục 4); P-01 nhìn điện thoại nhanh giữa giờ | Cao | **Modify**: bỏ “Bàn”, nhãn đổi mã đưa lên 14 | Figma GV-102, IT-1 |
| F6 | GV-102 (`03-phien-diem-danh`) | Phần trăm và thanh tiến độ lặp lại đúng thông tin của bộ đếm “32/35” | Luật 8 “không lặp thông tin”; T4 số là chữ chính | Thấp | **Reject** thanh tiến độ và % | IT-1 |
| F7 | GV-101 Chi tiết slot (`02-chi-tiet-slot`) | Hiện số có mặt / vắng khi chưa mở điểm danh; có đoạn “Lưu ý FPT … cấm thi final” | H1 trạng thái hệ thống phải đúng; H2 khớp thực tế; T1 | Cao | **Modify**: số liệu chỉ có ở trạng thái .D3 đã chốt; bỏ đoạn lưu ý | Figma GV-101 .D1/.D2/.D3, IT-2 |
| F8 | GV-101 (`02-chi-tiet-slot`) | Hàng “Nhãn: giá trị” (Môn học:, Lớp:, Phòng:) tốn chữ | T5 ngân sách 25 từ | Thấp | **Modify**: icon + giá trị, bỏ nhãn | Figma GV-101 |
| F9 | GV-104 Cần chú ý (`04-can-chu-y`) | Băng giải thích luật 20%, chip lọc “cấm thi”, nút chính “Xuất báo cáo”, tên bị cắt; tiêu đề lại là “Chi Tiet Sinh Vien” | T1; E-05 (thầy muốn chăm sóc sinh viên, không cần báo cáo); H4 nhất quán tên màn | Cao | **Modify**: nút chính là “Nhắc” ở hồ sơ GV-201; chip mức dưới tên; nhóm theo mức; tiêu đề “Cần chú ý” | Figma GV-104, GV-201, IT-2 |

## Giữ lại từ Stitch (Accept)

| # | Ý tưởng Stitch | Vì sao giữ |
|---|---|---|
| A1 | Ảnh đại diện sinh viên trên mọi hàng | Thầy nhận mặt sinh viên (E-04), ảnh giúp xử lý ngoại lệ nhanh hơn đọc mã |
| A2 | Thẻ “Chốt ngay” ở đầu Tổng quan khi có slot chưa chốt | Đúng nỗi sợ quên điểm danh bị trừ lương (E-01, E-09); thành trạng thái GV-001 .D1 |
| A3 | Thẻ QR to kèm bộ đếm tự động | Không đếm tay (E-04), lớp tự quét |
| A4 | Danh sách chỉ hiện người chưa quét, nút ✓ ✕ trên từng hàng | Xử lý ngoại lệ thay vì duyệt cả 35 người (E-06) |
| A5 | Mã QR tự đổi theo chu kỳ | Chống chụp mã gửi bạn; thành dòng “Mã đổi sau mỗi 15 giây” ở SV-101 .X |

## Tổng kết

9 phát hiện gắn với 4 màn: 1 Reject trọn (F6), 1 Reject phần chữ (F4), 7 Modify; 5 ý tưởng giữ lại. Lỗi lặp lại nhiều nhất là **chữ giải thích** (F4, F7, F9) và **màu** (F3), nên IT-1 tập trung vào hai việc đó; IT-2 sửa trạng thái; IT-3 thêm trạng thái lỗi, rỗng và web sinh viên mà IT-0 chưa có.
