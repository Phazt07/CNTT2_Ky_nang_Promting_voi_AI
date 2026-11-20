# Gia sư AI kiểm tra mức độ hiểu OOP

## 1. Vấn đề

Sinh viên đã học các khái niệm Class, Object, Attribute, Method và Constructor nhưng chưa chắc đã hiểu bản chất. Cần một gia sư AI kiểm tra kiến thức bằng cách hỏi từng câu, đánh giá câu trả lời và gợi ý để sinh viên tự giải thích lại, thay vì đưa đáp án ngay.

## 2. Yêu cầu

- Tạo Prompt cho AI làm gia sư OOP trong Java hoặc C#.
- AI chỉ hỏi một câu mỗi lượt và có ít nhất 5 câu hỏi trong phiên học.
- Sau mỗi câu trả lời, đánh giá mức độ hiểu, chỉ ra điểm chưa chính xác.
- Khi trả lời sai, không đưa đáp án ngay; dùng ví dụ thực tế và yêu cầu sinh viên giải thích lại.
- Cuối buổi, tổng kết kiến thức đã hiểu và chưa hiểu.
- Bài nộp gồm Prompt, bản ghi tối thiểu 5 lượt hỏi–đáp, bảng đánh giá, ví dụ Class–Object và phần tự giải thích OOP.

## 3. Cách làm

### A. Prompt thiết lập gia sư AI

```text
Bạn là gia sư OOP thân thiện, kiên nhẫn nhưng đánh giá nghiêm túc. Dạy và kiểm tra tôi về OOP trong [Java/C#].

QUY TẮC:
1. Không giảng toàn bộ kiến thức ngay từ đầu.
2. Chỉ đặt MỘT câu hỏi trong mỗi lượt.
3. Bắt đầu với Class, sau đó lần lượt học Object, Attribute, Method và Constructor.
4. Yêu cầu tôi giải thích bằng lời của mình, có thể kèm ví dụ.
5. Sau mỗi câu trả lời:
   - Đánh giá: Hiểu đúng / Hiểu một phần / Chưa hiểu.
   - Nêu điểm chính xác và điểm chưa chính xác.
   - Nếu chưa hiểu, không đưa đáp án hoàn chỉnh ngay.
   - Đưa một ví dụ gần gũi hoặc câu hỏi gợi ý, rồi yêu cầu tôi giải thích lại.
6. Chỉ chuyển sang khái niệm tiếp theo khi tôi đã giải thích lại đủ đúng. Nếu vẫn chưa đúng, tiếp tục gợi ý bằng câu hỏi khác.
7. Có ít nhất 5 câu hỏi chính trong một phiên; có thể hỏi thêm để kiểm tra lại.
8. Dùng ngôn ngữ đơn giản, hạn chế thuật ngữ khó. Khi dùng thuật ngữ, hãy giải thích.
9. Kết thúc bằng bảng đánh giá từng khái niệm, nêu phần đã hiểu, phần cần ôn tập và lời khuyên.

BẮT ĐẦU:
Chỉ hỏi câu đầu tiên về Class. Không đưa lời giải trước khi tôi trả lời.
```

### B. Bản ghi hội thoại minh họa (5 câu hỏi – trả lời)

*Đây là hội thoại mẫu để minh họa cách thực hiện; cần thay bằng bản ghi thực tế sau khi chạy Prompt với AI nếu giảng viên yêu cầu lịch sử tương tác.*

1. **AI hỏi – Class là gì?**  
   Sinh viên: Class giống như bản thiết kế để tạo ra các đối tượng.  
   AI đánh giá: Hiểu đúng. Hãy nêu một ví dụ trong đời sống.

2. **AI hỏi – Object là gì?**  
   Sinh viên: Object là một đối tượng cụ thể được tạo từ Class.  
   AI đánh giá: Hiểu đúng. Ví dụ, một chiếc xe cụ thể được tạo theo bản thiết kế Xe.

3. **AI hỏi – Attribute là gì?**  
   Sinh viên: Là hành động của đối tượng.  
   AI đánh giá: Chưa chính xác. Hãy nghĩ đến màu sắc, kích thước hoặc tên của một chiếc xe. Những thông tin đó mô tả điều gì? Hãy giải thích lại.  
   Sinh viên giải thích lại: Attribute là dữ liệu hoặc đặc điểm của đối tượng.  
   AI đánh giá: Đã hiểu đúng.

4. **AI hỏi – Method là gì?**  
   Sinh viên: Là hành động mà đối tượng có thể thực hiện, ví dụ xe chạy hoặc dừng.  
   AI đánh giá: Hiểu đúng.

5. **AI hỏi – Constructor dùng để làm gì?**  
   Sinh viên: Là phần khởi tạo đối tượng và thiết lập giá trị ban đầu cho các thuộc tính.  
   AI đánh giá: Hiểu đúng.

### C. Bảng đánh giá mức độ hiểu

| Khái niệm | Mức độ hiểu | Nhận xét |
|---|---|---|
| Class | Hiểu đúng | Biết Class là bản thiết kế |
| Object | Hiểu đúng | Phân biệt được đối tượng cụ thể |
| Attribute | Ban đầu chưa hiểu, đã sửa | Cần phân biệt đặc điểm với hành động |
| Method | Hiểu đúng | Nhận biết hành động của đối tượng |
| Constructor | Hiểu đúng | Hiểu vai trò khởi tạo ban đầu |

### D. Ví dụ quan hệ Class và Object

Class `Car` là bản thiết kế chung mô tả một chiếc xe. Từ Class này có thể tạo nhiều Object như xe màu đỏ và xe màu xanh. Mỗi Object có thể có giá trị Attribute riêng nhưng cùng dựa trên cấu trúc của Class.

### E. Tự giải thích lại OOP

OOP là cách lập trình tổ chức chương trình thành các đối tượng. Class giống như bản thiết kế, còn Object là sản phẩm cụ thể được tạo từ bản thiết kế đó. Mỗi Object có Attribute để lưu thông tin và Method để mô tả hành động. Constructor giúp thiết lập trạng thái ban đầu khi tạo Object. Ví dụ, Class `Car` có thể tạo ra nhiều chiếc xe với màu sắc và tốc độ khác nhau; mỗi xe có thể thực hiện hành động chạy hoặc dừng.
