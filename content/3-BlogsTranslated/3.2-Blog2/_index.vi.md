---
title: "Blog 2"
date: 2025-09-10
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

## Tapestry Giúp Kiến Thức Doanh Nghiệp Dễ Tiếp Cận Hơn Nhờ Generative AI trên AWS
Tác giả: Nishant Singh, Aditya Pendyala, Aravind Narasimhan, và Karthigeyan Ramakrishnan

Ngày đăng: 26 tháng 2, 2025

Danh mục: Amazon Aurora, Amazon Bedrock, Amazon Bedrock Knowledge Bases, Amazon CloudFront, Amazon S3, AWS IAM, AWS Lambda, Retail

# Giới thiệu

Generative AI (Trí tuệ nhân tạo tạo sinh) có tiềm năng thay đổi cách các công ty lớn hoạt động. Đối với các doanh nghiệp, thông tin thường được lưu trữ rời rạc (siloed) bởi nhiều đội nhóm khác nhau. Bằng cách kết hợp các mô hình ngôn ngữ lớn (LLMs) với các cơ sở kiến thức (knowledge bases) mạnh mẽ, các tổ chức này có thể tạo ra hệ thống thông minh không chỉ lưu trữ thông tin, mà còn hiểu được thông tin đó—giúp kiến thức doanh nghiệp trở nên dễ dàng truy cập và sử dụng hơn bao giờ hết.

Tapestry, tập đoàn công nghệ sở hữu các thương hiệu biểu tượng như Coach và Kate Spade, đang dẫn đầu trong việc ứng dụng generative AI để chuyển đổi mô hình quản lý kiến thức doanh nghiệp. Sử dụng AWS, công ty đã phát triển hệ thống quản lý thông tin thông minh, tập trung hóa truy cập dữ liệu giữa các đơn vị kinh doanh, giúp nhân viên đưa ra quyết định nhanh hơn và tốt hơn.

---

## Chuyển đổi quản lý kiến thức doanh nghiệp bằng AI trên AWS

Tapestry đã nuôi dưỡng văn hóa đổi mới công nghệ trong ngành bán lẻ cao cấp, thể hiện qua việc thử nghiệm và triển khai các giải pháp mới. Cam kết này rõ ràng trong phương pháp tiếp cận AI của họ: có tính toán, coi trọng bảo mật và nhằm tạo ra giá trị kinh doanh.

    “Chúng tôi muốn xây dựng một giải pháp AI tạo sinh nội bộ trước khi thử nghiệm trên môi trường công khai,” Aravind Narasimhan, Phó Chủ tịch công nghệ ứng dụng tại Tapestry chia sẻ. “Điều này cho chúng tôi cơ hội thử nghiệm công nghệ, học hỏi, và giáo dục các đối tác trong công ty.”

Như nhiều doanh nghiệp lớn khác, Tapestry đã gặp thách thức trong quản lý kiến thức. Thông tin bị phân mảnh trong các bộ phận như CNTT, nhân sự, pháp lý và những team khác, khiến nhân viên khó tìm câu trả lời nhanh chóng. Quy trình hoạt động tiêu chuẩn, chính sách, và kiến thức nội bộ cũng được lưu trữ trên các hệ thống và định dạng khác nhau. Tapestry nhận thấy có cơ hội sử dụng generative AI để giải quyết vấn đề này.

Amazon Bedrock — cung cấp nhiều mô hình nền tảng hiệu suất cao — cùng với Amazon Bedrock Knowledge Bases — cho phép các mô hình nền tảng và các agent có thông tin ngữ cảnh từ các nguồn dữ liệu riêng tư của công ty — đã tạo nền móng lý tưởng để xây dựng một giải pháp quy mô doanh nghiệp.

    “Amazon Bedrock Knowledge Bases là một giải pháp plug-and-play với ít yêu cầu code,” Karthigeyan Ramakrishnan, Giám đốc ứng dụng tại Tapestry nói. “Bạn có thể chọn mô hình embedding, các vector store, và LLM. Bạn có thể cấu hình việc chia nhỏ dữ liệu (chunking), tokens, và các phần khác một cách dễ dàng. Chính vì vậy chúng tôi rất thích nó.”


## Xây dựng nền tảng công ty để chia sẻ thông tin trôi chảy

Quá trình phát triển kéo dài 4 tháng, bắt đầu bằng một bản thử nghiệm (proof of concept) trong bộ phận CNTT. Hệ thống quản lý kiến thức này sử dụng nhiều dịch vụ của AWS. Ở trung tâm là Amazon Bedrock Knowledge Bases để quản lý và tổ chức kho tài liệu, còn Claude 3 Haiku được dùng như mô hình ngôn ngữ lớn để xử lý các truy vấn ngôn ngữ tự nhiên.

