# Lab 2 v2 · Kế hoạch làm lại từ đầu

| Mục | Nội dung |
|---|---|
| Trạng thái | **v0.2** (16/10 tối): cập nhật theo câu trả lời của thien, xem mục 12. Mục 12 thắng khi khác các mục trên |
| Ngày | 16/10/2026, sau buổi thuyết trình 14:30 |
| Đầu vào đã đọc | Đề Lab 2 (12 trang), Presentation Assessment Guidelines, UI Simplicity Checklist (20 tiêu chí), PRM393 Persona Guideline, ghi nhớ của thien sau buổi thuyết trình, tóm tắt của nhóm, repo v1 (52 commit, khoảng 52.000 chữ tài liệu), kịch bản slide v9 |
| Chưa đọc được | `checklist.design/mobile`: trang chặn truy cập từ môi trường của Claude. Phần dùng checklist này ở mục 5 là **suy luận từ hiểu biết chung**, cần thien mở trang để đối chiếu |
| Vai trò | Claude đóng vai BA: đề xuất, phản biện, giữ quy trình. thien chốt mọi quyết định |

---

## 0. Tóm tắt một phút

1. **v1 sai ở gốc, không chỉ ở bề mặt.** Nghiên cứu dựa trên 11 cuộc phỏng vấn mô phỏng bằng AI, nên sản phẩm phản ánh điều AI tưởng giảng viên cần (đếm sĩ số, kiểm tra ngẫu nhiên, chống quét hộ) thay vì điều giảng viên thật cần (không quên điểm danh, xem lịch, chăm sóc sinh viên). Màu, chữ nhiều và thứ tự slide là hệ quả, không phải nguyên nhân.
2. **v2 bắt đầu bằng người thật.** Người dùng thật đầu tiên và quan trọng nhất là chính GVHD. Không có ít nhất 3 cuộc phỏng vấn giảng viên thật thì không mở Stitch.
3. **Sản phẩm v2:** app mobile **cho giảng viên** (tổng quan, lịch, lớp, điểm danh, sinh viên cần chú ý), cộng **web sinh viên tối giản** (quét mã, xem số buổi vắng còn lại, báo sai). Không còn đếm sĩ số.
4. **Không đổi tên repo GitHub.** Đề bắt buộc tên `prm323-lab2-<mã SV>`. Archive bằng tag + nhánh, rồi làm mới trên `main` (mục 4).
5. **Có 10 câu hỏi cần thien trả lời** trước khi bắt đầu Giai đoạn 1 (mục 10). Câu quan trọng nhất: hạn nộp lại là khi nào, và có hẹn phỏng vấn GVHD được không.

---

## 1. Rà soát v1: vì sao lệch insight của thầy

### 1.1 Năm nguyên nhân gốc

| # | Nguyên nhân gốc | Bằng chứng trong v1 | Hệ quả thầy nhìn thấy |
|---|---|---|---|
| R1 | **Dữ liệu người dùng là mô phỏng.** 11 người trả lời R01–R11 đều do subagent AI đóng vai (D-05). Lý do chính của persona là “Assumed” từ đề của GVHD (D-19, D-33) | `research/05-raw/R01..R11`, `ux/persona.md` mục 12: “chưa được kiểm chứng với người dùng thật” | Thầy: “AI chưa hiểu sâu FAP”, “không mặc định AI biết nội dung sau đăng nhập” |
| R2 | **Khung bài toán sai từ đầu: “bổ trợ FAP” thay vì “thay một phần FAP”.** Phạm vi bị khóa vào một khoảnh khắc (ghi điểm danh một slot) | `ux/persona.md` mục 1: “Ứng dụng bổ trợ FAP, không thay FAP” | Thiếu tổng quan, lịch tuần, lớp học; giảng viên vẫn phải mở hai app |
| R3 | **Giải pháp đi trước vấn đề.** Đã có app thật `fap-attendance-assistant` (QR, mở từ xa, extension) trước khi nghiên cứu, rồi nghiên cứu được dùng để biện minh | README: “Spec cũ 38 màn, 8 flow”; D-19 lấy QR từ app thật | Tính năng chống quét hộ (SC-04 đối chiếu sĩ số, SC-05 kiểm tra ngẫu nhiên) mà giảng viên thấy thừa |
| R4 | **Tài liệu và màn hình đều quá nhiều chữ.** Viết để chứng minh, không phải để người dùng dùng | 52.000 chữ tài liệu; thầy nhận xét chữ quá nhiều trên màn Figma | Khó đọc, UI “không nổi trội”, slide dày |
| R5 | **Trình bày theo thứ tự của bảng chấm, không theo thứ tự tư duy.** Slide đi theo bảng 12 slide của guideline (Design System ở slide 9, sau Final UI) | `kich-ban-thuyet-trinh-v9.md`: slide 5 prompt, slide 9 design system | Thầy: “slide lộn tùng phèo”, style guide phải trước Stitch |

### 1.2 Giữ gì, bỏ gì từ v1

| Giữ (đưa vào v2, ghi rõ nguồn là v1) | Bỏ |
|---|---|
| Nghiên cứu bàn giấy về quy định FPTU: `research/02-desk/fap-edit-window.md`, `fptu-hcm.md` (nguồn văn bản, vẫn đúng) | Toàn bộ phỏng vấn mô phỏng R01–R11 làm bằng chứng chính. Chỉ giữ làm “giả thuyết cần kiểm chứng” |
| `O-01` quan sát của thien, `O-02` ảnh giao diện FAP (người thật, Observed) | SC-04 Đối chiếu sĩ số, SC-05 Kiểm tra ngẫu nhiên, mọi bước đếm người |
| Khung tài liệu theo đề (persona, user-flow, DESIGN.md, handoff 6 mục, 2 bảng ánh xạ) | Bảng màu lấy từ FAP (primary `#4254BA`) |
| Kinh nghiệm dựng Figma bằng MCP: biến token, component có variant, prototype không dead end | Laptop + extension tự điền FAP làm trung tâm luồng (thầy không nhắc tới; cần hỏi lại) |
| Kỷ luật ghi log AI nguyên văn, quyết định Accept / Modify / Reject có lý do | Hệ mã dày đặc (CR-01..73, D-01..34, F-, N-, O-, RB-, TC-) trên slide |

