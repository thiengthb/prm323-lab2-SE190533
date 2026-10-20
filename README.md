# PRM323 Lab 2 · SE190533 (v2)

Thiết kế UI/UX có AI hỗ trợ (Google Stitch → Figma): **app điện thoại cho giảng viên FPTU** để xem lịch, quản lý lớp, điểm danh và theo dõi sinh viên cần chú ý, kèm **web tối giản cho sinh viên** (quét mã, xem số buổi vắng còn lại, báo sai).

| Mục | Nội dung |
|---|---|
| Nhóm | Group 3: Trần Ngọc Thiên · SE190533; Vũ Anh Khôi · SE194606; Vũ Huy Phương · SE190742; Lê Thành Lộc · SE182702 |
| Persona một dòng | **P-01:** giảng viên dạy 3–4 slot mỗi ngày, quen mặt sinh viên, sợ quên điểm danh (bị trừ lương) và sợ phát hiện muộn em vắng nhiều ([ux/persona.md](ux/persona.md)) |
| Figma | [PRM323 Lab 2 v2 · SE190533](https://www.figma.com/design/1qIZVpL0Q7bD9UzT5TVBRy) (6 trang đúng thứ tự đề) |
| Hạn | Đã gia hạn với giảng viên (sau 20/10/2026) |
| Bản trước (v1) | [prm323-lab2-SE190533-archieve](https://github.com/thiengthb/prm323-lab2-SE190533-archieve), trình bày 16/10/2026. Bài học: [process/retro-v1.md](process/retro-v1.md) |

## Bản đồ sản phẩm nộp

| Sản phẩm | Đường dẫn | Trạng thái |
|---|---|---|
| Mục tiêu sản phẩm, phạm vi, giả định | [research/00-brief.md](research/00-brief.md) | Mục tiêu đã duyệt 17/10 |
| Phiếu phỏng vấn sinh viên | [research/01-phieu-phong-van-sv.md](research/01-phieu-phong-van-sv.md) | Sẵn sàng dùng |
| Ma trận bằng chứng, ghi chép phỏng vấn | [research/02-evidence-matrix.md](research/02-evidence-matrix.md), [research/03-ghi-chep/](research/03-ghi-chep/) | 20 phát hiện, 2 phỏng vấn SV |
| Persona, problem statement, tiêu chí thành công | [ux/persona.md](ux/persona.md) | v0.2 (P-01, P-02, P-03) |
| Kiến trúc thông tin, user flow | [ux/user-flow.md](ux/user-flow.md) | v0.2 |
| Design brief cho Stitch | [design/DESIGN.md](design/DESIGN.md) | v1.1 Đen trắng (v1.0 viết trước Stitch) |
| Đặc tả màn hình | [design/screen-spec.md](design/screen-spec.md) | v1.1 (14 màn, 3 lớp phủ) |
| Quyết định thiết kế, checklist accessibility | [design/design-decisions.md](design/design-decisions.md) | D-01..D-10, checklist 10 mục đạt |
| Nhật ký AI | [ai/ai-design-log.md](ai/ai-design-log.md), [ai/critique/](ai/critique/) | AI-01..AI-08; phản biện IT-0: 9 phát hiện |
| Ảnh Stitch, ảnh Figma | `assets/stitch/`, `assets/figma/` | Stitch IT-0, IT-1, IT-2 có (IT-3 chờ chạy); 50 ảnh Figma có |
| Flutter handoff | [handoff/flutter-handoff.md](handoff/flutter-handoff.md) | v1.0 (2 bảng ánh xạ, 6 mục cho 14 màn) |
| Slide thuyết trình | PPTX theo thứ tự giảng viên yêu cầu, lời nói trong ghi chú người nói | v2.1 (20/10): 13 slide, thêm slide vòng sửa Stitch IT-1, IT-2 |
| Kế hoạch và quy trình | [process/plan.md](process/plan.md) | v0.2 |

## Công cụ AI đã dùng

| Công cụ | Dùng vào việc gì |
|---|---|
| Claude (Anthropic), qua Claude Code | Đóng vai BA: rà soát v1, lập kế hoạch, soạn prompt Stitch, phản biện, dựng Figma qua Figma MCP. Mọi quyết định do nhóm chốt |
| Google Stitch | Sinh UI đầu tiên (IT-0) và 3 vòng sửa (IT-1..IT-3), thien chạy |
