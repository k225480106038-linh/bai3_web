# Bài tập 3   : Môn phát triển ứng dụng trên nền web

## Giảng viên  : Đỗ Duy Cốp

## Lớp học phần: 58KTPM

## Ngày giao   : 2025-10-24 13:50

## Hạn nộp     : 2025-11-05 00:00

--------------------------------------------------
Yêu cầu     : LẬP TRÌNH ỨNG DỤNG WEB trên nền linux
1. Cài đặt môi trường linux: SV chọn 1 trong các phương án
 - enable wsl: cài đặt docker desktop
 - enable wsl: cài đặt ubuntu
 - sử dụng Hyper-V: cài đặt ubuntu
 - sử dụng VMware : cài đặt ubuntu
 - sử dụng Virtual Box: cài đặt ubuntu
- Cài  enable wsl: cài đặt ubuntu
   Cài đặt ubuntu.
    <img width="964" height="992" alt="image" src="https://github.com/user-attachments/assets/9d91a830-4590-4a5c-a271-91ae9a134321" />


2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
   
  <img width="1917" height="952" alt="image" src="https://github.com/user-attachments/assets/ca2b8e2e-a43a-43f0-94fb-6908882cfa36" />


3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau:mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)

<img width="1917" height="951" alt="image" src="https://github.com/user-attachments/assets/c6602169-38fd-4e66-a281-0e37d8ac0a98" />


4. Lập trình web frontend+backend:
 SV chọn 1 trong các web sau:

 4.1 Web thương mại điện tử
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
   <img width="1285" height="865" alt="image" src="https://github.com/user-attachments/assets/13a80ff0-c197-48ce-9d9c-87b1e43f2785" />

 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
   <img width="1515" height="871" alt="image" src="https://github.com/user-attachments/assets/a847134d-2dc7-491b-a2d8-7b740cb0386f" />

 - Có tính năng liệt kê các sản phẩm bán chạy ra trang chủ
 - Có tính năng liệt kê các nhóm sản phẩm
 - Có tính năng liệt kê sản phẩm theo nhóm
 - Có tính năng tìm kiếm sản phẩm
 - Có tính năng chọn sản phẩm (đưa sản phẩm vào giỏ hàng, thay đổi số lượng sản phẩm trong giỏ, cập nhật tổng tiền)
 - Có tính năng đặt hàng, nhập thông tin giao hàng => được 1 đơn hàng.
 - Có tính năng dành cho admin: Thống kê xem có bao nhiêu đơn hàng, call để xác nhận và cập nhật thông tin đơn hàng. chuyển cho bộ phận đóng gói, gửi bưu điện, cập nhật mã COD, tình trạng giao hàng, huỷ hàng,...
 - Có tính năng dành cho admin: biểu đồ thống kê số lượng mặt hàng bán được trong từng ngày. (sử dụng grafana)
 - backend: sử dụng nodered xử lý request gửi lên từ javascript, phản hồi về json.
   
 4.2 Web IOT: Giám sát dữ liệu IOT.
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - hiển thị giá trị mới nhất của các thông số đang giám sát, khi click vào thì hiển thị đồ thị lịch sử quá trình thay đổi (gọi grafana iframe để hiển thị)
 - backend: Sử dụng nodered để đọc dữ liệu từ các cảm biến (có thể dùng api online để lấy dữ liệu theo giời gian thực), 
   nodered sẽ lưu dữ liệu mới nhất (dạng update) vào cơ sở dữ liệu mariadb (sử dụng phpmyadmin để tạp table và quản trị lần đầu)
   nodered sẽ lưu dữ liệu (insert) vào influxdb để lưu giá trị lịch sử, để cho grafana dùng để hiển thị biểu đồ.
   
5. Nginx làm web-server
 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
   <img width="1425" height="666" alt="image" src="https://github.com/user-attachments/assets/a010861e-db22-409d-9a93-6aa8a75bb9dd" />

 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
  <img width="1607" height="926" alt="image" src="https://github.com/user-attachments/assets/2f80f7e1-8f72-4546-872d-51037a4ef9ec" />


 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7c927ef2-9929-4dde-b938-7d1f34efbc15" />

Yêu cầu sinh viên lưu code trên github
có file readme.md có hình ảnh + text: ghi lại nhật ký quá trình làm bài.

