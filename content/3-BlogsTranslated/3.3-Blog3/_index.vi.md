---
title: "Blog 3"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---



# **Khai thác sức mạnh của các quy tắc AWS IoT với các mẫu t**

Bởi Andrea Sichel và Avinash Upadhyaya ngày 17 tháng 9 2025 trong   [Advanced (300)](https://aws.amazon.com/blogs/iot/category/learning-levels/advanced-300/), [Architecture](https://aws.amazon.com/blogs/iot/category/architecture/), [AWS IoT Core](https://aws.amazon.com/blogs/iot/category/internet-of-things/aws-iot-platform/), [AWS Lambda](https://aws.amazon.com/blogs/iot/category/compute/aws-lambda/), [Best Practices](https://aws.amazon.com/blogs/iot/category/post-types/best-practices/), [Intermediate (200)](https://aws.amazon.com/blogs/iot/category/learning-levels/intermediate-200/), [Internet of Things](https://aws.amazon.com/blogs/iot/category/internet-of-things/), [Technical How-to Permalink  Share](https://aws.amazon.com/blogs/iot/category/post-types/technical-how-to/)

[AWS IoT Core](https://aws.amazon.com/iot-core/) là một dịch vụ được quản lý giúp bạn kết nối an toàn hàng tỷ thiết bị Internet of Things (IoT) với AWS cloud.  [AWS IoT rules engine](https://docs.aws.amazon.com/iot/latest/developerguide/iot-rules.html) là một thành phần của AWS IoT core và cung cấp khả năng giống như SQL để lọc, chuyển đổi và giải mã dữ liệu thiết bị IoT của bạn. Bạn có thể sử dụng các quy tắc  AWS IoT để định tuyến hơn 20 dịch vụ AWS và HTTP endpoints bằng cách sử dụng [AWS IoT rule actions](https://docs.aws.amazon.com/iot/latest/developerguide/iot-rule-actions.html). [Substitution templates](https://docs.aws.amazon.com/iot/latest/developerguide/iot-substitution-templates.html) là một khả năng trong các quy tắc của IoT giúp tăng cường dữ liệu JSON được trả về khi một quy tắc được kích hoạt và AWS IoT thực hiện một hành động. Bài đăng trên blog này khám phá cách các hành động quy tắc AWS IoT với các mẫu thay thế mở khóa các kiến trúc IoT đơn giản hơn, mạnh mẽ hơn. Bạn sẽ học được những cách đã được kiểm chứng để cắt giảm chi phí và tăng cường khả năng mở rộng. Thông qua các ví dụ thực tế của định tuyến tin nhắn và cân bằng tải,các giải pháp IoT  thông minh hơn, hiệu quả hơn

**Hiểu các thành phần cơ bản**

Mỗi quy tắc AWS IoT được xây dựng dựa trên ba thành phần cơ bản: một câu lệnh giống SQL xử lý việc lọc và chuyển đổi tin nhắn, một hoặc hơn các hành động quy tắc IoT chạy và định tuyến dữ liệu đến các AWS khác nhau và dịch vụ bên thứ ba, và các hàm tùy chọn có thể được sử dụng trong cả hai câu lệnh SQL và hành động quy tắc.

Sau đây là ví dụ về quy tắc AWS IoT và các thành phần của nó.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.3-Blog3/a1.png)

Câu lệnh SQL đóng vai trò là cổng xử lý quy tắc và xác định tin nhắn MQTT nào sẽ được xử lý dựa trên các mẫu chủ đề và điều kiện cụ thể. Quy tắc này sử dụng một câu lệnh tương tự SQL và hỗ trợ các mệnh đề SELECT, FROM và WHERE (để biết thêm thông tin, hãy xem [AWS IoT SQL reference)](https://docs.aws.amazon.com/iot/latest/developerguide/iot-sql-reference.html)).Trong cấu trúc này, mệnh đề FROM định nghĩa bộ lọc chủ đề MQTT, còn mệnh đề SELECT và WHERE chỉ định phần tử dữ liệu nào sẽ được trích xuất hoặc chuyển đổi từ tin nhắn đến.

Các hàm rất cần thiết cho các lệnh SQL và hành động của quy tắc IoT. Quy tắc AWS IoT cung cấp một bộ sưu tập [hàm](https://docs.aws.amazon.com/iot/latest/developerguide/iot-sql-functions.html)  nội bộ phong phú được thiết kế để chuyển đổi kiểu dữ liệu, thao tác chuỗi, thực hiện các phép tính toán học, xử lý dấu thời gian và nhiều hơn nữa. Ngoài ra, quy tắc AWS IoT còn cung cấp một bộ hàm bên ngoài giúp bạn truy xuất dữ liệu từ các dịch vụ AWS (chẳng hạn như Amazon DynamoDB, AWS Lambda, Amazon Secrets Manager và AWS IoT Device Shadow) và nhúng dữ liệu đó vào tải trọng tin nhắn của bạn. Các hàm này hỗ trợ các chuyển đổi dữ liệu phức tạp ngay trong quy trình xử lý quy tắc và loại bỏ nhu cầu xử lý bên ngoài. 

Các hành động quy tắc xác định đích đến và cách xử lý dữ liệu đã xử lý. Các quy tắc AWS IoT hỗ trợ một thư viện [các hành động quy tắc](https://docs.aws.amazon.com/iot/latest/developerguide/iot-rule-actions.html) tích hợp có thể truyền dữ liệu đến các dịch vụ AWS, chẳng hạn như AWS Lambda, Amazon Simple Storage Service (Amazon S3), Amazon DynamoDB và Amazon Simple Queue Service (Amazon SQS). Các hành động quy tắc này cũng có thể truyền dữ liệu đến các dịch vụ của bên thứ ba như Apache Kafka. Mỗi hành động quy tắc có thể được cấu hình với các tham số cụ thể chi phối cách dữ liệu được phân phối hoặc xử lý bởi dịch vụ đích.

**Mẫu thay thế: Viên ngọc ẩn**

Bạn có thể triển khai các hàm trong các câu lệnh SELECT và WHERE của quy tắc AWS IoT để chuyển đổi và chuẩn bị dữ liệu tin nhắn. Tuy nhiên, nếu áp dụng cách tiếp cận này quá thường xuyên, bạn có thể bỏ qua tùy chọn mạnh mẽ là sử dụng các mẫu thay thế và thực hiện chuyển đổi trực tiếp trong hành động của quy tắc IoT.

Các mẫu thay thế hỗ trợ các giá trị và hàm quy tắc được chèn động vào JSON của hành động quy tắc bằng cú pháp ${expression}. Các mẫu này hỗ trợ nhiều hàm câu lệnh SQL, chẳng hạn như thao tác dấu thời gian, thao tác mã hóa/giải mã, xử lý chuỗi và trích xuất chủ đề. Khi sử dụng các mẫu thay thế trong hành động quy tắc AWS IoT, bạn có thể triển khai định tuyến tinh vi giúp giảm đáng kể độ phức tạp trong các lớp kiến ​​trúc khác, mang lại các giải pháp AWS IoT hiệu quả và dễ bảo trì hơn.

**Các mẫu triển khai thực tế**

Hãy cùng tìm hiểu một số ví dụ thực tế cho thấy tính linh hoạt và sức mạnh của việc sử dụng mẫu thay thế trong các hành động quy tắc AWS IoT. Những ví dụ này sẽ minh họa cách tính năng này có thể đơn giản hóa quy trình xử lý dữ liệu IoT và mở ra những khả năng mới cho các ứng dụng IoT của bạn.

**Ví dụ 1: Phân phối tin nhắn có điều kiện bằng cách sử dụng các thuộc tính sổ đăng ký AWS IoT**

Hãy xem xét một kịch bản IoT phổ biến, trong đó một nền tảng phân phối tin nhắn thiết bị cho các đối tác kinh doanh khác nhau, và mỗi đối tác có hàng đợi xử lý tin nhắn SQS riêng. Các đối tác khác nhau sở hữu từng thiết bị trong đội tàu và mối quan hệ của họ được duy trì trong sổ đăng ký dưới dạng một thuộc tính gọi là partnerId.

Cách tiếp cận truyền thống bao gồm những điều sau:

* Tùy chọn 1 – Duy trì logic định tuyến đối tác trên thiết bị. Nhiều quy tắc AWS IoT dựa vào điều kiện WHERE để nhập tải trọng:
  * Yêu cầu thiết bị phải biết ID của đối tác.
  * Làm tăng độ phức tạp và bảo trì thiết bị.
  * Tạo ra mối lo ngại về bảo mật khi để lộ mã định danh đối tác.
  * Làm cho việc quản lý các thay đổi đối tác trở nên khó khăn.

* Tùy chọn 2 – Sử dụng hàm Lambda trung gian để truy xuất giá trị ID đối tác được liên kết với thiết bị từ sổ đăng ký AWS IoT và sau đó truyền thông báo đến hàng đợi SQS cụ thể của đối tác:
  * Thêm chi phí tính toán và truy vấn sổ đăng ký không cần thiết.
  * Có khả năng làm tăng độ trễ của thông báo.
  * Tạo thêm điểm lỗi.
  * Yêu cầu bảo trì logic định tuyến.
  * Có thể gặp phải giới hạn đồng thời của Lambda.

Sau đây là giải pháp và quy trình tinh tế hơn sử dụng mẫu thay thế và [tính năng thuộc tính lan truyền](https://docs.aws.amazon.com/iot/latest/developerguide/thing-types-propagating-attributes.html) AWS IoT mới: 

Chèn ID Đối tác dưới dạng thuộc tính vào sổ đăng ký AWS IoT.

* Sử dụng tính năng lan truyền thuộc tính để làm giàu thuộc tính người dùng MQTTv5 của bạn và xây dựng URL hàng đợi Amazon SQS một cách linh hoạt bằng cách sử dụng partnerId. của thiết bị. Xem ví dụ sau:

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.3-Blog3/a2.png)

Sử dụng giải pháp này, một thiết bị có partnerId=”partner123″ sẽ xuất bản một tin nhắn. Tin nhắn này sẽ tự động được định tuyến đến hàng đợi SQS “partner-queue-partner123”.

Những lợi ích của giải pháp này:

Việc sử dụng mẫu thay thế giúp đơn giản hóa đáng kể kiến ​​trúc và cung cấp giải pháp có khả năng mở rộng và bảo trì cho việc phân phối tin nhắn cụ thể cho từng đối tác. Giải pháp,

  * Loại bỏ nhu cầu về tài nguyên tính toán bổ sung.
  * Cung cấp định tuyến tức thì mà không làm tăng độ trễ.
  * Đơn giản hóa việc quản lý mối quan hệ đối tác thông qua các bản cập nhật trong sổ đăng ký AWS IoT. Ví dụ: việc giới thiệu đối tác mới có thể được cập nhật bằng cách sửa đổi các thuộc tính sổ đăng ký. Bản cập nhật này không yêu cầu bất kỳ bản cập nhật hoặc thay đổi nào đối với thiết bị hoặc logic định tuyến.
  * Duy trì bảo mật bằng cách không tiết lộ thông tin hàng đợi cho các thiết bị.

**Ví dụ 2: Cân bằng tải thông minh với Amazon Kinesis Data Firehose**

Hãy xem xét một kịch bản trong đó hàng triệu thiết bị xuất bản dữ liệu đo từ xa cho cùng một chủ đề. Cũng cần phải phân phối dữ liệu khối lượng lớn này trên nhiều luồng Amazon Data Firehose để tránh sự cố nghẽn băng thông khi lưu trữ dữ liệu vào bộ đệm Amazon S3.

Phương pháp truyền thống bao gồm:

* Cân bằng tải phía thiết bị:
  * Triển khai quản lý cấu hình để cung cấp các ID luồng khác nhau trên các thiết bị.
  * Yêu cầu các thiết bị bao gồm mục tiêu luồng trong thông báo của chúng.
  * Tạo nhiều quy tắc AWS IoT để khớp với các ID luồng cụ thể.
* Định tuyến dựa trên AWS Lambda:
  * Triển khai một hàm Lambda để phân phối thông báo trên các luồng.
  * Triển khai logic cân bằng tải tùy chỉnh.
  
Các phương pháp truyền thống cũng gây ra những tác động tiêu cực tương tự như đã nêu trong ví dụ trước (chi phí bảo trì, lỗ hổng bảo mật, độ phức tạp của thiết bị, chi phí bổ sung, độ trễ tăng và điểm lỗi). Hơn nữa, chúng còn đặt ra những thách thức cụ thể trong các tình huống khối lượng công việc lớn, chẳng hạn như nguy cơ bị giới hạn băng thông cao và quản lý luồng phức tạp.

Bằng cách tận dụng các mẫu thay thế quy tắc AWS IoT, bạn có thể triển khai giải pháp cân bằng tải không cần máy chủ, hợp lý hóa, có khả năng gán động các tin nhắn cho các luồng phân phối Firehose khác nhau bằng cách:

1. Tạo một số ngẫu nhiên từ 0-100000 bằng rand()*100000.
2. Chuyển đổi (ép kiểu) số ngẫu nhiên này thành một số nguyên.
3. Sử dụng phép toán modulo (mod) để lấy số dư khi chia cho 8.
4. Thêm số dư này (0-7) vào tên cơ sở “firehose_stream_”.
   
Kết quả là các tin nhắn được phân phối ngẫu nhiên trên tám luồng Amazon Data Firehose khác nhau (firehose_stream_0 đến firehose_stream_7). Xem ví dụ sau:

```json
{ 
  "ruleArn": 
    "arn:aws:iot:us-east-1:123456789012:rule/testFirehoseBalancing", 
  "rule": { 
    "ruleName": "testFirehoseBalancing", 
    "sql": "SELECT * FROM 'devices/+/telemetry'", 
    "description": "", 
    "createdAt": "2025-04-11T11:09:02+00:00", 
    "actions": [ 
        { "firehose": { 
            "roleArn": "arn:aws:iam::123456789012:role/service-role/firebaseDistributionRoleDemo", 
            "deliveryStreamName": "firehose_stream_${mod(cast((rand()*100000) as Int),8)}", 
            "separator": ",",
            "batchMode": false 
        } 
     } 
    ], 
  "ruleDisabled": false, 
  "awsIotSqlVersion": "2016-03-23" 
  }
}
```

Những lợi ích của giải pháp này:

Mô hình cân bằng tải linh hoạt này giúp xử lý khối lượng tin nhắn lớn bằng cách phân bổ tải trên nhiều luồng. Ưu điểm chính của phương pháp này nằm ở khả năng mở rộng. Bằng cách sửa đổi hàm modulo (xác định phần dư của phép chia, ví dụ: 5 mod 3 = 2), số bị chia (hiện được đặt thành 8) có thể được điều chỉnh để tương ứng với số luồng mong muốn. Ví dụ:

* Đổi thành mod(…, 4) để phân phối trên 4 luồng.
* Đổi thành mod(…, 16) để phân phối trên 16 luồng.
  
Sử dụng mẫu này giúp bạn dễ dàng tăng hoặc giảm quy mô kiến ​​trúc mà không cần thay đổi logic cốt lõi của quy tắc.

**Ví dụ 3: Sử dụng các câu lệnh CASE trong các mẫu thay thế để xây dựng logic định tuyến có điều kiện**

Hãy xem xét một tình huống mà bạn cần định tuyến dữ liệu thiết bị IoT của mình, tùy thuộc vào thiết bị cụ thể, đến chức năng Lambda dựa trên sản xuất hoặc đến chức năng Lambda Development/Testing (Dev/Test).

Cách tiếp cận truyền thống bao gồm những điều sau:

Cân bằng tải phía thiết bị:

* Triển khai quản lý cấu hình để cung cấp các ID môi trường khác nhau trên các thiết bị.
* Yêu cầu các thiết bị bao gồm ID môi trường trong thông báo của chúng.
* Tạo nhiều quy tắc AWS IoT để khớp với ID môi trường cụ thể.
  
Định tuyến dựa trên AWS Lambda:

* Triển khai một hàm Lambda để phân phối thông báo trên các hàm AWS Lambda khác nhau trên các môi trường sau khi kiểm tra với sổ đăng ký AWS IoT (hoặc cơ sở dữ liệu thay thế).

Các cách tiếp cận truyền thống cũng có những tác động tiêu cực tương tự như đã nêu trong các ví dụ trước.

Sau đây là giải pháp và quy trình tinh tế hơn sử dụng mẫu thay thế và [tính năng thuộc tính lan truyền](https://docs.aws.amazon.com/iot/latest/developerguide/thing-types-propagating-attributes.html) AWS IoT mới:

* Liên kết ID môi trường làm thuộc tính cho tất cả các thiết bị trong AWS IoT Registry
* Sử dụng tính năng lan truyền thuộc tính để làm phong phú thêm thuộc tính người dùng MQTTv5 của bạn
* Sử dụng thuộc tính lan truyền để xây dựng động hàm ARN của AWS Lambda trong câu lệnh CASE được nhúng trong định nghĩa hành động của AWS IoT Rule.

Xem ví dụ sau:

```json
{ 
  "ruleArn": 
    "arn:aws:iot:us-east-1:123456789012:rule/ConditionalActions", 
  "rule": { 
    "ruleName": "testLambdaConditions", 
    "sql": "SELECT * FROM 'devices/+/telemetry'", 
    "description": "", 
    "createdAt": "2025-04-11T11:09:02+00:00", 
    "actions": [ 
        { "lambda": { 
            "functionArn": 
                "arn:aws:lambda:us-east-1:123456789012:function:${CASE get(get_user_properties('environment'),0) 
                    WHEN \"PROD\" THEN \"message_handler_PROD\" 
                    WHEN \"DEV\" THEN \"message_handler_DEV\" 
                    WHEN NULL THEN \"message_handler_PROD\" 
                    ELSE \"message_handler_PROD\" END }",  
        } 
     } 
  ], 
  "ruleDisabled": false, 
  "awsIotSqlVersion": "2016-03-23" 
 }
}
```
Những lợi ích của giải pháp này:
 
Việc sử dụng mẫu thay thế giúp đơn giản hóa đáng kể kiến ​​trúc và cung cấp giải pháp có khả năng mở rộng và bảo trì cho việc phân phối tin nhắn cụ thể cho từng đối tác. Giải pháp, 

* Loại bỏ yêu cầu xác định quy tắc IoT và hành động quy tắc IoT riêng biệt cho từng điều kiện.
* Giúp bạn giảm chi phí sử dụng quy tắc IoT và hành động quy tắc IoT.

**Kết luận:**

Bài đăng trên blog này đã khám phá cách các mẫu thay thế cho quy tắc AWS IoT có thể chuyển đổi các kiến ​​trúc IoT phức tạp thành các giải pháp tinh tế và hiệu quả. Các ví dụ đã chứng minh rằng các mẫu thay thế không chỉ là một tính năng – chúng là một công cụ kiến ​​trúc mạnh mẽ tận dụng các khả năng của AWS IoT để giải quyết hiệu quả các thách thức phức tạp mà không làm tăng thêm độ phức tạp hoặc chi phí. Các mẫu thay thế cung cấp một phương pháp tiếp cận không cần máy chủ, có khả năng mở rộng, giúp loại bỏ nhu cầu về tài nguyên tính toán bổ sung hoặc logic phía máy khách phức tạp. Phương pháp này không chỉ giảm chi phí vận hành mà còn mang lại lợi ích chi phí ngay lập tức bằng cách loại bỏ các tài nguyên tính toán không cần thiết và đơn giản hóa kiến ​​trúc tổng thể.
Lần tới khi bạn thấy mình đang thiết kế các mẫu định tuyến tin nhắn AWS IoT hoặc gặp phải các thách thức về khả năng mở rộng, hãy cân nhắc xem mẫu thay thế có thể cung cấp giải pháp đơn giản và hiệu quả hơn như thế nào. Bằng cách tận dụng các tính năng mạnh mẽ của AWS IoT, bạn có thể tạo ra các giải pháp IoT dễ bảo trì, tiết kiệm chi phí và có khả năng mở rộng hơn, thực sự phục vụ nhu cầu kinh doanh của bạn.
Hãy nhớ rằng: Giải pháp đơn giản nhất thường là giải pháp tinh tế nhất. Với các mẫu thay thế quy tắc AWS IoT, sự đơn giản đó được tích hợp sẵn.


---

