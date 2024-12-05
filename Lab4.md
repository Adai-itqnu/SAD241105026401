# Thiết kế các ca sử dụng cho hệ thống "Payroll System"

## 1. Phân tích tác nhân (Actors)
### Các tác nhân chính:
- **Nhân viên (Employee):** 
  - Đăng nhập vào hệ thống để xem lương hoặc cập nhật thông tin cá nhân.
- **Quản lý nhân sự (HR Manager):** 
  - Quản lý bảng lương, phê duyệt thông tin nhân viên, và tạo báo cáo.
- **Hệ thống thanh toán (Payroll System):** 
  - Tự động tính toán lương và hỗ trợ lưu trữ thông tin lương.

---

## 2. Các ca sử dụng chính
### **2.1. Xem thông tin lương (View Payroll Information)**
- **Tác nhân:** Nhân viên.
- **Mô tả:** Nhân viên đăng nhập vào hệ thống để xem chi tiết lương của mình.
- **Luồng chính:**
  1. Nhân viên đăng nhập vào hệ thống.
  2. Hệ thống xác thực thông tin đăng nhập.
  3. Nhân viên chọn chức năng “Xem lương”.
  4. Hệ thống hiển thị chi tiết lương (bao gồm lương cơ bản, phụ cấp, khấu trừ).
- **Điều kiện tiên quyết:** Nhân viên đã được tạo tài khoản trong hệ thống.
- **Luồng thay thế:**
  - Nếu thông tin đăng nhập sai, hệ thống thông báo lỗi và yêu cầu nhập lại.
  
**Biểu đồ**

![XemTTLuong](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9hRa5EVcLgAXUCeQ1hfn2GM5cKdvCJN5bSaffhfN1amf7cl7I5l8o7kzOMSA58Ob4TSNXXia99niFT6q7KuIr0dIMPUPZQO1PQANXaFjpTd0VMqusaHI7ds8PZ2_FIkHnIyrA0BWO0003__mC0)

 ### 2.2. Cập nhật thông tin cá nhân (Update Personal Information)
- **Tác nhân:** Nhân viên, Quản lý nhân sự.
- **Mô tả:** Nhân viên gửi yêu cầu cập nhật thông tin cá nhân, và Quản lý nhân sự phê duyệt.
- **Luồng chính:**
  1. Nhân viên chọn chức năng “Cập nhật thông tin”.
  2. Nhân viên nhập thông tin cần thay đổi và gửi yêu cầu.
  3. Hệ thống ghi nhận yêu cầu và gửi thông báo đến Quản lý nhân sự.
  4. Quản lý nhân sự phê duyệt yêu cầu.
  5. Hệ thống cập nhật thông tin cá nhân và thông báo kết quả.
**Điều kiện tiên quyết:**
- Nhân viên đã đăng nhập vào hệ thống.
- Quản lý nhân sự có quyền phê duyệt thay đổi.
**Luồng thay thế:**
- Nếu Quản lý nhân sự từ chối yêu cầu, hệ thống thông báo cho nhân viên lý do từ chối.


**Biểu đồ**


![Cập nhật thông tin các nhân](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9hRa5EVcLgAfJh4UIRc9UOdbh41PDGqBLJ24YiBChFoGckB2v9pRLIS7-uUsscGkNXLQKAoGztBGUJQmiKyZA0L8b2ISRXBNdf2YMPULme-a06mOt7OaX1nk5L2YcbbGztjvTmmHLYiJu0IQ5-IKPYfSAHYGztJyt4QpFCErOA8H1LIOSNvYjaFzorlqIXiFJXhiLS3gbvAQ1m0G000F__0m00)

### 2.3. Tính toán lương (Calculate Payroll)
- **Tác nhân:** Hệ thống.
- **Mô tả:** Hệ thống tự động tính toán lương dựa trên thông tin đã lưu trữ.
- **Luồng chính:**
  1. Hệ thống thu thập thông tin nhân viên (lương cơ bản, giờ làm, khấu trừ, phụ cấp).
  2. Hệ thống tính toán lương cho từng nhân viên.
  3. Lưu trữ thông tin lương vào cơ sở dữ liệu.
