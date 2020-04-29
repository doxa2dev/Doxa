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

> Region có nghĩa là vùng, phạm vi chứa resource điện đoán đám mây của Amazon được host tại nhiều nơi trên thế giới, region về mặt vật lý là những địa danh trên thế giới. Vào thời điểm hiện tại thì trên toàn thế giới hiện có khoảng 23 region chính và các vùng con (là những data center) bên trong chúng như hình bên dưới. Chuẩn bị sẽ có thêm vài region nữa. Mỗi region sẽ cung cấp một hoặc một số dịch vụ riêng như DB (Aurora), storage (S3), Batch ... 

[https://aws.amazon.com/about-aws/global-infrastructure/]

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image9.png) <br/>

* AZ : Availability Zone

> Mỗi region lại có một hoặc nhiều AZ, ví dụ như Tokyo region là vùng cung cấp dịch vụ AWS trên thế giới nhưng còn trong nó lại có 3 data center độc lập nhau,gọi là AZ.

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image10.jpg) <br/>

Do region có nhiều AZ nên khi thiết kết cho hệ thống thì có thể dùng chế độ Multi-AZ để nâng cao an toàn giảm thiểu tổn thất nếu chẳng may xảy ra cho hệ thống.


##### 11. IAM Introduction

* IAM là gì? 

> IAM (Identity and Access Management) là dịch vụ web giúp bạn kiểm soát truy cập tới tài nguyên AWS. Khi đó, chỉ có những tài khoản IAM mà bạn cho phép mới có thể truy cập hoặc có quyền sử dụng tài nguyên mà bạn chỉ định.

* Vì sao nên sử dụng IAM?

> Mặc định khi đăng ký AWS, tài khoản của bạn là tài khoản root, tài khoản có quyền cao nhất với tất cả tài nguyên trong hệ thống AWS. Vì vậy, nếu ta không có nhu cầu sử dụng tất cả các dịch vụ của AWS thì ta nên tạo tài khoản IAM để giới hạn quyền truy cập tới tài nguyên cần thiết.

* Một số lợi ích của IAM như sau:

> - Chia sẻ quyền truy cập tới tài khoản của bạn cho ứng dụng và user khác
> - Chỉ định quyền truy cập của tài khoản IAM trên từng tài nguyên nhất định.
> - Multi-factor authentication (MFA): Hỗ trợ xác thực 2 bước
> - Bạn có thể sử dụng dịch vụ IAM mà không phải trả bất kỳ chi phí nào để duy trì tài khoản IAM

##### 12. IAM Hands On

1 – Tạo tài khoản IAM – AWS Management Console access

Bước 1: Login vào AWS với tài khoản root (Tài khoản khi đăng ký AWS)

Tìm kiếm dịch vụ có tên là IAM, và click vào kết quả tìm kiếm.

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image11.png) <br/>

Bước 2: Ở trang “Welcome to Identity and Access Management” sẽ cung cấp cho ta tổng quan về tình trạng các tài khoản IAM như: Đường dẫn đăng nhập (Login Link), Số lượng User hiện tại, Số lượng Group hiện tại,… <br/>
Tiếp tục click vào liên kết “User” như hình bên dưới. Nó sẽ dẫn ta tới trang quản lý tài khoản.

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image12.png) <br/>

Bước 3: Ở giao diện quản lý tài khoản IAM <br/>

Click [Add user] để tạo một tài khoản mới

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image13.png) <br/>

Bước 4: Nhập thông tin tài khoản

– User name: Ở đây mình sử dụng User Name là “doxa1”<br/>
– Access Type: Mọi người chọn “AWS Management Console access”. Chú ý một tài khoản có thể chọn cả 2 loại Access Type.<br/>
– Console Password: Chọn “Custom password” để điền password vào.<br/>
– Require Password reset: Bỏ chọn trường này, nếu các bạn không muốn đổi password ở lần đăng nhập đầu tiên.<br/>

Click button [Next: Permissions] để tiếp tục

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image14.png) <br/>

Bước 5: Thiết lập quyền hạn cho tài khoản IAM

Ở đây chúng ta lựa chọn đơn giản là “Attach existing policies directly” và chọn chính sách là “AdministratorAccess” để sao chép quyền của tài khoản root cho tài khoản của chúng ta.

Tuy nhiên nên tìm hiểu thêm quyền hạn và tạo chính sách phù hợp hơn với nhu cầu sử dụng.

Click button [Nex: Reviews] để tiếp tục.

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image16.png) <br/>


Bước 6: Xác nhận lại thông tin tài khoản mà ta đang tạo
Nếu đúng như mong muốn, click button [Create user] để tạo tài khoản

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image17.png) <br/>

Nếu nhận được thông báo như hình dưới thì ta đã tạo thành công tài khoản cho mình rồi, click button [Close] để trở về giao diện quản lý tài khoản IAM


![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image18.png) <br/>


2 – Thay đổi đường dẫn login

Mặc định đường dẫn login sẽ có dạng: https://123456789.signin.aws.amazon.com/console

Với 123456789 là ID của tài khoản. Vì vậy mà chúng ta cần đổi sang một đường dấn Alias dễ nhớ hơn.

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image19.png) <br/>

Truy cập tag Dashboard chọn Customize
Sau đó nhập Alias cho tài khoản.

3 – Xóa tài khoản IAM
Ở trang quản lý tài khoản -> Chọn tài khoản ta muốn xóa -> Click button [Delete user]

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image20.png) <br/>


4 – Tạo Group

b1. Nhấn vào Create New Group
![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image21.png) <br/>

b2.Nhập vào Group Name, nhấn Next Step

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image22.png) <br/>