### 1.3 Bài học, viết thành luật cho v2

| Luật | Vì sao |
|---|---|
| **L1.** Không có câu trả lời của người thật thì một nhu cầu chỉ là giả thuyết, và không được thành tính năng chính | R1, R3 |
| **L2.** Mỗi tính năng phải trả lời được: persona nào, nỗi đau nào, bằng chứng nào. Không trả lời được thì cắt | Thầy: “không giữ tính năng chỉ vì AI gợi ý” |
| **L3.** Màn hình không giải thích chính nó. Giải thích nằm ở chú thích Figma và tài liệu, không nằm trên UI | Thầy và thien cùng đồng ý; R4 |
| **L4.** Style guide trước, AI sau | Đề (DESIGN.md trước prompt Stitch đầu tiên) và thầy |
| **L5.** Kể theo thứ tự tư duy: mục tiêu → nghiên cứu → persona → giải pháp → cấu trúc → hình | R5 |
| **L6.** Không tin AI review là đủ. Mỗi cổng (gate) có một người thật kiểm | Thầy: “tự kiểm tra, không chỉ dựa vào AI review nhiều lần” |

---

## 2. Hợp nhất góp ý: thầy, thien, nhóm

Nguyên tắc: **insight của thầy là mục tiêu; ghi nhớ của thien là nguồn chính; tóm tắt của nhóm để bổ sung và đối chiếu.** Bản tóm tắt nhóm tự ghi là “từ nhận dạng âm thanh có biên tập, chưa kiểm chứng hoàn toàn”, nên chỗ nào chỉ một nguồn nói thì đánh dấu cần xác nhận.

| # | Chủ đề | Thien nhớ | Nhóm ghi | Kết luận BA | Độ chắc |
|---|---|---|---|---|---|
| G1 | Người dùng chính | App tập trung giảng viên | Ưu tiên GV; phần SV chỉ thao tác cần thiết | **Thống nhất.** App mobile = giảng viên. SV dùng web | Chắc |
| G2 | Kênh của sinh viên | Web SV (điện thoại, laptop tùy chọn): quét mã, báo sai, cảnh báo sắp hết slot | “Profile cần thêm cảnh báo SV sắp hết slot” | **Có mâu thuẫn nhỏ.** “Profile” là hồ sơ SV trên web, hay trang SV trong app GV? Đề xuất làm cả hai mặt: SV tự thấy trên web, GV thấy trong app. Cần thien xác nhận (Câu hỏi Q4) | Cần hỏi |
| G3 | Đếm sinh viên | Thừa; GV nhớ mặt khoảng 35 người qua 10 tuần | Bỏ đếm người, tăng giảm số lượng | **Thống nhất bỏ.** Nhưng xem phản biện P2: bỏ đếm không có nghĩa là bỏ chống sai | Chắc |
| G4 | Phạm vi app | Quản lý lớp, lịch tuần, hôm nay, ngày mai, thời gian biểu, tổng quan | Làm rõ tổng quan, lớp học, lịch dạy, buổi theo ngày; thêm tổng quan, lịch tuần | **Thống nhất.** 4 khu vực cấp một: Tổng quan, Lịch, Lớp, Tài khoản | Chắc |
| G5 | Trừ lương | GV không điểm danh thì bị trừ lương | “Persona quên điểm danh không tính lương” | **Đây là insight mạnh nhất**, đổi nỗi đau chính từ “mất thời gian đọc tên” sang “quên là mất tiền”. Phải xác minh quy định thật (Q2) | Cần xác minh |
| G6 | Báo cáo | Nhận biết SV vắng nhiều, chăm sóc SV, không chỉ số liệu | Như thien; thêm “nhiều lý do vắng dẫn tới cấm thi” | **Thống nhất.** Báo cáo = danh sách hành động (ai cần chú ý, vì sao, làm gì), không phải biểu đồ | Chắc |
| G7 | Flow | Không nói cụ thể | “Setup môn học 1 flow; báo cáo trước, trong, sau điểm danh” | **Chỉ nhóm nhắc, cần kiểm.** “Setup môn học” mâu thuẫn với thực tế: GV không tạo lớp trên FAP, phòng Đào tạo tạo. Có thể ý thầy là cài đặt ban đầu (nhắc nhở, quy tắc). Xem P5, Q5 | Cần hỏi |
| G8 | Thứ tự quy trình | Mục tiêu → câu hỏi phỏng vấn → dữ liệu → persona → giải pháp → màn hình → flow → component + màu → wireframe → trạng thái → final UI → prototype | Style guide trước chỗ dựng Stitch | **Thống nhất**, và khớp đề (DESIGN.md trước Stitch). Xem P6 về chỗ đề và thầy khác nhau | Chắc |
| G9 | Mã màn hình | SC có nhiều trạng thái, cần ký hiệu phân biệt | Chưa phân cấp màn hình | **Thống nhất.** Hệ mã mới ở mục 6.4 | Chắc |
| G10 | Giao diện | Không đẹp, đổi sang hiện đại, shadcn, lucide, ít chữ | Phong cách hiện đại hơn | Đồng ý hướng, phản biện cách làm ở P3, P4 | Chắc |
| G11 | Điểm danh sai, thiếu | Không nhắc | “Có thể điểm danh sai hoặc thiếu”; kiểm tra thao tác nhầm | **Thien bỏ sót ý này.** Rubric Usability cũng chấm “error prevention and recovery”. Phải có cơ chế chống sai nhẹ thay cho đếm người (P2) | Chắc |
| G12 | Hiểu FAP | Không nhắc | “Chưa biết rõ UX FAP; AI chưa hiểu FAP” | **Thien bỏ sót ý này, và đây là nguyên nhân gốc R1.** Phải có quan sát FAP phía giảng viên (Q3) | Chắc |
| G13 | Cách trình bày | Không nhắc | Tập trung ý chính, không chuyển màn quá nhanh | Đưa vào kịch bản v2: ít slide hơn trên mỗi ý, demo chậm | Chắc |

