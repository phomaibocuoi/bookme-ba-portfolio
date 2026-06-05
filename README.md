# BookMe – Dự Án Phân Tích Nghiệp Vụ Cá Nhân

[![Xem Interactive Prototype](https://img.shields.io/badge/Figma%20%2F%20Stitch-Interactive%20Prototype-E18E96?style=for-the-badge&logo=figma)](https://stitch.withgoogle.com/preview/8269607224269675093?node-id=54221aeaf2c5410097d05367014205d9)
Đây là dự án cá nhân tự thực hiện để luyện tập toàn bộ quy trình phân tích nghiệp vụ của một IT Business Analyst — từ xác định vấn đề, thu thập yêu cầu, viết tài liệu đặc tả, đến thiết kế sơ đồ hệ thống và xây dựng kịch bản kiểm thử.

Dự án được xây dựng từ một vấn đề thực tế quan sát được: nhiều salon, spa và cơ sở làm đẹp nhỏ vẫn quản lý lịch hẹn qua Zalo hoặc điện thoại, dẫn đến khó kiểm soát lịch, thiếu cơ chế nhắc hẹn tự động và tỷ lệ khách bỏ hẹn cao.

---

## Giới thiệu

**BookMe** là nền tảng đặt lịch trực tuyến kết nối khách hàng với các cơ sở dịch vụ làm đẹp và chăm sóc sức khỏe (salon, spa, nail, phòng khám). Hệ thống cho phép khách đặt lịch 24/7, nhận nhắc lịch tự động qua Email/SMS và giúp cơ sở quản lý toàn bộ lịch hẹn tập trung trên một nền tảng.

Phạm vi phân tích: **Phase 1 – MVP**, nền tảng web responsive.

**Luồng đặt lịch chính:**
Khách tìm cơ sở → chọn dịch vụ & nhân viên → chọn khung giờ (hệ thống giữ slot 10 phút) → xác nhận → nhận Email/SMS xác nhận → Partner duyệt lịch → nhắc lịch tự động trước 24h và 2h → check-in → hoàn thành.

**Booking status flow:** `Pending` → `Confirmed` → `Checked-in` → `Completed` (hoặc `Cancelled` / `No-show`)

---

## Cấu trúc thư mục

```text
bookme-ba-portfolio/
├── specifications/             # Tài liệu đặc tả chi tiết
│   ├── BookMe-BRD-v1.0.pdf                 # Business Requirements Document (Yêu cầu nghiệp vụ)
│   └── BookMe-SRS-v1.0.pdf                 # Software Requirements Specification (Đặc tả phần mềm)
├── diagrams/                   # Sơ đồ thiết kế hệ thống
│   └── BookMe-System-Diagrams-v1.0.pdf     # File tổng hợp Use Case, Activity, ERD
├── wireframes/                 # Bản vẽ thiết kế giao diện (UI Mockups)
│   ├── BookMe-Figma-Prototype-Spec.txt     # Đặc tả liên kết & logic prototype
│   ├── C3-Trang-chu-Discovery.png          # Giao diện Trang chủ & Bộ lọc Tìm kiếm
│   ├── C4-Chi-tiet-Co-so.png               # Giao diện Trang chi tiết cơ sở
│   ├── C5-Chon-Thoi-gian-Nhan-vien.png     # Giao diện Form đặt lịch hẹn từng bước (Wizard)
│   ├── P1-Partner-Dashboard.png            # Giao diện Bảng điều khiển quản lý của Đối tác
│   └── ... (22 màn hình UI Mockups chi tiết từ Khách hàng, Đối tác đến Admin)
├── test-plans/                 # Tài liệu kiểm thử & Nghiệm thu
│   └── BookMe-RTM-UAT-Test-Cases-v1.0.xlsx   # Ma trận vết (RTM) & Kịch bản kiểm thử UAT
└── README.md                   # Hướng dẫn và tổng quan dự án (File này)
```

---

## Tài liệu trong dự án

### 1. BRD – Business Requirements Document
Xác định vấn đề nghiệp vụ, mục tiêu kinh doanh, phân tích stakeholder, quy trình As-Is / To-Be, 8 Business Requirements, 15 Business Rules và tiêu chí nghiệm thu ở cấp độ nghiệp vụ.

### 2. SRS – Software Requirements Specification
Đặc tả 28 Functional Requirements cho 3 nhóm người dùng (Customer, Partner, Admin), Non-Functional Requirements (Performance, Security, Scalability, Availability, Usability), đặc tả chi tiết 5 Use Cases và quản lý trạng thái booking.

### 3. Sơ đồ hệ thống
Gồm 3 sơ đồ trong một file PDF:
- **Use Case Diagram** – 18 UC, 4 primary actors, 3 secondary actors
- **Activity Diagram** – luồng đặt lịch UC-05 với 4 swimlanes, 2 decision points, luồng lỗi
- **ERD** – 8 entities, chuẩn hóa 3NF, đánh dấu PK/FK rõ ràng

### 4. Wireframe – Interactive Prototype
Hệ thống gồm 22 màn hình UI Mockups từ Customer, Partner, Staff đến Admin, mô phỏng luồng tương tác người dùng thực tế. Trong đó tập trung vào 4 màn hình cốt lõi: Trang chủ & tìm kiếm, Chi tiết cơ sở, Form đặt lịch hẹn từng bước (Wizard), và Partner Dashboard.

[Xem prototype tương tác](https://stitch.withgoogle.com/preview/8269607224269675093?node-id=54221aeaf2c5410097d05367014205d9)

### 5. RTM & UAT Test Cases
Ma trận vết tracing từ Business Requirements → Functional Requirements → Use Case → Test Case. Gồm 11 test cases UAT cho các tính năng cốt lõi, phân vai Tester Role rõ ràng (Customer / Partner / Staff / Admin).

---

## Stakeholders & Actors

| Role | Loại | Mô tả |
|------|------|-------|
| Customer | Primary | Tìm kiếm, đặt, hủy lịch hẹn |
| Partner | Primary | Quản lý cơ sở, duyệt lịch, xem báo cáo |
| Staff | Primary | Xem lịch cá nhân, check-in, cập nhật trạng thái |
| Admin | Primary | Duyệt Partner, quản lý danh mục, xử lý khiếu nại |
| Email/SMS System | Secondary | Gửi xác nhận và nhắc lịch tự động |
| Google OAuth | Secondary | Xác thực đăng nhập |

---

## Business Rules nổi bật

- **BUS-01** – Một nhân viên không thể có 2 booking trùng khung giờ
- **BUS-02** – Chỉ được đặt lịch trước giờ hẹn tối thiểu 30 phút
- **BUS-03** – Chỉ được hủy lịch trước giờ hẹn tối thiểu 2 giờ
- **BUS-08** – Booking phải tuân theo đúng luồng trạng thái, không nhảy cóc
- **BUS-14** – Tài khoản Partner chỉ được hoạt động sau khi Admin phê duyệt
- **BUS-15** – Mọi thao tác tạo/cập nhật/hủy booking đều được ghi audit log

---

## Công cụ sử dụng

| Công cụ | Mục đích |
|---------|---------|
| Google Docs | Soạn thảo BRD, SRS |
| Google Stitch (Figma) | Thiết kế wireframe và interactive prototype |
| draw.io | Vẽ Use Case Diagram, Activity Diagram, ERD |
| Excel | RTM và UAT Test Cases |

---

## Thông tin tác giả

**Hồ Khổng Tuyết Như**
IT Business Analyst

- Email: hokhongtuyetnhu0807@gmail.com
- LinkedIn: [linkedin.com/in/hokhongtuyetnhu](https://linkedin.com/in/hokhongtuyetnhu)

---

*Dự án này được thực hiện độc lập phục vụ mục đích học tập và ứng tuyển vị trí IT Business Analyst. Mọi thông tin, tên công ty và dữ liệu trong tài liệu mang tính giả định.*