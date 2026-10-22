# AI-10 · Phản biện Stitch IT-3

- **Đầu vào:** prompt [AI-07](../prompts/AI-07-stitch-IT-3.md), chạy ngày 22/10 trong cùng project Stitch (Claude thao tác trình duyệt trên máy thien, thien đăng nhập). Stitch sinh 8 màn mới; zip cả project có 21 màn. Ảnh và HTML 8 màn mới lưu ở [assets/stitch/IT-3/](../../assets/stitch/IT-3/), tên theo mã màn. `stitch-DESIGN.md` giống hệt bản IT-2 nên không lưu lại.
- **Ai làm:** Claude so từng màn với prompt, với F1–F15 của [AI-04](AI-04-critique-IT-0.md) và [AI-09](AI-09-critique-IT-1-2.md), theo Nielsen (H1–H10), WCAG 2.x và luật [DESIGN.md](../../design/DESIGN.md); nhóm quyết định.
- **Bằng chứng:** chữ và cỡ chữ đọc từ HTML; bố cục, màu và độ mờ đọc từ ảnh `screen.png`.

## 1. Prompt có được làm đúng không

| # trong prompt | Màn | Đúng | Sai hoặc thiếu |
|---|---|---|---|
| 1 | [GV-OV1](../../assets/stitch/IT-3/GV-OV1.png) | Đúng chữ “Chốt điểm danh?”, “34 có mặt · 1 vắng”, “Huỷ” / “Chốt” | Nền sau hộp thoại bị làm mờ (`blur-xl`), không đọc được danh sách |
| 2 | [GV-102.X-GV-OV2](../../assets/stitch/IT-3/GV-102.X-GV-OV2.png) | Đúng chữ “Chưa gửi được”, “Mất mạng · đã lưu trên máy”, “Để sau” / “Thử lại”; thêm icon wifi gạch | Prompt yêu cầu danh sách “vẫn thấy” phía sau, Stitch làm mờ hẳn |
| 3 | [GV-102.S](../../assets/stitch/IT-3/GV-102.S.png) | Snackbar “Đã chốt” + “Hoàn tác” | Thêm “97.1%” và thanh tiến độ lặp lại số “34 có mặt · 1 vắng” |
| 4 | [GV-001.L](../../assets/stitch/IT-3/GV-001.L.png) | Skeleton theo hình thẻ slot và hàng cần chú ý, không spinner | Nhãn thanh đáy 11 px |
| 5 | [GV-001.E](../../assets/stitch/IT-3/GV-001.E.png) | Icon trong vòng xám, “Hôm nay không có slot”, nút “Xem lịch” | Bỏ mất khối “Cần chú ý”; nút không phải kiểu outline; nhãn thanh đáy 11 px |
| 6 | [SV-001.D](../../assets/stitch/IT-3/SV-001.D.png) | Banner “PRM393 còn 1 buổi được vắng”, 2 nút cố định dưới | Banner xám chứ không vàng; số “3/4” màu đen; thêm câu giải thích, thanh tiến độ, “Giảng viên: Trần NV” |
| 7 | [SV-101](../../assets/stitch/IT-3/SV-101.png) | Khung camera vuông | Ba trạng thái thành ba tab “Ống kính / Thành công / Báo lỗi” trên màn; ảnh chỉ vẽ tab camera, phần “Đã ghi nhận” và “Mã đã hết hạn” nằm ẩn trong HTML |
| 8 | [SV-102](../../assets/stitch/IT-3/SV-102.png) | Chip đỏ buổi “Vắng”, ô “Lý do”, nút “Gửi” | Hai thanh tiêu đề trùng tên; chip “Vắng” lồng trong chip đỏ; thiếu bản “Đã gửi” |

## 2. Phát hiện cũ tái phạm

| # | Phát hiện cũ | Ở IT-3 | Bằng chứng |
|---|---|---|---|
| F1 | Avatar trên app bar | **Tái phạm** ở mọi màn giảng viên | Icon người tròn đen góc phải `GV-OV1`, `GV-102.S`, `GV-001.*` |
| F5 | Chữ dưới 14 px | **Tái phạm** | `text-[11px]` nhãn thanh đáy (`GV-001.L`, `.E`), `text-[12px]` dòng “Sinh Viên Điểm Danh” (3 màn SV) |
| F6 | Thanh % lặp số | **Tái phạm** | “97.1%” ở `GV-102.S`; thanh dưới mỗi số “3/4” ở `SV-001.D` |
| F8 | Hàng “Nhãn: giá trị” | **Tái phạm** | “Giảng viên: Trần NV” ở `SV-001.D` |
| F15 | Dữ liệu mẫu sai | **Tái phạm** | “Học kỳ Fall 2024”; “Chủ Nhật, 29/10” và “Thứ Ba, 24/10” sai thứ (năm 2026 là thứ Năm và thứ Bảy); ảnh nam gắn tên “Trần Thị Minh Châu” |

