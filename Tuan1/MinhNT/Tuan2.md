#Day 1: Tìm hiểu hoạt động các thiết bị: Firewall, Router, Switch, Load Balancer, Proxy, VPN, IDS/IPS, Application Firewall.
----
##I-Firewall: 
> Hệ thống Firewall sử dụng để tạo rào chắn cho một mạng cần được bảo vệ đối với những mạng khác. Hệ thống này sẽ giữ lại các gói tin đi vào và đi ra khỏi mạng này, phân tích chúng để cho phép chúng đi qua hoặc hủy bỏ dựa trên một chính sách bảo vệ mà mạng đã thiết lập từ trước. Có thể hiểu đơn giản Firewall dùng để bảo vệ một mạng của một tổ chức khi mạng này được kết nối với các mạng khác :D

Firewall kiểm soát sự kết nối giữa mạng cần bảo vệ với các mạng ngoài. Mục đích của Firewall là:
- Chống lại các cuộc tấn công định tuyến nguồn và gửi lại các đường dẫn định tuyến tới các site dàn xếp thông qua giao thức ICMP.
- Để giới hạn các truy cập với mạng ngoài.
- Tăng độ riêng tư và an toàn cho tài nguyên mạng.

**Chức năng của Firewall:**
1. Điều khiển truy nhập:
Firewall kiểm soát và điều khiển các truy cập, chỉ cho phép những người dùng hợp lệ có quyền truy cập đến tài nguyên của mạng mà người dùng đó cần. Firewall phải hiểu được tất cả các dịch vụ và các ứng dụng đang hoạt động trên mạng.

2. Theo dõi truy nhập: 
Firewall có thể theo dõi, hiển thị, báo cáo về những lưu thông mạng mà nó điều khiển, người dùng có thể theo dõi kết nối theo thời gian thực, ngắt hoặc chặn các kết nối đó.

3. Ghi lại quá trình làm việc:
Firewall có thể tính toán về các thông tin truy nhập hay mọi kết nối một cách chi tiết: user, service, thời gian bắt đầu kết nối, đích đến,....

4. Cảnh báo an ninh: 
Firewall có thể đưa ra nhiều tùy chọn để cảnh báo qua Email hay sử dụng giao thức SNMP để gửi các cảnh báo an ninh tới các hệ thống quản trị mạng.

5. Ngăn chặn các kiểu tấn công như:
- IP Spoofing (giả mạo địa chỉ IP): dựa trên sự giả mạo địa chỉ IP của một router hoặc máy chủ để thu được quyền truy cập tới các tài nguyên được bảo vệ.
Các Gateway sẽ ngăn chặn kiểu tấn công mạo danh IP bằng cách hạn chế truy nhập mạng dựa trên giao diện mạng của Gateway, không cho các hoạt động thu nhận tin từ giao diện đó.
- DOS-Denial of service (tấn công phong tỏa dịch vụ): đây là một tập các cuộc tấn công có chủ đích nhằm ngăn chặn một máy tính đang cung cấp các dịch vụ cho những người sử dụng hợp pháp. Firewall sẽ kiểm tra số lượng yêu cầu dịch vụ tới một máy chủ nào đó và thực hiện từ chối cung cấp dịch vụ khi số lượng này vượt quá một giới hạn cho phép nào đó.
- Tấn công mạng LAN (LAN attack): nếu kẻ tấn công gửi các gói SYN giả tạo chứa địa chỉ IP nguồn và đích cho nạn nhân, nạn nhân đó gửi các gói tin SYN-ACK cho chính bản thân mình, từ đó tạo ra các kết nối không được sử dụng chiếm khoảng trống đến khi hết thời gian. 
Firewall có thể chống lại các cuộc tấn công mạng LAN bằng cách kết hợp sự bảo vệ chống lại SYS Flood và IP Spoofing.
----

**Phân loại Firewall:**
1. Packet Filtering Firewall - Firewall lọc gói:
Đây là thế hệ đầu phân tích về tầng giao vận trong các gói tin IP của mạng. 
Firewall lọc gói cho pháp các thao tác truyền dữ liệu trên các điều khiển sau:
- Giao diện vật lý mà gói tin đã đến từ đó.
- Địa chỉ IP nguồn của gói tin.
- Địa chỉ IP đích của gói tin.
- Kiểu tầng vận chuyển: TCP, UDP, ICMP.
- Cổng nguồn & cổng đích tầng vận chuyển.
...
Việc kiểm tra gói tin trên mạng một cách đầy đủ gắn với thuật toán thông thường sau:
- Nếu không tìm thấy một quy tắc nào thích hợp thì bỏ gói tin đó.
- Nếu tìm thấy một quy tắc thích hợp, cho phép truyền thông tin ngang hàng.
- Nếu tìm thấy một quy tắc từ chối thông tin thì bỏ gói tin đó.

