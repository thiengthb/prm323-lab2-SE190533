# AI-07 · Prompt Stitch IT-3 “Trạng thái lỗi, rỗng + web sinh viên” (nguyên văn)

- **Công cụ:** Google Stitch, cùng project, chạy **sau** IT-2. Phần web sinh viên vẫn dùng khổ 360 (web mở trên điện thoại).
- **Thêm gì:** trạng thái loading, rỗng, lỗi (heuristic 9) và 3 màn web sinh viên mà IT-0 chưa có (FL-4 trong [user-flow.md](../../ux/user-flow.md)).
- **Đầu ra cần lưu:** ảnh vào `assets/stitch/IT-3/`, tên theo mã màn, ví dụ `GV-102.X.png`, `SV-101.S.png`.

```text
Keep the same black-and-white shadcn style and rules (no helper sentences, 14sp minimum, one primary button, status = icon + color + 1-2 words).

LECTURER APP
1. "Điểm danh" after tapping "Chốt điểm danh": a confirmation dialog "Chốt điểm danh?" with "34 có mặt · 1 vắng", buttons "Huỷ" (ghost) and "Chốt" (primary).
2. Same screen, network failure: an error dialog, title "Chưa gửi được", one line "Mất mạng · đã lưu trên máy", buttons "Để sau" (ghost) and "Thử lại" (primary). The attendance list stays visible behind the dialog.
3. Same screen, success: list shows the final result, snackbar at the bottom "Đã chốt" with action "Hoàn tác".
4. "Tổng quan" loading: skeleton cards in the shape of the slot cards, no spinner.
5. "Tổng quan" empty day: icon in a grey circle, one line "Hôm nay không có slot", outline button "Xem lịch".

STUDENT WEB (mobile browser, single column, no bottom navigation, header with student name "Lê Gia Huy · SE190533")
6. "Buổi vắng của tôi": an amber banner "PRM393 còn 1 buổi được vắng"; rows per course: course code, big number "3/4", number colored amber at 3/4 and red at 4/4; two buttons fixed at the bottom: outline "Báo sai" and primary "Quét mã".
7. "Quét mã": full-width camera frame with a square scan guide; after success show a green check, "Đã ghi nhận", "PRM393 · Slot 1 · 07:01", chip "Có mặt" and "Còn được vắng 2 buổi"; error version: red icon, "Mã đã hết hạn", "Mã đổi sau mỗi 15 giây", button "Quét lại".
8. "Báo sai": the session currently marked "Vắng" (PRM393 · 20/10 · 07:00) as a red chip, one text field "Lý do" and primary button "Gửi"; success version with green check and "Đã gửi".
```
