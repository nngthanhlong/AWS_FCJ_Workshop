---
title: "Worklog Tuần 4"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Cấp quyền cho ứng dụng truy cập dịch vụ AWS với IAM Role

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                 | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Giới thiệu tổng quan về cách cấp quyền truy cập cho ứng dụng trên AWS <br> - Tìm hiểu lý do không nên sử dụng access key/secret access key trực tiếp trong ứng dụng                                   | 29/09/2025   | 29/09/2025      | https://000048.awsstudygroup.com/vi/   |
| 3   | - Thực hành sử dụng access key và secret access key trong ứng dụng <br> - Kiểm tra khả năng truy cập các dịch vụ AWS (S3, EC2) từ ứng dụng                                                   | 30/09/2025   | 30/09/2025      | https://000048.awsstudygroup.com/vi/   |
| 4   | - Tìm hiểu IAM Role trên EC2 <br> - Tạo IAM Role với policy phù hợp <br> - Gắn IAM Role vào EC2 instance <br> - Thử nghiệm truy cập dịch vụ AWS mà không cần access key trực tiếp                       | 01/10/2025   | 01/10/2025      | https://000048.awsstudygroup.com/vi/   |
| 5   | - Cấu hình ứng dụng sử dụng IAM Role <br> - Thử nghiệm truy cập S3, DynamoDB hoặc các dịch vụ khác từ ứng dụng đang chạy trên EC2 <br> - Quan sát logs và xác nhận quyền truy cập                           | 02/10/2025   | 02/10/2025      | https://000048.awsstudygroup.com/vi/   |
| 6   | - Dọn dẹp tài nguyên đã tạo trong tuần: xóa IAM Role, policies, EC2 thử nghiệm <br> - Ghi chép lại toàn bộ quy trình cấp quyền và bài học kinh nghiệm <br> - Chuẩn bị kiến thức cho tuần tiếp theo | 03/10/2025   | 03/10/2025      | https://000048.awsstudygroup.com/vi/   |



### Kết quả đạt được tuần 4:

* Hiểu cơ chế cấp quyền truy cập cho ứng dụng trên AWS:
  * Khái niệm IAM Role và vai trò trong bảo mật
  * Khác biệt giữa sử dụng access key/secret access key và IAM Role
  * Nhận biết các rủi ro khi dùng access key trực tiếp trong ứng dụng

* Thực hành sử dụng access key/secret access key:
  * Cấu hình trong ứng dụng
  * Truy cập các dịch vụ AWS như S3, EC2
  * Quan sát logs và debug khi quyền truy cập không đủ

* Thực hành IAM Role trên EC2:
  * Tạo IAM Role với policy phù hợp
  * Gắn IAM Role vào EC2 instance
  * Cấu hình ứng dụng sử dụng IAM Role để truy cập dịch vụ AWS mà không cần access key
  * Kiểm tra truy cập thành công và ghi nhận kết quả

* Quản lý quyền và policy:
  * Hiểu cách tạo policy đúng chuẩn least-privilege
  * Thực hành gán policy cho IAM Role
  * Kiểm tra quyền truy cập từng dịch vụ từ ứng dụng

* Kỹ năng tổng hợp:
  * Tự tin triển khai ứng dụng trên EC2 với quyền truy cập an toàn
  * Nắm rõ các best practice trong quản lý quyền truy cập AWS
  * Ghi chép và dọn dẹp tài nguyên: xóa IAM Role, policies, EC2 thử nghiệm






