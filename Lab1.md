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
   - Vai trò: Lưu trữ dữ liệu thông tin nhân viên, dữ liệu thanh toán, dữ liệu chấm công.
   - Thành phần chính:
     - `EmployeeRepository`, `PaymentRepository`, `TimecardRepository`: Quản lý truy xuất dữ liệu.
   - Tương tác: Nhận yêu cầu từ Application, thực hiện truy vấn và trả kết quả về cho tầng Application.

### Biểu đồ Package
- Dưới đây là biểu đồ package thể hiện các tầng kiến trúc của hệ thống:
![Biểu đồ Package](https://www.planttext.com/api/plantuml/png/R91D2i8m44RtEKNelbUG2hhehgWzm90E4imVoIW4yMGkF99Ni1QYCMQPRzxapSpp_kW2WQUpLio1EC4HUJDu36W8I5hJy2lZN2W8WOyzkx4ljdPEIV573H3rtBr7Vv42F_51QXJWfpBVQgTiH4nvRjW0GVvrOdVeR91aVIojbKeIPwNPCVQyRLVbiB_FXQWuYrKMh68fDijz6TMXcTxNVm400F__0m00)

## 2. Cơ chế phân tích

**Các cơ chế cần thiết trong hệ thống "Payroll System"**

1. **Tính toán lương (Payroll Calculation):**
   - Mô tả: Tính toán lương dựa trên các thông tin như giờ làm việc, hợp đồng của nhân viên, và các khoản khấu trừ.
   - Thành phần: Sử dụng `PayrollCalculator` trong `PaymentService`.
2. **Quản lý thẻ thời gian (Timecard Management):**
   - Mô tả: Ghi nhận, lưu trữ và cập nhật thông tin giờ làm việc của nhân viên.
   - Thành phần: `TimeCardService` và `TimeCardRespository`.
3. **Bảo mật (Security):**
   - Mô tả: Chỉ người dùng được phép mới có thể truy cập hoặc thay đổi dữ liệu.
   - Thành phần: Phân quyền truy cập trong hệ thống qua các lớp `EmployeeService`.
4. **Báo cáo (Reporting):**
   - Mô tả: Xuất báo cáo cho lương và giờ làm việc để quản lý dễ dàng theo dõi.
   - Thành phần: Các báo cáo có thể được truy vấn từ `PaymentService` và `TimecardService`.
     
## 3. Phân tích ca sử dụng Select Payment Method

1. **Mô tả ca sử dụng**
   - Tác nhân (Actor): Nhân viên
   - Mục tiêu: Cho phép nhân viên chọn phương thức thanh toán lương.
   - Kết quả mong đợi: Thông tin về phương thức thanh toán được cập nhật thành công.
     
2. **Lớp phân tích và nhiệm vụ của từng lớp**
   1. Employee: Lưu trữ thông tin nhân viên, bao gồm tên, chức danh, và các phương thức thanh toán hiện tại.
   2. Payment: Thể hiện thông tin chi tiết về thanh toán cho nhân viên.
   3. PaymentMethod: Định nghĩa các phương thức thanh toán (chuyển khoản, gửi bưu điện, nhận trực tiếp).
   4. PaymentService: Xử lý logic chính để cập nhật phương thức thanh toán cho nhân viên.

3. **Biểu đồ Sequence**
   - Biểu đồ này mô tả quy trình chọn phương thức thanh toán của nhân viên.
![Biểu đồ Sequence](https://www.planttext.com/api/plantuml/png/R9A_QW8n7CVtF4LmKj0Nw514ALr4IZtSunakeNU_7BaelT6fSn-Wu5LAGH0wTBeREWHyZpn1Nw6_M0_FrY4G-7w-VmZvhhxwcM7QB9AOiD0eJM-ID5OvvvHb59OaHL66CcLWQEkEvGa7C-5wAKFUyaYQdIE1J7Z8zBp9c3_CWC53Kvzb_sgqYkDxdYfzNgOpGc19UzVOIwzeRhUBeIlV5u5W809b2sXt24e860_4hdpB9wvwlfMkUXdPTJB5orFOJkncBEmhJANTGeSWtAj3ZNRbPkggrGNVCVkNixjZPwCzGq-0w0gwDAgzzQIPjqMksic6usn9bvu2EcJMMFLeYt0iNBbhjDLhz66EAmiri8KQuXdjF_O5H3xyX3V3knGYkyvncRvOKWSTAb36HySAOJyXyj8fD11s3MBe1NpwFeUv_qe_0000__y30000)

## 4. Phân tích ca sử dụng Maintain Timecard

1. **Mô tả ca sử dụng**
   - Tác nhân (Actor): Nhân viên hoặc quản lý
   - Mục tiêu: Thêm hoặc cập nhật thẻ thời gian của nhân viên.
   - Kết quả mong đợi: Thẻ thời gian được ghi lại và cập nhật vào hệ thống.
     
2. ** Lớp phân tích và nhiệm ** 
   - Employee: Đại diện cho nhân viên, lưu trữ thông tin cơ bản của nhân viên.
   - Timecard: Chứa dữ liệu về giờ làm việc của nhân viên cho từng ngày.
   - TimecardRepository: Lưu trữ và quản lý truy xuất dữ liệu thẻ thời gian của nhân viên.

3. ** Biểu đồ Sequence **
   - Biểu đồ dưới đây mô tả quy trình thêm hoặc sửa thẻ thời gian cho nhân viên.
     







