---
title: "Sự kiện 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.4. </b> "
---



# Bài thu hoạch “FCAJ Community Day - Tháng 6 2026”



### Mục Đích Của Sự Kiện

- **Chia sẻ kinh nghiệm doanh nghiệp**: Sự kiện FCAJ Community Day là một sự kiện được tổ chức hàng tháng nhằm mục đích tạo không gian cho các diễn giả đến từ nhiều doanh nghiệp khác nhau chia sẻ những kinh nghiệm, trải nghiệm và góc nhìn thực tế nhất từ môi trường làm việc doanh nghiệp.


### Danh Sách Diễn Giả

- **Anh Steve Trần**: Hành trình sự nghiệp và Ứng dụng AI trong việc hỗ trợ vận hành hạ tầng Cloud.
- **Anh Hiếu Nghị , Anh Kiệt và Anh Trung**: Cùng trình bày chủ đề Xây dựng hệ thống Voice AI (AI Giọng nói) cho Tiếng Việt.
- **Chị Bảo và Anh Nguyên Nguyễn**: Tự động hóa điều tra lỗi và phục hồi hệ thống với DevOps Agent.
- **Anh Trường và Chị Minh Anh**: AI và nguồn nhân lực của doanh nghiệp - Ứng dụng Amazon Q trong tối ưu hóa quy trình Nhân sự (HR).
- **Anh Toàn Nguyễn**: Thiết lập kết nối bảo mật nội bộ (Private Security/VPC Connection) cho AI (Amazon Q) và hệ thống MCP Server.

### Nội Dung Nổi Bật
Sự kiện bao gồm nhiều phiên trình bày xoay quanh sự phát triển của công nghệ Đám mây (Cloud) và Trí tuệ nhân tạo (AI) trong nhiều lĩnh vực:

#### Hành trình sự nghiệp và AI trong vận hành Cloud

- **SRE & Tiến hóa Cloud**: Anh Steve Trần chia sẻ về chặng đường từ một người quản trị máy chủ thủ công đến vị trí Solution Architect tại AWS, và lý do sáng lập Cloud Thinker.
- **AI trong tuyển dụng**: Anh nhấn mạnh việc AI đang thay đổi cách các công ty tuyển dụng, ưu tiên những người giỏi hoặc sử dụng AI cực kỳ xuất sắc.
- **Kiến trúc Agent**: Anh cũng so sánh giữa cấu trúc AI Multi-agent và Single-agent trong việc quản lý cơ sở hạ tầng phức tạp.

#### Xây dựng Voice AI (AI Giọng nói) cho Tiếng Việt

- **Kiến trúc Voice AI**: Nhóm diễn giả trình bày về kiến trúc Voice AI, đặc biệt là thách thức khi Tiếng Việt thiếu dữ liệu cho mô hình Speech-to-Speech trực tiếp.
- **Giải pháp chuyển đổi**: Giải pháp là chuyển đổi giọng nói thành văn bản (STT), đưa qua LLM xử lý, rồi chuyển ngược thành giọng nói (TTS).
- **Tối ưu ngữ cảnh**: AI cũng được huấn luyện để hiểu ngữ cảnh, biết ngắt lời hợp lý, nhận diện giới tính (anh/chị) và xử lý giọng vùng miền trong các ứng dụng ngân hàng.

#### Tự động hóa với DevOps Agent

- **DevOps Agent**: Giới thiệu về AI DevOps Agent giúp tự động điều tra, phân loại lỗi hệ thống và đề xuất phương án khắc phục.
- **Đặc trưng nổi bật**: Điểm mạnh của Agent này là có thể học hỏi ngữ cảnh (Context learning), kết nối công cụ qua MCP, và tính phí dựa trên thời gian chạy thay vì hạ tầng.
- **Demo DoS Attack**: Demo thực tế cho thấy DevOps Agent phân tích log và tìm ra nguyên nhân ứng dụng chậm là do bị tấn công DoS chỉ trong thời gian ngắn.

#### Ứng dụng Amazon Q trong Nhân sự (HR)

- **Vấn đề**: Việc lọc CV thủ công dễ dẫn đến bỏ lỡ nhân tài và dựa nhiều vào cảm tính.
- **Hỗ trợ tuyển dụng**: Amazon Q được giới thiệu như một AI Assistant có thể tự động đọc CV, chấm điểm ứng viên dựa trên Job Description (JD), và đưa ra báo cáo trực quan mà không lo bị lộ dữ liệu nhờ tính năng bảo mật.

#### Bảo mật kết nối mạng cho AI bằng Private MCP

- **Vấn đề bảo mật**: Thay vì kết nối AI với các máy chủ MCP ngoài internet công cộng (dễ bị tấn công DoS hoặc lộ dữ liệu), hệ thống cần giải pháp truyền dữ liệu an toàn.
- **Đường truyền nội bộ**: Hệ thống sử dụng VPC Connection, ALB, và Route 53 Resolver để tạo ra một đường truyền hoàn toàn nội bộ và bảo mật trên AWS Cloud.


### Những Gì Học Được

#### Định hướng nghề nghiệp & Khởi nghiệp 

- **Cọ xát sớm**: Các bạn sinh viên hoặc người mới ra trường nên tìm cơ hội cọ xát sớm ở môi trường doanh nghiệp để tích lũy kinh nghiệm thực tế.
- **Vai trò của AI**: Mặc dù AI đang phát triển mạnh mẽ và các công ty có xu hướng ngừng tuyển dụng ồ ạt, AI sẽ không thay thế hoàn toàn con người ở những hệ thống hạ tầng trọng yếu (critical), mà nó đóng vai trò hỗ trợ và khuếch đại kỹ năng.
- **Tinh thần Startup**: Đừng mất quá nhiều thời gian suy nghĩ mà hãy bắt tay vào thực thi ngay lập tức. Cần tìm ra những khách hàng “champion” (những đơn vị lớn có sẵn bài toán thực tế) để áp dụng ý tưởng giải quyết đúng nỗi đau của doanh nghiệp.

#### Thiết kế & Vận hành hệ thống

- **Lựa chọn Agent**: Khi thiết kế AI Agent, Multi-agent giúp kiểm soát quyền truy cập và phân chia công việc tốt, nhưng đôi khi một Single-agent được thiết kế đủ tốt cũng có thể xử lý 95% các tác vụ phức tạp.
- **Con người làm chủ**: Các giải pháp AI không được tự động thực thi các hành động thay đổi trên môi trường thực tế (production) mà chỉ nên đưa ra đề xuất (recommendation), quyền quyết định và phê duyệt (approve) cuối cùng vẫn phải thuộc về con người. Mọi sự phụ thuộc hoàn toàn vào hệ thống tự động đều mang lại rủi ro lớn.
- **Observability**: Để AI có thể điều tra lỗi chính xác, hệ thống nền tảng phải có khả năng quan sát (observability) tốt với dữ liệu log đầy đủ.

