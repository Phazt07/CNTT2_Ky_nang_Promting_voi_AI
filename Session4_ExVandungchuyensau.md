Session4_ExVandungchuyensau

Báo cáo phân tích

Bài toán

Cửa hàng cần kiểm tra thông tin đơn hàng trước khi chuyển sang bộ phận đóng gói. Prompt sẽ kiểm tra dữ liệu khách hàng, sản phẩm, số lượng, tồn kho và địa chỉ giao hàng. Quy trình dùng Prompt Chaining để tách việc kiểm tra dữ liệu, kiểm tra tồn kho và đưa ra kết quả xử lý.

Input

- Mã đơn hàng
- Tên và số điện thoại khách hàng
- Địa chỉ giao hàng
- Danh sách sản phẩm và số lượng đặt
- Danh sách sản phẩm và số lượng tồn kho

Output

Một JSON object gồm mã đơn hàng, trạng thái, danh sách lỗi, các bước xử lý và ghi chú. Trạng thái chỉ gồm READY, NEED_INFO, OUT_OF_STOCK hoặc INVALID. Không được tự đoán dữ liệu còn thiếu. Nếu dữ liệu thiếu thì NEED_INFO; nếu sai định dạng hoặc số lượng không hợp lệ thì INVALID; nếu tồn kho không đủ thì OUT_OF_STOCK; nếu hợp lệ và đủ hàng thì READY.

Prompt thực thi

Bạn là trợ lý kiểm tra đơn hàng cho cửa hàng. Hãy xử lý dữ liệu đơn hàng theo từng bước nội bộ: kiểm tra dữ liệu bắt buộc, kiểm tra tính hợp lệ, so sánh số lượng đặt với tồn kho, rồi xác định trạng thái. Không hiển thị suy luận nội bộ; chỉ trả về kết quả cuối cùng theo JSON.

Các trường bắt buộc: order_id, customer_name, phone, address, items, inventory. Mỗi sản phẩm đặt phải có product_id và quantity là số nguyên dương. Tồn kho phải có product_id và available là số nguyên không âm.

Quy tắc:
- Nếu thiếu trường bắt buộc hoặc thiếu thông tin cần thiết để kiểm tra, đặt status là NEED_INFO và ghi trường còn thiếu vào errors.
- Nếu quantity hoặc available sai định dạng, hoặc quantity không phải số nguyên dương, đặt status là INVALID.
- Nếu số lượng tồn kho thấp hơn số lượng đặt của bất kỳ sản phẩm nào, đặt status là OUT_OF_STOCK và ghi sản phẩm thiếu hàng.
- Chỉ đặt status là READY khi tất cả dữ liệu hợp lệ và tồn kho đủ.
- Không tự sửa, suy đoán hoặc thêm dữ liệu.
- Chỉ trả về một JSON object hợp lệ, không thêm lời chào, Markdown hay giải thích.

Cấu trúc đầu ra:
{"order_id":"...","status":"READY|NEED_INFO|OUT_OF_STOCK|INVALID","errors":[],"steps":[{"step":"input_check","result":"..."},{"step":"stock_check","result":"..."},{"step":"decision","result":"..."}],"note":"..."}

Nếu chuỗi xử lý bị gián đoạn hoặc thiếu kết quả của một bước, không tự đưa đơn sang READY. Trả status NEED_INFO, ghi bước bị gián đoạn vào errors và nêu ngắn gọn trong note.

Dữ liệu đơn hàng cần xử lý:
{{ORDER_DATA}}

Kết quả chạy thử

Input:
{"order_id":"DH1024","customer_name":"Lê Minh Anh","phone":"0901234567","address":"12 Nguyễn Trãi, Hà Nội","items":[{"product_id":"SP01","quantity":2},{"product_id":"SP02","quantity":1}],"inventory":[{"product_id":"SP01","available":5},{"product_id":"SP02","available":0}]}

Output:
{"order_id":"DH1024","status":"OUT_OF_STOCK","errors":["SP02 đặt 1 sản phẩm nhưng tồn kho còn 0"],"steps":[{"step":"input_check","result":"Đủ trường bắt buộc"},{"step":"stock_check","result":"SP01 đủ hàng; SP02 thiếu hàng"},{"step":"decision","result":"Chưa chuyển đơn sang đóng gói"}],"note":"Cần bổ sung tồn kho SP02 hoặc điều chỉnh đơn hàng."}
