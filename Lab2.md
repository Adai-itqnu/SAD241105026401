# **Phân tích các ca sử dụng trong Payroll System**

## **1. Maintain Timecard (Quản lý bảng chấm công)**
### Mô tả
- Nhân viên ghi lại giờ làm việc hàng tuần và liên kết với các mã dự án.
- Chỉ có thể chỉnh sửa bảng chấm công trong kỳ lương hiện tại trước khi nộp.

### Các bước chính
1. Tạo hoặc truy xuất bảng chấm công hiện tại.
2. Ghi nhận giờ làm việc theo mã dự án.
3. Nộp bảng chấm công và khóa chỉnh sửa.

### Điều kiện
- **Trước**: Nhân viên phải đăng nhập.
- **Sau**: Thông tin bảng chấm công được lưu hoặc khóa chỉnh sửa.

---

## **2. Run Payroll (Chạy bảng lương)**
### Mô tả
- Tự động tính toán và xử lý bảng lương hàng tuần (thứ Sáu) và ngày làm việc cuối tháng.

### Các bước chính
1. Lấy danh sách nhân viên cần trả lương.
2. Tính lương dựa trên bảng chấm công, thông tin nhân viên và các khoản khấu trừ.
3. Xử lý thanh toán:
   - In séc.
   - Gửi yêu cầu chuyển khoản ngân hàng.
4. Xóa nhân viên được đánh dấu xóa.

### Điều kiện
- **Trước**: Hệ thống phải được định thời gian chạy tự động.
- **Sau**: Lương của nhân viên được xử lý và cập nhật.

---

## **3. Maintain Employee Information (Quản lý thông tin nhân viên)**
### Mô tả
- Quản trị viên bảng lương có thể thêm, cập nhật, hoặc xóa thông tin nhân viên.

### Các bước chính
1. Chọn thao tác (thêm, cập nhật hoặc xóa).
2. Cập nhật thông tin, bao gồm:
   - Loại nhân viên (theo giờ, lương, hoa hồng).
   - Tùy chọn thanh toán (nhận tại văn phòng, chuyển khoản, gửi qua bưu điện).
   - Lương cơ bản, tỷ lệ hoa hồng, giới hạn giờ làm việc.
3. Lưu hoặc xóa nhân viên.

### Điều kiện
- **Trước**: Quản trị viên phải đăng nhập.
- **Sau**: Thông tin nhân viên được cập nhật hoặc xóa.

---

## **4. Maintain Purchase Order (Quản lý đơn đặt hàng)**
### Mô tả
- Nhân viên hưởng hoa hồng có thể tạo, chỉnh sửa hoặc xóa đơn đặt hàng.

### Các bước chính
1. Chọn thao tác (tạo, cập nhật hoặc xóa).
2. Cập nhật thông tin đơn hàng, bao gồm:
   - Khách hàng, địa chỉ thanh toán.
   - Sản phẩm, ngày đặt hàng.
3. Lưu hoặc xóa đơn hàng.

### Điều kiện
- **Trước**: Nhân viên phải đăng nhập.
- **Sau**: Đơn đặt hàng được cập nhật hoặc xóa.

---

## **5. Create Employee Report (Tạo báo cáo nhân viên)**
### Mô tả
- Nhân viên có thể tạo các báo cáo cá nhân, như tổng số giờ làm, số giờ cho từng dự án, số tiền lương nhận được.

### Các bước chính
1. Chọn loại báo cáo.
2. Cung cấp các thông số báo cáo (ngày bắt đầu, ngày kết thúc).
3. Xem hoặc lưu báo cáo.

### Điều kiện
- **Trước**: Nhân viên phải đăng nhập.
- **Sau**: Báo cáo được hiển thị hoặc lưu.

---

## **6. Create Administrative Report (Tạo báo cáo quản trị)**
### Mô tả
- Quản trị viên có thể tạo báo cáo như tổng số giờ làm việc hoặc tổng lương năm.

### Các bước chính
1. Chọn loại báo cáo.
2. Cung cấp các thông số báo cáo (ngày bắt đầu, ngày kết thúc, nhân viên liên quan).
3. Xem hoặc lưu báo cáo.

### Điều kiện
- **Trước**: Quản trị viên phải đăng nhập.
- **Sau**: Báo cáo được hiển thị hoặc lưu.

---

## **7. Select Payment Method (Chọn phương thức thanh toán)**
### Mô tả
- Nhân viên có thể chọn phương thức thanh toán (nhận trực tiếp, chuyển khoản, hoặc gửi qua bưu điện).

### Các bước chính
1. Chọn phương thức thanh toán.
2. Cung cấp thông tin cần thiết (như địa chỉ hoặc thông tin tài khoản ngân hàng).
3. Lưu tùy chọn thanh toán.

### Điều kiện
- **Trước**: Nhân viên phải đăng nhập.
- **Sau**: Phương thức thanh toán được cập nhật.

---

## **8. Login (Đăng nhập)**
### Mô tả
- Nhân viên và quản trị viên có thể đăng nhập để truy cập các tính năng của hệ thống.

### Các bước chính
1. Nhập tên đăng nhập và mật khẩu.
2. Xác thực thông tin đăng nhập.
3. Hiển thị các chức năng khả dụng dựa trên vai trò.

### Điều kiện
- **Trước**: Hệ thống phải sẵn sàng.
- **Sau**: Người dùng được đăng nhập vào hệ thống hoặc nhận thông báo lỗi.
