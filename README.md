☕ TDTU Cafe Factory SCADA
Hệ thống điều khiển và giám sát Web SCADA cho Máy đóng gói cà phê tự động

Đồ án chuyên ngành Cơ điện tử - Khoa Điện - Điện tử, Đại học Tôn Đức Thắng (TDTU)

📖 Giới thiệu dự án
Dự án TDTU Cafe Factory SCADA là một hệ thống tự động hóa công nghiệp thu nhỏ, cho phép giám sát và điều khiển máy đóng gói cà phê từ xa thông qua giao diện Web hiện đại.

Hệ thống kết nối trực tiếp với phần cứng điều khiển trung tâm là PLC Siemens S7-1200 thông qua giao thức S7 Communication, dữ liệu sau đó được xử lý qua Node-RED và truyền tải theo thời gian thực (Real-time) qua giao thức MQTT (HiveMQ Cloud) đến trình duyệt Web của người dùng.

🚀 Các tính năng nổi bật
Điều khiển từ xa (Remote Control): Gửi các lệnh START, STOP, RESET xuống PLC với độ trễ cực thấp. Thiết lập các thông số sản xuất (Trọng lượng W1, W2, Số lượng mục tiêu).

Giám sát thời gian thực (Real-time Monitoring): Đếm số gói hoàn thành, hiển thị trạng thái hoạt động của máy.

Chẩn đoán kỹ thuật (Watchdog Timer): Tự động phát hiện sự cố mất kết nối mạng hoặc PLC mất điện trong vòng 6 giây và cảnh báo trực quan trên giao diện.

Dashboard OEE (Overall Equipment Effectiveness): Tự động tính toán và vẽ biểu đồ hiệu suất vận hành của máy theo thời gian thực.

Quản lý lịch sử lệnh (Order History): Ghi nhận mọi thao tác điều khiển ngay trên giao diện Web.

Xuất báo cáo (CSV Export): Xuất toàn bộ dữ liệu lịch sử vận hành ra định dạng Excel/CSV chỉ với 1 cú click để phục vụ báo cáo.

🛠️ Kiến trúc hệ thống & Công nghệ sử dụng
Phần cứng (Hardware):

PLC Siemens S7-1200 (Lập trình Ladder logic bằng TIA Portal).

Cơ cấu máy đóng gói cà phê (Loadcell, Xilanh khí nén, Động cơ).

Middleware (Trạm trung chuyển):

Node-RED: Đóng vai trò Gateway kết nối PLC (S7 node) và Internet (MQTT node).

HiveMQ Cloud: MQTT Broker xử lý thông điệp truyền tải.

Giao diện người dùng (Frontend):

HTML5 / CSS3 / JavaScript thuần.

Tailwind CSS: Thiết kế giao diện Industrial Dashboard linh hoạt (Responsive).

Chart.js: Trực quan hóa dữ liệu OEE.

MQTT.js (WebSocket): Nhận và gửi dữ liệu trực tiếp trên trình duyệt.

⚙️ Hướng dẫn cài đặt và sử dụng
1. Phía PLC & Node-RED
Nạp chương trình Ladder logic chứa các biến điều khiển %M0.0 (Start/Stop), %M0.7 (Reset), MD60, MD64, MW20, MW22 xuống PLC S7-1200.

Đảm bảo PLC và máy tính chạy Node-RED kết nối chung một mạng LAN.

Mở Node-RED, import cấu hình luồng (Flow) và nhấn Deploy. Kiểm tra đảm bảo Node S7 báo trạng thái Online.

2. Phía Web SCADA
Hệ thống Frontend được thiết kế dạng Serverless, không cần cài đặt Node.js hay Backend nội bộ:

Mở trực tiếp file index.html bằng bất kỳ trình duyệt nào (Chrome, Edge, Safari...).

Hoặc tải toàn bộ thư mục lên các nền tảng Hosting miễn phí như Vercel, GitHub Pages để điều khiển máy qua mạng Internet 4G/5G từ điện thoại.

Kiểm tra thanh trạng thái MQTT ở góc phải báo CONNECTED là hệ thống đã sẵn sàng.