Để tạo embeddings văn bản (text embeddings) có khả năng phản ánh ý nghĩa ngữ nghĩa, Tapestry dùng các foundation model Titan trong Amazon Bedrock, cung cấp đa dạng lựa chọn về mô hình hình ảnh, đa phương thức (multimodal), và văn bản.

Cùng với đó, Amazon Aurora cho PostgreSQL — với hiệu suất cao và độ sẵn sàng (availability) vượt trội ở quy mô toàn cầu — được sử dụng làm vector store và đánh chỉ mục (index) các embeddings văn bản để hỗ trợ tìm kiếm ngữ nghĩa nhanh chóng và hiệu quả trên hàng triệu đoạn tài liệu.

Nhóm phát triển của Tapestry thiết kế hệ thống quản lý kiến thức với các kho kiến thức công khai và riêng tư riêng biệt, mỗi kho được cấu hình độc lập đáp ứng nhu cầu từng bộ phận. Kho công khai được mọi người trong công ty truy cập, chứa thông tin hoạt động chung; còn các kho riêng tư bị hạn chế bằng kiểm soát truy cập dựa trên vai trò (role-based access control) đối với dữ liệu nhạy cảm của từng bộ phận.

Để thực hiện sự phân tách này, họ sử dụng hai cách:

  1. Vai trò (roles) trong AWS Identity and Access Management (IAM), để quản lý bảo mật danh tính và quyền truy cập tới các dịch vụ và tài nguyên AWS.

  2. Tích hợp giải pháp với hệ thống đăng nhập một lần (single sign-on) của Tapestry.

Kiến trúc không máy chủ (serverless) của giải pháp mang lại trải nghiệm liền mạch cho người dùng đồng thời đảm bảo khả năng mở rộng toàn cầu. Nhân viên có thể truy cập hệ thống quản lý kiến thức từ hầu như bất cứ nơi nào trên thế giới thông qua giao diện chatbot trên web do Amazon CloudFront đảm nhiệm phân phối nội dung bảo mật.

Khi người dùng gửi truy vấn, AWS Lambda — chạy mã theo sự kiện và tự động quản lý tài nguyên tính toán — sẽ khởi tạo các hàm để xử lý yêu cầu, thực hiện các kiểm tra bảo mật cần thiết, và điều hướng truy vấn tới kho kiến thức thích hợp.

Các tài liệu nguồn và metadata được lưu trữ trong Amazon S3 — dịch vụ lưu trữ đối tượng có khả năng truy xuất lượng lớn dữ liệu từ bất cứ nơi nào.

Một đặc điểm nổi bật của hệ thống quản lý kiến thức là khả năng giữ nội dung luôn mới, cập nhật. Đội ngũ Tapestry đã triển khai những quy trình tự động để quét và cập nhật các kho kiến thức, đảm bảo mọi thay đổi trong tài liệu nguồn được phản ánh trong hệ thống.

Họ phát triển một pipeline tự động để theo dõi các kho tài liệu khi có thay đổi, xử lý các tài liệu mới hoặc được chỉnh sửa sử dụng chiến lược chia nhỏ dữ liệu phù hợp với từng loại nội dung, tạo embeddings mới dùng các foundation model Titan của Amazon. Những embeddings mới này sau đó được đánh chỉ mục tự động trong Aurora PostgreSQL vector store để kho kiến thức luôn được cập nhật.


---

## Tạo giá trị doanh nghiệp thông qua quản lý kiến thức được nâng cao

Tapestry đang mở rộng khả năng của hệ thống để biến nó thành một giải pháp mạnh mẽ hơn. Kế hoạch bao gồm triển khai công cụ tìm kiếm hình ảnh để trích xuất và truy vấn thông tin từ nội dung trực quan, bên cạnh việc tích hợp giải pháp vào các hệ thống doanh nghiệp khác để tạo báo cáo và phân tích dữ liệu gần thời gian thực (near real-time).

    “Chúng tôi đang làm việc để hệ thống thông minh và tương tác hơn với phản hồi của người dùng,” Ramakrishnan chia sẻ. “Hiện giờ chúng tôi có tìm kiếm văn bản, và đang xem xét cách có thể bổ sung khả năng giọng nói. Chúng tôi cũng làm việc để đưa dữ liệu cấu trúc vào, nơi người dùng có thể đặt câu hỏi về doanh số, hàng tồn, lưu lượng cửa hàng, và đơn đặt hàng.”

