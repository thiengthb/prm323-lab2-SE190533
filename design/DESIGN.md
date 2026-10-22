# DESIGN.md · Style guide (design brief cho Stitch)

> **v2.0 · 22/10/2026.** v1.0 viết **trước** prompt Stitch đầu tiên (đề mục 4, bước 3; luật 4 trong [retro-v1](../process/retro-v1.md)). Mọi màn trong Stitch và Figma phải theo file này.
>
> **Thay đổi v1.1 → v2.0:** màu nhấn từ Đen trắng sang **Xanh đại dương** (petrol `#0B6283`), nền và chữ ngả lạnh theo cùng tông; thẻ slot đang diễn ra thành thẻ nền màu; bớt chữ phụ lần hai (quyết định [D-11](design-decisions.md), [D-12](design-decisions.md)). Lý do: thien thấy bản Đen trắng chưa đẹp, cả màn chỉ có xám nên không có điểm nhìn.
>
> **Thay đổi v1.0 → v1.1:** đổi màu nhấn từ Violet `#7C3AED` sang **Đen trắng** (shadcn mặc định, Zinc 900 `#18181B`). Lý do: ở Stitch IT-0 màn có tới 5 họ màu và nền ngả tím kiểu Material 3, nhìn không ra chất shadcn; thien chọn phương án Đen trắng trong 3 phương án so sánh (quyết định [D-01](design-decisions.md)). Các token khác giữ nguyên.

## 1. Tinh thần

**Gọn, yên tĩnh, rõ việc chính.** Phong cách shadcn/ui đặt lên mobile: nền trung tính, **một** màu nhấn, viền mảnh, bo vừa, gần như không đổ bóng. Màn hình nói bằng **số, icon và trạng thái**, không bằng câu.

Ba câu kiểm trước khi chốt một màn (theo UI Simplicity Checklist):
1. **5 giây:** nhìn 5 giây, nói được màn này để làm gì và nút chính là gì.
2. **Thang xám:** chuyển sang đen trắng, vẫn phân biệt được mọi trạng thái.
3. **Cắt bớt:** xóa thử từng chữ, thẻ, màu; cái gì xóa mà không mất thông tin thì xóa.

## 2. Luật chữ trên màn hình

| # | Luật |
|---|---|
| T1 | **Không có câu giải thích tính năng.** Giải thích để ở chú thích Figma, ngoài khung 360 × 800 |
| T2 | Tiêu đề màn ≤ 3 từ. Nhãn nút ≤ 3 từ, bắt đầu bằng động từ (“Mở điểm danh”, “Chốt”) |
| T3 | Trạng thái = **icon + màu + 1–2 từ** (✓ Có mặt, ✕ Vắng, ◷ Chưa) |
| T4 | Số là chữ chính: “3/8” to hơn nhãn “buổi vắng” |
| T5 | Ngân sách: tối đa khoảng **25 từ** ngoài dữ liệu (tên, giờ, phòng, số) trên mỗi màn |
| T6 | Thông báo lỗi = nguyên nhân bằng lời thường (≤ 6 từ) + một nút hành động |
| T7 | Tiếng Việt có dấu; không viết hoa toàn bộ |

## 3. Màu (light theme, bắt buộc)

Tương phản tính theo công thức WCAG 2.x.