Stitch giữ được điều đã sửa khi prompt nhắc lại luật, nhưng mỗi màn mới lại sinh lại các lỗi cũ: luật chỉ có hiệu lực trên màn mà prompt nêu tên.

## 3. Phát hiện mới

| # | Màn | Vấn đề quan sát được | Căn cứ | Mức | Quyết định | Sửa ở đâu |
|---|---|---|---|---|---|---|
| F16 | SV-101 | Trạng thái màn biến thành tab người dùng bấm được; kết quả quét không hiện trong ảnh | H1 trạng thái hệ thống; spec tách .D / .S / .X | Cao | **Reject** | Figma SV-101 .D, .S, .X là 3 khung riêng |
| F17 | SV-001.D, SV-101 | Chữ giải thích quay lại: “Chú ý điểm danh để không bị cấm thi”, “Giữ camera cách màn hình chiếu 15 - 30cm”, đoạn “Mọi hành vi gian lận sẽ bị hủy kết quả môn học” | Góp ý trực tiếp của thầy (quá nhiều chữ); H8; giọng đe doạ trái persona P-03 | Cao | **Reject** | Figma: SV-001 chỉ có banner và số; SV-101 .D chỉ “Đưa mã vào khung” |
| F18 | GV-OV1, GV-OV2 | Nền sau hộp thoại mờ hẳn, giảng viên không thấy em nào đang chưa quét khi quyết định chốt hay thử lại | H6 nhận ra thay vì nhớ; prompt mục 2 | Vừa | **Modify** | Figma: lớp phủ 50% không blur, danh sách vẫn đọc được |
| F19 | GV-001.E | Ngày không có slot bỏ luôn khối “Cần chú ý”, đúng lúc giảng viên rảnh để xử lý | E-05, E-22; mục tiêu GV-001 “bây giờ tôi phải làm gì” | Vừa | **Modify** | Figma GV-001 .E giữ “Cần chú ý” dưới trạng thái rỗng |
| F20 | SV-001.D | Màu trạng thái mất nghĩa: banner xám, “3/4” đen, chip “Sắp chạm ngưỡng” xám; chỉ 4/4 có màu đỏ | T4, D-05 (màu = trạng thái); H1 | Vừa | **Modify** | Figma SV-001 .D1 số và chip vàng ở 3/4, .D2 đỏ ở 4/4 |
| F21 | Tiêu đề nhiều màn | Viết hoa mỗi chữ: “Điểm Danh”, “Tổng Quan”, “Sinh Viên Điểm Danh” | Tiếng Việt viết hoa chữ đầu câu; H4 nhất quán | Thấp | **Modify** | Figma dùng “Điểm danh”, “Tổng quan” |
| F22 | SV-102 | Hai thanh tiêu đề cùng ghi “Lê Gia Huy · SE190533”, nút quay lại trên web | H8; web một cột không cần điều hướng app | Thấp | **Modify** | Figma SV-102: Browser bar + tiêu đề “Báo sai” |

## 4. Giữ lại

- **A6 · icon wifi gạch trong hộp thoại lỗi mạng (GV-OV2):** giúp nhận ra lỗi trước khi đọc chữ (H9). Nhóm ghi nhận, chưa thêm vào Figma vì Dialog dùng chung cho GV-OV1; sẽ là variant `Error` nếu làm vòng sau.
- **Ảnh chân dung:** Stitch sinh ảnh chân dung AI (không phải người thật) cho hàng sinh viên. Nhóm cắt 7 ảnh từ ảnh render (`GV-102.S`, màn cần chú ý, màn hồ sơ) làm ảnh đại diện trong Figma, đúng D-06; lưu ở [assets/stitch/IT-3/avatars/](../../assets/stitch/IT-3/avatars/). Bùi Lan Anh và giảng viên giữ chữ viết tắt, cũng là cách app hiển thị khi FAP thiếu ảnh. Không dùng Figma AI vì team Figma đang mượn hết tín dụng tới 01/11.

## 5. Tổng kết

IT-3 làm đúng chữ của cả 3 hộp thoại và trạng thái skeleton, nhưng tái phạm 5 lỗi cũ (F1, F5, F6, F8, F15) và sinh 7 lỗi mới, 2 lỗi Cao đều ở web sinh viên. Bốn vòng Stitch cho thấy công cụ hợp để tìm ý tưởng (A1–A6) hơn là ra màn cuối: mỗi màn mới lại phải soát lại cùng bộ luật. Màn cuối vẫn dựng trên Figma; mọi phát hiện trên đã đúng sẵn ở trang 03.
