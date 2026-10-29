# Đặc tả màn hình (ý đồ thiết kế)

> v1.4 · 29/10 tối: Google ở GV-A01/A02, GV-A04, GV-A05, GV-001 .E2/.N giữ 4 ô số trống + thẻ Chưa có lịch, GV-002 .E2, GV-100 có app bar. v1.3 · 29/10/2026: thêm GV-A01..A03, SV-000, GV-001 .E2/.N, GV-003 .D2 (vòng đời, D-16..D-18). v1.2 · 22/10/2026 (v1.1 thêm GV-001 .D1 theo A2; v1.2 thêm GV-OV4 thông báo nhắc chốt, tiến độ slot trong ngày ở GV-001, đồng hồ đổi mã ở GV-102 .D1, thanh địa chỉ ở web SV-*). Mỗi màn: để làm gì, hiện gì, hành động chính, thuộc flow nào. Mã màn và trạng thái theo [user-flow.md](../ux/user-flow.md) mục 1. Cách dựng chi tiết ở [flutter-handoff.md](../handoff/flutter-handoff.md).

## App giảng viên

| Mã | Màn | Để làm gì | Nội dung chính (trên → dưới) | Hành động chính | Flow | Trạng thái |
|---|---|---|---|---|---|---|
| GV-A01 | Đăng nhập | Vào app trên máy mới | App icon + “Đăng nhập” · Email · Mật khẩu · Quên mật khẩu? | **Đăng nhập**; link Đăng ký | FL-0 | .D · .X sai mật khẩu |
| GV-A02 | Đăng ký | Tạo tài khoản bằng email trường (D-16) | App icon + “Đăng ký” · “Dùng email @fe.edu.vn” · Họ tên · Email · Mật khẩu | **Tạo tài khoản**; link Đăng nhập | FL-0 | .D · .X email không phải @fe.edu.vn |
| GV-A03 | Xác nhận email | Chắc email là của giảng viên | “Mã 6 số đã gửi tới …” · 6 ô · gửi lại sau 28 giây | **Xác nhận** | FL-0 | .D |
| GV-A04 | Bắt đầu | Sau đăng ký, chỉ rõ việc phải làm trước khi điểm danh được (D-21) | “Chào thầy Quân” · 3 bước: Nhập danh sách lớp (đang chọn) · Lịch dạy tự có · Điểm danh mỗi slot | **Nhập lớp ngay**; Để sau → Tổng quan .E2 | FL-0 | .D |
| GV-A05 | Quên mật khẩu | Lấy lại quyền vào app | Ô Email · nút gửi link | **Gửi link đặt lại**; Quay lại đăng nhập | FL-0 | .D · .S đã gửi link |
| GV-100 | Thiết lập lần đầu | Lấy lớp và lịch từ FAP để không phải nhập tay (E-12) | Icon tải về · tiêu đề “Nhập từ FAP” · danh sách lớp kỳ này có ô chọn (.X giữ nguyên tiêu đề, lỗi nằm giữa phần còn lại) | **Nhập 4 lớp** | FL-2 | .D chọn lớp · .L đang nhập · .X nhập lỗi · .S xong |
| GV-001 | Tổng quan | Trả lời “bây giờ tôi phải làm gì” trong 5 giây (E-01, E-05) | App bar top-level + chuông · ngày + **“1/3 slot đã chốt” và thanh 3 đoạn** (mỗi đoạn một slot: đã chốt xanh, chưa chốt hổ phách, đang diễn ra đen, sắp tới xám) · thẻ slot đang diễn ra · thẻ slot chưa chốt (nếu có) · “Cần chú ý” 2–3 hàng · các slot còn lại hôm nay | **Mở điểm danh** trên thẻ slot đang diễn ra | FL-1, FL-2, FL-3 | .D · .D1 có slot chưa chốt (thẻ **Chốt ngay** lên đầu) · .L skeleton · .E hôm nay không dạy · .X mất mạng |
| GV-002 | Lịch | Xem hôm nay, ngày mai, tuần mà không mở FAP (E-03) | Segmented Hôm nay / Ngày mai / Tuần · nhóm theo ngày · thẻ slot | Chạm thẻ slot | FL-1, FL-2 | .D1 hôm nay · .D2 ngày mai · .D3 tuần · .E không có slot |
| GV-003 | Lớp | Danh sách lớp đang dạy kỳ này | Hàng lớp: môn · lớp · sĩ số · số em cần chú ý | Chạm hàng lớp | FL-3 | .D · .E chưa nhập lớp |
| GV-004 | Tài khoản | Cài nhắc nhở để không quên (P-02) | Thẻ giảng viên · nhóm Nhắc nhở (2 công tắc) · Nhập lại từ FAP · Đăng xuất | Bật công tắc nhắc | FL-2 | .D |
| GV-101 | Chi tiết slot | Xem một slot và bắt đầu điểm danh | Giờ · môn · lớp · phòng · chip trạng thái · sĩ số lớp | **Mở điểm danh** (cố định đáy) hoặc **Chốt ngay** nếu chưa chốt | FL-1, FL-2 | .D1 sắp tới (nút tắt) · .D2 đang diễn ra · .D3 đã chốt (nút Sửa điểm danh, trong ngày) |
| GV-102 | Phiên điểm danh | Chốt điểm danh nhanh, **không đếm** (E-04), chỉ xử lý ngoại lệ (E-06) | Thẻ QR + chip “Đổi mã sau 12s” + bộ đếm tự động (.D1 “31/35 đã quét”, .D2 “32/35”) · “Chưa quét (3)” với hàng có ảnh và 2 nút ✓ ✕ | **Chốt điểm danh** (cố định đáy) | FL-1, FL-2 | .D1 mã đang mở · .D2 xem ngoại lệ · .L đang chốt · .X mất mạng (GV-OV2) · .S đã chốt + snackbar Hoàn tác |
| GV-103 | Chi tiết lớp | Nhìn sức khỏe chuyên cần của một lớp | Dòng số liệu: sĩ số · buổi đã học · số em cần chú ý · danh sách cần chú ý · các buổi gần nhất | Chạm hàng sinh viên | FL-3 | .D |
| GV-104 | Cần chú ý | Danh sách hành động: ai sắp hoặc đã chạm ngưỡng 20% (E-05, E-22) | Hàng: ảnh · tên · lớp · chip mức · số “3/4” | Chạm hàng → hồ sơ | FL-3 | .D · .E không ai cần chú ý |
| GV-105 | Yêu cầu sửa | Duyệt báo sai từ sinh viên trong ngày (E-06, E-20) | Thẻ yêu cầu: sinh viên · slot · lý do · Duyệt / Từ chối | **Duyệt** | FL-4 | .D · .E không có yêu cầu |
| GV-201 | Hồ sơ sinh viên | Biết em này vắng những buổi nào và nhắc em (E-05) | Ảnh · tên · mã · lớp · số lớn “3/4 buổi vắng” + chip · lịch sử buổi vắng | **Nhắc sinh viên** | FL-3 | .D · .S đã gửi nhắc |
| GV-OV1 | Hộp thoại xác nhận chốt | Chặn chốt nhầm (heuristic 5) | “Chốt điểm danh?” · “34 có mặt · 1 vắng” | **Chốt** | FL-1 | Confirmation |
| GV-OV2 | Hộp thoại lỗi mạng | Phục hồi khi gửi thất bại (heuristic 9) | “Chưa gửi được” · “Mất mạng · đã lưu trên máy” (kết quả giữ trên máy) | **Thử lại** (phụ: Để sau) | FL-1 | Destructive/error |
| GV-OV3 | Sheet nhắc sinh viên | Gửi lời nhắc ngắn có sẵn | Mẫu tin nhắn ngắn · kênh gửi | **Gửi** | FL-3 | .D |
| GV-OV4 | Thông báo nhắc chốt | Kéo giảng viên quay lại chốt khi slot hết giờ mà chưa chốt, trước khi bị trừ lương (E-01, E-09) | Thông báo trên màn khoá: “PRM393 · SE1801 chưa chốt”, “Slot 1 đã hết giờ” | **Chốt ngay** → GV-102 .D2 | FL-2 | .D |