| Token | Hex | Dùng cho | Tương phản |
|---|---|---|---|
| `color/bg` | `#F3F6F8` | Nền màn | — |
| `color/surface` | `#FFFFFF` | Thẻ, sheet, ô nhập, thanh điều hướng | — |
| `color/muted-surface` | `#EAF0F3` | Nền segmented control, skeleton, nút phụ | — |
| `color/border` | `#DCE4E9` | Viền thẻ, đường chia (trang trí) | — |
| `color/border-control` | `#6A7C87` | Viền ô nhập, viền nút outline | 4,33:1 trên surface (≥ 3:1, WCAG 1.4.11) |
| `color/fg` | `#0D1B24` | Chữ chính | 16,13:1 trên bg |
| `color/fg-muted` | `#4E5F6A` | Chữ phụ: giờ, phòng, mã SV | 6,11:1 trên bg |
| `color/fg-disabled` | `#A0AEB8` | Chữ trên điều khiển bị tắt | Miễn trừ WCAG (thành phần không hoạt động) |
| `color/primary` | `#0B6283` | Nút chính, thẻ slot đang diễn ra, tab đang chọn, viền focus, link | 6,80:1 với chữ trắng; 6,26:1 trên bg |
| `color/primary-pressed` | `#084C66` | Nút chính khi nhấn | 9,39:1 với chữ trắng |
| `color/primary-soft` | `#E3F1F6` | Nền mục đang chọn, chip Sắp tới, thẻ đếm “đã quét” | — |
| `color/on-primary-soft` | `#08506B` | Chữ, icon trên primary-soft | 7,67:1 trên primary-soft |
| `color/on-primary` | `#FFFFFF` | Chữ trên primary | 6,80:1 trên primary |
| `color/success` | `#15803D` | **Có mặt**, đã chốt | 4,79:1 trên success-soft |
| `color/success-soft` | `#F0FDF4` | Nền chip Có mặt | — |
| `color/warning` | `#B45309` | **Chưa điểm danh**, sắp chạm ngưỡng | 4,84:1 trên warning-soft |
| `color/warning-soft` | `#FFFBEB` | Nền chip cảnh báo | — |
| `color/danger` | `#B91C1C` | **Vắng**, lỗi, đã chạm ngưỡng, nút destructive | 5,91:1 trên danger-soft; 6,47:1 với chữ trắng |
| `color/danger-soft` | `#FEF2F2` | Nền chip Vắng, nền thẻ lỗi | — |
| `color/scrim` | `#0D1B24` 50% | Lớp phủ sau hộp thoại, sheet | Danh sách phía sau vẫn đọc được |

**Kỷ luật màu:** xanh đại dương (primary) chỉ cho hành động, lựa chọn và **một** thẻ quan trọng nhất mỗi màn (slot đang diễn ra); xanh lá, hổ phách, đỏ chỉ cho trạng thái; không màu nào để trang trí. Mỗi trạng thái luôn kèm icon và chữ (không truyền tin chỉ bằng màu).

**Vì sao Xanh đại dương (v2.0):** bản Đen trắng sạch nhưng cả màn chỉ có xám, không có điểm nhìn; thien chê chưa đẹp. Petrol là màu nhấn duy nhất, đậm và trầm nên hợp giọng “công cụ làm việc”, chữ trắng trên nó đạt 6,8:1. Nhìn lại các lý do của D-01:
- **So với xanh FAP:** petrol (sắc độ 197°) đậm và ngả lục hơn xanh liên kết kiểu Bootstrap (208°, `#337AB7`), nhưng vẫn cùng họ xanh dương. Đây là rủi ro còn lại, chưa đo trên ảnh chụp FAP thật.
- **So với xanh lá “Có mặt”:** cách 55° sắc độ, và trạng thái luôn có icon + chữ (T3), nên không lẫn.
- **Phương án đã bỏ:** cam thương hiệu FPT (lẫn với hổ phách “Sắp chạm ngưỡng”); Violet (bị bỏ ở IT-0, F3); Teal sáng (lẫn với “Có mặt”).

**Vì sao Đen trắng (v1.1, đã thay):** đúng theme mặc định của shadcn/ui; ba màu trạng thái là thứ duy nhất có màu. Phương án đã bỏ lúc đó: Indigo `#4F46E5` (gần xanh FAP), Teal (lẫn với xanh “Có mặt”), Violet v1.0 (xem D-01).

## 4. Chữ

Font **Inter** (có đủ dấu tiếng Việt). Không cỡ nào dưới 14.

| Token | Cỡ / dòng | Độ đậm | Dùng cho |
|---|---|---|---|
| `type/display` | 32 / 40 | Semi Bold | Số lớn: “3/8”, “35/36” |
| `type/title-lg` | 22 / 28 | Semi Bold | Tiêu đề màn cấp 0 |
| `type/title` | 18 / 24 | Semi Bold | Tiêu đề màn cấp 1–2, tiêu đề thẻ |
| `type/body` | 16 / 24 | Regular | Nội dung chính, tên sinh viên |
| `type/body-strong` | 16 / 24 | Medium | Tên lớp, mã môn |
| `type/label` | 14 / 20 | Medium | Nhãn nút, chip, tab, tiêu đề nhóm |
| `type/body-sm` | 14 / 20 | Regular | Chữ phụ: giờ, phòng |

## 5. Khoảng cách, bo góc, đổ bóng

