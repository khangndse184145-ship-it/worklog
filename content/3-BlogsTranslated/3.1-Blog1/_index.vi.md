---
title: "Blog 1"
date: 2025-09-10
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Bắt đầu xây dựng hệ thống thông minh giọng nói với mô hình chuyển lời nói thành văn bản của AssemblyAI từ AWS Marketplace
 Tác giả: Shun Mao và Zackary Klebanoff

 Ngày đăng: 16 tháng 4, 2025

 Nguồn: AWS Marketplace Blog


# Giới thiệu

Công nghệ trí tuệ giọng nói (voice intelligence) và chuyển giọng nói thành văn bản (Speech-to-Text – STT) đã trở nên thiết yếu khi các tổ chức thu thập hàng nghìn giờ ghi âm cuộc gọi, cuộc họp và tương tác với khách hàng mỗi ngày. Tuy nhiên, chỉ riêng dữ liệu âm thanh thô thì không thể giúp đưa ra quyết định — các tổ chức cần có khả năng khai thác thông minh để rút ra giá trị từ dữ liệu giọng nói ở quy mô lớn.

Trí tuệ giọng nói kết hợp giữa công nghệ nhận dạng giọng nói, xử lý ngôn ngữ tự nhiên (NLP) và học máy (ML) để biến dữ liệu âm thanh thành những thông tin có thể hành động được. Các mô hình STT hiện đại có khả năng phiên âm hội thoại với độ chính xác cao và phối hợp với các công cụ bổ trợ khác để phân tích cảm xúc, phát hiện chủ đề chính, cũng như tạo ra bản tóm tắt tự động nhằm cung cấp những hiểu biết sâu hơn.

Công nghệ trí tuệ giọng nói và STT được ứng dụng rộng rãi trong nhiều lĩnh vực như: phân tích cuộc gọi và trí tuệ hội thoại, ghi chép y tế, dịch vụ khách hàng, tối ưu hóa nội dung video, tra cứu và tuân thủ pháp lý, phân tích và huấn luyện bán hàng, v.v.
Với sự xuất hiện của trí tuệ nhân tạo tạo sinh (Generative AI) và các mô hình ngày càng tiên tiến hơn, nhu cầu về các mô hình STT hiệu quả tiếp tục tăng mạnh trong những ứng dụng này.


---

## Giới thiệu về AssemblyAI

AssemblyAI, một nhà cung cấp phần mềm độc lập (ISV) trên AWS Marketplace, là một tổ chức định hướng nghiên cứu với mục tiêu thúc đẩy và phổ cập công nghệ trí tuệ nhân tạo giọng nói (speech AI) trên toàn cầu. Được thành lập vào năm 2017, công ty đã xây dựng một đội ngũ gồm các nhà nghiên cứu liên ngành, nhà khoa học và kỹ sư, cùng chung mục tiêu phát triển những mô hình AI giọng nói siêu việt, mở ra nhiều khả năng mới cho các ứng dụng dựa trên dữ liệu âm thanh.
Công nghệ của AssemblyAI hiện phục vụ hàng nghìn khách hàng và hàng trăm nghìn nhà phát triển trên toàn thế giới thông qua một API đơn giản, thân thiện với lập trình viên. AssemblyAI cung cấp các khả năng toàn diện về AI giọng nói, bao gồm:
Chuyển giọng nói thành văn bản (Speech-to-Text) cốt lõi


Nhận diện người nói (Speaker Detection)


Tự động nhận dạng ngôn ngữ (Automatic Language Detection)


Phân tích cảm xúc (Sentiment Analysis)


Phát hiện chương mục nội dung (Chapter Detection)


Ẩn thông tin nhận dạng cá nhân (PII Redaction)


Mô hình Universal-2 thể hiện cam kết của AssemblyAI trong việc không ngừng mở rộng giới hạn của công nghệ AI giọng nói. Mô hình này đạt độ chính xác cao nhờ giải quyết các thách thức cốt lõi trong nhận dạng giọng nói, cải thiện khả năng nhận dạng danh từ riêng, định dạng văn bản, viết hoa, và tạo dấu thời gian chính xác. AssemblyAI áp dụng phương pháp tiếp cận dựa trên nghiên cứu để xây dựng các mô hình AI giọng nói vừa mạnh mẽ vừa dễ dàng tích hợp.
Bài viết này sẽ hướng dẫn cách bắt đầu với API của AssemblyAI trên AWS Marketplace, đồng thời xây dựng bản thử nghiệm ban đầu (Proof of Concept – POC) bằng cách gọi các API mô hình này chỉ trong vài bước đơn giản.


