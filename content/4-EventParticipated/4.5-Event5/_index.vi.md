---
title: "Sự kiện 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.5. </b> "
---

# BÀI THU HOẠCH “FIRST CLOUD AI JOURNEY - AWS SLA, SECURITY & EXAM ROADMAPS”

### Mục Đích Của Sự Kiện

- Xây dựng phương pháp ôn luyện và định hướng lộ trình ngắn nhất để đạt chứng chỉ AWS Certified Cloud Practitioner (CLF-C02).
- Thấu hiểu triết lý giám sát ứng dụng lấy trải nghiệm người dùng cuối làm thước đo thay vì chỉ tập trung vào thông số phần cứng.
- Khám phá các công cụ tự động hóa quét bảo mật bằng AI giúp nâng cao chất lượng mã nguồn và tối ưu hóa ngân sách doanh nghiệp.
- Định hình tư duy quản trị rủi ro hạ tầng và áp dụng linh hoạt các bộ khung chuẩn thiết kế từ AWS vào dự án thực tế.

### Danh Sách Diễn Giả

- **Nguyễn Huỳnh Sơn** - Member of AWS Student Builder Group HUFLIT, Ex Infrastructure Reliability Engineer tại SPS; diễn giả chia sẻ về SLA và hệ thống giám sát (Monitoring).
- **Ngô Lê Tấn Huy** - Diễn giả hướng dẫn chiến lược ôn luyện và mẹo làm bài thi chứng chỉ AWS Cloud Practitioner.
- **Thịnh Nguyễn** - DevOps/DevSecOps/Cloud Engineer tại Styl Solutions; diễn giả giới thiệu giải pháp an toàn thông tin với AWS Security Agent.

### Nội Dung Nổi Bật

1. Hệ thống Giám sát (Monitoring) và Cam kết Dịch vụ (SLA)

   - **Bản chất của SLA**: Cam kết chất lượng dịch vụ giữa nhà cung cấp hạ tầng và khách hàng sử dụng. AWS bảo đảm độ sẵn sàng cho các dịch vụ Cloud của họ, nhưng trải nghiệm ứng dụng thực tế trên môi trường Production lại hoàn toàn thuộc về trách nhiệm của nhà phát triển.
   - **Lỗ hổng giám sát hạ tầng**: Hạ tầng báo trạng thái "xanh" (CPU, RAM ổn định) không đảm bảo ứng dụng đang vận hành hoàn hảo. Ví dụ: Route kiểm tra sức khỏe (`/health`) trả về kết quả tốt nhưng luồng đăng nhập thực tế (`/login`) lại tắc nghẽn do sự cố kết nối cơ sở dữ liệu.
   - **Mô hình Kim tự tháp Giám sát**:
     - **Tầng đáy (Hạ tầng/Dịch vụ Cloud)**: Đo lường CPU, RAM, EC2, RDS phục vụ công tác chẩn đoán nguyên nhân gốc rễ (Root cause).
     - **Tầng đỉnh (Trải nghiệm người dùng/Kinh doanh)**: Đo lường tỷ lệ đăng nhập thành công, lượng đơn hàng và doanh thu để đánh giá mức độ ảnh hưởng thực tế đối với hoạt động kinh doanh.
   - **Chu trình quản trị rủi ro**: Phát hiện nguy cơ $\rightarrow$ Thu thập dữ liệu giám sát (metrics, logs, alarms) $\rightarrow$ Phát cảnh báo tự động qua SNS/Slack $\rightarrow$ Cải tiến hạ tầng.

2. Chiến lược chinh phục chứng chỉ AWS Cloud Practitioner (CLF-C02)

   - **Cấu trúc bài thi**: Bài thi gồm 65 câu hỏi lựa chọn, thời gian 90 phút (bổ sung 30 phút đối với ứng viên không sử dụng tiếng Anh làm ngôn ngữ chính), điểm chuẩn đạt từ 700/1000 với thời hạn hiệu lực 3 năm.
   - **Trọng tâm 4 phân vùng kiến thức**:
     - **Cloud Concepts (24%)**: Tập trung tư duy chuyển đổi số, 6 lợi ích cốt lõi của Đám mây, khung Well-Architected Framework và CAF.
     - **Security and Compliance (30%)**: Thấu hiểu Mô hình trách nhiệm chia sẻ (Security OF vs IN the cloud), IAM, nhóm bảo mật (Security Groups/NACLs) và AWS Artifact.
     - **Cloud Technology and Services (34%)**: Định hình mục đích sử dụng dịch vụ thông qua nhóm chức năng (Compute, Storage, Database, Networking).
     - **Billing, Pricing, and Support (12%)**: Các hình thức chi trả EC2, công cụ quản lý ngân sách (Cost Explorer, Budgets) và các cấp độ gói hỗ trợ.
   - **Phương pháp ôn luyện hiệu quả**:
     - **Tư duy lập bản đồ từ khóa**: Liên kết mỗi dịch vụ với 1-2 từ khóa quyết định (Ví dụ: "Decouple" liên tưởng ngay đến SQS).
     - **Phân tích lỗi sai**: Khi luyện đề thi thử, cần phân tích kỹ nguyên nhân các phương án sai để tránh rơi vào bẫy của bài thi thật.
     - **Thực hành Free Tier**: Tự tay thao tác trên môi trường Cloud thực tế để ghi nhớ sâu sắc các dịch vụ cơ bản.

