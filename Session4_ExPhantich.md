Session4_ExPhantich

Bước 1: Hai prompt mẫu

Giải pháp 1 (đơn giản)

Hãy phân tích quy trình xử lý đơn hàng bằng Prompt Chaining. Kiểm tra thông tin đơn, kiểm tra tồn kho rồi đưa ra kết luận. Nếu thiếu dữ liệu hoặc một bước bị lỗi, không tự đoán và nêu rõ vấn đề. Trả lời ngắn gọn theo các mục: kiểm tra dữ liệu, kiểm tra tồn kho, kết quả.

Giải pháp 2 (chi tiết)

Bạn là trợ lý kiểm tra đơn hàng. Xử lý lần lượt theo ba bước: (1) kiểm tra có mã đơn, thông tin khách, địa chỉ, sản phẩm và số lượng; (2) kiểm tra số lượng đặt là số nguyên dương và so sánh với tồn kho; (3) chỉ kết luận đơn sẵn sàng khi dữ liệu hợp lệ và tồn kho đủ.

Quy tắc xử lý:
- Thiếu thông tin: kết quả NEED_INFO và liệt kê trường còn thiếu.
- Dữ liệu sai định dạng hoặc số lượng không hợp lệ: kết quả INVALID và nêu lỗi.
- Tồn kho thấp hơn số lượng đặt: kết quả OUT_OF_STOCK và ghi sản phẩm thiếu.
- Dữ liệu hợp lệ, tồn kho đủ: kết quả READY.
- Nếu một bước không có kết quả hoặc bị gián đoạn, không tiếp tục như thể bước đó thành công; trả NEED_INFO và nêu bước bị gián đoạn.
- Không tự đoán, sửa hoặc tạo dữ liệu.
- Không trình bày suy luận nội bộ. Chỉ trả kết quả ngắn gọn theo cấu trúc: status, errors, steps, note.

Bước 2: So sánh Trade-off

Tiêu chí: Độ dễ hiểu
Giải pháp 1: Cao, prompt ngắn và dễ dùng.
Giải pháp 2: Trung bình, có nhiều quy tắc cần đọc.

Tiêu chí: Tốn token
Giải pháp 1: Ít.
Giải pháp 2: Nhiều hơn.

Tiêu chí: Chặn lỗi biên
Giải pháp 1: Trung bình; chỉ nêu chung việc thiếu dữ liệu hoặc lỗi.
Giải pháp 2: Tốt; phân biệt dữ liệu thiếu, dữ liệu sai, hết hàng và chuỗi bị gián đoạn.

Tiêu chí: Độ nhất quán đầu ra
Giải pháp 1: Trung bình; chưa quy định cấu trúc chi tiết.
Giải pháp 2: Cao hơn; quy định trạng thái và các trường cần trả về.

Bước 3: Lựa chọn và chạy thử

Lựa chọn: Giải pháp 2. Dù tốn nhiều token hơn và cần đọc kỹ hơn, phương án này phù hợp khi xử lý nhiều đơn hàng vì quy định rõ từng bước, trạng thái lỗi và cách xử lý khi chuỗi bị đứt gãy.

Input chạy thử:
Mã đơn DH205; khách hàng Nguyễn An; số điện thoại 0901234567; địa chỉ 10 Lê Lợi, Đà Nẵng; sản phẩm SP01, số lượng đặt 2; tồn kho SP01 còn 5.

Kết quả:
status: READY
errors: []
steps: Kiểm tra dữ liệu hợp lệ; tồn kho đủ; đơn hàng sẵn sàng.
note: Có thể chuyển đơn sang bước đóng gói.
