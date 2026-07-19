---
title: "Sự kiện 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---



# Bài thu hoạch “First Cloud Journey Meetup - June 2026”

### Mục Đích Của Sự Kiện

- Chuẩn hóa nền tảng kỹ thuật về công nghệ Containerization và ứng dụng Docker cho lập trình viên mới.
- Khám phá các giải pháp AI nâng cao như mô hình GraphRAG kết hợp Amazon Bedrock và cơ sở dữ liệu đồ thị Amazon Neptune.
- Phương pháp xây dựng hệ thống phát hiện xâm nhập mạng (NIDS) ứng dụng thuật toán Machine Learning.
- Chia sẻ câu chuyện phát triển sự nghiệp thực tế từ vai trò IT Helpdesk đến vị trí Senior System Administrator / Cloud Engineer.
- Phân tích kiến trúc mạng thời gian thực cho game Multiplayer sử dụng AWS WebSockets và game engine Godot.
- Đề cao bộ quy tắc vàng và công cụ quản trị để tối ưu hóa hiệu quả làm việc nhóm.

### Danh Sách Diễn Giả

- **Bao Huynh** - Junior Cloud Native Developer tại Endava Vietnam & Founder ITea Lab.
- **Viet Phat** - Chuyên ngành AI tại Swinburne University of Technology.
- **Lê Hoàng Gia Đại** - Sinh viên năm cuối HUTECH, Team AWS G3.
- **Tran Trung Vinh** - System Administrator tại Central Retail Group.
- **Nguyen Quoc Bao** - Diễn giả về Multiplayer Cloud Networking.
- **Truong Huy Phuoc** - Diễn giả về The Art of Effective Teamwork.

### Nội Dung Nổi Bật

#### Docker - Công nghệ Container hóa

- Khái niệm: Đóng gói toàn bộ ứng dụng cùng mã nguồn và môi trường phụ thuộc vào một đơn vị đóng gói duy nhất, bảo đảm khả năng thực thi đồng nhất trên mọi nền tảng.
- Lợi ích: Tối ưu tính linh hoạt, đóng đóng gói đồng bộ, nâng cao hiệu suất sử dụng tài nguyên và tăng tốc độ triển khai ứng dụng.
- Thành phần chính: Docker Images (bản mẫu đóng gói chỉ đọc), Dockerfile (tệp cấu hình kịch bản build) và Docker Containers (thực thể môi trường đang vận hành).

#### GraphRAG với Amazon Bedrock & Neptune

- Vấn đề: Kỹ thuật RAG truyền thống thường gặp giới hạn khi truy vấn các bài toán phức tạp đòi hỏi khả năng suy luận liên kết (multi-hop reasoning).
- Giải pháp: Tận dụng cấu trúc Đồ thị (Graph Database) để biểu diễn các mối quan hệ ngữ nghĩa giữa các thực thể, giúp mô hình ngôn ngữ lớn (LLM) nắm bắt ngữ cảnh sâu sắc hơn.
- Công cụ: Amazon Bedrock (trích xuất thực thể & tạo vector embeddings) kết hợp Amazon Neptune (lưu trữ và truy vấn tri thức đồ thị).

#### Lộ trình nghề nghiệp IT Infrastructure

- Kỹ năng cốt lõi: Khởi đầu từ năng lực phân tích nguyên nhân sự cố (troubleshooting), kỹ năng giao tiếp và tinh thần chủ động học hỏi ở vị trí Helpdesk.
- Bước chuyển mình: Làm chủ hệ điều hành Linux, kiến thức mạng (Networking) và tự xây dựng các phòng lab thực hành để hiểu sâu bản chất vận hành hệ thống.
- Tư duy Cloud/DevOps: Dịch chuyển từ quản trị hạ tầng vật lý sang mô hình hạ tầng dưới dạng mã (IaC - Terraform) kết hợp văn hóa tự động hóa (CI/CD, Container).

#### Kết nối Game với AWS WebSockets

- Kiến trúc: Khai thác Amazon API Gateway WebSocket nhằm duy trì kênh giao tiếp hai chiều liên tục (full-duplex) với độ trễ thấp.
- Quản lý trạng thái: Phối hợp AWS Lambda (xử lý logic sự kiện) và DynamoDB (lưu trữ session ID cùng trạng thái phòng game).
- Tích hợp Godot: Sử dụng thư viện WebSocketPeer để lắng nghe và xử lý các sự kiện mạng trực tiếp trong vòng lặp xử lý của game (game loop).

### Những Gì Học Được

#### Tư Duy Thiết Kế

