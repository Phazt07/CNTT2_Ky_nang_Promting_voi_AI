# Session 1 – Bài tập 05: Human-in-the-loop tại MartX

## Phần 1: Phân tích vi phạm

1. **Giao quyết định có tác động lớn cho AI và bỏ qua thẩm định của con người.** AI chỉ hỗ trợ phân tích, không có thẩm quyền quyết định sa thải. Trưởng phòng đã biến đề xuất thành quyết định tức thời mà không kiểm tra dữ liệu, tiêu chí, hoàn cảnh từng nhân viên hay cho họ cơ hội giải trình. Điều này vi phạm nguyên tắc Human-in-the-loop và trách nhiệm nghề nghiệp của người quản lý.

2. **Cho rằng dữ liệu và AI mặc nhiên khách quan, đồng thời xử lý dữ liệu nhân sự thiếu trách nhiệm.** KPI và chấm công có thể thiếu, sai hoặc phản ánh định kiến trong cách đặt chỉ tiêu, phân công ca và ghi nhận hiệu suất. Lệnh yêu cầu xếp “3 người kém nhất” để sa thải ngay cũng áp đặt kết luận, không xem xét bối cảnh hay tiêu chí công bằng. Việc đưa dữ liệu nhân sự vào AI còn cần được phép và bảo vệ đúng quy định nội bộ, quyền riêng tư và pháp luật áp dụng. Nói “AI quyết nên tôi không chịu trách nhiệm” không loại bỏ trách nhiệm của người ra quyết định.

## Phần 2: Sơ đồ quy trình an toàn 3 bước

```text
┌──────────────────────────────────────────────┐
│ 1. NHẬP DỮ LIỆU                              │
│ HR xác nhận thẩm quyền sử dụng, mục đích,     │
│ độ chính xác và tính cần thiết của dữ liệu;   │
│ giảm thiểu/ẩn danh dữ liệu nếu phù hợp.       │
└──────────────────────┬───────────────────────┘
                       ↓
┌──────────────────────────────────────────────┐
│ 2. AI ĐỀ XUẤT – CON NGƯỜI THẨM ĐỊNH          │
│ AI chỉ phân tích theo tiêu chí đã nêu, chỉ   │
│ ra giới hạn và điểm chưa chắc chắn; không    │
│ tự xếp hạng để sa thải. HR kiểm tra nguồn,   │
│ sai lệch, bối cảnh và nghe nhân viên giải    │
│ trình; yêu cầu sửa hoặc bác đề xuất khi cần. │
└──────────────────────┬───────────────────────┘
                       ↓
┌──────────────────────────────────────────────┐
│ 3. QUYẾT ĐỊNH VÀ KÝ                          │
│ Người có thẩm quyền cân nhắc độc lập theo    │
│ chính sách và pháp luật; ghi nhận căn cứ,    │
│ kiểm tra quyền khiếu nại và thông báo rõ lý  │
│ do. Chỉ ký khi đã thẩm định đầy đủ.          │
└──────────────────────────────────────────────┘
```

**Nguyên tắc:** AI cung cấp thông tin tham khảo; con người chịu trách nhiệm kiểm chứng và quyết định. Không dùng đầu ra AI làm căn cứ duy nhất để sa thải.
