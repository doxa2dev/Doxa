# RabbitMQ

----
## RabbitMQ là gì??

> RabbitMQ là một message broker ( message-oriented middleware) sử dụng giao thức AMQP(Advanced Message Queue Protocol — Giao thức giao nhận tin nhắn sử dụng hàng đợi). Đây là chương trình đóng vai trò trung gian lưu trữ cũng như điều phối các yêu cầu (message) giữa người nhận(consumer) và người gửi(producer).

----
## Tại sao sử dụng RabbitMQ?
### Vấn đề
* Đối với các hệ thống sử dụng kiến trúc microservice thì việc gọi chéo giữa các service khá nhiều, khiến cho luồng xử lý khá phức tạp.

* Mức độ trao đổi data giữa các thành phần tăng lên khiến cho việc lập trình trở nên khó khăn hơn(vấn đề maintain khá đau đầu)

* Khi phát triển ứng dụng làm sao để các lập trình viên tập trung vào các domain, business logic thay vì các công việc trao đổi ở tầng infrastructure

* Với các hệ thống phân tán, khi việc giao tiếp giữa các thành phần với nhau đòi hỏi chúng cần phải biết nhau. Nhưng điều này gây rắc rối cho việc viết code. Một thành phần phải biết quá nhiều đâm ra rất khó maintain, debug

### Lợi ích
* Một producer không cần phải biết consumer. Nó chỉ việc gửi message đến các queue trong message broker. Consumer chỉ việc đăng ký nhận message từ các queue này

* Vì producer giao tiếp với consumer trung gian qua message broker nên dù producer và consumer có khác biệt nhau về ngôn ngữ thì giao tiếp vẫn thành công.(Hiện nay rabbitmq đã hỗ trợ rất nhiều ngôn ngữ khác nhau)

* Một đặc tính của rabbitmq là bất đồng bộ(asynchronous). Producer không thể biết khi nào message đến được consumer hay khi nào message được consumer xử lý xong. Đối với producer, đẩy message đến message broker là xong việc. Consumer sẽ lấy message về khi nó muốn. Đặc tính này có thể được tận dụng để xây dựng các hệ thống lưu trữ và xử lý log