---

## 3. Phản biện: chỗ tôi không đồng ý hoặc thấy rủi ro

**P1. “Đổi tên project thành archive” không nên áp cho repo GitHub.** Đề mục 8 bắt buộc repo tên `prm323-lab2-<student-id>` và chấm “Repository matches the structure; all links work”. Đổi tên repo làm link đã nộp chuyển hướng lung tung và mất điểm Documentation. Archive bằng tag và nhánh, giữ nguyên tên repo (mục 4).

**P2. Bỏ đếm sĩ số đúng, nhưng không được bỏ chống sai.** Thầy chê *thao tác* thừa, không chê *mục tiêu* đúng dữ liệu. Nhóm ghi “có thể điểm danh sai hoặc thiếu”, và rubric chấm error prevention. Đề xuất thay bằng cơ chế không tốn thêm bước:
- Danh sách điểm danh **ưu tiên ngoại lệ**: chỉ đẩy lên đầu những người chưa quét, kèm ảnh, để GV liếc là biết (dựa đúng vào trí nhớ khuôn mặt mà thầy nói).
- **Hoàn tác** sau khi chốt, và sửa được trong ngày.
- **Nhắc khi slot kết thúc mà chưa chốt** (gắn thẳng vào nỗi đau trừ lương).

**P3. Bảng màu FAP chỉ là một phần lý do “không đẹp”.** Trước khi đổ lỗi cho màu, hãy chạy Grayscale test trong checklist của bạn trên màn v1: nếu bản đen trắng vẫn rối, vấn đề là mật độ, thứ bậc và chữ, không phải màu. Tôi đoán phần lớn là vậy (Inferred, chưa chạy). Vì vậy v2 sửa theo thứ tự: bớt chữ → thứ bậc → khoảng trắng → rồi mới tới màu.

**P4. shadcn là thư viện web React, còn đề yêu cầu handoff Flutter.** Lấy shadcn làm *ngôn ngữ thị giác* (nền trung tính, một màu nhấn, viền mảnh, bo góc vừa, đổ bóng nhẹ) là hợp lý. Nhưng bảng component-to-widget phải ánh xạ sang Flutter: hoặc gói `shadcn_ui` trên pub.dev, hoặc Material 3 có theme lại. Thêm một xung đột: nút shadcn mặc định cao 36–40 px, đề yêu cầu vùng chạm ≥ 48 dp. Ta giữ phong cách shadcn nhưng kích thước theo chuẩn mobile. Lucide có gói Flutter `lucide_icons_flutter`, ổn.

**P5. “Thay một phần FAP” cần một giả định rõ về dữ liệu.** App lấy lịch, lớp, danh sách SV từ đâu, và kết quả điểm danh ghi về đâu? Bài lab không code nên có thể giả định “app đọc và ghi cùng dữ liệu với FAP”, nhưng phải ghi rõ là **Assumed** trong persona và handoff. Nếu không, thầy sẽ hỏi “dữ liệu ở đâu ra”. Tương tự, “setup môn học” chỉ hợp lý nếu là cài đặt cá nhân của GV, không phải tạo lớp.

**P6. Thứ tự của thầy và thứ tự trang Figma của đề khác nhau.** Đề cố định trang Figma: 01 User Flow, 02 Wireframe, 03 Final UI, 04 Design System, 05 Components, 06 Prototype. Thầy muốn trình bày component và màu *trước* wireframe. Cả hai đều đúng ở chỗ của nó: **làm việc** và **kể chuyện** theo thứ tự của thầy; **file Figma** giữ đúng 6 trang theo đề vì bị chấm. Slide v2 đi theo thứ tự của thầy và có bảng đối chiếu sang 12 mục của guideline để không sót bằng chứng (mục 9).

**P7. Thêm web sinh viên là mở rộng phạm vi.** Thầy muốn có, nhưng cũng nói “phần SV chỉ thao tác cần thiết”. Đề đếm “ít nhất 8 màn khác nhau” cho *ứng dụng mobile*. Đề xuất: **8–10 màn cho app GV là đủ điều kiện chấm**; web SV chỉ 3 màn, thiết kế ở khổ 360 dp (web trên điện thoại), đặt thành một section riêng trong trang 03. Không để web SV ăn thời gian của app GV.

**P8. Persona “quên điểm danh” không nên chỉ là đổi tên của persona chính.** Guideline cấm tách persona chỉ vì khác thuộc tính. Một persona phụ chỉ có giá trị nếu *hành vi* khác: ví dụ giảng viên thỉnh giảng hoặc dạy ít slot, không quen lịch FAP, hay quên vì không có thói quen; khác với giảng viên cơ hữu dạy dày, quen mặt SV, cần nhanh. Phỏng vấn sẽ quyết định có tách hay không.

**P9. Tài liệu v2 phải ngắn hơn v1 rất nhiều.** v1 có khoảng 52.000 chữ, người chấm không đọc hết. Đề xuất ngân sách: persona ≤ 1 trang A4 mỗi người (đúng guideline), mỗi tài liệu chính ≤ 1.500 chữ, bằng chứng và transcript đặt ở phụ lục.

