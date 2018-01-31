# 1. Sử dụng tcpdump để bắt gói tin

## 1.1 Giới thiệu:
`tcpdump:` 
- Là công cụ CLI để phân tích các gói dữ liệu mạng
- Cho phép chặn và hiển thị các gói tin đến hoặc đi trên một mạng mà máy tính có tham gia.
- Có thể lưu ra file và đọc bằng công cụ đồ họa Wireshark.

## 1.2 Sử dụng tcpdump:
### 1.2.1 Xem các interface đang hoạt động:
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
*- Với n là số gói tin cần bắt.*

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
- `-n`: Hiển thị số port thay cho tên giao thức, IP thay cho Hostname
Ví dụ bắt `5` gói tin qua cổng `443` trên card `eth0` :

<img src="https://i.imgur.com/v3cXrqE.png" />

### 1.2.7. Bắt theo địa chỉ nguồn hoặc đích

Địa chỉ nguồn: 

```
 tcpdump -i <INTERFACE> src <source_IP>
```
Ví dụ bắt `5` gói tin từ IP nguồn `10.1.62.65` trên card `eth0` :

<img src="https://i.imgur.com/7Wmgb1p.png" />

Địa chỉ đích: 

```
 tcpdump -i <INTERFACE> dst <destination_IP>
```

Ví dụ bắt `5` gói tin đên IP đích `172.217.161.174` trên card `eth0` :

<img src="https://i.imgur.com/odjBizN.png" />
