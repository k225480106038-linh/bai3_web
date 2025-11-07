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
 4.2 Web IOT: Giám sát dữ liệu IOT.
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
   <img width="1806" height="895" alt="image" src="https://github.com/user-attachments/assets/bd12cddf-1e61-482e-8d7b-b1ecf9419821" />
   <img width="1818" height="660" alt="image" src="https://github.com/user-attachments/assets/33debee5-3734-4e9c-9fff-20cc80e45d8b" />


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

6. Kết luận.

Trong quá trình thực hiện bài tập, em đã triển khai trực tiếp trên máy tính thật (host vật lý) chạy hệ điều hành Ubuntu, thay vì máy ảo. Điều này giúp hệ thống hoạt động ổn định hơn, tận dụng tốt hiệu năng phần cứng và giảm độ trễ khi truyền dữ liệu giữa các container.

Em đã cài đặt và cấu hình đầy đủ môi trường Docker, sau đó sử dụng Docker Compose để triển khai thành công các dịch vụ:

MariaDB và phpMyAdmin (quản lý cơ sở dữ liệu),

Node-RED (xử lý dữ liệu cảm biến và cung cấp API),

InfluxDB (lưu trữ dữ liệu lịch sử),

Grafana (hiển thị biểu đồ trực quan),

Nginx (máy chủ web trung tâm, reverse proxy).

Ứng dụng web được xây dựng theo mô hình Single Page Application (SPA) với file index.html duy nhất, sử dụng JavaScript để xử lý giao diện động. Người dùng có thể đăng nhập, giám sát dữ liệu cảm biến theo thời gian thực, và xem đồ thị lịch sử được hiển thị trực quan thông qua Grafana.

Hệ thống vận hành thông suốt:

Node-RED chịu trách nhiệm thu thập, xử lý và lưu dữ liệu cảm biến vào MariaDB (dữ liệu mới nhất) và InfluxDB (dữ liệu lịch sử).

Nginx đóng vai trò máy chủ trung tâm, giúp truy cập tất cả dịch vụ thông qua tên miền tùy chỉnh, đảm bảo tính thống nhất và chuyên nghiệp.

Thông qua bài tập này, em đã nắm vững quy trình triển khai ứng dụng IoT trên nền Linux thật, từ cài đặt hệ điều hành, quản lý container đến cấu hình web server và bảo mật truy cập.
Bài làm giúp em củng cố kiến thức về Docker, Nginx, Node-RED, và cơ sở dữ liệu, đồng thời rèn luyện tư duy hệ thống và kỹ năng tích hợp công nghệ thực tế – một bước quan trọng để ứng dụng vào các dự án Web – IoT trong tương lai.


