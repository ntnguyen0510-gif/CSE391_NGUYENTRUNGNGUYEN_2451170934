Phần A:
Câu A1:

Dưới đây là phần đáp án chi tiết và phân tích nguyên lý hệ thống Grid System (chuẩn Bootstrap) cho đoạn mã HTML của bạn.
I. BẢNG PHÂN TÍCH LAYOUT QUA 3 KÍCH THƯỚC MÀN HÌNHHệ thống Grid chia màn hình thành 12 cột ảo chiều ngang.
 Dựa vào các class được chỉ định, bố cục của 4 khối Box sẽ thay đổi như sau:Kích thước< 768px (Mobile)768px - 991px (Tablet)≥ 992px (Desktop)Số cột chiếm dụng12 cột mỗi Box(Ăn theo class col-12)6 cột mỗi Box(Ăn theo class col-md-6)3 cột mỗi Box(Ăn theo class col-lg-3)Box layout hình trực quanXếp dọc thành 1 cột(Mỗi hàng chứa 1 Box)Xếp thành lưới 2x2(Mỗi hàng chứa 2 Box)Xếp ngang thành 1 hàng(Hàng chứa đủ cả 4 Box)Sơ đồ bố cục chi tiết┌──────────┐│  Box 1   │├──────────┤│  Box 2   │├──────────┤│  Box 3   │├──────────┤│  Box 4   │└──────────┘┌─────┬─────┐│Box 1│Box 2│├─────┼─────┤│Box 3│Box 4│└─────┴─────┘┌───┬───┬───┬───┐│B1 │B2 │B3 │B4 │└───┴───┴───┴───┘
 
 II. GIẢI THÍCH CÂU HỎI THÊM
 1. col-md-6 nghĩa là gì?col: Viết tắt của Column (Cột).md: Viết tắt của Medium screen breakpoint (Áp dụng cho màn hình kích thước trung bình, cụ thể là từ 768px trở lên).6: Số lượng cột ảo mà phần tử này sẽ chiếm trong tổng số 12 cột của hệ thống Grid ($6/12 = 50\%$ chiều rộng hàng).Ý nghĩa trọn vẹn: Khi màn hình có độ rộng từ 768px trở lên, phần tử này sẽ chiếm chính xác 6 cột trên tổng số 12 cột (tức là rộng bằng nửa màn hình).
Do đó, cần 2 phần tử col-md-6 để lấp đầy 1 hàng ngang.
 2. Tại sao không cần viết col-sm-12?Trong hệ thống Grid của Bootstrap, các class hoạt động theo nguyên lý Mobile-First và Kế thừa hướng lên (Upward Inheritance).Class col-12 không chứa hậu tố kích thước (như sm, md, lg) được hiểu là cấu hình áp dụng cho mốc nhỏ nhất (màn hình X-Small, < 576px).Giá trị này sẽ tự động kế thừa và giữ nguyên cho các màn hình lớn hơn tiếp theo (sm: $\ge 576px$) cho đến khi nó gặp một Media Query khác lớn hơn ghi đè lên nó (ở đây là col-md-6 ở mốc $\ge 768px$).Do đó, ở khoảng màn hình sm (từ 576px đến 767px), các Box đã tự động nhận giá trị rộng 12 cột từ col-12 rồi. Việc viết thêm col-sm-12 là hoàn toàn dư thừa và làm bẩn code.

 