| Nhóm | Token |
|---|---|
| Khoảng cách (lưới 4) | `space/4` 4 · `space/8` 8 · `space/12` 12 · `space/16` 16 · `space/20` 20 · `space/24` 24 · `space/32` 32 |
| Lề màn | `space/20` hai bên; `space/24` giữa các nhóm; `space/12` giữa các thẻ trong nhóm |
| Bo góc | `radius/sm` 8 (chip) · `radius/md` 12 (nút, ô nhập) · `radius/lg` 16 (thẻ, sheet, dialog) · `radius/full` 999 (avatar, badge) |
| Đổ bóng | `elevation/0`: không bóng, viền `color/border` (thẻ) · `elevation/1`: 0 1 2 / 6% đen (thanh điều hướng) · `elevation/2`: 0 8 24 / 12% đen (dialog, sheet, snackbar) |
| Vùng chạm | `size/touch` 48: mọi nút, hàng, tab, icon bấm được cao ít nhất 48 |
| Icon | Lucide, nét 2, cỡ 20 hoặc 24 |

## 6. Bố cục mobile

- Khung 360 × 800 dp; kiểm thêm ở 412 dp. Nội dung co giãn theo chiều ngang (Auto Layout fill), không cố định bề rộng.
- **Vùng ngón cái:** hành động chính ở nửa dưới màn (nút cố định đáy hoặc trong thẻ thấp nhất), không đặt ở góc trên.
- **Một hành động chính mỗi màn** (nút primary). Hành động phụ dùng outline hoặc ghost.
- Thanh điều hướng dưới 4 tab cho app giảng viên: Tổng quan · Lịch · Lớp · Tài khoản. Màn cấp 1–2 có app bar với nút Quay lại.
- Danh sách dài thì cuộn; app bar và nút đáy cố định.
- Web sinh viên: một cột, không thanh điều hướng dưới; tối đa 3 màn.

## 7. Luật component

| Component | Biến thể và trạng thái bắt buộc | Ghi chú |
|---|---|---|
| Button | primary, outline, ghost, destructive × default, pressed, disabled, loading | Cao 48, bo `radius/md`, chữ `type/label` |
| Text field | default, focused, filled, error, disabled | Cao 48, viền `border-control`; focus viền primary 2; lỗi viền danger + một dòng lỗi |
| Card | default, pressed (khi bấm được) | Nền surface, viền border, bo lg, padding 16 |
| Bottom navigation | 4 biến thể, mỗi tab được chọn | Icon 24 + nhãn 14; tab chọn: icon và chữ primary, nền chỉ báo primary-soft |
| App bar | top-level, nested (nút Quay lại), with actions | Cao 64 (top-level), 56 (nested) |
| Dialog | confirmation, destructive/error | Bo lg, `elevation/2`, tối đa 2 nút |
| Loading | skeleton theo hình thẻ; spinner trong nút | — |
| Empty state | icon Lucide 24 trong vòng tròn muted-surface 48 + 1 câu ≤ 6 từ + 1 nút | — |
| Error state | icon + nguyên nhân bằng lời thường + nút “Thử lại” | — |
| Status chip | present, absent, pending, warning | Icon 16 + chữ, nền soft tương ứng |
| Student row | default, exception (chưa quét), marked | Avatar 40, tên, chip; mã SV chỉ ở hồ sơ (GV-201); cả hàng cao ≥ 56 |
| Attention row | near, over | Avatar 40, tên, icon + số “3/4” màu trạng thái; không chip, không chữ “buổi vắng” (nhóm đã có tiêu đề) |
| Slot card | upcoming, live, unclosed, closed | Giờ, môn, phòng, chip trạng thái; **live: nền primary, chữ trắng, nút trắng**; unclosed: viền hổ phách + nút “Chốt ngay” |
| Segmented control | mỗi mục được chọn | Hôm nay / Ngày mai / Tuần |
| Snackbar | with action | “Đã chốt” + Hoàn tác |
| Status bar, Browser bar | — | Chỉ để trình bày: giờ + sóng, wifi, pin; web SV-* thêm thanh địa chỉ để nhìn là biết web |

## 8. Không làm

- Không gradient, không ảnh minh họa trang trí, không nhiều màu nhấn.
- Không thẻ lồng thẻ. Không chia một nhóm thông tin thành nhiều thẻ.
- Không đếm sĩ số, không nhập số người (E-04).
- Không lặp cùng một thông tin ở hai chỗ trên một màn.
