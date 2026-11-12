# Session 1 – Bài tập 09: RAG Grounding và khóa an toàn

## Phần 1: Vì sao AI tự tin đưa ra con số sai?

Khi không được cung cấp hợp đồng MartX, LLM dự đoán câu trả lời dựa trên các mẫu ngôn ngữ và thông tin chung đã học; nó không tra cứu được điều khoản riêng của doanh nghiệp. Vì vậy, mô hình có thể tạo ra con số nghe hợp lý nhưng không có căn cứ. Câu trả lời trôi chảy hoặc tự tin không chứng minh rằng thông tin đúng.

**Khác biệt:** Hỏi LLM không kèm tài liệu khiến câu trả lời dựa vào kiến thức tổng quát và có nguy cơ ảo giác. RAG Grounding cung cấp nguồn liên quan trong prompt để mô hình trả lời dựa trên nội dung đó, đồng thời yêu cầu nêu rõ khi tài liệu không có thông tin.

## Phần 2: Prompt RAG Grounding hoàn chỉnh

```text
Bạn là trợ lý nghiệp vụ thu mua của MartX. Hãy trả lời chỉ dựa trên văn bản hợp đồng được cung cấp dưới đây.

[1. VĂN BẢN HỢP ĐỒNG CHUẨN]
“Nhà cung cấp giao rau bị dập nát trên 10% thì phạt 5% giá trị lô bị dập nát và yêu cầu đổi hàng trong 24h.”

[2. CÂU HỎI NGHIỆP VỤ]
Theo hợp đồng, nếu nhà cung cấp giao rau bị dập nát trên 10% thì mức phạt là bao nhiêu và cần xử lý thế nào?

[3. NEGATIVE CONSTRAINT – KHÓA AN TOÀN]
Nếu thông tin không có trong văn bản, tuyệt đối trả lời “Không có dữ liệu trong tài liệu”, không tự suy đoán. Không bổ sung quy định từ kiến thức chung hoặc nguồn bên ngoài. Không thay đổi mức phạt, cơ sở tính phạt hay thời hạn. Nêu rõ căn cứ trong văn bản.
```

**Kết quả mong đợi:** Phạt 5% giá trị lô bị dập nát và yêu cầu đổi hàng trong 24 giờ. Không áp dụng mức 20% tổng giá trị đơn hàng hoặc đình chỉ nhập 30 ngày vì hợp đồng đã cung cấp không quy định như vậy.
