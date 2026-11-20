# Xử lý tài liệu nhân sự nhiều chương bằng AI khi giới hạn Context Window

## 1. Vấn đề

Tài liệu nội bộ của ABC Technology có nhiều chương và tối thiểu 50 trang, vượt khả năng xử lý trong một lần do giới hạn Context Window. Cần chia tài liệu thành các phần logic, xử lý riêng từng chương, lưu kết quả và tổng hợp mà không tự suy đoán hoặc làm sai lệch số liệu, thời hạn, điều kiện và ngoại lệ.

Lưu ý: Chưa có file PDF/DOCX gốc được cung cấp, vì vậy chưa thể tạo bảng quy định thực tế, bản tóm tắt 1.000–1.500 từ hoặc câu hỏi có đáp án và số trang xác thực. Các Prompt dưới đây dùng để thực hiện khi có tài liệu.

## 2. Yêu cầu

- Chia tài liệu theo chương và các mục nội dung logic.
- Tóm tắt từng phần theo một cấu trúc thống nhất và lưu lại kết quả.
- Giữ nguyên số liệu, thời hạn, tỷ lệ, điều kiện và trường hợp ngoại lệ.
- Chỉ sử dụng thông tin có trong tài liệu; đánh dấu rõ nội dung chưa được đề cập.
- Tổng hợp các chương, tìm nội dung liên quan và kiểm tra thiếu sót.
- Đầu ra gồm hai Prompt, bảng tổng hợp, bản tóm tắt 1.000–1.500 từ và ít nhất 5 câu hỏi kèm đáp án, vị trí trích dẫn.

## 3. Cách làm

### Prompt 1 – Xử lý từng phần tài liệu

```text
Bạn là trợ lý phân tích tài liệu nhân sự. Hãy xử lý riêng phần tài liệu tôi cung cấp. Chỉ sử dụng nội dung trong phần này, không suy đoán hoặc bổ sung quy định từ bên ngoài.

YÊU CẦU:
1. Xác định tên chương, mục, tiểu mục và phạm vi trang.
2. Tóm tắt nội dung theo các chủ đề:
   - Nội quy lao động.
   - Nghỉ phép.
   - Làm thêm giờ.
   - Đánh giá nhân viên.
   - Khen thưởng và kỷ luật.
3. Ghi chính xác mọi con số, tỷ lệ, thời hạn, đối tượng, điều kiện và quy trình.
4. Ghi riêng tất cả trường hợp ngoại lệ, điều kiện loại trừ và lưu ý.
5. Nếu nội dung không xuất hiện, ghi "Tài liệu chưa đề cập"; không tự điền.
6. Với mỗi thông tin quan trọng, ghi số trang hoặc tên mục để truy xuất.
7. Nếu nội dung mơ hồ hoặc mâu thuẫn, đánh dấu để kiểm tra, không tự kết luận.

ĐỊNH DẠNG KẾT QUẢ:
- Tên chương/phần và phạm vi trang.
- Bảng gồm: Chủ đề | Quy định chính | Điều kiện áp dụng | Ngoại lệ | Vị trí trong tài liệu.
- Các con số, thời hạn và tỷ lệ cần giữ nguyên.
- Nội dung chưa được đề cập hoặc cần xác minh.
- Danh sách thông tin quan trọng để lưu vào bản tổng hợp.

Không được bỏ qua ngoại lệ. Không thay đổi ý nghĩa câu chữ của quy định.
```

Lưu kết quả của từng chương thành các bản ghi riêng, ví dụ: Tomtat_Chuong1, Tomtat_Chuong2... và kiểm tra lại với tài liệu gốc trước khi chuyển sang bước tổng hợp.

### Prompt 2 – Tổng hợp và kiểm tra

```text
Bạn là trợ lý tổng hợp tài liệu nhân sự. Hãy sử dụng các bản tóm tắt từng chương tôi cung cấp để tạo tài liệu tổng hợp.

NGUYÊN TẮC:
- Chỉ dùng thông tin có trong các bản tóm tắt và tài liệu gốc đã cung cấp.
- Không suy đoán, không tự tạo quy định.
- Giữ nguyên số liệu, tỷ lệ, thời hạn, điều kiện và ngoại lệ.
- Phân biệt rõ "Có quy định trong tài liệu" và "Tài liệu chưa đề cập".
- Khi thông tin giữa các chương liên quan hoặc có vẻ mâu thuẫn, nêu rõ vị trí để đối chiếu; không tự chọn một nội dung làm kết luận.

ĐẦU RA:

1. BẢNG TỔNG HỢP
| Chủ đề | Quy định chính | Điều kiện áp dụng | Ngoại lệ |
|---|---|---|---|

2. BẢN TÓM TẮT HOÀN CHỈNH
Viết khoảng 1.000–1.500 từ, chia theo chủ đề hoặc chương. Giữ nguyên các thông tin quan trọng và ghi vị trí trang/mục khi có dữ liệu.

3. CÁC NỘI DUNG LIÊN QUAN GIỮA CÁC CHƯƠNG
Nêu các quy định có liên hệ, điểm bổ sung hoặc điểm có khả năng mâu thuẫn. Ghi rõ nguồn và vị trí.

4. CÂU HỎI KIỂM TRA
Tạo ít nhất 5 câu hỏi dựa trên tài liệu gốc. Mỗi câu phải có:
- Câu hỏi.
- Câu trả lời được trích xuất từ tài liệu.
- Chương, mục hoặc số trang làm căn cứ.
Nếu không tìm thấy câu trả lời, ghi "Tài liệu chưa đề cập".

5. KIỂM TRA ĐỘ ĐẦY ĐỦ
Đối chiếu từng chương và chủ đề với bản tổng hợp. Liệt kê:
- Nội dung đã được đưa vào.
- Thông tin hoặc ngoại lệ có nguy cơ bị bỏ sót.
- Nội dung chưa đề cập.
- Điểm cần mở lại tài liệu gốc để xác minh.

Không khẳng định đã kiểm tra tài liệu gốc nếu chỉ nhận được bản tóm tắt. Không tạo số trang hoặc trích dẫn không có căn cứ.
```

### Quy trình thực hiện

1. Tải PDF/DOCX và xác định cấu trúc chương, mục, số trang.
2. Chia theo từng chương hoặc phần logic; không chia cắt giữa một quy định và phần ngoại lệ của nó.
3. Chạy Prompt 1 cho từng phần, lưu riêng kết quả.
4. Cung cấp toàn bộ bản tóm tắt đã lưu cho Prompt 2.
5. Đối chiếu bảng tổng hợp, câu hỏi và các điểm nghi vấn với tài liệu gốc trước khi nộp.
