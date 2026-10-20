# Đặc tả màn hình (ý đồ thiết kế)

> v1.1 · 20/10/2026 (thêm GV-001 .D1 theo phản biện IT-0, A2). Mỗi màn: để làm gì, hiện gì, hành động chính, thuộc flow nào. Mã màn và trạng thái theo [user-flow.md](../ux/user-flow.md) mục 1. Cách dựng chi tiết ở [flutter-handoff.md](../handoff/flutter-handoff.md).

## App giảng viên

| Mã | Màn | Để làm gì | Nội dung chính (trên → dưới) | Hành động chính | Flow | Trạng thái |
|---|---|---|---|---|---|---|
| GV-100 | Thiết lập lần đầu | Lấy lớp và lịch từ FAP để không phải nhập tay (E-12) | Icon tải về · tiêu đề “Nhập từ FAP” · danh sách lớp kỳ này có ô chọn | **Nhập 4 lớp** | FL-2 | .D chọn lớp · .L đang nhập · .X nhập lỗi · .S xong |
| GV-001 | Tổng quan | Trả lời “bây giờ tôi phải làm gì” trong 5 giây (E-01, E-05) | App bar top-level + chuông · thẻ slot đang diễn ra · thẻ slot chưa chốt (nếu có) · “Cần chú ý” 2–3 hàng · các slot còn lại hôm nay | **Mở điểm danh** trên thẻ slot đang diễn ra | FL-1, FL-2, FL-3 | .D · .D1 có slot chưa chốt (thẻ **Chốt ngay** lên đầu) · .L skeleton · .E hôm nay không dạy · .X mất mạng |
| GV-002 | Lịch | Xem hôm nay, ngày mai, tuần mà không mở FAP (E-03) | Segmented Hôm nay / Ngày mai / Tuần · nhóm theo ngày · thẻ slot | Chạm thẻ slot | FL-1, FL-2 | .D1 hôm nay · .D2 ngày mai · .D3 tuần · .E không có slot |
| GV-003 | Lớp | Danh sách lớp đang dạy kỳ này | Hàng lớp: môn · lớp · sĩ số · số em cần chú ý | Chạm hàng lớp | FL-3 | .D · .E chưa nhập lớp |
| GV-004 | Tài khoản | Cài nhắc nhở để không quên (P-02) | Thẻ giảng viên · nhóm Nhắc nhở (2 công tắc) · Nhập lại từ FAP · Đăng xuất | Bật công tắc nhắc | FL-2 | .D |
| GV-101 | Chi tiết slot | Xem một slot và bắt đầu điểm danh | Giờ · môn · lớp · phòng · chip trạng thái · sĩ số lớp | **Mở điểm danh** (cố định đáy) hoặc **Chốt ngay** nếu chưa chốt | FL-1, FL-2 | .D1 sắp tới (nút tắt) · .D2 đang diễn ra · .D3 đã chốt (nút Sửa điểm danh, trong ngày) |
| GV-102 | Phiên điểm danh | Chốt điểm danh nhanh, **không đếm** (E-04), chỉ xử lý ngoại lệ (E-06) | Thẻ QR + “32/35 đã quét” (đếm tự động) · “Chưa quét (3)” với hàng có ảnh và 2 nút ✓ ✕ | **Chốt điểm danh** (cố định đáy) | FL-1, FL-2 | .D1 mã đang mở · .D2 xem ngoại lệ · .L đang chốt · .X mất mạng (GV-OV2) · .S đã chốt + snackbar Hoàn tác |
| GV-103 | Chi tiết lớp | Nhìn sức khỏe chuyên cần của một lớp | Dòng số liệu: sĩ số · buổi đã học · số em cần chú ý · danh sách cần chú ý · các buổi gần nhất | Chạm hàng sinh viên | FL-3 | .D |
| GV-104 | Cần chú ý | Danh sách hành động: ai sắp hoặc đã chạm ngưỡng 20% (E-05, E-22) | Hàng: ảnh · tên · lớp · chip mức · số “3/4” | Chạm hàng → hồ sơ | FL-3 | .D · .E không ai cần chú ý |
| GV-105 | Yêu cầu sửa | Duyệt báo sai từ sinh viên trong ngày (E-06, E-20) | Thẻ yêu cầu: sinh viên · slot · lý do · Duyệt / Từ chối | **Duyệt** | FL-4 | .D · .E không có yêu cầu |
| GV-201 | Hồ sơ sinh viên | Biết em này vắng những buổi nào và nhắc em (E-05) | Ảnh · tên · mã · lớp · số lớn “3/4 buổi vắng” + chip · lịch sử buổi vắng | **Nhắc sinh viên** | FL-3 | .D · .S đã gửi nhắc |
| GV-OV1 | Hộp thoại xác nhận chốt | Chặn chốt nhầm (heuristic 5) | “Chốt điểm danh?” · “34 có mặt · 1 vắng” | **Chốt** | FL-1 | Confirmation |
| GV-OV2 | Hộp thoại lỗi mạng | Phục hồi khi gửi thất bại (heuristic 9) | “Không gửi được” · “Mất kết nối mạng” · kết quả được giữ trên máy | **Thử lại** | FL-1 | Destructive/error |
| GV-OV3 | Sheet nhắc sinh viên | Gửi lời nhắc ngắn có sẵn | Mẫu tin nhắn ngắn · kênh gửi | **Gửi** | FL-3 | .D |

## Web sinh viên (khổ 360)

| Mã | Màn | Để làm gì | Nội dung chính | Hành động chính | Flow | Trạng thái |
|---|---|---|---|---|---|---|
| SV-001 | Buổi vắng của tôi | Biết còn được vắng mấy buổi mà không phải tự tra (E-25, E-26) | Băng cảnh báo môn sắp chạm ngưỡng · hàng môn: mã môn · “3/4” · chip | **Quét mã** (cố định đáy) | FL-4 | .D · .D1 sắp chạm ngưỡng · .D2 đã chạm ngưỡng |
| SV-101 | Quét mã | Điểm danh bằng camera | Khung camera · kết quả ngay trên màn | Quét | FL-4 | .D camera · .S “Đã ghi nhận 07:01” + dòng còn vắng được N buổi · .X mã hết hạn → Quét lại |
| SV-102 | Gửi báo sai | Báo giảng viên trong ngày khi bị ghi sai | Slot đang ghi Vắng · ô lý do | **Gửi** | FL-4 | .D · .S đã gửi |