---

## 4. Archive v1: đề xuất cơ chế (chưa làm, chờ thien đồng ý)

| Nơi | Cách làm | Đảo ngược được? |
|---|---|---|
| **GitHub repo** | (1) Gắn tag `v1-thuyet-trinh-2026-10-16` lên commit hiện tại của `main` (`b169725`). (2) Tạo nhánh `archive/v1` từ tag đó. (3) Trên `main`, xóa nội dung v1 bằng một commit, dựng khung thư mục mới theo đề. (4) README v2 có một dòng trỏ tới tag v1 và file `process/retro-v1.md` (bài học, khoảng 1 trang). **Giữ nguyên tên repo** | Có: lịch sử còn đủ, checkout tag là thấy lại v1 |
| **Figma** | Đổi tên file cũ thành `[ARCHIVE v1] PRM323 Lab 2 · SE190533`, giữ nguyên (còn lịch sử phiên bản). Tạo **file mới** cho v2. Đề có xem lịch sử phiên bản Figma, nên file v2 nên được tạo sớm và lưu dần, không dựng xong một lần | Có |
| **Thư mục dự án** (`/mnt/project-files/`) | Giữ nguyên `slides/` của v1. Mọi thứ mới nằm trong `lab2-v2/` | Có |
| **Slide** | Deck v2 đánh số lại từ `v2.0`, để khỏi lẫn với v2..v9 của bản cũ. Vẫn theo luật mỗi lần sửa một số mới | Có |

Cần thien quyết: file Figma v1 đang nằm ở tài khoản Figma Education **mượn của bạn** (D-30). File v2 nên tạo ở tài khoản nào (Q8)?

Tôi sẽ không xóa, đổi tên hay đẩy gì lên GitHub và Figma cho tới khi thien đồng ý mục này.

---

## 5. Quy trình v2: 7 giai đoạn, mỗi giai đoạn có cổng duyệt

Mỗi cổng (Gate) là một điểm dừng: thien (và nếu được, một thành viên khác) kiểm bằng checklist của cổng đó. Qua cổng mới sang giai đoạn sau. Đây là chỗ sửa lỗi “chỉ dựa vào AI review”.

| GĐ | Tên | Làm gì | Đầu ra (theo đề) | Cổng duyệt: phải trả lời “Có” |
|---|---|---|---|---|
| **0** | Khởi động | Archive v1; viết **mục tiêu sản phẩm** một câu và phạm vi; liệt kê giả định | `process/retro-v1.md`, `research/00-brief.md` | Mục tiêu nói được trong một câu, có ghi app *không* làm gì |
| **1** | Nghiên cứu thật | Câu hỏi nghiên cứu → bộ câu hỏi phỏng vấn → phỏng vấn **GVHD + 2–4 GV khác + 3–5 SV** → quan sát FAP phía GV (nhờ một GV chia sẻ màn hình hoặc chụp ảnh) → ghi chép ẩn danh có mã | `research/` (kế hoạch, ghi chép, ảnh FAP) | Mỗi câu hỏi nghiên cứu có ít nhất 2 người thật trả lời; có ảnh hoặc mô tả FAP phía GV do người thật cung cấp |
| **2** | Tổng hợp → Persona | Affinity board có mã nguồn → chọn phân khúc theo hành vi → persona 12 trường → problem statement → tiêu chí thành công đo được → bảng Persona → Nhu cầu → Ý tưởng → Cách kiểm chứng | `ux/persona.md` | Xóa một persona thì mất một quyết định thiết kế; mỗi trường có nhãn Observed / Reported / Inferred / Assumed |
| **3** | Giải pháp → Cấu trúc | Danh sách tính năng có truy vết về nhu cầu → cắt tính năng không có nguồn → hành trình trước / trong / sau buổi học → kiến trúc thông tin (màn, cấp, điều hướng) → 3+ flow (một flow lỗi, phục hồi) → bảng flow ↔ màn | `ux/user-flow.md`, `design/screen-spec.md` (bản ý đồ) | Mỗi màn thuộc ít nhất một flow; mọi tính năng có nguồn; không còn bước “đếm” |
| **4** | Style guide | Moodboard 3 hướng → chọn một → token màu, chữ, khoảng cách, bo góc, đổ bóng → luật component → **luật chữ trên màn hình** → kiểm tương phản | `design/DESIGN.md` | Viết xong **trước** prompt Stitch đầu tiên; mọi cặp màu chữ đạt 4,5:1 |
| **5** | AI sinh và phản biện | Prompt Stitch đầy đủ (người dùng, tác vụ, nền tảng, ràng buộc, phong cách từ DESIGN.md) → IT-0 → 3 vòng sửa, mỗi vòng một vấn đề có tên → AI critique ≥ 5 phát hiện theo Nielsen, accessibility, persona → bảng quyết định | `ai/ai-design-log.md`, `assets/stitch/` | Mỗi vòng có ảnh trước, sau; mọi gợi ý quan trọng có Accept / Modify / Reject kèm lý do dựa trên persona, heuristic hoặc ràng buộc |
| **6** | Figma | Token thành Variables → component có variant và trạng thái → wireframe → final UI kèm trạng thái cạnh màn → prototype 3 flow → kiểm 360 và 412 dp → chạy UI Simplicity Checklist + 3 bài test (5 giây, thang xám, cắt bớt) | 6 trang Figma đúng thứ tự, `assets/figma/`, `design/design-decisions.md` | Checklist ≥ 85/100 trên mọi màn chính; không còn câu giải thích trên UI; prototype không dead end |
| **7** | Kiểm chứng + bàn giao + trình bày | Thử prototype với 1–2 GV thật (đo tiêu chí thành công) → handoff Flutter → README → slide theo thứ tự tư duy → tập nói, demo chậm | `handoff/flutter-handoff.md`, `README.md`, slide | Một bạn cùng lớp dựng được một màn từ handoff mà không hỏi; mọi link mở được ở cửa sổ ẩn danh |

