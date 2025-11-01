# I. Mô hình OSI

Bài viết gốc: [OSI Model in computer network - Mô hình OSI trong mạng máy tính](https://viblo.asia/p/osi-model-in-computer-network-mo-hinh-osi-trong-mang-may-tinh-Ny0VG7XEVPA)

Mô hình OSI (Open Systems Interconnection), hay mô hình tham chiếu kết nối các hệ thống mở là một mô hình khái niệm được phát triển bởi Tổ chức Quốc tế về Tiêu chuẩn hóa (ISO) để hỗ trợ trong việc thiết kế và hiểu cách thức hoạt động của các giao tiếp trong mạng máy tính.

Hiện nay chúng ta có thể dễ dàng chia sẻ một hình ảnh, một dòng trạng thái nhanh chóng qua mạng xã hội. Thực ra, hành trình dữ liệu được gửi thành công tới đích rất phức tạp. Trong suốt quá trình gửi, dữ liệu phải trải qua nhiều công việc xử lý khác nhau, đòi hỏi sự kết hợp hài hòa giữa các thiết bị phần cứng, phần mềm khác nhau. Mô hình OSI như một tiêu chuẩn chung, cung cấp một khuôn khổ quy trình cho các công nghệ đa dạng ngày nay tuôn theo nhằm thực hiện giao tiếp chính xác.

Mô hình được áp dụng vào đầu những năm 19801980, bao gồm 77 tầng/lớp (layer):

-   Tầng vật lý (Physical layer)
-   Tầng liên kết dữ liệu (Data link layer)
-   Tầng mạng (Network layer)
-   Tầng giao vận (Transport layer)
-   Tầng phiên (Session layer)
-   Tầng trình diễn (Presentation layer)
-   Tầng ứng dụng (Application layer)

![image.png](https://images.viblo.asia/8cd3a77b-9d9a-4999-9b5a-aadc36d49f47.png)

## II. Các tầng trong mô hình OSI

Mô hình bao gồm 77 tầng riêng biệt nhưng chúng liên kết chặt chẽ với nhau, mỗi tầng đều có nhiệm vụ gửi/nhận dữ liệu từ tầng kề trên hoặc kề dưới nó. Tại thiết bị gửi, dữ liệu xuất phát từ tầng ứng dụng (Application layer), lần lượt được chuyển tiếp và xử lý qua mỗi tầng, cho tới tầng vật lý (Physical layer); bên nhận thu được dữ liệu từ tầng vật lý, chuyển tiếp và xử lý lần lượt qua các tầng, cho tới tầng ứng dụng, thiết bị nhận đón tiếp dữ liệu tại đây.

![image.png](https://images.viblo.asia/926d6a4a-25dc-4025-9d35-3999e4ae9ff5.png)

Có thể hình dung việc gửi và nhận dữ liệu dựa trên mô hình OSI giống như quá trình gửi và nhận thư: dữ liệu là nội dung thư, được ghi vào giấy, cho vào phong bì thư, đóng phong bì, dán tem, cho vào hòm thư, người đưa thư chuyển thư trong hòm tới hòm thư đích, bên nhận sẽ thực hiện ngược lại các bước này, cuối cùng đọc được nội dung thư. Mỗi bước đều lấy dữ liệu từ bước trước và xử lý thêm một thao tác, dữ liệu cũng được chuyển đổi từ hình trạng này tới hình trạng khác. Trong mô hình OSI cũng vậy, tương ứng với mỗi tầng, dữ liệu được thể hiện ở một hình thái khác nhau:

![image.png](https://images.viblo.asia/08454e3b-64d3-491a-93f6-a4899ff71e17.png)

## 1\. Tầng vật lý (Physical layer)

Là tầng thấp nhất trong mô hình OSI, tầng vật lý thực hiện chức năng chuyển tiếp dữ liệu từ kênh truyền nguồn tới kênh truyền đích. Dữ liệu trong tầng vật lý được biểu diễn dưới dạng dãy bit 00 và 11. Sau khi nhận được dữ liệu từ kênh truyền khác, tầng vật lý thực hiện chuyển tiếp dữ liệu lên tầng liên kết dữ liệu.

Có thể hình dung tầng vật lý chính là quá trình người đưa thư chuyển bức thư từ hòm thư này sang hòm thư khác. Quá trình này cần xem xét các yếu tố như tốc độ chuyển thư, phương tiện di chuyển, ... Tầng vật lý bao gồm các chức năng:

-   Biểu diễn bit: Chuyển đổi dữ liệu số (bit) thành tín hiệu vật lý (như tín hiệu điện, quang học, radio) để truyền trên phương tiện vật lý như cáp đồng, cáp quang, không khí.
-   Kiểm soát tốc độ dữ liệu (Bit rate control): Điều chỉnh tốc độ truyền dữ liệu, tức là số lượng bit truyền trên một kênh truyền trong một đơn vị thời gian. Điều này đảm bảo dữ liệu được truyền một cách hiệu quả và phù hợp với khả năng của phương tiện truyền dẫn.
-   Đồng bộ hóa các bit (Bit synchronization): Đảm bảo người nhận và người gửi đồng bộ về thời gian khi truyền và nhận từng bit, để tránh hiểu nhầm về dữ liệu đang được truyền.
-   Cấu hình đường truyền: Thiết lập cấu hình vật lý của đường truyền, bao gồm cài đặt các thiết bị như bộ định tuyến, switch, và hub.
-   Topo (Mô hình ghép nối) vật lý (Physical topologies): Xác định cách các thiết bị trong mạng được kết nối vật lý với nhau. Ví dụ như topo dạng sao, dạng vòng, dạng cây, ...
-   Chế độ truyền dẫn (Transmission mode): Xác định hướng truyền dữ liệu trong mạng. Có ba chế độ chính: Simplex (chỉ một hướng), Half-duplex (hai hướng nhưng không đồng thời), và Full-duplex (hai hướng đồng thời).

## 2\. Tầng liên kết dữ liệu (Data link layer)

Ở tầng vật lý, dữ liệu được truyền qua các đường truyền vật lý (các loại cáp) nên không đảm bảo tính toàn vẹn và bảo mật. Khắc phục cho nhược điểm đó, tầng liên kết dữ liệu cung cấp các cơ chế kiểm tra lỗi, quản lý quyền truy cập và điều chỉnh việc truyền dữ liệu, giúp đảm bảo tính toàn vẹn và tin cậy của dữ liệu trên mạng.

Tầng liên kết dữ liệu chịu trách nhiệm:

-   Đóng gói dữ liệu (Framing): Chia dữ liệu được nhận từ tầng mạng thành các khung (frames) nhỏ hơn để dễ dàng xử lý. Mỗi khung chứa thông tin cần thiết để kiểm soát lỗi và đồng bộ hóa.
-   Định địa chỉ vật lý (Physical addressing): Gán địa chỉ vật lý, thường là địa chỉ MAC (Media Access Control), cho mỗi thiết bị trong mạng để xác định nguồn và đích của mỗi khung dữ liệu.
-   Kiểm soát lưu lượng (Flow Control): Điều chỉnh tốc độ truyền dữ liệu giữa người gửi và người nhận để tránh quá tải dữ liệu tại người nhận. Điều này giúp đảm bảo rằng tất cả các dữ liệu được nhận một cách đầy đủ và chính xác.
-   Kiểm soát lỗi (Error control): Phát hiện và sửa chữa lỗi có thể xảy ra trong quá trình truyền dữ liệu. Điều này thường được thực hiện thông qua việc sử dụng các thuật toán kiểm tra lỗi như CRC (Cyclic Redundancy Check).
-   Kiểm soát truy cập (Access control): Xác định cách thức các thiết bị trên cùng một mạng chia sẻ kênh truyền thông. Ví dụ, trong một mạng LAN có thể sử dụng CSMA/CD (Carrier Sense Multiple Access/Collision Detection) hoặc CSMA/CA (Carrier Sense Multiple Access/Collision Avoidance) để quản lý truy cập.

## 3\. Tầng mạng (Network layer)

Với sự phối hợp của hai tầng vật lý và tầng mạng, các gói dữ liệu đã có thể truyền thành công từ thiết bị này sang thiết bị khác trong cùng một môi trường truyền (cùng mạng). Tuy nhiên, trên thực tế các gói dữ liệu phần lớn được truyền thông qua hai thiết bị khác môi trường truyền, đó là lý do cần có sự tham gia của tầng mạng.

Tầng mạng giúp truyền các gói dữ liệu qua các chặng trung gian, từ đó dữ liệu có thể được truyền qua nhiều mạng khác nhau.

Tầng mạng có hai chức năng chính:

-   Định địa chỉ logic (Logical Addressing): Tầng mạng gán địa chỉ logic, thường là địa chỉ IP, cho mỗi thiết bị trong mạng. Điều này giúp xác định đích cuối cùng của dữ liệu trong mạng rộng lớn và đa dạng.
-   Định tuyến (Routing): Xác định lộ trình cho dữ liệu đi từ nguồn đến đích. Định tuyến dựa trên các thuật toán để chọn đường đi tối ưu nhất, giúp dữ liệu đến được đích nhanh chóng và hiệu quả. Định tuyến có thể thực hiện trong mạng nội bộ (LAN) hoặc qua các mạng khác nhau (WAN).

## 4\. Tầng giao vận (Transport layer)

Thay vì chuyển tiếp các gói dữ liệu một cách độc lập như tầng mạng, tầng giao vận giúp đảm bảo các gói dữ liệu thuộc cùng một thông điệp được chuyển tiếp một cách toàn vẹn.

Các chức năng của tầng giao vận:

-   Phân mảnh/Phân đoạn và tái hợp (Segmentation and Reassembly): Chia nhỏ dữ liệu từ tầng phiên thành các phân đoạn nhỏ hơn để truyền tải dễ dàng hơn trên mạng. Khi đến đích, những phân đoạn này được tái hợp thành dữ liệu ban đầu.
-   Kiểm soát kết nối: Thiết lập, duy trì và kết thúc các kết nối logic giữa người gửi và người nhận. Điều này bao gồm việc quản lý thiết lập kết nối, duy trì kết nối ổn định, và đóng kết nối sau khi truyền dữ liệu.
-   Kiểm soát lưu lượng: Điều chỉnh lưu lượng dữ liệu giữa người gửi và người nhận để tránh quá tải và đảm bảo truyền dữ liệu hiệu quả.
-   Kiểm soát lỗi: Phát hiện và sửa chữa lỗi có thể xảy ra trong quá trình truyền dữ liệu. Bao gồm việc kiểm tra lỗi và gửi lại dữ liệu nếu cần.
-   Định địa chỉ điểm dịch vụ (Service Point Addressing): Sử dụng cổng (port) để định địa chỉ dịch vụ tại các máy chủ, giúp xác định các ứng dụng cụ thể đang giao tiếp trên máy chủ.

## 5\. Tầng phiên (Session layer)

Chúng ta gọi một phiên (session) là một kết nối tạm thời giữa hai thiết bị để trao đổi dữ liệu. Tầng phiên quản lý việc thiết lập và duy trì phiên làm việc giữa các thiết bị trên mạng. Điều này giúp đảm bảo tính toàn vẹn và đáng tin cậy của phiên, đồng thời quản lý việc đồng bộ hóa dữ liệu và xác định các điểm dừng phiên (session termination).

Tầng phiên chịu trách nhiệm cho:

-   Thiết lập, duy trì, chấm dứt phiên (Session establishment, maintenance, and termination): Quản lý việc bắt đầu, duy trì và kết thúc các phiên giao tiếp giữa các ứng dụng. Điều này bao gồm việc mở, duy trì và đóng cửa sổ giao tiếp giữa các người dùng hoặc các quy trình.
-   Đồng bộ hóa (Synchronization): Đảm bảo việc đồng bộ hóa dữ liệu giữa các quá trình giao tiếp. Điều này có thể bao gồm việc đánh dấu các điểm kiểm tra trong dữ liệu để cho phép phục hồi từ điểm đó nếu có lỗi hoặc sự cố xảy ra.
-   Kiểm soát hội thoại (Dialog Controller): Quản lý quyền kiểm soát giao tiếp trong một phiên. Điều này có thể bao gồm việc xác định liệu giao tiếp là một chiều (simplex), hai chiều lần lượt (half-duplex) hay hai chiều cùng lúc (full-duplex).

## 6\. Tầng trình diễn (Presentation layer)

Tầng trình diễn còn có tên gọi khác là tầng phiên dịch (Translation layer), thực hiện một số chức năng:

-   Phiên dịch (Translation): Chuyển đổi dữ liệu giữa các định dạng mà các ứng dụng (trên tầng ứng dụng) hiểu được và định dạng mạng. Điều này bao gồm việc chuyển đổi giữa các định dạng mã hóa khác nhau, ví dụ từ ASCII sang EBCDIC.
-   Mã hóa và giải mã (Encryption and Decryption): Bảo mật thông tin bằng cách mã hóa dữ liệu trước khi chúng được gửi qua mạng và sau đó giải mã chúng khi đến nơi nhận. Điều này giúp bảo vệ dữ liệu khỏi sự truy cập không được phép.
-   Nén (Compression): Giảm kích thước của dữ liệu để tối ưu hóa việc truyền tải qua mạng. Nén có thể được thực hiện ở mức độ khác nhau tùy thuộc vào loại dữ liệu và yêu cầu cụ thể của ứng dụng.

## 7\. Tầng ứng dụng (Application layer)

Tầng ứng dụng cung cấp giao diện, dịch vụ trực tiếp cho người dùng cuối và các ứng dụng phần mềm. Các chức năng của tầng ứng dụng:

-   Thiết bị đầu cuối ảo của mạng (Network Virtual Terminal): Cho phép các ứng dụng từ máy tính khác nhau tương tác như thể chúng đang chạy trên cùng một thiết bị. Điều này giúp người dùng có thể truy cập và sử dụng các ứng dụng hoặc dịch vụ mạng từ bất kỳ máy tính nào.
-   Quản lý, truy cập và chuyển file (FTAM- File transfer access and management): Cung cấp khả năng truyền, truy cập và quản lý các tệp tin giữa các máy tính trên mạng. Điều này bao gồm việc truyền tải tệp tin (như FTP), quản lý tệp tin từ xa, và các chức năng quản lý quyền truy cập.
-   Các dịch vụ khác như mail services, directory services: Bao gồm một loạt các ứng dụng và dịch vụ phổ biến như email (SMTP, IMAP, POP3), dịch vụ thư mục (LDAP), dịch vụ web (HTTP), và nhiều dịch vụ khác được thiết kế để hỗ trợ giao tiếp và chia sẻ thông tin trong mạng.

## III. Tầm quan trọng của mô hình OSI

## 1\. Tiêu chuẩn hóa

-   Tương thích quốc tế: Mô hình OSI giúp đảm bảo rằng các thiết bị và giao thức mạng từ nhiều nhà sản xuất khác nhau có thể tương thích với nhau. Điều này rất quan trọng trong việc xây dựng và duy trì một mạng toàn cầu để các thiết bị và hệ thống từ khắp nơi trên thế giới có thể giao tiếp hiệu quả.
-   Dễ dàng tích hợp: Bằng cách tuân theo một bộ quy chuẩn chung, các công ty có thể dễ dàng tích hợp các sản phẩm và dịch vụ từ các nhà cung cấp khác nhau, tạo ra hệ thống mạng linh hoạt và mạnh mẽ.

## 2\. Phát triển và bảo trì mạng đơn giản hơn

-   Rõ ràng và có tổ chức: Mô hình OSI chia quá trình truyền thông thành các lớp rõ ràng, giúp kỹ sư và nhà phát triển hiểu rõ cách thức hoạt động và tương tác của các phần khác nhau trong một mạng.
-   Gỡ lỗi và bảo trì: Khi có vấn đề xảy ra, việc chia mạng thành các lớp giúp xác định và sửa chữa vấn đề trở nên dễ dàng hơn, vì có thể tập trung vào từng lớp cụ thể mà không cần xem xét toàn bộ hệ thống.

## 3\. Linh hoạt trong phát triển và cải tiến

-   Độc lập giữa các lớp: Các lớp trong mô hình OSI hoạt động độc lập với nhau. Điều này cho phép các nhà phát triển tập trung vào việc cải tiến hoặc thay đổi một lớp cụ thể mà không làm ảnh hưởng đến các lớp khác.
-   Kích thích đổi mới: Mô hình OSI khuyến khích sự đổi mới và phát triển công nghệ, vì mỗi lớp có thể được cải tiến một cách độc lập, dẫn đến sự tiến bộ liên tục trong từng lĩnh vực.

## 4\. Tính phổ quát và mở rộng

-   Tính phổ quát: Mô hình OSI được thiết kế để không phụ thuộc vào bất kỳ công nghệ cụ thể nào, làm cho nó phù hợp với nhiều loại mạng và ứng dụng khác nhau.
-   Dễ dàng mở rộng: Mô hình OSI cho phép mạng dễ dàng mở rộng và thích ứng với các công nghệ mới, vì mỗi lớp có thể được nâng cấp hoặc thay đổi mà không ảnh hưởng đến các lớp khác.

## 5\. Đào tạo

Mô hình OSI là một công cụ giáo dục quan trọng trong lĩnh vực mạng máy tính. Giúp sinh viên và chuyên gia mới có thể tìm hiểu cơ bản về mạng máy tính một cách có hệ thống.

## Tài liệu tham khảo

-   [https://www.geeksforgeeks.org/open-systems-interconnection-model-osi/](https://www.geeksforgeeks.org/open-systems-interconnection-model-osi/)
-   [https://csc-knu.github.io/sys-prog/books/Andrew%20S.%20Tanenbaum%20-%20Computer%20Networks.pdf](https://csc-knu.github.io/sys-prog/books/Andrew%20S.%20Tanenbaum%20-%20Computer%20Networks.pdf)
-   [https://www.ucg.ac.me/skladiste/blog\_44233/objava\_64433/fajlovi/Computer%20Networking%20\_%20A%20Top%20Down%20Approach,%207th,%20converted.pdf](https://www.ucg.ac.me/skladiste/blog_44233/objava_64433/fajlovi/Computer%20Networking%20_%20A%20Top%20Down%20Approach,%207th,%20converted.pdf)