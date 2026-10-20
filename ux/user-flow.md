# Kiến trúc thông tin và user flow

> **Trạng thái:** v0.2 (20/10/2026). “Setup” là bước nhập lớp và lịch từ FAP lúc dùng lần đầu (thien chốt 20/10, E-12). Mọi tính năng truy về E-xx trong [ma trận bằng chứng](../research/02-evidence-matrix.md).

## 1. Hệ mã màn hình

```
<Kênh>-<Cấp><Số> · <Tên> .<Trạng thái>
Kênh:       GV = app giảng viên   SV = web sinh viên
Cấp:        0 = tab gốc   1 = màn con   2 = màn cháu   OV = lớp phủ (dialog, sheet)
Trạng thái: .D mặc định  .L đang tải  .E rỗng  .X lỗi  .S thành công
            Trạng thái nghiệp vụ đánh số: .D1, .D2, ...
```

Tên frame Figma, ảnh trong `assets/figma/` và dòng trong `design/screen-spec.md` dùng cùng một mã. Ví dụ: `GV-102 · Phiên điểm danh .X` là màn phiên điểm danh khi mất mạng.

## 2. Kiến trúc thông tin

```mermaid
flowchart TD
    subgraph GV["App giảng viên · thanh điều hướng dưới"]
        T1["GV-001 · Tổng quan"]
        T2["GV-002 · Lịch"]
        T3["GV-003 · Lớp"]
        T4["GV-004 · Tài khoản"]
        T1 --> S101["GV-101 · Chi tiết slot"]
        T2 --> S101
        S101 --> S102["GV-102 · Phiên điểm danh"]
        T1 --> S104["GV-104 · Cần chú ý"]
        T1 --> S105["GV-105 · Yêu cầu sửa"]
        T3 --> S103["GV-103 · Chi tiết lớp"]
        S104 --> S201["GV-201 · Hồ sơ sinh viên"]
        S103 --> S201
        N(["Thông báo nhắc"]) -.-> S102
        S100["GV-100 · Thiết lập lần đầu: nhập từ FAP"] -->|"lần đầu"| T1
    end
    subgraph SV["Web sinh viên · 360 dp"]
        W1["SV-001 · Buổi vắng của tôi"]
        W1 --> W2["SV-101 · Quét mã"]
        W1 --> W3["SV-102 · Gửi báo sai"]
    end
    W3 -.->|"yêu cầu tới"| S105
```

## 3. Danh sách màn hình

11 màn khác nhau cho app giảng viên (đề yêu cầu ≥ 8), 3 màn cho web sinh viên.

| Mã | Tên | Cấp | Persona | Flow | Trạng thái | Nguồn |
|---|---|---|---|---|---|---|
| GV-001 | Tổng quan | 0 | P-01, P-02 | FL-1, FL-3 | .D, .D1 (có slot chưa chốt), .L, .E (hôm nay không dạy), .X | E-01, E-03, E-05, E-09 |
| GV-002 | Lịch | 0 | P-01, P-02 | FL-1, FL-2 | .D1 hôm nay, .D2 ngày mai, .D3 tuần, .E | E-03 |
| GV-003 | Lớp | 0 | P-01 | FL-3 | .D, .E | E-03 |
| GV-004 | Tài khoản | 0 | P-02 | FL-2 | .D | E-01 (cài nhắc) |
| GV-100 | Thiết lập lần đầu: nhập lớp, lịch từ FAP | 1 | P-02 | FL-2 | .D chọn lớp, .L đang nhập, .X nhập lỗi, .S xong | E-12 |
| GV-101 | Chi tiết slot | 1 | P-01, P-02 | FL-1, FL-2 | .D1 sắp tới, .D2 đang diễn ra, .D3 đã chốt | E-03 |
| GV-102 | Phiên điểm danh | 1 | P-01, P-02 | FL-1, FL-2 | .D1 mã đang mở, .D2 xem ngoại lệ, .L đang chốt, .X mất mạng, .S đã chốt | E-01, E-04, E-06 |
| GV-103 | Chi tiết lớp | 1 | P-01 | FL-3 | .D | E-03, E-05 |
| GV-104 | Cần chú ý | 1 | P-01 | FL-3 | .D, .E (không ai cần chú ý) | E-05, E-22 |
| GV-105 | Yêu cầu sửa | 1 | P-01 | FL-4 | .D, .E | E-06, E-20 |
| GV-201 | Hồ sơ sinh viên | 2 | P-01 | FL-3 | .D, .S (đã gửi nhắc) | E-05 |
| GV-OV1 | Hộp thoại xác nhận chốt | OV | P-01 | FL-1 | Xác nhận | E-06 |
| GV-OV2 | Hộp thoại lỗi mạng | OV | P-01 | FL-1 | Lỗi (biến thể destructive/error) | — |
| GV-OV3 | Sheet nhắc sinh viên | OV | P-01 | FL-3 | .D | E-05 |
| SV-001 | Buổi vắng của tôi | 0 | P-03 | FL-4 | .D, .D1 sắp chạm ngưỡng, .D2 đã chạm ngưỡng | E-21, E-22 |
| SV-101 | Quét mã | 1 | P-03 | FL-4 | .D camera, .S đã ghi nhận, .X mã hết hạn | E-20 |
| SV-102 | Gửi báo sai | 1 | P-03 | FL-4 | .D, .S đã gửi | E-20 |

