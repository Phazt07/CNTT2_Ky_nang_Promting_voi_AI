Session4_ExBTTH

Báo cáo thiết kế giải pháp

Bài toán

Cửa hàng trực tuyến muốn tự động phân tích phản hồi khách hàng và chuyển đến đúng bộ phận. Quy trình gồm các bước nối tiếp: kiểm tra dữ liệu, phân loại phản hồi, xác định bộ phận phụ trách và tạo kết quả JSON.

Input

Mã phản hồi (có thể thiếu) và nội dung phản hồi của khách hàng.

Output

Một JSON object gồm id, status, sentiment, topics, department, summary và errors. Sentiment là Positive, Negative, Neutral hoặc Invalid. Topics có thể gồm Product, Delivery, Service, System. Department là Product, Delivery, Customer Service, Technical hoặc null.

Cách xử lý lỗi

Nếu phản hồi trống hoặc không đọc được, dừng chuỗi và trả Invalid. Nếu một bước không có đầu ra hoặc sai định dạng, thử lại bước đó một lần. Nếu vẫn lỗi, trả status NEED_REVIEW, ghi bước bị lỗi và không tự tạo dữ liệu. Chỉ chuyển kết quả hợp lệ sang bước kế tiếp. Không yêu cầu AI xuất suy luận nội bộ; chỉ yêu cầu kết quả và trạng thái từng bước.

Prompt hệ thống

Bạn là trợ lý phân tích phản hồi khách hàng cho cửa hàng trực tuyến. Làm theo đúng các bước dưới đây. Không suy đoán thông tin, không trình bày suy luận nội bộ. Chỉ tạo dữ liệu theo yêu cầu của từng bước.

Bước 1 – Kiểm tra dữ liệu

Prompt:
Kiểm tra mã phản hồi và nội dung. Nếu nội dung trống hoặc không thể đọc, trả JSON {"status":"INVALID","error":"Phản hồi trống hoặc không đọc được"}. Nếu đọc được, trả {"status":"OK","id":"...","text":"..."}. Giữ nguyên nội dung phản hồi, không tự sửa nghĩa.

Bước 2 – Phân loại

Chỉ chạy khi bước 1 có status OK.

Prompt:
Dựa trên nội dung đã kiểm tra, phân loại sentiment thành Positive, Negative, Neutral hoặc Invalid. Chọn tất cả topics phù hợp trong Product, Delivery, Service, System. Viết summary ngắn dưới 15 từ. Nếu phản hồi đề cập nhiều chủ đề, ghi đủ các chủ đề. Trả JSON gồm sentiment, topics, summary. Không thêm giải thích.

Bước 3 – Chuyển bộ phận

Chỉ chạy khi bước 2 có kết quả hợp lệ.

Prompt:
Dựa trên topics, chọn department theo quy tắc: Product -> Product; Delivery -> Delivery; Service -> Customer Service; System -> Technical. Nếu có nhiều chủ đề, trả danh sách các bộ phận tương ứng, không trùng lặp. Nếu không có chủ đề phù hợp, dùng null. Trả JSON gồm department.

Bước 4 – Ghép kết quả

Prompt:
Ghép dữ liệu của các bước trước thành đúng một JSON object theo cấu trúc:
{"id":"...","status":"OK","sentiment":"...","topics":[],"department":[],"summary":"...","errors":[]}
Chỉ trả JSON hợp lệ, không Markdown hay lời giải thích. Nếu dữ liệu đầu vào bị Invalid, dùng status INVALID, sentiment Invalid, topics [], department null, summary "", và ghi lỗi vào errors. Nếu một bước bị thiếu hoặc sai định dạng sau một lần thử lại, dùng status NEED_REVIEW, các giá trị chưa xác định là null hoặc [], và ghi tên bước lỗi trong errors. Không tự điền dữ liệu.

Dữ liệu cần xử lý:
ID: FB-301
Phản hồi: Giao hàng nhanh nhưng ứng dụng thanh toán bị lỗi.

Kết quả chạy thử

{"id":"FB-301","status":"OK","sentiment":"Negative","topics":["Delivery","System"],"department":["Delivery","Technical"],"summary":"Giao hàng nhanh nhưng ứng dụng thanh toán bị lỗi","errors":[]}
