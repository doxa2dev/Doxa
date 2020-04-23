# Hướng dẫn sử dụng Owasp Zap

---
## Khái niệm và chức năng của Owasp Zap

> Owasp Zap – The Open Web Application Security Project được hiểu là dự án mở về bảo mật ứng dụng web. Đây là một dự án được cả cộng đồng chung tay tham gia, giúp các tổ chức có thể phát triển mở hoặc bảo trì các ứng dụng ở trạng thái an toàn. Chúng được người dùng biết đến nhiều nhất với tính năng quét lỗi bảo mật của ứng dụng web, mã nguồn mở. Bạn sẽ tìm thấy nhiều tính năng tuyệt vời ở Owasp Zap bao gồm cả miễn phí và trả phí:<br/>
1.Là mã nguồn mở.<br/>
2.Các công cụ đạt chuẩn về an toàn thông tin.<br/>
3.Thực hiện chính sách kiểm tra về bảo mật, an toàn cho mã nguồn.<br/>
4.Sử dụng hoàn toàn miễn phí.<br/>
5.Ứng dụng đa nền tảng.<br/>
6.Dễ dàng cài đặt và sử dụng.<br/>
7.Cho phép triển khai sử dụng nhiều ngôn ngữ.<br/>
8.Quét tự động.<br/>
9.Tự động cập nhật nhiều tính năng cho người dùng.<br/>
10.Là công cụ được nhiều người dùng tham gia sử dụng, tạo thành một cộng đồng nhiều thành viên.<br/>
11.Được phát triển bởi các chuyên gia lập trình chuyên nghiệp.<br/>
Ngoài ra, Owasp Zap cũng đưa ra 10 rủi ro mà bạn có thể gặp phải:<br/>
1.Khả năng bị tiêm nhiễm mã độc.<br/>
2.Tính sai lầm trong việc kiểm tra định danh cũng như các phiên làm việc.<br/>
3.Thực thi mã Scrip xấu.<br/>
4.Đối tượng tham chiếu không được an toàn tuyệt đối.<br/>
5.Cấu hình an ninh có thể bị sai.<br/>
6.Có thể bị lộ cấu hình nhạy cảm.<br/>
7.Đôi khi còn bị mất kiểm soát mức độ truy cập chức năng.<br/>
8.Giả mạo yêu cầu.<br/>
9.Bị tấn công khi sử dụng các thành phần với những lỗ hổng bảo mật.<br/>
10.Chuyển hướng không an toàn.<br/>
----
## Các bước cài đặt Owasp Zap
### Điều kiện
Owasp Zap chạy bằng Java chính vì vậy ta cần phải cài đặt JRE. Nếu bạn chưa cài JRE thì có thể vào Web Site Oracle download và cặt đặt.
### Download cài đặt
B1. Truy cập vào link: https://www.zaproxy.org/download/ và lựa chọn phiên bản
phù hợp với hệ điều hành đang dùng. Sau đó tiến hành download và cài đặt thông
thường.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa1.png)
Sau khi cài đặt xong ta khởi động ứng dụng và sẽ có giao diện như hình bên dưới:
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa2.png)
### Thiết lập Local Proxy
OWASP ZAP có chức năng proxy cục bộ, cho phép OWASP ZAP hoạt động như một proxy cục bộ.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa3.png)
Chọn Tools -> Options màn hình sau sẽ xuất hiện.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa4.png)
Ta sẽ thiết lập Address và Port . Mặc đinh sẽ là localhost:8080. Trường hợp mà có ứng dụng nào khác đã chiếm dụng port 8080 thì ta có thể đổi 1 port khác tùy ý, rồi nhấn OK để lưu thiết lập.
### Thiết lập bên phía Browser (Google chorme)
Cài đặt Add-on SwitchyOmega. Add-on này sẽ giúp  ON OFF việc chuyển đổi proxy 1 cách dễ dàng.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa18.png)
Chọn New profile và điền những thông tin cần thiết , chú ý là chỗ Proxy servers
phải thiết lập cùng Address và cùng Port đã được thiết lập ở phía Owasp Zap. Thiết lập này sẽ giúp cho Owasp Zap bắt được những truy cập mà ta đang truy cập phía Browser.
Sau khi thiết lập xong , nút Apply changes sẽ sáng lên, click vào để lưu thiết lập.
Ok, Ta đã thiết lập xong Proxy cho Browser , nhìn lên góc phải browser ta sẽ thấy icon hình tròn. Click vào cái profile  vừa thiết lập  để ON và Click vào System Proxy để vô hiệu hóa thiết lập.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa6.png)
Vậy là bước này đã xong , bây giờ ta đã có thể ON OFF để chuyển đổi proxy 1 cách dễ dàng.