**Flow để gửi-nhận message trong RabbitMQ**
![](https://gitlab.com/trung-nb/ari_website/-/raw/master/document/multiple_languague/images/img1.png)

> 1.Producer đẩy message vào exchange. Khi tạo exchange, bạn phải mô tả nó thuộc loại gì. Các loại exchange sẽ được giải thích phía dưới.

> 2.Sau khi exchange nhận message, nó chịu trách nhiệm định tuyến message. Exchange sẽ chịu trách về các thuộc tính của message, ví dụ routing key, phụ thuộc loại exchange.

> 3.Việc binding phải được tạo từ exchange đến hàng đợi. Trong trường hợp này, ta sẽ có hai binding đến hai hàng đợi khác nhau từ một exchange. Exchange sẽ định tuyến message vào các hàng đợi dựa trên thuộc tính của của từng message.

> 4.Các message nằm ở hàng đợi đến khi chúng được xử lý bởi một consumer.

> 5.Consumer xử lý message trong queue.

## Các loại Exchange

![](https://gitlab.com/trung-nb/ari_website/-/raw/master/document/multiple_languague/images/img2.png)

### Có 4 loại Exchange: direct, topic, fanout, headers.

Ví dụ:
Nếu hàng đợi gắn với một exchange có binding key là *user_created*, message được đẩy vào exchange với routing key là *user_created* sẽ được đưa vào hàng đợi. Nếu không có một routing key nào khớp với binding key thì message sẽ bị hủy.

### 1. Direct Exchange

![](https://gitlab.com/trung-nb/ari_website/-/raw/master/document/multiple_languague/images/img3.png)

> Một Direct exchange sẽ đẩy message đến hàng đợi dựa theo khóa định tuyến — routing key. Ví dụ, nếu hàng đợi gắn với một exchange có binding key là user_created, message được đẩy vào exchange với routing key là user_created sẽ được đưa vào hàng đợi.

Mặc định của exchange là một string trống “”.

Loại trao đổi trực tiếp hữu ích khi bạn muốn phân biệt các thông báo được xuất bản cho cùng một trao đổi bằng cách sử dụng một mã định danh chuỗi đơn giản.

### 2. Fanout Exchange

![](https://gitlab.com/trung-nb/ari_website/-/raw/master/document/multiple_languague/images/img4.png)

Một Fanout exchange sẽ đẩy message đến toàn bộ hàng đợi gắn với nó.
Ở đây được hiểu là một bản copy message tới tất cả những hàng đợi với bất kể một routing key nào. Nếu được đăng ký thì nó sẽ bị bỏ qua.
Exchange này hữu ích với trường hợp ta cần một dữ liệu được gửi tới nhiều thiết bị khác nhau với cùng một message nhưng cách xử lý ở mỗi thiết bị, mỗi nơi là khác nhau.

### 3. Topic Exchange

![](https://gitlab.com/trung-nb/ari_website/-/raw/master/document/multiple_languague/images/img5.png)

Một topic exchange sẽ làm một lá bài (gọi là wildcard) để gắn routing key với một routing pattern khai báo trong binding. Consumer có thể đăng ký những topic mà nó quan tâm. Cú pháp được sử dụng ở đây là * và #.
Ví dụ:
booking.* -> Được đăng ký bởi tất cả những key với pattern bắt đầu bằng booking.
booking.# -> Được đăng ký bởi tất cả các key booking hoặc bắt đầu với booking

### 4. Headers Exchange

![](https://gitlab.com/trung-nb/ari_website/-/raw/master/document/multiple_languague/images/img6.png)

Một header exchange sẽ dùng các thuộc tính header của message để định tuyến. Headers Exchange rất giống với Topic Exchange, nhưng nó định tuyến dựa trên các giá trị tiêu đề thay vì các khóa định tuyến.
Một thông điệp được coi là phù hợp nếu giá trị của tiêu đề bằng với giá trị được chỉ định khi ràng buộc.

## Dead Letter Exchange

Nếu không tìm thấy hàng đợi phù hợp cho tin nhắn, tin nhắn sẽ tự động bị hủy. RabbitMQ cung cấp một tiện ích mở rộng AMQP được gọi là “Dead Letter Exchange” — Cung cấp chức năng để chụp các tin nhắn không thể gửi được.

# Các thuật ngữ chính

* AMQP — Advanced Message Queueing Protocol
* Producer: thực hiện quá trình gửi bản tin lên RabbitMQ server
* Exchange: Nhận message từ producer và đẩy chúng đến hàng đợi dựa trên những nguyên tắc củatừng loại exchange hiện tại. Để nhận về message, một hàng đợi phải gắn với một exchange nào đó. Có 4 loại Exchange: direct, topic, fanout, headers.
* Queues: có nhiệm vụ lưu trữ bản tin được gửi lên
* Consumer: thực hiện việc lấy các bản tin từ queue về
Connection: Là một kết nối TCP giữa ứng dụng của bạn và RabbitMQ
* Channel: Một channel là một kết nối ảo bên trong một connection. Khi bạn đẩy đi hoặc nhận các message từ hàng đợi, tất cả phải đi qua channel
* Binding: Là một kết nối giữa hàng đợi và exchange
* Routing Key: là một khóa mà exchange dùng để tìm xem và ra quyết cách định tuyến message đến hàng đợi. Có thể hiểu như là một địa chỉ của message.
* User: người dùng có thể kết nối đến #RabbitMQ bằng username/password. Mỗi người dùng được cấp quyền như đọc, ghi và cấu hình quyền bên trong một instance. User còn có quyền trên một host ảo.
* Virtual Host: Cung cấp chức năng tách ứng dụng dùng trên cùng #RabbitMQ. Người dùng khác nhau có quyền hạn khác nhau trên virtual host, hàng đợi hay exchange khác nhau. Chúng chỉ tồn tại trong một virtual host.

Tài liệu tham khảo

link [https://www.rabbitmq.com/](https://www.rabbitmq.com/)
