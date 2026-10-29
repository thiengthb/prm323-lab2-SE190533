# Nhật ký AI

Mọi lần dùng AI đều ghi ở đây, prompt nguyên văn nằm trong [prompts/](prompts/). AI đề xuất; nhóm quyết định.

## Disclosure

| Công cụ | Dùng vào việc gì | Ai thao tác |
|---|---|---|
| Claude (Anthropic) qua Claude Code | Đóng vai BA: rà soát v1, kế hoạch, ma trận bằng chứng, nháp persona, IA, flow, DESIGN.md, prompt Stitch, phản biện | Claude soạn, thien duyệt và chốt |
| Google Stitch | Sinh UI đầu tiên (IT-0) và 3 vòng sửa | thien chạy prompt Claude soạn |
| Figma MCP (gọi từ Claude Code) | Dựng token, component, màn, prototype trong Figma | Claude thực thi, thien duyệt |

**Không dùng AI để giả lập người dùng.** Phỏng vấn ở v2 là người thật (SV-01, SV-02); phía giảng viên dựa vào phản hồi trực tiếp của GVHD (bài học R1 trong [retro-v1](../process/retro-v1.md)).

## Nhật ký

| Mã | Ngày | Công cụ | Việc | Kết quả và quyết định |
|---|---|---|---|---|
| AI-01 | 16/10 | Claude | Rà soát v1, đối chiếu góp ý thầy và nhóm, lập kế hoạch v2 | Kế hoạch [process/plan.md](../process/plan.md). thien bác đề xuất giữ tên repo cũ, chọn tạo repo mới (Modify) |
| AI-02 | 17–20/10 | Claude | Nháp persona, IA, flow từ ma trận bằng chứng | thien giữ P-02 riêng (Accept); thien định nghĩa lại “setup” thành nhập từ FAP (Modify, thêm GV-100) |
| AI-03 | 20/10 | Claude → Stitch | Prompt IT-0 từ DESIGN.md v1.0; thien chạy, Stitch sinh 4 màn | [prompts/AI-03-stitch-IT-0.md](prompts/AI-03-stitch-IT-0.md); ảnh và HTML ở [assets/stitch/IT-0/](../assets/stitch/IT-0/). Stitch tự đổi sang bảng màu Material 3 tím (`stitch-DESIGN.md`) |
| AI-04 | 20/10 | Claude | Phản biện IT-0 theo Nielsen, accessibility, persona | [critique/AI-04-critique-IT-0.md](critique/AI-04-critique-IT-0.md): 9 phát hiện (7 Modify, 2 Reject), giữ 5 ý tưởng. Claude đưa 3 bảng màu (Đen trắng, Indigo, Teal); thien chọn **Đen trắng** (D-01, Modify bảng màu Violet của chính Claude) |
| AI-05 | 20/10 | Claude → Stitch | IT-1 “Đen trắng + bỏ chữ giải thích” | [prompts/AI-05-stitch-IT-1.md](prompts/AI-05-stitch-IT-1.md). thien chạy; 4 màn ở [assets/stitch/IT-1/](../assets/stitch/IT-1/). Hết tím, hết chữ dưới 14, hết đoạn hướng dẫn; xem AI-09 |
| AI-06 | 20/10 | Claude → Stitch | IT-2 “Đúng trạng thái” | [prompts/AI-06-stitch-IT-2.md](prompts/AI-06-stitch-IT-2.md). thien chạy; 5 màn ở [assets/stitch/IT-2/](../assets/stitch/IT-2/) (GV-101 .D1/.D2/.D3, GV-104, GV-201 mới); xem AI-09 |
| AI-07 | 20/10, chạy 22/10 | Claude → Stitch | IT-3 “Trạng thái lỗi, rỗng + web sinh viên” | [prompts/AI-07-stitch-IT-3.md](prompts/AI-07-stitch-IT-3.md). Claude thao tác Stitch trên trình duyệt máy thien (thien tự đăng nhập); 8 màn ở [assets/stitch/IT-3/](../assets/stitch/IT-3/); xem AI-10 |
| AI-08 | 20/10 | Claude → Figma MCP | Dựng final UI (trang 03) và prototype (trang 06) theo đặc tả, đã sửa theo AI-04 | 14 màn, 41 khung trạng thái, 4 khung kiểm 412 dp; prototype 4 flow, 73 điểm chạm. Nhật ký ở [design/figma-build.md](../design/figma-build.md) |
| AI-09 | 20/10 | Claude | Phản biện IT-1, IT-2 | [critique/AI-09-critique-IT-1-2.md](critique/AI-09-critique-IT-1-2.md): 9/9 phát hiện IT-0 đã đóng; 6 phát hiện mới F10–F15 (chip và nút xuống dòng ở 360 dp, tên bị cắt, nút “Nhắc sinh viên” mất chữ do token sai). Lỗi bố cục lặp lại nên màn cuối dựng trên Figma |
| AI-10 | 22/10 | Claude | Phản biện IT-3; lấy ảnh chân dung Stitch làm ảnh đại diện | [critique/AI-10-critique-IT-3.md](critique/AI-10-critique-IT-3.md): đúng chữ 3 hộp thoại và skeleton; tái phạm F1, F5, F6, F8, F15; 7 phát hiện mới F16–F22 (2 Cao ở web sinh viên). Figma AI hết tín dụng nên thien chọn dùng ảnh Stitch (Accept): 7 ảnh gắn vào 93 avatar trang 03, 06 |
| AI-11 | 26/10 | Claude | Chấm 42 khung Figma theo UI Simplicity Checklist (20 tiêu chí) và 3 bài kiểm bổ sung | [design/ui-simplicity-check.md](../design/ui-simplicity-check.md): 18/20 (90/100); 6 việc sửa U-01..U-06. Chưa phải cổng duyệt: chờ thien hoặc nhóm chấm lại |
| AI-12 | 26–29/10 | Claude → Figma MCP | Thử 3 hướng giao diện (trang `00 Hướng`), dựng lại theo hướng C; 4 vòng duyệt từng màn với thien qua trang duyệt có nút OK / Cần sửa / Chưa chắc (nhóm A–E) | thien chọn hướng C (D-13). Luật chung chốt qua các vòng (D-14). U-01, U-03, U-05, U-06 của AI-11 đã sửa trên Figma; U-02 thành khung SV-101 .X2 |
| AI-13 | 29/10 | Claude → Figma MCP | Tài khoản Claude mới tiếp tục: rà repo và Figma, sửa nhóm D theo điểm thien chấm (GV-100 .S icon trên chữ dưới), nhóm E theo 4 lựa chọn của thien; soát MSSV mẫu trùng; cập nhật DESIGN.md v3.0 từ biến Figma, tính lại tương phản | D-15. Tương phản mọi cặp chữ ≥ 4,5:1 (thấp nhất chữ trắng trên cam 4,79:1); viền điều khiển 3,23:1 |
| AI-14 | 29/10 | Claude → Figma MCP | Trang duyệt nhóm E (ảnh lấy thẳng từ Figma); sửa theo điểm thien chấm; thien chỉ ra thiếu vòng đời dùng app, Claude hỏi 3 câu rồi dựng đăng nhập, đăng ký, xác nhận email, Tổng quan chưa có lớp, kỳ mới, kỳ cũ, đăng nhập web SV và nối prototype FL-0, FL-0b | D-16..D-19. thien chọn đăng ký email + mật khẩu (Modify gợi ý “tài khoản FPT, lần đầu là đăng ký” của Claude); web SV đăng nhập FPT, giữ kỳ cũ (Accept) |
