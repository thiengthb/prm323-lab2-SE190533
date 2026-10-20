# AI-09 · Phản biện Stitch IT-1 và IT-2

- **Đầu vào:** thien chạy prompt [AI-05](../prompts/AI-05-stitch-IT-1.md) (IT-1) và [AI-06](../prompts/AI-06-stitch-IT-2.md) (IT-2) trong cùng project Stitch, xuất zip ngày 20/10. Ảnh và HTML lưu ở [assets/stitch/IT-1/](../../assets/stitch/IT-1/) (4 màn, giữ tên file như IT-0) và [assets/stitch/IT-2/](../../assets/stitch/IT-2/) (5 màn, tên theo mã màn). IT-3 ([AI-07](../prompts/AI-07-stitch-IT-3.md)) chưa có trong zip.
- **Ai làm:** Claude so từng màn với phát hiện F1–F9 của [AI-04](AI-04-critique-IT-0.md), soi lỗi mới theo Nielsen (H1–H10), WCAG 2.x và luật [DESIGN.md](../../design/DESIGN.md); nhóm quyết định.
- **Bằng chứng:** cỡ chữ, màu và token đọc từ HTML Stitch xuất ra; lỗi bố cục đọc từ ảnh `screen.png` Stitch render.

## 1. Phát hiện cũ đã sửa chưa

| # | Phát hiện IT-0 | Sau IT-1 | Sau IT-2 | Bằng chứng |
|---|---|---|---|---|
| F1 | “Tong Quan” mất dấu, logo và avatar trên app bar | **Đã sửa** | | `IT-1/01-tong-quan`: “Tổng quan”, chỉ còn chuông |
| F2 | Chip đè chip ở hàng slot | **Đã sửa** ở Tổng quan, nhưng sinh lỗi mới F10 | | Chip “Chưa bắt đầu” nằm riêng bên phải |
| F3 | 5 họ màu, nền ngả tím | **Đã sửa** | | Không còn mã tím nào trong 9 file HTML; primary `#18181B` |
| F4 | Đoạn hướng dẫn quét QR | **Đã sửa** | | `IT-1/03-phien-diem-danh`: chỉ còn QR, “Đổi mã sau 12s”, “32/35 đã quét” |
| F5 | Chữ 11–12 px | **Đã sửa** | Vẫn đạt | 9 file HTML không còn `text-xs` hay `text-[1x px]` dưới 14 |
| F6 | Thanh % lặp số 32/35 | **Đã sửa** ở Điểm danh; **tái phạm** ở Chi tiết slot (thêm thanh dưới “32/35”) | **Đã sửa** | `IT-1/02-chi-tiet-slot` so với `IT-2/GV-101.D2` |
| F7 | Chi tiết slot hiện số khi chưa mở điểm danh | Chưa sửa (đúng phạm vi IT-2) | **Đã sửa** | `GV-101.D1`, `.D2` không có số; `.D3` chỉ có “34 có mặt · 1 vắng” |
| F8 | Hàng “Nhãn: giá trị” | **Đã sửa** | | Icon + giá trị: giờ, môn, lớp, phòng |
| F9 | Cần chú ý: băng luật, lọc, “Xuất báo cáo”, tên bị cắt | Chưa sửa (đúng phạm vi IT-2) | **Đã sửa** | `IT-2/GV-104.D`: hai nhóm “Đã chạm ngưỡng”, “Sắp chạm ngưỡng”, tên đầy đủ, không nút xuất |

Kết quả: 9/9 phát hiện IT-0 đã đóng sau hai vòng. Prompt chia theo loại vấn đề (IT-1 màu và chữ, IT-2 trạng thái) có tác dụng, nhưng Stitch tái phạm F6 ở màn không được nhắc tên.

## 2. Phát hiện mới