## Tổng quan giải pháp


---

Dịch vụ chuyển giọng nói thành văn bản (Speech-to-Text) của AssemblyAI xử lý âm thanh thông qua quy trình hai giai đoạn.
Ở giai đoạn đầu, hệ thống sử dụng mô hình Universal-2 ASR (Automatic Speech Recognition) — một mô hình Conformer RNN-T với 600 triệu tham số, được huấn luyện trên 12,5 triệu giờ dữ liệu âm thanh đa ngôn ngữ. Mô hình này có khả năng chuyển đổi giọng nói thành văn bản đồng thời xử lý hiệu quả các tình huống phức tạp như nhiều người nói cùng lúc, đa dạng giọng địa phương, và nhiễu nền.
Ở giai đoạn thứ hai, hệ thống áp dụng các mô hình thần kinh (neural models) để định dạng văn bản, bao gồm thêm dấu câu, viết hoa, và chuẩn hóa văn bản, nhằm tạo ra bản phiên âm sạch, dễ đọc và chuyên nghiệp.
Ngoài chức năng phiên âm cơ bản, người dùng có thể kích hoạt thêm các mô hình trí tuệ bổ sung chạy song song với quá trình ASR chính. Các mô hình này bao gồm:
Nhận diện người nói (Speaker Identification) – xác định ai nói gì trong cuộc hội thoại.


Phân tích cảm xúc (Sentiment Analysis) – hiểu được sắc thái và cảm xúc trong lời nói.


Phát hiện chủ đề (Topic Detection) – tự động phân loại nội dung hội thoại.


Tóm tắt nội dung (Content Summarization) – rút trích các ý chính quan trọng.


Ẩn thông tin nhận dạng cá nhân (PII Redaction) – đảm bảo tuân thủ các yêu cầu về quyền riêng tư.


Tất cả các mô hình này hoạt động liền mạch thông qua cùng một giao diện API, giúp nhà phát triển dễ dàng tích hợp và mở rộng khả năng phân tích giọng nói.

<img src="/images/blog1.png" alt="Sơ đồ kiến trúc cấp cao cho API của AssemblyAI về phiên mã" width="600">

> *Hình 1: Sơ đồ kiến ​​trúc cấp cao cho API của AssemblyAI về phiên mã*

---

## Yêu cầu chuẩn bị

Trước khi bắt đầu, hãy đảm bảo bạn đã có đầy đủ các điều kiện sau:
Tài khoản Amazon Web Services (AWS) có quyền truy cập vào Amazon Simple Storage Service (Amazon S3).


Dịch vụ API của AssemblyAI có thể được mua trên AWS Marketplace. Ngoài ra, bạn cũng có thể truy cập trang web của AssemblyAI để đăng ký tài khoản dùng thử (trial account).


Với tài khoản dùng thử, hệ thống sẽ được nạp sẵn một lượng tín dụng miễn phí, cho phép bạn thực hiện thử nghiệm Proof of Concept (POC) ngay lập tức.



Sau khi tạo tài khoản AssemblyAI thành công, hãy lưu khóa API (API key) ở nơi an toàn để sử dụng trong các bước tiếp theo.


Tiếp theo, hãy chạy đoạn mã Python sau để chuẩn bị cho các kịch bản trong phần hướng dẫn triển khai (solution walkthrough):

!pip install assemblyai

import assemblyai as aai

aai.settings.api_key = "xxxxxxxx"  #your AssemblyAI API key


---

## Hướng dẫn giải pháp
 
Trong phần này, chúng ta sẽ tìm hiểu năm trường hợp mà API của AssemblyAI có thể mang lại giá trị cao.

Mỗi trường hợp đều đi kèm với đoạn mã minh họa, giúp người đọc có thể tự thử nghiệm trong môi trường của mình.

  1. Phiên âm âm thanh từ tệp cục bộ (Transcribe an audio from a local file)

  2. Phiên âm tệp âm thanh từ Amazon S3 (Transcribe an audio file from Amazon S3)

  3. Phân tách người nói (Speaker diarization)

  4. Tự động nhận dạng ngôn ngữ (Automatic language detection)

  5. Ẩn thông tin nhận dạng cá nhân (PII redaction)


---

## Phiên âm tệp âm thanh từ Amazon S3

Trong nhiều tổ chức, dữ liệu âm thanh thường được lưu trữ trên dịch vụ lưu trữ đám mây, chẳng hạn như Amazon S3.

