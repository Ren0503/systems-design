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

