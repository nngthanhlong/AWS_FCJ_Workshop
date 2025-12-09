---
title: "Worklog Tuần 7"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Hiểu khái niệm và lợi ích của Amazon RDS so với cơ sở dữ liệu trên EC2.  
* Triển khai và quản lý DB instance với các engine phổ biến (Aurora, MySQL, PostgreSQL, SQL Server, Oracle).  
* Thực hành các tính năng quản lý: Multi-AZ, Read Replicas, Snapshots, Backup & Restore.  
* Quản lý bảo mật, mã hóa dữ liệu, IAM Policy và VPC Subnet Group.  
* Theo dõi, ghi log và tối ưu hiệu năng DB.  
* Dọn dẹp tài nguyên sau thực hành.

### Các công việc cần triển khai trong tuần này:
 Thứ | Công việc                                                                                                                                                                                                                                                                       | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Giới thiệu Amazon RDS và các hệ quản trị cơ sở dữ liệu được hỗ trợ <br> - Tìm hiểu lợi ích của RDS so với DB trên EC2 <br> - Khởi tạo VPC và DB Subnet Group cho DB instances                                                                                               | 20/10/2025   | 20/10/2025      | https://000005.awsstudygroup.com/vi/   |
| 3   | - Tạo DB instance cơ bản (MySQL hoặc PostgreSQL) <br> - Triển khai Multi-AZ deployment <br> - Thử failover giữa các AZ <br> - Thiết lập cấu hình sao lưu tự động và cửa sổ bảo trì                                                                                          | 21/10/2025   | 21/10/2025      | https://000005.awsstudygroup.com/vi/   |
| 4   | - Tạo và quản lý Read Replicas <br> - Snapshot DB và khôi phục từ snapshot <br> - Mở rộng lưu trữ và thay đổi loại instance <br> - Kiểm tra các hạn chế Multi-AZ và Read Replicas                                                                                              | 22/10/2025   | 22/10/2025      | https://000005.awsstudygroup.com/vi/   |
| 5   | - Thiết lập bảo mật DB: IAM Role, KMS encryption, Security Group, Public/Private endpoints <br> - Thực hành di chuyển dữ liệu với AWS DMS & SCT                                                                                                                                | 23/10/2025   | 23/10/2025      | https://cloudjourney.awsstudygroup.com/   |
| 6   | - **Theo dõi và tối ưu RDS:** <br> &emsp; + CloudWatch Metrics & Alarms: giám sát CPU, IOPS, Storage, DatabaseConnections <br> &emsp; + Enhanced Monitoring: theo dõi hệ điều hành chi tiết <br> &emsp; + Performance Insights: phân tích truy vấn và tối ưu <br> &emsp; + Kiểm tra log, RDS Events & CloudTrail | 24/10/2025   | 24/10/2025      | https://000005.awsstudygroup.com/vi/   |
| 6   | - **Dọn dẹp DB instance và tài nguyên:** <br> &emsp; + Xóa DB instances, Multi-AZ, Read Replicas <br> &emsp; + Xóa DB Snapshots (thủ công và tự động) <br> &emsp; + Xóa DB Subnet Groups <br> &emsp; + Xóa Security Groups liên quan <br> &emsp; + Kiểm tra trên Console & CLI, ghi chú quy trình dọn dẹp | 24/10/2025   | 24/10/2025      | https://000005.awsstudygroup.com/vi/   |



### Kết quả đạt được tuần 7:

* Hiểu rõ Amazon RDS là dịch vụ quản lý cơ sở dữ liệu quan hệ, khác biệt so với DB trên EC2.  
* Triển khai thành thạo DB instances với các engine phổ biến: MySQL, PostgreSQL, Aurora, SQL Server, Oracle.  
* Sử dụng Multi-AZ để tăng tính sẵn sàng và thử nghiệm failover thành công.  
* Quản lý Read Replicas và Snapshots để mở rộng khả năng đọc và phục hồi dữ liệu.  
* Thực hành mở rộng lưu trữ và thay đổi loại instance mà không gián đoạn dịch vụ.  
* Triển khai bảo mật DB: IAM Role, KMS encryption, Security Group và quản lý Public/Private endpoints.  
* Thực hành di chuyển dữ liệu với AWS DMS & SCT.  
* Theo dõi hiệu năng và log RDS qua CloudWatch, Performance Insights, Enhanced Monitoring và CloudTrail.  
* Dọn dẹp tài nguyên và ghi chép quy trình thực hành đầy đủ.



