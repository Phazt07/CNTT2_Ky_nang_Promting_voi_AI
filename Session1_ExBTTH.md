# Session 1 – Bài tập tổng hợp

## 1. Vấn đề

Tân sinh viên thường dùng AI để học lập trình nhưng có thể hiểu sai cách AI tạo câu trả lời, tin vào thông tin bịa (ảo giác), hoặc viết prompt quá chung chung. Cần một cẩm nang ngắn giúp sử dụng AI an toàn và hiệu quả.

## 2. Yêu cầu

Tạo cẩm nang gồm ba nội dung: (1) LLM đoán từ như thế nào; (2) ba cách nhận diện ảo giác; (3) mẫu prompt theo khung CREATE. Dùng **Prompt Chaining**: chia yêu cầu thành các prompt nối tiếp, đầu ra mỗi bước làm đầu vào bước sau. Kiểm soát độ dài bằng cách yêu cầu nội dung súc tích; kiểm chứng thông tin thay vì xem câu trả lời AI là sự thật.

## 3. Cách làm

### Sơ đồ xâu chuỗi prompt

`Yêu cầu tổng quát → Prompt 1: giải thích LLM → Prompt 2: nêu 3 cách phát hiện ảo giác → Prompt 3: tạo prompt CREATE → Prompt 4: biên tập, kiểm tra và ghép thành cẩm nang`

### Các prompt thành phần

1. **Prompt 1:** “Giải thích ngắn cho tân sinh viên: mô hình ngôn ngữ lớn (LLM) tạo câu trả lời bằng cách dự đoán token tiếp theo dựa trên ngữ cảnh như thế nào? Nêu một ví dụ đơn giản; tránh mô tả AI như người có hiểu biết hoặc ý thức.”
2. **Prompt 2 (dùng kết quả Prompt 1):** “Dựa trên phần giải thích trên, nêu đúng 3 cách sinh viên kiểm tra câu trả lời AI khi học lập trình. Mỗi cách gồm một hành động cụ thể; nhấn mạnh chạy thử mã và đối chiếu tài liệu đáng tin cậy.”
3. **Prompt 3 (dùng các đầu ra trước):** “Soạn một prompt mẫu theo CREATE cho bài tập lập trình. Ghi rõ từng thành phần: **C**ontext (bối cảnh), **R**ole (vai trò), **E**xpectation (kết quả mong muốn), **A**udience (người đọc), **T**one (giọng điệu), **E**xtras (ràng buộc/yêu cầu thêm).”
4. **Prompt 4:** “Ghép và biên tập các nội dung trên thành cẩm nang ngắn cho tân sinh viên. Dùng tiếng Việt dễ hiểu, tiêu đề rõ, giữ đủ ba chủ đề; kiểm tra tính chính xác, bỏ ý lặp và giới hạn độ dài.”

### Cẩm nang: Học lập trình cùng AI an toàn và hiệu quả

#### 1. LLM đoán từ như thế nào?

LLM chia văn bản thành các đơn vị nhỏ gọi là **token**, rồi dự đoán token nào có khả năng theo sau dựa trên những token trước đó. Ví dụ, sau câu “Python dùng `print` để…”, mô hình có thể dự đoán “hiển thị”. Câu trả lời được tạo từng bước như vậy; trôi chảy không đồng nghĩa luôn đúng. Mô hình cũng có giới hạn về lượng ngữ cảnh (token) xử lý, nên hãy đưa yêu cầu và đoạn mã liên quan, tránh gửi thông tin thừa hoặc nhạy cảm.

#### 2. Ba cách nhận diện ảo giác

1. **Kiểm tra nguồn:** tra tên hàm, thư viện và quy tắc trong tài liệu chính thức; cảnh giác với trích dẫn hoặc đường dẫn không tìm thấy.
2. **Chạy thử và kiểm thử:** thực thi mã trong môi trường an toàn, thử cả trường hợp biên và so sánh kết quả với điều mong đợi.
3. **Hỏi lại và đối chiếu:** yêu cầu AI giải thích từng bước, nêu giả định; so sánh với giáo trình, giảng viên hoặc nguồn độc lập đáng tin cậy. Đừng coi sự tự tin trong câu trả lời là bằng chứng.

#### 3. Prompt mẫu theo CREATE

- **C – Context:** Tôi đang học Python cơ bản và làm bài tính trung bình danh sách số.
- **R – Role:** Hãy đóng vai trợ giảng lập trình kiên nhẫn.
- **E – Expectation:** Giải thích cách tiếp cận rồi gợi ý từng bước; chưa đưa lời giải hoàn chỉnh ngay.
- **A – Audience:** Sinh viên mới học, chưa biết nhiều về hàm.
- **T – Tone:** Dễ hiểu, thân thiện, chính xác.
- **E – Extras:** Dùng Python 3; nêu một ví dụ nhỏ, chỉ ra trường hợp danh sách rỗng và nhắc tôi tự chạy kiểm thử. Nếu thiếu thông tin, hãy hỏi lại; không bịa kết quả.

**Mẹo:** Prompt càng rõ về bối cảnh, đầu ra và giới hạn thì câu trả lời càng hữu ích. Hãy dùng AI như trợ giảng để học và kiểm tra, không thay thế việc tự hiểu, tự chạy mã và xác minh thông tin.
