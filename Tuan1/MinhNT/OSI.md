# Day 1: Sơ lược về OSI.

----
## What is OSI?
> Mô hình tham chiếu OSI là một cấu trúc phả hệ có 7 tầng, nó xác định các yêu cầu cho sự giao tiếp giữa hai máy tính.

Mô hình OSI phân chia chức năng của một giao thức ra thành một chuỗi các tầng cấp. Mỗi một tầng cấp có một đặc tính là nó chỉ sử dụng chức năng của tầng dưới nó, đồng thời chỉ cho phép tầng trên sử dụng các chức năng của mình.

## Các tầng của OSI:
# Tầng 1: Physical Layer (Tầng vật lý):

> Lớp vật lý định nghĩa các đặc tính vật lý của mạng chẳng hạn như kết nối, cấp điện áp và thời gian.  

**Tầng vật lý bao gồm:**

- Hub.
- Repeater: bộ lặp.
- Converter: thiết bị chuyển đổi tín hiệu.
- Network Adapter: thiết bị tiếp hợp mạng.
- Host bus adapter: thiết bị tiếp hợp kênh máy chủ.

**Chức năng của tầng vật lý:**

- Thiết lập hoặc ngắt mạch kết nối điện với một môi trường truyền dẫn phương tiện truyền thông.
- Tham gia vào quy trình mà trong đó các tài nguyên truyền thông được chia sẻ hiệu quả giữa nhiều người dùng.
- Điều chế hoặc biến đổi giữa BIỂU DIỄN GIỮ LIỆU SỐ của các thiết bị người dùng và các tín hiệu tương ứng được truyền qua kênh truyền thông.


# Tầng 2: Data-link layer (Tầng liên kết dữ liệu):
Tầng liên kết dữ liệu cung cấp các phương tiện có tính chức năng và quy trình để truyền dữ liệu giữa các thực thể mạng (truy cập đường truyền, đưa dữ liệu vào mạng), phát hiện và có thể sửa chữa các lỗi trong tầng vật lý nếu có.

Các lớp liên kết dữ liệu định dạng các thông điệp vào một khung dữ liệu(Frame), và thêm vào đó một header chứa các địa chỉ phần cứng nơi nhận và địa chỉ nguồn của nó.Tiêu đề này chịu trách nhiệm cho việc tìm kiếm các thiết bị đích tiếp theo trên một mạng nội bộ.

>Lớp này là chia nhỏ thành 2 lớp con: điều khiển logic liên kết (LLC) và kiểm soát truy cập media (MAC).  
Các chức năng LLC bao gồm:  
- Quản lý các khung cho các lớp trên và dưới  
- Kiểm soát lỗi.  
- Điều khiển luồng.  
Lớp con MAC mang địa chỉ vật lý của mỗi thiết bị trên mạng.Địa chỉ này là thường được gọi là địa chỉ MAC của thiết bị.Địa chỉ MAC là một địa chỉ 48 bit được ghi vào NIC trên thiết bị của nhà sản xuất.

# Tầng 3: Network Layer (Tầng mạng):
Tầng mạng cung cấp các chức năng và quy trình cho việc truyền các chuỗi dữ liệu có độ dài đa dạng, từ một nguồn tới một đích, thông qua một hoặc nhiều mạng, trong khi vẫn duy trì chất lượng dịch vụ **(quality of service)** mà tầng giao vận yêu cầu. 

Tầng mạng thực hiện chức năng định tuyến.Các thiết bị định tuyến (router) hoạt động tại tầng này — gửi dữ liệu ra khắp mạng mở rộng, làm cho liên mạng trở nên khả thi.  
Đây là một hệ thống định vị địa chỉ logic – các giá trị được chọn bởi kỹ sư mạng. Hệ thống này có cấu trúc phả hệ.

# Tầng 4: Transport Layer (Tầng giao vận): 

Tầng giao vận cung cấp dịch vụ chuyên dụng chuyển dữ liệu giữa các người dùng tại đầu cuối, nhờ đó các tầng trên không phải quan tâm đến việc cung cấp dịch vụ truyền dữ liệu đáng tin cậy và hiệu quả.

Tầng giao vận kiểm soát độ tin cậy của một kết nối được cho trước. Có nghĩa là tầng giao vận có thể theo dõi các gói tin và truyền lại các gói bị thất bại.

Ở tầng 4 địa chỉ được đánh là address ports, thông qua address ports để phân biệt được ứng dụng trao đổi.

# Tầng 5: Session Layer:
**Chức năng của Session layer:**  

- Kiểm soát các phiên hội thoại giữa các máy tính. 
- Thiết lập, duy trì và kết thúc giao tiếp với các thiết bị nhận.

Tầng này hỗ trợ hoạt động từ duplex (đơn công) - half duplex đến single và thiết lập các quy trình đánh dấu điểm hoàn thành (trì hoãn - kết thúc - khởi động lại); giúp việc phục hồi truyền thông nhanh hơn khi có lỗi xảy ra.

Tầng này có khả năng ngắt các phiên giao dịch và kiểm tra/phục hồi phiên.

#Tầng 6: Presentation Layer:
**Chức năng:**  
Lớp này trên máy tính truyền dữ liệu đảm nhiệm vai trò dịch dữ liệu được gửi từ tầng application sang định dạng chung.  
Tại máy tính nhận, lớp này lại chuyển từ định dạng chung sang định dạng của tầng application.

- Dịch các mã kí tự từ ASCII -> EBCDIC.
- Chuyển đổi dữ liệu như từ số interger sang số dấu phảy động.
- Nén dữ liệu để giảm lượng giữ liệu truyền trên mạng.
- Mã hóa và giải mã dữ liệu để đảm bảo sự bảo mật trên mạng.

# Tầng 7: Tầng ứng dụng (Application layer):
Đây là tầng gần với người sử dụng nhất. Nó cung cấp phương tiện cho người dùng truy nhập các thông tin và dữ liệu trên mạng thông qua chương trình ứng dụng. Tầng này là giao diện chính để người dùng tương tác với chương trình ứng dụng, và qua đó với mạng.