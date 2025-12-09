---
title: "Worklog Tuần 6"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Hiểu và sử dụng thành thạo **AWS CLI** để quản lý tài nguyên AWS.
* Nắm được cơ chế profile, cấu hình region, output format.
* Thực hành tương tác với:
  * S3
  * SNS
  * IAM
  * VPC
  * EC2
* Hiểu cơ bản về **Amazon DynamoDB**, mô hình NoSQL, table, partition key, sort key.
* Thực hành đầy đủ CRUD và GSI trên DynamoDB bằng Console & CloudShell.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2   | - **Cài đặt AWS CLI** <br>&emsp; + Tải AWS CLI từ trang chủ AWS <br>&emsp; + Cài đặt trên Windows/macOS/Linux <br> - **Cấu hình AWS CLI cơ bản** <br>&emsp; + Chạy lệnh `aws configure` <br>&emsp; + Nhập Access key ID, Secret access key, Region, Output format <br>&emsp; + Kiểm tra kết nối với `aws s3 ls` | 13/11/2025 | 13/11/2025 | https://000011.awsstudygroup.com/vi/ |
| 3   | - **Tạo và sử dụng profile** <br>&emsp; + Tạo thêm profile ngoài default bằng `--profile` <br>&emsp; + Chỉ định profile qua biến môi trường `AWS_PROFILE` <br>&emsp; + Kiểm tra profile với `aws s3 ls --profile <tên_profile>` <br> - **Kiểm tra AWS CLI với S3** <br>&emsp; + Liệt kê bucket: `aws s3 ls` <br>&emsp; + Upload file: `aws s3 cp file.txt s3://bucket-name/` <br>&emsp; + Download file: `aws s3 cp s3://bucket-name/file.txt ./` | 14/11/2025 | 14/11/2025 | https://000011.awsstudygroup.com/vi/ |
| 4   | - **Thực hành AWS CLI với SNS** <br>&emsp; + Tạo topic SNS: `aws sns create-topic --name MyTopic` <br>&emsp; + Đăng ký subscriber: `aws sns subscribe --topic-arn <ARN> --protocol email --notification-endpoint example@gmail.com` <br>&emsp; + Gửi thông báo: `aws sns publish --topic-arn <ARN> --message "Hello SNS"` <br> - **AWS CLI với IAM** <br>&emsp; + Tạo user và nhóm IAM <br>&emsp; + Gán policy và quyền truy cập <br>&emsp; + Kiểm tra quyền với lệnh AWS CLI | 15/11/2025 | 15/11/2025 | https://000011.awsstudygroup.com/vi/ |
| 5   | - **Amazon DynamoDB – làm quen** <br>&emsp; + Tạo table DynamoDB <br>&emsp; + Thêm, sửa, xóa item <br>&emsp; + Kích hoạt tự động xóa item hết hạn <br> - **DynamoDB – sao lưu & khôi phục** <br>&emsp; + Tạo backup table <br>&emsp; + Khôi phục table tại thời điểm nhất định <br>&emsp; + Kiểm tra khôi phục dữ liệu thành công | 16/11/2025 | 16/11/2025 | https://000060.awsstudygroup.com/vi/ |
| 6   | - **Amazon DynamoDB – nâng cao / Thực hành** <br>&emsp; + Thêm chỉ số phụ (Global/Local Secondary Index) <br>&emsp; + Tối ưu query & scan <br>&emsp; + Kiểm tra tính năng TTL (Time To Live) <br> - **Dọn dẹp tài nguyên DynamoDB** <br>&emsp; + Xóa bảng thử nghiệm không cần thiết <br>&emsp; + Đảm bảo không phát sinh chi phí | 17/11/2025 | 17/11/2025 | https://000060.awsstudygroup.com/vi/ |

### Kết quả đạt được tuần 6:
**AWS CLI**
  * Cài đặt và cấu hình AWS CLI cơ bản.
  * Nhập Access Key ID, Secret Access Key, Region và Output format.
  * Kiểm tra kết nối AWS bằng `aws s3 ls`.
  * Tạo và sử dụng profile, chỉ định profile qua biến môi trường.
  * Thực hành quản lý S3: liệt kê bucket, upload/download file.
  * Thực hành SNS: tạo topic, đăng ký subscriber, gửi thông báo.
  * Thực hành IAM: tạo user và nhóm, gán policy, kiểm tra quyền truy cập.

**Amazon DynamoDB**
  * Làm quen với table, partition key, sort key.
  * Thực hành CRUD: thêm, sửa, xóa item.
  * Kích hoạt TTL (tự động xóa item hết hạn).
  * Tạo backup table và khôi phục dữ liệu.
  * Thêm Global/Local Secondary Index.
  * Tối ưu truy vấn query & scan.
  * Dọn dẹp table thử nghiệm, đảm bảo không phát sinh chi phí.


