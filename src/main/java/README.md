Báo cáo: Lựa chọn cấp độ Logging (Log Levels) cho BankSystem

Hệ thống áp dụng thư viện SLF4J/Logback và sử dụng các cấp độ log sau để tăng tính quan sát (observability):

Mức INFO (Thông tin): Được sử dụng để ghi lại các giao dịch thành công (Nạp tiền, Rút tiền hợp lệ, Chuyển khoản hoàn tất).

Dữ liệu ghi lại: Mã tài khoản (Account ID), Số tiền giao dịch, Loại giao dịch. (Không ghi mật khẩu hay thông tin nhạy cảm).

Lý do: Giúp quản trị viên có cái nhìn tổng quan về lượng giao dịch đang diễn ra bình thường trong hệ thống.

Mức WARN (Cảnh báo): Được sử dụng khi xảy ra các thao tác lỗi logic từ phía người dùng nhưng hệ thống vẫn hoạt động bình thường (Ví dụ: Rút tiền vượt quá số dư - InsufficientFundsException, nhập sai định dạng tiền tệ).

Dữ liệu ghi lại: Mã tài khoản cố tình thao tác lỗi, Số dư hiện tại, Số tiền yêu cầu rút.

Lý do: Để đánh dấu các hành vi đáng ngờ, hoặc phục vụ việc hỗ trợ khách hàng (Customer Service) khi họ phàn nàn không rút được tiền.

Mức ERROR (Lỗi hệ thống): (Nếu có kết nối DB) Được gọi khi hệ thống không thể kết nối tới cơ sở dữ liệu, hoặc bắt được các RuntimeException không lường trước.

Dữ liệu ghi lại: Toàn bộ Stack Trace của Exception.

Lý do: Giúp Developer ngay lập tức dò ra dòng code gây crash hệ thống để tung ra bản vá lỗi (Hotfix).