Firewall lọc gói không kiểm tra dữ liệu tầng ứng dụng của gói tin và không theo dõi trạng thái kết nối nên giải pháp này kém an toàn nhất trong các công nghệ Firewall. Tuy nhiên, vì nó xử lý ít hơn so với các kĩ thuật Firewall khác nên nó là công nghệ nhanh nhất hiện có và thường được thực hiện trong các giải pháp phần cứng như bộ định tuyến IP.
Các Firewall lọc gói thường thay địa chỉ cho các gói tin để luồng thông tin đi ra có địa chỉ nguồn khác với địa chỉ của máy trạm nội bộ, che giấu cách đánh địa chỉ của mạng cần bảo vệ.

Firewall lọc gói có các ưu điểm sau:
- Cài đặt và vận hành đơn giản.
- Nhanh hơn các kỹ thuật firewall khác và có thể dễ dàng thực hiện như các giải pháp phần cứng.
- Các bộ lọc gói không yêu cầu các máy tính sử dụng dịch vụ phải được cấu hình một cách đặc biệt; chúng làm tất cả các công việc này.
- Khi kết hợp với chuyển dịch địa chỉ, có thể dùng các Firewall lọc gói để che giấu các địa chỉ IP nội bộ.

Nhược điểm của Firewall lọc gói:
- Là điểm yếu cho các cuộc tấn công được chỉ định ở các giao thức cao hơn giao thức lớp mạng - giao thức duy nhất nó hiểu được.
- Không hiểu các giao thức ở tầng ứng dụng nên không hạn chế truy cập đối với giao thức lớp con cho đến cả các dịch vụ cơ bản nhất; nên kém an toàn hơn các Firewall mức kết nối và ứng dụng.
- Không thể cất giấu topo mạng riêng và phơi bày mạng riêng cho thế giới bên ngoài.
- Các bộ lọc gói không quản lý được thông tin về trạng thái và không giữ được thông tin về phiên làm việc hoặc thông tin nhận được từ ứng dụng. 
- Các bộ lọc gói bị hạn chế về khả năng xử lý thông tin trong gói tin. Do đó, nó có thể cho phép một số dịch vụ có điểm yếu bảo mật đi qua, thông qua lỗ hổng thì virus có thể làm tê liệt hệ thống.
- Các bộ lọc gói không hạn chế thông tin nào được truyền từ các máy tính nội bộ thông qua các dịch vụ máy chủ trên máy chủ Firewall. Các bộ lọc gói chỉ hạn chế thông tin nào có thể đi tới nó, vì vậy kẻ xâm nhập có thể truy cập tới dịch vụ trên máy chủ firewall.
- Kỹ thuật lọc gói có rất ít hoặc không có khả năng thống kê sự kiện và cơ chế báo động.
- Gặp khó khăn trong việc kiểm tra quy tắc chấp nhận & từ chối vì sự phức tạp trong việc hỗ trợ các dịch vụ mạng.

2. Circuit Level Firewall (Firewall mức kết nối):
Đây là thế hệ thứ 2, xác nhận tính hợp lệ của một gói tin là yêu cầu kết nối hoặc gói tin dữ liệu thuộc về một kết nối (hoặc kết nối ảo) giữa 2 tầng giao vận tương đương.
Để phê chuẩn một phiên làm việc, Firewall mức kết nối kiểm tra thiết lập kết nối để đảm bảo rằng kết nối này tạo ra một thủ tục bắt tay hợp lệ cho giao thức tầng giao vận đang được sử dụng (điển hình như TCP). Các gói tin dữ liệu sẽ không được gửi cho đến khi thủ tục bắt tay được hoàn thành. 
Mỗi lần một kết nối kết thúc thì mục chứa thông tin về kết nối này trong bảng kết nối ảo sẽ bị xóa và kết nối ảo giữa hai tầng giao vận tương đương cũng bị đóng. Khi một kết nối được thiết lập, Firewall mức kết nối thường lưu giữ các thông tin về kết nối sau:

- Nhận dạng phiên làm việc duy nhất đối với kết nối này, được sử dụng cho các mục đích theo dõi, giám sát.
- Trạng thái của kết nối: đang bắt tay, đã thiết lập hay kết thúc.
- Thông tin thứ tự của các gói tin.
- Địa chỉ IP nguồn (địa chỉ gói dữ liệu được gửi đi).
- Địa chỉ IP đích (địa chỉ đến của gói dữ liệu).
- Giao diện vật lý mà gói dữ liệu đến từ đó.
- Giao diện vật lý mà gói dữ liệu sẽ đi qua nó để đi ra.