b3.Chọn một policy name, nhấn Next Step

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image23.png) <br/>


5 – Add User Vào Group

b1.Check vào user cần add vào group, chọn Action Add User to Group

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image25.png) <br/>

b2.Chọn user cần add vào group, nhấn Add Users

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image26.png) <br/>

b3.Kết quả add thành công user vào group

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image27.png) <br/>


##### 13. EC2 Introduction

* Amazon EC2 là gì?

> Amazon EC2 (Amazon Elastic Compute Cloud) là các máy chủ đám mây có khả năng tính toán mở rộng trong môi trường đám mây AWS. Sử dụng Amazon EC2 giúp ta phát triển và triển khai ứng dụng một cách nhanh chóng hơn, loại bỏ nhu cầu đầu tư vào phần cứng.<br/>
Ta có thể sử dụng Amazon EC2 để khởi tạo 1 hoặc nhiều máy chủ ảo, cấu hình bảo mật, mạng và quản lý lưu trữ. Amazon EC2 cho phép bạn tăng hoặc giảm quy mô theo yêu cầu, hoặc đối phó với sự tăng hoặc giảm đột biến đối với traffic, tài nguyên sử dụng.

* Các tính năng của máy chủ Amazon EC2

> 1.Môi trường máy tính ảo hóa, được hiểu là 1 instance<br/>
> 2.Các template được cấu hình sẵn cho instance, được gọi là AMIs (Amazon Machine Images), ít nhiều sẽ cần cho server của bạn, nó bao gồm HDH và các phần mềm bổ sung.<br/>
> 3.Các máy chủ có các cấu hình khác nhau về CPU, bộ nhớ, lưu trữ, lưu lượng mạng gọi là các Instance Types<br/>
> 4.Sử dụng cặp khóa (public key và private key) với mã hóa công khai để bảo mật thông tin đăng nhập<br/>
> 5.Instance store volumens: Lưu trữ data tạm thời, data sẽ bị xóa khi bạn stop hoặc terminate instance<br/>
> 6.Amazon EBS volumes: sử dụng để lưu trữ dữ liệu của bạn<br/>
> 7.Security Group: Một firewall ảo để bạn có thể chỉ ra giao thức, cổng, dải IP nguồn mà có thể tiếp cận tới instance<br/>
> 8.Elastic IP addresses: Địa chỉ IP cố định cho các máy chủ ảo<br/>
> 9.VPCs (Virtual Private Cloud): Đám mây riêng ảo<br/>


##### Hướng dẫn tạo máy ảo Amazon EC2 trên AWS

Bắt đầu: Ở giao diện quản lý Amazon EC2 ở địa chỉ: https://console.aws.amazon.com/ec2

Bấm [ Lauch Instance ] để bắt đầu quá trình khởi tạo máy chủ EC2

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image28.png) <br/>

Bước 1: Chọn “Amazon AMI“, các bạn cứ hiểu giống như là chúng ta chọn file iso để cài đặt HDH vậy.


Ở đây mình chọn Amazon Linux 2 AMI

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image29.png) <br/>

Bước 2: Chọn “Instance Type”, Loại EC2 Instance tương ứng với tài nguyên sẽ được cấp phát cho máy chủ.

Loại nhỏ nhất là t2.nano với 1 vCPUs và 0.5 Memory. Mình chọn loại t2.micro cho tài khoản Free tier.

Bấm button [ Next: Configure Instance Details ] để tiếp tục

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image30.png) <br/>

Bước  3: Cấu hình thông tin cơ bản của EC2 Instance

1.Number of instances: Số lượng instance<br/>
2.Network: Chọn VPC bạn đã tạo ở các bước trước đó, nếu chưa tạo bấm “Create new VPC”<br/>
3.Subnet: Chọn Subnet bạn đã tạo, nếu chưa tạo bấm “Create new subnet”<br/>
4.Auto-assign Public IP: Chọn Enable để được gán 1 địa chỉ Public IPv4 cho việc kết nối tới máy ảo<br/>

Bấm button [ Add storage ] để tiếp tục

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image31.png) <br/>

Bước 4: Điều chỉnh dung lượng lưu trữ của Amazon EC2

Bấm button [ Next: Add Tags ] để tiếp tục

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image32.png) <br/>

Bước 5: Thêm tag để quản lý máy ảo một cách dễ dàng

Thêm 1 name cho máy ảo cho dễ nhớ.  Bấm [ Next: Configure Security Group ]

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image33.png) <br/>

Bước 6: Cấu hình chính sách bảo mật Security Group

Chọn “Select an existing security group” mà bạn đã tạo trước đó. Nếu chưa tạo thì lựa chọn “Create a new security group”

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image34.png) <br/>

Bấm button [ Review and Launch ] để  review lại instance.

Bước 7: Review lại các thông tin Instance

Nếu ok, chúng ta bấm button [ Launch ] để tiếp tục

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image35.png) <br/>

Một cửa sổ hiển thị để chọn Key pair mà ta đã tạo trước đó, hoặc tạo mới 1 Key pair

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image37.png) <br/>

Tạo EC2 thành công

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image38.png) <br/>

Kêt quả chúng ta đã tạo thành công máy chủ Amazon EC

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image39.png) <br/>

Setting trạng thái cho máy chủ EC2

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image40.png) <br/>


### 14. SSH Overview

* SSH tới EC2 trong Linux and Mac
* SSH tới EC2 trong window sử dụng putty
* Sử dụng EC2 Instance Connect

### SSH trên Window10

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image41.png) <br/>

SSH thành công

![](https://gitlab.com/trung-nb/public/-/raw/master/aws_image/image42.png) <br/>












