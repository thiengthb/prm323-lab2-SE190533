# DESIGN.md · Style guide (design brief cho Stitch)

> **v3.0 · 29/10/2026.** v1.0 viết **trước** prompt Stitch đầu tiên (đề mục 4, bước 3; luật 4 trong [retro-v1](../process/retro-v1.md)). Mọi màn trong Figma phải theo file này. Token ở đây khớp 1–1 với biến `Color`, `Spacing`, `Radius`, `Size` và 9 kiểu chữ `type/*` trong file Figma.
>
> **Thay đổi v2.0 → v3.0:** chọn hướng **C · Nổi khối, cam FPT** trong 3 hướng thử ngày 26/10 (trang Figma `00 Hướng`): viền 2 px, gờ đáy 2 px như nút bấm thật, font tròn **Nunito**, màu nhấn cam đất `#B9551F`; sau đó 4 vòng duyệt từng màn với thien (27–29/10) chốt luật chung: chữ chỉ dùng 9 kiểu, lề màn 12, icon 20/24 (quyết định [D-13](design-decisions.md), [D-14](design-decisions.md)). Lý do: bản Xanh đại dương đúng luật nhưng vẫn "nhạt", giống mọi app quản lý; cam là màu nhận diện FPT nên giảng viên thấy quen.
>
> **Thay đổi v1.1 → v2.0:** màu nhấn từ Đen trắng sang Xanh đại dương `#0B6283` (D-11). **v1.0 → v1.1:** Violet `#7C3AED` sang Đen trắng (D-01).

## 1. Tinh thần

**Gọn, chắc tay, rõ việc chính.** Nền trắng trung tính, **một** màu nhấn cam đất; thẻ và nút có viền 2 px và gờ đáy 2 px nên nhìn như vật bấm được (kiểu Duolingo), không đổ bóng mờ. Màn hình nói bằng **số, icon và trạng thái**, không bằng câu.

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

Tương phản tính theo công thức WCAG 2.x (29/10, script trong nhật ký AI-13).

| Token | Hex | Dùng cho | Tương phản |
|---|---|---|---|
| `color/bg`, `color/surface` | `#FFFFFF` | Nền màn, thẻ, sheet, ô nhập | — |
| `color/muted-surface` | `#F4F4F4` | Nền segmented control, skeleton, ô ghi chú | — |
| `color/border` = `color/edge` | `#E5E5E5` | Viền 2 px và gờ đáy của thẻ | — |
| `color/border-control` | `#8F8F8F` | Viền ô nhập, radio, nút outline | 3,23:1 trên trắng (≥ 3:1, WCAG 1.4.11) |
| `color/fg-strong` | `#1F1F1F` | Số lớn, tiêu đề | 16,48:1 |
| `color/fg` | `#3C3C3C` | Chữ chính | 11,03:1 |
| `color/fg-muted` | `#6B6B6B` | Chữ phụ: giờ, phòng, mã SV | 5,33:1 trên trắng; 4,85:1 trên muted-surface |
| `color/fg-disabled` | `#AFAFAF` | Chữ trên điều khiển bị tắt | Miễn trừ WCAG |
| `color/primary` | `#B9551F` | Nút chính, thẻ slot đang diễn ra, tab đang chọn, link | 4,79:1 với chữ trắng và trên trắng |
| `color/primary-pressed` = `color/edge-primary` | `#8A3D14` | Gờ đáy nút chính, nút khi nhấn | 7,61:1 với chữ trắng |
| `color/primary-soft` | `#FBEFE8` | Nền mục đang chọn, chip lý do đang chọn | — |
| `color/primary-soft-edge` | `#F9B98F` | Viền chip đang chọn | — |
| `color/on-primary-soft` | `#9A4518` | Chữ, icon trên primary-soft | 5,75:1 |
| `color/brand` | `#F26F21` | Chỉ icon ứng dụng (cam FPT gốc); không dùng cho chữ | — |
| `color/success` / `-soft` | `#15803D` / `#ECFDF3` | **Có mặt**, đã chốt | 4,76:1 |
| `color/warning` / `-soft` | `#A15C00` / `#FFF6DD` | **Chưa chốt**, sắp chạm ngưỡng (3/4, 4/4) | 4,81:1 trên soft; 5,19:1 trên trắng |
| `color/danger` / `-soft` | `#B42318` / `#FEF0EF` | **Vắng**, lỗi, quá ngưỡng (5/4), nút destructive | 5,92:1 trên soft; 6,57:1 với chữ trắng |
| `color/scrim` | `#1F1F1F` 50% | Lớp phủ sau hộp thoại, sheet | — |
| `color/camera` | `#000000` | Nền khung camera SV-101 | — |

**Kỷ luật màu:** cam chỉ cho hành động, lựa chọn và **một** thẻ quan trọng nhất mỗi màn (slot đang diễn ra); xanh lá, hổ phách, đỏ chỉ cho trạng thái. Mỗi trạng thái luôn kèm icon và chữ (T3).

**Rủi ro đã biết:** cam đất (sắc độ 21°) và hổ phách cảnh báo (34°) cùng họ ấm. Giảm bằng ba cách: hổ phách chỉ xuất hiện ở chip/số trạng thái, luôn có icon tam giác hoặc đồng hồ; cam chỉ ở nút và thẻ slot; số liệu ngưỡng dùng hổ phách, không dùng cam.

## 4. Chữ