**Song song suốt quá trình:** commit đều mỗi ngày (đề chấm lịch sử Git trải nhiều ngày), lưu Figma theo từng bước, ghi log AI ngay khi dùng chứ không viết lại sau.

**Về checklist.design/mobile:** dùng ở GĐ 3 và GĐ 6, mỗi màn đối chiếu với trang checklist cùng loại (ví dụ màn lịch với checklist Calendar, màn rỗng với Empty state, đăng nhập với Login). Tôi chưa mở được trang này, nên cần thien chụp hoặc dán danh sách mục khi tới bước đó.

---

## 6. Định hướng sản phẩm ban đầu (proto, sẽ đổi sau nghiên cứu)

Phần này là **giả thuyết** để soạn câu hỏi phỏng vấn, không phải đáp án. Mọi dòng ở đây đều là Assumed cho tới GĐ 1.

### 6.1 Mục tiêu sản phẩm (nháp)

> Giúp giảng viên FPTU **không bao giờ quên điểm danh** và **biết sớm sinh viên nào cần được quan tâm**, trên một app điện thoại thay cho việc mở FAP để xem lịch, lớp và điểm danh.

### 6.2 Phân khúc người dùng (nháp, để phỏng vấn kiểm chứng)

| Mã | Phân khúc theo hành vi | Mức | Khác biệt cần thiết kế |
|---|---|---|---|
| P1 | Giảng viên dạy dày, quen mặt SV, ngày 3–4 slot | Primary | Cần nhanh, cần thấy hôm nay và slot kế tiếp, cần nhắc khi chưa chốt điểm danh |
| P2 | Giảng viên ít slot hoặc thỉnh giảng, không có thói quen mở FAP, dễ quên | Secondary (chờ dữ liệu) | Nhắc chủ động, lịch tuần rõ, ít thao tác lạ |
| P3 | Sinh viên đã vắng nhiều, có nguy cơ bị cấm thi | Secondary (web) | Biết mình còn vắng được mấy buổi; quét mã nhanh; báo sai |

### 6.3 Kiến trúc thông tin (nháp)

**App giảng viên (mobile):** thanh điều hướng dưới 4 tab.

| Cấp | Màn | Mục đích |
|---|---|---|
| L0 | **Tổng quan** | Slot hôm nay, slot chưa chốt điểm danh, SV cần chú ý |
| L0 | **Lịch** | Hôm nay, ngày mai, tuần (chuyển bằng segmented control) |
| L0 | **Lớp** | Danh sách lớp đang dạy |
| L0 | **Tài khoản** | Thông tin, cài đặt nhắc nhở, đăng xuất |
| L1 | Chi tiết buổi học | Thông tin slot, nút mở điểm danh |
| L1 | Phiên điểm danh | Mã QR cho SV quét; danh sách ưu tiên ngoại lệ; chốt |
| L1 | Chi tiết lớp | Danh sách SV, lịch sử điểm danh, SV cần chú ý của lớp |
| L2 | Hồ sơ sinh viên | Số buổi vắng / ngưỡng, lịch sử, hành động chăm sóc |
| L1 | Yêu cầu sửa điểm danh | Báo sai từ SV, duyệt hoặc từ chối |
| OV | Hộp thoại, bottom sheet | Xác nhận chốt, hoàn tác, lỗi mạng |

Đã có 9 màn L0–L2 khác nhau cho app GV, đủ điều kiện ≥ 8 màn.

**Web sinh viên (360 dp):** Quét mã → Kết quả; Buổi vắng của tôi (còn vắng được N buổi, cảnh báo); Gửi báo sai.

### 6.4 Hệ mã mới cho màn và trạng thái

Sửa đúng lỗi thầy chỉ: “SC-01 có nhiều trạng thái, làm sao phân biệt”.

```
<Kênh>-<Cấp><Số> · <Tên>  [<Trạng thái>]

Kênh:       GV = app giảng viên     SV = web sinh viên
Cấp:        0 = tab gốc   1 = màn con   2 = màn cháu   OV = lớp phủ (dialog, sheet)
Trạng thái: .D default   .L loading   .E empty   .X error   .S success
            Trạng thái nghiệp vụ thêm số: .D1 chưa mở, .D2 đang mở, .D3 đã chốt
```

Ví dụ: `GV-101 · Phiên điểm danh .D2` (đang mở), `GV-101 .X` (mất mạng), `GV-001 · Tổng quan .E` (hôm nay không có slot). Tên frame Figma, tên file ảnh trong `assets/figma/` và dòng trong `screen-spec.md` dùng **cùng một mã**, nên đồng bộ ba chiều Figma, repo, slide kiểm được bằng mắt. Trên slide chỉ hiện tên tiếng Việt và mã ngắn, không hiện chuỗi mã quyết định.

### 6.5 Ba flow chấm điểm (nháp)

| Flow | Persona | Bắt đầu → Mục tiêu → Kết thúc | Nhánh lỗi, phục hồi |
|---|---|---|---|
| FL-1 Điểm danh một slot | P1 | Nhận nhắc đầu slot → mở phiên → SV quét → liếc ngoại lệ → chốt | Mất mạng khi chốt → lưu tạm, gửi lại; chốt nhầm → hoàn tác |
| FL-2 Không để quên điểm danh | P1, P2 | Slot kết thúc chưa chốt → nhắc → mở từ Tổng quan → chốt muộn trong ngày | Đã qua hạn sửa → hướng dẫn đường chính thức |
| FL-3 Chăm sóc SV cần chú ý | P1 | Tổng quan báo 3 SV gần ngưỡng → hồ sơ SV → hành động (nhắc, ghi chú) | Không có SV nào cần chú ý → trạng thái rỗng |
| FL-4 (web SV, phụ) | P3 | Quét mã → kết quả → xem còn vắng được mấy buổi | Mã hết hạn → quét lại |

