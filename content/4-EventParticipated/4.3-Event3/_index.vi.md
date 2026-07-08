---
title: "Sự kiện 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---



# Bài thu hoạch “First Cloud Journey Meetup - June 2026”


### Mục Đích Của Sự Kiện

- Chia sẻ kiến thức về công nghệ Container và Docker cho người mới bắt đầu.
- Giới thiệu các giải pháp nâng cao như GraphRAG trên AWS Bedrock và Neptune.
- Hướng dẫn xây dựng hệ thống phát hiện xâm nhập mạng (NIDS) sử dụng Machine Learning.
- Chia sẻ kinh nghiệm thực tế về lộ trình phát triển sự nghiệp từ IT Helpdesk lên Senior Sysadmin/Cloud Engineer.
- Khám phá kiến trúc kết nối game Multiplayer sử dụng AWS WebSockets và Godot.
- Đề cao các quy tắc vàng và công cụ để làm việc nhóm hiệu quả.

### Danh Sách Diễn Giả

- **Bao Huynh** - Junior Cloud Native Developer tại Endava Vietnam & Founder ITea Lab.
- **Viet Phat** - Chuyên ngành AI tại Swinburne University of Technology.
- **Lê Hoàng Gia Đại** - Sinh viên năm cuối HUTECH, Team AWS G3.
- **Tran Trung Vinh** - System Administrator tại Central Retail Group.
- **Nguyen Quoc Bao** - Diễn giả về Multiplayer Cloud Networking.
- **Truong Huy Phuoc** - Diễn giả về The Art of Effective Teamwork.

### Nội Dung Nổi Bật

#### Docker - Công nghệ Container hóa

- Khái niệm: Đóng gói ứng dụng và các thành phần phụ thuộc vào một gói duy nhất để hoạt động ổn định ở mọi nơi.
- Lợi ích: Tính di động cao, nhất quán, hiệu quả tài nguyên và triển khai nhanh chóng.
- Thành phần chính: Docker Images (mẫu chỉ đọc), Dockerfile (tệp chỉ dẫn xây dựng) và Docker Containers (thực thể ứng dụng đang chạy).

#### GraphRAG với Amazon Bedrock & Neptune

- Vấn đề: RAG truyền thống có giới hạn trong việc trả lời các câu hỏi yêu cầu suy luận đa bước (multi-hop reasoning).
- Giải pháp: Sử dụng đồ thị (Graph) để lưu trữ các mối quan hệ rõ ràng giữa các thực thể, giúp LLM hiểu ngữ cảnh sâu hơn.
- Công cụ: Amazon Bedrock (xử lý thực thể/embedding) và Amazon Neptune (lưu trữ và truy vấn đồ thị).

#### Lộ trình nghề nghiệp IT Infrastructure

- Kỹ năng cốt lõi: Bắt đầu từ kỹ năng giải quyết vấn đề (troubleshooting), giao tiếp và tư duy học hỏi tại Helpdesk.
- Bước chuyển mình: Học Linux, mạng (Networking) và xây dựng các phòng lab thực hành để hiểu cách hệ thống được xây dựng.
- Tư duy Cloud/DevOps: Chuyển từ quản lý server vật lý sang hạ tầng dưới dạng mã (IaC - Terraform) và văn hóa tự động hóa (CI/CD, Docker).

#### Kết nối Game với AWS WebSockets

- Kiến trúc: Sử dụng API Gateway WebSocket để duy trì kết nối hai chiều toàn song công (full-duplex).
- Quản lý trạng thái: Kết hợp Lambda (xử lý logic) và DynamoDB (lưu trữ ID kết nối và trạng thái trận đấu).
- Tích hợp Godot: Sử dụng lớp WebSocketPeer để xử lý các sự kiện mạng trong vòng lặp game.



### Những Gì Học Được

#### Tư Duy Thiết Kế 

