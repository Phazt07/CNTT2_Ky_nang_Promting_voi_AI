Session5_Baithuchanh1

Lập kế hoạch tài chính cá nhân

Vấn đề

Người dùng có thu nhập thay đổi, chi phí cố định, các khoản nợ và mục tiêu tiết kiệm. Cần lập ngân sách tháng, kiểm tra phép tính và phát hiện khi tiền không đủ cho các mục tiêu.

Yêu cầu

Prompt cần yêu cầu AI tính thu nhập sau thuế, trừ chi phí cố định, dành tiền trả nợ tối thiểu, trích tiết kiệm ít nhất 20% thu nhập sau thuế và chia phần còn lại theo quy tắc 50/30/20 cải tiến.

AI phải trình bày các phép tính và số trung gian để người dùng kiểm tra. Không yêu cầu tiết lộ suy luận nội bộ. Bảng cuối cùng cần có hạng mục, số tiền, tỷ lệ phần trăm và ghi chú. Tỷ lệ được tính trên thu nhập sau thuế và tổng tỷ lệ cần bằng 100%. Nếu ngân sách không đủ, phải báo thiếu hụt và không được tự tạo số liệu để làm cho ngân sách cân bằng.

Prompt thực thi

Bạn là trợ lý lập ngân sách cá nhân. Dựa trên dữ liệu người dùng cung cấp, hãy tính kế hoạch ngân sách tháng. Hãy nêu công thức và các số liệu trung gian để người dùng kiểm tra; không trình bày suy luận nội bộ dài dòng.

Dữ liệu đầu vào:
- Thu nhập gộp tháng: {{INCOME}}
- Thuế và khoản khấu trừ: {{TAX}}
- Chi phí cố định bắt buộc: {{FIXED_COSTS}}
- Các khoản nợ, số tiền tối thiểu và hạn thanh toán: {{DEBTS}}
- Mục tiêu tiết kiệm: {{SAVINGS_GOAL}}

Thực hiện lần lượt:
1. Tính thu nhập sau thuế = thu nhập gộp - thuế và khoản khấu trừ.
2. Tính tiền còn lại sau chi phí cố định = thu nhập sau thuế - tổng chi phí cố định.
3. Dành tiền trả tối thiểu cho các khoản nợ đến hạn. Không giảm khoản thanh toán tối thiểu đã được cung cấp.
4. Dành tiết kiệm tối thiểu bằng 20% thu nhập sau thuế hoặc mức mục tiêu cao hơn nếu ngân sách cho phép. Nếu không đủ tiền, báo rõ phần thiếu.
5. Chia phần còn lại sau các khoản trên theo quy tắc 50/30/20 cải tiến: 50% cho chi phí thiết yếu linh hoạt, 30% cho chi tiêu tùy ý, 20% cho quỹ dự phòng hoặc trả nợ thêm. Ghi rõ số tiền từng phần.
6. Kiểm tra tổng tiền phân bổ và tổng tỷ lệ phần trăm. Tỷ lệ tính trên thu nhập sau thuế. Làm tròn tiền đến đơn vị tiền tệ đầu vào và tỷ lệ đến 2 chữ số thập phân; điều chỉnh sai số làm tròn ở hạng mục cuối để tổng tỷ lệ hiển thị là 100.00%.
7. Nếu tổng các khoản bắt buộc, trả nợ tối thiểu và tiết kiệm tối thiểu vượt thu nhập sau thuế, báo ngân sách không khả thi, tính số tiền thiếu và không phân bổ giả định. Không bỏ qua khoản nợ đến hạn.
8. Nếu thiếu dữ liệu cần thiết, hỏi bổ sung hoặc đánh dấu chưa đủ dữ liệu; không tự đoán.

Chỉ xuất hai phần:
Phần 1: Các phép tính kiểm tra được, ghi rõ công thức và kết quả từng bước.
Phần 2: Bảng Markdown có các cột Hạng mục, Số tiền, Tỷ lệ %, Ghi chú.

Ví dụ chạy thử

Dữ liệu:
Thu nhập gộp: 30.000.000 đồng
Thuế và khoản khấu trừ: 3.000.000 đồng
Chi phí cố định: 9.000.000 đồng
Nợ đến hạn: 4.000.000 đồng
Mục tiêu tiết kiệm: 20% thu nhập sau thuế

Kết quả mẫu:

Phần 1: Các phép tính
- Thu nhập sau thuế = 30.000.000 - 3.000.000 = 27.000.000 đồng.
- Sau chi phí cố định = 27.000.000 - 9.000.000 = 18.000.000 đồng.
- Sau trả nợ tối thiểu = 18.000.000 - 4.000.000 = 14.000.000 đồng.
- Tiết kiệm tối thiểu = 27.000.000 x 20% = 5.400.000 đồng.
- Còn lại để chia theo 50/30/20 cải tiến = 14.000.000 - 5.400.000 = 8.600.000 đồng.
- Thiết yếu linh hoạt = 8.600.000 x 50% = 4.300.000 đồng.
- Chi tiêu tùy ý = 8.600.000 x 30% = 2.580.000 đồng.
- Quỹ dự phòng hoặc trả nợ thêm = 8.600.000 x 20% = 1.720.000 đồng.
- Tổng phân bổ = 9.000.000 + 4.000.000 + 5.400.000 + 4.300.000 + 2.580.000 + 1.720.000 = 27.000.000 đồng.

Phần 2: Bảng phân bổ ngân sách

| Hạng mục | Số tiền | Tỷ lệ % | Ghi chú |
| Chi phí cố định | 9.000.000 đồng | 33.33% | Bắt buộc |
| Trả nợ tối thiểu | 4.000.000 đồng | 14.81% | Thanh toán đúng hạn |
| Tiết kiệm | 5.400.000 đồng | 20.00% | Đạt mục tiêu tối thiểu |
| Thiết yếu linh hoạt | 4.300.000 đồng | 15.93% | 50% phần còn lại |
| Chi tiêu tùy ý | 2.580.000 đồng | 9.56% | 30% phần còn lại |
| Quỹ dự phòng hoặc trả nợ thêm | 1.720.000 đồng | 6.37% | 20% phần còn lại |
| Tổng | 27.000.000 đồng | 100.00% | Cân bằng với thu nhập sau thuế |
