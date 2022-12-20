# Network Protocols

## Giao thức mạng

{% embed url="https://github.com/Ren0503/system-design/raw/master/concepts/network-protocols/assets/network-protocols.svg" %}

Mạng máy tính có thể được định nghĩa là một tập hợp các máy tính và thiết bị khác được kết nối với nhau bằng một vài cách để chuyển đổi dữ liệu. Nó là một nhóm máy tính sử dụng một giao thức tiêu chuẩn để giao tiếp trên kết nối số để chia sẻ tài nguyên.

### Giao thức mạng là gì?

Một giao thức mạng là một tập hợp luật lệ được định sẵn để chỉ định dữ liệu sẽ được truyền như thế nào trong cùng mạng giữa các thiết bị với nhau. Nói chung, nó cho phép các thiết bị tương tác với nhau, bất kể khác biệt về cấu hình, cấu trúc và các chương trình nội bộ của chúng.

### Mô hình OSI

**Open Systems Interconnection (OSI)** : Mô hình OSI mô tả 7 lớp, mà các hệ thống máy tính sử dụng để giao tiếp với nhau qua mạng. Mỗi lớp biểu diễn một chức năng mạng khác nhau.

{% embed url="https://github.com/Ren0503/system-design/raw/master/concepts/network-protocols/assets/osi-model.png" %}

Các chức năng mạng có thể thực hiện bởi các giao thức. Ví dụ, để có thể chỉ định địa chỉ nguồn và đích của các gói tin, giao thức IP (Internet Protocol) sẽ chịu trách nhiệm cho định tuyến. IP cho phép giao tiếp giữa các mạng máy tính (network-to-network). Vì thế nó nằm ở lớp thứ 3 của mô hình.

Một ví dụ khác, giao thức TCP (Transmission Control Protocol) đảm bảo rằng việc truyền tải dữ liệu gói tin thông qua mạng sẽ diễn ra mượt mà. Do đó, TCP nằm ở lớp thứ 4.

**Lưu ý**:Một gói tin là một phân đoạn nhỏ của một thông điệp lớn. Dữ liệu được truyền tải thông qua mạng máy tính (như Internet) sẽ bị chia nhỏ thành nhiềugói tin. Sau đó hệ thống sẽ tự động thu thập và gộp chúng lại theo đúng thứ tự dữ liệu.

### Các giao thức phổ biến

#### Internet Protocols

Internet Protocol (IP) là một giao thức hoạt động ở lớp Network, có thể xem nó như là một tập hợp các quy tắc cho phép các gói tin được định tuyến thông qua mạng đến đúng địa chỉ cần đến.&#x20;

Khi một máy tính cố gắng tương tác hay gửi dữ liệu đến với các thiết bị máy tính khác. Gói dữ liệu đó sẽ được gửi như một gói tin IP. Gói tin IP là một đơn vị cơ bản của dữ liệu được gửi từ máy tính này sang máy tính khác. Nó thường sử dụng đơn vị là bytes, một gói tin IP gồm hai thành phần là tiêu đề (Header) và dữ liệu (Data).

{% embed url="https://github.com/Ren0503/system-design/raw/master/concepts/network-protocols/assets/ip-address.png" %}

Ảnh trên mô tả một gói tin IP đơn giản. Phần tiêu đề (header) bao gồm các thông tin thiết yếu của gói tin như:

* Địa chỉ IP nguồn của gói tin.
* Địa chỉ IP đích của gói tin.&#x20;
* Các thông tin khác như total\_size hay verison như IPv4, IPv6,....

#### IPv4 vs IPv6

IPv4 là phiên bản đầu tiên của IP. Nó được phát triến bên trong ARPANET vào nằm 1983/. Ngày nay nó là phiên bản được sử dụng rộng rải nhất. Nó dùng để định danh các thiết bị trong một mạng bằng cách sử dụng địa chỉ của hệ thống.

IPv4 sử 32bit  để lưu trữ 2³² địa chỉ, tức là hơn 4 tỷ địa chỉ. Cho đến hiện tại, nó được xem là IP chính với 94% lưu lượng Internet.

IPv6 là phiên bản mới nhất của IP. Internet Engineer Taskforce khởi tạo nó vào đầu năm 1994. Bản phát triển và thiết kế phù hợp hơn đến nay được gọi là IPv6.

Đây là phiên bản mới nhất được phát triển để phù hợp với nhu cầu ngày càng cần nhiều địa chỉ IP hơn. Nó tương đồng với IPv4 về mục đích, nhưng vì sử dụng đến 128-bit cho lưu trữ địa chỉ nó nó có thể lưu nhiều hơn.

IPv6 còn được gọi là IPng (Internet Protocol next generation).

{% embed url="https://github.com/Ren0503/system-design/raw/master/concepts/network-protocols/assets/ip-package-transfer.gif" %}

#### IP Packet Transfer

Kích thước của một gói tin IP khá nhỏ, nó không đủ để gửi files như ảnh, mail hay các thông tin nặng khác. Song ta vẫn có thể sử dụng nhiều gói tin để gửi các loại dữ liệu này. Tuy nhiên trong trường hợp mà các gói tin có thể không đến được đích mà bị thất lạc trên đường đi. Nó sẽ phát sinh vấn đề về thứ tự của các gói tin.

### Transmission Control Protocols (TCP)

{% embed url="https://github.com/Ren0503/system-design/raw/master/concepts/network-protocols/assets/tcp.png" %}
