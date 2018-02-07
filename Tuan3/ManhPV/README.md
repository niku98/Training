# Bản báo cáo tuần 3


### Mục lục
1. [Linux](#linux-start)
- [Linux là gì?](#what-is-linux)
- [Một số Distro của Linux](#linux-distro)
- [Ưu nhược điểm của Linux](#linux-dis-advantages)
- [Ưu điểm](#linux-advantages)
- [Nhược điểm](#linux-disadvantages)
- [Phân quyền trong Linux](#linux-user-role)
- [Các quyền của user](#linux-roles)
- [Cách xem quyền của File - Folder](#linux-view-role)

***
## I/Linux
### <a name="linux-start"></a> 1. Linux là gì?
**Linux** là tên một *hệ điều hành* máy tính dựa trên **Unix** được phát triển và phân phối qua mô hình phần mềm tự do mã nguồn mở.

Đồng thời, **Linux** cũng là tên của một *nhân hệ điều hành*, ra đời bản đầu tiên vào tháng 8 năm 1991 bởi **Linus Torvalds**. Nhiều người gọi **Linux** là **GNU/Linux**, lý do là bản thân **Linux** chỉ là phần nhân hệ điều hành. Rất nhiều phần mềm, ứng dụng khác như hệ thống đồ họa, trình biên dịch, soạn thảo, các công cụ phát triển cũng cần được *gắn vào nhân* để tạo nên một HĐH hoàn chỉnh. Hầu hết những phần mềm này được phát triển bởi cộng đồng *GNU*.

**Unix** ban đầu được phát triển từ năm 1969 bởi một nhóm kỹ sư ở Bell Labs trực thuộc cty AT&T, gồm **Ken Thompson**, **Dennis Ritchies**, **Douglas Mcllroy** và **Joe Ossanna**. Bản phát hành lần đầu ra mắt năm 1970. Có vài phiên bản **Unix** trên thị trường như **Solaris Unix**, **AIX**, **HP Unix**, **BSD**... **Linux** cũng là một bản của **Unix** được cung cấp miễn phí. **Unix** có khả năng đa người dùng (vài người có thể dùng máy tính chạy **Unix** tại cùng một thời điểm) và đa nhiệm (chạy nhiều chương trình một lúc). Được viết bằng ngôn ngữ C nên **Unix** có thể cài đặt trên nhiều loại máy tính khác nhau, đây là *tính khả chuyển*.

#### <a name="linux-distro"></a> Một số Distro của Linux

- **Ubuntu**
- **Fedora**
- **LinuxMint**
- **OpenSUSE**
- **PCLinuxOS**
- **Debian**
- **Mandriva**

### <a name="linux-dis-advantages"></a> 2.Ưu nhược điểm của Linux

#### <a name="linux-advantages"></a> a. Ưu điểm
- **Linh hoạt:** **Linux** là mã nguồn mở nên ta có thể tùy ý chỉnh sửa các *hệ điều hành* sử dụng nhân **Linux** để phù hợp với nhu cầu cá nhân.
- **Bảo mật cao:** Hệ thống phân quyền của **Linux** cực tốt. Ngoài ra, vì **Linux** là mã nguồn mở nên khi có bất kì lỗi nào được phát hiện, nó sẽ được cả cộng đồng sửa lỗi.

#### <a name="linux-disadvantages"></a> b. Nhược điểm
- **Thiếu thân thiện với người dùng:** Do hầu hết các mọi việc trên **Linux** đều thực hiện qua dòng lệnh(Command line), nên việc người dùng phổ thông có thể sử dụng được **Linux** là một điều khó khăn.
- **Tính thống nhất:** Do **Linux** là mã nguồn mở nên ai cũng có thể chỉnh sửa và phát hành một phiên bản lên *Internet*. Điều này khiến người dùng phải mất một thời gian tìm hiểu để lựa chọn một phiên bản phù hợp với nhu cầu, nhất là với người dùng không có nhiều kiến thức - kinh nghiệm.
- **Phần cứng:** Có nhiều nhà sản xuất phần cứng không hỗ trợ driver chạy trên **Linux**. Do đó, sẽ có những thiết bị - phần cứng không thể chạy trên **Linux**.

### <a name="linux-user-role"></a> 3. Phân quyền trong Linux
#### <a name="linux-roles"></a> a. Các quyền của user
- **Read(r : 4):**
- **Files:** quyền được *xem* nội dung của *file*.
- **Folders:** quyền được *xem* danh sách các 	*subfolder* và file bên trong *folder* đó.
- **Write(w : 2):**
- **Files:** quyền *thêm*, *sửa* nội dung file.
- **Folders:** quyền *thêm*, *xóa* một *subfolder* hay *file* trong *folder* đó.
- **Excute(x : 1):**
- **Files:** cho phép thực thi *file*, nếu là *file* **program** hay **script**.
- **Folders:** cho phép **cd** vào *folder* này.
- **Deny(- : 0):** **Không** có quyền làm một **thao tác** gì đó đối với một **file** hay **folder** xác định.

#### <a name="linux-view-role"></a> b. Xem phân quyền của file, folder
Sử dụng lệnh ```ls -la``` để liệt kê danh sách *file* và *subfolder* trong **folder** hiện hành.

![](https://viblo.asia/uploads/9958476f-bc2d-41e0-9ddf-204c8bfc50ed.png)
<br/>

##### Cách xem:
- Cột đầu gồm 10 ký tự:
- Ký tự đầu cho biết kiểu file: **d** là *folder*, **-** là *file*.
- 9 ký tự sau chia làm **3 phần**, mỗi phần 3 ký tự:
- **Phần 1:** Cho biết quyền của **user** sở hữu (**Owner**).
- **Phần 2:** Cho biết quyền của **group** sở hữu (**Owner group**).
- **Phần 3:** Cho biết quyền của các **user** khác.
- Cột hai gồm 1 số:
- **Folder:** Cho biết số lượng *subfolder* + *parentfolder* + chính nó.
- **File:**  Cho biết số đường dẫn cố định đến nó.
- Cột 3: Cho biết **Owner** - người sở hữu.
- Cột 4: Cho biết **Owner group** - nhóm sở hữu.
- Cột 5: Cho biết dung lượng *file*(*folder*).
- Cột 6: Thời gian tạo.
- Cột 7: Tên *file*(*folder*).

#### <a name="linux-change-role"></a> c. Thay đổi quyền.
Chỉ *User* có quyền **root** hoặc **Owner User** mới có thể thay đổi quyền có *file*, *folder* đó.

Để thay đổi quyền của *file* hay *folder*, ta dùng lệnh:<br/> ```chmod <mode> file_name```

**Mode** có thể viết theo hai cách:
>**Symbolic:** ```chmode [group][operator][permission] file_name```

**Grouop:**

| Group Permision | Symbolic     | Description     |
| :------------- | :------------- | :------------- |
| Owner       | u       | 	Người sở hữu	|
| Group       | g       |	Nhóm sở hữu	|
| Other       | o       |	Người khác	|
| All         | a       |		Tất cả	|

**Operator:**

| Operator | Symbolic     | Description     |
| :------------- | :------------- | :------------- |
| Add       	| +       | 	Thêm quyền		|
| Remove       	| -       |	Loại bỏ quyền		|
| Assign       	| =       |		Chỉ định quyền	|

**Permision:**

| Permision | Symbolic     | Description     |
| :------------- | :------------- | :------------- |
| Read       	| r       | 	Quyền đọc													|
| Write       	| w       |	Quyền ghi														|
| Excute       	| x       |		Quyền thực thi 												|
| Setuid/Setgid | s       |		Người thực thi là người sở hữu thay vì người sử dụng lệnh	|
|        		| S       |		Tương tự với Setuid/Setgid nhưng file không thể thực thi	|
| Sticky       	| t       |		**Owner User** (hoặc root) mới được phép xóa hoặc thay đổi tên file	|

> **Octal Mode:**