Để phiên âm tệp âm thanh từ S3 bucket, AssemblyAI cần được cấp quyền truy cập tạm thời vào tệp đó.

Để cung cấp quyền truy cập này, bạn cần tạo một URL có quyền truy cập tạm thời (presigned URL) — đây là một đường dẫn đặc biệt cho phép truy cập tệp trong thời gian giới hạn.

Để biết thêm chi tiết về cách tạo presigned URL, hãy tham khảo tài liệu: “Chia sẻ đối tượng bằng presigned URL (Sharing objects with presigned URLs)” của AWS.

Thực thi đoạn mã Python sau để tiến hành phiên âm:

    import requests

    import time

    p_url = "S3 pre-signed url"

    assembly_key = "xxxxxxxx"  # API key của bạn tại AssemblyAI

    # Sử dụng API key của AssemblyAI để xác thực

    headers = {"authorization": assembly_key, "content-type": "application/json"}

    # Địa chỉ endpoint của API phiên âm AssemblyAI

    upload_endpoint = "https://api.assemblyai.com/v2/transcript"

    # Sử dụng presigned URL làm giá trị của `audio_url` trong yêu cầu POST

    json = {"audio_url": p_url}

    # Gửi yêu cầu POST để đưa tệp âm thanh vào hàng đợi phiên âm

    post_response = requests.post(upload_endpoint, json=json, headers=headers)

    # Lấy endpoint của tiến trình xử lý

    get_endpoint = upload_endpoint + "/" + post_response.json()["id"]

    # Gửi yêu cầu GET để kiểm tra trạng thái phiên âm

    get_response = requests.get(get_endpoint, headers=headers)

    # Nếu quá trình phiên âm chưa hoàn tất, chờ đến khi hoàn tất

    while get_response.json()["status"] != "completed":

        get_response = requests.get(get_endpoint, headers=headers)

        time.sleep(5)

    # Khi quá trình phiên âm hoàn tất, in kết quả ra màn hình

    print(get_response.json()["text"])


---

## Phiên âm âm thanh từ tệp cục bộ

Đây là thiết lập cơ bản, trong đó các tệp âm thanh được lưu trữ tại thư mục cục bộ nơi mã lệnh được thực thi.

API của AssemblyAI hỗ trợ hầu hết các định dạng âm thanh và video phổ biến như mp3, m4a, m4p, wav, hoặc wma.

Khuyến nghị nên sử dụng tệp âm thanh ở định dạng gốc của nó, không nên chuyển mã (transcode) hoặc chuyển đổi định dạng (convert) để đảm bảo chất lượng nhận dạng tốt nhất.

Để biết thêm thông tin chi tiết về các định dạng tệp âm thanh, bạn có thể tham khảo bài viết blog của AssemblyAI.

Hãy tải xuống một tệp âm thanh công khai từ trang web được AssemblyAI lưu trữ, sau đó lưu vào thư mục cục bộ của bạn.

Thực thi đoạn mã dưới đây để tiến hành phiên âm:

    # Phiên âm tệp âm thanh cục bộ

    transcriber = aai.Transcriber()

    transcript = transcriber.transcribe("./Audios/ford_clip_trimmed.mp3")

    print(transcript.text)

Kết quả thu được sẽ tương tự như bản phiên âm sau:

“Chào buổi tối. Vào ngày 15 tháng 1 vừa qua, tôi đã trình bày trước các thượng nghị sĩ và hạ nghị sĩ trong Quốc hội một kế hoạch toàn diện nhằm giúp đất nước chúng ta độc lập với các nguồn năng lượng từ nước ngoài trước năm 1985. Chương trình như vậy đã bị trì hoãn quá lâu. Chúng ta ngày càng phụ thuộc vào người khác về nhiên liệu – thứ mà toàn bộ nền kinh tế của chúng ta vận hành dựa trên đó.

Dưới đây là những dữ kiện và con số không thể phớt lờ. Hoa Kỳ hiện đang phụ thuộc vào các nguồn nước ngoài cho khoảng 37% nhu cầu dầu mỏ hiện tại. Trong vòng 10 năm nữa, nếu chúng ta không hành động, chúng ta sẽ phải nhập khẩu hơn một nửa lượng dầu với mức giá do người khác quyết định — nếu họ còn muốn bán cho chúng ta. Trong hai năm rưỡi tới, chúng ta sẽ trở nên dễ bị tổn thương gấp đôi trước một lệnh cấm vận dầu mỏ từ nước ngoài so với hai mùa đông trước.
Hiện nay, chúng ta đang chi ra 25 tỷ đô la mỗi năm cho dầu nhập khẩu. Năm năm trước, con số này chỉ là 3 tỷ đô la mỗi năm. Năm năm nữa, nếu chúng ta vẫn không làm gì, ai biết được sẽ còn bao nhiêu tỷ đô la nữa sẽ chảy ra khỏi nước Mỹ.”


