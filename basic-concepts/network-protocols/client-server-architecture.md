# Client-server architecture

## Kiến trúc Client Server

Hầu hết chúng ta đã quá quen với mạng Internet, nhưng bạn đã bao giờ tự hỏi làm thế nào yêu cầu của chúng ta lấy về đúng kết quả mà nó mong đợi. Nếu bạn muốn biết điều đó, bài viết này là dành cho bạn. Hôm nay, chúng ta sẽ thảo luận về ý tưởng đằng sau mô hình Client Server và làm cách nào để nó hoạt động. Bắt đầu.

### Kiến trúc Client Server là gì?

Kiến trúc client-server là một mô hình ứng dụng phân tán bao gồm nhiều client và nhiều server trong đó, phía server (máy chủ) đảm nhận vai trò lưu trữ, quản lý và phân phối dịch vụ đến cho các client (máy khách). Ở đây các client được kết nối qua một server trung tâm, và giao tiếp trên toàn mạng hay Internet thông qua một mạng máy tính. Bất cứ khi nào client cần một dịch vụ bất kỳ nào, nó sẽ gửi một yêu cầu đến các server, nơi sẽ xử lý yêu cầu và trả về phản hồi cho client.

{% embed url="https://github.com/Ren0503/system-design/raw/master/concepts/network-protocols/assets/client-server.png" %}

### Ví dụ về kiến trúc Client Server

**Ứng dụng chăm sóc sức khỏe**: Một thiết bị máy tính phía client có thể chạy một ứng dụng để nhập thông tin bệnh nhân. Đồng thời, một máy tính phía server có thể chạy một đoạn code khác để có thể truy vấn và quản lý hệ thống cơ sở dữ liệu nơi dữ liệu được lưu trữ.

**Ứng dụng ngân hàng**: Khi một khách hàng truy cập vào dịch vụ ngân hàng thông qua trình duyệt web (client), phía client khởi tạo một yêu cầu đến với web server. Danh tính khách hàng đã đăng nhập được lưu trữ tại một cơ sở dữ liệu và webserver truy cập đến cơ sở dữ liệu như là một client. Sau đó server ứng dụng sẽ trả về dữ liệu chuẩn hóa bằng cách áp dụng các logic nghiệp vụ của ngân hàng và cung cấp output cho webserver. Cuối cùng webserver trả về cho trình duyệt để hiển thị.&#x20;

Tương tự, các ứng dụng như email, WWW đều sử dụng kiến trúc client-server.

### Các thành phần của kiến trúc Client Server

Có bốn thành phần bắt buộc trong kiến trúc client-server: **client**, **server**, **bộ cân bằng tải** và **giao thức mạng**.&#x20;

* **Server**: Là phần mềm chịu trách nhiệm nhận và xử lý các yêu cầu từ client. Nó thường thực thi trên một thiết bị từ xa và có thể truy cập bởi người dùng máy tính nội bộ.
* **Bộ Cân Bằng Tải**: chịu trách nhiệm phân phối các yêu cầu đến trên nhóm server để quản lý lưu lượng và tối ưu tài nguyên sử dụng.
* **Client**: Là phần mềm máy tính thực hiện việc nhận input và gửi yêu cầu đến server. Nó chạy ở phía thiết bị của người dùng hoặc thiết bị từ xa đế kết nối đến server. Nó là phần mềm ứng thực hiện việc yêu cầu tài nguyên hoặc dịch vụ khả dụng từ server. Vd: trình duyệt Web.
* **Giao thức mạng**: mô hình client-server tuân theo theo  khuôn mẫu truyền tải thông tin request-response. Nó giao tiếp bằng giao thức TCP/IP, để phân phối dữ liệu ứng dụng thành các gói tin để có thể phân phối và quản lý luồng điều khiển qua mạng. Mỗi lần một kết nối được thiết lập trong giao thức TCP, nó sẽ được duy trì cho đến khi client và serveer hoàn tất quá trình trao đổi thông tin. Trong khi IP là một giao thức phi kết nối, ở đó mỗi đơn vị dữ liệu độc lập không có kết nối đến các đơn vị dữ liệu khác và được truyền tải trên toàn mạng Internet.

{% embed url="https://github.com/Ren0503/system-design/raw/master/concepts/network-protocols/assets/advanced.png" %}

### Mô hình Client Server hoạt động như thế nào?

Luồng dữ liệu là vô hướng, có thể biểu diễn như một vòng tròn. Khi bắt đầu một client gửi yêu cầu lấy một vài dữ liệu và server sẽ xử lý yêu cầu và gửi phản hồi dữ liệu theo mong muốn của client thông qua một giao thức mạng. Các ứng dụng phía client không thể giao tiếp trực tiếp với nhau. Mô hình phân cấp dữ liệu trong kiến trúc client-server có thể mô tả như sau:

* Client gửi yêu cầu đến server.
* Bộ cân bằng tải sẽ định tuyến yêu cầu đến với server thích hợp.
* Server xử lý yêu cầu và thực hiện truy vấn (đọc, tạo, xóa, sửa) lên cơ sở dữ liệu.
* Cơ sở dữ liệu trả về dữ liệu cho server.
* Server xử lý dữ liệu và phản hồi lại cho client.

Để hiểu rõ hơn về luồng dữ liệu trong kiến trúc client-server, hãy tìm hiểu xem các trình duyệt web tương tác với server.

* Người dùng nhập URL của trang web.
* Trình duyệt gửi yêu cầu đến DNS server để tìm địa chị IP của web server.
* DNS gửi địa chỉ IP của web server về lại cho trình duyệt.
* Bây giờ, trình duyệt lại gửi yêu cầu HTTP/HTTPS đến địa chỉ IP của web server.
* Web Server gửi file cần thiết cho trang web.
* Bây giờ trình duyệt có thể hiển thị trang web.

### Client-Server vs P2P

{% embed url="https://github.com/Ren0503/system-design/raw/master/concepts/network-protocols/assets/compare.png" %}

### Ưu điểm của mô hình Client Server

**Quản lý tập trung**: nó là một hệ thống mạng tập trung, với toàn bộ dữ liệu được đặt ở một nơi duy nhất, để điều khiển các tiến trình và hoạt động. Nó có thể chia sẻ tài nguyên và dữ liệu trên các nền tảng khác nhau một cách dễ dàng, và người dùng được ủy quyền có thể truy cập đến bất kỳ file nào trong trung tâm lưu trữ tại bất kỳ thời điểm nào.

**Linh động**:&#x20;
