# TuTime — Lê Đoàn Văn Tú

Ứng dụng Flutter chấm công, kết nối backend ASP.NET Core.

## Chức năng

- Đăng ký email, đăng nhập bằng mật khẩu và OTP email.
- Phân quyền quản trị viên và nhân viên.
- Thêm, xem, sửa, xóa nhân viên; liên kết hồ sơ với tài khoản theo họ tên và email.
- Nhân viên tự đăng ký và xác nhận OTP sẽ tự xuất hiện trong danh sách nhân viên của Admin.
- Admin thêm thủ công tạo luôn tài khoản bằng tên đăng nhập và mật khẩu ban đầu; nhân viên đăng nhập bằng tên đăng nhập hoặc email, xác nhận OTP, không cần đăng ký lại. Tài khoản đã có được liên kết và giữ nguyên mật khẩu.
- Chấm công vào/tan ca bằng QR, lưu GPS và sai số; admin xem và hủy lượt chấm công.
- Chia sẻ vị trí GPS; bảng áp suất có biểu đồ theo thời gian, thấp/cao/trung bình, tạm dừng và đo lại.
- Sau lần đăng nhập OTP: cả nhân viên và quản trị viên đều có mục Quét / đăng ký khuôn mặt tại Tổng quan và Tài khoản. Có thể đăng ký, kiểm tra và tắt đăng nhập bằng camera trên thiết bị này.
- Đổi cỡ chữ, màu nền và cập nhật họ tên trong Cài đặt.
- Xin đi muộn/về sớm: nhân viên gửi đơn, admin duyệt/từ chối; lịch sử có nhãn khi lượt chấm công phù hợp đơn đã duyệt.

Danh sách chức năng ngắn gọn: [Lê Đoàn Văn Tú.txt](L%C3%AA%20%C4%90o%C3%A0n%20V%C4%83n%20T%C3%BA.txt). Điểm trong file là tự đánh giá tham khảo.

## Chạy

Đặt dự án ở đường dẫn không dấu rồi chạy:

```powershell
flutter pub get
flutter devices
flutter run -d emulator-5554 --dart-define=API_BASE_URL=https://ledoanvantu2-api.onrender.com --dart-define=OFFICE_LAT=10.7769 --dart-define=OFFICE_LNG=106.7009
```

Thay `emulator-5554` bằng mã thiết bị thực tế. Không thêm dấu `\` ở cuối lệnh PowerShell và chỉ chạy một phiên `flutter run` cho cùng thiết bị. Cấu hình debug tắt Impeller; Gradle giới hạn heap 3 GB và tự dừng daemon sau 2 phút không hoạt động để giảm tải khi chạy giả lập.

API: https://ledoanvantu2-api.onrender.com
Swagger: https://ledoanvantu2-api.onrender.com/swagger/index.html
Backend: https://github.com/vantu1410/2380615001_LEDOANVANTU_backend

## Lưu ý trình diễn

- Bản nhận diện khuôn mặt qua camera dùng cho bài demo, chưa có cơ chế chống ảnh/video giả mạo. Mẫu khuôn mặt và phiên đăng nhập lưu mã hóa trên thiết bị; phiên API hết hạn sau 8 giờ thì cần đăng nhập OTP lại.
- Trên giả lập, cấu hình camera trước là webcam laptop. GPS và áp suất giả lập là dữ liệu mô phỏng, không phải cảm biến của laptop.
- Chức năng hồ sơ, liên kết nhân viên và xin phép cần backend bản mới.
- Biên dịch thư viện nhận diện lần đầu có thể mất vài phút. Chạy bộ test Flutter trên Windows cần môi trường C++/CMake phù hợp cho thư viện xử lý ảnh native.
