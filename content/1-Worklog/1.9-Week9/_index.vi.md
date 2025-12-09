---
title: "Worklog Tuần 9"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

* Hiểu kiến trúc và cách thức hoạt động của **Amazon Route 53**, đặc biệt là **Hybrid DNS** kết hợp với hệ thống DNS on-premise.
* Thành thạo sử dụng **CloudWatch** để:
  * Thu thập logs & metrics
  * Tạo cảnh báo (Alarm)
  * Xây Dashboard giám sát
  * Theo dõi container với Container Insights
* Nắm được mô hình giám sát tập trung và tự động hóa phản ứng theo sự kiện.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|-----|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|------------------|----------------|
| 2   | **Route 53 – Kiến trúc DNS & Hybrid DNS** <br> - Ôn lại mô hình DNS truyền thống (Authoritative, Recursive). <br> - Tìm hiểu tổng quan Amazon Route 53: <br> &emsp; • Public Hosted Zone <br> &emsp; • Private Hosted Zone <br> &emsp; • Quy trình phân giải DNS trên AWS. <br> - Phân tích DNS on-premise và nhu cầu Hybrid DNS. <br> - Tìm hiểu Route 53 Resolver và vai trò của nó. <br> - Ôn tập các record phổ biến: A, AAAA, CNAME, Alias… <br> - Vẽ sơ đồ DNS hoạt động trước và sau khi tích hợp Route 53.                                                | 03/11/2025 | 03/11/2025      | https://000010.awsstudygroup.com/vi/ |
| 3   | **Route 53 – Hybrid DNS** <br> - Tìm hiểu Outbound Endpoints: cách AWS gửi query về on-premise. <br> - Tìm hiểu Inbound Endpoints: điểm nhận query từ on-premise. <br> - Cấu hình Route 53 Resolver Rules: <br> &emsp; • Forwarding rule <br> &emsp; • Conditional rule <br> - Demo: tạo thử Outbound + Inbound endpoint. <br> - Thử nghiệm phân giải tên giữa AWS ↔ on-premise. <br> - Tổng hợp lỗi thường gặp: timeout, loop, rule conflict, network unreachable. | 04/11/2025 | 04/11/2025       | https://000010.awsstudygroup.com/vi/ |
| 4   | **AWS CloudWatch Workshop – Metrics & Logs** <br> - Hiểu kiến trúc giám sát CloudWatch. <br> - Phân tích cấu trúc Metrics: Namespace, Dimension, Retention. <br> - Phân biệt Logs: Log group, Log stream, Log event. <br> - Demo: <br> &emsp; • Cài CloudWatch Agent lên EC2. <br> &emsp; • Gửi logs hệ thống lên CloudWatch. <br> &emsp; • Xem metrics CPU, RAM, Network. <br> - Học cách tối ưu chi phí CloudWatch.                                                                                                                        | 05/11/2025 | 05/11/2025       | https://000008.awsstudygroup.com/vi/ |
| 5   | **AWS CloudWatch Workshop – Alarms & Automation** <br> - Tạo Metric Alarm theo ngưỡng tùy chỉnh. <br> - Tạo Log Filter → Log Alarm. <br> - Tích hợp SNS để gửi thông báo. <br> - Tạo Composite Alarm theo nhiều điều kiện. <br> - Bài tập mô phỏng thực tế: <br> &emsp; • CPU > 70% → gửi cảnh báo → Auto Scaling scale-out. <br> &emsp; • EC2 log ERROR → gửi thông báo qua email.                                                                                       | 06/11/2025 | 06/11/2025       | https://000008.awsstudygroup.com/vi/ |
| 6   | **AWS CloudWatch Workshop – Dashboard & Container Insights** <br> - Tạo CloudWatch Dashboard hiển thị: <br> &emsp; • CPU, RAM, Network <br> &emsp; • ALB request count <br> &emsp; • RDS metrics <br> - Thiết kế dashboard chuẩn best practice (nhóm panel, chú thích, màu sắc). <br> - Tìm hiểu EventBridge & vai trò trong tự động hóa. <br> - Container Insights: <br> &emsp; • Thu thập metrics ECS/EKS. <br> &emsp; • Điều tra lỗi container restart, OOMKilled. <br> - Cleanup toàn bộ tài nguyên. | 07/11/2025 | 07/11/2025       | https://000008.awsstudygroup.com/vi/ |                                                                                         


