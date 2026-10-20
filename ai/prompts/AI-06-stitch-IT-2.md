# AI-06 · Prompt Stitch IT-2 “Đúng trạng thái” (nguyên văn)

- **Công cụ:** Google Stitch, cùng project, chạy **sau** IT-1.
- **Sửa gì:** F7, F9 trong [phản biện IT-0](../critique/AI-04-critique-IT-0.md), và tách trạng thái nghiệp vụ theo mã màn ([user-flow.md](../../ux/user-flow.md) mục 1).
- **Đầu ra cần lưu:** ảnh vào `assets/stitch/IT-2/`, tên file theo mã màn và trạng thái, ví dụ `GV-101.D1.png`.

```text
Keep the IT-1 style exactly (neutral black-and-white, status colors only on chips, no helper text, 14sp minimum). Now make each screen show the right content for its state.

1. "Chi tiết slot": make 3 versions.
   a) Upcoming (09:30–11:45, chip "Sắp tới" neutral): NO attendance numbers; bottom button "Mở điểm danh" disabled.
   b) Live now (07:00–09:15, chip "Đang diễn ra"): NO attendance numbers; bottom button "Mở điểm danh" enabled.
   c) Closed (chip "Đã chốt" green): show "34 có mặt · 1 vắng" as the only numbers; bottom button outline "Sửa điểm danh".
2. "Cần chú ý": title "Cần chú ý". Remove the rule banner, the filter chips and the "Xuất báo cáo" button. Group rows under two small headers "Đã chạm ngưỡng" and "Sắp chạm ngưỡng". Each row: avatar 40, full name on one line (never truncated at 360dp, wrap to 2 lines if needed), class code below the name, a big number "4/4" or "3/4" on the right and the status chip under the name. Tapping a row opens the student.
3. New screen "Hồ sơ sinh viên": back arrow; avatar 56, name "Trần Minh Long", "SE190155 · PRM393 · SE1801"; a big amber number "3/4" + "buổi vắng" with amber chip "Sắp chạm ngưỡng"; a list of absent sessions (date, slot, time); ONE primary button fixed at the bottom "Nhắc sinh viên".
```