Font **Nunito** (tròn, đủ dấu tiếng Việt). Chỉ dùng **9 kiểu** dưới đây (luật chung vòng duyệt 3); không cỡ nào dưới 12, chữ thường không dưới 13.

| Token | Cỡ / dòng | Độ đậm | Dùng cho |
|---|---|---|---|
| `type/display` | 28 / 34 | Bold | Số lớn: “32/35”, “3/4” |
| `type/title-lg` | 22 / 28 | Bold | Tiêu đề màn cấp 0, tiêu đề trạng thái |
| `type/title` | 17 / 24 | Bold | Tiêu đề màn cấp 1–2, giờ trên thẻ slot |
| `type/section` | 16 / 22 | Bold | Tiêu đề nhóm (“Chưa quét (3)”, “Fall 2026”) |
| `type/body` | 15 / 22 | Medium | Nội dung chính, tên sinh viên |
| `type/body-strong` | 15 / 22 | SemiBold | Tên lớp, mã môn |
| `type/label` | 14 / 20 | SemiBold | Nhãn nút, chip, tab |
| `type/body-sm` | 13 / 18 | Medium | Chữ phụ: giờ, phòng, MSSV |
| `type/caption` | 12 / 16 | SemiBold | Nhãn thanh điều hướng dưới, chú thích nhỏ |

## 5. Khoảng cách, bo góc, viền

| Nhóm | Token |
|---|---|
| Khoảng cách (lưới 4) | `space/4` · `space/8` · `space/12` · `space/16` · `space/20` · `space/24` · `space/32` |
| Lề màn | **12** hai bên (luật chung vòng 3); 16–24 giữa các nhóm; 8–12 giữa các thẻ |
| Bo góc | `radius/sm` 6 (chip trạng thái) · `radius/md` = `radius/lg` 8 (nút, thẻ, ô nhập) · `radius/xl` 10 (dialog, sheet) · `radius/full` 999 (avatar, chip chọn) |
| Viền và gờ | Thẻ: viền 2 px `color/edge` + gờ đáy 2 px cùng màu. Nút chính: gờ đáy 2 px `color/edge-primary`. Không đổ bóng mờ, trừ snackbar |
| Vùng chạm | `size/touch` 48: nút đáy, hàng, tab, icon bấm được cao ít nhất 48 |
| Icon | Lucide, nét 2, cỡ `size/icon-20` hoặc `size/icon-24`; avatar `size/avatar` 40 |

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
| Button | primary, outline, ghost, destructive × default, pressed, disabled, loading (16 biến thể) | Cao 48 trên màn (component gốc 40 + gờ, kéo giãn), bo 8, gờ đáy 2, chữ `type/label` |
| Text field | default, focused, filled, error, disabled | Cao 48, viền `border-control`; focus viền primary 2; lỗi viền danger + một dòng lỗi |
| Card | default, pressed (khi bấm được) | Nền surface, viền 2 + gờ đáy 2 `color/edge`, bo 8, padding 12–16 |
| Bottom navigation | 4 biến thể, mỗi tab được chọn | Icon 24 + nhãn 14; tab chọn: icon và chữ primary, nền chỉ báo primary-soft |
| App bar | top-level, nested (nút Quay lại), with actions | Cao 64 (top-level), 56 (nested) |
| Dialog | confirmation, destructive/error | Bo lg, `elevation/2`, tối đa 2 nút |
| Loading | skeleton theo hình thẻ; spinner trong nút | — |
| Empty state | icon Lucide 24 trong vòng tròn muted-surface 48 + 1 câu ≤ 6 từ + 1 nút | — |
| Error state | icon + nguyên nhân bằng lời thường + nút “Thử lại” | — |
| Status chip | present, absent, pending, warning (6 biến thể) | Icon 16 + chữ, viền 2 màu trạng thái, nền soft; badge tròn (Status badge) cho thẻ slot |
| Chip | on, off | Chip chọn lý do (GV-OV5): bo tròn, viền 2; đang chọn: nền primary-soft, viền primary-soft-edge |
| Student row | default, exception (chưa quét), marked | Avatar 40, tên, chip; mã SV chỉ ở hồ sơ (GV-201); cả hàng cao ≥ 56 |
| Attention row | near, over | Avatar 40, tên, icon + số “3/4” màu trạng thái; không chip, không chữ “buổi vắng” (nhóm đã có tiêu đề) |
| Slot card | upcoming, live, unclosed, closed | Giờ, môn, phòng, chip trạng thái; **live: nền primary, chữ trắng, nút trắng**; unclosed: viền hổ phách + nút “Chốt ngay” |
| Segmented control | mỗi mục được chọn | Hôm nay / Ngày mai / Tuần |
| Snackbar | with action | “Đã chốt” + Hoàn tác |
| Status bar, Browser bar | — | Chỉ để trình bày: giờ + sóng, wifi, pin; web SV-* thêm thanh địa chỉ để nhìn là biết web |

## 8. Không làm

- Không gradient, không ảnh minh họa trang trí, không nhiều màu nhấn, không bóng mờ.
- Không dùng MSSV thật của thành viên nhóm làm dữ liệu mẫu; mỗi sinh viên mẫu một MSSV riêng.
- Không thẻ lồng thẻ. Không chia một nhóm thông tin thành nhiều thẻ.
- Không đếm sĩ số, không nhập số người (E-04).
- Không lặp cùng một thông tin ở hai chỗ trên một màn.
