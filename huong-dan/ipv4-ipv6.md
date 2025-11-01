# IPv4 và IPv6

Bài viết gốc: [IPv4 và IPv6](https://viblo.asia/p/ipv4-va-ipv6-PwlVmbz845Z)

IPv4 (Internet Protocol version 4) và IPv6 (Internet Protocol version 6) là hai phiên bản giao thức IP được sử dụng để xác định các thiết bị trong mạng Internet. IPv4 ra đời đầu tiên, nhưng với sự phát triển mạnh mẽ của Internet và sự gia tăng các thiết bị kết nối, số lượng địa chỉ IPv4 ngày càng cạn kiệt. IPv6 được phát triển để giải quyết vấn đề này và mở ra khả năng kết nối mạng rộng lớn hơn.

![](https://images.viblo.asia/e1165b27-159e-448d-8242-2c22b859758f.jpg)

### IPv4

-   **IPv4** là phiên bản địa chỉ IP phổ biến nhất, sử dụng địa chỉ 32-bit để xác định thiết bị trong mạng. Một địa chỉ IPv4 bao gồm 4 phần, mỗi phần có 8 bit (gọi là octet), được biểu diễn dưới dạng thập phân, ví dụ: `192.168.1.1`.
-   **Khả năng địa chỉ**: IPv4 có khoảng **4,3 tỷ địa chỉ** khả dụng (2^32), điều này dường như là đủ vào thời điểm ban đầu, nhưng với sự bùng nổ của các thiết bị kết nối internet, số lượng địa chỉ IPv4 đã trở nên không đủ.
-   **Chạy trên hạ tầng**: IPv4 sử dụng phương pháp định tuyến và cấu hình đơn giản, nhưng vấn đề cạn kiệt địa chỉ đã dẫn đến việc triển khai các kỹ thuật như NAT (Network Address Translation) để chia sẻ một địa chỉ IP cho nhiều thiết bị.
-   Các dãy địa chỉ IPv4 dành cho mạng nội bộ (private networks) gồm:
    -   10.0.0.0 đến 10.255.255.255
    -   172.16.0.0 đến 172.31.255.255
    -   192.168.0.0 đến 192.168.255.255

### IPv6

-   **IPv6** là phiên bản mới hơn của địa chỉ IP, sử dụng địa chỉ 128-bit, có thể cung cấp một lượng địa chỉ khổng lồ – khoảng **340 tỷ tỷ tỷ tỷ tỷ tỷ tỷ (3.4 x 10^38) địa chỉ**. Địa chỉ IPv6 được viết dưới dạng hexa, ví dụ: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.
-   **Khả năng địa chỉ**: IPv6 giải quyết vấn đề cạn kiệt địa chỉ của IPv4, cung cấp khả năng địa chỉ vô hạn cho các thiết bị kết nối Internet trong tương lai.
-   **Cải tiến**: IPv6 hỗ trợ các tính năng mới như cấu hình tự động (Stateless Address Autoconfiguration), bảo mật tốt hơn với IPSec, và hiệu suất định tuyến cao hơn.

### So Sánh IPv4 và IPv6

| **Yếu tố** | **IPv4** | **IPv6** |
| --- | --- | --- |
| **Địa chỉ** | 32-bit (4 tỷ địa chỉ) | 128-bit (340 undecillion địa chỉ) |
| **Cấu trúc** | Thập phân, 4 phần (octets) | Hệ thập lục phân, 8 phần (hexadecimal) |
| **Định tuyến** | Đơn giản nhưng có NAT | Hiệu quả hơn với hỗ trợ định tuyến tự động |
| **Bảo mật** | Cần cấu hình thêm IPSec | Tích hợp sẵn IPSec |
| **Quản lý** | Quản lý mạng phức tạp (NAT) | Quản lý mạng đơn giản hơn, cấu hình tự động |
| **Sử dụng** | Cạn kiệt địa chỉ | Được phát triển cho tương lai, không giới hạn |

**IPv4** vẫn là giao thức chính hiện nay, nhưng sự phát triển nhanh chóng của các thiết bị kết nối internet đã thúc đẩy sự chuyển đổi sang **IPv6**.

All rights reserved