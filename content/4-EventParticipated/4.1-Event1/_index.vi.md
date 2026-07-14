---
title: "Sự kiện 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---


# Bài thu hoạch “FCAJ Community Day - Tháng 5 2026”


### Mục Đích Của Sự Kiện

- **Chia sẻ kiến thức và định hướng**: Sự kiện là nơi để các thành viên trong cộng đồng (AWS Study Group/FCAJ) chia sẻ cả về kỹ năng mềm (cách tạo động lực học tập) lẫn kỹ năng chuyên môn (công nghệ AWS, cách ứng dụng AI, định hướng nghề nghiệp).
- **Kết nối cộng đồng**: Tạo cơ hội giao lưu, kết nối giữa các thành viên có cùng mục tiêu phát triển bản thân.
- **Tạo môi trường rèn luyện**: Mục tiêu của ban tổ chức là tạo ra một sân chơi để các bạn trẻ mạnh dạn lên sân khấu làm diễn giả (speaker), chia sẻ kiến thức (thay vì chỉ “hóng drama” trên mạng), từ đó rèn luyện kỹ năng thuyết trình và sự tự tin trước đám đông.

### Danh Sách Diễn Giả

- **Huỳnh Hoàng Long** - Speaker về chủ đề “Addicted to learning like you’re addicted to social media”.
- **Nguyễn Tuấn Thịnh** - Speaker về “Automated prompt engineering: enhancing LLM Output Quality”.
- **Anh Khang** - Speaker về “AI-Ready Freshers - skill and Mindset in AI era”.
- **Anh Thảo (Chị Thảo)** - Speaker về phương pháp BMX (BMAD Method) trong phát triển phần mềm bằng AI.

### Nội Dung Nổi Bật


#### 1. Hack não bộ để “nghiện” học tập (Dopamine)

- **Vấn đề**: Mạng xã hội và game lôi cuốn vì có “phần thưởng nhanh” và tính “tò mò”, trong khi việc học cần tập trung lâu dài và trả kết quả chậm.
- **Giải pháp**: Dopamine tiết ra không phải khi nhận thưởng, mà là khi kỳ vọng phần thưởng sắp đến. Để học tốt, hãy tạo ra các phần thưởng nhỏ ngẫu nhiên (như bốc thăm trúng thưởng sau 10 phút học) để kích thích sự tò mò.
- **Mẹo thực hành**: Dùng nỗi sợ mất mát bằng cách “lập chuỗi” học tập hàng ngày (như check-in game), chia nhỏ khối lượng kiến thức khổng lồ thành các mốc nhỏ (như học từng dịch vụ AWS một) để não không bị ngợp, và tạo hệ thống phản hồi (cộng điểm kinh nghiệm, lên rank) để đánh lừa não bộ.
#### 2. Kỹ năng sử dụng AI (Prompt Engineering) và Kiến trúc AWS

- **Prompt Engineering**: Để AI trả lời tốt, prompt cần đầy đủ 7 thành phần chính: Vai trò (Role), Hướng dẫn (Instruction), Ngữ cảnh (Context), Định dạng đầu vào/đầu ra, Ví dụ (Example) và Ràng buộc (Constraint).
- **Tránh ảo giác (Hallucination)**: Tránh để AI bị “hallucination” bằng cách không hỏi những thứ không liên quan trong cùng một đoạn chat và chia nhỏ dữ liệu đầu vào. Các kỹ thuật nâng cao gồm: Chain of Thought (nghĩ từng bước) và Tree of Thought.
- **AWS Architecture Demo**: Diễn giả demo một kiến trúc ứng dụng AWS sử dụng CloudFront, S3 (lưu trữ tĩnh), Cognito (quản lý user), API Gateway, Lambda (backend serverless), Bedrock (cung cấp model AI) và DynamoDB.

#### 3. Tư duy nghề nghiệp trong thời đại AI

- **AI không thay thế bạn**: AI chỉ đóng vai trò khuếch đại (amplify). Nếu bạn giỏi, AI giúp bạn x2 năng suất; nhưng nếu bạn không có kiến thức nền tảng, AI sẽ chỉ làm bạn tệ hơn vì bạn không hiểu bản chất để xử lý khi bài toán thay đổi.
- **Tập trung vào nền tảng (Foundation)**: Công nghệ thay đổi nhanh, nhưng nền tảng thì không. Doanh nghiệp không cần bạn biết mọi framework, mà cần tư duy giải quyết vấn đề đúng đắn.
- **Luôn hỏi “Tại sao?” (Why)**: Khi làm bài tập hay dự án, đừng chỉ làm cho xong (What) mà phải biết tại sao mình chọn giải pháp đó (Why). Sự liêm chính (integrity) - tự xử lý các trường hợp ngoại lệ dù không ai yêu cầu - là chìa khóa để thăng tiến dài hạn.
- **5 lợi ích của công việc**: Khi đánh giá cơ hội, đừng chỉ nhìn vào Lương (Salary), mà hãy chú ý đến Kinh nghiệm (Experience), Mối quan hệ (Network), Kiến thức (Knowledge) và Hồ sơ cá nhân (Profile).