---

## 7. Định hướng giao diện

### 7.1 Luật chữ (áp cho mọi màn)

| Luật | Cách đo |
|---|---|
| Không có câu giải thích tính năng trên màn. Giải thích để ở chú thích Figma ngoài khung 360 × 800 | Rà từng frame: câu nào bắt đầu bằng “Bạn có thể…”, “Màn này…” thì xóa |
| Tiêu đề ≤ 4 từ, nhãn nút ≤ 3 từ | Đếm |
| Trạng thái bằng **icon + màu + một từ**, không bằng câu | Grayscale test vẫn đọc được |
| Ngân sách chữ ngoài dữ liệu: khoảng ≤ 25 từ mỗi màn (đề xuất, sẽ hiệu chỉnh khi dựng) | Đếm trên ảnh xuất |
| Số liệu là chữ chính: “3/4 vắng” to hơn mọi nhãn | Thứ bậc chữ trong DESIGN.md |

### 7.2 Phong cách: shadcn trên mobile

- Nền trung tính (thang zinc), **một màu nhấn duy nhất** cho hành động chính.
- Viền 1 dp, bo góc 12 dp cho thẻ và 10 dp cho nút, đổ bóng rất nhẹ chỉ cho lớp phủ.
- Icon Lucide nét 2, cỡ 20–24.
- Màu trạng thái chỉ dùng cho trạng thái (có mặt, vắng, chưa điểm danh), không dùng trang trí.
- Bố cục mobile: lề 16–20 dp, lưới 4 dp, hành động chính ở vùng ngón cái (nửa dưới màn), thanh điều hướng dưới, vùng chạm ≥ 48 dp. Sẽ nghiên cứu kỹ ở GĐ 4 từ Material 3 và Apple HIG, có trích nguồn.

### 7.3 Ba hướng màu để chọn ở GĐ 4

Số tương phản đã tính theo công thức WCAG, chữ trắng trên màu nhấn.

| Hướng | Nền / chữ | Màu nhấn | Tương phản | Nhận xét BA |
|---|---|---|---|---|
| **A · Zinc + Violet** (đề xuất) | `#FAFAFA` / `#18181B` | `#7C3AED` | 5,70:1 | Tách hẳn khỏi xanh dương của FAP; không đụng xanh lá (Có mặt), vàng (Chưa), đỏ (Vắng) nên màu trạng thái giữ được nghĩa |
| B · Slate + Teal | `#F8FAFC` / `#0F172A` | `#0F766E` | 5,47:1 | Dịu, chuyên nghiệp, nhưng teal gần xanh lá “Có mặt”, dễ lẫn nghĩa |
| C · Đơn sắc shadcn | `#FFFFFF` / `#09090B` | `#18181B` (nút đen) + cam `#C2410C` cho cảnh báo | 17,7:1 và 5,18:1 | Sang và tối giản nhất, nhưng dễ bị chê “nhạt” nếu làm không khéo |

Màu trạng thái chung cho cả ba: Có mặt `#15803D` (5,02:1), Chưa điểm danh `#B45309` (5,02:1), Vắng `#DC2626` (4,83:1), luôn kèm icon và chữ. Bản chốt phải qua moodboard và một màn thử trên Stitch, không chọn từ bảng này.

---

## 8. Nghiên cứu: kế hoạch phỏng vấn (nháp)

**Người cần gặp, theo thứ tự ưu tiên:**
1. **GVHD** (30 phút). Đây là nguồn insight bị bỏ lỡ ở v1, và là người chấm.
2. 2–4 giảng viên khác: ít nhất 1 cơ hữu dạy dày, 1 thỉnh giảng hoặc ít slot.
3. 3–5 sinh viên, ưu tiên người từng vắng nhiều hoặc suýt cấm thi.

Guideline gợi ý 6–12 người cho môn học; mục tiêu là khoảng 8.

**Câu hỏi nghiên cứu (cái ta muốn biết):**
- RQ1. Một ngày dạy của GV trôi qua thế nào, họ mở FAP lúc nào và để làm gì?
- RQ2. Khi nào GV quên điểm danh, hậu quả thật là gì (trừ lương thế nào, ai báo)?
- RQ3. GV hiện theo dõi SV vắng nhiều bằng cách nào, và họ làm gì khi phát hiện?
- RQ4. FAP phía GV có những màn nào, thao tác nào chậm hoặc dễ nhầm?
- RQ5. SV biết mình còn vắng được mấy buổi bằng cách nào?

**Câu hỏi phỏng vấn giảng viên (mẫu, hỏi về lần gần nhất, không hỏi ý kiến chung):**
1. Thầy/cô kể lại ngày dạy gần nhất, từ sáng tới lúc về.
2. Lần gần nhất thầy/cô điểm danh, thầy/cô làm những bước nào, trên thiết bị nào?
3. Đã bao giờ quên hoặc điểm danh trễ chưa? Lúc đó chuyện gì xảy ra, ai nhắc, hậu quả là gì?
4. Lần gần nhất thầy/cô biết một sinh viên vắng nhiều là khi nào? Thầy/cô biết bằng cách nào và đã làm gì?
5. Ngoài điểm danh, thầy/cô mở FAP để làm gì? Việc nào làm trên điện thoại?
6. Nếu chỉ được giữ ba việc trên điện thoại, thầy/cô giữ việc nào?
7. Thầy/cô có thể cho em xem (hoặc chụp, che tên SV) màn điểm danh và màn lịch trên FAP không?

