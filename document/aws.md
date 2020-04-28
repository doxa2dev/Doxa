# AWS Certified Solutions Architect Associate

### Section 1: Introduction - AWS Certified Solutions Architect Associ...

##### 1. Course Introduction - AWS Certified Solutions Architect Associate

> AWS (viết tắt của cụm từ Amazon Web Services) là một hệ thống các dịch vụ điện toán đám mây cung cấp cho doanh nghiệp các giải pháp về: Storage, computing power, databases, networking, analytics, developer tools, sercurity, virtualization,… <br/>
mang đến khả năng tính toán, lưu trữ cơ sở dữ liệu, phân phối nội dung và các chức năng khác nhằm giúp các doanh nghiệp mở rộng và phát triển. 

##### 2. Creating an AWS Account
##### 3. AWS Account Activation Troubleshooting
* Tạo tài khoản 

> Truy cập vào trang http://aws.amazon.com/ và chọn Create an AWS Account. Sau đó hãy làm theo hướng dẫn để đăng ký. Chú ý rằng cần có tài khoảng Credit/Debit card để có thể tạo tài khoản Amazon. Và trong quá trình đăng ký, sẽ nhập số điện thoại, và xác thực
mã PIN.<br/>
Sau khi đăng ký xong, sẽ phải mất một khoảng thời gian (trong vòng 24h) để Amazon xác nhận các thông tin trước khi cho phép vào console thiết lập sử dụng các dịch vụ của AWS.


##### 4. AWS Budget Setup

> Để có thể yên tâm cài đặt các dịch vụ và tin chắc rằng dịch vụ mà ta đang sử dụng là miễn phí, hãy kiểm tra các khoản phí mà ta đã sử dụng một cách thường xuyên.<br/>
Chọn vào tên tài khoản của mình ở navigation bar ở góc trên bên phải, sẽ hiện ra một dropdown menu, ở đó hãy chọn mục "My billing Dashboard", ta sẽ đi tới màn hình quản lý các khoản chi phí sử dụng của AWS.<br/>

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image2.png) <br/>

Để chắc ăn hơn, hãy sử dụng các alert và notification. Đây là các báo động ta có thể thiết lập, nó sẽ gửi email mỗi khi tài nguyên mà ta sử dụng chạm tới một ngưỡng nào đó.

b1. Nhập vào từ khóa Budgets

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image3.png) <br/>

b2. Nhấn Set your budget

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image4.png) <br/>

b3.Nhập số tiền, nhấn Configure alerts

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image5.png) <br/>

b4.Nhập vào giới hạn số tiền cần alert

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image6.png) <br/>

b5.Review và nhấn Create

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image7.png) <br/>

b6.Tạo budgets thành công

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image8.png) <br/>

##### 5. Important Message

* Chỉnh speed video
* Hiển thị sub

##### 6. About your instructor
* Anh ấy tên là Stephane Maarek :)))

##### 7. SAA-C01 vs SAA-C02

* Thông tin kì thi

### Section 2: Code & Slides Download

##### 8. Slides and Code Download
link 
[https://courses.datacumulus.com/downloads/certified-solutions-architect-pn9/]

### Section 3: AWS Fundamentals: IAM & EC2

##### 9. AWS Fundamentals - Section
Introduction

##### 10. AWS Regions and AZs

* Region

> Region bản thân nó mang ý nghĩa là vùng, phạm vi và với resource điện đoán đám mây của Amazon được host tại nhiều nơi trên thế giới, thì region chỉ theo nghĩa đen về mặt vật lý là những địa danh trên thế giới. Vào thời điểm hiện tại thì trên toàn thế giới họ có khoảng 19 region chính và các vùng con (là những data center) bên trong chúng như hình bên dưới. Chuẩn bị sẽ có thêm vài region nữa. Mỗi region có thể là cung cấp một hoặc một số dịch vụ riêng như DB (Aurora), storage (S3), Batch ... 

[https://aws.amazon.com/about-aws/global-infrastructure/]

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image9.png) <br/>

* AZ : Availability Zone

> Mỗi region lại có một hoặc nhiều AZ, ví dụ như Tokyo region là vùng cung cấp dịch vụ AWS trên thế giới nhưng còn trong nó lại có 3 data center độc lập nhau, và họ gọi là AZ.

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image10.jpg) <br/>

Do region có nhiều AZ nên khi mà thiết kết infra cho hệ thống thì có thể dùng chế độ Multi-AZ để nâng cao an toàn giảm thiểu tổn thất nếu chẳng may xảy ra cho hệ thống.