---

## Nhận diện người nói (Speaker diarization)

Nhận diện người nói là một thành phần quan trọng trong xử lý âm thanh, vì nó giải quyết thách thức xác định danh tính của người nói và thời điểm họ nói trong một bản ghi âm. Khả năng này rất cần thiết cho nhiều tác vụ khác nhau, chẳng hạn như cải thiện độ rõ ràng và cấu trúc của bản ghi, hỗ trợ phân tích nâng cao, cũng như cho phép cá nhân hóa và tùy chỉnh nội dung.

Thực thi đoạn mã sau để thực hiện việc phiên âm:

    config = aai.TranscriptionConfig(speaker_labels=True)

    transcriber = aai.Transcriber(config=config)

    FILE_URL = "https://github.com/AssemblyAI-Examples/audio-examples/raw/main/20230607_me_canadian_wildfires.mp3"

    transcript = transcriber.transcribe(FILE_URL)

    # Trích xuất tất cả các đoạn hội thoại từ kết quả phản hồi

    utterances = transcript.utterances

    # Với mỗi đoạn hội thoại, in ra người nói và nội dung họ nói

    for utterance in utterances:

      speaker = utterance.speaker

      text = utterance.text

      print(f"Speaker {speaker}: {text}")

Bản ghi sau đây cho thấy một phần kết quả của ví dụ này:

Người nói A: Khói từ hàng trăm vụ cháy rừng ở Canada đang gây ra các cảnh báo về chất lượng không khí trên khắp nước Mỹ. Đường chân trời từ Maine đến Maryland đến Minnesota đều mờ xám và đầy khói bụi. Ở một số nơi, cảnh báo chất lượng không khí còn khuyến cáo mọi người nên ở trong nhà. Chúng tôi muốn hiểu rõ hơn điều gì đang xảy ra và lý do tại sao, vì vậy chúng tôi đã gọi cho Peter DeCarlo, phó giáo sư tại Khoa Sức khỏe Môi trường và Kỹ thuật của Đại học Johns Hopkins. Chào buổi sáng, Giáo sư.

Người nói B: Chào buổi sáng.

Người nói A: Vậy điều kiện hiện tại có gì khiến đợt cháy rừng này ảnh hưởng đến nhiều người ở xa như vậy?

Người nói B: Ồ, có một vài nguyên nhân. Mùa này đã khá khô hạn, và việc nước Mỹ bị ảnh hưởng là do có một vài hệ thống thời tiết đang dẫn luồng khói từ các đám cháy rừng ở Canada qua Pennsylvania vào vùng trung Đại Tây Dương và Đông Bắc, rồi tích tụ khói ở đó.

Người nói A: Vậy trong làn sương mù này có gì khiến nó trở nên nguy hại? Tôi đoán là nó có hại, đúng không?

---
## Tự động nhận dạng ngôn ngữ 
Tự động nhận dạng ngôn ngữ là một tính năng quan trọng khác trong phân tích âm thanh, vì nó giúp hệ thống xử lý và hiểu nội dung nói một cách chính xác và hiệu quả hơn.

Tính năng này có thể nâng cao trải nghiệm người dùng trong nhiều ứng dụng bằng cách hỗ trợ đa ngôn ngữ và cho phép tùy chỉnh theo từng ngôn ngữ cụ thể.

Thực thi đoạn mã sau để thực hiện việc phiên âm:

    config = aai.TranscriptionConfig(language_detection=True)

    transcriber = aai.Transcriber(config=config)

    FILE_URL = "https://assembly.ai/news.mp4"

    transcript = transcriber.transcribe(FILE_URL)

    transcript.json_response['language_code']

Kết quả đầu ra trong ví dụ này rất ngắn: en.

Để xem danh sách đầy đủ các ngôn ngữ được hỗ trợ, vui lòng tham khảo tài liệu Supported Language.

---

## Ẩn thông tin nhận dạng cá nhân 
Bảo mật luôn là ưu tiên hàng đầu tại AWS và cả AssemblyAI.