Sử dụng thông tin này, Firewall mức kết nối kiểm tra thông tin trong phần header của mỗi gói tin để xác định xem liệu máy tính có được phép gửi dữ liệu tới máy tính nhận hay không và máy tính có quyền nhận hay không.
....
Các Firewall mức kết nối có những ưu điểm sau:
- Nhanh hơn các Firewall mức ứng dụng vì chúng thực hiện việc đánh giá gói tin ít hơn.
- Có thể bảo vệ toàn bộ mạng bằng cách ngăn các kết nối giữa địa chỉ nguồn cụ thể từ mạng Internet với các kết nối giữa địa chỉ nguồn cụ thể từ mạng Internet với các máy tính ở mạng trong.
- Bằng việc kết hợp với dịch chuyển địa chỉ, ta có thể sử dụng Firewall mức kết nối để che địa chỉ IP của mạng trong đối với người dùng mạng ngoài.

Nhược điểm của Firewall mức kết nối:
- Firewall mức kết nối không hạn chế theo các nhóm con của TCP.
- Firewall mức kết nối không thể thực hiện được kiểm tra an ninh một cách chặt chẽ đối với giao thức lớp cao hơn khi có yêu cầu.
- Do chỉ xây dựng được một số kiểu nhất định của trạng thái phiên làm việc, các Firewall mức kết nối chỉ có thể thống kê gói dữ liệu theo thuộc tính đã có từ trước của giao thức tầng ứng dụng mà không thể thống kê theo các thuộc tính bổ sung thêm về sau.
- Các Firewall mức kết nối không đưa thêm các tính năng đánh giá, bổ sung như: lưu giữ tạm thời đối tượng HTTP, lọc theo URL và tính năng xác thực. Vì chúng không hiểu các giao thức đang được sử dụng và không phân biệt các giao thức này.
- Khó có thể kiểm tra quy tắc chấp nhận - từ chối.

3. Application layer Firewall (Firewall mức ứng dụng):
Là công nghệ thế hệ thứ 3, cung cấp điều khiển tại lớp ứng dụng nên hoạt động giống như mức ứng dụng.
Với khả năng kiểm tra chi tiết sự lưu thông, độ an toàn của Firewall múc ứng dụng cao hơn so với Firewall lọc gói tin nhưng đồng thời cũng làm cho Firewall này chậm hơn. Nó kiểm tra tính hợp lệ của các gói dữ liệu tại tầng ứng dụng trước khi cho phép thực hiện một kết nối. Nó kiểm tra tất cả các gói tin tại tầng ứng dụng và duy trì thông tin về trạng thái kết nối đầy đủ và thông tin về thứ tự.
Ngoài ra, một Firewall mức ứng dụng còn có thể phê chuẩn các mục bảo vệ an ninh khác mà nó chỉ xuất hiện trong tầng ứng dụng.
...
Giống như các Firewall mức kết nối, các Firewall mức ứng dụng có thể thực hiện các kiểm tra bổ sung để đảm bảo rằng các gói tin không bị giả mạo và chúng thường thực hiện chuyển dịch địa chỉ mạng.

Các dịch vụ ủy quyền có một số ưu điểm sau:
- Dễ cấu hình hơn các Firewall lọc gói tin.
- Có thể giấu topo mạng riêng.
- Các dịch vụ ủy quyền có thể áp đặt điều khiển được đối với các giao thức lớp cao, chẳng hạn HTTP và FTP.
- Các dịch vụ ủy quyền lưu giữ các thông tin về các cuộc liên lạc thông qua server Firewall. Chúng có thể cung cấp một phần trung tâm trạng thái hoặc toàn bộ thông tin trạng thái nhận được từ các cuộc liên lạc, và một phần thông tin về phiên làm việc.
- Các dịch vụ ủy quyền có thể được sử dụng để từ chối truy cập đối với các dịch vụ nào đó, trong khi cho phép truy nhập tới các dịch vụ khác.
- Các gói dịch vụ ủy quyền có khả năng xử lý và thao tác dữ liệu gói.
- Các dịch vụ ủy quyền che giấu địa chỉ IP mạng trong đối với mạng ngoài, không cho phép liên lạc trực tiếp giữa các server bên ngoài và máy tính nội bộ.
- Có thể dẫn đường cho các dịch vụ nội bộ, cũng như các yêu cầu từ mạng ngoài đến mạng trong, hoặc tới một nơi nào đó.
- Các dịch vụ ủy quyền có thể cung cấp các tính năng bổ sung: lưu giữ tạm thời đối tượng HTTP, lọc URL, xác thực người dùng.
- Cho phép người quản trị giám sát sự cố thẻ vi phạm các chính sách bảo vệ an ninh.

