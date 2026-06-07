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


Phần C:
Câu C1:
I. QUY TRÌNH ĐỔI MÀU $primary TRONG BOOTSTRAP
Để thay đổi màu thương hiệu $primary một cách đồng bộ từ màu xanh mặc định sang màu #E63946, chúng ta bắt buộc phải cấu hình lại mã nguồn Sass của Bootstrap trước khi nó được biên dịch ra CSS.

1. Các công cụ cần chuẩn bị
Môi trường Node.js & NPM để quản lý và cài đặt thư viện Bootstrap gốc.

Trình biên dịch Sass (Dart Sass): Cài đặt qua dòng lệnh CLI bằng NPM (npm install -g sass) hoặc sử dụng extension như Live Sass Compiler trên VS Code.

Thư viện Bootstrap gốc (Source code SCSS): Được cài đặt thông qua câu lệnh npm install bootstrap.

2. Các file cần chỉnh sửa và tạo mới
Quy trình đúng chuẩn không bao giờ được phép sửa trực tiếp vào file nằm trong thư mục node_modules/bootstrap. Thay vào đó, bạn cần tạo các file tùy biến riêng:

Bước 1: Tạo một file scss chính của dự án, ví dụ đặt tên là custom.scss.

Bước 2: Khai báo đè (override) biến màu $primary bằng mã màu mới TRƯỚC TỪ KHÓA IMPORT mã nguồn Bootstrap.

Cấu trúc file custom.scss sẽ được viết như sau:

SCSS
// 1. Khai báo biến màu mới của bạn (Viết trước để ghi đè giá trị mặc định)
$primary: #E63946;

// 2. Tùy chọn bổ sung: Thay đổi bản đồ màu (Color map) nếu cần
// $theme-colors: (
//   "primary": $primary
// );

// 3. Import toàn bộ thư viện Bootstrap gốc vào để nhận cấu hình mới
@import "../node_modules/bootstrap/scss/bootstrap";
Bước 3: Chạy lệnh biên dịch file custom.scss thành file custom.css để nhúng vào HTML:

Bash
sass custom.scss custom.css
II. TẠI SAO KHÔNG NÊN OVERRIDE TRỰC TIẾP .btn-primary { background: red; }?
Việc ghi đè trực tiếp bằng CSS thuần (.btn-primary { background: red; }) là một lỗi tư duy thiết kế hệ thống nghiêm trọng (Anti-pattern). Chúng ta nên dùng SASS Variables vì 3 lý do cốt lõi sau:

1. Tính đồng bộ toàn hệ thống (System-wide Consistency)
Trong Bootstrap, biến $primary không chỉ quy định màu nền của mỗi nút bấm .btn-primary. Nó còn được Framework sử dụng tự động để tính toán và tạo ra hàng trăm Class khác, bao gồm:

Màu chữ liên kết (.text-primary)

Màu nền thông thường (.bg-primary)

Màu viền đường kẻ (.border-primary)

Màu trạng thái kích hoạt của thẻ Nav, Pagination, Progress Bar, Form Checkbox, v.v.

Nếu bạn chỉ override .btn-primary, nút bấm của bạn sẽ biến thành màu đỏ, nhưng các thành phần như viền input, liên kết văn bản, màu thẻ active... vẫn sẽ là màu xanh dương mặc định. Giao diện trang web sẽ bị vá víu, rời rạc và mất đồng bộ thương hiệu.

2. Đồng bộ các trạng thái tương tác động (Hover, Active, Focus, Disabled)
Khi bạn đổi màu $primary qua biến Sass, Bootstrap sẽ tự động chạy các hàm xử lý màu (như shade-color() hay tint-color()) để tự sinh ra các gam màu phái sinh chuẩn xác cho nút bấm khi di chuột vào hoặc nhấn giữ.

Nếu bạn dùng CSS thuần, bạn sẽ phải viết thủ công thêm rất nhiều dòng code rườm rà như:

CSS
.btn-primary { background-color: red; border-color: red; }
.btn-primary:hover { background-color: darkred; }
.btn-primary:focus { box-shadow: 0 0 0 0.25rem rgba(255, 0, 0, 0.5); }
.btn-primary:disabled { background-color: lightpink; }
Cách viết thủ công này cực kỳ tốn thời gian, dễ sót và làm tăng dung lượng file CSS một cách không cần thiết.

3. Dễ dàng bảo trì và mở rộng (Maintainability)
Nếu sau này doanh nghiệp thay đổi bộ nhận diện thương hiệu từ màu đỏ #E63946 sang màu tím hoặc xanh lá, người viết bằng Sass chỉ cần thay đổi độc nhất 1 dòng code ở vị trí khai báo biến ban đầu rồi lưu lại là xong.

Ngược lại, người lạm dụng ghi đè CSS thuần sẽ phải dùng tính năng Tìm & Thay thế (Find & Replace) trên toàn bộ dự án để sửa hàng loạt class thủ công, dẫn tới nguy cơ cao làm lỗi/vỡ cấu trúc giao diện ở những phân đoạn khác.

 