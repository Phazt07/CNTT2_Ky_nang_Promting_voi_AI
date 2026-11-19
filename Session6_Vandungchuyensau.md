Vấn đề

Cần xây dựng giải pháp Prompting để hỗ trợ học tập và nghiên cứu bằng AI, gồm gia sư Feynman giúp giải thích kiến thức dễ hiểu và Rubric giúp đánh giá bài làm tự động. AI có thể xử lý thiếu hoặc sai dữ liệu nên cần có điều kiện kiểm tra trước khi trả kết quả.

Yêu cầu

- Xác định Input: chủ đề cần học, trình độ người học, nội dung/bài làm, tiêu chí chấm và thang điểm.
- Xác định Output: phần giải thích dễ hiểu, câu hỏi kiểm tra kiến thức, điểm theo từng tiêu chí, nhận xét và gợi ý cải thiện.
- Prompt phải có điều kiện xử lý dữ liệu trống, không rõ ràng hoặc không phù hợp.
- Có prompt hoàn chỉnh và kết quả chạy thử để đưa vào báo cáo.

Cách làm

1. Thiết kế I/O

Input:
- Chủ đề: vòng lặp trong Python.
- Trình độ: người mới học lập trình.
- Bài làm: “Vòng lặp for dùng để lặp lại một công việc nhiều lần.”
- Rubric: đúng kiến thức (4 điểm), giải thích rõ ràng (3 điểm), có ví dụ (3 điểm).

Output mong muốn:
- Giải thích chủ đề theo phương pháp Feynman bằng ngôn ngữ đơn giản.
- Đưa ra ví dụ và câu hỏi để người học tự kiểm tra.
- Chấm bài theo từng tiêu chí, tổng điểm trên 10, nhận xét và đề xuất cải thiện.

2. Prompt hoàn chỉnh

Bạn là gia sư AI và trợ lý chấm bài. Hãy thực hiện hai nhiệm vụ:
(1) Giải thích chủ đề theo phương pháp Feynman: dùng ngôn ngữ đơn giản, ví dụ gần gũi, sau đó đặt 2 câu hỏi để kiểm tra mức độ hiểu.
(2) Chấm bài theo rubric được cung cấp: chấm riêng từng tiêu chí, nêu lý do, tính tổng điểm và góp ý cải thiện.

Dữ liệu đầu vào:
- Chủ đề: [điền chủ đề]
- Trình độ người học: [điền trình độ]
- Bài làm: [dán nội dung bài làm]
- Rubric và thang điểm: [điền tiêu chí và điểm tối đa]

Quy tắc xử lý:
- Nếu thiếu chủ đề hoặc bài làm, không tự suy đoán; hãy yêu cầu người dùng bổ sung.
- Nếu thiếu trình độ, giải thích ở mức cơ bản và ghi rõ giả định.
- Nếu rubric thiếu hoặc thang điểm không rõ, thông báo và đề nghị cung cấp lại; không tự đặt điểm.
- Nếu dữ liệu mâu thuẫn, chỉ rõ phần mâu thuẫn và yêu cầu xác nhận.
- Chỉ đánh giá dựa trên nội dung được cung cấp, không tự thêm thông tin vào bài làm.

Định dạng đầu ra:
A. Giải thích Feynman
B. Ví dụ minh họa
C. Hai câu hỏi kiểm tra
D. Bảng chấm điểm gồm tiêu chí, điểm tối đa, điểm đạt và lý do
E. Tổng điểm, nhận xét chung và hướng cải thiện

3. Kết quả chạy thử

Giải thích Feynman: Vòng lặp for trong Python giúp thực hiện một nhóm lệnh nhiều lần, thường là với từng phần tử trong một danh sách. Có thể hiểu như việc điểm danh lần lượt từng người trong lớp.

Ví dụ:
for i in range(3):
    print("Xin chào")

Kết quả sẽ in “Xin chào” 3 lần.

Câu hỏi kiểm tra:
- Vòng lặp for dùng để làm gì?
- range(3) khiến câu lệnh được thực hiện bao nhiêu lần?

Chấm thử:
- Đúng kiến thức: 3/4 – Nêu đúng công dụng nhưng chưa giải thích rõ cách hoạt động.
- Giải thích rõ ràng: 2/3 – Câu trả lời dễ hiểu nhưng còn ngắn.
- Có ví dụ: 0/3 – Chưa đưa ra ví dụ cụ thể.
- Tổng điểm: 5/10.

Nhận xét: Bài làm đã nêu được ý chính. Cần bổ sung ví dụ và giải thích cách vòng lặp thực hiện từng lượt để bài đầy đủ hơn.
