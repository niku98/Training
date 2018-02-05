# 1. Sử dụng tcpdump để bắt và phân tích gói tin

## 1.1. Giới thiệu:
**`tcpdump:`**
- Là công cụ CLI để phân tích các gói dữ liệu mạng
- Cho phép chặn và hiển thị các gói tin đến hoặc đi trên một mạng mà máy tính có tham gia.
- Có thể lưu ra file và đọc bằng công cụ đồ họa Wireshark.

## 1.2. Sử dụng tcpdump:
### 1.2.1. Xem các interface đang hoạt động:
```
tcpdump -D
```
Câu lệnh sẽ liệt kê các giao diện mạng đang hoạt động trên host:

<img src="https://i.imgur.com/rx5do31.png" />

### 1.2.2. Bắt gói tin trên Interface
```
tcpdump -i <INTERFACE>
```
Ví dụ, bắt gói tin trên card `eth0`
        
<img src="https://i.imgur.com/B3DFgv0.png" />
    
Bấm tổ hợp phím `Ctrl` + `C` để dừng.
Sau khi dừng, bảng thống kê gói tin đã bắt hiện ra với các thông số:
- **Packet capture**: số lượng gói tin bắt được và xử lý.
- **Packet received by filter**: số lượng gói tin được nhận bởi bộ lọc.
- **Packet dropped by kernel**: số lượng packet đã bị dropped bởi cơ chế bắt gói tin của hệ điều hành.

<img src="https://i.imgur.com/1eNdjDk.png" />

### 1.2.3. Bắt n gói tin với tùy chọn -c
Mặc định, `tcpdump` sẽ bắt liên tiếp các gói tin. Để dừng quá trình này, chúng ta phải thao tác tổ hợp phím `Ctrl` + `C`.
Sử dụng tùy chọn `-c`, chúng ta có thể giới hạn số lượng gói tin sẽ được bắt:
```
tcpdump -c n -i <INTERFACE>
```
***- Với n là số gói tin cần bắt.***

Ví dụ bắt `5` gói tin trên card `eth0`:

<img src="https://i.imgur.com/zst4UKN.png" />

### 1.2.4. Lưu file .pcap (Wireshark)
```
tcpdump -i <INTERFACE> -w <path>
```
Ví dụ bắt `5` gói tin trên card `eth0` và lưu vào đường dẫn `/opt/capture1.pcap` :

<img src="https://i.imgur.com/CUq8aI9.png" />

### 1.2.5. Chỉ bắt các gói TCP

```
tcpdump -i <INTERFACE> tcp
```
Ví dụ bắt `5` gói tin TCP trên card `eth0`:

<img src="https://i.imgur.com/Do1nFY4.png" />

Ngoài TCP, chúng ta có thể bắt theo UDP, IMCP,...

### 1.2.6. Bắt các gói theo `port`
```
tcpdump -i <INTERFACE> port <port_number> -n
```
- `-n`: Hiển thị số port thay cho tên giao thức, IP thay cho Hostname.

Ví dụ bắt `5` gói tin qua cổng `443` trên card `eth0` :

<img src="https://i.imgur.com/v3cXrqE.png" />

### 1.2.7. Bắt theo địa chỉ nguồn hoặc đích

- ***Địa chỉ nguồn:***

```
 tcpdump -i <INTERFACE> src <source_IP>
```
Ví dụ bắt `5` gói tin từ IP nguồn `10.1.62.65` trên card `eth0` :

<img src="https://i.imgur.com/7Wmgb1p.png" />

- ***Địa chỉ đích:*** 

```
 tcpdump -i <INTERFACE> dst <destination_IP>
```

Ví dụ bắt `5` gói tin đến IP đích `172.217.161.174` trên card `eth0` :

<img src="https://i.imgur.com/odjBizN.png" />

 # 2. Sử dụng Wireshark để bắt và phân tích gói tin
 
 ## 2.1. Giới thiệu:
**`Wireshark:`**
-  Là một ứng dụng phân tích dữ liệu hệ thống mạng.
-  Có khả năng theo dõi, giám sát các gói tin theo thời gian thực
-  Hiển thị chính xác báo cáo cho người dùng qua giao diện khá đơn giản và thân thiện.
## 2.2. Sử dụng Wireshark:
### 2.2.1. Mở file pcap có sẵn:
Sử dụng Wireshark để mở file Capture1.pcap đã tạo ra sau khi bắt gói tin bằng **`tcpdump`**:

<img src="https://i.imgur.com/X7MA1Wg.png" />

### 2.2.2. Bắt gói tin trên Interface
Khởi động Wireshark, chọn một card mạng. Ví dụ, bắt gói tin trên card `eth0`:
        
<img src="https://i.imgur.com/5OkpueL.png" />
    
Wireshark sẽ liên tục bắt các gói tin đến và đi qua card mạng và liệt kê lên giao diện:

<img src="https://i.imgur.com/zPDYvZd.png" />

Trên giao diện chính, Wireshark hiển thị các thông tin:
- **`Packet List`** : Liệt kê các gói tin đã được capture

<img src="https://i.imgur.com/kIK2Q5V.png" />

- **`Packet Details`:** Hiển thị các thông số chi tiết của gọi tin được chọn

<img src="https://i.imgur.com/MNWcg69.png" />

- **`Packet Bytes`:** Hiển thị gói tin dưới dạng mã Hexa

<img src="https://i.imgur.com/wgOHJ0J.png" />

### 2.2.3. Phân tích gói tin
Gõ tên giao thức gói tin muốn tìm lên bộ lọc, chẳng hạn `http`:

<img src="https://i.imgur.com/nOHmH0K.png" />

Chọn gói tin cần phần tích trong danh sách các gói tin, xem các thông số chi tiết gói tin ở phần **Packet Details**, bao gồm:
- ***Frame:***

<img src="https://i.imgur.com/X2fc2Ja.png" />

- ***Source IP, Destination IP:***

<img src="https://i.imgur.com/RTh4PuQ.png" />

- ***Protocols:***

<img src="https://i.imgur.com/vnbJMuq.png" />

<img src="https://i.imgur.com/rgYwcJc.png" />

<img src="https://i.imgur.com/zYu7kVc.png" />

<img src="https://i.imgur.com/JgCDtsI.png" />

Ở phần **Packet Bytes**, gói tin được hiển thị đầy đủ ở dạng mã Hexa:

<img src="https://i.imgur.com/lhVTj82.png" />

# 3. So sánh và kết luận
## 3.1. So sánh
|               **tcpdump**                  |                    **Wireshark**                     |
|--------------------------------------------|------------------------------------------------------|
|Có khả năng quét và chặn bắt gói tin trên toàn bộ dải mạng mà host tham gia|Chỉ có thể bắt được các gói tin đi qua một interface nhất định của host|
|Giao diện dòng lệnh gây khó khăn cho người dùng trong việc xem và phân tích gói tin|Giao diện đồ họa khiến việc hiển thị và phân tích gói tin trở nên dễ dàng|
|Có nhiều tùy chọn bắt gói tin như: Bắt gói tin theo giao thức, port, địa chỉ nguồn hoặc đích. Có thể giới hạn số lượng gói tin được bắt| Bắt toàn bộ gói tin qua giao diện mạng cho đến khi chọn dừng bắt gói tin. Sau đó phải sử dụng bộ lọc (theo giao thức, port) để tìm kiếm gói tin|

## 3.2. Kết luận
Từ bảng so sánh trên, có thể kết luận rằng: **Nên sử dụng tcpdump để chặn bắt gói tin và ghi file pcap rồi sử dụng Wireshark để hiển thị và phân tích gói tin.**
