# Đặc tả màn hình (ý đồ thiết kế)

> v2.0 · 30/10/2026, khớp Final UI sau lượt duyệt cuối (luật chung ở [DESIGN.md](DESIGN.md) mục 7). Mỗi màn: để làm gì, hiện gì, hành động chính, thuộc flow nào. Mã màn và flow theo [user-flow.md](../ux/user-flow.md). Cách dựng ở [flutter-handoff.md](../handoff/flutter-handoff.md).
>
> **Dữ liệu:** lớp, lịch và danh sách sinh viên do giảng viên nhập từ file Excel/CSV phòng đào tạo gửi (GV-100); kết quả điểm danh, yêu cầu sửa và lời nhắc lưu trên Cloud Firestore. Dữ liệu mẫu trên Figma: giảng viên Nguyễn Minh Quân (quanm@fe.edu.vn), kỳ Fall 2026, 4 lớp PRM393 · SE1801 (35), PRM393 · SE1802 (34), MMA301 · SE1805 (30), PRN221 · SE1810 (32). Ngưỡng vắng: 20% số buổi (4/20).

## App giảng viên (Android, 360 × 800, kiểm 412)

| Mã | Màn | Để làm gì | Nội dung chính (trên → dưới) | Hành động chính | Flow | Trạng thái |
|---|---|---|---|---|---|---|
| GV-090 | Đăng nhập | Vào app | Logo + “Quick Attend” · Email · Mật khẩu · Quên mật khẩu? · “hoặc” | **Đăng nhập**; Đăng nhập với Google; link Đăng ký | FL-0 | .D · .X “Sai email hoặc mật khẩu” dưới ô mật khẩu |
| GV-091 | Đăng ký | Tạo tài khoản email trường | Họ tên · Email · Mật khẩu | **Tạo tài khoản**; Đăng ký với Google; link Đăng nhập | FL-0 | .D |
| GV-092 | Xác nhận email | Chắc email là của giảng viên | “Mã 6 số đã gửi tới …” · 6 ô số · “Gửi lại mã sau 28 giây” · Sai email? Sửa lại | **Xác nhận** | FL-0 | .D |
| GV-093 | Bắt đầu | Chỉ rõ việc phải làm trước khi điểm danh được | “Chào thầy Quân” · 3 bước B1 Nhập danh sách lớp, B2 App tự xếp lịch dạy, B3 Điểm danh từng slot | **Nhập lớp ngay**; Để sau | FL-0 | .D |
| GV-094 | Quên mật khẩu | Lấy lại quyền vào app | Ô Email | **Gửi link đặt lại**; Quay lại đăng nhập | FL-0 | .D · .S “Đã gửi link”, Về đăng nhập |
| GV-001 | Tổng quan | Trả lời “bây giờ tôi phải làm gì” trong 5 giây | Tiêu đề + icon đặc · dòng “Fall 2026” trái, “Thứ Ba, 20/10” phải · 4 ô số: lớp đang dạy, sinh viên, % có mặt tuần này, yêu cầu sửa (chạm mở GV-105) · thẻ slot đang diễn ra (nền cam, nút trắng **Điểm danh** + QR) · nhóm **Chú ý** (tam giác hổ phách, “Xem tất cả ›”) 2 hàng số 5/4 đỏ, 3/4 hổ phách | **Điểm danh** | FL-0, 1, 2, 3, 4b | .D · .D1 thẻ slot chưa chốt, nút **Chốt ngay** · .L khung xám · .E Chủ nhật, không thẻ slot · .E2 ô số “—”, ô trống “Chưa có lịch / Hãy nhập danh sách lớp” + **Nhập** · .X “Mất kết nối mạng” + **Thử lại** |
| GV-002 | Lịch | Xem lịch không cần FAP | Tab Hôm nay / Tuần / Tháng · dòng ngày · thẻ slot (icon trạng thái: tick xanh đã chốt, tam giác hổ phách chưa chốt, đồng hồ xám chỉ cho slot sắp tới gần nhất; thẻ đang diễn ra không icon) | Chạm thẻ → GV-101; **Điểm danh** / **Chốt ngay** trên thẻ | FL-1, FL-2 | .D1 Hôm nay · .D2 Tuần 19/10 – 25/10 (nhãn “Hôm nay”) · .D3 Tháng: lưới tháng + slot ngày chọn · .E “Lịch trống” · .E2 “Chưa có lịch” + **Nhập** |
| GV-003 | Lớp | Danh sách lớp kỳ đang xem | Chip kỳ (Fall 2026, Summer 2026, Spring 2026; kỳ cũ ẩn ▲) · thẻ lớp: môn · lớp · sĩ số · ô số hổ phách = số em cần chú ý | Chạm thẻ → GV-103 | FL-0b, FL-3 | .D · .D2 kỳ mới Spring 2027 đứng đầu · .E “Chưa có lớp” + **Nhập** |
| GV-004 | Tài khoản | Cài nhắc nhở, nhập lại lớp, đăng xuất | Avatar MQ · tên · email · nhóm Nhắc nhở (Trước slot · 10 phút; Slot chưa chốt · Khi hết giờ) · nhóm Dữ liệu (Nhập danh sách lớp · Lần cuối 20/10) | Đăng xuất | FL-0, FL-2 | .D · .C hộp thoại “Đăng xuất?” + email, Hủy / **Đăng xuất** |
| GV-100 | Nhập lớp | Tạo lớp, lịch, sinh viên từ file | .D: “File Excel hoặc CSV từ phòng đào tạo”, **Chọn file**, “.xlsx hoặc .csv, tối đa 5 MB”, Tải file mẫu · .D1: tên file, “Fall 2026 · 4 lớp · 12 slot mỗi tuần”, 4 hàng lớp | **Nhập** | FL-0, FL-0b | .D · .D1 · .L “Đã nhập 2/4 lớp”, nút **Đang xử lý** · .X “2 dòng lỗi, chưa nhập”: Dòng 12 Thiếu MSSV, Dòng 30 MSSV trùng; Bỏ qua / **Chọn file khác** · .S “Đã nhập 4 lớp · 12 slot tuần này” + 2 công tắc nhắc + **Tổng quan** |
| GV-101 | Chi tiết slot | Xem một slot, bắt đầu hoặc xem kết quả | Giờ · môn · lớp · ngày · phòng · sĩ số · (.D2/.D3) ô có mặt / vắng · (.D3) danh sách Vắng | **Điểm danh** | FL-1 | .D1 sắp tới · .D2 đang diễn ra, ô số “—” · .D3 đã chốt 34/1, hàng Lê Gia Huy, nút **Sửa** |
| GV-102 | Phiên điểm danh | Chốt nhanh, không đếm, chỉ xử lý ngoại lệ | Thẻ đếm “32/35” + thanh tiến độ hết chiều ngang thẻ · (.D1) QR “Còn 04:12”, chip “Đổi mã 12s” · (.D2) nút **Mở lại** · “Chưa quét (n)” rồi “Đã quét (n)”, mỗi hàng avatar · tên · MSSV · công tắc có mặt | **Chốt** (ghim đáy) | FL-1, FL-2 | .D1 mã đang mở · .D2 đóng mã, xem ngoại lệ (34/35 sau khi bật tay 2 em) · OV1 “Chốt điểm danh? 34 có mặt · 1 vắng”, Hủy / **Chốt** · .L “Đang xử lý” · .X GV-OV2 “Chưa gửi được · Mất mạng · đã lưu trên máy”, Để sau / **Thử lại** · .S kết quả như GV-101 .D3 + toast “Đã chốt” + Hoàn tác, nút **Xong** |
| GV-103 | Chi tiết lớp | Sức khỏe chuyên cần một lớp | Tiêu đề SE1801 · “PRM393 · Fall 2026” · 2 ô số: 35 sinh viên, 6/20 buổi đã học · tab Sinh viên / Buổi học | Chạm sinh viên → GV-201 | FL-3 | .D tab Sinh viên: ô tìm, hàng số vắng “5/4” … “0/4” · .D1 tab Buổi học: dòng ngày + “Slot 1 · P.305” + 34/35 |
| GV-104 | Chú ý | Ai sắp hoặc đã quá ngưỡng 20% | Ô tìm · chip Tất cả / Vượt / Sắp chạm / Lớp · hàng: avatar · tên · MSSV · lớp · số 5/4 đỏ, 3/4 hổ phách | Chạm hàng → GV-201 | FL-3 | .D · .E “Trống” |
| GV-105 | Yêu cầu sửa | Duyệt báo sai từ sinh viên | Thẻ: avatar · tên · chip Vắng · “PRM393 · Thứ Ba, 20/10 · Slot 1” · lời sinh viên trong ngoặc kép · Từ chối / **Duyệt** | **Duyệt** | FL-4b | .D 2 thẻ · .S toast “Đã duyệt” + Hoàn tác · .E “Trống” · OV5 sheet “Từ chối yêu cầu”: chip lý do Không có mặt / Quét sau giờ / Khác, ô Ghi thêm, **Gửi từ chối** |
| GV-201 | Hồ sơ sinh viên | Biết em vắng buổi nào và nhắc em | Avatar · tên · “SE190155 · PRM393 · SE1801” · số lớn “3/4 buổi vắng” · danh sách Buổi vắng (ngày, Slot 1 · P.305) | **Nhắc nhở** + chuông | FL-3 | .D 3/4 · .D1 5/4 + dòng “Sinh viên đã bị cấm thi” · .S nút **Đã nhắc** (chuông rung, tắt) + toast “Đã gửi” · OV3 sheet “Nhắc sinh viên”: nội dung soạn sẵn “Em đã vắng 3 buổi PRM393.”, người nhận email, **Gửi** |

