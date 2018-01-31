# I. Sử dụng tcpdump để bắt gói tin

## 1. Giới thiệu:
`tcpdump:` 
- Là công cụ CLI để phân tích các gói dữ liệu mạng
- Cho phép chặn và hiển thị các gói tin đến hoặc đi trên một mạng mà máy tính có tham gia.
- Có thể lưu ra file và đọc bằng Wireshark.

## 2. Sử dụng tcpdump:
### 2.1. Xem các interface đang hoạt động:
```
tcpdump -D
```
Câu lệnh sẽ liệt kê các giao diện mạng đang hoạt động trên host:

<img src="https://drive.google.com/open?id=1H8V1mVz8sQrP8b46RlPAYOjA1A4Yq13X" />

### 2.2. Bắt gói tin trên Interface
```
tcpdump -i <INTERFACE>
```
Ví dụ, bắt gói tin trên card `enp0s3`
        
<img src="https://drive.google.com/open?id=1H8V1mVz8sQrP8b46RlPAYOjA1A4Yq13X" />
    
Bấm tổ hợp phím `Ctrl` + `C` để dừng.
Sau khi dừng, bảng thống kê gói tin hiện ra với các thông số:
- **Packet capture**: số lượng gói tin bắt được và xử lý.
- **Packet received by filter**: số lượng gói tin được nhận bởi bộ lọc.
- **Packet dropped by kernel**: số lượng packet đã bị dropped bởi cơ chế bắt gói tin của hệ điều hành.

### 2.3. Bắt n gói tin với tùy chọn -c
Mặc định, `tcpdump` sẽ bắt liên tiếp các gói tin. Để dừng quá trình này, chúng ta phải thao tác tổ hợp phím `Ctrl` + `C`.
Sử dụng tùy chọn `-c`, chúng ta có thể giới hạn số lượng gói tin sẽ được bắt:
```
tcpdump -c n -i enp0s3
```
