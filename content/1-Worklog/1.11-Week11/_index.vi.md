---
title: "Worklog Tuần 11"
date: 2025-09-10T15:39:35+07:00
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

* Hiểu và thực hành lưu trữ nội dung web tĩnh trên S3, tăng tốc bằng CloudFront.  
* Cấu hình quyền truy cập và tối ưu cache cho CloudFront distribution.  
* Làm quen với Amazon ElastiCache for Redis: tạo cluster, quản lý node và shards.  
* Thực hành scale cluster, quản lý parameter group và chạy trong VPC.  
* Nắm được các bước dọn dẹp tài nguyên để tránh phát sinh chi phí.


### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2   | - **CloudFront với S3 – Giới thiệu & Điều kiện cần thiết** <br>&emsp; + Tài khoản AWS <br>&emsp; + Quyền IAM với S3 và CloudFront <br>&emsp; + Chi phí dự kiến < $1/tháng <br> - **Thực hành** <br>&emsp; + Tạo bucket S3 <br>&emsp; + Tải lên tệp `index.html` | 17/11/2025 | 17/11/2025 | https://000094.awsstudygroup.com/vi/ |
| 3   | - **Cấu hình Amazon CloudFront** <br>&emsp; + Tạo distribution <br>&emsp; + Liên kết với S3 bucket <br>&emsp; + Kiểm tra truy cập nội dung web tĩnh <br> - **Dọn dẹp tài nguyên** <br>&emsp; + Xóa distribution CloudFront và bucket S3 khi không cần thiết | 18/11/2025 | 18/11/2025 | https://000094.awsstudygroup.com/vi/ |
| 4   | - **Kiểm tra, tối ưu & tham khảo** <br>&emsp; + Kiểm tra tốc độ tải nội dung <br>&emsp; + Tối ưu cache và quyền truy cập <br>&emsp; + Tài liệu tham khảo: Amazon S3 & CloudFront | 19/11/2025 | 19/11/2025 | https://000094.awsstudygroup.com/vi/ |
| 5   | - **Amazon ElastiCache for Redis – Giới thiệu & Tổng quan** <br>&emsp; + Thiết lập và quản lý cluster Redis <br>&emsp; + Tích hợp với EC2, CloudWatch, CloudTrail, SNS <br>&emsp; + Tự động phát hiện lỗi và khôi phục <br> - **Clusters & Nodes** <br>&emsp; + Tạo cluster, chọn instance, node type <br>&emsp; + Phân cấp dữ liệu, loại lưu trữ Standard/Memory-optimized | 20/11/2025 | 20/11/2025 | https://000061.awsstudygroup.com/vi/ |
| 6   | - **ElastiCache for Redis – Thực hành nâng cao** <br>&emsp; + Tạo và quản lý shards <br>&emsp; + Scale node và cluster <br>&emsp; + Quản lý parameter group <br>&emsp; + Chạy cluster trong VPC, subnet, security group <br>&emsp; + Kiểm tra số lượng node, shard và địa chỉ IP khả dụng | 21/11/2025 | 21/11/2025 | https://000061.awsstudygroup.com/vi/ |                                                                  


### Kết quả đạt được tuần 11:

**CloudFront với S3**
  * Hiểu cách hoạt động của S3 và CloudFront.
  * Tạo bucket S3 và upload file `index.html`.
  * Cấu hình quyền truy cập cho bucket.
  * Tạo CloudFront distribution và liên kết S3.
  * Kiểm tra truy cập nội dung web tĩnh qua CloudFront.
  * Tối ưu cache và tốc độ tải.
  * Dọn dẹp S3 và CloudFront để tránh chi phí.
  * Sử dụng IAM để phân quyền truy cập.

**Amazon ElastiCache for Redis**
  * Hiểu khái niệm cluster, node và shard.
  * Tạo cluster Redis và chọn node type phù hợp.
  * Thực hành scale cluster và shard.
  * Quản lý parameter group cơ bản.
  * Triển khai cluster trong VPC và cấu hình security group.
  * Kiểm tra khả năng tự phục hồi lỗi.
  * Dọn dẹp cluster sau khi thực hành.