**Câu hỏi phỏng vấn sinh viên (mẫu):**
1. Lần gần nhất bạn kiểm tra số buổi vắng là khi nào, vì sao?
2. Bạn có biết ngưỡng vắng của môn đang học không? Biết từ đâu?
3. Đã bao giờ bạn hoặc bạn bè suýt hoặc bị cấm thi vì vắng chưa? Chuyện gì xảy ra?
4. Bạn từng bị ghi sai điểm danh chưa? Bạn đã làm gì?

**Luật ghi chép:** mã người (GV-01, SV-01), ngày, nhãn Observed / Reported, không ghi họ tên thật. AI chỉ được tổng hợp từ ghi chép có mã, không được tự sinh câu trích hay số liệu (đúng prompt mẫu trong guideline).

---

## 9. Cấu trúc slide v2 (theo thứ tự tư duy, có đối chiếu guideline)

| # | Slide v2 | Nội dung | Bù cho mục guideline |
|---|---|---|---|
| 1 | Mục tiêu và vấn đề | App để làm gì, cho ai, giải quyết gì; link Figma, GitHub | 01 |
| 2 | Nghiên cứu | Câu hỏi nghiên cứu, ai đã phỏng vấn, 3 phát hiện chính kèm trích dẫn thật | 02 (căn cứ) |
| 3 | Persona | Primary + secondary, nỗi đau, problem statement, tiêu chí đo được | 02 |
| 4 | Giải pháp cho từng persona | Bảng Persona → Nhu cầu → Tính năng; tính năng đã **cắt** và vì sao (đếm sĩ số) | 07 (một phần) |
| 5 | Cấu trúc và màn hình | Kiến trúc thông tin, cấp màn, hệ mã | 03 |
| 6 | Ba flow | Trước, trong, sau buổi học; nhánh lỗi | 04 |
| 7 | Style guide | Màu, chữ, khoảng cách, luật chữ, component chính, **trước** AI | 05 (DESIGN.md), 09 |
| 8 | AI sinh và 3 vòng sửa | Prompt, IT-0, ba vấn đề có tên, critique | 05, 06 |
| 9 | Quyết định | 3–5 Accept / Modify / Reject có lý do | 07 |
| 10 | Wireframe → trạng thái → Final UI | Đặt cạnh nhau, trạng thái rỗng, tải, lỗi | 08 |
| 11 | Accessibility và prototype | Kiểm 360/412, tương phản; dẫn vào demo | 10, 11 |
| 12 | Bàn giao và bài học | Handoff, ánh xạ token, giới hạn | 12 |

Cần thien quyết: trình bày theo thứ tự này (đúng ý thầy), hay giữ đúng số thứ tự 12 slide của guideline (Q7). Tôi đề xuất theo thầy, vì thầy là người chấm và guideline ghi rõ thứ tự slide là “khuyến nghị”, không phải yêu cầu của đề.

---

## 10. Câu hỏi cần thien trả lời trước GĐ 1

| # | Câu hỏi | Vì sao cần | Mặc định nếu chưa trả lời |
|---|---|---|---|
| Q1 | Hạn nộp lại hoặc trình bày lại là khi nào? Thầy có chấm lại không, hay đây là để học? | Quyết định làm sâu tới đâu | Giả định còn khoảng 2 tuần |
| Q2 | “Không điểm danh bị trừ lương” là quy định thật thầy nói, hay suy diễn? Có văn bản không? | Nỗi đau chính của persona dựa vào đây | Ghi Reported (lời GVHD), cần xác minh |
| Q3 | Có hẹn được 30 phút phỏng vấn GVHD không? Có quen GV nào khác chịu cho xem FAP phía GV không? | Nguyên nhân gốc R1 | Soạn sẵn bộ câu hỏi, thien đi hẹn |
| Q4 | “Profile cảnh báo SV sắp hết slot” là trên web SV hay trong app GV? | Mâu thuẫn G2 | Làm cả hai mặt |
| Q5 | “Setup môn học 1 flow” thầy nói nghĩa là gì? | GV không tạo lớp trên FAP | Hiểu là cài đặt nhắc nhở cá nhân |
| Q6 | Còn làm nhóm 4 người không? Ai phỏng vấn, ai dựng Figma, ai làm slide? | Chia việc và lịch sử commit | thien làm chính, Claude hỗ trợ |
| Q7 | Slide theo thứ tự của thầy hay theo guideline? | P6, mục 9 | Theo thầy |
| Q8 | File Figma v2 tạo ở tài khoản nào? Vẫn dựng bằng Figma MCP chứ? | Lịch sử phiên bản bị xem xét; lượt gọi MCP | Tài khoản cũ, MCP như v1 |
| Q9 | Mã QR hiện ở đâu: trên điện thoại GV, máy chiếu, hay cả hai? | v1 dựa vào laptop + extension | Hiện trên điện thoại GV, chiếu được |
| Q10 | Đồng ý cơ chế archive ở mục 4 không? | Thao tác trên GitHub, Figma | Chưa làm gì cho tới khi có câu trả lời |

---

## 11. Rủi ro

| Rủi ro | Khả năng | Ảnh hưởng | Giảm thiểu |
|---|---|---|---|
| Không phỏng vấn được GV thật | Trung bình | Lặp lại lỗi v1 | Ít nhất GVHD; nếu không, ghi rõ Assumed và kiểm bằng buổi thử prototype |
| Web SV ăn thời gian | Cao | App GV nông | Giới hạn 3 màn, làm sau cùng |
| Phong cách mới đẹp nhưng sai chuẩn mobile (nút nhỏ, chữ xám nhạt) | Trung bình | Mất điểm Accessibility | Kiểm tương phản ngay ở DESIGN.md; vùng chạm 48 dp là token |
| Tài liệu lại phình to | Cao (thói quen v1) | Khó chấm, khó trình bày | Ngân sách chữ ở P9; mỗi cổng có kiểm độ dài |
| Lịch sử Git hoặc Figma trông như làm một lần | Trung bình | Bị nghi ngờ (đề mục 10) | Commit theo ngày, lưu Figma theo bước |