Nhờ generative AI trên AWS, Tapestry đang phá bỏ các silo thông tin, thúc đẩy tốc độ ra quyết định, và bảo tồn kiến thức tổ chức có giá trị mà nếu không có hệ thống này, rất dễ bị mất đi. Giải pháp đã giảm đáng kể thời gian nhân viên dành để tìm thông tin và chờ đợi ý kiến từ chuyên môn bên trong công ty. Đồng thời, các năng lực này giúp nhân viên tập trung vào những công việc chiến lược và đổi mới hơn.

    “Các bộ phận của chúng tôi hưởng lợi từ generative AI trên AWS bởi vì họ ít phải trả lời những câu hỏi thông thường hơn, và từ góc nhìn người dùng, họ nhận được những gì họ muốn nhanh hơn,” Narasimhan cho biết. “Chúng tôi trở nên linh hoạt hơn và có thể hành động nhanh hơn.”


---

## Tác giả

Nishant Singh

        Nishant là Quản lý Giải pháp Khách hàng Cấp cao (Senior Customer Solutions Manager – CSM) tại AWS, nơi anh tập trung chuyên môn của mình vào ngành bán lẻ và hàng tiêu dùng đóng gói (CPG). Sứ mệnh của anh là giúp khách hàng thiết kế và triển khai các giải pháp dựa trên giá trị, mang lại kết quả kinh doanh có thể đo lường được thông qua các công nghệ của AWS. Với tư duy “lấy khách hàng làm trung tâm”, anh tập trung chuyển hóa các thách thức kinh doanh thành cơ hội để thúc đẩy tăng trưởng, đổi mới và nâng cao hiệu quả vận hành bằng cách tận dụng năng lực toàn diện của nền tảng AWS.

Aditya Pendyala

        Aditya là Kiến trúc sư Giải pháp Cấp cao (Principal Solutions Architect) tại AWS, làm việc tại New York (NYC). Anh có kinh nghiệm sâu rộng trong việc thiết kế các ứng dụng dựa trên nền tảng đám mây. Hiện tại, anh đang hợp tác với các doanh nghiệp lớn để giúp họ xây dựng kiến trúc đám mây có khả năng mở rộng cao, linh hoạt và bền bỉ, đồng thời tư vấn toàn diện về các giải pháp trên nền tảng đám mây. Aditya có bằng Thạc sĩ Khoa học Máy tính tại Đại học Shippensburg, và anh tin tưởng vào câu nói: “Khi bạn ngừng học hỏi, bạn ngừng phát triển.”

Aravind Narasimhan

        Aravind Narasimhan là một nhà lãnh đạo cấp cao dày dạn kinh nghiệm, kết hợp giữa tầm nhìn chiến lược về CNTT, kiến trúc hệ thống, đánh giá công nghệ và lập kế hoạch khả thi trong các môi trường hiệu suất cao. Trong suốt sự nghiệp của mình, ông đã dẫn dắt việc triển khai kỹ thuật cho các dự án chuyển đổi Omni, Cloud và ERP, đồng thời xây dựng và phát triển mảng tự động hóa quy trình bằng robot (RPA). Ngoài ra, Aravind còn lãnh đạo Trung tâm Xuất sắc về Trí tuệ nhân tạo (AI Center of Excellence – COE) tại Tapestry, nơi ông thúc đẩy đổi mới và nâng cao hiệu quả trong lĩnh vực AI. Trước khi gia nhập Tapestry, ông đã dẫn dắt nhiều sáng kiến trong các mảng lập kế hoạch, bán hàng, hệ thống POS và giải pháp BI trong ngành bán lẻ. Về học vấn, Aravind có bằng Kỹ sư từ Đại học Bangalore và MBA chuyên ngành Tài chính tại Đại học Rutgers.

Karthigeyan Ramakrishnan

        Karthigeyan Ramakrishnan là một chuyên gia CNTT dày dạn kinh nghiệm với hơn 20 năm trong lĩnh vực lãnh đạo, kiến trúc, tư vấn và triển khai các giải pháp CNTT sáng tạo. Ông đã làm việc trong ngành CNTT bán lẻ, bao phủ nhiều lĩnh vực chức năng khác nhau như quản lý kho, lập kế hoạch, mua hàng, dịch vụ khách hàng, tự động hóa và trí tuệ nhân tạo thế hệ mới (Gen AI). Karthigeyan có kinh nghiệm tư vấn toàn cầu tại nhiều thị trường, bao gồm châu Âu, Ấn Độ, Nam Mỹ và Hoa Kỳ. Tại Tapestry, ông phụ trách mảng Lập kế hoạch và Tự động hóa. Ông có niềm đam mê đặc biệt với Gen AI và luôn tìm cách tận dụng công nghệ này không chỉ để giải quyết vấn đề mà còn để khám phá những cơ hội tiềm năng chưa được khai phá. Ông tốt nghiệp ngành Kỹ thuật Hóa học tại Đại học Anna, Chennai và yêu thích việc áp dụng các nguyên lý thiết kế phản ứng vào giải pháp công nghệ.

---

