---
title: "Blog 3"
date: 2025-09-10
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

## Cửa hàng Chủ động (The Agentic Store): Cách việc điều phối bằng Trí tuệ Nhân tạo sẽ cách mạng hóa ngành bán lẻ vật lý
Tác giả: Justin Swagler

Ngày đăng: 16 tháng 4, 2025

Danh mục: Amazon Bedrock, Amazon Bedrock Agents, Amazon Elastic Kubernetes Service, Amazon SageMaker, Phân tích dữ liệu (Analytics), Trí tuệ nhân tạo sinh tạo (Generative AI), Ngành công nghiệp (Industries), Internet Vạn Vật (IoT), Bán lẻ (Retail)

# Ngày đăng trên AWS Industries Blog

Ngành bán lẻ vật lý — vốn chiếm hơn 80% tổng doanh số bán lẻ tại Hoa Kỳ — đang bước vào một thời kỳ phục hưng hiện đại. Các nhà bán lẻ đang hiện đại hóa mọi khía cạnh, từ trải nghiệm khách hàng cho đến vận hành nội bộ, bằng cách tận dụng sức mạnh của công nghệ.

Tuy nhiên, phần lớn những nỗ lực đầu tư công nghệ này lại tạo ra những “ốc đảo kỹ thuật” (silo) — nơi các hệ thống hoạt động tách biệt, không giao tiếp với nhau, dẫn đến trải nghiệm khách hàng bị phân mảnh và hiệu suất vận hành kém.

Bài viết này khám phá tầm nhìn về “Cửa hàng Chủ động” (Agentic Store) — một cửa hàng vật lý nơi mọi hệ thống, thiết bị và con người đều được điều phối thông minh, thời gian thực bằng trí tuệ nhân tạo (AI), mang lại hiệu quả và trải nghiệm chưa từng có cho cả doanh nghiệp và khách hàng.


---

## Thách thức: Sự chia cắt công nghệ trong ngành bán lẻ

Phần lớn các nhà bán lẻ hiện nay đang đối mặt với một trở ngại cốt lõi ảnh hưởng trực tiếp đến khả năng cạnh tranh và tăng trưởng: hệ sinh thái công nghệ bị phân mảnh.

Theo khảo sát, 84% lãnh đạo bán lẻ cho biết họ gặp khó khăn do dữ liệu bị chia cắt trong các hệ thống khác nhau, trong khi chỉ 37% thực sự có thể kết nối và hợp nhất giữa các hoạt động trực tuyến và tại cửa hàng.

Kết quả là, mỗi sự cố vận hành nhỏ có thể gây ra hàng loạt vấn đề dây chuyền. Ví dụ, khi một thiết bị trong cửa hàng — chẳng hạn máy làm lạnh hoặc máy bán nước — gặp sự cố, nhân viên phải thao tác thủ công qua nhiều hệ thống: tắt thiết bị, điều chỉnh menu điện tử, báo lỗi, cập nhật hàng tồn, thông báo nhân viên, mở yêu cầu bảo trì, v.v.

Những quy trình rời rạc này không chỉ tiêu tốn thời gian mà còn gây tổn thất tài chính nghiêm trọng. Một nghiên cứu của IDC cho thấy, trung bình mỗi giờ hệ thống POS (Point of Sale) ngừng hoạt động có thể khiến một chuỗi bán lẻ thiệt hại hơn 5 triệu USD.

Ngoài ra, “nợ kỹ thuật” (technical debt) phát sinh từ các giải pháp chắp vá — hệ thống tùy chỉnh, tích hợp không đồng bộ, và cập nhật thủ công — đang dần làm chậm tốc độ đổi mới của toàn bộ tổ chức.

Trong khi đó, làn sóng công nghệ mới như IoT, thị giác máy tính, thanh toán không tiếp xúc, kệ hàng thông minh và cảm biến môi trường lại tiếp tục được triển khai nhưng vẫn thiếu khả năng kết nối thống nhất.

Hậu quả là các cửa hàng không thể phản ứng kịp thời với các sự kiện trong thời gian thực, khiến hoạt động dự báo, bảo trì, hoặc tối ưu nhân sự gặp nhiều hạn chế.


## Tầm nhìn: Vận hành bán lẻ được điều phối bởi trí tuệ nhân tạo

