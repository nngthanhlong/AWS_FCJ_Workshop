---
title: "Event 2"
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch "Generative AI with Amazon Bedrock"
**Thời gian:** 08:30 – 15/11/2025  

### Mục Đích Của Sự Kiện

- Trang bị nền tảng về Generative AI và chỉ ra điểm khác biệt so với cách tiếp cận Machine Learning truyền thống.
- Giới thiệu chi tiết dịch vụ Amazon Bedrock cùng các mô hình nền tảng (Foundation Models) được hỗ trợ.
- Trình bày quy trình kỹ thuật RAG (Retrieval Augmented Generation) để xây dựng ứng dụng AI thông minh, chính xác hơn và hạn chế hiện tượng ảo giác.
- Khái quát hệ sinh thái các dịch vụ AI chuyên dụng trên AWS và cách chúng kết hợp với Bedrock.

### Danh Sách Diễn Giả

- **Lam Tuan Kiet** - Sr DevOps Engineer, FPT Software.
- **Danh Hoang Hieu Nghi** - AI Engineer, Renova Cloud.
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud AI Journey.

### Nội Dung Nổi Bật

#### Sự chuyển dịch: Từ Traditional ML đến Foundation Models

- **Mô hình Machine Learning** truyền thống hoạt động theo dạng “một mô hình – một nhiệm vụ”, đòi hỏi lượng dữ liệu gán nhãn lớn và quy trình huấn luyện, triển khai khá phức tạp.
  
- **Foundation Models (FM)** lại được huấn luyện trên dữ liệu khổng lồ và không cần gán nhãn, vì vậy khả năng tổng quát tốt hơn và có thể áp dụng cho nhiều tác vụ khác nhau như tạo văn bản, tóm tắt, hỏi đáp hay chatbot.
  

#### Hệ sinh thái AI của AWS

- **Amazon Bedrock** là nơi tập trung nhiều mô hình tiên tiến từ AI21, Anthropic, Cohere, Meta, Stability AI,… cùng các mô hình của chính Amazon.
  
- Ngoài các FM, AWS còn cung cấp loạt Specialized AI Services – các dịch vụ dùng ngay không cần tự huấn luyện:

   - Amazon Rekognition: Nhận diện và phân tích hình ảnh/video.

   - Amazon Translate: Dịch ngôn ngữ thời gian thực.

   - Amazon Textract: Trích xuất dữ liệu có cấu trúc từ tài liệu scan.

   - Amazon Transcribe: Chuyển âm thanh thành văn bản.

   - Amazon Polly: Chuyển văn bản sang giọng nói.

   - Amazon Comprehend: Phân tích cảm xúc, chủ đề, từ khóa.

   - Amazon Kendra: Tìm kiếm thông tin bằng ngôn ngữ tự nhiên trong tài liệu doanh nghiệp.

   - Amazon Lookout: Phát hiện bất thường trong hệ thống công nghiệp.

   - Amazon Personalize: Xây dựng hệ thống gợi ý theo thời gian thực.

#### Kỹ thuật Prompting: Chain of Thought (CoT)

- So sánh giữa **Standard Prompting** (hỏi và nhận một kết quả cuối) với **Chain-of-Thought Prompting**.
- CoT khuyến khích mô hình **nghĩ thành tiếng**, phân rã bài toán thành nhiều bước suy luận. Cách này đặc biệt hiệu quả cho các bài toán logic phức tạp và thường cho kết quả chính xác, nhất quán hơn so với việc yêu cầu mô hình trả lời trực tiếp.

#### RAG (Retrieval Augmented Generation) 

