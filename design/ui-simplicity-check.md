# UI Simplicity Checklist · chấm v2

> **26/10/2026.** Claude chấm trên 42 ảnh xuất từ Figma trang 03 (`assets/figma/GV-*.png`, `SV-*.png`, bản 22/10 sau D-11, D-12). Đây là lần AI tự chấm, **chưa phải cổng duyệt**: thien hoặc một bạn trong nhóm chấm lại bằng file checklist gốc (`ui_simplicity_checklist.html`) rồi ghi điểm của người vào cột cuối (luật L6 trong [retro-v1](../process/retro-v1.md)).

## Kết quả: 18/20 tiêu chí · 90/100 (Claude) · người chấm: chưa

| # | Tiêu chí | Claude | Ghi chú | Người chấm |
|---|---|---|---|---|
| A1 | Tiêu đề, nhãn ngắn, dễ quét | Đạt | Tiêu đề ≤ 3 từ, nút bắt đầu bằng động từ (T2) | |
| A2 | Không có đoạn giải thích dài | Đạt | Không còn câu hướng dẫn; dài nhất là tin nhắc trong GV-201 sheet, đó là nội dung gửi đi | |
| A3 | Thông tin ít dùng nằm ở chi tiết | Đạt | Danh sách 32 em đã quét gộp thành một hàng; lịch sử vắng nằm ở Hồ sơ | |
| A4 | Không lặp nội dung giữa các thẻ | **Chưa** | U-01 | |
| B1 | Một màu nhấn, nền trung tính | Đạt | Petrol `#0B6283` duy nhất | |
| B2 | Không tô màu thẻ để trang trí | Đạt | Thẻ nền màu duy nhất là slot đang diễn ra (D-11), có nghĩa | |
| B3 | Màu trạng thái nhất quán | Đạt | Xanh lá = có mặt/đã chốt, hổ phách = chưa chốt/sắp chạm ngưỡng, đỏ = vắng/chạm ngưỡng | |
| B4 | Màu không là kênh duy nhất | Đạt, 1 ghi chú | Chip đều có icon + chữ. Thanh 3 đoạn ở GV-001 chỉ có màu, nhưng có chữ “1/3 đã chốt” bên cạnh (U-04) | |
| C1 | Mật độ hợp tác vụ, thiết bị | Đạt | | |
| C2 | Khoảng cách theo spacing scale | Đạt | Biến Spacing gắn trên component (figma-build.md) | |
| C3 | Nhóm hợp lý, không chia nhỏ thẻ | Đạt | | |
| C4 | Bảng, form, nút dễ thao tác | Đạt | Vùng chạm ≥ 48 (A-5 trong design-decisions) | |
| D1 | Nội dung quan trọng thấy ngay | Đạt | GV-001: slot đang diễn ra lên đầu; .D1 thẻ Chốt ngay lên đầu | |
| D2 | Một hành động chính nổi bật | Đạt, 1 ghi chú | Nút ghost “Mở lại” ở GV-102 .D2 dễ hiểu nhầm là mở lại phiên (U-05) | |
| D3 | Cấp chữ phân biệt rõ | Đạt | Số to hơn nhãn (T4) | |
| D4 | Các phần có thứ tự | Đạt | | |
| E1 | Component, font, icon nhất quán | Đạt | | |
| E2 | Tương phản ≥ 4,5:1 | Đạt | Theo A-1, A-2 trong [design-decisions](design-decisions.md) | |
| E3 | Điều khiển có chỉ báo trạng thái | Đạt | | |
| E4 | Loading, empty, success, error rõ | **Chưa** | U-02, U-03 | |

## Việc cần sửa

| Mã | Màn | Vấn đề | Đề xuất | Mức |
|---|---|---|---|---|
| U-01 | GV-103 .D | Ô số “2 cần chú ý” và nhóm “Cần chú ý” ngay dưới nói cùng một điều | Bỏ ô số thứ ba, còn 2 ô (sĩ số, buổi đã học); hoặc giữ ô và bỏ tiêu đề nhóm | Thấp |
| U-02 | SV-101 | Không có khung cho lỗi quyền camera, dù handoff đã ghi “Cần quyền camera” | Thêm SV-101 .X2: icon camera gạch, “Cần quyền camera”, nút **Cho phép** | Vừa |
| U-03 | GV-101 .D1 | Nút “Mở điểm danh” xám mà không nói khi nào mở được (H1) | Nhãn nút tắt thành “Mở lúc <giờ>”, giờ theo quy tắc mở sớm mà nhóm chốt (không thêm câu giải thích, T1 vẫn giữ) | Vừa |
| U-04 | GV-001 .D, .D1 | Thanh 3 đoạn phân biệt slot bằng màu; ở thang xám hổ phách và xanh lá gần giống nhau | Chấp nhận được vì có chữ “1/3 đã chốt”; nếu sửa thì đoạn chưa chốt dùng nét chéo | Thấp |
| U-05 | GV-102 .D2 | “Mở lại” nghĩa là hiện lại mã QR, nhưng đọc như mở lại phiên đã đóng | Đổi thành “Hiện mã” | Thấp |
| U-06 | GV-002 .D1 và .D3 | Hôm nay ở .D1 dùng chip “Sắp tới” trên mỗi thẻ; ở .D3 (Tuần) chỉ slot đã chốt có chip | Chọn một quy tắc: Tuần chỉ hiện chip khi khác “Sắp tới”, áp cho cả Hôm nay | Thấp |

Sửa U-02 và U-03 là đủ lên 20/20 trên bảng này. U-01 sửa thì A4 đạt.

## 3 bài kiểm bổ sung

| Bài | Kết quả |
|---|---|
| 5 giây | GV-001, GV-102, SV-001: nói được ngay việc chính (mở/chốt điểm danh; xem còn vắng được mấy buổi). GV-103 chậm hơn vì 3 ô số cùng cỡ |
| Thang xám | Đạt nhờ icon trên chip; điểm yếu duy nhất là U-04 |
| Cắt bớt | Còn cắt được: “Fall 2026 · 4 lớp” ở GV-003 (lặp với GV-100), ô số thứ ba ở GV-103 (U-01) |
