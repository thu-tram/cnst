# DNS hoạt động như thế nào?

Bài viết gốc: [DNS hoạt động như thế nào?](https://viblo.asia/p/dns-hoat-dong-nhu-the-nao-018J26O5JYK)

## Mở đầu

Nhiều năm trước đây, khi mới bước chân vào nghề lập trình web, lần đầu tiên chạy được một ứng dụng web trên địa chỉ localhost:8080 và 127.0.0.1:3000, mình đã tự hỏi:

"Máy tính kết nối tới mạng internet qua địa chỉ IP các thứ, rồi bình thường mình vẫn truy cập web bằng tên miền website, vậy sao mà cái tên website kia lại dẫn tới cái máy chứa trang web được? bla bla..".

![53_750x750_Front_Color-NA.jpg](https://images.viblo.asia/c7e11df9-bcc8-4417-9795-923930d6ee4c.jpg) Trong bài viết này chúng ta cùng đi tìm hiểu IP, Domain, DNS là gì và chúng liên quan đến nhau như thế nào, và làm cách nào mà trình duyệt có thể request đến đúng máy tính chứa nội dung cần truy cập.

## IP và Domain

Thiết bị trong một mạng máy tính sử dụng giao thức Internet (Internet Protocol) sẽ được cung cấp một địa chỉ IP, địa chỉ IP tương đương với định danh của thiết bị trong network, giúp phân biệt giữa các máy tính khác nhau. Địa chỉ IP là một dãy số có dạng [xxx.xxx.xxx.xxx](http://xxx.xxx.xxx.xxx/)

Tương tự như vậy, với mạng Internet toàn cầu, các máy tính cũng được định danh bằng các địa chỉ IP. Nhưng con người làm sao nhớ được các con số vô nghĩa, chưa kể dãy số còn dài thế kia, vậy nên chúng ta sử dụng các từ gợi nhớ có nghĩa. Ví dụ:

-   [dichvucong.gov.vn](http://dichvucong.gov.vn/)
-   [vi.wikipedia.org](http://vi.wikipedia.org/)
-   [mail.google.com](http://mail.google.com/)
-   [dantri.com](http://dantri.com/)
-   [sunteco.vn](http://sunteco.vn/)

Các tên gợi nhớ này được gọi là tên miền (Domain) và được đặt theo một số quy tắc nhất định.

DNS (Domain name system) sẽ gắn kết hai phần này lại với nhau và bằng cách nào đó khi bạn truy cập tên miền bạn sẽ được chuyển đến đúng địa chỉ IP cần đến. Đó là cách mà DNS hoạt động.

## Hành trình từ Domain đến IP

Chúng ta vừa hiểu một cách sơ lược cách hoạt động của DNS, thử tham gia hành trình truy cập một trang web xem sao.

_23h PM_

_\--- Browser and OS---_

_**Human:** Typing..._

_**Browser:** Ể có request mới nè: [zzz.com](http://zzz.com/), cái trang web gì mà khó hiểu, đợi tí bạn ôi, để tôi xem có thông tin về trang này không, trước khi tôi hỏi OS, lão đấy khó chịu lắm... Haizza, không có rồi, đợi tí nhé. Hi OS, có đấy không, tui nhờ tí, tôi có thể tìm [zzz.com](http://zzz.com/) ở đâu_

_**OS:** Bruh bruh, System is updating..._

_**Browser:** Giúp tí đi_

_**OS:** (Checking now...) không thấy nhé, nhưng tôi biết phải hỏi ai để tìm. RESOLVERRRR!!!!_

Đến đây ta đều thấy Trình duyệt và hệ điều hành đều tìm kiếm trong cache nhưng không thấy, OS sẽ tiếp tục request đến Resolver

\--- Resolver and Root server ----

Resolver hay còn gọi là DNS recursive resolver. Resolver thường được cung cấp bởi ISP (Internet Service Provider) - Nhà cung cấp dịch vụ Internet. Tất cả các nhà cung cấp dịch vụ đều biết: Làm sao để tìm được Root server. Root server lại biết nơi nào để tìm được .COM TLD server. TLD là viết tắt của Top-Level Domain.

![](https://images.viblo.asia/5f2c62f0-acbd-4d0e-afb2-e60eafd6cbda.png)

\*Telecom Company - Nhà cung cấp dịch vụ mạng

_...Hộp thư đến có thư mới...loạt soạt_

_Resolver: Request mới đến, tuyệt vời, [zzz.com](http://zzz.com/), ok để xem nào... không có trong cache rồi. Đi hỏi Root server thôi._

_Root server: Người tiếp theo. Tôi giúp gì được cho bạn._

_Resolver: Hi root, tôi đang tìm địa chỉ của [zzz.com](http://zzz.com/). Bạn có thể giúp tôi không?_

_Root server: Sorry nhé, tôi không biết địa chỉ của [zzz.com](http://zzz.com/), nhưng tôi biết .COM Top-level domain server ở đâu đấy!_

_Resolver: Ok thanks , trước khi đi tiếp, tôi cache lại phát đã._

Root server này là 1 trong 13 máy chủ Root Name. Root server nằm trên đỉnh của hệ thống phân cấp DNS. Chúng được đặt khắp thế giới và được điều hành bởi 12 tổ chức độc lập khác nhau. Chúng được đặt tên theo định dạng \[chữ cái\].root-servers.net, các chữ cái được đặt từ a đến m. Điều này không có nghĩa là chỉ có 13 máy chủ vật lý để phục vụ cả thế giới, trên thực tế mỗi tổ chức sẽ cung cấp dịch vụ trên nhiều server vật lý phân tán.

\--- tại Top-level Domain .COM ---

_**Resolver:** Tôi không ngại đến đây, tôi chỉ cần một lý do thôi._

_**.com TLD:** WHAT??? bad joke, dude!_

_**Resolve:** Hợ, sorry, tôi đang tìm [zzz.com](http://zzz.com/), cho tôi biết nó ở đâu được không?_

_**.com TLD:** huhm, câu hỏi hay đấy!_

Sự sắp xếp của hầu hết các top-level domains thuộc về Internet Coporation for Assigned Names and Number (ICANN). **.COM TLD** là một trong những cái tên được tạo ra đầu tiên năm 1985. Ngày nay nó cũng trở thành TLD lớn nhất. Một vài loại TLD khác có thể kể đến như:

-   Tên quốc gia (.vn, .uk),
-   TLD viết bằng ngôn ngữ native locallization(tiếng trung, tiếng arap)
-   Những tên phổ biến khác như. net,. org, .edu
-   TLD hạ tầng: .ARPA, hầu hết dùng cho reverse DNS lookups (Tra cứu tên miền từ IP)

Ngày nay có càng nhiều hơn các TLD được tạo ra. Giờ thì quay trở lại với câu hỏi của **Resolver**.

_**.com TLD:** Cache searching...Tôi sợ là tôi không biết IP của [zzz.com](http://zzz.com/) ở đâu, nhưng tôi tìm thấy name server của [zzz.com](http://zzz.com/) đấy (Đưa cho mảnh giấy)_

_**Resolver:** Tuyệt vời,Cảm ơn nhé, cache phát nữa. Khoan đã, sao .com có thể chỉ mình tới name server nào nhỉ???_

Vậy là .Com TLD đã tìm thấy name servers của [zzz.com](http://zzz.com/) là [aleza.cloudflare.com](http://aleza.cloudflare.com/), name server hay còn gọi là authoritative name server. Khi một domain được thanh toán, Domain Registra (Nhà cung cấp tên miền) sẽ lưu trữ tên miền này và thông báo tới TLD về name server có thẩm quyền của mỗi tên miền. Từ đã, Resolve đang đi phân giải tên miền mà lại nhận được một tên miền nữa là sao? Trên thực tế có thêm những thông tin bổ sung đi kèm với name server, Resolve nhận được ít nhất một địa chỉ IP với mỗi name server, vậy nên Resolver có thể tới chính xác được máy chủ của name server.

[aleza.cloudflare.com](http://aleza.cloudflare.com/) - 197.246.15.51

[bzeta.cloudflare.com](http://bzeta.cloudflare.com/) - 51.32.246.54

\--- Last trip, tại name server--------

\***[aleza.cloudflare.com](http://aleza.cloudflare.com/):** Người tiếp theo \*

_**Resolver:** Thank god, tôi đã đi một chuyến dài, .com nói tôi tới đây, đằng ấy cho tôi biết địa chỉ IP của [zzz.com](http://zzz.com/) được không_

_**[aleza.cloudflare.com](http://aleza.cloudflare.com/):** Bạn tìm đúng người rồi đấy, tôi chính là name server của [zzz.com](http://zzz.com/) đây, thực ra có một vài người giống tôi nữa cũng có thể cung cấp IP của [zzz.com](http://zzz.com/) nữa, ví dụ [bzeta.cloudflare.com](http://bzeta.cloudflare.com/), đề phòng trường hợp 1 trong chúng tôi không thể phục vụ. Ok giải thích thế đủ rồi, IP của [zzz.com](http://zzz.com/) đây: 49.53.63.69_

_**Resolver:** Hả?_

_**[aleza.cloudflare.com](http://aleza.cloudflare.com/):** IP của [zzz.com](http://zzz.com/) đấy gì nữa 49.53.63.69_

_**Resolver:** Oh, thanks! (Hí hoáy ghi chú)_

_**Resolver:** Phùuuu, về nhà thôi._

\--- Tại Homie computer---

_**OS:** Did you finish? Resolver. Tôi đợi ông hơi lâu rồi đấy (5ms) Resolver: Hi OS, Câu trả lời đây, IP của [zzz.com](http://zzz.com/) là 49.53.63.69_

_**OS:** Được ấy nhể, nói chuyện sau nhé, tôi giải quyết công việc đã._

_**OS:** Hey Browser, đây là IP của [zzz.com](http://zzz.com/), làm gì làm đi._

_**Browser:** Ồ, thanks. Finally!_

Connecting...to 49.53.63.69

_**49.53.63.69:** Sure, here your website._

_**Human:** (Cuộn chuột, click, click...)_

## Kết

Quá trình phân giải từ Domain sang IP có thể tóm tắt bằng sơ đồ sau:

![](https://images.viblo.asia/e9c7594d-7d66-434a-90ad-f3142624f6d5.png)

Hi vọng với hành trình và câu chuyện của các nhân vật giả tưởng trên đây có thể giúp các bạn hiểu thêm về nguyên lý hoạt động của IP, Domain và DNS.

> Tìm hiểu thêm về các dịch vụ của Sunteco Cloud: [http://sunteco.vn/](http://sunteco.vn/)
> 
> Trải nghiệm [Sunteco Cloud](https://dashboard.sunteco.vn/register?utm_source=viblo&utm_medium=June&utm_campaign=DNS)