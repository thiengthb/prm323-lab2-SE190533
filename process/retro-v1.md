# Retro v1: vì sao bản trình bày 16/10/2026 lệch ý giảng viên

Bản v1 nằm ở repo [prm323-lab2-SE190533-archieve](https://github.com/thiengthb/prm323-lab2-SE190533-archieve). File này giữ lại bài học, không giữ lại sản phẩm.

## Giảng viên nhận xét gì (Reported, GVHD-01, 16/10/2026)

Nguồn: ghi nhớ của thien ngay sau buổi trình bày, đối chiếu với tóm tắt của nhóm (bản tóm tắt nhóm dựng từ ghi âm đã biên tập, chưa kiểm chứng từng câu).

| # | Nhận xét |
|---|---|
| 1 | App mobile tập trung vào giảng viên. Quét mã và báo sai của sinh viên làm trên web; web thêm cảnh báo sắp hết số buổi được vắng, vì nhiều sinh viên quên và bị cấm thi |
| 2 | Bước đếm sinh viên là thừa: giảng viên điểm danh lâu năm, khoảng 35 gương mặt qua 10 tuần thì nhớ được |
| 3 | App cần lịch hôm nay, ngày mai, tuần, lớp học, tổng quan: gộp các việc giảng viên đang mở FAP để làm |
| 4 | Giao diện chưa đẹp; quá nhiều chữ trên màn hình |
| 5 | Giảng viên không điểm danh thì bị trừ lương |
| 6 | Báo cáo phải giúp nhận ra sinh viên vắng nhiều, cần chăm sóc, không chỉ hiện số liệu |
| 7 | Slide sai trình tự: mục tiêu → câu hỏi phỏng vấn → dữ liệu → persona → giải pháp cho từng persona → màn hình → flow → component và màu → wireframe → trạng thái → final UI → prototype. Mã màn hình (SC) không phân biệt được các trạng thái |
| 8 | (theo nhóm) Không giữ tính năng chỉ vì AI gợi ý; không mặc định AI hiểu FAP phía sau đăng nhập; tự kiểm chứ không chỉ dựa vào AI review |

## Năm nguyên nhân gốc

| # | Nguyên nhân | Biểu hiện ở v1 |
|---|---|---|
| R1 | Phỏng vấn là mô phỏng bằng AI (11 người R01–R11) | Persona phản ánh điều AI đoán, không phải điều giảng viên cần |
| R2 | Đóng khung “bổ trợ FAP” thay vì “thay một phần FAP” | Thiếu lịch, lớp, tổng quan |
| R3 | Giải pháp có trước nghiên cứu (app thật đã có QR, mở từ xa) | Đối chiếu sĩ số, kiểm tra ngẫu nhiên: bước thừa |
| R4 | Viết để chứng minh: khoảng 52.000 chữ tài liệu, màn hình có câu giải thích | Khó đọc, UI rối |
| R5 | Slide theo thứ tự bảng chấm, không theo thứ tự tư duy | Style guide nằm sau final UI |

## Luật cho v2

1. Không có người thật nói thì chỉ là giả thuyết, gắn nhãn Assumed. Không phỏng vấn mô phỏng bằng AI.
2. Mỗi tính năng truy về một persona, một nỗi đau, một nguồn. Không truy được thì cắt.
3. Màn hình không tự giải thích; giải thích để ở chú thích Figma và tài liệu.
4. Style guide trước, AI sau.
5. Kể theo thứ tự tư duy.
6. Mỗi giai đoạn có một người thật duyệt, không chỉ AI review.

## Giữ lại từ v1

- Nghiên cứu bàn giấy về quy định FPTU (ngưỡng vắng 20%, hạn sửa điểm danh): `research/02-desk/` ở repo v1.
- Quan sát của thien (O-01) và ảnh giao diện FAP (O-02).
- Khung tài liệu theo đề và kinh nghiệm dựng Figma bằng token, component, prototype.