## Web sinh viên (Flutter Web; điện thoại 360, laptop 1280)

Đầu trang điện thoại chỉ có logo + “Quick Attend”; avatar + tên + MSSV là dòng đầu nội dung. Laptop: avatar + tên ở góc phải đầu trang. Thanh địa chỉ `diemdanh.fpt.edu.vn` trên Figma là của trình duyệt, không dựng.

| Mã | Màn | Để làm gì | Nội dung chính | Hành động chính | Flow | Trạng thái |
|---|---|---|---|---|---|---|
| SV-090 | Đăng nhập | Biết đúng sinh viên | Logo · Email · Mật khẩu · Quên mật khẩu? | **Đăng nhập**; Google; link Đăng ký | FL-4 | .D |
| SV-091 | Đăng ký | Tạo tài khoản sinh viên | Họ tên · MSSV · Email · Mật khẩu | **Tạo tài khoản**; Google | FL-4 | .D |
| SV-001 | Buổi vắng của tôi | Biết còn được vắng mấy buổi | Avatar, tên, MSSV · băng cảnh báo hổ phách (nếu có) · “Fall 2026” trái, “Có mặt” phải · thẻ môn: mã môn, lớp, “7/10” (có mặt / đã học), mũi tên › | **Quét mã** (ghim đáy) cạnh Báo sai | FL-4, FL-5 | .D · .D1 “PRM393 còn 1 buổi được vắng” (số hổ phách) · .D2 “PRM393: vắng thêm 1 buổi là cấm thi” (số đỏ) · .W laptop: bảng Môn học / Có mặt / đã học kéo hết ngang, gợi ý chữ mờ “Quét mã trên điện thoại” ở chân |
| SV-002 | Chi tiết môn | Xem từng buổi có mặt hay vắng | “PRM393 · SE1801” · số lớn “7/10 buổi có mặt” · danh sách Buổi học: ngày, “Slot 1 · P.305”, chip Có mặt / Vắng | **Báo sai**; chạm buổi Vắng mở SV-102 | FL-4, FL-5 | .D · .W laptop |
| SV-101 | Quét mã | Điểm danh bằng camera | Khung camera · “Quét mã trên màn chiếu” · lớp đang quét | Quét | FL-4 | .D · .S “Đã ghi nhận · PRM393 · Slot 1 · 07:01”, **Xong** · .X “Mã đã hết hạn”, **Quét lại** · .X2 “Cần quyền camera · Trình duyệt đang chặn camera”, **Cho phép** |
| SV-102 | Gửi báo sai | Báo giảng viên khi bị ghi sai | Môn, ngày, slot, chip Vắng · chọn lý do (5 lựa chọn) · ô Ghi thêm | **Gửi** + máy bay giấy | FL-4 | .D · .S “Đã gửi”, **Xong** |

## Kiểm tra 412 dp

Section “Kiểm tra 412 dp” có GV-001 .D, GV-102 .D2, GV-104 .D, SV-001 .D1 ở bề rộng 412: nội dung co giãn, không tràn.