Cửa hàng “Agentic Store” biến môi trường bán lẻ rời rạc hiện nay thành một hệ sinh thái được điều phối liền mạch. Được vận hành bởi các dịch vụ AWS, nó tạo ra một nền tảng thống nhất, nơi các tác nhân AI (AI agents) liên tục giám sát, dự đoán và phối hợp phản ứng trên tất cả các hệ thống trong cửa hàng.

Hãy bước vào một nhà hàng phục vụ nhanh trong giờ cao điểm buổi sáng. Cảm biến của máy pha nước ngọt phát hiện nguy cơ sắp gặp trục trặc — trước đây, tình huống này sẽ kích hoạt hàng loạt thao tác thủ công qua nhiều hệ thống, tốn thời gian nhân viên và có thể làm gián đoạn dịch vụ khách hàng. Nhưng trong “Agentic Store”, AI orchestration biến khủng hoảng thành giải pháp trơn tru. Chỉ trong vài giây, các tác nhân AI của cửa hàng bắt đầu hành động: bảng menu kỹ thuật số tự động điều chỉnh để loại bỏ món bị ảnh hưởng, ứng dụng đặt hàng di động cập nhật theo thời gian thực để tránh gây khó chịu cho khách hàng, nhân viên nhận được thông báo ưu tiên công việc trên thiết bị của họ, trong khi hệ thống hiển thị bếp tái cân bằng lịch sản xuất. Một phiếu bảo trì được tự động tạo ra và hệ thống lập lịch thông minh điều chỉnh thời gian nghỉ của nhân viên quanh thời gian sửa chữa dự kiến. Những gì từng mất hàng giờ quản lý xử lý, giờ đây diễn ra chỉ trong vài giây, giúp nhà quản lý tập trung vào đội ngũ và khách hàng thay vì phải xoay sở với các hệ thống rời rạc.

Khả năng điều phối này không chỉ giới hạn ở nhà hàng. Trong siêu thị hiện đại, hệ thống thị giác máy tính giám sát khu vực sản phẩm hữu cơ, nơi các tác nhân AI điều phối một “vũ điệu” tinh vi của quản lý hàng tồn. Khi mức hàng giảm xuống dưới ngưỡng tối ưu, hệ thống tự động kích hoạt nhiệm vụ bổ sung hàng, điều chỉnh nhãn kệ điện tử cho các mặt hàng sắp hết hạn và thông báo cho khách hàng thân thiết về chương trình giảm giá chớp nhoáng — tất cả đều không cần bất kỳ can thiệp thủ công nào.

Sự chuyển đổi này còn mở rộng đến các cửa hàng tiện lợi và trạm xăng, nơi cá nhân hóa kết hợp cùng hiệu quả vận hành. Khi một khách hàng quen lái xe vào trạm xăng buổi sáng, hệ thống cửa hàng nhận ra cô ấy và ngay lập tức bắt đầu điều phối trải nghiệm. Màn hình kỹ thuật số hiển thị bánh sandwich buổi sáng yêu thích của cô đã sẵn sàng và cà phê yêu thích vừa được pha mới. Bên trong, bếp đã xếp hàng sẵn đơn hàng, trong khi màn hình thông minh dọc theo lộ trình mua sắm quen thuộc làm nổi bật các sản phẩm yêu thích. Một giao dịch đổ xăng đơn thuần nay trở thành hành trình mua sắm cá nhân hóa, được điều phối liền mạch bởi các công nghệ cửa hàng kết nối.

Đối với các nhà bán lẻ vận hành hàng nghìn điểm trên toàn cầu, tác động là vô cùng to lớn. Các cửa hàng truyền thống gặp khó khăn với công nghệ rời rạc, thiết bị biên (edge devices) không đồng bộ và xử lý sự cố chậm. Cách tiếp cận “Agentic Store” giúp cải thiện tốc độ xử lý sự cố. Một nhà bán lẻ nhiên liệu toàn cầu, sau khi bắt đầu tích hợp tốt hơn các hệ thống dữ liệu trên AWS, đã cải thiện 30% hiệu quả trong việc xử lý các vấn đề như lỗi thanh toán hoặc thiết bị trục trặc trước khi chúng ảnh hưởng đến khách hàng. Bằng cách kết nối các thiết bị IoT, hệ thống thị giác máy tính, dữ liệu khách hàng và hệ thống hàng tồn thông qua điều phối thông minh, các cửa hàng có thể vận hành hiệu quả hơn và mang lại trải nghiệm khách hàng vượt trội hơn.

