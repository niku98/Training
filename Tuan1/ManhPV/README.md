# Báo cáo

## Mô hình OSI
### Định nghĩa:
	Là mô hình mạng phân lớp, gồm 7 lớp, mỗi lớp phụ trách một chức năng riêng. Mô hình OSI cho phép các máy từ những nhà sản xuất khác nhau có thể giao tiếp được với nhau, trước khi mô hình này ra đời, chỉ những máy được sản xuất từ cùng một hàng mới có thể giao tiếp được với nhau qua mạng.

### Các lớp của mô hình OSI
#### 1. Lớp Application
	Là lớp đầu tiên, trên cùng của mô hình OSI. Lớp này có nhiệm vụ cung cấp giao thức cho các ứng dụng người dùng sử dụng.
#### 2. Lớp Presentation
	Lớp này có chức năng chuẩn hóa dữ liệu nhận được từ lớp Application để các lớp dưới nó có thể hiểu được. Và nó cũng làm việc ngược lại là nhận dữ liệu từ lớp dưới nó, cụ thể là lớp Session, biến đổi dữ liệu này để lớp Application có thể hiểu được.
#### 3. Lớp Session
	Sau khi nhận được dữ liệu từ lớp Application, lớp này sẽ thiết lập một phiên(session) với máy nhận dữ liệu. Chức năng chính của lớp này là đồng bộ hóa qua trình liên lạc giữa hai máy và quản lý việc trao đổi dữ liệu.
#### 4. Lớp Transport
	Lớp Transport chịu trách nhiệm đảm bảo toàn bộ dữ liệu truyền tải từ máy gửi đến máy nhận. Từ việc nhận dữ liệu từ lớp Application qua lớp Session, tích hợp các dữ liệu này vào luồng, kiểm tra lỗi và khôi phục dữ liệu khi cần thiết.
