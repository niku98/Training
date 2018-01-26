# Báo cáo

## Mô hình OSI
Là mô hình mạng phân lớp, gồm 7 lớp, mỗi lớp phụ trách một chức năng riêng. Mô hình OSI cho phép các máy từ những nhà sản xuất khác nhau có thể giao tiếp được với nhau, trước khi mô hình này ra đời, chỉ những máy được sản xuất từ cùng một hàng mới có thể giao tiếp được với nhau qua mạng.

### Các lớp của mô hình OSI

<img src="http://2.bp.blogspot.com/_oI4G5UUCxnU/TRxegRxWZaI/AAAAAAAAAJ4/49EnNEMpPt8/s1600/osi.gif">

#### 1. Lớp Application
Là lớp đầu tiên, trên cùng của mô hình OSI. Lớp này có nhiệm vụ cung cấp giao thức cho các ứng dụng người dùng sử dụng.<br />
**Các giao thức:** HTTP, SMTP, FTP, Telnet, SSH,...
#### 2. Lớp Presentation
Lớp này có chức năng chuẩn hóa dữ liệu nhận được từ lớp Application để các lớp dưới nó có thể hiểu được. Và nó cũng làm việc ngược lại là nhận dữ liệu từ lớp dưới nó, cụ thể là lớp Session, biến đổi dữ liệu này để lớp Application có thể hiểu được.<br />
**Các giao thức:** XDR, SMB, AFP,...
#### 3. Lớp Session
Sau khi nhận được dữ liệu từ lớp Application, lớp này sẽ thiết lập một phiên(session) với máy nhận dữ liệu. Chức năng chính của lớp này là đồng bộ hóa quá trình liên lạc giữa hai máy.<br />
**Các giao thức:** ASAp, TLS, SSH,
#### 4. Lớp Transport
Lớp Transport chịu trách nhiệm đảm bảo toàn bộ dữ liệu truyền tải từ máy gửi đến máy nhận. Từ việc nhận dữ liệu từ lớp Application qua lớp Session, chuyển dữ liệu sang gói tin TCP hoặc UDP. Lớp này sẽ chia nhỏ dữ liệu nếu cần. Ngoài ra lớp Transport cũng sẽ kiểm tra lỗi và khôi phục dữ liệu khi cần thiết.<br />
**Các giao thức:** TCP, UDP,...
#### 5. Lớp Network
Lớp Network có hai trách nhiệm chính:
- Một là cung cấp địa chỉ IP để xác định máy chủ và mạng chứa máy chủ
- Hai là xác định đường dẫn tốt nhất dẫn đến máy đích và truyền dữ liệu sao cho phù hợp.<br />
**Các giao thức:** IP, ICMP, IGMP, IPX, BGP,...
#### 6. Lớp Data-Link
Lớp này được chia thành hai lớp con là:
- Lớp Logical Link Control, đảm bảo các giao thức như IP có thể hoạt động được với mọi công nghệ vật lý được cung cấp
- Lớp Media Access Control, điều khiển các thiết bị sử dụng liên kết vật lý.<br />
**Các giao thức:** Ethernet, Token ring, HDLC,...
#### 7. Lớp Physical
Chịu trách nhiệm điều khiển tín hiệu và truyền các bit đến thiết bị vật lý.
<br/>-----------------------------------------------------------------------------------------------------------------------<br/>
## Mô hình TCP/IP
Tương tự như mô hình OSI, mô hình TCP/IP là mô hình phân lớp, nhưng chỉ gồm 4 lớp thay vì 7 lớp của mô hình OSI.

### Các lớp của mô hình TCP/IP

<img src="https://4.bp.blogspot.com/-z3ks4An958s/V8lG64oSsbI/AAAAAAAAANQ/9Ear_1_rr9Q1xdwq4LI8l-BPAtpgv592ACLcB/s1600/3.png" />

#### 1. Lớp Application
Lớp Application trong mô hình TCP/IP đã được tích hợp thêm các chức năng của lớp Presentation và lớp Session trong mô hình OSI. Như vậy, chức năng của lớp này bao gồm các việc về cung cấp giao thức cho ứng dung, biểu diễn, mã hóa thông tin và điều khiển phiên.
#### 2. Lớp Transport
Chịu trách nhiệm quản lý việc truyền dữ liệu, kiểm tra lỗi, phân mảnh và lưu lượng.
#### 3. Lớp Internet
Chịu trách nhiệm giải quyết các vần đề về truyền tải gói tin trong mạng đơn hay liên mạng.
#### 4. Lớp Network Access
Truyền gói tin từ tầng mạng tới các máy chủ khác nhau.
<br/>-----------------------------------------------------------------------------------------------------------------------<br/>
## Cấu trúc các gói tin

### Gói tin TCP
Bao gồm hai phần:
#### Header:
![](http://www.informit.com/content/images/chap3_0672323516/elementLinks/03table01.gif)
<br/>
<ul>
	<li> Source port: Cổng tại máy gửi</li>
	<li> Destination port: Cổng tại máy nhận </li>
	<li> Sequence Number: Nếu cờ SYN bật thì nó là số thứ tự gói ban đầu và byte đầu tiên được gửi có số thứ tự này cộng thêm 1. Nếu không có cờ SYN thì đây là số thứ tự của byte đầu tiên. </li>
	<li> Acknowledgement number: Nếu cờ ACK bật thì giá trị của trường chính là số thứ tự gói tin tiếp theo mà bên nhận cần. </li>
	<li> Data offset: Trường có độ dài 4 bit quy định độ dài của phần header (tính theo đơn vị từ 32 bit). Phần header có độ dài tối thiểu là 5 từ (160 bit) và tối đa là 15 từ (480 bit). </li>
	<li> Reserved</li>
<li> Flag
<ul>
<li> URG: cho trường Urgent pointer </li>
<li> ACK: cho trường Acknowledgement </li>
<li> PSH: Hàm push</li>
<li> RST: Thiết lập lại đường truyền </li>
<li> FIN: Không gửi thêm số liệu </li>
</ul>
</li>
<li> Window: Số byte có thể nhận bắt đầu từ giá trị của trường báo nhận (ACK) </li>
<li> Checksum: Số byte có thể nhận bắt đầu từ giá trị của trường báo nhận (ACK). Dùng cho việc kiểm tra lỗi của phần header và phần dữ liệu </li>
<li>  Options: Đây là trường tùy chọn. Nếu có thì độ dài là bội số của 32 bit. </li>
</ul>
#### Data:
Giá trị của trường này là thông tin dành cho các tầng trên (trong mô hình 7 lớp OSI). Thông tin về giao thức của tầng trên không được chỉ rõ trong phần header mà phụ thuộc vào cổng được chọn.
<br/>
### Gói tin UDP
####Header:
<ul>
<li>Source Port: xác định cổng của người gửi thông tin và  nhận thông tin phản hồi từ người nhận. Nếu không dùng đến thì đặt nó bằng 0.</li>
<li>Destination Port: Trường xác định cổng nhận thông tin, và trường này là cần thiết.</li>
<li>Length: Trường có độ dài 16 bit xác định chiều dài của toàn bộ datagram: phần header và dữ liệu. Chiều dài tối thiểu là 8 byte khi gói tin không có dữ liệu, chỉ có header.</li>
<li>Checksum: Kiểm tra lỗi của phần header và đata.</li>
</ul>
