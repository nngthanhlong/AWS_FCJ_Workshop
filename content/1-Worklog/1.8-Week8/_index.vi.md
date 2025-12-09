---
title: "Worklog Tuần 8"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Hiểu rõ kiến trúc và cơ chế hoạt động của Amazon S3 (Bucket – Object – Storage Class).  
* Nắm được các tính năng quan trọng của S3: Versioning, Encryption, Lifecycle, Replication.  
* Thực hành quản lý dữ liệu trên S3: upload, phân quyền, public/private, static website hosting.  
* Áp dụng best practices về bảo mật và tối ưu chi phí khi làm việc với S3.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | -------- | ------------ | --------------- | -------------- |
| 2 | - Tìm hiểu tổng quan Amazon S3: <br>&emsp; + S3 là gì <br>&emsp; + Kiến trúc Bucket – Object <br>&emsp; + Khả dụng và mô hình lưu trữ | 27/10/2025   | 27/10/2025 | https://000057.awsstudygroup.com/vi/1-introduce/ |
| 3 | - Phân tích S3 Bucket vs Object <br>&emsp; + Cấu trúc URL <br>&emsp; + Prefix & folder ảo <br>&emsp; + Metadata, Key, ACL <br> - Phân loại Storage Classes | 28/10/2025   | 28/10/2025 | https://000057.awsstudygroup.com/vi/1-introduce/ |
| 4 | - Nghiên cứu tính năng bảo mật của S3: <br>&emsp; + Encryption (SSE-S3, SSE-KMS) <br>&emsp; + IAM Policy, Bucket Policy <br>&emsp; + Block Public Access <br> - Hiểu về Versioning | 29/10/2025   | 29/10/2025 | https://000057.awsstudygroup.com/vi/1-introduce/ |
| 5 | - Tìm hiểu Lifecycle Rules & Replication: <br>&emsp; + Chuyển storage class <br>&emsp; + CRR & SRR <br>&emsp; + Delete Marker <br> - S3 Storage Lens & phân tích chi phí | 30/10/2025   | 31/10/2025 | https://000057.awsstudygroup.com/vi/1-introduce/ |
| 6 | **Thực hành:** <br>&emsp; + Tạo bucket <br>&emsp; + Upload & quản lý object <br>&emsp; + Bật/tắt public access <br>&emsp; + Static website hosting <br>&emsp; + Cấu hình versioning & lifecycle <br>&emsp; + Test truy cập object | 31/10/2025   | 31/10/2025 | https://000057.awsstudygroup.com/vi/1-introduce/ |                                                                                      

### Kết quả đạt được tuần 8:

* Hiểu rõ nền tảng Amazon S3, bao gồm:  
  * Kiến trúc bucket–object  
  * Object metadata, prefix, folder ảo  
  * Cấu trúc URL truy cập object

* Nắm vững các lớp lưu trữ S3:  
  * Standard  
  * Standard-IA  
  * Intelligent-Tiering  
  * Glacier / Deep Archive  

* Áp dụng thành thạo các tính năng quan trọng:  
  * Versioning  
  * Lifecycle Management  
  * Replication (CRR, SRR)  
  * Block Public Access  
  * Encryption (SSE-S3, SSE-KMS)

* Thực hành đầy đủ trên S3:  
  * Tạo bucket  
  * Upload & phân quyền object  
  * Static website hosting  
  * Cấu hình versioning, lifecycle  
  * Kiểm tra public/private object qua URL  

* Nắm được best practices:  
  * Không public bucket  
  * Dùng encryption mặc định  
  * Tối ưu chi phí bằng lifecycle & storage class  
  * Tổ chức dữ liệu theo prefix để tăng hiệu năng