3. Tối ưu hóa bảo mật ứng dụng Web với AWS Security Agent

   - **Điểm nghẽn của Pentest truyền thống**: Hoạt động kiểm thử xâm nhập thủ công thường kéo dài nhiều tuần, chi phí đắt đỏ ($5k - $20k) và chất lượng báo cáo phụ thuộc lớn vào trình độ cá nhân.
   - **Giải pháp AI tự động (Frontier Agent)**: Được vận hành bởi Amazon Bedrock, có khả năng tự chủ xây dựng kịch bản và thực thi các thử nghiệm tấn công thực tế thay vì dừng lại ở việc phát hiện lý thuyết.
   - **Phạm vi bao phủ toàn diện**:
     - **Design Review**: Rà soát tài liệu kiến trúc Markdown hoặc mã nguồn Terraform ngay từ khâu thiết kế theo các bộ tiêu chuẩn PCI DSS, NIST CSF.
     - **Code Review**: Tự động tích hợp vào quy trình Pull Request (GitHub/GitLab) để quét lỗ hổng bảo mật, lộ secret và gợi ý đoạn mã sửa lỗi trực tiếp.
     - **Automated Pentesting**: Tiến hành các chuỗi tấn công phức tạp nhiều bước (IDOR $\rightarrow$ XSS) mô phỏng chính xác hành vi của kẻ tấn công.
   - **Hạn chế cốt lõi**: Chưa tối ưu khi gặp các cơ chế xác thực nâng cao (MFA, Biometrics, mTLS) và các lỗi gian lận logic nghiệp vụ phức tạp.

### Những Gì Học Được

#### Tư Duy Thiết Kế & Quản Lý

- Hạ tầng vận hành ổn định mới chỉ là điều kiện cần; trải nghiệm trơn tru và sự hài lòng của người dùng mới là thước đo thành công cuối cùng của hệ thống.
- An toàn thông tin phải được dịch chuyển sang trái (Shift-left security) - rà soát bảo mật ngay từ khâu thiết kế kiến trúc để tối ưu hóa chi phí khắc phục sự cố.

#### Kỹ Thuật & Công Cụ

- Thiết lập các chỉ số giám sát tùy biến (Custom metrics) kết hợp CloudWatch Alarm và dịch vụ SNS để chủ động phát hiện sự cố trước khi người dùng phản ánh.
- Nắm vững mẹo xử lý câu hỏi trắc nghiệm AWS, bao gồm phương pháp loại trừ đáp án nhiễu và nhận diện từ khóa then chốt (Not, Least cost, Most scalable).
- Đánh giá bài toán chi phí theo mô hình giờ thực thi (Task-Hour) của các đại lý AI bảo mật để lựa chọn phương án tối ưu so với chi phí nhân sự.

### Ứng Dụng Vào Công Việc

- **Tái thiết kế hệ thống Dashboard giám sát** cho các sản phẩm hiện tại: Bổ sung chỉ số đo lường trải nghiệm thực tế (Tỷ lệ đăng nhập, tỷ lệ hoàn tất đơn hàng) song song với các thông số hạ tầng (CPU/RAM).
- **Lên kế hoạch chinh phục chứng chỉ AWS Certified Cloud Practitioner** theo lộ trình 4 phân vùng, kết hợp tài nguyên học tập trên AWS Skill Builder và thực hành thực tế.
- **Tích hợp các công cụ tự động quét mã nguồn** vào quy trình CI/CD của dự án để rà soát an toàn thông tin tự động trong mỗi đợt Pull Request.

<div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin-top: 20px;">
  <img src="/images/4-EventParticipated/sk5_1.jpg" alt="sk5_1" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk5_2.jpg" alt="sk5_2" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk5_3.jpg" alt="sk5_3" style="width: 30%; min-width: 250px; height: auto;" />
</div>
