# AI-05 · Prompt Stitch IT-1 “Đen trắng + bỏ chữ giải thích” (nguyên văn)

- **Công cụ:** Google Stitch, **cùng project IT-0**, chọn cả 4 màn rồi dán khối dưới vào ô chỉnh sửa.
- **Sửa gì:** F1, F3, F4, F5, F6, F8 trong [phản biện IT-0](../critique/AI-04-critique-IT-0.md); bảng màu theo [D-01](../../design/design-decisions.md).
- **Đầu ra cần lưu:** ảnh 4 màn vào `assets/stitch/IT-1/` (giữ tên file như IT-0).

```text
Edit all 4 screens. Keep the layout and content structure, change only what is listed.

1. COLOR: switch to the shadcn/ui default neutral theme. Remove ALL violet and purple. Primary buttons, selected tab, focus ring and links = near-black #18181B with text #FAFAFA; pressed #3F3F46. Selected tab indicator background #F4F4F5. Background #FAFAFA, cards #FFFFFF with 1px border #E4E4E7, secondary text #52525B. Status colors stay ONLY on status chips: green #15803D on #F0FDF4, amber #B45309 on #FFFBEB, red #B91C1C on #FEF2F2. No filled colored cards: the "1 slot chưa chốt" card becomes a white card with a 2px amber #B45309 border and an amber chip.
2. TEXT: Vietnamese with full diacritics everywhere ("Tổng quan", "Chi tiết slot", "Điểm danh", "Cần chú ý"). Delete every explanatory sentence or helper paragraph, including the QR instructions, "Giảng viên đối chiếu & chạm nhanh" and any "Lưu ý" box. Nothing smaller than 14sp, including captions and the QR timer.
3. "Tổng quan": remove the logo and the avatar from the app bar; keep only the title and a bell icon. Put each status chip on its own line so chips never overlap.
4. "Điểm danh": remove the percentage and the progress bar; the counter "32/35 đã quét" in 32sp is the only progress. Remove seat labels like "Bàn 03". Timer text "Đổi mã sau 15s" at 14sp.
5. "Chi tiết slot": replace "Label: value" rows with an icon + value row (clock 07:00–09:15, book PRM393, users SE1801, map-pin P.305).
```