- **Cloud-Native Mindset**: Thấu hiểu bản chất của khả năng mở rộng linh hoạt (elastic scaling) và mô hình chi phí tối ưu theo giá trị thực dùng (pay-for-value).
- **Security-First**: Bảo mật không dừng ở các quy tắc cố định mà cần kết hợp linh hoạt thuật toán AI/ML để ứng phó với các hình thức tấn công mới.
- **Teamwork Core**: Nhận thức rõ ràng rằng mục tiêu chung minh bạch và tinh thần làm chủ cá nhân là yếu tố quyết định năng suất tập thể.

#### Kiến Trúc Kỹ Thuật

- **Containerization vs. Virtualization**: Phân biệt ưu thế của Container so với máy ảo VM truyền thống nhờ cơ chế chia sẻ chung nhân hệ điều hành (OS kernel).
- **Real-time Communication**: Xác định đúng kịch bản áp dụng WebSocket (game turn-based, tính năng chat) so với dịch vụ AWS GameLift đối với các game yêu cầu đồng bộ tần suất cao.
- **Data Engineering cho AI**: Tầm quan trọng của công đoạn làm sạch dữ liệu và cân bằng lớp (class imbalance) trong bài toán huấn luyện mô hình Machine Learning.

### Chiến Lược Phát Triển

- **Hands-on Experience**: Xây dựng sản phẩm thực tế qua các dự án cá nhân có giá trị vượt trội hơn việc tích lũy chứng chỉ đơn thuần.
- **Automation**: Tự động hóa các tác vụ lặp lại để giải phóng nguồn lực cho các hoạt động thiết kế và tối ưu hệ thống.

### Ứng dụng vào công việc

- Triển khai Docker: Đóng gói các ứng dụng hiện tại để chuẩn hóa quy trình CI/CD và tiết kiệm chi phí vận hành hạ tầng.
- Nâng cấp bảo mật: Nghiên cứu phương án tích hợp mô hình NIDS dựa trên ML vào kiến trúc AWS sẵn có để nâng cao năng lực phòng thủ.
- Cải thiện làm việc nhóm: Ứng dụng các công cụ quản trị (Trello, Slack, Discord) để tăng cường tính minh bạch và hiệu quả phối hợp công việc.
- Phát triển ứng dụng WebSocket: Thử nghiệm xây dựng các tính năng tương tác thời gian thực dựa trên AWS Lambda và DynamoDB.

### Trải nghiệm trong event

Tham gia sự kiện Meetup ngày Jun 06, 2026 là một hành trình học tập toàn diện từ hạ tầng, an toàn thông tin đến lập trình ứng dụng thực tế. Một số ấn tượng nổi bật:

#### Học hỏi từ thực tế
- Những trải nghiệm xương máu về các sự cố khi quản trị hệ thống và bài học “không bao giờ kiểm thử trực tiếp trên môi trường production” đem lại giá trị thực tiễn lớn.
- Phần trình diễn demo kết nối game Godot và cập nhật dữ liệu DynamoDB theo thời gian thực giúp cụ thể hóa các khái niệm lý thuyết.

#### Cập nhật công nghệ tiên phong
- Tiếp cận giải pháp GraphRAG - xu hướng công nghệ mới hỗ trợ giải quyết các bài toán tri thức phức tạp mà RAG truyền thống chưa tối ưu.
- Nắm bắt phương pháp kết hợp hạ tầng Cloud-native với Machine Learning để bảo vệ hệ thống trước các nguy cơ an ninh mạng hiện đại.

#### Kết nối cộng đồng
- Sự kiện tạo môi trường giao lưu cởi mở giữa sinh viên, nhân sự trẻ và các chuyên gia để thảo luận về định hướng phát triển nghề nghiệp.
- Nhận thức rõ vai trò của các công cụ chuyển đổi số trong việc thúc đẩy sự phối hợp ăn ý giữa các thành viên trong đội ngũ.

#### Bài học rút ra
- Công nghệ là phương tiện, tư duy thiết kế đúng đắn cùng sự kiên trì thực hành mới là yếu tố quyết định thành công bền vững.
- Hiện đại hóa ứng dụng thông qua Docker và Serverless giúp doanh nghiệp tăng tốc độ ra mắt sản phẩm và giảm thiểu rủi ro vận hành.

<div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin-top: 20px;">
  <img src="/images/4-EventParticipated/sk3_1.jpg" alt="sk3_1" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk3_2.jpg" alt="sk3_2" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk3_3.jpg" alt="sk3_3" style="width: 30%; min-width: 250px; height: auto;" />
</div>
<div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin-top: 10px;">
  <img src="/images/4-EventParticipated/sk3_4.jpg" alt="sk3_4" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk3_5.jpg" alt="sk3_5" style="width: 30%; min-width: 250px; height: auto;" />
</div>
