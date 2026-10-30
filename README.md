# TuTime — Lê Đoàn Văn Tú

Ứng dụng Flutter chấm công, kết nối backend ASP.NET Core.

## Chức năng

- Đăng ký email, đăng nhập bằng mật khẩu và OTP email.
- Phân quyền quản trị viên và nhân viên.
- Thêm, xem, sửa, xóa nhân viên; liên kết hồ sơ với tài khoản theo họ tên và email.
- Chấm công vào/tan ca bằng QR, lưu GPS và sai số; admin xem và hủy lượt chấm công.
- Chia sẻ vị trí GPS; bảng áp suất có biểu đồ theo thời gian, thấp/cao/trung bình, tạm dừng và đo lại.
- Sau lần đăng nhập OTP: cả nhân viên và quản trị viên đều có mục Quét / đăng ký khuôn mặt tại Tổng quan và Tài khoản. Có thể đăng ký, kiểm tra và tắt đăng nhập bằng camera trên thiết bị này.
- Đổi cỡ chữ, màu nền và cập nhật họ tên trong Cài đặt.
- Xin đi muộn/về sớm: nhân viên gửi đơn, admin duyệt/từ chối; lịch sử có nhãn khi lượt chấm công phù hợp đơn đã duyệt.

## Chạy

Đặt dự án ở đường dẫn không dấu rồi chạy:

```powershell
flutter pub get
flutter run -d emulator-5554 --dart-define=API_BASE_URL=https://ledoanvantu2-api.onrender.com --dart-define=OFFICE_LAT=10.7769 --dart-define=OFFICE_LNG=106.7009
```

API: https://ledoanvantu2-api.onrender.com
Swagger: https://ledoanvantu2-api.onrender.com/swagger/index.html
Backend: https://github.com/vantu1410/2380615001_LEDOANVANTU_backend

## Lưu ý trình diễn

- Bản nhận diện khuôn mặt qua camera dùng cho bài demo, chưa có cơ chế chống ảnh/video giả mạo. Mẫu khuôn mặt và phiên đăng nhập lưu mã hóa trên thiết bị; phiên API hết hạn sau 8 giờ thì cần đăng nhập OTP lại.
- Trên giả lập, cấu hình camera trước là webcam laptop. GPS và áp suất giả lập là dữ liệu mô phỏng, không phải cảm biến của laptop.
- Chức năng hồ sơ, liên kết nhân viên và xin phép cần backend bản mới.
- Biên dịch thư viện nhận diện lần đầu có thể mất vài phút. Chạy bộ test Flutter trên Windows cần môi trường C++/CMake phù hợp cho thư viện xử lý ảnh native.
