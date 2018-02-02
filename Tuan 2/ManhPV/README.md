# Báo cáo tuần 2

### Mục lục
1. [Wireshark](#wireshark-start)
	- [Cài đặt](#setup-wireshark)
	- [Bắt và phân tích gói tin](#capture-wireshark)
		- [Bắt gói tin](#capturing-packets)
		- [Màu sắc gói tin](#packets-color)
			- [Màu mặc định](#default-color)
		- [Lọc gói tin](#filter-packets)
		- [Chi tiết gói tin](#packget-detail)
2. [TCPDump](#TCPDump-start)
	- [Giới thiệu](#introduction)
	- [Cài đặt](#install-tcpdump)
	- [Cơ bản](#tcpdump-basic)
		- [Cấu trúc gói tin](#packet-struct)
	- [Tùy chọn trong TCPDump](#options-tcpdump)
	- [Một số bộ lọc cơ bản](#tcp-filters)
3. [Firewall](#Firewall-start)
	- [Chức năng](#Firewall-function)
	- [Nguyên lý](#Firewall-Principles)

## <a name="wireshark-start"></a>I/ Hướng dẫn sử dụng Wireshark để bắt và phân tích gói tin trong *Network*

Đây là phần mềm được dùng để bắt các gói tin được truyền trong *Network*, từ đó ta phân tích gói tin bắt được, phục vụ cho mục đích nhất định nào đấy. *Wireshark* cũng cung cấp chức năng save, giúp ta lư lại cá gói tin đã bắt được.

### <a name="setup-wireshark"></a> 1.Cài đặt
- Tải Wireshark trong link: https://www.wireshark.org/download.html
- Cài đặt như các phần mêm khác.
<br/>
### <a name="capture-wireshark"></a> 2. Bắt và phân tích gói tin bằng Wireshark
**Trước tiên là phải mở phần mềm lên đã :D**
#### <a name="capturing-packets"></a> a. Bắt gói tin:
- Chọn một *Interface* trong list *Network Interface*:

![](https://www.howtogeek.com/wp-content/uploads/2017/06/ximg_593af0b476165.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.-oQ4eGr04v.png)
<br/>
Sau khi chọn, Wireshark sẽ chuyển sang màn hình hiển thị các gói tin mà nó bắt được trong *Interface* bạn chọn:

![](https://fthmb.tqn.com/5qrzPliIm9ekuq1gy_52XMZFqY8=/768x0/filters:no_upscale()/wireshark-captured-data-panes-59512e265f9b58f0fc7b1f17.png)
<br/>
- Ta có thể dừng viêc bắt gói tin của **Wireshark** bằng cách nhấn vào nút **Stop**

![](https://www.howtogeek.com/wp-content/uploads/2017/06/img_593af1eb85f89.png.pagespeed.ce.fOjs80KNB2.png)
<br/>
#### <a name="packets-color"></a> b. Màu sắc các gói tin
##### <a name="default-color"></a> Một vài màu mặc định
- Màu xanh lá cây là gói tin trong giao thức **TCP**
- Màu xanh da trời nhạt là gói tin trong giao thức **UDP**
- Màu xanh da trời đậm là gói tin trong giao thức **DNS**
- Màu đen là gói tin *có vấn đề* trong giao thức **TCP**

Ta có thể tùy chỉnh màu của các gói tin trong phần **View > Coloring Rules**

![](https://www.howtogeek.com/wp-content/uploads/2017/06/img_593af2ab6427a.png.pagespeed.ce.uiH9_sCEpL.png)
<br/>
#### <a name="filter-packets"></a> c. Lọc gói tin
Nếu bạn cần tìm các gói tin đặc biệt nào đấy, **Wireshark** có hỗ trợ chức năng *Lọc gói tin*, bạn chỉ cần gõ đúng cú pháp *lọc* của **Wireshark** là được, sau đât là 3 cú pháp đơn giản hay được dùng:
- Tìm theo IP nguồn: **ip.src == *IP nguồn***
- Tìm theo IP đích: **ip.dst == *IP đích***
- Tìm theo *Protocol*: ***Protocol cần tìm***

Ngoài những cú pháp sẵn có, bạn có thể tự tạo cú pháp *lọc* mới bằng cách vào menu **Analyze > Display Filters**

![](https://www.howtogeek.com/wp-content/uploads/2017/06/img_593af5afe5e39.png.pagespeed.ce.ZGbuilwR7w.png)
<br/>
#### <a name="packget-detail"></a> d. Kiểm tra chi tiết gói tin
Bạn có thể kiểm tra kĩ hơn các thông tin trong gói tin bằng cách chọn nó. Hai phần màn hình dưới sẽ thay đổi sang thông tin chi tiết của gói tin, bao gồm toàn bộ phần *header* và *data* của gói tin.

![](https://fthmb.tqn.com/5qrzPliIm9ekuq1gy_52XMZFqY8=/768x0/filters:no_upscale()/wireshark-captured-data-panes-59512e265f9b58f0fc7b1f17.png)
<br/><br/>

## <a name="TCPDump-start"></a>II/ Hướng dẫn sử dụng TCPDump để bắt và phân tích gói tin trong *Network*

### <a name="introduction"></a>1. Giới thiệu
Tương tự như *Wireshark*, *TCPDump* cũng là một phần mềm dùng để bắt các gói tin trong *Network*, có điều, công cụ này hiển thị dưới màn hình console(màn hình command line). *TCPDump* có thể lưu lại các lần bắt gói tin vào file pcap để mở lại vào lần sau, có thể dùng cả *Wireshark* để mở.

### <a name="install-tcpdump"></a> 2. Cài đặt
Với hệ điều hành Ubuntu, chạy lệnh sau để cài đặt: ```sudo apt-get install tcpdump```

### <a name="tcpdump-basic"></a> 3. Sử dụng cơ bản
Để bắt đầu bắt các gói tin bằng *TCPDump* ta chạy câu lệnh: **tcpdump**

Khi này, màn hình console sẽ hiển thị ra các gói tin mà *TCPDump* bắt được theo dòng, bao gồm các thông tin của gói tin.

*TCPDump* sẽ bắt liên tục đến khi ta yêu cầu ngắt. Khi ngắt, *TCPDump* sẽ hiện ra 3 thông báo sau:

- **Packet capture:** số lượng gói tin bắt được và xử lý.
- **Packet received by filter:** số lượng gói tin được nhận bởi bộ lọc.
- **Packet dropped by kernel:** số lượng packet đã bị dropped bởi cơ chế bắt gói tin của hệ điều hành.

#### <a name="packet-struct"></a> Cấu trúc chung của một dòng gói tin:
	time-stamp src > dst:  flags  data-seqno  ack  window urgent options
**Chú giải**
- **time-stamp:** Thời gian lúc bắt gói tin
- **src > dst:** IP nguồn và IP đích
- **Flag:**
	- **S:** (SYN) Được sử dụng trong quá trình bắt tay của giao thức TCP.
	- **.** : (ACK) Được sử dụng để thông báo cho máy gửi biết là đã gửi gói tin thành công.
	- **F:** (FIN) Được sử dụng để đóng kết nối TCP.
	- **P:** (PUSH) Thường được đặt ở cuối để đánh dấu việc truyền dữ liệu.
	- **R:** (RST) Được sử dụng khi muốn thiết lập lại đường truyền.
	- **Data-sqeno:** Số sequence number của gói dữ liệu hiện tại.
	- **ACK:** Mô tả số sequence number tiếp theo của gói tin do máy gửi truyền (số sequence number máy nhận mong muốn nhận được)
	- **Window:** Số byte có thể nhận được.
	- **Urgent:** Cho biết dữ liệu khẩn trong gói tin.

### <a name="options-tcpdump"></a>4. Một số tùy chọn trong TCPDump
- **-D :** Liệt kê các *Network Interface* trong máy có thể sử dụng.
- **-i :** Bắt các gói tin trong một *Network Interface* được chỉ định. VD: ```tcpdump -i ens33```
- **-c N :** TCPDump bắt N gói tin, sau đó dừng lại.
- **-n :** Không phân dải IP sang hostname.
- **-nm :** Tương tự **-n** và không phân giải cả portname
- **-v :** Tăng số lượng thông tin nhận được trong gói tin(Có thể dùng **-vv** hay **-vvv**).
- **-s :** Tùy chỉnh kích thước gói tin sẽ lưu lại.
### <a name="tcp-filters"></a> 5. Các bộ lọc cơ bản
- **dst A:** Bắt các gói tin có IP đích là A.
- **src A:** Bắt các gói tin có IP nguồn là A.
- **host A:** Bắt các gói tin có hostname nguồn hoặc đích là A.
- **port A:** Bắt các gói tin có port được chỉ định.
- **less A:** Bắt các gói tin có *length* nhỏ hơn A.
- **greater A:** Bắt các gói tin có *length* lớn hơn A.
- **(ether | ip) broadcast:** Bắt các gói tin *IP broadcast* hoặc *Ether broadcast*.
- **Protocol:** Bắt các gói tin theo *Protocol*.VD: ```tcpdump tcp```
<br/><br/><br/>

## <a name="Firewall-start"></a>III/ Firewall
**Firewall** là một công cụ bảo vệ mạng máy tính từ những tấn công bên ngoài, gồm các thành phần cơ bản sau:
- **Bộ lọc gói (Packet Filter):** làm nhiệm vụ lọc các packet vào / ra khỏi mạng.
- **Proxy Services:** một Server đặc biệt ở giữa Client và Server thực sự làm nhiệm vụ lọc ở mức message mức ứng dụng (application level).
- **Cổng vòng (Circuit-Level Gateway):** chuyển tiếp (relay) các kết nối TCP mà không thực hiện bất kỳ một hành động xử lý hay lọc packet nào.

### <a name="Firewall-function"></a> 1. Chức năng
Chức năng chính của **Firewall** là kiểm soát luồng thông tin từ giữa *LAN* và *Internet*. Thiết lập cơ chế điều khiển dòng thông tin giữa *LAN* và mạng *Internet*:
- Cho phép hoặc cấm  dịch vụ truy cập ra ngoài.
- Cho phép hoặc cấm dịch vụ truy cập vào trong.
- Theo dõi luồng dữ liệu mạng giữa *Internet* và *LAN*.
- Kiểm soát địa chỉ truy cập, cấm địa chỉ truy cập.
- Kiểm soát người sử dụng và việc truy cập của người sử dụng.
- Kiểm soát nội dung thông tin lưu thông trên mạng.

### <a name="Firewall-Principles"></a> 2. Nguyên lý
**Firewall** hoạt động chặt chẽ với giao thức TCI/IP, vì giao thức này cũng làm việc theo thuật toán chia nhỏ dữ liệu thành các packets kèm địa chỉ rồi mới gửi đến đích.

Bộ lọc packet cho phép hay từ chối mỗi packet mà nó nhận đ­ợc. Nó kiểm tra toàn bộ đoạn dữ liệu để quyết định xem đoạn dữ liệu đó có thoả mãn một trong số các luật lệ của bộ lọc packet hay không. Các luật lệ lọc packet dựa trên các thông tin ở phần *Header* của packet, dùng để cho phép truyền các packet đó ở trên mạng:
- Địa chỉ IP nơi xuất phát ( IP Source address)
- Địa chỉ IP nơi nhận (IP Destination address)
- Những thủ tục truyền tin (TCP, UDP, ICMP, IP tunnel)
- Cổng TCP/UDP nơi xuất phát (TCP/UDP source port)
- Cổng TCP/UDP nơi nhận (TCP/UDP destination port)
- Dạng thông báo ICMP ( ICMP message type)
- Giao diện packet đến ( incomming interface of packet)
- Giao diện packet đi ( outcomming interface of packet)

Nếu packet thỏa mãn các luật của Firewall, nó sẽ được cho phép đi qua Firewall, nếu không nó sẽ bị bỏ qua.
