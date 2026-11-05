# Bài 2: Chuỗi tấn công từ mật khẩu bị rò rỉ

## 1. Vấn đề là gì?

Tài khoản diễn đàn nhỏ bị lộ mật khẩu `123456`. Kẻ tấn công lấy cặp email và mật khẩu đó rồi thử đăng nhập tự động vào Gmail, Facebook và GitHub. Cách này gọi là **credential stuffing**. Vì dùng lại cùng một mật khẩu, một vụ rò rỉ có thể kéo theo nhiều tài khoản bị chiếm (hiệu ứng domino). Nếu chiếm được Gmail, kẻ tấn công còn có thể nhận email đặt lại mật khẩu của những dịch vụ khác.

## 2. Yêu cầu đề bài (IPO)

- **Input:** Mật khẩu `123456` bị lộ từ diễn đàn và được dùng lại ở ba tài khoản lớn.
- **Process:** Phân tích cách thử lại thông tin đăng nhập, độ dễ đoán của mật khẩu và cách Password Manager bảo vệ kho mật khẩu bằng AES-256.
- **Output:** Giải thích nguyên nhân của hiệu ứng domino và đưa ra cách bảo vệ từng tài khoản.

## 3. Cách làm

**Vì sao mật khẩu tự nghĩ dễ bị bẻ khóa?** Người dùng hay chọn chuỗi ngắn, quen thuộc như `123456`, tên hoặc ngày sinh. Kẻ tấn công thử các mẫu phổ biến trước nên có thể đoán rất nhanh; nếu diễn đàn làm lộ mã băm mật khẩu, chúng cũng có thể thử danh sách mật khẩu phổ biến để tìm ra mật khẩu gốc. Trình quản lý mật khẩu có thể tạo chuỗi **dài, ngẫu nhiên và riêng cho từng trang**, nên khó dự đoán hơn và một mật khẩu bị lộ không mở được tài khoản khác.

**AES-256 bảo vệ kho mật khẩu ra sao?** Một Password Manager đáng tin cậy có thể mã hóa kho bằng AES với khóa 256 bit. Khi chưa có khóa giải mã, người lấy được tệp kho chỉ thấy dữ liệu đã mã hóa, khác với danh sách mật khẩu ghi rõ trên giấy hoặc trong tệp văn bản. Khóa được tạo từ Master Password qua cơ chế dẫn xuất khóa; vì vậy phải đặt Master Password dài, duy nhất và bật xác thực nhiều yếu tố nếu có. AES-256 bảo vệ dữ liệu lưu trữ, nhưng không cứu được người dùng nếu họ tự nhập Master Password vào trang giả mạo.

**Việc cần làm ngay:** Đổi mật khẩu Gmail trước, sau đó đổi Facebook, GitHub và diễn đàn; đăng xuất các phiên lạ, bật xác thực hai bước và kiểm tra thông tin khôi phục tài khoản. Từ nay dùng một mật khẩu ngẫu nhiên khác nhau cho mỗi dịch vụ.

### Tham khảo

- [CISA – Credential stuffing và việc dùng lại mật khẩu](https://www.cisa.gov/sites/default/files/2023-12/ESF%20IDENTITY%20AND%20ACCESS%20MANAGEMENT%20RECOMMENDED%20BEST%20PRACTICES%20FOR%20ADMINISTRATORS%20PP-23-0248_508C.pdf)
- [NIST – Cách tạo mật khẩu tốt và dùng Password Manager](https://www.nist.gov/cybersecurity-and-privacy/how-do-i-create-good-password)
- [Bitwarden – Cơ chế mã hóa AES-256](https://bitwarden.com/help/what-encryption-is-used/)