Đây chính là cốt lõi của “Agentic Store” — một hệ sinh thái thống nhất nơi AI orchestration biến các hoạt động rời rạc truyền thống thành trải nghiệm được phối hợp nhịp nhàng. Đây không chỉ là tự động hóa; mà là điều phối thông minh, hiểu rõ mối quan hệ phức tạp giữa hàng tồn kho, nhân sự, sở thích khách hàng và hiệu quả vận hành. Kết quả là một môi trường bán lẻ phản ứng nhanh hơn, hiệu quả hơn và có khả năng mang lại trải nghiệm khách hàng xuất sắc hơn, đồng thời giảm chi phí vận hành và tối ưu hóa sử dụng tài sản.

Công nghệ hoạt động hài hòa để giải quyết vấn đề trước khi chúng ảnh hưởng đến người tiêu dùng hoặc gây áp lực cho nhân viên, tạo ra môi trường nơi cả nhân viên và khách hàng đều hưởng lợi từ quy trình mượt mà hơn và tương tác cá nhân hóa hơn. Đây chính là tương lai của bán lẻ thực tế — nơi điều phối thông minh loại bỏ các điểm nghẽn đã tồn tại lâu nay trong vận hành cửa hàng, mở ra kỷ nguyên mới của sự xuất sắc trong ngành bán lẻ.


---

## Lộ trình chiến lược hướng tới tương lai của các cửa hàng

Hành trình trở thành “Agentic Store” đòi hỏi một cách tiếp cận có chiến lược, từng bước rõ ràng, cân bằng giữa việc tạo ra giá trị tức thì và chuyển đổi dài hạn. Tại AWS, chúng tôi đã xác định một lộ trình cụ thể, di chuyển từ nền tảng cơ bản đến tái tạo toàn diện trong khi vẫn duy trì sự ổn định vận hành.

Hành trình này bắt đầu bằng việc xây dựng nền tảng cốt lõi, tập trung vào việc kết nối các hệ thống rời rạc và xử lý “nợ kỹ thuật”. Các nhà bán lẻ trước hết phải thiết lập nền tảng dữ liệu thống nhất bằng cách di chuyển các hệ thống điểm bán hàng (POS) cũ lên đám mây và kết nối các hệ thống vận hành trọng yếu. Điều này bao gồm tích hợp hệ thống quản lý hàng tồn kho, hệ thống nhân sự, thiết bị IoT và nền tảng dữ liệu khách hàng. Mục tiêu là tạo ra cái nhìn tổng thể duy nhất về hoạt động cửa hàng thông qua cơ sở dữ liệu được xây dựng trên AWS và tối ưu hóa tại biên bằng Amazon EKS Hybrid Nodes.

Khi các hệ thống đã được kết nối, nhà bán lẻ có thể bắt đầu đưa trí tuệ nhân tạo vào bằng Amazon SageMaker để hỗ trợ phân tích dự đoán dựa trên máy học và tự động hóa quy trình. Giai đoạn này tập trung vào việc nâng cao trải nghiệm khách hàng thông qua ra quyết định dựa trên dữ liệu. Các năng lực chính bao gồm: tối ưu hóa hàng tồn theo thời gian thực bằng thị giác máy tính và cảm biến IoT, quản lý nhân sự thông minh với phân công công việc do AI điều phối, bảo trì dự đoán cho thiết bị cửa hàng, tự động hóa định giá và quản lý khuyến mãi, cùng khả năng thanh toán không ma sát.

Giai đoạn cuối cùng là khi cửa hàng truyền thống được chuyển hóa hoàn toàn thành môi trường được điều phối tự động, nơi các tác nhân Amazon Bedrock Agents tự động phối hợp phản ứng giữa tất cả các hệ thống trong cửa hàng. Đây là lúc sự khác biệt thực sự xuất hiện — với hoạt động cửa hàng tự động, trải nghiệm khách hàng được cá nhân hóa nhờ dữ liệu thống nhất, robot và tự động hóa nâng cao xử lý các tác vụ lặp lại, công nghệ nhập vai cải thiện trải nghiệm của cả nhân viên và khách hàng, cùng đổi mới dựa trên đám mây giúp triển khai nhanh các tính năng mới.

Trong suốt hành trình này, yếu tố then chốt là mỗi năng lực mới phải được xây dựng dựa trên nền tảng sẵn có thay vì tạo ra những “ốc đảo công nghệ” mới. Để chuyển đổi thành công, cần chú trọng vào đào tạo và quản lý thay đổi, giúp nhân viên cửa hàng và quản lý hiểu cách hợp tác hiệu quả với hệ thống AI. Các nhà bán lẻ nên bắt đầu với những trường hợp sử dụng có tác động cao và ROI rõ ràng, vì những thành công ban đầu sẽ tạo động lực và sự ủng hộ cho quá trình chuyển đổi rộng hơn.