## Web sinh viên (khổ 360)

| Mã | Màn | Để làm gì | Nội dung chính | Hành động chính | Flow | Trạng thái |
|---|---|---|---|---|---|---|
| SV-000 | Đăng nhập | Biết đúng sinh viên trước khi xem buổi vắng, quét mã | App icon · “Quick Attend” · một dòng phụ | **Đăng nhập tài khoản FPT** | FL-4 | .D |
| SV-001 | Buổi vắng của tôi | Biết còn được vắng mấy buổi mà không phải tự tra (E-25, E-26) | Băng cảnh báo môn sắp chạm ngưỡng · hàng môn: mã môn · “3/4” · chip | **Quét mã** (cố định đáy) | FL-4 | .D · .D1 sắp chạm ngưỡng · .D2 đã chạm ngưỡng |
| SV-101 | Quét mã | Điểm danh bằng camera | Khung camera · kết quả ngay trên màn | Quét | FL-4 | .D camera · .S “Đã ghi nhận 07:01” + dòng còn vắng được N buổi · .X mã hết hạn → Quét lại |
| SV-102 | Gửi báo sai | Báo giảng viên trong ngày khi bị ghi sai | Slot đang ghi Vắng · ô lý do | **Gửi** | FL-4 | .D · .S đã gửi |

Màn SV-* là web mở trên trình duyệt điện thoại: khung Figma có thanh địa chỉ `diemdanh.fpt.edu.vn` (component Browser bar) để phân biệt với app giảng viên (D-08). Thanh này là của trình duyệt, lập trình viên không dựng.