### Truy cập vào ứng dụng Web mà ta muốn test
Sau khi thiết lập xong Proxy cho cả Owasp Zap và Browser. Ta có thể truy cập vào ứng dụng Web để test.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa7.png)
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa8.png)
Nếu thiết lập đúng , phía bên trái phần Sites của Owaps Zap sẽ hiển thị URL của trang Web mà mình vừa truy cập. Đến đây thì bước chuẩn bị cho việc Scan Injection kết thúc.
Owasp Zap có 4 chế độ quét:
1.Safe Mode
Sẽ chỉ hiển thị và phát hiện những đường dẫn mà người dùng thao tác và cấm mọi hành động scan có thể gây nguy hiểm
2.Protected Mode
Chỉ cho phép scan đối với những URL được xác định trong phạm vi (là tập hợp những URL đã được thêm vào context và sẽ thực hiện theo những cài đặt mà người dùng định nghĩa)
3.Standard Mode
Là mode tấn công thông thường có thể scan ở mode này mà không cần phải bắt buộc khai báo trong context
4.Ở mode này thì OZ sẽ thực hiện active scanning cho mọi url mà nó phát hiện khi người dùng thao tác trên trình duyệt.<br/>
Khi khởi động nó được set chế độ mặc định là Standard, do đó ta cần phải chuyển sang chế độ Protected Mode.
Lý do chọn chế độ Protected là vì, nếu chọn chế độ mặc định Standard hay là chế độ Attack thì có khả năng là nó sẽ tấn công vào các trang Web mà mình không quản lý được. Ngược lại nếu trọn chế độ Safe thì nó lại không scan được hết hoàn toàn các lỗ hổng.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa9.png)
Một số thông tin:
* Một cảnh báo (alert) là một lỗ hổng tiềm năng và được liên kết với 1 request cụ
thể. Một request có thể có nhiều hơn 1 cảnh báo. 1 cảnh báo được hiển thị trong giao
diện người dùng với hình cờ cho biết mức độ rủi ro. (High – Mức độ dễ bị tấn công)
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa10.png)
* Spiders: sử dụng các AJAX Spiders để scan các AJAX request
* Active và Passive Scanning: quét lỗ hổng chủ động và bị động
* Fuzz : gửi những data không hợp lệ, không mong muốn
* Forced Browes : cho phép khám phá các thư mục và tệp

### Tiến hành Test
Click chuột phải vào link URL ở bên phía tab Sites, ta sẽ thấy mục Attack nhưng không kích hoạt được vì chưa Include in Context.
* Include in Context
* Để thực hiện kiểm tra thâm nhập ở chế độ Protected, ta cần include URL cần được kiểm tra trong Context.
* ![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa11.png)
* Chọn vào URL và nhấn OK để được include vào trong context. Khi nó được include vào trong context, 1 vòng tròn màu đỏ được hiển thị trong các icon của URL như hình bên dưới.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa12.png)
Bây giờ chúng ta đã có thể thực hiện các cuộc tấn công như quét động.
※　Khi thực hiện kiểm tra thâm nhập với OWASP ZAP, vui lòng chỉ đến trang web được quản lý bởi chính bạn trong môi trường cục bộ. Nếu nó được thực hiện cho một máy chủ được quản lý bởi một bên thứ ba được xuất bản trên Internet, nó có thể được coi là một truy cập trái phép.
Thực hiện test api login
* ![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa13.png)
* ![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa14.png)
Nếu có một lỗ hổng sau khi quét xong, nó sẽ được hiển thị trong Alert
Trong tab Active Scan, click vào 1 dòng bất kỳ , ta sẽ thấy được Owasp Zap đã giả lập request để tấn công và tìm lỗ hổng trong ứng dụng của bạn .Trong tab Request và Response ở phía trên sẽ hiển thị rõ những thông tin giả lập đó.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa15.png)
Owasp Zap đã làm giả các request và tìm ra lỗ hổng của ứng dụng.
### Lưu Session và xuất file Report
Bạn có thể lưu những thiết lập ở trên bằng cách. Nhập tên và chỗ cần lưu và nhấn OK là xong.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa16.png)
### Tạo Report
Sau khi Scan xong bạn có thể xuất file report cho kết quả vừa Scan. Có nhiều định dạng file report cho bạn lựa trọn như HTML, XML hay Markdown.
![](https://gitlab.com/trung-nb/public/-/raw/master/doxa_image/doxa17.png)

Tài liệu tham khảo
link [https://blog.vietnamlab.vn/2018/08/08/owasp-zap-de-test-security-cho-web-application-va-api/]<br/>
link [https://vdodata.vn/huong-dan-su-dung-owasp-zap-cong-cu-quet-lo-hong-bao-mat/]
