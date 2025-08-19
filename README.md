GPX Run Simulator

Một ứng dụng web mạnh mẽ được thiết kế để tạo ra các tệp tin GPX mô phỏng hoạt động chạy bộ một cách chân thực. Công cụ này cho phép người dùng tùy chỉnh chi tiết các buổi chạy, tạo lộ trình bám sát đường đi thực tế, và xuất hàng loạt file tương thích hoàn toàn với Strava và các nền tảng thể thao khác.

Dự án này được xây dựng hoàn toàn trong một file HTML duy nhất, không cần backend hay cài đặt phức tạp.



✨ Tính Năng Nổi Bật

Giao Diện Trực Quan: Thiết kế hiện đại, dễ sử dụng với các thanh trượt và bản đồ tương tác.

Tùy Chỉnh Linh Hoạt:

Vị trí: Chọn điểm xuất phát bằng cách kéo thả ghim trên bản đồ hoặc chọn nhanh từ 10 thành phố lớn của Việt Nam.

Hiệu suất: Dễ dàng điều chỉnh Quãng đường và Pace trung bình.

Mô Phỏng Chân Thực:

Quỹ đạo thông minh: Tích hợp API định tuyến OSRM để tạo ra lộ trình chạy bám sát đường đi thực tế, đảm bảo điểm kết thúc gần điểm xuất phát.

Dữ liệu động: Tốc độ, nhịp tim, và guồng chân (cadence) được mô phỏng biến thiên liên tục, có các giai đoạn khởi động, chạy chính, và hạ nhiệt.

Tính ngẫu nhiên: Tự động xê dịch nhẹ vị trí bắt đầu và các thông số hiệu suất để mỗi buổi chạy là độc nhất.

Tạo Hàng Loạt:

Thiết lập khoảng ngày và khung giờ để tự động tạo ra nhiều hoạt động.

Hỗ trợ các nút chọn nhanh số ngày (1-7 ngày).

Xem Trước & Tải Về:

Xem trước quỹ đạo của từng file đã tạo trên bản đồ.

Tùy chọn tải về các file riêng lẻ hoặc gộp tất cả vào một file .zip duy nhất.

🚀 Cách Sử Dụng

Mở file index.html bằng bất kỳ trình duyệt web hiện đại nào.

Thiết lập Vị trí:

Kéo thả ghim trên bản đồ đến vị trí mong muốn.

Hoặc nhấn vào các nút tên thành phố để di chuyển nhanh đến khu vực đó.

Thiết lập Hiệu suất:

Dùng thanh trượt để điều chỉnh Quãng đường và Pace trung bình.

Tích vào ô "Thêm ngẫu nhiên" để các chỉ số có sự dao động nhẹ (+/- 10%) cho mỗi lần tạo.

Thiết lập Xuất Hàng Loạt:

Chọn Ngày bắt đầu và Ngày kết thúc.

Sử dụng các nút [1 Ngày], [2 Ngày]... để chọn nhanh.

Điều chỉnh Khung giờ chạy trong ngày.

Nhấn nút "Tạo File GPX".

Xem lại & Tải về:

Trong bảng kết quả, chọn các file bạn muốn tải.

Sử dụng nút con mắt để xem trước quỹ đạo.

Chọn tùy chọn nén file .zip nếu cần.

Nhấn "Tải File Đã Chọn".

🛠️ Công Nghệ Sử Dụng

Frontend: HTML, JavaScript (ES6)

Styling: Tailwind CSS

Bản đồ: LeafletJS

API Định tuyến: Open Source Routing Machine (OSRM)

Nén File: JSZip

Icons: Lucide Icons

🧠 Logic Mô Phỏng Cốt Lõi

Điểm làm nên sự khác biệt của ứng dụng này là thuật toán mô phỏng dữ liệu phức tạp:



Tạo Lộ Trình Thông Minh: Thay vì vẽ đường ngẫu nhiên, ứng dụng tạo ra 3 điểm tọa độ (bắt đầu, điểm giữa ngẫu nhiên, kết thúc) và gửi đến OSRM API để nhận về một lộ trình thực tế bám theo đường đi bộ.

Hiệu Chỉnh Quãng Đường: Lộ trình từ API có thể dài hoặc ngắn hơn yêu cầu một chút. Ứng dụng sẽ "tái tạo" (resample) lại toàn bộ các điểm trên quỹ đạo để đảm bảo tổng quãng đường cuối cùng chính xác tuyệt đối với thiết lập của người dùng.

Mô Phỏng Dữ Liệu Động: Dữ liệu tốc độ không phải là một hằng số mà biến thiên liên tục dựa trên một hàm nhiễu (noise function), mô phỏng các giai đoạn khởi động, chạy chính và hạ nhiệt. Dữ liệu nhịp tim và guồng chân được tính toán tương quan với tốc độ tại mỗi thời điểm.
