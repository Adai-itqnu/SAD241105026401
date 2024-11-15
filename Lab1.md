# Lab 1 - Phân tích kiến trúc, cơ chế, ca sử dụng

## 1. Phân tích kiến trúc

### Kiến trúc đề xuất: 3-Tier Architecture
**Giải thích:** Hệ thống "Payroll System" được xây dựng trên kiến trúc ba tầng, gồm các tầng sau:

1. **Presentation (Giao diện người dùng)**
   - Vai trò: Đảm bảo tương tác với người dùng, hiển thị dữ liệu và nhận thông tin đầu vào.
   - Thành phần chính: UI (Giao diện đồ họa hoặc dòng lệnh).
   - Tương tác: Gửi yêu cầu tới tầng Application, nhận dữ liệu trả về.

2. **Application (Logic ứng dụng)**
   - Vai trò: Xử lý nghiệp vụ chính, tính toán lương và duy trì thẻ thời gian.
   - Thành phần chính:
     - `PaymentService`: Quản lý thanh toán.
     - `TimecardService`: Quản lý thẻ thời gian.
     - `EmployeeService`: Quản lý thông tin nhân viên.
   - Tương tác: Nhận yêu cầu từ tầng Presentation, xử lý logic nghiệp vụ, và truy cập tầng Data để lấy dữ liệu hoặc lưu trữ kết quả.

3. **Data (Dữ liệu)**
   - Vai trò: Lưu trữ dữ liệu.
   - Thành phần chính:
     - `EmployeeRepository`, `PaymentRepository`, `TimecardRepository`: Quản lý truy xuất dữ liệu.
   - Tương tác: Nhận yêu cầu từ Application, thực hiện truy vấn và trả kết quả.

### Biểu đồ Package
![Diagram](https://www.planttext.com/api/plantuml/png/R91D2i8m44RtEKNelbUG2hhehgWzm90E4imVoIW4yMGkF99Ni1QYCMQPRzxapSpp_kW2WQUpLio1EC4HUJDu36W8I5hJy2lZN2W8WOyzkx4ljdPEIV573H3rtBr7Vv42F_51QXJWfpBVQgTiH4nvRjW0GVvrOdVeR91aVIojbKeIPwNPCVQyRLVbiB_FXQWuYrKMh68fDijz6TMXcTxNVm400F__0m00)


