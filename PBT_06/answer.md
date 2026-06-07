Phần A:
Câu A1:

Dưới đây là phần đáp án chi tiết và phân tích nguyên lý hệ thống Grid System (chuẩn Bootstrap) cho đoạn mã HTML của bạn.
I. BẢNG PHÂN TÍCH LAYOUT QUA 3 KÍCH THƯỚC MÀN HÌNHHệ thống Grid chia màn hình thành 12 cột ảo chiều ngang.
 Dựa vào các class được chỉ định, bố cục của 4 khối Box sẽ thay đổi như sau:Kích thước< 768px (Mobile)768px - 991px (Tablet)≥ 992px (Desktop)Số cột chiếm dụng12 cột mỗi Box(Ăn theo class col-12)6 cột mỗi Box(Ăn theo class col-md-6)3 cột mỗi Box(Ăn theo class col-lg-3)Box layout hình trực quanXếp dọc thành 1 cột(Mỗi hàng chứa 1 Box)Xếp thành lưới 2x2(Mỗi hàng chứa 2 Box)Xếp ngang thành 1 hàng(Hàng chứa đủ cả 4 Box)Sơ đồ bố cục chi tiết┌──────────┐│  Box 1   │├──────────┤│  Box 2   │├──────────┤│  Box 3   │├──────────┤│  Box 4   │└──────────┘┌─────┬─────┐│Box 1│Box 2│├─────┼─────┤│Box 3│Box 4│└─────┴─────┘┌───┬───┬───┬───┐│B1 │B2 │B3 │B4 │└───┴───┴───┴───┘
 
 II. GIẢI THÍCH CÂU HỎI THÊM
 1. col-md-6 nghĩa là gì?col: Viết tắt của Column (Cột).md: Viết tắt của Medium screen breakpoint (Áp dụng cho màn hình kích thước trung bình, cụ thể là từ 768px trở lên).6: Số lượng cột ảo mà phần tử này sẽ chiếm trong tổng số 12 cột của hệ thống Grid ($6/12 = 50\%$ chiều rộng hàng).Ý nghĩa trọn vẹn: Khi màn hình có độ rộng từ 768px trở lên, phần tử này sẽ chiếm chính xác 6 cột trên tổng số 12 cột (tức là rộng bằng nửa màn hình).
Do đó, cần 2 phần tử col-md-6 để lấp đầy 1 hàng ngang.
 2. Tại sao không cần viết col-sm-12?Trong hệ thống Grid của Bootstrap, các class hoạt động theo nguyên lý Mobile-First và Kế thừa hướng lên (Upward Inheritance).Class col-12 không chứa hậu tố kích thước (như sm, md, lg) được hiểu là cấu hình áp dụng cho mốc nhỏ nhất (màn hình X-Small, < 576px).Giá trị này sẽ tự động kế thừa và giữ nguyên cho các màn hình lớn hơn tiếp theo (sm: $\ge 576px$) cho đến khi nó gặp một Media Query khác lớn hơn ghi đè lên nó (ở đây là col-md-6 ở mốc $\ge 768px$).Do đó, ở khoảng màn hình sm (từ 576px đến 767px), các Box đã tự động nhận giá trị rộng 12 cột từ col-12 rồi. Việc viết thêm col-sm-12 là hoàn toàn dư thừa và làm bẩn code.

Câu A2:
1. Giải thích class d-none d-md-blockĐây là sự kết hợp của hai class ẩn/hiển thị (Display utilities) hoạt động theo nguyên lý Mobile-First:d-none: Khai báo ẩn phần tử (display: none) ở kích thước màn hình mặc định nhỏ nhất (Mobile < 768px).d-md-block: Khai báo hiển thị phần tử dưới dạng khối (display: block) kể từ mốc màn hình Medium trở lên ($\ge 768px$).Kết luận trạng thái:Ẩn khi nào: Khi màn hình nhỏ hơn 768px (Điện thoại di động dọc và ngang).Hiển thị khi nào: Khi màn hình có độ rộng từ 768px trở lên (Máy tính bảng, Laptop, Desktop).Ứng dụng thực tế: Thường dùng để ẩn thanh Menu ngang trên điện thoại (để thay bằng nút Hamburger ☰) và hiện lại thanh Menu ngang khi sang màn hình máy tính.
2. Liệt kê và giải thích 5 Spacing Utilities (Margin/Padding)Hệ thống Spacing sử dụng công thức: {thuộc tính}{hướng}-{mức độ}. Trong đó m- là Margin (khoảng cách bên ngoài khối), p- là Padding (khoảng cách đệm bên trong khối). Các mức độ từ 0 - 5 tương ứng với các tỷ lệ quy đổi theo đơn vị rem.mt-3 (Margin Top 3): Thêm khoảng cách trống phía trên phần tử. Mức độ 3 thường tương đương với $1rem = 16px$ (nếu font gốc mặc định là 16px).mb-auto (Margin Bottom Auto): Tự động đẩy khoảng cách phía dưới phần tử ra mức tối đa có thể. Thường dùng trong Flexbox để đẩy các phần tử khác xuống đáy khối (ví dụ: đẩy nút "Mua ngay" xuống đáy thẻ Card sản phẩm dù mô tả dài ngắn khác nhau).px-4 (Padding X 4): Thêm khoảng cách đệm đồng thời vào cả hai bên trái (Left) và phải (Right) bên trong phần tử. Mức độ 4 tương đương với $1.5rem = 24px$.py-0 (Padding Y 0): Triệt tiêu hoàn toàn (bằng 0) khoảng cách đệm ở cả hai phía trên (Top) và dưới (Bottom) bên trong phần tử.ms-2 (Margin Start 2): Thêm khoảng cách bên ngoài ở phía bắt đầu (Start tương đương với bên trái trong ngôn ngữ viết từ trái sang phải như tiếng Việt). Mức độ 2 tương đương với $0.5rem = 8px$.
3. Sự khác nhau giữa .container, .container-fluid, .container-md
Đây là 3 thành phần bao bọc (Wrapper) dùng để giới hạn không gian hiển thị nội dung, điểm khác biệt lớn nhất nằm ở cách chúng co giãn theo các Breakpoints:
Thành phần                      Đặc điểm co giãn chiều rộng (width)                     Ứng dụng thực tế thích hợp

.container                      Co giãn theo từng nấc cố định. Ở mỗi mốc màn hình       Phù hợp làm khung nội dung chuẩn cho hầu hết 
                                (576px, 768px, 992px...), nó sẽ khóa cứng ở một độ      các website truyền thống (như VnExpress, Shopee)
                                rộng tối đa chuẩn (max-width: 540px, 720px, 960px...) 
                                và tự động căn giữa trang.

.container-fluid                Luôn luôn rộng 100% ở mọi kích thước màn hình, bất kể   Luôn luôn rộng 100% ở mọi kích thước màn hình, 
                                bạn đang dùng điện thoại hay màn hình tivi cỡ lớn.      bất kể bạn đang dùng điện thoại hay màn    hình                                                    tivi cỡ lớn.                        
.container-md                   Hỗn hợp (Hybrid): Nó sẽ tràn viền 100% khi ở màn hình   Phù hợp cho các thiết kế muốn nội dung tràn 
                                 nhỏ (Mobile $< 768px$). Nhưng ngay khi đạt từ mốc màn  viền thoáng đãng trên điện thoại nhưng gọn 
                                 hình md trở lên ($\ge 768px$), nó sẽ tự động biến thành gàng, đóng khung trên máy tính.
                                 .container thông thường và khóa cứng theo nấc.



 