**Đã cắt so với v1:** đếm sĩ số, đối chiếu sĩ số, kiểm tra ngẫu nhiên (E-04).

## 4. Flow

### FL-1 · Điểm danh một slot (P-01, K1)

Bắt đầu: slot đang diễn ra. Mục tiêu: chốt điểm danh đúng. Kết thúc: GV-102 .S.

```mermaid
flowchart TD
    A(["Bắt đầu: slot 1, 7:00"]) --> B["GV-001 · Tổng quan: thẻ slot đang diễn ra"]
    A -.->|"nhánh khác: từ lịch"| B2["GV-002 · Lịch .D1"]
    B2 --> C
    B --> C["GV-101 · Chi tiết slot .D2"]
    C --> D["GV-102 .D1 · Mở mã, lớp quét"]
    D --> E["GV-102 .D2 · Người chưa quét lên đầu, kèm ảnh"]
    E -->|"em có mặt mà chưa quét"| F["Đánh Có mặt bằng tay"]
    F --> G
    E --> G["GV-OV1 · Xác nhận chốt"]
    G --> H["GV-102 .L · Đang chốt"]
    H -->|"thành công"| I(["GV-102 .S · Đã chốt, có Hoàn tác"])
    H -->|"mất mạng"| X["GV-OV2 · Lỗi mạng"]
    X -->|"Thử lại"| H
    I -.->|"bấm Hoàn tác"| E
```

### FL-2 · Không để quên điểm danh (P-02, K2)

Bắt đầu: dùng app lần đầu. Mục tiêu: chốt slot trong ngày dù quên lúc đầu. Kết thúc: GV-102 .S.

```mermaid
flowchart TD
    A(["Bắt đầu: lần đầu dùng app"]) --> A1["GV-100 .D · Nhập lớp và lịch từ FAP"]
    A1 --> A2["GV-100 .L · Đang nhập"]
    A2 -->|"lỗi"| A3["GV-100 .X · Thử lại"] --> A2
    A2 --> A4["GV-100 .S · Đã nhập 4 lớp"]
    A4 --> B["GV-004 · Tài khoản: bật nhắc trước slot và khi slot hết"]
    B --> C["GV-002 · Lịch .D3 tuần"]
    C --> D{"Slot hết, chưa chốt?"}
    D -->|"Có"| E["Thông báo nhắc"]
    E --> F["GV-102 .D2 · Mở thẳng phiên"]
    F --> G(["GV-102 .S · Đã chốt"])
    D -->|"Bỏ qua thông báo"| H["GV-001 · Tổng quan: thẻ slot chưa chốt"]
    H --> I["GV-101 · Chi tiết slot .D2"]
    I --> F
```

### FL-3 · Chăm sóc sinh viên cần chú ý (P-01, K3)

Bắt đầu: Tổng quan. Mục tiêu: nhắc em sắp chạm ngưỡng vắng. Kết thúc: GV-201 .S.

```mermaid
flowchart TD
    A(["Bắt đầu: GV-001 · Tổng quan"]) --> B["GV-104 · Cần chú ý"]
    B -->|"không ai"| E(["GV-104 .E · Rỗng"])
    B --> C["GV-201 · Hồ sơ sinh viên: 3/4 buổi vắng được phép"]
    A -.->|"nhánh khác: theo lớp"| L["GV-003 · Lớp"] --> L2["GV-103 · Chi tiết lớp"] --> C
    C --> D["GV-OV3 · Nhắc sinh viên"]
    D --> F(["GV-201 .S · Đã gửi nhắc"])
```

### FL-4 · Sinh viên quét mã và báo sai (P-03, web)

Bắt đầu: SV-001. Mục tiêu: được ghi có mặt. Kết thúc: SV-101 .S hoặc GV-105 đã duyệt.

```mermaid
flowchart TD
    A(["Bắt đầu: SV-001 · Buổi vắng của tôi"]) --> B["SV-101 · Quét mã"]
    B -->|"thành công"| C(["SV-101 .S · Đã ghi nhận"])
    B -->|"mã hết hạn"| X["SV-101 .X"] -->|"Quét lại"| B
    A -->|"bị ghi sai"| D["SV-102 · Gửi báo sai"] --> E["SV-102 .S"]
    E -.-> F["GV-105 · Yêu cầu sửa (giảng viên duyệt)"]
    F --> G(["SV-001 · Cập nhật Có mặt"])
```

## 5. Bảng flow ↔ màn

| Flow | Persona | Màn |
|---|---|---|
| FL-1 | P-01 | GV-001, GV-002, GV-101, GV-102, GV-OV1, GV-OV2 |
| FL-2 | P-02 | GV-100, GV-004, GV-002, GV-001, GV-101, GV-102 |
| FL-3 | P-01 | GV-001, GV-104, GV-003, GV-103, GV-201, GV-OV3 |
| FL-4 | P-03, P-01 | SV-001, SV-101, SV-102, GV-105 |

Mọi màn đều thuộc ít nhất một flow. FL-1, FL-2 và FL-4 có nhánh lỗi, phục hồi.
