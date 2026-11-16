Session3_ExBaithuchanh1

Vấn đề

HR nhận được nhiều email ứng tuyển viết theo nhiều cách khác nhau. Việc đọc và nhập thông tin ứng viên vào hệ thống mất thời gian và dễ sai sót.

Yêu cầu

Tạo một prompt để AI đọc email ứng tuyển và lấy ra các thông tin sau: họ tên, số điện thoại, email, vị trí ứng tuyển, số năm kinh nghiệm và kỹ năng chính.

Kết quả cần có bảng Markdown tóm tắt và một mảng JSON để nhập vào database. Họ tên cần viết hoa chữ cái đầu, số điện thoại cần được chuẩn hóa, kỹ năng không được lặp lại. Không tự thêm thông tin. Nếu email không có thông tin nào thì ghi null.

Cách làm

Dùng prompt sau:

Bạn là nhân viên xử lý dữ liệu nhân sự. Đọc email ứng tuyển và tìm họ tên, số điện thoại, email, vị trí ứng tuyển, số năm kinh nghiệm và kỹ năng chính.

Viết họ tên theo cách thông thường, chuẩn hóa số điện thoại và liệt kê kỹ năng thành danh sách không trùng. Không đoán hoặc tự thêm thông tin. Thông tin nào không có trong email thì ghi null. experience_years là số hoặc null.

Chỉ trả về bảng Markdown và mảng JSON theo mẫu sau, không viết giải thích:
[{"name":"...","phone":"...","email":"...","position":"...","experience_years":2,"skills":["Python","SQL"]}]

Ví dụ 1
Email: Chào HR, mình là NGUYỄN VĂN AN, ứng tuyển Backend Intern. Mình có 1 năm làm dự án với Python, SQL và Python. Số điện thoại 0901 234 567, email an@example.com.
Kết quả: Nguyễn Văn An; +84901234567; an@example.com; Backend Intern; 1 năm; Python, SQL.
JSON: [{"name":"Nguyễn Văn An","phone":"+84901234567","email":"an@example.com","position":"Backend Intern","experience_years":1,"skills":["Python","SQL"]}]

Ví dụ 2
Email: Em là Trần Thị Bình, muốn ứng tuyển Data Analyst. Em sử dụng Excel và Power BI.
Kết quả: Trần Thị Bình; số điện thoại null; email null; Data Analyst; kinh nghiệm null; Excel, Power BI.
JSON: [{"name":"Trần Thị Bình","phone":null,"email":null,"position":"Data Analyst","experience_years":null,"skills":["Excel","Power BI"]}]

Email cần xử lý:
{{EMAIL_UNG_TUYEN}}

Kiểm tra JSON bằng công cụ Validate JSON trước khi nhập vào database.