Nhược điểm:
- Các dịch vụ ủy quyền yêu cầu thay đổi ngăn xếp mạng vốn có của server Firewall.
- Vì các proxy server chờ nhận trên cổng cùng với các server cung cấp dịch vụ đó nên không thể chạy các server này trên Firewall.
- Các dịch vụ ủy quyền có một độ trễ khi thực hiện. Dữ liệu phản hồi bị xử lý hai lần, bởi ứng dụng và proxy của nó.
- Các Firewall mức ứng dụng không thể cung cấp các proxy những giao thức UDP, RPC và những dịch vụ khác sử dụng giao thức này.
- Các dịch vụ ủy quyền thông thường yêu cầu một số thay đổi đối với các client hoặc các thủ tục của client, vì vậy cần phải có thêm những xử lý cấu hình.
- Các Firewall mức ứng dụng không chú ý tới thông tin chứa trong các lớp thấp hơn các gói. Nếu ngăn xếp mạng không thực hiện chính xác thì một số thông tin được sử dụng để thực hiện các phép kiểm tra an ninh mà các Firewall mức ứng dụng yêu cầu bằng cách sử dụng các lời gọi chuẩn từ các thư viện hệ điều hành có thể trả về thông tin không chính xác.
- Các Proxy server có thể yêu cầu thêm mật khẩu hoặc các thủ tục xác nhận tính hợp lệ khác làm tăng độ trễ của dịch vụ.

4. Dynamic packet filter Firewall (firewall lọc gói động):
Là công nghệ thứ tư, cho phép sửa đổi các chính sách đảm bảo an ninh dựa trên tình huống. Loại công nghệ này có ích trong việc cung cấp sự hỗ trợ nào đó đối với giao thức tầng giao vận UDP. 
Các Firewall này thực hiện chức năng liên kết tất cả các gói UDP đi qua vành đai bảo vệ an ning bằng một kết nối ảo đã được thay đổi và gói tin này được đi qua server Firewall. Thông tin kết hợp với kết nối ảo được lưu giữ trong một khoảng thời gian ngắn, và nếu không nhận được gói tin đáp ứng nào trong khoảng thời gian này, kết nối ảo là không hợp lệ.

Các Firewall lọc gói động có những ưu nhược điểm giống như các Firewall thế hệ thứ nhất trừ một điểm:
- Nó không cho phép tự động gửi các gói tin UDP vào mạng nội bộ.
Chỉ khi các gói tin UDP yêu cầu xuất phát từ mạng nội bộ gửi ra mạng ngoài, server Firewall mới cho phép các gói tin đáp ứng yêu cầu đó đi qua để đến máy trạm đã gửi các yêu cầu. Gói tin đáp ứng được phép đi qua phải có địa chỉ đích phù hợp với địa chỉ nguồn của máy. Cổng đích tầng giao vận phải phù hợp với cổng nguồn và phải cùng kiểu giao thức tầng giao vận.
Tính năng này cho phép các giao thức tầng ứng dụng hoạt động ngang qua vành đai bảo vệ an ninh. Một server DNS nội bộ phải đưa ra các yêu cầu cho các server DNS chạy trên mạng ngoài để lấy thông tin địa chỉ của các trạm mà nó không biết. Các server DNS phải tạo ra các yêu cầu này bằng cách sử dụng một kết nối TCP hoặc một kết nối ảo UDP.

----
**Những hệ thống Firewall trong thực tế:**

---------------------------------------------------

##II-Router: 
>Router là thiết bị mạng hoạt động ở tầng 3 của mô hình OSI-tầng network. Router được chế tạo với 2 mục đích chính:
- Phân cách các mạng máy tính thành các segment riêng biệt để giảm hiện tượng đụng độ, giảm broadcast hay thực hiện chức năng bảo mật.
- Kết nối các mạng máy tính hay kết nối các user với mạng máy tính ở các khoảng cách xa với nhau thông qua các đường truyền thông như điện thoại.

