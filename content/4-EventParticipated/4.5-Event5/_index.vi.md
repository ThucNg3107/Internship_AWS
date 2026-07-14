---
title: "Sự kiện 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.5. </b> "
---

# BÀI THU HOẠCH “FIRST CLOUD AI JOURNEY - AWS SLA, SECURITY & EXAM ROADMAPS”

### Mục Đích Của Sự Kiện

- Định hướng chiến lược và xây dựng lộ trình chinh phục chứng chỉ AWS Certified Cloud Practitioner (CLF-C02) cho người mới bắt đầu.
- Phân tích tầm quan trọng của việc giám sát dựa trên trải nghiệm người dùng cuối thay vì chỉ phụ thuộc vào hạ tầng kỹ thuật.
- Giới thiệu các giải pháp tự động hóa an toàn thông tin bằng AI nhằm tối ưu hóa chi phí và hiệu suất so với phương pháp thủ công.
- Trang bị tư duy quản trị rủi ro hệ thống và áp dụng các mô hình tiêu chuẩn của AWS vào thực tế.

### Danh Sách Diễn Giả

- **Nguyễn Huỳnh Sơn** - Member of AWS Student Builder Group HUFLIT, Ex Infrastructure Reliability Engineer tại SPS; chia sẻ về chủ đề SLA và hệ thống giám sát (Monitoring).
- **Ngô Lê Tấn Huy** - Diễn giả hướng dẫn lộ trình chiến lược và mẹo làm bài thi AWS Cloud Practitioner.
- **Thịnh Nguyễn** - DevOps/DevSecOps/Cloud Engineer tại Styl Solutions; chia sẻ về giải pháp bảo mật tự động với AWS Security Agent.

### Nội Dung Nổi Bật

1. Hệ thống Giám sát (Monitoring) và Cam kết Dịch vụ (SLA)

   - **Bản chất của SLA**: Là thỏa thuận chính thức về mức độ dịch vụ giữa nhà cung cấp và khách hàng. AWS chịu trách nhiệm bảo hành dịch vụ của họ, nhưng trải nghiệm thực tế của người dùng là trách nhiệm của người xây dựng hệ thống.
   - **Lỗ hổng giám sát hạ tầng**: Hạ tầng báo trạng thái "xanh" (CPU, RAM bình thường) không đồng nghĩa với việc người dùng có trải nghiệm tốt. Ví dụ: Endpoint kiểm tra sức khỏe hệ thống (`/health`) hoạt động bình thường, nhưng luồng đăng nhập thật (`/login`) có thể thất bại do lỗi kết nối cơ sở dữ liệu.
   - **Mô hình Kim tự tháp Giám sát**:
     - **Tầng đáy (Hạ tầng/Dịch vụ Cloud)**: CPU, Memory, EC2, RDS phục vụ chẩn đoán nguyên nhân gốc rễ (Root cause).
     - **Tầng đỉnh (Trải nghiệm người dùng/Kinh doanh)**: Tỷ lệ đăng nhập thành công, doanh thu, đơn hàng giúp xác định mức độ ảnh hưởng thực tế.
   - **Chu trình quản trị rủi ro**: Nhận diện rủi ro $\rightarrow$ Giám sát tín hiệu (metrics, logs, alarms) $\rightarrow$ Phản hồi tự động qua SNS/Slack $\rightarrow$ Cải tiến hệ thống.

2. Chiến lược chinh phục chứng chỉ AWS Cloud Practitioner (CLF-C02)

   - **Cấu trúc bài thi**: Gồm 65 câu hỏi trắc nghiệm (chọn một hoặc nhiều đáp án), thời gian làm bài 90 phút (người bản xứ không dùng tiếng Anh được thêm 30 phút), điểm đạt từ 700/1000. Chứng chỉ có giá trị trong 3 năm.
   - **Trọng tâm 4 phần vùng kiến thức**:
     - **Cloud Concepts (24%)**: Tập trung tư duy chuyển đổi số, 6 lợi ích của Cloud, khung chuẩn Well-Architected và CAF.
     - **Security and Compliance (30%)**: Mô hình trách nhiệm chia sẻ (Security OF vs IN the cloud), IAM, nhóm bảo mật (Security Groups/NACLs), AWS Artifact.
     - **Cloud Technology and Services (34%)**: Hiểu mục đích sử dụng thông qua tên dịch vụ (Compute, Storage, Database, Networking).
     - **Billing, Pricing, and Support (12%)**: Các mô hình giá EC2, công cụ quản lý chi phí (Cost Explorer, Budgets) và các gói hỗ trợ.
   - **Phương pháp ôn luyện hiệu quả**:
     - **Tư duy lập bản đồ từ khóa**: Gán liền mỗi dịch vụ với 1-2 từ khóa cốt lõi (Ví dụ: "Decouple" chọn SQS).
     - **Phân tích lỗi sai**: Khi giải đề mô phỏng, cần làm rõ tại sao các phương án khác lại sai để tránh bẫy của đề thi.
     - **Thực hành Free Tier**: Trực tiếp thao tác trên các dịch vụ cơ bản để dễ dàng hình dung.

