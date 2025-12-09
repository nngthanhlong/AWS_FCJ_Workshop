---
title: "Dọn dẹp Tài nguyên"
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

## Các Bước Dọn dẹp

- Xóa API Gateway stage/API đã tạo cho workshop.  
![image](/images/5-Workshop/5.6-Cleanup/api.png)
- Xóa các Lambda functions (Node.js, Python, suggest).  
![image](/images/5-Workshop/5.6-Cleanup/lambda.png)
- Xóa IAM roles/policies được tạo riêng cho Lambda (nếu không còn cần thiết).
![image](/images/5-Workshop/5.6-Cleanup/iam_role.png)  
- Kiểm tra CloudWatch Log Groups, đặt retention ngắn hoặc xóa.
![image](/images/5-Workshop/5.6-Cleanup/cloudwatch.png)  
- Đảm bảo không còn tài nguyên nào phát sinh chi phí (S3 buckets tạm, Secrets tạm nếu có).


## Lưu ý Chi phí

- Lambda/Logs/API Gateway có chi phí thấp nhưng vẫn nên xóa sau khi hoàn thành lab.  
- Nếu bạn tạo thêm tài nguyên khác (S3, KMS), xác nhận đã xóa hoặc đặt retention.