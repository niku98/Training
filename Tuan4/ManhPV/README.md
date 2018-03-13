# Báo cáo tuần 4

## I/ Apache
**Web server** là một phần mềm mã nguồn mở miễn phí được cài đặt trên các máy chủ *web server* để xử lý các yêu cầu gửi tới máy chủ dưới giao thức **HTTP**.
### 1. Apache là gì?
**Apache** là một *web server* được phát triển bởi tổ chức *Apache Software Foundation*.

**Apache** là một trong các *web server* đơn giản nhất và phổ thông nhất để phát triển các dự án website, và là *web server* phổ biến nhất thế giới.

**Apache** là một Web Server được xây dựng theo cấu trúc module, là một tập hợp nhiều thành phần nhỏ được gắn kết với nhau.
![](http://devopshub.net/wp-content/uploads/2013/11/11111111111111.png)

### 2. Apache core
Mọi request từ **Client** lên **Apache server** đều phải thông qua **Apache core** trước tiên, sau đó, sẽ được phân ra các module cần thiết.
**Apache core** bao gồm các thành phần sau:
- **HTTP Prototcol**: giao tiếp trực tiếp với các client thông qua socket bằng giao thức HTTP. Tất cả các công việc trao đổi dữ liệu với client đều do thành phần này đảm trách nhiệm.​

- **HTTP Main**: thành phần làm nhiệm vụ khởi động server và tạo vòng lặp chính để đợi và chấp nhận các kết nối. Đồng thời cũng làm nhiệm vụ quản lý các bộ thời gian timeout.​

- **HTTP Request**: làm nhiệm vụ quản lý các tiến trình xử lý request, đảm bảo chuyển các request tới các module phù hợp theo đúng thứ tự. Ngoài ra, nó còn đảm nhận vai trò quản lý các lỗi xảy ra trên server.​

- **HTTP Core**: triển khai các chức năng cơ bản nhất của Apache.​

- **Alloc**: kiểm soát việc phân chia tài nguyên và lưu trữ các thông tin về sự phân chia đó.​

- **HTTP Config**: xử lý file cấu hình và hỗ trợ cho các virtual host. Đây cũng là nơi liệt kê những module được sử dụng trong Apache.​

![](http://infocom.uniroma1.it/alef/labints/Images/apachearch.gif)

### 3. Cài đặt

Đầu tiên, ta cần cập nhật các repository mới nhất của *Ubuntu*, ta chạy lệnh:
```sh
sudo apt-get update
```
Để cài đặt **Apache**, ta dùng lệnh:
```sh
sudo apt-get install apache2

```
Sau đó, ta cần **Firewall** cho phép **Apache** đi qua.
- Trước tiên, ta cần xem **Apache** đã có trong danh sách ứng dụng của **Firewall** chưa, ta dùng:
```sh
sudo ufw app list
```
Nếu đã cài thành công **Apache**, Ta sẽ nhận được danh sách như sau:
```sh
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
```
- Giờ ta sẽ yêu cầu **Firewall** cho phép **Apache** đi qua bằng lệnh:
```sh
sudo ufw allow 'Apache Full'
sudo ufw allow 'OpenSSH'
```
- Để xác nhận lại **Apache** đã được phép, ta dùng lệnh:
```sh
sudo ufw status
```
Output:
```sh
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
Apache Full                ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
Apache Full (v6)           ALLOW       Anywhere (v6)
```
Có thể dụng lệnh ```systemctl``` để kiểm tra lại xem **Apache** đã hoạt động chưa:
```sh
sudo systemctl status apache2
```
<br/>
### 3. Cấu hình
File cấu hình cho **Apache** được để trong thư mục ```apache2``` theo đường dẫn sau:

**etc/apache2/apache.conf**
#### a. Cấu hình trong file apache.conf
- **Keep alive**
Là một phương thức cho phép sử dụng cùng một kết nối TCP cho một chuỗi các phiên giao dịch HTTP thay vì cứ phải tạo mới từng connection cho mỗi một HTTP Request
![](http://i.imgur.com/yjksohR.png)

Để bật/tắt (Mặc định là bật), ta vào file ```apache.conf```, tìm dòng:
```config
KeepAlive On/Off
```
Để tùy chỉnh lượng kết nối cho phép trong mỗi HTTP Request, ta chỉnh tham số:
```config
MaxKeepAliveRequests 100
```
Tùy chỉnh thời gian chờ cho KeepAlive:
```config
KeepAliveTimeout 5
```
- **HostnameLookups**
Log lại tên của *client* hoặc chỉ địa chỉ *IP* của họ
```config
HostnameLookups Off
```
Ví dụ: localhost(on) - 127.0.0.1(off)

- **ErrorLog**
Tùy chỉnh nơi lưu các lỗi của server, mặc định là:
```config
ErrorLog ${APACHE_LOG_DIR}/error.log
```
#### b. Cài thêm module cho Apache
- **PageSpeed**
	- Công dụng: Giúp tối ưu hóa hiệu suất tải web
	- Tải về module [tại đây](https://dl-ssl.google.com/dl/linux/direct/mod-pagespeed-beta_current_amd64.deb)
	- Sau đó cài đặt module bằng lệnh:
	```sh
	sudo dpkg -i mod-pagespeed-*.deb
	sudo apt-get -f install
	```
- **Security Module**
	- Công dụng: Cung cấp lớp cấu hình bảo mật, qua đó chấp nhận hoặc từ chối các *traffic* dựa trên những quy tắc được set bới quản trị viên.
	- Cài đặt *module* bằng lệnh:
	```sh
	sudo apt-get install libapache2-modsecurity
	```
	- Để bật module, dùng lệnh:
	```sh
	sudo a2enmod mod-security
	```
	![](http://www.webdevcorner.net/wp-content/uploads/2012/11/2012-11-10_18-04-20.png)
<br/>
## II/ NginX
**NginX** là một trong các *web server* mạnh mẽ nhất, có lợi thế về tốc độ và an toàn cho *server website* hơn so với **Apache**, **NginX** hiện nay đang được ưa chuộng để chạy các site lớn.

### 1. Nguyên lý hoạt động

Không giống với các máy chủ web truyền thống, **Nginx** không dựa trên luồn (thread) để xử lý yêu cầu. Thay vào đó, nó sử dụng 1 kiến trúc bất đồng bộ hướng sự kiện linh hoạt . Kiến trúc này sử dụng ít, nhưng quan trọng hợn, là lượng bộ nhớ có thể dự đoán khi hoạt động. Đây chính là điểm mấu chốt khiến **Nginx** là 1 trong số ít những máy chủ được viết để giải quyết vấn đề **C10K** (Chi tiết tại [đây](https://en.wikipedia.org/wiki/C10k_problem))

![](https://cms-assets.tutsplus.com/uploads/users/1160/posts/28540/image/149204501883689.png)

### 2. Cài đặt
- Tải và cài đặt **NginX** trên *Ubuntu*:
```sh
sudo apt-get update
sudo apt-get install nginx
```
- Cấu hình *Firewall*:
	- Xem tên các application của **NginX**:
	```sh
	sudo ufw app list
	```
	Output:
	```sh
	Available applications:
	Nginx Full
	Nginx HTTP
	Nginx HTTPS
	OpenSSH
	```
	- Cấu hình *Firewall*:
	```sh
	sudo ufw allow 'Nginx HTTP'
	```
- Kiểm tra trạng thái của **NginX**:
```sh
systemctl status nginx
```
<br/>
## III/ DNS Server

### 1. Nguyên lý hoạt động

- Khi một request được gửi đi từ *browser*, nó sẽ được phân giải địa chỉ url trong request thành IP và tìm trong cached DNS của client. Nếu tìm thấy, *browser* sẽ sử dụng địa chỉ IP đó để truy cập.

- Nếu không tìm thấy trong cached DNS, địa chỉ IP đó sẽ được tìm kiếm trong DNS Local.

- Trong DNS Local không có, nó sẽ gửi một interative request cho Root DNS và sau đó lần lượt sẽ là Top Level DNS rồi Second Level DNS, cuối cùng chính là IP chính xác của địa chỉ url.

### 2. Cài đặt
#### a. Bind
Là package để cài đặt **DNS Server**.
Để cài đặt **Bind**, ta dùng lệnh:
```sh
sudo apt-get install bind9 bind9utils bind9-doc
```
- Cấu hình **Bind**:
	File cấu hình được để trong đường dẫn ```/etc/bind/named.conf.options```, sử dụng vi để sửa file này:
	```sh
	sudo vi /etc/bind/named.conf.options
	```