- **Cloud-Native Mindset**: Hiểu về khả năng mở rộng đàn hồi (elastic scaling) và mô hình trả tiền theo mức sử dụng (pay-for-value).
- **Security-First**: Bảo mật không chỉ là dùng quy tắc cứng nhắc mà cần sự linh hoạt của AI/ML để thích ứng với các mối đe dọa mới.
- **Teamwork Core**: Hiểu rằng mục tiêu chung rõ ràng và sự chịu trách nhiệm cá nhân là chìa khóa của hiệu quả công việc.

#### Kiến Trúc Kỹ Thuật

- **Containerization vs. Virtualization**: Hiểu rõ tại sao Container lại nhẹ hơn và tối ưu hơn VM truyền thống nhờ dùng chung OS.
- **Real-time Communication**: Phân biệt khi nào nên dùng WebSocket (cho game turn-based, chat) và khi nào dùng GameLift cho các game yêu cầu tần suất cập nhật cao.
- **Data Engineering cho AI**: Tầm quan trọng của việc làm sạch dữ liệu và xử lý mất cân bằng lớp (class imbalance) trong huấn luyện mô hình ML.

### Chiến Lược Phát Triển

- **Hands-on Experience**: Thực hành qua các project thực tế và xây dựng portfolio quan trọng hơn chỉ có chứng chỉ.
- **Automation**: Tự động hóa các tác vụ lặp lại để dành thời gian cho việc thiết kế và cải tiến hệ thống.

### Ứng dụng vào công việc
- Triển khai Docker: Đóng gói các ứng dụng hiện tại để tối ưu hóa quá trình CI/CD và giảm chi phí hạ tầng.
- Nâng cấp bảo mật: Nghiên cứu tích hợp ML NIDS vào hệ thống AWS hiện có để tăng cường khả năng phát hiện tấn công.
- Cải thiện làm việc nhóm: Sử dụng các công cụ như Trello, Slack hoặc Discord để quản lý dự án và giao tiếp hiệu quả theo các quy tắc vàng.
- Phát triển ứng dụng WebSocket: Thử nghiệm xây dựng các tính năng tương tác thời gian thực sử dụng AWS Lambda và DynamoDB.
### Trải nghiệm trong event
Tham gia buổi Meetup ngày Jun 06, 2026 là một hành trình học tập đa chiều từ hạ tầng, bảo mật đến lập trình ứng dụng. Một số ấn tượng nổi bật:

#### Học hỏi từ thực tế
- Những câu chuyện về sai lầm trong quá trình làm Sysadmin và bài học “đừng bao giờ test trên môi trường production” mang lại giá trị thực tiễn cao.
- Các phiên demo trực tiếp kết nối game Godot và theo dõi dữ liệu DynamoDB thời gian thực giúp làm rõ các khái niệm trừu tượng.
#### Cập nhật công nghệ tiên phong
- Được tiếp cận với GraphRAG - một xu hướng mới giúp giải quyết các bài toán phức tạp mà RAG truyền thống chưa làm được.
- Hiểu được cách kết hợp sức mạnh của Cloud-native với Machine Learning để bảo vệ hệ thống trước các cuộc tấn công hiện đại.
#### Kết nối cộng đồng
- Sự kiện tạo không gian để các bạn sinh viên, người mới đi làm và các chuyên gia trao đổi về lộ trình phát triển “từ con số 0”.
- Hiểu thêm về tầm quan trọng của các công cụ số trong việc thúc đẩy sự phối hợp nhịp nhàng giữa các thành viên trong team.
#### Bài học rút ra
- Công nghệ chỉ là công cụ, tư duy thiết kế đúng đắn và sự kiên trì trong việc thực hành mới là yếu tố quyết định thành công.
- Việc hiện đại hóa ứng dụng thông qua Docker và Serverless giúp doanh nghiệp tăng tốc độ ra mắt sản phẩm và giảm thiểu rủi ro vận hành.
