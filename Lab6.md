
# Phân Tích Thiết Kế Hệ Thống **Payroll System**

## 1. Phân Tích Các Lớp Và Mối Quan Hệ

### 1.1. Subsystem: User Management
- **Lớp chính:**
  - `User`: Đại diện người dùng với thông tin đăng nhập và quyền.
  - `UserProfile`: Chứa thông tin cá nhân của người dùng.
  - `AuthenticationManager`: Xử lý xác thực và phân quyền.
- **Quan hệ:**
  - `User` liên kết 1-1 với `UserProfile`.
  - `AuthenticationManager` sử dụng `User` để xác thực thông tin đăng nhập và kiểm tra quyền.

---

### 1.2. Subsystem: Payroll Processing
- **Lớp chính:**
  - `PayrollRecord`: Chứa thông tin về lương (lương cơ bản, thưởng, khấu trừ, tổng lương).
  - `PayrollCalculator`: Tính toán lương dựa trên thời gian làm việc.
  - `PayrollManager`: Quản lý việc tạo và cập nhật bảng lương.
- **Quan hệ:**
  - `PayrollCalculator` tạo ra các đối tượng `PayrollRecord`.
  - `PayrollManager` quản lý và cập nhật các `PayrollRecord`.

---

### 1.3. Subsystem: Timecard Management
- **Lớp chính:**
  - `Timecard`: Lưu trữ thông tin chấm công của nhân viên.
  - `TimecardManager`: Xử lý việc nộp và truy xuất thông tin chấm công.
- **Quan hệ:**
  - `TimecardManager` sử dụng `Timecard` để quản lý dữ liệu thời gian làm việc.

---

### 1.4. Subsystem: Reporting
- **Lớp chính:**
  - `Report`: Tạo và xuất báo cáo theo tiêu chí.
  - `ReportManager`: Quản lý việc tạo và lập lịch báo cáo.
- **Quan hệ:**
  - `ReportManager` tạo ra các `Report`.
  - `Report` tham chiếu đến `PayrollRecord` để tạo nội dung báo cáo.

---

### 1.5. Subsystem: Security
- **Lớp chính:**
  - `Permission`: Quản lý quyền hạn của người dùng.
  - `SecurityManager`: Xử lý xác thực và mã hóa dữ liệu.
- **Quan hệ:**
  - `SecurityManager` sử dụng `Permission` để kiểm tra quyền truy cập.

---

### 1.6. Subsystem: Data Management
- **Lớp chính:**
  - `DatabaseManager`: Quản lý lưu trữ và truy xuất dữ liệu.
  - `SynchronizationManager`: Đồng bộ hóa dữ liệu trong hệ thống.
- **Quan hệ:**
  - `DatabaseManager` lưu trữ dữ liệu từ `PayrollRecord`, `Timecard`, và các lớp khác.
  - `SynchronizationManager` đồng bộ hóa với các nguồn dữ liệu khác.

---

**Biểu đồ lớp:**
![diagram](https://www.planttext.com/plantuml/png/b5V1Zjis4BtxAmXVAWDUeBaAmIBRE44D91jZlKNEOt9iiw58WHmvqHRviXxwIVs5WY8bYvHsazxCcJUZcNbFG_dVl_zvumWiDPLQk2zIrs2XObo1StT4LXuQmYqtUY-VaFswMFp2zit1jOwmAjaV3Ytx21fEMA6cHHSMh7yj66FiXZKExLQKR4zMwjF8gA72p5o3Sr-DpT7Mg1J9c38dgOiypNgIOLMoWp4AGSV0fXP0kBFcA1KM6h_6dw6NU5YLx6AaM7nVZ3gAlg6nOwFK_RG7h42glA-pqNZVL0UqcGU4iEXSrbqeygtH19os-cXyeU_6YTVCb-xJZZfDQxvhw8oQ90UIHWUIUbeOWwiNVswEVWQZO6FbKuWChZK3xXyqC_dlNZKFgBf2t5dMZaazqKvtlhcvJOPTikMhcrVBnNmpFTh36eTkcSbp1wqrIh6TDHoTymCEiucE1-J6Ye5HsnqdOiMgLgP5d3WEu70F2cnRigCoGBtTwCQb9e6YwSQJsJNI3f9mnZWetYWWlE-SnQft3zJ6yjz6eBdIMeTE8w0WMI47ApP0KB8Fqj7hnsYwNKL3CelRdk6wLkrcABe8enac6i0JoKLlhZLkqRzpuz1YEjGrIwlj2rrbJqrVv2HfJk0weiJ33ygVaUUCTgPZzm9CjLIoPMZNBNlyMAqJSDKv9yhjcvykry7JgxQVsi_hzcmQwpuR-mL5gaPpGUlJ_Uu1cO21i6GV30Ur0S9U9aBuF1s-E8-YraEkQEY77U9EI8-6G8N0gS3x9dCbkUPGIUgzWxmJiOmUOv6in0iE0NEg4sbdgskoPvGnnqrUiETwm3rFymFMnj9rBuNpQ27vuuG_Qklyrk564shAxf4JQhH06D8Mt4f2Aw5a7w5-tVV_wV0dSlBh8C1YB7xpXqUpsxpt1BsN2ZFFksySrU0Rk0jPvdT0B6JSm9hzhx8SFwDeL9yfdz1w0FZfZsZrnvTV-2iNQGUUoiZB-EMEfjcNsk8HBMe-9NoFlB6IsdvXegsaSzBeWVDwC6r_-1ta5U9COtbkJg_YApVzutDsJXOqtN6_w98hFK__mYKVjQ6vRMlo6xmGtHeVW8ao1LvnCGRZtiy3vjaQ1fctr15o7UipNmR-KTFTkW42VwbFrWvSiF2V7zIMKPZfeWdNp8iGWGe7o9NQ57IKMlpMRiKSx5ENTCHbg_dP6YsVPZ_mNAjvDzvy9JgZBlxRygWafsxvll1Iv7FA9pGh_ngjauxSSl5CZJugprIofIyve3l2tg0M_b_9Vm000F__0m00)
