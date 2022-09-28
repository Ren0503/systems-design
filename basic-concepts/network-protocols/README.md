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
