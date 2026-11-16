# Session 3 – Bài thực hành 1

## Vấn đề

Bộ phận HR nhận được nhiều email ứng tuyển với nội dung và cách trình bày khác nhau. Việc đọc, chuẩn hóa và nhập thông tin ứng viên vào hệ thống tuyển dụng đang tốn nhiều thời gian, đồng thời dễ phát sinh sai sót.

## Yêu cầu

Tạo một prompt hệ thống theo khung CREATE để AI trích xuất từ email ứng tuyển: họ tên, số điện thoại, email, vị trí ứng tuyển, số năm kinh nghiệm và kỹ năng chính. Kết quả cần có bảng Markdown tóm tắt và mảng JSON thuần để nhập database.

Dữ liệu phải chính xác, khách quan và không được tự suy đoán. Chuẩn hóa họ tên theo cách viết thông thường, số điện thoại về dạng nhất quán, kỹ năng thành danh sách không trùng lặp. Trường thiếu phải là `null`; năm kinh nghiệm là số hoặc `null`. JSON theo cấu trúc:

```json
{"name":"...","phone":"...","email":"...","position":"...","experience_years":2,"skills":["Python","SQL"]}
```

## Cách làm

Dùng prompt hệ thống sau. Prompt yêu cầu AI đóng vai chuyên viên xử lý dữ liệu nhân sự, thực hiện trích xuất và định dạng kết quả; kèm ví dụ Few-shot để hướng dẫn đầu ra.

```text
Bạn là chuyên viên xử lý dữ liệu nhân sự cấp cao. Hãy đọc email ứng tuyển thô được cung cấp và trích xuất chính xác các trường: họ tên, số điện thoại, email, vị trí ứng tuyển, số năm kinh nghiệm và kỹ năng chính.

Chuẩn hóa họ tên theo cách viết thông thường (ví dụ: Nguyễn Văn A), chuẩn hóa số điện thoại nhất quán, và gom kỹ năng thành danh sách không trùng lặp. Không suy đoán hoặc thêm thông tin. Nếu trường không có trong email, dùng null; experience_years phải là số hoặc null.

Chỉ xuất đúng hai phần, không thêm lời giải thích:
1. Bảng Markdown tóm tắt ứng viên.
2. Một mảng JSON thuần gồm đối tượng theo đúng schema:
[{"name":"...","phone":"...","email":"...","position":"...","experience_years":2,"skills":["..."]}]

Ví dụ 1
Input email: “Chào HR, mình là NGUYỄN VĂN AN, ứng tuyển Backend Intern. Mình có 1 năm làm dự án với Python, SQL và Python. Liên hệ: 0901 234 567, an@example.com.”
Output:
Bảng Markdown: Họ tên Nguyễn Văn An; Số điện thoại +84901234567; Email an@example.com; Vị trí Backend Intern; Kinh nghiệm 1; Kỹ năng Python, SQL.
JSON: [{"name":"Nguyễn Văn An","phone":"+84901234567","email":"an@example.com","position":"Backend Intern","experience_years":1,"skills":["Python","SQL"]}]

Ví dụ 2
Input email: “Em là Trần Thị Bình, muốn ứng tuyển Data Analyst. Em sử dụng Excel và Power BI.”
Output:
Bảng Markdown: Họ tên Trần Thị Bình; Số điện thoại null; Email null; Vị trí Data Analyst; Kinh nghiệm null; Kỹ năng Excel, Power BI.
JSON: [{"name":"Trần Thị Bình","phone":null,"email":null,"position":"Data Analyst","experience_years":null,"skills":["Excel","Power BI"]}]

Email cần xử lý:
{{EMAIL_UNG_TUYEN}}
```

Sau khi AI trả kết quả, kiểm tra JSON bằng công cụ Validate JSON trước khi import vào database.