---

## 12. Cập nhật v0.2 (16/10, 23:20): theo câu trả lời của thien

### 12.1 Sự thật mới

| Câu hỏi | Trả lời của thien | Hệ quả |
|---|---|---|
| Q1 Hạn | **Thứ Ba 20/10/2026, 15:00** | Còn 3,5 ngày. Lịch ở 12.3 |
| Q2 Trừ lương | **Thầy nói thẳng** trong buổi thuyết trình | Nhãn **Reported (GVHD, 16/10)**. Thành nỗi đau chính của persona giảng viên |
| Q3 Phỏng vấn thầy | Không gặp, không nhắn được tới hạn | Xem 12.2 |
| Q10 Archive | Repo mới **trống**, cùng tên `prm323-lab2-SE190533`; repo cũ đổi tên thêm chữ archive | Thay mục 4. Xem 12.4 |

### 12.2 Nghiên cứu khi không gặp được thầy

Tôi vẫn phản biện một điểm: **“chỉ dùng dữ kiện có sẵn và giả định” là đủ cho phía giảng viên, nhưng chưa đủ cho phía sinh viên.** Sinh viên ở ngay quanh bạn.

| Nguồn | Nhãn | Dùng cho |
|---|---|---|
| **Góp ý của thầy trong buổi 16/10** (ghi nhớ của thien + bản tóm tắt nhóm). Đây là một buổi “phỏng vấn” thật với người dùng mục tiêu: một giảng viên FPTU nhiều năm điểm danh | Reported (GVHD-01, 16/10) | Toàn bộ persona giảng viên. Trên slide nói thẳng: “nguồn là phản hồi trực tiếp của giảng viên trong buổi review” |
| Quan sát của thien và nhóm khi là sinh viên ngồi trong lớp (đã thấy giảng viên điểm danh nhiều kỳ) | Observed (O-thien, O-nhóm) | Hành vi giảng viên nhìn từ phía lớp |
| **3–5 sinh viên thật** (4 thành viên nhóm + 1–2 bạn từng suýt cấm thi), phỏng vấn 10 phút, theo bộ câu hỏi ở mục 8 | Reported (SV-01..05) | Persona sinh viên, tính năng cảnh báo hết slot |
| Nghiên cứu bàn giấy v1 về quy định FPTU (ngưỡng vắng 20%, hạn sửa) | Desk | Ràng buộc |
| Mọi thứ còn lại về giảng viên | **Assumed**, kèm cách kiểm chứng | Ghi thẳng, không giấu |

**Không quay lại phỏng vấn mô phỏng bằng AI.** Đó là nguyên nhân gốc R1, và guideline ghi rõ persona do AI tạo không được coi là đã xác thực. Thà ít nguồn mà thật.

### 12.3 Lịch 3,5 ngày

| Ngày | Giai đoạn | Cổng cuối ngày |
|---|---|---|
| **Thứ Sáu 16/10 tối** | GĐ 0: repo mới, `process/retro-v1.md`, mục tiêu sản phẩm | thien duyệt mục tiêu 1 câu |
| **Thứ Bảy 17/10** | GĐ 1–3: phỏng vấn SV (sáng), evidence matrix, persona, IA, 3 flow | thien duyệt persona + IA |
| **Chủ Nhật 18/10** | GĐ 4–5: DESIGN.md, Stitch IT-0 + 3 vòng, AI critique, bảng quyết định | thien chọn hướng màu (sáng), duyệt quyết định (tối) |
| **Thứ Hai 19/10** | GĐ 6: Figma 6 trang, prototype 3 flow, kiểm 360/412, checklist UI | Checklist ≥ 85/100 |
| **Thứ Ba 20/10 sáng** | GĐ 7: handoff, README, slide, tập nói | Link mở ở cửa sổ ẩn danh trước 12:00 |

Đề chấm lịch sử Git trải nhiều ngày: lịch này cho commit đều 5 ngày liên tiếp.

### 12.4 Archive và repo mới

GitHub không cho tạo repo trùng tên, và công cụ GitHub của Claude **không có quyền đổi tên repo**. Thứ tự:

1. **thien** đổi tên repo cũ: GitHub → `prm323-lab2-SE190533` → Settings → General → Repository name → `prm323-lab2-SE190533-archive-v1` → Rename. (Đã làm 17/10; tên thực tế là `prm323-lab2-SE190533-archieve`.)
2. **thien** tạo repo mới trống (công cụ GitHub của Claude bị chặn quyền tạo repo), **Claude** đẩy khung lên. Repo mới: `prm323-lab2-SE190533` (public, vì người chấm phải mở được), dựng khung thư mục đúng đề mục 8, commit đầu tiên.
3. Claude vẫn đọc repo archive để lấy bài học và phần còn tốt (mục 1.2).

Lưu ý: sau khi tạo repo mới, link cũ `github.com/thiengthb/prm323-lab2-SE190533` sẽ trỏ vào repo mới (GitHub bỏ chuyển hướng về repo đã đổi tên). Mọi link trong slide v1 sẽ không còn mở ra bản cũ. Bản cũ chỉ còn ở tên `-archieve`.

### 12.5 Câu hỏi còn mở (giảm từ 10 xuống 5)

Q4 profile cảnh báo ở đâu, Q5 “setup môn học”, Q6 chia việc nhóm, Q8 tài khoản Figma, Q9 mã QR hiện ở đâu. Mặc định ở bảng mục 10 được dùng nếu thien chưa trả lời; không câu nào chặn việc tối nay.
