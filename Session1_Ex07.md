# Session 1 – Bài tập 07: Data Masking và De-masking

## Phần A: Masking Table

| Thông tin PII thật | Nhãn che mờ Placeholder | Loại dữ liệu |
|---|---|---|
| Phạm Minh C | `[KHACH_HANG]` | Họ tên |
| 0988.111.222 | `[SO_DIEN_THOAI]` | Số điện thoại |
| minhc@gmail.com | `[EMAIL]` | Địa chỉ email |
| Căn hộ 502 Chung cư Sunrise, Q7 | `[DIA_CHI_KHACH_HANG]` | Địa chỉ nơi ở |

> Bảng ánh xạ này chỉ lưu trong hệ thống nội bộ có phân quyền; không gửi kèm nội dung cho AI công cộng.

## Phần B: Masked Input

“Tôi là `[KHACH_HANG]` (SĐT: `[SO_DIEN_THOAI]`, Email: `[EMAIL]`, ở `[DIA_CHI_KHACH_HANG]`). Ngày 20/09 tôi mua 2kg thịt bò Wagyu giá 4.500.000 VNĐ tại MartX District 7 nhưng bị giao chậm 3 tiếng làm hỏng tiệc gia đình. Tôi yêu cầu bồi thường 100%!”

## Phần C: Prompt gửi AI

> Dựa trên khiếu nại dưới đây, hãy soạn một email xin lỗi bằng tiếng Việt, giọng chân thành và chuyên nghiệp. Xưng hô lịch sự với khách; dùng `[KHACH_HANG]` hoặc “Quý khách”, tuyệt đối không đoán hay thay thế các placeholder. Thừa nhận sự bất tiện do giao chậm, thể hiện sự cảm thông, xin lỗi và cho biết bộ phận CSKH sẽ kiểm tra đơn hàng cùng yêu cầu bồi thường 100%, rồi phản hồi theo chính sách của MartX. Không tự hứa mức bồi thường hoặc thời hạn chưa được xác nhận. Giữ email ngắn gọn.
>
> Khiếu nại: “Tôi là `[KHACH_HANG]` (SĐT: `[SO_DIEN_THOAI]`, Email: `[EMAIL]`, ở `[DIA_CHI_KHACH_HANG]`). Ngày 20/09 tôi mua 2kg thịt bò Wagyu giá 4.500.000 VNĐ tại MartX District 7 nhưng bị giao chậm 3 tiếng làm hỏng tiệc gia đình. Tôi yêu cầu bồi thường 100%!”

## Phần D: Thư xin lỗi sau khi de-mask

**Kính gửi ông Phạm Minh C,**

MartX chân thành xin lỗi ông vì đơn hàng 2kg thịt bò Wagyu trị giá 4.500.000 VNĐ mua ngày 20/09 tại MartX District 7 bị giao chậm 3 tiếng, ảnh hưởng đến buổi tiệc gia đình. Chúng tôi hiểu sự việc đã gây bất tiện và rất tiếc về trải nghiệm này.

Bộ phận Chăm sóc Khách hàng sẽ kiểm tra đơn hàng và yêu cầu bồi thường 100% của ông, sau đó liên hệ để phản hồi theo chính sách của MartX.

Trân trọng,  
Bộ phận Chăm sóc Khách hàng MartX

**Thông tin de-mask nội bộ (không gửi AI):** `[KHACH_HANG]` → Phạm Minh C; `[SO_DIEN_THOAI]` → 0988.111.222; `[EMAIL]` → minhc@gmail.com; `[DIA_CHI_KHACH_HANG]` → Căn hộ 502 Chung cư Sunrise, Q7. Thư mẫu chỉ dùng tên để xưng hô; không đưa số điện thoại, email và địa chỉ vào thư vì không cần thiết.
