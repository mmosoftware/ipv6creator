Hướng dẫn cài đặt hàng trăm IPv6 proxy trên VPS Linux
IPv6 là giao thức IP mới nhất và sẽ dần thay thế IPv4 hiện tại. Ưu điểm của IPv6 có thể kể đến:

- Số lượng rất nhiều, gần như vô tận

- Giá thành rẻ

- Khắc phục được nhiều hạn chế về routing của IPv4

Trong quá trình chuyển đổi lên IPv6, khách hàng có thể sẽ cần cài đặt Proxy để chuyển đổi từ mạng IPv4 tới IPv6. Trong bài viết này, chúng tôi sẽ hướng dẫn cài đặt proxy để tạo hàng trăm IPv6 một cách rất đơn giản.

1. Cài đặt phần mềm
LowendViet đã phát triển phần mềm giúp việc cài đặt Proxy IPv6 đơn giản hơn. Phần mềm này được LowendViet cung cấp miễn phí và có thể sử dụng được trên tất cả các VPS khác, không chỉ VPS của LowendViet.

Sau khi đăng nhập vào VPS, quý khách chỉ việc copy và dán lần lượt các câu lệnh sau:

Với hệ điều hành CentOS 8, 9 (khuyến cáo nên dùng)

yum update -y

wget https://github.com/mmosoftware/ipv6creator/blob/main/levip6 && chmod +x levip6 && ./levip6
Sau khi cài đặt phần mềm, quý khách sẽ được yêu cầu sử dụng lệnh levip6 để chạy lại phần mềm.



2. Sử dụng phần mềm
Sau khi cài đặt phần mềm, quý khách gõ levip6 để vào menu chính:



Bước 1: Tại giao diện của phần mềm, quý khách chọn menu 1 để kiểm tra xem tính năng IPv6 đã bật trên VPS hay chưa. Nếu chưa bật, quý khách chọn “Y” để bật lên.



Bước 2: Cài đặt IPv6 chính. Để cài đặt 1 IPv6 là IP chính, quý khách cần chọn menu 3 và điền các thông số IP chính mà nhà cung cấp đã cung cấp cho quý khách (nếu quý khách mua VPS trên lowendviet.com, quý khách cần ghi chú vào đơn hàng “cần thông tin IPv6” hoặc liên hệ CSKH trước khi mua hàng để được tư vấn chi tiết về các gói/IP có thể cấp được IPv6), bao gồm:

1. IP kèm netmask

Ví dụ: 2607:f8b0:4007:815::200e/64 (nếu netmask là 64)

hoặc 2607:f8b0:4007:815::200e/80 (nếu netmask là 80)

1. Gateway

Nếu nhà cung cấp chỉ cung cấp cho quý khách 1 dải IP ví dụ: 2607:f8b0:4007:815::/80, quý khách có thể đặt IP chính là : 2607:f8b0:4007:815::2, netmask là 80, gateway là 2607:f8b0:4007:815::1



Bước 3: Kiểm tra kết nối của IPv6. Quý khách chọn menu 6 để kiểm tra xem IPv6 có hoạt động hay chưa. Tại menu này, phần mềm sẽ thực hiện 2 kiểm tra:

1. Kết nối ra một trang check IP bên ngoài xem IPv6 hiện tại của quý khách là bao nhiêu

2. Ping tới ipv6.google.com xem mạng đã thông chưa



Nếu mạng đã thông, quý khách có thể tiến hành cài đặt IPv6 Proxy. Nếu mạng chưa thông, quý khách kiểm tra lại IPv6 chính hoặc liên hệ nhà cung cấp để kiểm tra cài đặt IPv6 đầu server.

Bước 4: Quý khách chọn menu 7 để cài đặt proxy. Quý khách sẽ được hỏi 2 câu hỏi:

1. Nhập số lượng proxy muốn khởi tạo. Mặc định phần mềm sẽ tạo 1 proxy. Quý khách nên tạo khoảng 100-200 proxy để đảm bảo ổn định tùy theo cấu hình VPS của quý khách. Trong ví dụ là cài 10 proxy.

2. Tạo password cho proxy. Nhập “Y” nếu quý khách muốn đặt password, nhập “n” phần mềm sẽ tạo password ngẫu nhiên.



Sau khi cài đặt, quý khách sẽ nhận được 1 link download file proxy đã khởi tạo. File được nén với phần mềm zip, quý khách sử dụng mật khẩu được hiển thị để giải nén. (File chỉ tồn tại được 15-20 phút, quý khách lưu ý lưu lại file trong thời gian này. Trong trường hợp quý khách để quá thời gian, hãy tạo thêm 1 proxy mới, phần mềm sẽ update lại toàn bộ proxy vào file mới).

Bất kì lúc nào, quý khách cũng có thể chạy lại phần mềm “levip6” để thêm (menu 7), xóa proxy cũ (menu 10) nếu cần.



Quý khách cũng có thể xem lại các proxy đã được khởi tạo bằng menu 8.



Quý khách cũng có thể đổi lại user/password proxy bằng menu 9 nếu cần.

1. Phần mềm sẽ hiển thị user/password hiện tại của proxy.

2. Quý khách chọn Y nếu cần thay đổi.

3. Nhập user mới

4. Nhập password mới

Nếu quý khách cần tạo proxy không cần user/pass hãy bỏ trống thông tin. Proxy sẽ trở thành không có thông tin user/password.



3. Kiểm tra IPv6 hoạt động
Có 2 cách để kiểm tra xem IPv6 Proxy đã hoạt động hay chưa.

Cách 1: Sử dụng trang dịch vụ của bên thứ 3: <https://proxy6.net/en/checker>

Quý khách chỉ cần điền proxy theo định dang: IP:PORT:USER:PASS vào ô check và tiến hành kiểm tra. Trang web sẽ cho kết quả Proxy đã hoạt động hay chưa.



Cách 2: Dùng trình duyệt firefox

Quý khách có thể vào phần cài đặt proxy Firefox và tiến hành cài đặt như hình sau.



Sau đó, khi kết nối đến 1 trang bất kỳ, Firefox sẽ hỏi username/password của proxy. Sau khi điền username/password, quý khách có thể truy cập vào trang web: <http://v6.testmyipv6.com/> để xem IPv6 đã hoạt động hay chưa. Hình dưới là IPv6 đã hoạt động hoàn hảo.



Chúc quý khách thành công. Nếu gặp khó khăn gì, quý khách đừng ngại liên hệ bộ phận chăm sóc khách hàng của LowendViet tại LowendViet fanpage nhé!
