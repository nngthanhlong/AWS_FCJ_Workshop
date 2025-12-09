---
title: "Worklog Tuần 2"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Tuần này tập trung tìm hiểu sâu hơn về các dịch vụ mạng trên AWS, bắt đầu từ VPC và các thành phần nền tảng cho đến những giải pháp kết nối nâng cao và hệ thống cân bằng tải.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                      | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                          |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | --------------------------------------- |
| 2   | - Tìm hiểu khái niệm VPC và cách AWS tổ chức mạng ảo <br> - Tạo VPC mới <br> - Tạo subnet public/private <br> - Thiết lập Route Table và gán route phù hợp                   | 15/09/2025   | 15/09/2025      | https://000003.awsstudygroup.com/vi/ |
| 3   | - Gắn Internet Gateway vào VPC <br> - Cấu hình route cho subnet public ra Internet <br> - Tạo NAT Gateway cho subnet private <br> - Kiểm tra kết nối EC2 public/private       | 16/09/2025   | 16/09/2025      | https://000003.awsstudygroup.com/vi/ |
| 4   | - Tìm hiểu Security Group & Network ACL <br> - So sánh SG và NACL <br> - Thử nghiệm: SG allow nhưng NACL deny để quan sát kết quả                                          | 17/09/2025   | 17/09/2025      | https://000003.awsstudygroup.com/vi/ |
| 5   | - Tìm hiểu ALB, NLB, GWLB <br> - Tạo ALB <br> - Tạo 2 EC2 chạy web server đơn giản <br> - Gắn EC2 vào Target Group <br> - Kiểm tra hoạt động load balancing                  | 18/09/2025   | 18/09/2025      | https://000003.awsstudygroup.com/vi/ |
| 6   | - Tìm hiểu VPC Peering <br> - Tạo 2 VPC và thiết lập Peering <br> - Kiểm tra giao tiếp giữa 2 EC2 ở hai VPC <br> - Tìm hiểu thêm về Transit Gateway                         | 19/09/2025   | 19/09/2025      | https://000003.awsstudygroup.com/vi/ |




### Kết quả đạt được tuần 2:

* Hiểu VPC là gì và nắm được các thành phần mạng cơ bản trong AWS bao gồm:
  * VPC
  * Subnet (Public / Private)
  * Route Table
  * Internet Gateway (IGW)
  * NAT Gateway

* Tự tạo và cấu hình một VPC hoàn chỉnh:
  * Tạo VPC mới
  * Tạo public subnet và private subnet
  * Gán Route Table cho từng subnet
  * Thiết lập đường route ra Internet

* Kết nối VPC với Internet thông qua:
  * Internet Gateway cho public subnet
  * NAT Gateway cho private subnet
  * Kiểm tra kết nối giữa các EC2 ở hai subnet để xác nhận hoạt động đúng

* Nắm rõ mô hình bảo mật mạng của AWS:
  * Hiểu sự khác nhau giữa Security Group và Network ACL
  * Biết cách cấu hình rule inbound/outbound
  * Thử nghiệm các trường hợp SG cho phép nhưng NACL chặn và ngược lại

* Triển khai hệ thống cân bằng tải cơ bản:
  * Tạo Application Load Balancer (ALB)
  * Tạo 2 EC2 đóng vai web server
  * Tạo và cấu hình Target Group
  * Kiểm thử hoạt động phân phối traffic giữa các EC2

* Hiểu các giải pháp kết nối VPC nâng cao:
  * Tìm hiểu VPC Peering
  * Tạo và cấu hình Peering giữa 2 VPC
  * Kiểm tra giao tiếp giữa EC2 ở hai VPC khác nhau
  * Nắm được vai trò của Transit Gateway trong hệ thống lớn

* Có khả năng xây dựng sơ đồ kiến trúc mạng:
  * Vẽ sơ đồ VPC
  * Sơ đồ ALB + EC2
  * Sơ đồ VPC Peering

* Có cái nhìn toàn diện về mô hình mạng AWS và tự tin thao tác các dịch vụ networking quan trọng.