- **Bài toán**: Các LLM thường bị giới hạn bởi dữ liệu huấn luyện (không cập nhật liên tục) và đôi khi sinh ảo giác (hallucination).
- **Hướng giải quyết**: Kết hợp LLM với một tầng tìm kiếm kiến thức bên ngoài (Knowledge Base). Mô hình sẽ truy xuất các đoạn thông tin liên quan rồi dùng chúng để xây dựng câu trả lời – thay vì chỉ dựa trên “trí nhớ” sẵn có.
- **Quy trình Data Ingestion (Nạp dữ liệu)**:
    1. Thu thập dữ liệu mới (New data) và chia nhỏ thành các đoạn (chunk).
    2. Đưa từng đoạn qua Embeddings model (ví dụ: Amazon Titan Text Embeddings V2.0) để chuyển thành vector.
    3. Lưu các vector này vào Vector Store (OpenSearch Serverless, Pinecone, Redis,...).
- **RetrieveAndGenerate API**: Đảm nhận toàn bộ pipeline: từ việc nhận input của người dùng → tạo embedding cho câu hỏi → truy vấn Vector Store → ghép ngữ cảnh vào prompt → gọi LLM sinh câu trả lời cuối cùng.

### Những Gì Học Được

#### Về AI và Cloud

- Hiểu rõ hơn khi nào nên dùng các dịch vụ AI chuyên biệt – thích hợp cho tác vụ nhanh và cụ thể – và khi nào nên sử dụng Generative AI hay Bedrock cho bài toán mang tính sáng tạo hoặc cần sự tùy biến cao. Hiểu cách tư duy về RAG, vốn tập trung nhiều vào tổ chức dữ liệu và cung cấp đúng ngữ cảnh hơn là chỉ gọi API của LLM.

#### Kiến Trúc Kỹ Thuật

- Hiểu rõ hơn cách một hệ thống AI hoạt động từ đầu đến cuối. Không chỉ đơn giản là “gọi mô hình để tạo câu trả lời”, mà hệ thống còn cần nhiều bước chuẩn bị dữ liệu và tổ chức thông tin trước khi AI có thể trả lời chính xác.
  
- Kiến trúc RAG được chia thành nhiều bước rõ ràng: thu thập dữ liệu → chia nhỏ → lưu vào kho tìm kiếm → lấy lại thông tin phù hợp → đưa vào cho mô hình trả lời. Cách tách thành từng bước như vậy giúp dễ quản lý và dễ mở rộng khi dữ liệu tăng.

### Ứng Dụng Vào Công Việc

- Chuẩn hóa dữ liệu phi cấu trúc: Sử dụng Textract và Bedrock Agents để tự động hoá việc trích rút thông tin từ biểu mẫu, hóa đơn và tài liệu scan, giảm thiểu thao tác thủ công.

- Hỗ trợ ra quyết định: Ứng dụng mô hình tạo sinh để tự động tóm tắt báo cáo, nêu bật các chỉ số quan trọng và đề xuất hướng xử lý dựa trên dữ liệu hiện có.

### Trải nghiệm trong event

Tham gia workshop là một trải nghiệm rất bổ ích, giúp tôi có cái nhìn toàn diện về AI và cách sử dụng AI sao cho tối ưu và hợp lý nhất. Phần trò chơi cũng rất bổ ích giúp tôi củng cố lại các kiến thức được nghe trong buổi workshop

#### Kết nối và trao đổi
- Workshop tạo cơ hội trao đổi trực tiếp với diễn giả giúp em hiểu thêm về cách sử dụng AI và một số công cụ AI mới và sau mỗi bài thuyết trình mình có truy cập linkin của các diễn giả để có thể học hỏi thêm sau này.

#### Bài học rút ra
- Tham gia workshop giúp tôi có cái nhìn rõ ràng hơn về cách ứng dụng AI sao cho hiệu quả. Tôi nhận ra rằng RAG là thành phần quan trọng để AI có thể trả lời chính xác dựa trên dữ liệu nội bộ của doanh nghiệp.
  
- Bên cạnh đó, tôi ấn tượng với hệ sinh thái đầy đủ của AWS — từ lưu trữ, mô hình cho đến công cụ điều phối — khiến việc xây dựng một ứng dụng AI thực tế trở nên dễ dàng và khả thi hơn nhiều


