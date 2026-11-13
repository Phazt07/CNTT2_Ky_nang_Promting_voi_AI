# Session 2 – Bài tập 06: Ép đầu ra JSON

## Phần 1: Phân tích nguyên nhân lỗi

Mô hình ngôn ngữ thường được huấn luyện để tạo hội thoại tự nhiên, lịch sự và hữu ích. Vì vậy, khi yêu cầu chưa giới hạn rõ định dạng, mô hình có thể thêm lời chào, câu dẫn hoặc lời chúc theo thói quen hội thoại. Các phần này khiến toàn bộ phản hồi không còn là JSON thuần: `JSON.parse` gặp chữ “Dạ” ở ký tự đầu tiên nên báo lỗi trước khi đọc đến dấu `{`.

## Phần 2: Prompt ép cấu trúc

```text
Bạn là bộ trích xuất dữ liệu bảo hành cho hệ thống ERP TechShop. Trích xuất thông tin từ biên bản bên dưới và trả về đúng một đối tượng JSON theo cấu trúc:

{
  "customer_name": "string hoặc null",
  "device": "string hoặc null",
  "issue": "string hoặc null"
}

Quy tắc:
- Chỉ lấy thông tin có trong biên bản; không suy đoán. Nếu không có trường nào, dùng null.
- Giữ nguyên tên riêng và mô tả lỗi theo nội dung nguồn.
- Chỉ trả về chuỗi JSON thuần túy, hợp lệ. Bắt đầu bằng { và kết thúc bằng }.
- Không dùng Markdown hoặc khối mã.
- Không thêm lời chào, lời dẫn, giải thích, ghi chú hay câu kết.
- Không thêm trường nào ngoài customer_name, device, issue.
- Dùng dấu ngoặc kép cho tên trường và giá trị chuỗi. Không dùng dấu phẩy sau trường cuối.

Biên bản:
{{warranty_record}}
```

**Lưu ý triển khai:** Prompt nghiêm ngặt giúp giảm lỗi định dạng nhưng không bảo đảm parse thành công 100%. Để bảo đảm quy trình, backend nên dùng chế độ JSON/schema-constrained output nếu API hỗ trợ, sau đó parse và kiểm tra schema; nếu không hợp lệ thì xử lý lỗi hoặc yêu cầu tạo lại trước khi nạp Database.
