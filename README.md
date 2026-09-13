# CHECKPOINT 1: ĐĂNG KÝ ĐỀ TÀI

**Tên dự án:** NutriLife - Hệ thống quản lý dinh dưỡng
**Sinh viên thực hiện:** Lê Bích Diệp 

---

## 1. Lý Do Chọn Đề Tài

Trong xã hội hiện đại, nhu cầu chăm sóc sức khỏe, kiểm soát cân nặng và duy trì lối sống lành mạnh ngày càng gia tăng. Việc theo dõi chế độ ăn uống hằng ngày đóng vai trò quyết định đến hiệu quả của quá trình tăng cân, giảm cân hoặc duy trì vóc dáng. 

Tuy nhiên, người tiêu dùng Việt Nam hiện gặp nhiều khó khăn trong việc:
- Không nắm rõ lượng calo và thành phần dinh dưỡng (Macro: Protein, Carbs, Fat) trong các món ăn hằng ngày.
- Thiếu công cụ theo dõi khoa học, dễ sử dụng và được cá nhân hóa theo thể trạng cá nhân.
- Các giải pháp hiện có trên thị trường đa phần là ứng dụng nước ngoài, chưa tối ưu hóa cho cơ sở dữ liệu món ăn thuần Việt.

Từ thực trạng đó, dự án **NutriLife** được xây dựng nhằm cung cấp giải pháp toàn diện giúp người dùng dễ dàng tính toán, kiểm soát lượng calo nạp vào và xây dựng chế độ dinh dưỡng hợp lý.

---

## 2. Mục Tiêu Của Đề Tài

* **Mục tiêu tổng quát:** Xây dựng hệ thống ứng dụng web/mobile NutriLife hỗ trợ quản lý dinh dưỡng, tính toán chỉ số calo và đề xuất khẩu phần ăn cá nhân hóa dựa trên thể trạng và mục tiêu sức khỏe của người dùng.
* **Mục tiêu cụ thể:**
  1. Nghiên cứu và áp dụng các công thức tính toán chỉ số dinh dưỡng chuẩn mực (BMR Mifflin-St Jeor, TDEE, tỷ lệ Macro).
  2. Xây dựng các chức năng cốt lõi: Đăng ký/Đăng nhập, Quản lý hồ sơ thể trạng, Tra cứu thực phẩm, Nhập nhật ký ăn uống, Gợi ý thực đơn, và Thống kê/Cảnh báo tiến độ.
  3. Triển khai, kiểm thử và tối ưu hóa hiệu năng, tính ổn định của hệ thống.

---

## 3. Đối Tượng Và Phạm Vi Nghiên Cứu

### 3.1. Đối tượng nghiên cứu
- Các công thức toán học và thuật toán tính chỉ số dinh dưỡng: BMR (Mifflin-St Jeor), TDEE, phân bổ dinh dưỡng Macro (Protein, Carbs, Fat).
- Luồng nghiệp vụ quản lý nhật ký ăn uống và tính toán calo tiêu thụ/nạp vào.
- Quy trình phân tích, thiết kế và triển khai ứng dụng phần mềm theo mô hình client-server.

### 3.2. Phạm vi nghiên cứu
- **Phạm vi chức năng:**
  - Quản lý tài khoản và thông tin thể trạng người dùng (chiều cao, cân nặng, tuổi, mức độ vận động, mục tiêu).
  - Tra cứu và quản lý thư viện thực phẩm.
  - Ghi chép nhật ký ăn uống theo bữa (Sáng, Trưa, Tối, Bữa phụ).
  - Thống kê, báo cáo calo nạp vào so với TDEE mục tiêu và đưa ra cảnh báo.
- **Phạm vi người dùng:** Người dùng cá nhân có nhu cầu theo dõi chế độ ăn uống và kiểm soát cân nặng.
- **Phạm vi dữ liệu:** Tập trung vào chỉ số dinh dưỡng của các thực phẩm và món ăn phổ biến.

---

## 4. Phương Pháp Nghiên Cứu Và Công Nghệ Sử Dụng

### 4.1. Phương pháp nghiên cứu
- **Phương pháp thu thập thông tin:** Khảo sát thực trạng nhu cầu kiểm soát calo và phân tích các giải pháp hiện có.
- **Phương pháp phân tích & thiết kế:** Sử dụng ngôn ngữ UML để thiết kế sơ đồ Use Case, ERD, Sequence Diagram và RESTful API Specs.
- **Phương pháp thực nghiệm:** Lập trình xây dựng sản phẩm, xây dựng kịch bản kiểm thử (Test Cases) và sửa lỗi dựa trên kết quả kiểm thử.

### 4.2. Danh mục công nghệ dự kiến (Tech Stack)

| Thành phần | Công nghệ lựa chọn | Lý do lựa chọn |
| :--- | :--- | :--- |
| **Frontend** | HTML,CSS, JavaScrip | Tối ưu trải nghiệm người dùng (UI/UX), tương thích đa nền tảng. |
| **Backend** | Node.js (Express) | Hiệu năng cao, xử lý RESTful API nhanh chóng, dễ mở rộng. |
| **Database** | MongoDB | Hệ quản trị CSDL quan hệ ổn định, hỗ trợ truy vấn dữ liệu cấu trúc tốt. |
| **Thiết kế & Tool** | Figma, Git/GitHub | Hỗ trợ thiết kế UI/UX, test API và quản lý mã nguồn/tiến độ. |

---

## 5. Bố Cục Dự Kiến Của Báo Cáo Đồ Án

* **LỜI CẢM ƠN**
* **MỞ ĐẦU**
* **CHƯƠNG 1: TỔNG QUAN VÀ PHÂN TÍCH YÊU CẦU NGHIỆP VỤ**
  * 1.1. Tổng quan về bài toán quản lý dinh dưỡng và calo
  * 1.2. Yêu cầu hệ thống NutriLife (Functional & Non-functional)
  * 1.3. Phân tích các chỉ số dinh dưỡng cốt lõi (BMR, TDEE, Macro)
* **CHƯƠNG 2: THIẾT KẾ HỆ THỐNG NUTRILIFE**
  * 2.1. Kiến trúc tổng thể của hệ thống
  * 2.2. Phân tích và thiết kế Use Case
  * 2.3. Thiết kế Cơ sở dữ liệu (ERD & Chi tiết bảng)
  * 2.4. Thiết kế Luồng xử lý và API (Sequence Diagram & REST API)
  * 2.5. Thiết kế giao diện người dùng (UI/UX Design)
* **CHƯƠNG 3: TRIỂN KHAI VÀ KIỂM THỬ HỆ THỐNG**
  * 3.1. Môi trường phát triển và công nghệ cài đặt
  * 3.2. Triển khai các chức năng cốt lõi
  * 3.3. Kiểm thử hệ thống (Test Cases & Đánh giá)
* **KẾT LUẬN VÀ HƯỚNG PHÁT TRIỂN**