Kiến trúc công nghệ cần được xây dựng trên các dịch vụ đám mây bản địa, cho phép vừa xử lý tại biên cho hoạt động theo thời gian thực, vừa phân tích dữ liệu chuyên sâu trên đám mây để có thêm hiểu biết. Đồng thời, phải triển khai các biện pháp bảo mật toàn diện ngay từ đầu nhằm bảo vệ dữ liệu khách hàng và dữ liệu vận hành.

Khi các nhà bán lẻ tiến xa hơn trong hành trình này, họ sẽ tạo ra các cửa hàng phản ứng nhanh hơn, hiệu quả hơn và mang lại trải nghiệm khách hàng vượt trội hơn. “Agentic Store” không chỉ là tự động hóa – mà là một môi trường bán lẻ thông minh, liên tục học hỏi và thích nghi, giúp nhân viên và khách hàng cùng phát triển, đồng thời thúc đẩy hiệu suất vận hành vượt trội.

---

## Nhìn về tương lai: Tương lai của bán lẻ thực tế

Ngành bán lẻ đang đứng trước một thời điểm quan trọng. Các cửa hàng vật lý sẽ không biến mất – thay vào đó, chúng tiến hóa trở thành những môi trường mạnh mẽ và hiệu quả hơn bao giờ hết. “Agentic Store” đại diện cho bước tiến tiếp theo trong bán lẻ, kết hợp những ưu điểm của cửa hàng vật lý với trí tuệ và tự động hóa của công nghệ đám mây hiện đại.

Thành công trong kỷ nguyên mới này đòi hỏi tư duy lại về cách vận hành cửa hàng truyền thống. Các nhà bán lẻ không chỉ đơn thuần là thêm công nghệ mới mà cần tập trung vào tạo ra môi trường tích hợp, thông minh, nơi các hệ thống phối hợp trơn tru. “Agentic Store” cung cấp khung sườn này, giúp các nhà bán lẻ chuyển đổi vận hành trong khi vẫn duy trì kết nối con người, điều làm cho bán lẻ vật lý trở nên độc đáo.

Sự chuyển đổi này sẽ không xảy ra trong một sớm một chiều, nhưng lộ trình đã rõ ràng: những nhà bán lẻ chấp nhận chuyển đổi theo mô hình “Agentic Store”, đầu tư cả vào công nghệ và con người, sẽ có vị thế tốt nhất để phát triển mạnh trong bối cảnh bán lẻ đang tiến hóa. Những ai duy trì phương thức silo truyền thống sẽ có nguy cơ bị bỏ lại phía sau, khi khách hàng ngày càng mong đợi sự tiện lợi, cá nhân hóa và hiệu quả mà chỉ “Agentic Store” mới có thể mang lại.


---

## Tìm hiểu thêm tại Hội nghị Ban Quản lý Vận hành Cửa hàng 2025

Tôi sẽ chia sẻ thêm quan điểm về Agentic Stores tại Hội nghị Ban Quản lý Vận hành Cửa hàng tháng 6/2025. Nếu bạn quan tâm đến việc kết nối với cộng đồng quản lý vận hành cửa hàng và tìm hiểu thêm về cách AWS hỗ trợ các nhà bán lẻ trong quá trình chuyển đổi này, hãy đăng ký ngay để đảm bảo chỗ tham dự tại sự kiện đầy ý nghĩa này.

---

## Tác giả

Justin Swagler

    Justin Swagler là Trưởng bộ phận Bán lẻ Vật lý Toàn cầu (Worldwide Head of Physical Retail) tại AWS, nơi ông dẫn dắt chiến lược toàn cầu và tư duy lãnh đạo trong lĩnh vực bán lẻ vật lý. Justin có hơn 15 năm kinh nghiệm trong ngành hàng tiêu dùng đóng gói, bán lẻ và chiến lược, bao gồm chiến lược đổi mới, vận hành bán lẻ, phát triển sản phẩm và lãnh đạo cấp cao. Ông đam mê hướng dẫn các tổ chức đổi mới chiến lược và tái tạo trải nghiệm người tiêu dùng. Justin tốt nghiệp cử nhân tại Đại học Illinois, Urbana-Champaign và có MBA từ Trường Quản lý Kellogg.
