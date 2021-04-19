# 1. API
## 1.1. API là gì?
API(***A**pplication **P**rogramming **I**nterface*) là phương thức trung gian kết nối giữa các ứng dụng và thư viện khác nhau. \
API cung cấp khả năng truy xuất đến một tập các hàm hay dùng, từ đó trao đổi dữ liệu giữa các ứng dụng.
## 1.2. Tại sao nên sử dụng API?
+ API sử dụng mã nguồn mở, dùng được với mọi client hỗ trợ XML, JSON.
+ API đáp ứng đầy đủ các thành phần HTTP: URI, request/response, caching,...
+ Mô hình web API dùng để hỗ trợ MVC như: unit test, injection, container, action result, filter, routing, controller. Nó cũng hỗ trợ RESTful đầy đủ các phương thức như: GET, POST, PUT, DELETE các dữ liệu
+ Được đánh giá là 1 trong những kiểu kiến trúc hỗ trợ tốt nhất cho các thiết bị băng thông bị giới hạn như smart phone, tablet...
## 1.3. API hoạt động như thế nào?
+ Đầu tiên là xây dựng URL API để bên thứ ba có thể gửi request dữ liệu đến máy chủ cung cấp dịch vụ thông qua giao thức HTTP/HTTPS.
+ Tại Server cung cấp nội dung, các ứng dụng nguồn sẽ kiểm tra và tìm đến tài nguyên thích hợp để tạo nội dung và trả về kết quả.
+ Server trả kết quả về dưới dạng JSON hoặc XML thông qua giao thức HTTP/HTTPS.
+ Tại nơi gửi request ban đầu, dữ liệu JSON/XML được parse để lấy data rồi thực hiện tiếp các hoạt động khác sử dụng dữ liệu đó.

# 2. JWT
## 2.1. JWT là gì?
**JWT (JSON Web Token)** là 1 tiêu chuẩn mở định nghĩa cách thức truyền tin an toàn giữa các thành viên được định dạng bằng JSON. Nó được xác thực và đánh dấu tin cậy nhờ chữ ký số. Phần chữ ký của JWT sẽ được mã hóa lại bằng **HMAC** hoặc **RSA**.
**Cấu trúc của chuỗi JWT:** bao gồm ba phần phân tách bằng dấu chấm (`.`):
+ Header\
  ```Chứa kiểu dư liệu và thuật toán sử dụng để mã hóa chuỗi JWT ```
+ Payload\
  ``` Chứa các thông tin mình muốn đặt trong chuỗi Token ```
+ Signature\
  ```Phần chữ ký này được tạo ra bằng cách mã hóa phần header, payload kèm theo 1 chuỗi secret(khóa bí mật)```
## 2.2. Khi nào nên sử dụng JWT?
+ **Ủy quyền**: Đây là kịch bản phổ biến nhất để sử dụng JWT.
  + Khi người dùng đã đăng nhập, mỗi yêu cầu tiếp theo sẽ kèm theo mã JWT cho phép họ truy cập được vào các routes, services và resource được cho phép với mã token đó.
+ **Trao đổi thông tin**: JWT là 1 cách thức tốt để trao đổi thông tin giữa các bên một cách an toàn: 
  + Nhờ vào "chữ ký" của nó, phía người nhận có thể biết được người gửi là ai.
  + Ngoài ra, trong chữ ký có cả phần sử dụng **header** và **payload** nên ta có thể xác minh nội dung có giả mạo hay không.
## 2.3. JWT hoạt động như thế nào?
+ Trong quá trình xác thực, khi người dùng đăng nhập thành công bằng thông tin đăng nhập của họ, JWT sẽ được trả lại.