### Kết quả đạt được tuần 9:
**1. Route 53 & Hybrid DNS**

* Hiểu rõ mô hình DNS truyền thống và DNS trong môi trường AWS.
* Nắm vững các thành phần trong Route 53:
  * Public Hosted Zone
  * Private Hosted Zone
  * Record types (A, AAAA, CNAME, Alias)
  * Route 53 Resolver
* Hiểu kiến trúc **Hybrid DNS** giữa on-premise và AWS.
* Cấu hình và kiểm thử được:
  * **Outbound Endpoint** để AWS gửi query về DNS on-premise.
  * **Inbound Endpoint** để on-premise gửi query vào AWS.
  * **Resolver Rules** (Forwarding rule / Conditional rule).
* Thực hành phân giải DNS 2 chiều:
  * EC2 trong VPC → DNS on-premise.
  * DNS on-premise → Private Hosted Zone của AWS.
* Biết cách xử lý các lỗi thường gặp:
  * DNS timeout
  * Forwarding loop
  * Sai rule priority
  * Endpoint không thể attach vào VPC
* Tự vẽ và phân tích sơ đồ kiến trúc hệ thống Hybrid DNS hoàn chỉnh.


**2. CloudWatch Metrics & Logs**

* Hiểu kiến trúc giám sát của Amazon CloudWatch và vai trò trong hệ thống AWS.
* Nắm được cách thức hoạt động của Metrics:
  * Namespace
  * Dimension
  * Statistic (Average, Sum, Maximum)
  * Metric retention 15 tháng
* Thu thập Logs thông qua:
  * CloudWatch Log Groups
  * Log Streams
  * Log Events
* Cài đặt và cấu hình **CloudWatch Agent** để gửi:
  * System logs
  * Application logs
  * Custom metrics (CPU, RAM, Disk, Network)

---

**3. CloudWatch Alarm & Tự động hóa**

* Tạo và cấu hình được:
  * **Metric Alarm** theo ngưỡng CPU, Network…
  * **Log Metric Filter** để phát hiện Error/Warning trong logs.
  * **Log Alarm** dựa trên filter pattern.
* Tích hợp Alarm với SNS:
  * Gửi email cảnh báo.
  * Gửi thông báo khi tài nguyên vượt ngưỡng.
* Thực hiện mô hình Automation:
  * CPU > 70% → gửi cảnh báo → kích hoạt Auto Scaling Scale Out.
  * Xuất hiện ERROR trong ứng dụng → gửi thông báo ngay lập tức.
* Có khả năng phân tích nguyên nhân qua metrics/logs để giảm MTTR.

---

**4. CloudWatch Dashboard & Container Insights**

* Tạo và tùy chỉnh Dashboard để giám sát:
  * EC2 (CPU, RAM, Network)
  * ALB (Request count, Target health)
  * RDS (Latency, Connections)
  * Custom metrics
* Biết cách nhóm widgets khoa học để giám sát theo module.
* Sử dụng Container Insights để theo dõi containers:
  * CPU/memory usage theo pod/task
  * Lỗi container restart, OOMKilled
  * Thống kê deployment, node health
* Hiểu cách vận hành monitoring chuẩn DevOps/SRE:
  * Observability
  * Alerting
  * Distributed logs
  * Telemetry data pipeline

---

**5. Kỹ năng quản lý tài nguyên**

* Thực hiện cleanup tài nguyên đúng cách để tránh phát sinh chi phí.
* Có khả năng nhận biết tài nguyên nào gây tốn phí trong CloudWatch:
  * Metric storage
  * Log ingestion
  * High-resolution metrics
  * Dashboard widgets