**Điều kiện tiên quyết:**
- Dữ liệu nhân viên và bảng công đã được cập nhật đầy đủ.
**Luồng thay thế:**
- Nếu dữ liệu thiếu, hệ thống gửi thông báo cho Quản lý nhân sự bổ sung.

**Biểu đồ**

![Tính toán lương](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO97a6zYNc9wQX5NG69bKNvEJd1bSKbgheAkdGAAW9L2I4QfGad6mrrh2nHI7kvUhv2J-N1tUwb2ph4DnnRcfMDgTqaiIKnAB4wrKl0vjW6ejGYagIJZy9QyT8MIp3nC3N2dM2au7LwOhv0C8l8UxjeFiZSJJ2DPpEMGcfS2yWS0003__mC0)

### 2.4. Quản lý bảng lương (Manage Payroll Records)
- **Tác nhân:** Quản lý nhân sự.
- **Mô tả:** Quản lý nhân sự có thể tạo mới, cập nhật hoặc xóa bảng lương.
- **Luồng chính:**
  1. Quản lý nhân sự chọn chức năng “Quản lý bảng lương”.
  2. Chọn một trong các tùy chọn: Tạo mới, Cập nhật, Xóa.
  3. Hệ thống thực hiện hành động và lưu trữ thay đổi.
**Điều kiện tiên quyết:** Quản lý nhân sự có quyền truy cập chức năng này.

**Biểu đồ**


![Quản lý bản lương](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO97a6zYNc9wQX4NdAMWQwSGa5XPb9-J4rnPN9AQQwNWdF5mTs-UGc3fmrsBynHo3kzLI0AnqXLoZcqujZ0ldGj5FSW0byIInAJ4ubGhXH2Wtet92XcP3tUtvocKP2HMAXoP-73tr4m5ZP27knRcwpi_tBMsG24l0qYLw4SStfoeYMaSt74Wymvl0TgST7XXlaBsmrtxInGAGSxYSaZDIm7v2m000F__0m00)

### 2.5. Tạo báo cáo lương (Generate Payroll Reports)
- **Tác nhân:** Quản lý nhân sự.
- **Mô tả:** Quản lý nhân sự tạo báo cáo lương hàng tháng hoặc quý.
- **Luồng chính:**
  1. Quản lý chọn chức năng “Tạo báo cáo”.
  2. Nhập phạm vi thời gian hoặc tiêu chí cụ thể (bộ phận, phòng ban).
  3. Hệ thống tạo báo cáo và hiển thị kết quả.
**Điều kiện tiên quyết:**
- Dữ liệu lương đã đầy đủ trong hệ thống.

**Biểu đồ**

![Tạo báo cáo lương](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO97a6zYNc9wQX4NdAMWQwSGa5XPb9-J4rnPN9AQQwNWb_5mrze2XSh3gqeLaX_kMbwga7HuORv2Cf3WGb4AqkkIM9AOb5YSQgKGab6gK0BHcl9mztg5dCo7kzjBCNN0hRPIy00gQSu3wThTZMI9GsfU2iZH00000F__0m00)

## 3. Giải thích thiết kế
- Phản ánh yêu cầu nghiệp vụ: Các ca sử dụng được xây dựng để đáp ứng các yêu cầu cốt lõi của hệ thống Payroll.
- Dựa trên phân tích: Các tác nhân và chức năng được xác định từ bài phân tích (lab 2 và lab 3).
- Tính khả thi: Thiết kế linh hoạt, có thể mở rộng để bổ sung các chức năng khác như quản lý phúc lợi hoặc chấm công

### **Lợi ích của thiết kế này:**
- **Tính rõ ràng:** Cách tiếp cận theo từng bước giúp dễ dàng hiểu được các chức năng chính của hệ thống.
- **Dễ bảo trì:** Với cấu trúc này, các chức năng mới có thể được thêm vào mà không ảnh hưởng đến hệ thống hiện tại.
- **Phù hợp thực tế:** Thiết kế dựa trên phân tích từ các bài lab trước đảm bảo đáp ứng yêu cầu nghiệp vụ.












