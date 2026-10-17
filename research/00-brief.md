# Mục tiêu sản phẩm và phạm vi

> Mục tiêu một câu đã được thien duyệt ngày 17/10/2026 (cổng GĐ 0).

## Mục tiêu một câu

> Giúp giảng viên FPTU **không bao giờ quên điểm danh** và **biết sớm sinh viên nào cần được quan tâm**, trên một app điện thoại thay cho việc mở FAP để xem lịch, lớp và điểm danh.

## Vấn đề muốn giải quyết

| Vấn đề | Nguồn | Nhãn |
|---|---|---|
| Giảng viên quên điểm danh thì bị trừ lương | GVHD-01, 16/10 | Reported |
| Giảng viên phải mở FAP trên điện thoại để xem lịch, lớp, điểm danh; không muốn chuyển giữa hai app | GVHD-01, 16/10 | Reported |
| Sinh viên vắng quá 20% số buổi thì bị cấm thi; nhiều sinh viên quên mình đã vắng bao nhiêu | GVHD-01; desk v1 (S3, S12, S21) | Reported + Desk |
| Báo cáo hiện tại chỉ là số liệu, không chỉ ra ai cần được giúp | GVHD-01, 16/10 | Reported |
| Điểm danh có thể sai hoặc thiếu | Tóm tắt nhóm | Reported (chưa kiểm từng câu) |

## Trong phạm vi

- **App giảng viên (mobile, chính):** tổng quan, lịch (hôm nay, ngày mai, tuần), lớp, điểm danh một slot, sinh viên cần chú ý, xử lý báo sai.
- **Web sinh viên (360 dp, phụ, tối đa 3 màn):** quét mã, xem số buổi còn được vắng, báo sai.

## Ngoài phạm vi

- Đếm sĩ số, kiểm tra ngẫu nhiên, bất kỳ bước kiểm đếm nào (GVHD-01 đánh giá là thừa).
- Tạo lớp, xếp lịch (phòng Đào tạo làm trên FAP).
- Đơn từ, điểm số, các chức năng khác của FAP.

## Giả định (Assumed, ghi rõ trên slide)

| # | Giả định | Vì sao cần |
|---|---|---|
| A1 | App đọc và ghi cùng dữ liệu với FAP (lịch, lớp, danh sách sinh viên, kết quả điểm danh) | Bài lab không code; tránh câu hỏi “dữ liệu ở đâu ra” |
| A2 | Sinh viên điểm danh bằng cách quét mã QR giảng viên hiện trên điện thoại hoặc máy chiếu | GVHD-01 nói sinh viên quét mã trên web |
| A3 | Ngưỡng vắng mặc định 20% số buổi của môn; mỗi môn có thể khác | Desk v1: quy chế để ngưỡng trong đề cương môn |
| A4 | Giảng viên sửa được điểm danh trong ngày có slot | Desk v1, một nguồn |
