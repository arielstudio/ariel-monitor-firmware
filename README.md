# Ariel Monitor — firmware

Máy cầm tay theo dõi thời tiết và máy in 3D Bambu Lab, của [Ariel Studio](https://arielstudio.vn).
Chạy trên board **Sunton ESP32-2432S028** ("Cheap Yellow Display", màn cảm ứng 2.8").

Kho này chỉ chứa firmware đã ký số. Máy Ariel Monitor tự kiểm tra bản mới ở đây mỗi ngày.

📖 **Hướng dẫn sử dụng** (chức năng, thông báo, màu đèn LED, cài đặt, xử lý sự cố): tải file
`HUONG-DAN-SU-DUNG-vX.Y.Z.pdf` ở mục [Releases](../../releases/latest) (bản mới nhất).

## Nạp lần đầu (máy mới)

> File `-full.bin` xoá toàn bộ cài đặt (WiFi, thành phố, mã máy in). Chỉ dùng cho board mới
> hoặc khi muốn cài lại từ đầu. Máy đang dùng thì cập nhật trong app Cài đặt (mục dưới).

1. Tải file **`ArielMonitor-vX.Y.Z-full.bin`** ở mục [Releases](../../releases/latest) (bản mới nhất).
2. Cắm board vào máy tính bằng cáp USB.
3. Mở **https://espressif.github.io/esptool-js/** bằng Chrome hoặc Edge, bấm **Connect**, chọn cổng USB của board.
4. Ô **Flash Address** điền `0x0`, chọn file vừa tải, bấm **Program**. Chờ khoảng 1 phút.
5. Rút rồi cắm lại cáp USB (hoặc bấm nút RST nếu board còn nút này).

Nếu báo lỗi kết nối: rút cáp, **giữ nút BOOT** trong lúc cắm lại cáp, thả BOOT rồi bấm Connect / Program lại.

## Lần đầu bật máy

1. Màn khởi động "Ariel Monitor", sau đó hiện danh sách WiFi xung quanh.
2. Chạm vào WiFi nhà bạn, gõ mật khẩu, bấm **Nối** (chỉ WiFi 2.4 GHz).
3. Xong. Muốn đổi thành phố hoặc thêm máy in Bambu Lab: mở app **Cài đặt** trên máy,
   quét mã QR, đăng nhập bằng tài khoản `admin` và mật khẩu hiện ngay dưới mã QR.

## Dùng hằng ngày

- Nút tròn hình ngôi nhà hoặc bấm nút **BOOT**: về màn hình chính. **Giữ BOOT 2 giây**: tắt / mở máy.
- Máy tự ngủ sau 3 phút; chạm màn hình hoặc bấm BOOT để thức. Máy bị treo sẽ tự khởi động lại.
- Chuông trên màn hình chính: xem thông báo (tắt tự hiện ở **Cài đặt → Thông báo**). Đặt vỏ ngược: **Cài đặt → trang 2 → Lật màn hình 180°**.
- Máy in có chấm đỏ: mở máy đó, chạm dòng **"N cảnh báo"** để đọc nội dung cảnh báo tiếng Việt của Bambu.
- Dùng pin: xem sơ đồ đấu trong gói firmware gửi kèm (LiPo + mạch sạc tăng áp 5 V → cổng P1, đo pin bằng MAX17048).

## Cập nhật

Không cần nạp lại qua USB. Máy tự kiểm tra mỗi ngày; có bản mới là hiện hộp hỏi → **Cập nhật ngay**
(hoặc **Để sau**, rồi cài ở **Cài đặt → trang 2 → Phiên bản**). Máy tự tải, kiểm tra chữ ký và khởi động lại.
Nếu bản mới có lỗi, máy tự quay về bản cũ.

## Ghi chú

- Hỗ trợ board bản 2 cổng USB (màn ST7789). Bản 1 cổng USB (ILI9341) được tự nhận nhưng chưa kiểm chứng.
- Máy in Bambu Lab: kết nối trong mạng LAN bằng mã truy cập (Access Code) trên màn hình máy in, chỉ đọc trạng thái.
- Dữ liệu thời tiết: [Open-Meteo](https://open-meteo.com).