Tính năng PII redaction mà AssemblyAI cung cấp giúp duy trì quyền riêng tư và bảo mật cho các thông tin nhạy cảm, cho phép khách hàng xây dựng những ứng dụng an toàn và đáng tin cậy mà không gặp rủi ro pháp lý hoặc vi phạm quy định.

Người dùng có thể kiểm soát loại dữ liệu nhạy cảm nào — chẳng hạn như số thẻ tín dụng, địa chỉ email và số điện thoại — mà họ muốn ẩn thông qua phần cấu hình, như được minh họa trong đoạn mã sau:

    config = aai.TranscriptionConfig()

    config.set_redact_pii( 

      # Các loại dữ liệu cần được ẩn

      policies=[

          aai.PIIRedactionPolicy.credit_card_number,

          aai.PIIRedactionPolicy.email_address,

          aai.PIIRedactionPolicy.location,

          aai.PIIRedactionPolicy.person_name,

          aai.PIIRedactionPolicy.phone_number, 
      ], 

      # Cách thức ẩn thông tin

      substitution=aai.PIISubstitutionPolicy.hash, 
    ) 

    transcriber = aai.Transcriber(config=config) 

    # Sử dụng tệp âm thanh của riêng bạn có chứa một số thông tin PII giả để kiểm thử

    FILE_URL = "https://example.org/audio.mp3" 

    transcript = transcriber.transcribe(FILE_URL) 

    print(transcript.text)

AssemblyAI cung cấp thêm nhiều sản phẩm khác không được đề cập trong bài viết này, bao gồm API truyền trực tiếp (streaming API) cho việc phiên âm theo thời gian thực và LeMUR để trích xuất thông tin chuyên sâu từ bản ghi âm bằng các mô hình ngôn ngữ lớn (LLMs).
Để biết thêm thông tin chi tiết, vui lòng tham khảo tài liệu AssemblyAI.

---

## Kết luận
AssemblyAI cam kết xây dựng một nền tảng API chất lượng cao dành cho các nhà phát triển, giúp chuyển đổi và hiểu dữ liệu giọng nói bằng AI, từ đó tạo ra những sản phẩm và dịch vụ sáng tạo.

Các mô hình speech-to-text của AssemblyAI giải quyết những thách thức quan trọng trong quá trình phiên âm.

Mô hình mới nhất của họ — Universal-2 — tập trung vào việc xử lý các vấn đề “chặng cuối” ảnh hưởng đến quy trình AI giọng nói trong thực tế, chẳng hạn như nâng cao độ chính xác của chữ số, ký tự đặc biệt và từ hiếm.

Tìm hiểu thêm về những cải tiến của Universal-2: [Đọc blog của AssemblyAI]

Xem cách AssemblyAI so sánh với các đối thủ: [Xem bảng so sánh hiệu năng]

Khám phá nghiên cứu phía sau Universal-2: [Tìm hiểu nghiên cứu]

Bạn có thể bắt đầu sử dụng API của AssemblyAI bằng cách truy cập trang sản phẩm trên AWS Marketplace hoặc tạo tài khoản trực tiếp trên trang web của AssemblyAI.
---

## Tác giả

Shun Mao

        Shun Mao là kiến trúc sư giải pháp đối tác cao cấp trong nhóm đối tác phần mềm độc lập (ISV) chuyên về trí tuệ nhân tạo và học máy (AI/ML) tại Amazon Web Services (AWS). Ông có nhiều năm kinh nghiệm trong khoa học dữ liệu, phân tích, AI và điện toán đám mây trên nhiều lĩnh vực khác nhau, bao gồm dầu khí và dược phẩm. Tại AWS, ông hỗ trợ các đối tác chiến lược về AI/ML xây dựng sản phẩm và giải pháp sáng tạo nhằm mang lại giá trị kinh doanh cho khách hàng. Ngoài công việc, Shun Mao thích câu cá, du lịch và chơi bóng bàn.

Zackary Klebanoff

        Zackary Klebanoff là kiến trúc sư giải pháp cao cấp tại AssemblyAI. Anh có nhiều năm kinh nghiệm hỗ trợ khách hàng tận dụng công nghệ trí tuệ nhân tạo giọng nói (speech AI) để xây dựng những sản phẩm và ứng dụng tuyệt vời. Trong suốt sự nghiệp của mình, anh đã làm việc tại các công ty khởi nghiệp, giúp họ phát triển bằng cách kết nối giữa công nghệ và các ứng dụng thực tế. Ngoài công việc, Zackary thích chơi bóng rổ, tham dự các buổi hòa nhạc và cổ vũ cho đội bóng Philadelphia Eagles.



