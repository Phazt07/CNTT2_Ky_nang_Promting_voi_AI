Session3_ExBaithuchanh2

Vấn đề

Một cửa hàng trực tuyến nhận được rất nhiều phản hồi mỗi ngày. Cần tự động phân loại cảm xúc và chủ đề để chuyển phản hồi đến đúng bộ phận, đồng thời tổng hợp kết quả trên Dashboard.

Yêu cầu

Tạo prompt để phân tích phản hồi khách hàng và trả về một JSON object gồm:
- sentiment: Positive, Negative hoặc Neutral
- topics: danh sách gồm Product, Delivery, Service, System
- score: điểm hài lòng từ 1 đến 5
- summary: tóm tắt dưới 15 từ, bỏ từ cảm thán không cần thiết

Một phản hồi có thể có nhiều chủ đề. Ví dụ, khách khen giao hàng nhanh nhưng chê sản phẩm thì topics phải có cả Delivery và Product. Nếu phản hồi trống hoặc không đọc được, trả về Invalid. Chỉ dùng prompt, không dùng thư viện ngoài. Kết quả cuối cùng phải là JSON thô, không thêm định dạng hay giải thích.

Cách làm

Dùng prompt sau:

Bạn là chuyên gia phân tích dữ liệu thị trường. Hãy đọc phản hồi khách hàng và phân loại theo hướng dẫn dưới đây.

Sentiment chỉ được là Positive, Negative hoặc Neutral. Topics là danh sách gồm một hoặc nhiều giá trị trong Product, Delivery, Service, System. Gắn tất cả chủ đề được đề cập trong phản hồi. Nếu khách vừa khen vừa chê ở các chủ đề khác nhau, chọn cảm xúc chính theo ý kiến nổi bật và vẫn ghi đủ các chủ đề.

Score là số nguyên từ 1 đến 5, trong đó 1 là rất không hài lòng và 5 là rất hài lòng. Summary tóm tắt nội dung dưới 15 từ, không giữ lại từ cảm thán thừa.

Nếu phản hồi trống hoặc chứa ký tự không thể đọc được, trả về:
{"sentiment":"Invalid","topics":[],"score":null,"summary":"Invalid"}

Chỉ trả về một JSON object hợp lệ theo cấu trúc:
{"sentiment":"...","topics":["..."],"score":1,"summary":"..."}
Không thêm lời giải thích, tiêu đề, Markdown hay nội dung nào khác.

Ví dụ 1
Phản hồi: Giao hàng rất nhanh, tôi nhận được hàng sớm hơn dự kiến.
Kết quả: {"sentiment":"Positive","topics":["Delivery"],"score":5,"summary":"Giao hàng nhanh hơn dự kiến"}

Ví dụ 2
Phản hồi: Sản phẩm bị lỗi, ứng dụng cũng không mở được.
Kết quả: {"sentiment":"Negative","topics":["Product","System"],"score":1,"summary":"Sản phẩm bị lỗi và ứng dụng không mở được"}

Ví dụ 3
Phản hồi: Sản phẩm đúng như mô tả, nhưng giao hàng nhanh hơn dự kiến.
Kết quả: {"sentiment":"Neutral","topics":["Product","Delivery"],"score":3,"summary":"Sản phẩm đúng mô tả và giao hàng nhanh"}

Ví dụ 4
Phản hồi: Giao hàng nhanh nhưng hộp sản phẩm bị móp méo.
Kết quả: {"sentiment":"Negative","topics":["Delivery","Product"],"score":2,"summary":"Giao hàng nhanh nhưng sản phẩm bị móp méo"}

Phản hồi cần phân tích:
{{PHAN_HOI_KHACH_HANG}}
