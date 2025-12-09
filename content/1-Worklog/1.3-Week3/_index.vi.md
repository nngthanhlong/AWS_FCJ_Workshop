---
title: "Worklog Tuần 3"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Tuần này hướng trọng tâm vào các dịch vụ Compute của AWS, với trọng điểm là Amazon EC2 cùng các dịch vụ hỗ trợ liên quan.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                                                | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Giới thiệu tổng quan về dịch vụ Compute trên AWS và vai trò của EC2 <br> - Chuẩn bị tài khoản AWS và IAM user cho thực hành <br> - Tìm hiểu các loại instance (General, Compute, Memory, GPU) <br> - Tìm hiểu về AMI, snapshot, cách backup EC2 | 22/09/2025   | 22/09/2025      | https://000004.awsstudygroup.com/vi/   |
| 3   | - Khởi tạo Microsoft Windows Server 2022 EC2 instance <br> - Khởi tạo Amazon Linux 2 EC2 instance <br> - Thực hành kết nối RDP vào Windows EC2 và SSH vào Linux EC2 <br> - Cài đặt các gói cơ bản trên EC2 (ví dụ: Web Server, Node.js)             | 23/09/2025   | 23/09/2025      | https://000004.awsstudygroup.com/vi/   |
| 4   | - Thực hành các thao tác quản lý EC2 cơ bản: <br>&emsp; + Start, Stop, Reboot, Terminate instance <br>&emsp; + Kiểm tra trạng thái instance, public IP, private IP <br>&emsp; + Quản lý Security Group, mở port cần thiết cho ứng dụng           | 24/09/2025   | 24/09/2025      | https://000004.awsstudygroup.com/vi/   |
| 5   | - Triển khai ứng dụng User Management trên Amazon Linux 2: cài đặt môi trường, upload code, chạy service <br> - Triển khai ứng dụng Node.js trên EC2 Windows: cài Node.js, deploy, chạy thử <br> - Kiểm tra kết nối từ máy local và web browser | 25/09/2025   | 25/09/2025      | https://000004.awsstudygroup.com/vi/   |
| 6   | - Quản lý chi phí và quyền truy cập với IAM: tạo policy, gán role, kiểm tra quyền user <br> - Theo dõi báo cáo usage & budget để kiểm soát chi phí <br> - Dọn dẹp tài nguyên tuần này: terminate EC2, delete volumes, detach AMI, xóa security group | 26/09/2025   | 26/09/2025      | https://000004.awsstudygroup.com/vi/   |




### Kết quả đạt được tuần 3:

* Hiểu tổng quan về dịch vụ Compute trên AWS và cách sử dụng các thành phần liên quan:
  * Amazon EC2
  * Auto Scaling
  * Amazon Lightsail
  * EFS, FSx
  * AMI, Snapshot

* Nắm vững các loại EC2 instance và thông số kỹ thuật:
  * General Purpose, Compute Optimized, Memory Optimized, Storage Optimized, GPU
  * Thông số vCPU, RAM, Burst, Network Performance

* Thao tác thành thạo trên EC2:
  * Khởi tạo và quản lý EC2 Windows và Linux
  * Kết nối RDP/SSH và cài đặt các package cơ bản
  * Quản lý Security Group, mở port cần thiết cho ứng dụng
  * Thực hành start, stop, reboot, terminate, kiểm tra trạng thái instance

* Hiểu và triển khai AMI, snapshot, backup:
  * Tạo AMI tùy chỉnh từ EC2
  * Thực hành snapshot EBS
  * Khôi phục EC2 từ AMI/snapshot

* Thực hành Auto Scaling cơ bản:
  * Tạo Launch Template
  * Tạo Auto Scaling Group
  * Kiểm tra khả năng scale out/scale in tự động

* Triển khai ứng dụng trên EC2:
  * Deploy User Management Application trên Amazon Linux 2
  * Deploy Node.js Application trên Windows EC2
  * Kiểm tra kết nối từ client và web browser, đảm bảo hoạt động ổn định

* Quản lý chi phí và quyền truy cập:
  * Cấu hình IAM, role, policy
  * Theo dõi báo cáo usage & budget
  * Nhận biết các chi phí tiềm ẩn và cách tối ưu

* Dọn dẹp tài nguyên sau thực hành:
  * Terminate EC2, delete volume, detach AMI, xóa Security Group
  * Giữ môi trường sạch sẽ cho tuần tiếp theo

* Kỹ năng tổng hợp:
  * Hiểu mối quan hệ giữa EC2, EBS, AMI, Auto Scaling
  * Có khả năng triển khai, kiểm thử và quản lý môi trường Compute trên AWS một cách độc lập




