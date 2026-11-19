Vấn đề

Cần xây dựng quy trình Prompt Chaining để AI vừa giải thích kiến thức theo phương pháp Feynman, vừa chấm bài tự động theo rubric. Các bước phải chạy tuần tự, truyền dữ liệu chính xác và xử lý được dữ liệu thiếu hoặc sai định dạng mà không làm gián đoạn hệ thống.

Yêu cầu

- Thiết kế chuỗi prompt liên kết từ kiểm tra dữ liệu đến giải thích, chấm điểm và tổng hợp kết quả.
- Mỗi bước có nhiệm vụ và đầu ra rõ ràng để chuyển sang bước tiếp theo.
- Tối ưu token, tránh lặp lại thông tin không cần thiết.
- Có cơ chế báo lỗi khi dữ liệu thiếu, sai định dạng hoặc mâu thuẫn.
- Báo cáo gồm thiết kế giải pháp, prompt từng bước và kết quả chạy thử.

Cách làm

1. Thiết kế giải pháp

Chuỗi xử lý gồm 4 bước:
- Bước 1 – Kiểm tra dữ liệu: kiểm tra chủ đề, trình độ, bài làm và rubric.
- Bước 2 – Gia sư Feynman: giải thích kiến thức đơn giản, đưa ví dụ và câu hỏi kiểm tra.
- Bước 3 – Chấm bài: đánh giá bài làm theo từng tiêu chí trong rubric.
- Bước 4 – Tổng hợp: ghép kết quả, kiểm tra điểm số và xuất báo cáo cuối cùng.

Nếu bước 1 phát hiện dữ liệu bắt buộc bị thiếu hoặc không hợp lệ, hệ thống dừng xử lý và yêu cầu bổ sung. Các bước sau chỉ nhận dữ liệu đã được kiểm tra.

2. Prompt thực thi các bước

Prompt hệ thống:

Bạn là hệ thống hỗ trợ học tập gồm gia sư Feynman và công cụ chấm bài. Làm việc theo đúng thứ tự các bước. Chỉ sử dụng dữ liệu đầu vào, không tự bịa thông tin. Trả kết quả ngắn gọn, đúng cấu trúc. Nếu phát hiện dữ liệu thiếu, sai định dạng hoặc mâu thuẫn, hãy báo rõ lỗi và không tiếp tục bước phụ thuộc vào dữ liệu đó.

Prompt bước 1 – Kiểm tra dữ liệu:

Kiểm tra các trường: chủ đề, trình độ, bài làm, rubric và thang điểm. Xác định trường nào bị thiếu, sai định dạng hoặc mâu thuẫn. Nếu thiếu chủ đề, bài làm hoặc rubric, trả về trạng thái NEED_MORE_DATA và liệt kê thông tin cần bổ sung. Nếu hợp lệ, trả về trạng thái VALID cùng dữ liệu đã chuẩn hóa.

Prompt bước 2 – Gia sư Feynman:

Dựa trên chủ đề và trình độ đã được xác nhận, hãy giải thích bằng ngôn ngữ đơn giản, đưa một ví dụ gần gũi và đặt 2 câu hỏi kiểm tra. Không tự thêm nội dung ngoài phạm vi chủ đề.

Prompt bước 3 – Chấm bài:

Dựa trên bài làm và rubric đã được xác nhận, chấm riêng từng tiêu chí. Với mỗi tiêu chí, ghi điểm tối đa, điểm đạt và lý do. Không vượt điểm tối đa. Không tự thêm tiêu chí hoặc thay đổi thang điểm.

Prompt bước 4 – Tổng hợp:

Tổng hợp phần giải thích, ví dụ, câu hỏi và kết quả chấm. Kiểm tra tổng điểm bằng tổng điểm các tiêu chí và không vượt tổng điểm tối đa. Nếu phát hiện sai lệch, ghi rõ lỗi thay vì tự sửa dữ liệu gốc. Xuất báo cáo gồm: Giải thích Feynman, câu hỏi kiểm tra, bảng điểm, tổng điểm và nhận xét.

3. Kết quả chạy thử

Input:
- Chủ đề: Vòng lặp for trong Python.
- Trình độ: Người mới học lập trình.
- Bài làm: “Vòng lặp for dùng để lặp lại một công việc nhiều lần.”
- Rubric: Đúng kiến thức 4 điểm; giải thích rõ ràng 3 điểm; có ví dụ 3 điểm.

Bước 1 – Kiểm tra dữ liệu:
Dữ liệu hợp lệ, đủ thông tin để xử lý.

Bước 2 – Gia sư Feynman:
Vòng lặp for giúp chương trình thực hiện một nhóm lệnh nhiều lần, thường là lần lượt với từng phần tử trong danh sách.
Ví dụ: for i in range(3): print("Xin chào") sẽ in lời chào 3 lần.
Câu hỏi: Vòng lặp for dùng để làm gì? range(3) lặp bao nhiêu lần?

Bước 3 – Chấm bài:
- Đúng kiến thức: 3/4 – Nêu đúng công dụng nhưng chưa giải thích cách hoạt động.
- Giải thích rõ ràng: 2/3 – Nội dung dễ hiểu nhưng còn ngắn.
- Có ví dụ: 0/3 – Chưa có ví dụ trong bài làm.

Bước 4 – Tổng hợp:
Tổng điểm: 5/10.
Nhận xét: Bài làm đã nêu được ý chính. Cần giải thích rõ hơn cách vòng lặp hoạt động và bổ sung ví dụ cụ thể.

4. Cơ chế xử lý lỗi

- Thiếu dữ liệu bắt buộc: dừng chuỗi và yêu cầu nhập bổ sung.
- Điểm rubric không phải số hoặc nhỏ hơn 0: báo lỗi, không chấm.
- Điểm đạt vượt điểm tối đa: đánh dấu kết quả không hợp lệ.
- Dữ liệu mâu thuẫn: yêu cầu người dùng xác nhận.
- Nội dung quá dài: chỉ tóm tắt phần cần thiết, không làm mất tiêu chí chấm.

Kết luận: Prompt Chaining giúp chia bài toán lớn thành các bước nhỏ, dễ kiểm soát và tái sử dụng. Việc kiểm tra dữ liệu trước khi xử lý giúp hạn chế lỗi và tạo kết quả nhất quán.