| # | Màn (file) | Vấn đề quan sát được | Căn cứ | Mức | Quyết định | Sửa ở đâu |
|---|---|---|---|---|---|---|
| F10 | GV-101, GV-102, GV-104, thanh dưới (IT-1, IT-2) | Chữ trong chip và nút **xuống dòng** ở 360 dp: “Đang diễn / ra”, “Sắp / tới”, “Trực / tiếp”, “Đã chạm / ngưỡng”, “2 sinh / viên”; nút “Sửa điểm / danh” tràn khỏi viền nút (`GV-101.D3`); nhãn “Tổng / quan” ở thanh dưới | WCAG 1.4.10 (không vỡ bố cục); H8 | Cao | **Modify**: chip và nút chỉ một dòng, co theo chữ | Figma: Status chip, Button, Bottom navigation dùng Auto Layout hug, một dòng (đã đạt, A-8 trong [design-decisions.md](../../design/design-decisions.md)) |
| F11 | GV-102 Điểm danh (`IT-1/03-phien-diem-danh`) | Tên sinh viên bị cắt “Nguyễn Hoà…”, “Trần Minh Đ…” vì hai nút chữ “Có mặt”, “Vắng” chiếm chỗ | D-06, persona P-01 nhận mặt và tên; H6 | Cao | **Modify**: nút ✓ ✕ dạng icon 48 × 48, tên đủ | Figma Student row (GV-102 .D1, .D2) |
| F12 | GV-201 Hồ sơ (`IT-2/GV-201.D`) | Nút chính “Nhắc sinh viên” **mất chữ**: HTML có chữ nhưng dùng class `text-on-primary` không có trong cấu hình Tailwind của màn, nên chữ `#18181B` nằm trên nền `#18181B` (1:1) | WCAG 1.4.3 (≥ 4,5:1); H1 | Cao | **Reject** mã Stitch | Figma token `on-primary` `#FAFAFA` trên `primary`, 16,97:1 |
| F13 | GV-201 (`IT-2/GV-201.D`) | App bar ghi “Chi tiết slot” cho màn hồ sơ | H4 nhất quán tên màn | Vừa | **Modify** | Figma app bar “Hồ sơ” |
| F14 | GV-201 (`IT-2/GV-201.D`) | Số “3/4” cỡ chữ thường: class `text-metric-num` không được định nghĩa, nên số rơi về 16 px | T4 số là chữ chính | Vừa | **Modify**: số lớn 32 | Figma GV-201 .D |
| F15 | Nhiều màn | Dữ liệu mẫu sai: “Học kỳ Fall 2024”, ngày 2024 | H2 | Thấp | **Reject** dữ liệu mẫu, không ảnh hưởng thiết kế | Figma dùng dữ liệu tuần 20/10/2026. Khi soát lỗi này, nhóm thấy chính Figma ghi “Thứ Hai, 20/10” (đúng là Thứ Ba) ở 24 lớp chữ trang 03, 06; đã sửa cả ba ngày trong tuần |

Nguyên nhân chung của F12 và F14: ở IT-2 Stitch tự sinh bộ token kiểu Material (“Neutral Precision”, `IT-2/stitch-DESIGN.md`) nhưng cấu hình Tailwind của màn lại theo tên shadcn, nên vài class trỏ vào token không tồn tại. Lỗi này không thấy được nếu chỉ đọc mã; phải nhìn ảnh render.

## 3. Giữ lại

Năm ý tưởng A1–A5 của IT-0 còn nguyên qua hai vòng (ảnh đại diện, thẻ Chốt ngay, QR kèm bộ đếm, danh sách chưa quét, mã tự đổi). Không có ý tưởng mới đáng giữ.

## 4. Tổng kết

Hai vòng đóng 9/9 phát hiện cũ và sinh 6 phát hiện mới (3 Cao, 2 Vừa, 1 Thấp). Lỗi lặp lại là **bố cục ở 360 dp** (F10, F11), thứ Stitch không tự kiểm. Vì vậy màn cuối dựng trên Figma bằng component có Auto Layout thay vì sửa tiếp trong Stitch.
