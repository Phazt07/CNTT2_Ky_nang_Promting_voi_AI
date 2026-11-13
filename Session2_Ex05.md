# Session 2 – Bài tập 05: In-Context Learning và Few-shot

## Phần 1: Phân tích cơ chế In-Context Learning

In-Context Learning (ICL) là khả năng mô hình suy ra cách làm một nhiệm vụ từ chỉ dẫn và ví dụ đặt ngay trong prompt. Mô hình dùng các mẫu đó để diễn giải đầu vào mới trong phiên hiện tại; trọng số mô hình không bị cập nhật và không cần huấn luyện lại.

Với phân loại cảm xúc, chỉ dẫn đơn thuần có thể khiến AI dựa quá nhiều vào các từ tích cực như “đẹp mê ly” hay “đầm tay”. Các ví dụ Few-shot cho thấy cách đọc toàn bộ câu, phát hiện tương phản giữa lời khen và hệ quả bất lợi, rồi chọn nhãn theo ý định thực tế của khách hàng. Nhờ vậy, con số CPU 98°C được hiểu là dấu hiệu máy quá nóng, còn câu “khỏi cần bật lò sưởi” là mỉa mai. Đây là suy luận dựa trên ngữ cảnh mẫu trong prompt, không phải mô hình đã học thêm vĩnh viễn.

## Phần 2: Prompt Few-shot hoàn chỉnh

```text
Bạn là chuyên viên đảm bảo chất lượng của TechShop. Hãy phân loại cảm xúc chính của mỗi đánh giá sản phẩm thành đúng một nhãn: TÍCH CỰC hoặc TIÊU CỰC.

Hướng dẫn:
- Đọc toàn bộ câu và xác định ý định thực sự, không chỉ đếm từ tích cực hay tiêu cực.
- Nhận diện mỉa mai, khen đểu và nghĩa bóng. Lời khen đi kèm một hậu quả rõ ràng gây bất tiện hoặc cho thấy lỗi sản phẩm thường mang ý chê.
- Cân nhắc các dữ kiện cụ thể như nhiệt độ quá cao, pin tụt nhanh hoặc giao hàng trễ.
- Nếu câu có cả khen lẫn chê, chọn cảm xúc chính mà khách muốn truyền đạt.
- Chỉ trả về nhãn, không giải thích.

Ví dụ 1
Input: "Máy thiết kế đẹp mê ly, cầm rất đầm tay, mùa đông ôm máy chơi game thì khỏi cần bật lò sưởi vì CPU lên tận 98°C!"
Output: TIÊU CỰC

Ví dụ 2
Input: "Pin đúng là đỉnh cao, vừa rút sạc đi họp một tiếng đã phải tìm ổ cắm để máy khỏi tắt giữa chừng."
Output: TIÊU CỰC

Ví dụ 3
Input: "Giao hàng nhanh thật, đặt từ tuần trước, đến hôm nay mới thấy shipper gọi. Dịch vụ cho mình thời gian chờ để suy ngẫm luôn!"
Output: TIÊU CỰC

Bây giờ hãy phân loại đánh giá sau.
Input: "{{review}}"
Output:
```
