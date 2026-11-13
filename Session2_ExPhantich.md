# Session 2 – Phân tích trade-off

## 1. Vấn đề

Cần chọn cách viết prompt cho tác vụ CREATE nội dung, có thể dùng ví dụ mẫu (few-shot) và yêu cầu đầu ra dạng JSON hoặc bảng. Prompt ngắn dễ dùng; prompt chi tiết thường kiểm soát kết quả tốt hơn.

## 2. Yêu cầu

- Đề xuất hai prompt: một đơn giản, một có nhiều ràng buộc.
- So sánh ưu và nhược điểm theo các tiêu chí.
- Chọn phương án phù hợp và chạy thử.

## 3. Cách làm

### Hai prompt mẫu

**Giải pháp 1 – Đơn giản**

> Tạo 3 ý tưởng bài đăng về tiết kiệm điện. Trả về JSON gồm các trường `title` và `content`.

**Giải pháp 2 – Chi tiết**

> Tạo 3 ý tưởng bài đăng mạng xã hội về tiết kiệm điện cho học sinh. Mỗi ý tưởng gồm `title` (tối đa 10 từ) và `content` (1–2 câu, thân thiện, dễ hiểu). Trả về duy nhất một JSON array hợp lệ, không thêm lời giải thích hay Markdown. Đảm bảo đủ 3 phần tử và không để trống trường nào. Ví dụ: `[{"title":"Tắt đèn khi ra khỏi phòng","content":"Một thao tác nhỏ giúp tiết kiệm điện mỗi ngày."}]`

### Bảng so sánh trade-off

| Tiêu chí | Giải pháp 1 (Đơn giản) | Giải pháp 2 (Chi tiết) |
|---|---|---|
| Độ dễ hiểu | Cao | Trung bình |
| Tốn token | Ít | Nhiều hơn |
| Chặn lỗi biên | Trung bình | Tốt |
| Kiểm soát định dạng | Cơ bản | Cao |
| Phù hợp | Tác vụ đơn giản, thử nhanh | Kết quả cần nhất quán |

### Lựa chọn và chạy thử

**Chọn Giải pháp 2** vì quy định rõ số lượng, nội dung và định dạng JSON, giúp kết quả nhất quán, dễ xử lý.

```json
[
  {
    "title": "Tắt đèn khi ra khỏi phòng",
    "content": "Nhớ tắt đèn khi không sử dụng để tiết kiệm điện mỗi ngày."
  },
  {
    "title": "Rút sạc khi dùng xong",
    "content": "Rút bộ sạc khỏi ổ điện khi không còn dùng để tránh lãng phí."
  },
  {
    "title": "Tận dụng ánh sáng tự nhiên",
    "content": "Mở cửa sổ vào ban ngày để giảm nhu cầu bật đèn."
  }
]
```