#### 4. Phương pháp BMX trong phát triển phần mềm bằng AI

- **Vấn đề**: Trực tiếp nhờ AI code ngay từ đầu sẽ tạo ra code “rác”, chắp vá và làm AI mất ngữ cảnh (context) khi dự án lớn lên.
- **Giải pháp (BMX Method)**: Chia nhỏ dự án theo chuẩn phát triển phần mềm (Software Development). Gắn vai trò cho AI làm PM, Architect, Scrum Master, và Dev.
- **Quy trình**: Yêu cầu AI lên ý tưởng (Brainstorm) -> Viết tài liệu yêu cầu (BRD) -> Lên kiến trúc hệ thống -> Cắt nhỏ thành từng tính năng (Epic/Story) -> Cuối cùng mới để AI Dev viết code dựa trên các tài liệu nhỏ đó. Triết lý là: “Viết document chuẩn chỉnh, AI sẽ code tốt”.



### Những Gì Học Được

#### Tư Duy Thiết Kế

- **Sự kiên trì quan trọng hơn sự chăm chỉ**: Người chiến thắng là người biết xây dựng môi trường và thói quen để tự động hóa việc học mỗi ngày, thay vì chỉ dựa vào nỗ lực ép buộc.
- **Biết cách đặt câu hỏi và dám sai**: Sai lầm là điều cần thiết đối với fresher. Nếu không có sai lầm, bạn sẽ không có kinh nghiệm. Hãy đặt nhiều giả định và tự tìm câu trả lời.
- **Không ỷ lại vào AI**: Cần biến AI thành người đồng cấp để tư duy cùng (brainstorm), nhưng tuyệt đối không “outsource” (thuê ngoài) trí thông minh của mình cho AI. Nếu bạn không tự hiểu bài toán, bạn sẽ không thể kiểm chứng được kết quả AI làm ra.
- **Làm việc nhóm luôn được đánh giá cao**: Thay vì đi một mình, hãy thực hiện dự án cùng người khác để chứng minh không chỉ kỹ năng kỹ thuật mà còn kỹ năng giao tiếp và quản lý nhóm.
- **Kiểm soát AI thay vì phó mặc**: Trong phát triển phần mềm, cần phải chia nhỏ ngữ cảnh (context window) và phân chia tác vụ rõ ràng để AI không bị “ảo giác” (hallucination) và người lập trình có thể kiểm soát hoàn toàn hệ thống.   

### Ứng Dụng Vào Công Việc

- **Áp dụng kỹ thuật Dopamine** để duy trì thói quen tự học hàng ngày (học AWS theo lộ trình từng phần nhỏ).
- **Viết prompt cho AI** chuẩn chỉnh theo 7 thành phần để tăng chất lượng code đầu ra.
- **Sử dụng quy trình BMX** để quản lý dự án khi phát triển phần mềm với AI (lên kế hoạch tài liệu rõ ràng trước khi yêu cầu sinh mã nguồn).
- **Củng cố kiến thức nền tảng** (networking, hệ điều hành, cloud core) thay vì chạy theo framework nhất thời.

### Trải nghiệm trong event

Tham gia sự kiện giúp tôi tích lũy được nhiều bài học bổ ích:

- **Truyền cảm hứng**: Câu chuyện từ các diễn giả sinh viên cho thấy sự tự tin và nỗ lực chia sẻ kiến thức cộng đồng là cực kỳ đáng quý.
- **Thực tế trực quan**: Demo trực tiếp luồng serverless với Cognito và Bedrock giúp tôi dễ dàng tiếp cận kiến trúc cloud-native.
- **Kết nối cộng đồng**: Nhận được định hướng nghề nghiệp quý báu từ các anh chị mentor có kinh nghiệm trong ngành.

<div style="display: flex; justify-content: center; margin-top: 20px;">
  <img src="/images/4-EventParticipated/sk1_1.jpg" alt="sk1_1" style="width: 30%; min-width: 200px; height: auto;" />
</div>