3. Tối ưu hóa bảo mật ứng dụng Web với AWS Security Agent

   - **Điểm nghẽn của Pentest truyền thống**: Kiểm thử thủ công thường tốn nhiều tuần, chi phí đắt đỏ ($5k - $20k), và kết quả không đồng đều tùy thuộc vào kỹ năng của chuyên gia.
   - **Giải pháp AI tự động (Frontier Agent)**: Được vận hành bởi Amazon Bedrock, có khả năng tự chủ lập kế hoạch và xác minh lỗ hổng bằng cách thử nghiệm khai thác thực tế thay vì chỉ đưa ra cảnh báo lý thuyết.
   - **Phạm vi bao phủ toàn diện**:
     - **Design Review**: Kiểm tra tài liệu Markdown hoặc code Terraform ngay từ giai đoạn thiết kế theo các tiêu chuẩn PCI DSS, NIST CSF.
     - **Code Review**: Tích hợp tự động vào Pull Requests trên GitHub/GitLab để quét mã độc, lộ bí mật và gợi ý bản vá sửa lỗi trực tiếp.
     - **Automated Pentesting**: Thực hiện tấn công chuỗi nhiều bước (IDOR $\rightarrow$ XSS) như một người dùng thực thụ.
   - **Hạn chế cốt lõi**: Bị chặn bởi các hệ thống xác thực phức tạp (MFA, Biometrics, mTLS) và gặp khó khăn khi phát hiện các gian lận về logic nghiệp vụ.

### Những Gì Học Được

#### Tư Duy Thiết Kế & Quản Lý

- Dịch vụ hạ tầng ổn định mới chỉ là điều kiện cần; điều kiện đủ để đánh giá một hệ thống tốt là sự hài lòng và trải nghiệm thông suốt của người dùng cuối.
- An toàn thông tin cần được tích hợp từ sớm (Shift-left security) ngay từ khâu thiết kế kiến trúc thông qua các công cụ duyệt tự động để giảm thiểu chi phí khắc phục sau này.

#### Kỹ Thuật & Công Cụ

- Biết cách thiết lập các chỉ số tùy chỉnh (Custom metrics) kết hợp với CloudWatch Alarm và SNS để nhận cảnh báo sớm trước khi khách hàng kịp phản ánh.
- Nắm vững các kỹ thuật làm bài thi trắc nghiệm AWS như phương pháp loại trừ phương án giả mạo và chú ý các từ khóa quyết định (Not, Least cost, Most scalable).
- Hiểu rõ mô hình định giá dựa trên số giờ thực thi tác vụ (Task-Hour) của các đại lý AI bảo mật để cân đối bài toán chi phí so với thuê nhân sự.

### Ứng Dụng Vào Công Việc

- **Xây dựng lại hệ thống Dashboard giám sát** cho các dự án hiện tại: Bổ sung các chỉ số đo lường tầng ứng dụng và trải nghiệm doanh nghiệp (Tỷ lệ login, tỷ lệ checkout thành công) thay vì chỉ nhìn vào biểu đồ CPU/RAM.
- **Lên kế hoạch ôn tập chứng chỉ AWS Certified Cloud Practitioner** theo lộ trình 4 phân vùng, tận dụng nguồn tài liệu miễn phí AWS Skill Builder và thực hành trên tài khoản Free Tier.
- **Thử nghiệm tích hợp các công cụ quét mã nguồn tự động** vào quy trình CI/CD của nhóm để tự động kiểm tra bảo mật mỗi khi tạo Pull Request.

<div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin-top: 20px;">
  <img src="/images/4-EventParticipated/sk5_1.jpg" alt="sk5_1" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk5_2.jpg" alt="sk5_2" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk5_3.jpg" alt="sk5_3" style="width: 30%; min-width: 250px; height: auto;" />
</div>
