# CHECKPOINT 02: PHÂN TÍCH YÊU CẦU NGHIỆP VỤ HỆ THỐNG NUTRILIFE


---

## 1. MỤC TIÊU CHECKPOINT 02

Checkpoint 02 tập trung vào phân tích yêu cầu nghiệp vụ của hệ thống NutriLife, bao gồm:
* Xác định rõ người dùng và tác nhân trong hệ thống.
* Mô tả yêu cầu chức năng (Functional Requirements) và yêu cầu phi chức năng (Non-functional Requirements).
* Xây dựng sơ đồ Use Case tổng quan và đặc tả chi tiết các use case chính.
* Phân tích dữ liệu đầu vào – đầu ra và các ràng buộc nghiệp vụ.
* Làm rõ quy tắc xử lý chính liên quan đến thuật toán dinh dưỡng (BMR, TDEE, Macro).

---

## 2. TỔNG QUAN BÀI TOÁN NGHIỆP VỤ

### 2.1. Bối cảnh và vấn đề
Người dùng hiện nay gặp nhiều khó khăn trong việc:
* Theo dõi lượng calo và dinh dưỡng nạp vào hằng ngày.
* Lựa chọn thực phẩm phù hợp để cân bằng các nhóm chất đa lượng (Protein, Carbohydrate, Fat).

### 2.2. Giải pháp đề xuất
Xây dựng hệ thống Web App **NutriLife** cho phép người dùng:
* Khai báo thông tin thể trạng để hệ thống tự động tính BMR, TDEE, calo mục tiêu và định lượng Macro.
* Tra cứu thư viện thực phẩm phong phú (đặc biệt là các món ăn thuần Việt) và ghi nhật ký ăn uống theo từng bữa.

---

## 3. XÁC ĐỊNH TÁC NHÂN (ACTORS)

| Tác nhân | Mô tả | Quyền hạn chính |
| :--- | :--- | :--- |
| **Người dùng (User)** | Đăng ký/đăng nhập, tra cứu thực phẩm,, xem gợi ý thực đơn, nhận cảnh báo. |
| **Quản trị viên (Admin)** | Người quản lý hệ thống và dữ liệu nội dung. | Quản lý thư viện thực phẩm (CRUD), quản lý tài khoản người dùng, quản lý thực đơn mẫu, xem thống kê hệ thống. |
| **Hệ thống (System)** | Tác nhân tự động xử lý các thuật toán và thông báo background. | Tính BMR/TDEE/Macro, gợi ý thực đơn thông minh, kiểm tra vượt TDEE và kích hoạt cảnh báo. |

---

## 4. YÊU CẦU CHỨC NĂNG VÀ QUY TẮC NGHIỆP VỤ

### 4.1. Bảng yêu cầu chức năng (Functional Requirements)

| Mã | Tên chức năng | Mô tả chi tiết | Tác nhân | Độ ưu tiên |
| :---: | :--- | :--- | :---: | :---: |
| **F-01** | Đăng ký tài khoản | Tạo tài khoản mới với username, email, mật khẩu và thông tin thể trạng ban đầu. | User | Cao |
| **F-02** | Đăng nhập | Xác thực người dùng bằng email/mật khẩu, cấp JWT token. | User, Admin | Cao |
| **F-03** | Đăng xuất | Hủy phiên làm việc, xóa token phía client. | User, Admin | Trung bình |
| **F-05** | Tính toán chỉ số dinh dưỡng | Tự động tính BMR, TDEE, calo mục tiêu và phân bổ macro (Protein/Carb/Fat). | System | Cao |
| **F-06** | Tra cứu thực phẩm | Tìm kiếm thực phẩm theo từ khóa, hỗ trợ gợi ý tự động (AJAX + Debounce). | User | Cao |
| **F-09** | Chỉnh sửa/Xóa món ăn | Cho phép sửa khối lượng hoặc xóa món khỏi nhật ký ăn uống hằng ngày. | User | Trung bình |
| **F-10** | Gợi ý thực đơn thông minh | Đề xuất 3–5 thực đơn dựa trên calo và macro còn lại trong ngày. | System | Cao |
| **F-12** | Cảnh báo dinh dưỡng | Cảnh báo real-time khi tổng calo vượt quá TDEE cho phép (>100% mục tiêu). | System | Cao |
| **F-14** | Quản lý người dùng | Admin xem danh sách người dùng, vô hiệu hóa tài khoản vi phạm. | Admin | Trung bình |
| **F-15** | Quản lý thực đơn mẫu | Admin tạo/sửa/xóa các thực đơn mẫu phục vụ gợi ý. | Admin | Trung bình |

### 4.2. Quy tắc xử lý nghiệp vụ (Business Rules)

* **BR-01 (Ràng buộc thể trạng):** Tuổi: $10 \le \text{age} \le 120$; Chiều cao: $50 \le \text{height} \le 300\text{ cm}$; Cân nặng: $10 \le \text{weight} \le 500\text{ kg}$.
* **BR-02 (Mật khẩu):** Mật khẩu tối thiểu 6 ký tự, khuyến nghị bao gồm chữ hoa, chữ thường, chữ số và ký tự đặc biệt.
* **BR-05 (Khối lượng món ăn):** Khối lượng nhập phải lớn hơn 0 ($>0$); đơn vị tính mặc định là gram ($g$).
* **BR-07 (Gợi ý thực đơn):** Chỉ đề xuất các món ăn có tổng calo $\le \text{Calo còn lại} + 20\%$ để tránh vượt ngưỡng quá nhiều.
* **BR-08 (Phân quyền Admin):** Chỉ các tài khoản có trường `role = "admin"` mới được phép thực hiện các chức năng CRUD thực phẩm và quản lý người dùng.

---

## 5. YÊU CẦU PHI CHỨC NĂNG (NON-FUNCTIONAL REQUIREMENTS)

| Mã | Loại yêu cầu | Mô tả chi tiết | Tiêu chí đo lường / Đánh giá |
| :---: | :--- | :--- | :--- |
| **NF-01** | Hiệu năng | Phản hồi API nhanh chóng cho các thao tác thông thường. | Thời gian phản hồi $< 2$ giây (trung bình $< 500\text{ms}$). |
| **NF-02** | Bảo mật | Mã hóa mật khẩu, xác thực bằng JWT, phân quyền RBAC. | Mật khẩu hash bằng `bcrypt`; JWT token hết hạn sau 7 ngày. |
| **NF-05** | Trải nghiệm (UX) | Giao diện thân thiện, responsive, hỗ trợ đa thiết bị. | Đạt độ tương thích Mobile/Tablet/Desktop; thao tác chính $\le 3$ clicks. |

---

## 6. SƠ ĐỒ USE CASE VÀ ĐẶC TẢ CHI TIẾT

### 6.1. Sơ đồ Use Case Tổng Quan

admin: quản lý thực phẩm, quản lý người dùng, đăng nhập, quản lý thực đơn
người dùng: đăng ký, đăng nhập, chọn thực đơn, nhận cảnh báo