Do hoạt động ở tầng thứ 3 của mô hình OSI, router sẽ hiểu được các protocol quyết định phương thức truyền dữ liệu. Các địa chỉ mà router hiểu là các địa chỉ giả được quy định bởi các protocol. Tùy theo cấu hình, router quyết định phương thức và đích đến của việc chuyển các packet từ nơi này sang nơi khác, theo các bước sau:
- Đọc packet.
- Gỡ bỏ dạng format quy định bởi protocol của nơi gửi.
- Thay thế phần gỡ bỏ đó bằng dạng format của protocol của đích đến.
- Cập nhật thông tin về việc chuyển dữ liệu: địa chỉ, trạng thái của nơi gửi, nơi nhận.
- Gửi packet đến nơi nhận qua đường truyền tối ưu nhất.

**Nguyên tắc hoạt động của Router-ARP Protocol**
Như ta đã biết tại tầng network của mô hình OSI, chúng ta thường sử dụng các loại địa chỉ mang tính quy ước như IP, IPX,...Các địa chỉ này là các địa chỉ có hướng, nghĩa là chúng được phân thành hai phần riêng biệt là phần địa chỉ network và phần địa chỉ host.
Cách đánh số địa chỉ như vậy nhằm giúp cho việc tìm ra các đường kết nối từ hệ thống mạng này sang hệ thống mạng khác được dễ dàng hơn, có thể thay đổi theo tùy ý người sử dụng. Trên thực tế, các card mạng chỉ có thể kết nối với nhau theo địa chỉ MAC, địa chỉ cố định và duy nhất của phần cứng. Do vậy ta phải có một phương pháp để chuyển đổi các dạng địa chỉ này qua lại với nhau. Từ đó ta có giao thức phân giải địa chỉ: Address Resolution Protocol (ARP).

> ARP là một protocol dựa trên nguyên tắc: Khi một thiết bị mạng muốn biết địa chỉ MAC của một thiết bị mạng nào đó mà nó đã biết địa chỉ ở tầng network (IP, IPX…); nó sẽ gửi một ARP request bao gồm địa chỉ MAC address của nó và địa chỉ IP của thiết bị mà nó cần biết MAC address trên toàn bộ một miền broadcast. 
Mỗi một thiết bị nhận được request này sẽ so sánh địa chỉ IP trong request với địa chỉ tầng network của mình. Nếu trùng địa chỉ thì thiết bị đó phải gửi ngược lại cho thiết bị gửi ARP request một packet (trong đó có chứa địa chỉ MAC của mình).

Trong một hệ thống mạng đơn giản, ví dụ như máy A muốn gửi packet đến máy B và nó chỉ biết được địa chỉ IP của máy B. Khi đó máy A sẽ phải gửi một ARP broadcast cho toàn mạng để hỏi xem “địa chỉ MAC của máy có địa chỉ IP này là gì” Khi máy B nhận được broadcast này, có sẽ so sánh địa chỉ IP trong packet này với địa chỉ IP của nó. Nhận thấy địa chỉ đó là địa chỉ của mình, máy B sẽ gửi lại một packet cho máy B trong đó có chứa địa chỉ MAC của B. Sau đó máy A mới bắt đầu truyền packet cho B

https://imgur.com/a/hTDST

Trong một môi trường phức tạp hơn: hai hệ thống mạng gắn với nhau thông qua một router C. Máy A thuộc mạng A muốn gửi packet đến máy B thuộc mạng B. Do các broadcast không thể truyền qua router nên khi đó máy A sẽ xem router C như một cầu nối để truyền dữ liệu. 
Trước đó, máy A sẽ biết được địa chỉ IP của router C (port X) và biết được rằng để truyền packet tới B phải đi qua C. Tất cả các thông tin như vậy sẽ
được chứa trong một bảng gọi là bảng routing (routing table). Bảng routing table theo cơ chế này được lưu giữ trong mỗi máy. Routing table chứa thông tin về các gateway để truy cập vào một hệ thống mạng nào đó. Ví dụ trong trường hợp trên trong bảng sẽ chỉ ra rằng để đi tới LAN B phải qua port X của router C. Routing table sẽ có chứa địa chỉ IP của port X. Quá trình truyền dữ liệu theo từng bước sau:
- Máy A gửi một ARP request (broadcast) để tìm địa chỉ MAC của port X.
- Router C trả lời, cung cấp cho máy A địa chỉ MAC của port X.
- Máy A truyền packet đến port X của router.
- Router nhận được packet từ máy A, chuyển packet ra port Y của router. Trong packet có chứa địa chỉ IP của máy B.
- Router sẽ gửi ARP request để tìm địa chỉ MAC của máy B.
- Máy B sẽ trả lời cho router biết địa chỉ MAC của mình.
- Sau khi nhận được địa chỉ MAC của máy B, router C gửi packet của A đến B.
https://imgur.com/a/kY0eV