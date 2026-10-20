# Ma trận bằng chứng

Mỗi dòng là một phát hiện có mã nguồn. Persona và tính năng chỉ được trích từ bảng này (luật 2 trong [retro-v1](../process/retro-v1.md)).

**Nhãn:** Observed (quan sát có bối cảnh), Reported (người tham gia tự nói), Desk (văn bản), Inferred (nhóm suy luận, có ghi lý do), Assumed (chưa có nguồn).

**Nguồn:**
- **GVHD-01:** giảng viên hướng dẫn, phản hồi trực tiếp trong buổi review 16/10/2026. Ghi lại từ trí nhớ của thien ngay sau buổi, đối chiếu tóm tắt nhóm. Không gặp lại được trước hạn.
- **NHOM-16/10:** tóm tắt của nhóm từ ghi âm đã biên tập; chỉ dùng khi khớp hoặc bổ sung GVHD-01, có đánh dấu.
- **DESK-v1:** nghiên cứu bàn giấy ở repo v1 (`research/02-desk/`).
- **SV-01, SV-02:** phỏng vấn sinh viên thật, ghi ở [03-ghi-chep/](03-ghi-chep/). Mới có 2 người, ít hơn mục tiêu 3–5.

## Phía giảng viên

| Mã | Phát hiện | Nguồn | Nhãn |
|---|---|---|---|
| E-01 | Giảng viên không điểm danh thì bị trừ lương | GVHD-01 | Reported |
| E-02 | Giảng viên không muốn chuyển qua lại giữa hai app trên điện thoại; muốn lịch, lớp, tổng quan ngay trong app điểm danh | GVHD-01 (thien diễn giải lý do “lười chuyển app”) | Reported + Inferred |
| E-03 | Cần xem lịch hôm nay, ngày mai, tuần; quản lý lớp; trang tổng quan | GVHD-01; NHOM-16/10 | Reported |
| E-04 | Đếm sinh viên là thừa: giảng viên lâu năm nhớ khoảng 35–36 gương mặt qua 10 tuần | GVHD-01; NHOM-16/10 | Reported |
| E-05 | Báo cáo phải giúp nhận ra sinh viên vắng nhiều, cần chú ý, hỗ trợ theo dõi và chăm sóc, không chỉ hiện số | GVHD-01; NHOM-16/10 | Reported |
| E-06 | Điểm danh có thể sai hoặc thiếu; cần kiểm khả năng thao tác nhầm | NHOM-16/10 | Reported (một nguồn) |
| E-07 | Cần xem lại hành trình trước, trong, sau buổi học | NHOM-16/10 (nhóm ghi “ghi âm chưa rõ”) | Reported (một nguồn, chưa chắc) |
| E-08 | Không mặc định AI hiểu FAP phía sau đăng nhập | NHOM-16/10 | Reported |
| E-09 | Giảng viên **có quên điểm danh thật**: hai lớp khác nhau, hai lần | SV-01, SV-02 | Reported (2 nguồn độc lập) |
| E-10 | Khi giảng viên quên, giảng viên **tự phát hiện muộn 1–2 ngày**; lớp biết nhưng không ai nhắc | SV-02 | Reported |
| E-11 | Cách sửa hiện nay đi qua nhóm chat của lớp: sinh viên nhắn, giảng viên điểm danh lại | SV-01, SV-02 | Reported |
| E-12 | Lớp học và lịch dạy nhập từ dữ liệu FAP, giảng viên không tự tạo | thien (quyết định 20/10) | Assumed |

## Phía sinh viên

| Mã | Phát hiện | Nguồn | Nhãn |
|---|---|---|---|
| E-20 | Sinh viên quét mã và báo sai trên web (điện thoại, laptop tùy chọn) | GVHD-01 | Reported |
| E-21 | Nhiều sinh viên nghỉ mà không có hệ thống báo nên quên, rồi rớt vì vắng quá số buổi | GVHD-01; NHOM-16/10 | Reported |
| E-22 | Vắng quá 20% số buổi của môn thì không được thi cuối môn | DESK-v1 (S3 chính thức, S12) | Desk |
| E-23 | Có sinh viên tự viết extension cảnh báo vàng ở 15%, đỏ ở 20% | DESK-v1 (S21) | Desk (một nguồn) |
| E-24 | Không tìm thấy cơ chế nghỉ có phép không tính vào 20% | DESK-v1 (S11) | Desk (một nguồn) |
| E-25 | Sinh viên **hiếm khi xem** số buổi vắng (“lâu rồi không xem”, “5 tuần trước”, xem vì tò mò) | SV-01, SV-02 | Reported |
| E-26 | Sinh viên **không nhớ chắc** mình được vắng mấy buổi; người nhớ thì nhớ đúng 20% | SV-01 (ước lượng “2 đến 4”), SV-02 (“8 slot, 20%”) | Reported |
| E-27 | Cả hai người chưa từng suýt cấm thi, cũng không quen ai bị | SV-01, SV-02 | Reported. **Mâu thuẫn một phần với E-21**, xem ghi chú |

## Ghi chú phân tích

- **E-09, E-10 củng cố E-01 mạnh nhất bộ dữ liệu.** Thầy nói quên là bị trừ lương; hai sinh viên kể giảng viên quên thật và chỉ biết sau 1–2 ngày. Nhắc nhở và thẻ “slot chưa chốt” là tính năng có nhiều bằng chứng nhất.
- **E-27 làm yếu E-21.** Thầy nói nhiều sinh viên rớt vì vắng, nhưng 2/2 người hỏi chưa gặp. Mẫu quá nhỏ để bác bỏ, và người được hỏi đều là sinh viên đi học đều. Kết luận: giữ cảnh báo hết slot (vì người chấm đã yêu cầu và E-22 là quy định thật), nhưng **không** nói trên slide là “nhiều sinh viên bị cấm thi”; nói là “sinh viên không theo dõi được, nên một khi chạm ngưỡng thì đã muộn” (E-25, E-26).
- **E-25 quyết định hình thức cảnh báo:** sinh viên không tự mở xem, nên cảnh báo phải **chủ động** (hiện ngay đầu trang khi quét mã, và qua giảng viên nhắc ở FL-3), không chờ sinh viên vào xem.

## Giả định đang mở

Xem bảng A1–A4 ở [00-brief.md](00-brief.md). Phỏng vấn sinh viên sẽ kiểm A3 (ngưỡng) và E-21.
