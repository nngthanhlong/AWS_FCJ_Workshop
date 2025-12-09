---
title: "Blog 1"
date: 2025-09-10T15:39:35+07:00
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Thông báo hỗ trợ Capacity Blocks cho Dịch vụ Tính toán Song song AWS

bởi Kareem Abdol-Hamid và Kyle Bush vào ngày 18 tháng 9 năm 2025 trong [AWS Parallel Computing Service](https://aws.amazon.com/blogs/hpc/category/compute/aws-parallel-computing-service/), [Compute](https://aws.amazon.com/blogs/hpc/category/compute/), [High Performance Computing](https://aws.amazon.com/vi/blogs/hpc/category/high-performance-computing/)

Bài viết này được đóng góp bởi Kareem Abdol-Hamid và Kyle Bush

Hôm nay, chúng tôi vui mừng thông báo rằng [Amazon EC2 Capacity Blocks](https://aws.amazon.com/ec2/capacityblocks/) cho Machine Learning hiện đã được hỗ trợ trong AWS Parallel Computing Service (AWS PCS). Tính năng này cho phép bạn dự trữ và lên lịch các instance Amazon EC2 tăng tốc GPU cho việc sử dụng trong tương lai, bao gồm dòng GPU NVIDIA Hopper và AWS Trainium.


[AWS PCS](https://aws.amazon.com/pcs/) là một dịch vụ được quản lý, giúp bạn dễ dàng chạy và mở rộng các khối lượng công việc HPC cũng như xây dựng các mô hình khoa học, kỹ thuật hoặc AI trên AWS bằng Slurm. Với việc bổ sung hỗ trợ Capacity Blocks, các tổ chức giờ đây có thể đảm bảo quyền truy cập đã được dự trữ vào tài nguyên tính toán tăng tốc khi cần thiết nhất, đồng thời vẫn duy trì sự đơn giản của dịch vụ được quản lý đầy đủ, chịu trách nhiệm vận hành cụm, cập nhật và quan sát.

**Capacity Blocks là gì?**

Capacity Blocks là một tính năng của EC2 cho phép khách hàng dự trữ các instance tăng tốc để sử dụng trong tương lai bằng cách thanh toán trước. Bạn có thể dự trữ các khối từ 1 đến 64 instance trong thời gian tối đa 6 tháng, với khả năng gia hạn các dự trữ đang hoạt động.
Điều này đặc biệt hữu ích cho các tổ chức chạy các khối lượng công việc huấn luyện hoặc suy luận quy mô lớn trong AI hoặc machine learning (ML), hoặc các mã tăng tốc GPU như trong molecular dynamics hoặc fluid dynamics, trong môi trường HPC.

**Lợi ích chính**

**Reserved Access** cho phép khách hàng dự trữ các instance GPU trước tới 8 tuần, đảm bảo tài nguyên sẵn có cho các khối lượng công việc quan trọng đồng thời cung cấp mức giá ưu đãi so với giá on-demand. Tính năng này lấp đầy khoảng trống giữa các instance on-demand linh hoạt và các cam kết On-Demand Capacity Reservation (ODCR) dài hạn, làm cho nó trở nên lý tưởng cho khách hàng chạy các khối lượng công việc ML hoặc HPC cần thực thi nhất quán trên GPU mạnh mẽ mà không cần dự trữ lâu dài. Bằng cách cho phép đặt trước tài nguyên GPU, khách hàng có thể duy trì tính liên tục của workflow và tối ưu hóa kế hoạch sử dụng tài nguyên cho các tình huống như chu kỳ huấn luyện định kỳ, cập nhật mô hình theo lịch trình, và các công việc huấn luyện ML nhạy cảm về thời gian cũng như các dự án nghiên cứu.

**Flexible Scheduling** cho phép bạn dự trữ tài nguyên GPU ngay lập tức cho các tác vụ khẩn cấp như tối ưu hóa suy luận thời gian thực, hoặc lên lịch trước cho các công việc GPU quy mô lớn đã được kế hoạch trên PCS. Với Slurm trên PCS, bạn có thể xếp hàng các job và chúng sẽ bắt đầu ngay khi các instance của Capacity Block sẵn sàng. Sự linh hoạt này đảm bảo rằng bạn có thể truy cập nhanh các instance mạnh mẽ khi cần, ví dụ như tinh chỉnh mô hình nhanh chóng và xác thực, hoặc lên lịch chiến lược cho các khối lượng công việc nặng sắp tới như huấn luyện phân tán trên nhiều GPU. Dù bạn đang phản ứng với nhu cầu mô hình hóa ngay lập tức hay lập kế hoạch cho các pipeline huấn luyện lớn, khả năng chuyển đổi giữa đặt trước ngay lập tức và đặt trước cho tương lai giúp bạn luôn có quyền truy cập vào tài nguyên tính toán cần thiết, đồng thời giữ lợi ích về chi phí và khả năng dự trữ công suất.

Capacity Blocks cũng cung cấp **khả năng chia sẻ tài nguyên mạnh mẽ** — cho phép bạn phân phối các instance GPU đã dự trữ trên nhiều cụm PCS. Bạn cũng có thể **tập hợp nhiều Capacity Blocks thành một hàng lớn duy nhất** trong PCS để tận dụng tối đa hiệu suất trên các loại instance khác nhau. Điều này giúp **tối đa hóa giá trị của các GPU đã dự trữ** cho các loại khối lượng công việc hoặc thí nghiệm đa dạng. Khả năng này còn mở rộng đến việc **chia sẻ công suất dự trữ giữa nhiều dự án**, lý tưởng cho các tổ chức muốn **phân bổ hiệu quả tài nguyên GPU đã được lên lịch trước** giữa các sáng kiến hoặc đội nhóm khác nhau.

**Seamless Integration** mang đến trải nghiệm liền mạch bằng cách **tích hợp Capacity Blocks trực tiếp vào PCS Compute Node Groups (CNGs)** thông qua một tùy chọn mua đơn giản.iản. Chỉ cần cập nhật launch template, bạn có thể **tận dụng tất cả các khả năng lập lịch và quản lý hàng đợi quen thuộc của PCS** với công suất đã dự trữ.trữ. Các nhóm có thể ngay lập tức sử dụng quyền truy cập GPU đã dự trữ trong khi vẫn duy trì các workflow và quy trình ML hoặc HPC hiện có, khiến việc chuyển sang sử dụng Capacity Blocks trở nên **đơn giản như chọn một tùy chọn mua mới**.

**Bắt đầu với Capacity Blocks trong PCS**
Trước khi bắt đầu, hãy đảm bảo rằng bạn đã [tạo một cụm PCS](https://docs.aws.amazon.com/pcs/latest/userguide/getting-started.html) **(PCS cluster)**.

1.Tạo hoặc Chọn một Capacity Block
 Trước tiên, mua Capacity Block của bạn thông qua EC2 console, chỉ định:
* Loại instance
* Số lượng instance (1-64)
* Thời lượng (tối đa 6 tháng)
* Ngày bắt đầu (trước tối đa 8 tuần)

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.1-Blog1/capacity-blocks-requirements.png)

<small><small>Hình 1 – Hộp thoại yêu cầu EC2 Capacity Blocks trong AWS Management Console, hiển thị loại instance, dung lượng, thời lượng và ngày bắt đầu.</small></small>

2. **Tạo launch template của bạn**
   
    Chúng ta sẽ **tạo một launch template** thông qua **trang Amazon EC2** [launch templates](https://us-east-2.console.aws.amazon.com/ec2/home?region=us-east-2#LaunchTemplates:). 
    
    Cập nhật **loại instance** để khớp với **loại instance trong Capacity Block** của bạn (trong trường hợp này là **p5.4xlarge**).

    ![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.1-Blog1/capacity-blocks-requirements-1.png)

    <small><small>Hình 2 – Hộp thoại Create Launch Template trong AWS Management Console EC2, hiển thị loại instance khớp với loại instance đã chỉ định khi mua Capacity Block.</small></small>

Trong **Network settings**, chỉ định **Availability Zone** tương ứng với **Capacity Block** của bạn (trong trường hợp này là **us-west-2c**) và chọn **security group** mà bạn đã tạo trong quá trình thiết lập cụm PCS. Bạn có thể để nguyên các cấu hình còn lại hoặc tùy chỉnh theo sở thích – chúng **không bắt buộc** để kích hoạt Capacity Blocks.
![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.1-Blog1/capacity-blocks-requirements-2.png)

<small><small>Hình 3 – Hộp thoại Create Launch Template trong AWS Management Console, hiển thị Availability Zone khớp với AZ của Capacity Block và security group khớp với security group của cụm PCS.
</small></small>

Trong **Advanced Details**, thay đổi **purchasing option** thành **Capacity Blocks** và dưới mục **Capacity Reservation**, chọn **Specify Capacity Reservation**. Chọn **Reservation ID** của bạn. **Bỏ qua các chi tiết còn lại** trong Launch Template. Đây là **bước cuối cùng** để kích hoạt Capacity Blocks.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.1-Blog1/capacity-blocks-requirements-3.png)

3. **Tạo Compute Node Group**
Trong **[PCS Console](https://us-east-2.console.aws.amazon.com/pcs/home?region=us-east-2#/clusters)**, tạo một **Compute Node Group** bằng cách chọn **launch template** và phiên bản thích hợp. Cập nhật **instance profile** nếu cần bằng cách tạo một profile cơ bản với **quyền cho các instance EC2 tham gia cụm AWS PCS**. Tiếp theo, chọn **subnet** tương ứng với **Capacity Block** của bạn và chọn **Instance Type** khớp với **Capacity Block**, ví dụ **p5.4xlarge**.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.1-Blog1/capacity-blocks-requirements-4.png)

<small><small>Hình 5 – Hộp thoại Create Compute Node Group trong AWS Management Console PCS, hiển thị subnet khớp với subnet của Capacity Block, instance type khớp với Capacity Block, và purchase option là “Capacity Block”.
</small></small>

Sau vài phút, bạn sẽ thấy **instance** của mình chạy trong **EC2 instances dashboard**. Khi một instance **vượt qua kiểm tra trạng thái (status check)**, nó đã **sẵn sàng để sử dụng**.

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.1-Blog1/capacity-blocks-requirements-5.png)

<small><small>Hình 6 – EC2 Instances dashboard trong AWS Management Console hiển thị instance từ Capacity Block đã được PCS khởi chạy và đã vượt qua kiểm tra trạng thái (status check).</small></small>

**Gợi ý best practices**

Chúng tôi khuyến nghị [theo dõi mức sử dụng công suất](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-blocks-view.html) khi **chia sẻ Capacity Blocks giữa nhiều dịch vụ** bằng **console** hoặc **CLI**.

  * Để **thay đổi loại instance** hoặc sử dụng một **Capacity Block mới**, hãy **tạo một compute node group mới** thay vì cập nhật nhóm hiện có. Điều này đảm bảo **chuyển đổi liền mạch** và tránh **gián đoạn tiềm ẩn cho khối lượng công việc**.

  * **Lập kế hoạch xử lý công việc khi Capacity Blocks hết hạn:** bạn có thể [gia hạn CB](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-blocks-extend.html) hoặc **cảnh báo các nhóm thông qua thông báo tự động của EventBridge.** Khi gia hạn CB, **không có gián đoạn** cho các job đã gửi tới **compute node group** của PCS.
  * 
  * **Để xác định Capacity Block sắp hết hạn**, lưu ý: **EC2** sẽ phát ra sự kiện **Capacity Block Reservation Delivered** qua EventBridge khi một **CB reservation bắt đầu**, và sự kiện **Capacity Block Reservation Expiration Warning 40 phút trước khi CB hết hạn,** với **instance bị thu hồi 30 phút trước khi CB hết hạn**. Bạn có thể **đăng ký các sự kiện này và thực hiện hành động thích hợp**. Chi tiết hơn có trong phần [giám sát (monitoring)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-blocks-monitor.html) của tài liệu chính thức về **Capacity Blocks**.

  * Đảm bảo **AZ (Availability Zone)** khớp giữa **Capacity Block** và **compute node group** (xem hướng dẫn [Capacity Blocks launch](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-blocks-launch.html)).
  
  * **Capacity Blocks** phải ở trạng thái **scheduled** hoặc [active](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-blocks-view.html) trước khi **kết nối với PCS**. Nếu ở trạng thái **scheduled**, **PCS scheduler** sẽ **giữ các job trong hàng đợi** cho đến khi **CB trở thành active**.
  
  * Khi tạo một **compute node group**, lưu ý rằng **instance sẽ không được khởi chạy cho đến thời điểm bắt đầu của Capacity Reservation**, ngay cả khi **reservation đã active** trước đó.
  * 
**Khả năng sẵn có và giá cả**

PCS hiện **hỗ trợ Amazon EC2 Capacity Blocks** ở tất cả các **AWS Regions** [nơi cả hai dịch vụ có sẵn](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/).

**Giá tiêu chuẩn** cho [PCS](https://aws.amazon.com/pcs/pricing/) và [Capacity Block](https://aws.amazon.com/ec2/capacityblocks/pricing/) được áp dụng. Bạn sẽ **bị tính phí cho công suất đã dự trữ** theo **mô hình giá EC2 Capacity Blocks**, bất kể mức sử dụng.

**Chúc bạn xây dựng thành công!**

TAGS: [AI](https://aws.amazon.com/blogs/hpc/tag/ai/), [Compute](https://aws.amazon.com/blogs/hpc/tag/compute/), [GPU](https://aws.amazon.com/blogs/hpc/tag/gpu/), [HPC](https://aws.amazon.com/blogs/hpc/tag/hpc/), [Machine Learning](https://aws.amazon.com/blogs/hpc/tag/machine-learning/), [Research Computing](https://aws.amazon.com/blogs/hpc/tag/research-computing/), [Scientific Computing](https://aws.amazon.com/blogs/hpc/tag/scientific-computing/)

![Capacity Blocks Requirements](/images/3-BlogsTranslated/3.1-Blog1/capacity-blocks-requirements-6.png)


---



