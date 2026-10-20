# AI-03 · Prompt Stitch IT-0 (nguyên văn)

- **Công cụ:** Google Stitch, chế độ App (mobile).
- **Ai chạy:** thien dán nguyên văn khối dưới vào Stitch, không sửa. Claude soạn từ [DESIGN.md](../../design/DESIGN.md) v1.0.
- **Đầu ra cần lưu:** ảnh từng màn vào `assets/stitch/IT-0/` (tên file theo mã màn, ví dụ `GV-001.png`).

```text
Design a mobile app (Android, 360 x 800 dp, light theme) for lecturers at FPT University Vietnam. All UI text must be in Vietnamese.

USER
A lecturer who teaches 3 to 4 class slots a day, about 35 students per class, 10-week term. They use the phone between slots, often one-handed, with little time. Their two fears: forgetting to take attendance (they lose salary if they forget) and noticing too late that a student is absent too often (students absent more than 20% of slots are banned from the final exam). They know every student by face, so the app must NEVER ask them to count students or enter a headcount.

TASK (main flow, generate these 4 screens)
1. "Tổng quan" (Overview, bottom-nav tab 1): today's date; a highlighted card for the slot that is live now (time 07:00–09:15, course PRM393, class SE1801, room P.305, status chip "Đang diễn ra", primary button "Mở điểm danh"); a warning card "1 slot chưa chốt" for an earlier slot with button "Chốt ngay"; a section "Cần chú ý" listing 3 students with absence counts like "3/4 buổi vắng" and a warning chip; the rest of today's slots as compact rows.
2. "Chi tiết slot": app bar with back arrow; course, class, room, time; status chip; one primary button "Mở điểm danh" fixed at the bottom.
3. "Điểm danh" session: a large QR code card for students to scan with a live counter "32/35 đã quét"; below it a list "Chưa quét" showing only the 3 students who have not scanned yet, each row with avatar photo, full name, student ID and two compact actions "Có mặt" / "Vắng"; one primary button "Chốt điểm danh" fixed at the bottom.
4. "Cần chú ý": list of students close to the absence limit across all classes, each row with avatar, name, class code, a big number "3/4" (absences used / allowed) and a status chip ("Sắp chạm ngưỡng" amber, "Đã chạm ngưỡng" red); tap a row to open the student.

PLATFORM AND NAVIGATION
Bottom navigation with 4 tabs: Tổng quan, Lịch, Lớp, Tài khoản (Lucide-style line icons, 2px stroke, 24px, label below). Nested screens use a top app bar with a back arrow. All touch targets at least 48 x 48 dp. Primary action in the bottom half of the screen.

STYLE (from our DESIGN.md)
shadcn/ui look adapted to mobile: neutral zinc background #FAFAFA, white cards #FFFFFF with 1px border #E4E4E7, radius 16 for cards and 12 for buttons, almost no shadows. ONE accent color only: violet #7C3AED for primary buttons, selected tab and focus. Status colors only for status: present green #15803D on #F0FDF4, pending/warning amber #B45309 on #FFFBEB, absent/error red #B91C1C on #FEF2F2. Every status = icon + color + 1-2 words, never color alone. Text: Inter font, primary text #18181B, secondary #52525B, nothing smaller than 14sp; big numbers 32sp semibold. Spacing on a 4dp grid, 20dp side margins.

CONSTRAINTS
- No explanatory sentences or helper paragraphs on screen. Titles max 3 words, button labels max 3 words starting with a verb.
- At most about 25 words per screen besides data (names, times, rooms, numbers).
- One primary button per screen. No gradients, no decorative illustrations, no cards inside cards.
- No headcount, no "count students" step, no random check step.
```
