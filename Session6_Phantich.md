Vấn đề

Cần tối ưu quy trình gia sư Feynman và chấm bài tự động bằng AI. Có hai cách viết prompt: prompt ngắn, dễ dùng và prompt chi tiết, có nhiều điều kiện kiểm soát. Cần so sánh để chọn cách phù hợp.

Yêu cầu

- Viết hai prompt mẫu: một đơn giản và một chi tiết.
- So sánh hai giải pháp theo độ dễ hiểu, lượng token và khả năng xử lý lỗi.
- Chọn giải pháp tối ưu, giải thích lý do và chạy thử.
- Có báo cáo so sánh, prompt được chọn và kết quả thử nghiệm.

Cách làm

1. Đề xuất hai prompt mẫu

Giải pháp 1 – Prompt đơn giản:

Bạn là gia sư AI. Hãy giải thích chủ đề [chủ đề] theo phương pháp Feynman bằng ngôn ngữ dễ hiểu, có ví dụ minh họa và 2 câu hỏi kiểm tra. Sau đó, chấm bài làm [nội dung bài làm] theo rubric [tiêu chí chấm], nêu điểm số và góp ý cải thiện.

Giải pháp 2 – Prompt chi tiết:

Bạn là gia sư AI và trợ lý chấm bài. Hãy thực hiện:
- Giải thích [chủ đề] theo phương pháp Feynman, phù hợp với trình độ [trình độ].
- Dùng ví dụ gần gũi, sau đó đưa ra 2 câu hỏi kiểm tra mức độ hiểu.
- Chấm bài làm [nội dung bài làm] theo rubric [tiêu chí và thang điểm].
- Chấm riêng từng tiêu chí, nêu lý do, tính tổng điểm và đưa ra góp ý.

Điều kiện xử lý:
- Nếu thiếu chủ đề hoặc bài làm, yêu cầu người dùng bổ sung, không tự suy đoán.
- Nếu thiếu trình độ, mặc định giải thích ở mức cơ bản và thông báo giả định.
- Nếu rubric hoặc thang điểm không rõ, yêu cầu cung cấp lại, không tự đặt tiêu chí.
- Nếu dữ liệu mâu thuẫn hoặc không liên quan, chỉ rõ vấn đề trước khi xử lý.
- Chỉ sử dụng thông tin được cung cấp, không bịa nội dung.

Định dạng kết quả:
A. Giải thích Feynman
B. Ví dụ minh họa
C. Hai câu hỏi kiểm tra
D. Bảng chấm điểm theo từng tiêu chí
E. Tổng điểm, nhận xét và hướng cải thiện

2. So sánh Trade-off

Tiêu chí | Giải pháp 1 (Đơn giản) | Giải pháp 2 (Chi tiết)
Độ dễ hiểu | Cao, dễ viết và sử dụng | Trung bình, nhiều yêu cầu hơn
Tốn token | Ít | Nhiều hơn
Chặn lỗi biên | Trung bình, ít điều kiện xử lý | Tốt, có quy tắc cho dữ liệu thiếu hoặc sai
Độ nhất quán đầu ra | Có thể thay đổi tùy phản hồi | Cao hơn nhờ định dạng cụ thể
Khả năng tùy chỉnh | Cơ bản | Linh hoạt hơn

3. Lựa chọn và chạy thử

Chọn giải pháp 2 vì tuy tốn nhiều token hơn nhưng kiểm soát dữ liệu đầu vào tốt, hạn chế AI tự suy đoán và tạo kết quả có cấu trúc rõ ràng. Giải pháp này phù hợp hơn khi vừa cần hướng dẫn học tập vừa cần chấm bài theo tiêu chí.

Prompt được chọn: Giải pháp 2 – Prompt chi tiết.

Kết quả chạy thử:

Input:
- Chủ đề: Vòng lặp for trong Python.
- Trình độ: Người mới học lập trình.
- Bài làm: “Vòng lặp for dùng để lặp lại một công việc nhiều lần.”
- Rubric: Đúng kiến thức 4 điểm; giải thích rõ ràng 3 điểm; có ví dụ 3 điểm.

Output:
- Giải thích: Vòng lặp for giúp chương trình thực hiện một nhóm lệnh nhiều lần, thường là lần lượt với từng phần tử trong danh sách.
- Ví dụ: for i in range(3): print("Xin chào") sẽ in lời chào 3 lần.
- Câu hỏi kiểm tra: Vòng lặp for dùng để làm gì? range(3) lặp bao nhiêu lần?
- Chấm điểm:
  + Đúng kiến thức: 3/4 – Nêu đúng công dụng nhưng chưa giải thích cách hoạt động.
  + Giải thích rõ ràng: 2/3 – Nội dung dễ hiểu nhưng còn ngắn.
  + Có ví dụ: 0/3 – Bài làm chưa có ví dụ.
- Tổng điểm: 5/10.
- Nhận xét: Bài làm đã nêu được ý chính, cần bổ sung ví dụ và giải thích rõ hơn cách vòng lặp hoạt động.
