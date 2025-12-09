---
title: "Các bài blogs đã dịch"
date: 2025-09-10T15:39:35+07:00
weight: 3
chapter: false
pre: " <b> 3. </b> "
---


Tại đây sẽ là phần liệt kê, giới thiệu các blogs mà các bạn đã dịch.

###  [Blog 1 - Thông báo hỗ trợ Capacity Blocks cho Dịch vụ Tính toán Song song AWS](3.1-Blog1/)
Blog này giới thiệu tính năng hỗ trợ Amazon EC2 Capacity Blocks trong AWS Parallel Computing Service (PCS), giúp người dùng đặt trước và lên lịch sử dụng các instance GPU cho các workload AI/ML và HPC. Bạn sẽ tìm hiểu Capacity Blocks là gì, lý do chúng hữu ích cho các tác vụ huấn luyện mô hình, suy luận, mô phỏng khoa học; và cách PCS tận dụng tính năng này để cung cấp môi trường tính toán linh hoạt, dễ mở rộng và đáng tin cậy. Bài viết cũng hướng dẫn quy trình thiết lập Capacity Blocks trong PCS — từ mua block, tạo launch template, cấu hình compute node group — cho đến các best practices khi vận hành, cũng như thông tin về giá, vùng hỗ trợ và các sự kiện giám sát giúp đảm bảo vận hành liền mạch.
###  [Blog 2 - Thông báo Amazon EC2 M4 và M4 Pro Mac instances](3.2-Blog2/)
Blog này giới thiệu các Amazon EC2 M4 và M4 Pro Mac instances — thế hệ mới dành cho đội ngũ phát triển ứng dụng Apple cần hiệu năng build & test cao. Bạn sẽ tìm hiểu cách Apple silicon M4/M4 Pro mang lại tốc độ build cải thiện (tăng đến 20% so với M2 Mac), bộ nhớ hợp nhất lớn hơn, và 2 TB lưu trữ nội bộ giúp tăng tốc caching. Bài viết cũng hướng dẫn cách khởi tạo dedicated host, chọn AMI macOS phù hợp, cấu hình lưu trữ, và cài Xcode trong môi trường EC2. Ngoài ra, blog chia sẻ các lưu ý quan trọng khi vận hành EC2 Mac, các tùy chọn tích hợp CI/CD với AWS, và thông tin giá & vùng hỗ trợ, giúp đội ngũ Apple developers hiện đại hóa workflow trên AWS một cách linh hoạt và hiệu quả.
###  [Blog 3 - Khai thác sức mạnh của các quy tắc AWS IoT với các mẫu t](3.3-Blog3/)
Blog này giới thiệu cách tận dụng substitution templates trong AWS IoT Rules để tối ưu hóa kiến trúc IoT. Bạn sẽ tìm hiểu cách AWS IoT Core và rules engine dùng SQL-like syntax để lọc, chuyển đổi và định tuyến dữ liệu đến hơn 20 dịch vụ AWS. Bài viết giải thích vì sao substitution templates là “vũ khí bí mật” giúp đơn giản hóa kiến trúc, giảm phụ thuộc vào Lambda, cắt chi phí và tăng khả năng mở rộng. Blog cũng minh họa 3 tình huống thực tế: định tuyến tin nhắn theo partnerId từ IoT Registry, cân bằng tải thông minh qua nhiều Firehose streams bằng hàm rand() + mod, và chuyển hướng động đến các Lambda khác nhau bằng CASE. Qua các ví dụ này, bạn sẽ thấy cách xây dựng giải pháp IoT linh hoạt, không cần máy chủ và dễ bảo trì hơn nhờ khả năng chèn giá trị động trực tiếp trong hành động của AWS IoT Rule.
