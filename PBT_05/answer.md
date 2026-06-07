Phần A:
Câu A1:
1. Thẻ <meta name="viewport"> chuẩn và giải thích thuộc tính
Đoạn mã khai báo thẻ viewport chuẩn quốc tế được khuyên dùng bởi W3C:

HTML
<meta name="viewport" content="width=device-width, initial-scale=1.0">
Giải thích từng thuộc tính bên trong:

name="viewport": Định nghĩa cho trình duyệt biết rằng thẻ meta này dùng để thiết lập vùng hiển thị (viewport) của trang web trên các thiết bị.

content="...": Chứa các tham số cấu hình cụ thể cho viewport.

width=device-width: Ép chiều rộng của trang web phải bằng chính xác chiều rộng màn hình của thiết bị (ví dụ: màn hình iPhone 15 có chiều rộng là 393px thì trang web sẽ tự đặt chiều rộng hiển thị là 393px thay vì tự động zoom nhỏ).

initial-scale=1.0: Thiết lập mức độ thu phóng (zoom) ban đầu khi trang web vừa được tải xong là 1:1 (không phóng to, không thu nhỏ).

2. Nếu THIẾU thẻ này, iPhone sẽ hiển thị trang web như thế nào?
Nếu thiếu thẻ <meta name="viewport">, các thiết bị di động như iPhone sẽ mặc định hiểu rằng trang web này chỉ được thiết kế dành cho máy tính để bàn (Desktop). Theo cơ chế hiển thị mặc định (Chương 13 - Quy chuẩn trình duyệt di động):

Trình duyệt Safari trên iPhone sẽ giả lập một vùng hiển thị lớn có chiều rộng khoảng 980px (hoặc lớn hơn tùy đời máy).

Sau đó, nó sẽ tự động thu nhỏ toàn bộ trang web lại (Scale down / Zoom out) để vừa khít với màn hình nhỏ của điện thoại.

Hệ quả: Chữ viết (text) sẽ trở nên siêu nhỏ như con kiến, các nút bấm tí hon và người dùng buộc phải dùng hai ngón tay để phóng to (pinch-to-zoom) mới có thể đọc được nội dung hoặc nhấn vào các liên kết.

3. Phân biệt Mobile-First và Desktop-First
Đây là hai tư duy tiếp cận thiết kế responsive trái ngược nhau:

Mobile-First (Ưu tiên di động): Bạn viết CSS cơ bản cho màn hình nhỏ (Mobile) trước, không dùng Media Queries. Sau đó, bạn dùng Media Queries để thêm thắt hoặc ghi đè thuộc tính khi màn hình mở rộng dần lên (Tablet, Desktop). Cách này sử dụng điều kiện min-width (chiều rộng tối thiểu).

Desktop-First (Ưu tiên máy tính): Bạn viết CSS cơ bản cho màn hình lớn (Desktop) trước. Sau đó, bạn dùng Media Queries để co nhỏ hoặc ẩn bớt các thành phần khi màn hình thu hẹp dần về thiết bị di động. Cách này sử dụng điều kiện max-width (chiều rộng tối đa).

Ví dụ CSS với breakpoint 768px:
Cách 1: Mobile-First (Sử dụng min-width)

CSS
/* CSS mặc định áp dụng cho Mobile (Màn hình từ 0px đến 767px) */
body {
    background-color: lightblue; /* Mobile nền xanh dương */
    font-size: 14px;
}
.sidebar {
    display: none; /* Mobile ẩn sidebar để đỡ chật */
}

/* Áp dụng cho các màn hình CÓ CHIỀU RỘNG TỪ 768PX TRỞ LÊN (Tablet, Desktop) */
@media (min-width: 768px) {
    body {
        background-color: lightcoral; /* Lên màn hình lớn đổi sang nền đỏ nhạt */
        font-size: 16px;
    }
    .sidebar {
        display: block; /* Màn hình lớn có chỗ trống nên hiện sidebar */
    }
}
Cách 2: Desktop-First (Sử dụng max-width)

CSS
/* CSS mặc định áp dụng cho Desktop (Màn hình lớn từ 768px trở lên vô hạn) */
body {
    background-color: lightcoral; /* Desktop nền đỏ nhạt */
    font-size: 16px;
}
.sidebar {
    display: block; /* Desktop hiển thị sidebar */
}

/* Áp dụng cho các màn hình CÓ CHIỀU RỘNG TỪ 768PX TRỞ XUỐNG (Mobile) */
@media (max-width: 768px) {
    body {
        background-color: lightblue; /* Xuống mobile đổi sang nền xanh dương */
        font-size: 14px;
    }
    .sidebar {
        display: none; /* Xuống mobile ẩn sidebar */
    }
}
4. Tại sao Mobile-First được khuyên dùng mãnh liệt?
Hiện nay, Mobile-First đã trở thành tiêu chuẩn bắt buộc trong ngành thiết kế web vì 3 lý do cốt lõi sau:

Tối ưu hóa hiệu năng và tốc độ tải trang trên di động: Thiết bị di động thường có cấu hình phần cứng yếu hơn máy tính và dùng mạng 3G/4G/5G kém ổn định hơn. Viết code Mobile-First giúp trình duyệt điện thoại đọc và thực thi các đoạn code CSS cơ bản, gọn nhẹ ngay lập tức mà không phải tốn tài nguyên xử lý hay tải các hiệu ứng phức tạp (như hover, ảnh nặng, video nền) của Desktop trước rồi mới ẩn đi.

Tập trung vào nội dung cốt lõi (Content Strategy): Thiết kế trên không gian màn hình nhỏ buộc lập trình viên và nhà thiết kế phải giữ lại những gì quan trọng nhất, lược bỏ các thành phần rác rưởi, rườm rà. Khi mở rộng lên Desktop, trang web sẽ có bố cục thoáng đãng và mạch lạc hơn.

Tốt cho SEO (Điểm xếp hạng Google): Từ lâu Google đã áp dụng thuật toán Mobile-First Indexing. Nghĩa là Google sẽ dùng giao diện di động của trang web để thu thập dữ liệu và tính điểm xếp hạng tìm kiếm. Một trang web tối ưu Mobile-First tốt sẽ có lợi thế vượt trội về thứ hạng trên Google Search.

Câu A2:
1. Bảng Breakpoints chuẩn theo Bootstrap 5
Breakpoint          Kích thước Pixel        Thiết bị đại diện                   Số cột hiển thị cho lưới sản phẩm (Gợi ý chuẩn UI/UX)
X-Small (<576px)    Dưới 576px              Điện thoại di động dọc              1 cột hoặc 2 cột nhỏ
Small (sm)          Từ 576px trở lên        máy tính bảng cỡ rất nhỏ            2 cột
Medium (md)         Từ 768px trở lên        Máy tính bảng hướng dọc             2 cột hoặc 3 cột
Large (lg)          Từ 992px trở lên        Máy tính bảng hướng ngang           3 cột hoặc 4 cột
                                            (iPad Pro 12.9")
X-Large (xl)        Từ 1200px trở lên       Màn hình máy tính xách tay          4 cột
                                            thông thường (MacBook 13"/14"/16")  4 cột, 5 cột hoặc 6 cột
XX-Large (xxl)      Từ 1400px trở lên       Màn hình máy tính để bàn

2. Ví dụ minh họa code thực tế áp dụng Breakpoints
Dưới đây là cách bạn áp dụng các breakpoint trên vào mã nguồn CSS bằng phương pháp Mobile-First sử dụng CSS Grid để điều khiển số cột của lưới sản phẩm tự động theo đúng bảng quy chuẩn trên:CSS/* --- TRẠNG THÁI MẶC ĐỊNH (X-Small < 576px) --- */
.product-grid {
    display: grid;
    grid-template-columns: repeat(1, 1fr); /* 1 cột trên điện thoại dọc */
    gap: 15px;
}

/* --- BREAKPOINT 1: Small Devices (sm: >= 576px) --- */
@media (min-width: 576px) {
    .product-grid {
        grid-template-columns: repeat(2, 1fr); /* Chuyển thành 2 cột trên điện thoại ngang */
    }
}

/* --- BREAKPOINT 2: Medium Devices (md: >= 768px) --- */
@media (min-width: 768px) {
    .product-grid {
        grid-template-columns: repeat(3, 1fr); /* Chuyển thành 3 cột trên iPad/Tablet dọc */
    }
}

/* --- BREAKPOINT 3: Large / XL Devices (lg/xl: >= 992px) --- */
@media (min-width: 992px) {
    .product-grid {
        grid-template-columns: repeat(4, 1fr); /* Chuyển thành 4 cột ổn định trên Laptop/Desktop */
    }
}

/* --- BREAKPOINT 4: XX-Large Devices (xxl: >= 1400px) --- */
@media (min-width: 1400px) {
    .product-grid {
        grid-template-columns: repeat(6, 1fr); /* Chuyển hẳn thành 6 cột trên màn hình PC lớn để không bị trống trang */
    }
}
Tại sao nên nhớ các mốc 576px, 768px, 992px, 1200px?Đây là các con số được đúc kết qua hàng chục năm phát triển web dựa trên thông số phần cứng thực tế của hàng nghìn dòng thiết bị của Apple, Samsung, Dell, LG... Việc tuân thủ theo các breakpoint tiêu chuẩn này giúp giao diện của bạn không bao giờ bị lỗi hiển thị hay tràn viền (horizontal scrollbar) khi người dùng đổi thiết bị truy cập.

Câu A3:
Chiều rộng màn hình	    .container width    
375px (iPhone SE)	    100%
600px	                540px
800px	                720px
1000px	                960px
1400px	                1140px

Câu A4:
1. Giải thích 4 tính năng chính của SCSS kèm ví dụa. Variables (Biến số)Giải thích: Cho phép bạn lưu trữ các giá trị được sử dụng lặp đi lặp lại nhiều lần trong toàn bộ dự án (như mã màu, font chữ, kích thước padding, độ rộng border) vào một cái tên gợi nhớ bắt đầu bằng ký tự $. Khi muốn thay đổi giao diện (ví dụ đổi màu chủ đạo của thương hiệu từ Xanh sang Đỏ), bạn chỉ cần sửa giá trị ở một nơi duy nhất thay vì phải đi tìm và sửa hàng trăm dòng CSS.Ví dụ SCSS:SCSS$primary-color: #3498db;
$base-padding: 15px;

.button {
    background-color: $primary-color;
    padding: $base-padding;
}
.nav-item {
    color: $primary-color;
}
b. Nesting (Viết CSS lồng nhau)Giải thích: Tính năng này cho phép bạn viết các bộ chọn CSS lồng vào bên trong nhau, mô phỏng lại chính xác cấu trúc hình cây phân cấp của các thẻ HTML. Nó giúp mã nguồn gọn gàng hơn, dễ đọc, dễ quản lý cấu trúc và tránh việc phải viết đi viết lại tên của class cha.Ví dụ SCSS:SCSS.navbar {
    background: #fff;
    padding: 10px;

    .menu-list {
        display: flex;
        list-style: none;

        li {
            margin-right: 20px;

            a {
                text-decoration: none;
                /* Ký tự & đại diện cho chính phần tử cha (thẻ a) */
                &:hover { color: red; } 
            }
        }
    }
}
c. Mixins (@mixin và @include)Giải thích: Mixin giống như một "hàm" (function) trong lập trình. Bạn dùng @mixin để định nghĩa ra một nhóm các thuộc tính CSS thường xuyên đi kèm với nhau (có thể truyền vào các tham số/biến số thay đổi linh hoạt). Sau đó, ở bất kỳ class nào cần dùng lại đoạn CSS này, bạn chỉ cần dùng cú pháp @include để gọi nó ra.Ví dụ SCSS:SCSS/* Định nghĩa một mixin để căn giữa tuyệt đối bằng Flexbox */
@mixin center-flex($direction: row) {
    display: flex;
    flex-direction: $direction;
    justify-content: center;
    align-items: center;
}

/* Sử dụng mixin */
.hero-container {
    @include center-flex(column); /* Truyền tham số hướng dọc */
    height: 100vh;
}
.icon-wrapper {
    @include center-flex(); /* Không truyền thì lấy mặc định là row */
}
d. @extend / Inheritance (Kế thừa)Giải thích: Cho phép một bộ chọn class chia sẻ và sử dụng chung lại toàn bộ các thuộc tính CSS đã được định nghĩa ở một class khác. Điểm khác biệt lớn nhất của @extend so với Mixin là trong file CSS đầu ra sau khi biên dịch, các class dùng chung sẽ được gom lại và viết chung bằng dấu phẩy (comma-separated), giúp file CSS thành phẩm tối ưu dung lượng và không bị trùng lặp code.Ví dụ SCSS:SCSS/* Tạo một class gốc (base) làm chuẩn */
.message-box {
    border: 1px solid #ccc;
    padding: 10px;
    border-radius: 4px;
    color: #333;
}

/* Kế thừa lại class gốc và bổ sung thuộc tính riêng biệt */
.success-box {
    @extend .message-box;
    border-color: green;
    background-color: #e6ffe6;
}

.error-box {
    @extend .message-box;
    border-color: red;
    background-color: #ffe6e6;
}
2. Tại sao trình duyệt KHÔNG đọc được file .scss?Trình duyệt web (như Google Chrome, Safari, Microsoft Edge, Firefox) được lập trình để chỉ hiểu và thông dịch duy nhất một bộ quy chuẩn ngôn ngữ định dạng giao diện tĩnh nguyên bản, đó là CSS tiêu chuẩn (Vanilla CSS).

File .scss chứa các cú pháp mở rộng mang tư duy lập trình như biến số ($), hàm lồng nhau, vòng lặp, kế thừa... Trình duyệt không có bộ máy phân tích dữ liệu (parser) cho những cú pháp này. Nếu bạn liên kết trực tiếp một file .scss vào thẻ <link href="style.scss"> trong HTML, trình duyệt sẽ hoàn toàn bỏ qua và không áp dụng bất kỳ giao diện nào cho trang web của bạn.

3. Cần bước gì để chuyển đổi SCSS --> CSS?
Để chuyển đổi từ SCSS sang CSS, bạn bắt buộc phải trải qua một bước gọi là Biên dịch (Compilation) bằng một công cụ tiền xử lý (Pre-processor compiler). Công cụ này sẽ đọc hiểu file cấu trúc .scss của bạn, tính toán các biến số, giải nén các hàm lồng nhau, gộp các class kế thừa rồi "phiên dịch" nó ra thành một file .css thuần túy.
Các phương pháp và công cụ phổ biến để thực hiện bước biên dịch này bao gồm:
-Sử dụng Extension trên VS Code (Đơn giản nhất cho người mới bắt đầu): Bạn cài đặt extension tên là Live Sass Compiler. Sau khi bật tính năng "Watch Sass", mỗi lần bạn nhấn Lưu (Save) file .scss, công cụ này sẽ tự động chạy ngầm và tạo ra một file .css song song nằm ngay bên cạnh để bạn nhúng vào file HTML.
-Sử dụng công cụ dòng lệnh (Command Line Interface - CLI): Cài đặt gói sass thông qua Node.js (NPM). Bạn chạy câu lệnh trong cửa sổ Terminal:Bashsass style.scss style.css --watch
(Lệnh này có nghĩa là: Hãy liên tục theo dõi file style.scss, nếu có thay đổi gì thì tự động biên dịch và cập nhật đè vào file style.css ngay lập tức).
-Sử dụng các công cụ Build Tools mạnh mẽ trong dự án lớn: Các lập trình viên chuyên nghiệp thường tích hợp bước biên dịch này vào các hệ thống tự động hóa như Vite, Webpack, hoặc Gulp để vừa biên dịch vừa tự động nén nhỏ dung lượng file CSS (Minify) trước khi tải lên máy chủ.

Phần B:
Câu B3:
# Nhật Ký Biên Dịch Dự Án SCSS (Refactor Bài B3)

## 1. Công cụ sử dụng
Dự án sử dụng trình biên dịch **Dart Sass** chính thức được khuyến nghị bởi core team Sass (thông qua môi trường cài đặt Node.js/NPM hoặc Extension).

## 2. Các câu lệnh biên dịch thực tế

### Cách 1: Sử dụng Command Line (CLI) trực tiếp trong Terminal
Để biên dịch file `scss/style.scss` thành file `style.css` thông thường bên ngoài, chạy lệnh:
"```"bash
sass scss/style.scss style.css

Phần C:
Câu C2:
I. WIREFRAME (SƠ ĐỒ BỐ CỤC) CHO 3 KÍCH THƯỚC1. Giao diện Mobile ($< 768px$)Những gì bị ẩn: Ẩn bớt 3 ảnh món ăn ít hấp dẫn nhất (chỉ giữ lại Grid 3 ảnh thay vì 6 ảnh để giảm tải dung lượng và độ dài cuộn trang). Ẩn bớt bản đồ trực quan hoặc thu nhỏ lại thành một nút bấm "Xem bản đồ đường đi" dẫn link ra ứng dụng Google Maps.Vị trí Form đặt bàn: Nằm ở vị trí trung tâm, xếp dọc 1 cột ngay dưới Grid ảnh món ăn để kích thích hành động chuyển đổi của khách hàng.Plaintext┌───────────────────────────────────────────┐
│ HEADER (Logo / Nút gọi Hotline )       │
├───────────────────────────────────────────┤
│                                           │
│ HERO IMAGE (Ảnh không gian nhà hàng)       │
│                                           │
├───────────────────────────────────────────┤
│ GRID 3 ẢNH MÓN ĂN (Xếp dọc 1 cột)         │
│ [Ảnh 1]                                   │
│ [Ảnh 2]                                   │
│ [Ảnh 3]                                   │
├───────────────────────────────────────────┤
│ FORM ĐẶT BÀN (Các ô Input xếp dọc 1 cột)  │
│ [Ngày / Giờ / Số người / Ghi chú]         │
│ [NÚT ĐẶT BÀN NGAY]                        │
├───────────────────────────────────────────┤
│ BẢN ĐỒ GOOGLE MAPS (Full width nhỏ)       │
├───────────────────────────────────────────┤
│ FOOTER                                    │
└───────────────────────────────────────────┘
2. Giao diện Tablet ($768px - 1023px$)Grid ảnh mấy cột: Chuyển sang cấu trúc lưới 2 cột hiển thị đầy đủ 6 món ăn (mỗi hàng 2 ảnh x 3 hàng).Vị trí Bản đồ: Bản đồ được đẩy xuống góc cuối trang, nằm trải dài toàn màn hình (Full width) ngay phía trên Footer để người dùng dễ quan sát trên màn hình máy tính bảng.Plaintext┌───────────────────────────────────────────┐
│ HEADER (Logo trái ───────────────── Hotline phải) │
├───────────────────────────────────────────┤
│               HERO IMAGE                  │
├───────────────────────────────────────────┤
│ GRID MÓN ĂN (2 Cột x 3 Hàng)              │
│ ┌───────────────────┬───────────────────┐ │
│ │      [Ảnh 1]      │      [Ảnh 2]      │ │
│ ├───────────────────┼───────────────────┤ │
│ │      [Ảnh 3]      │      [Ảnh 4]      │ │
│ ├───────────────────┼───────────────────┤ │
│ │      [Ảnh 5]      │      [Ảnh 6]      │ │
│ └───────────────────┴───────────────────┘ │
├───────────────────────────────────────────┤
│ FORM ĐẶT BÀN (Chia đôi: 2 cột input)      │
├───────────────────────────────────────────┤
│ BẢN ĐỒ GOOGLE MAPS (Trải ngang)            │
├───────────────────────────────────────────┤
│ FOOTER                                    │
└───────────────────────────────────────────┘
3. Giao diện Desktop ($\ge 1024px$)Layout bao nhiêu cột: Layout chính chuyển đổi thành 3 cột lớn toàn trang (Tận dụng cơ chế grid-template-areas).Sidebar có không: Có. Sidebar bên phải đóng vai trò là tổ hợp cố định (Sticky Sidebar) chứa Form đặt bàn và Bản đồ thu nhỏ, giúp khách hàng cuộn xem ảnh không gian/món ăn ở bên trái mà form đặt bàn vẫn luôn nằm trong tầm mắt.Plaintext┌───────────────────────────────────────────────────────────────────────────┐
│ HEADER (Thanh điều hướng rộng + Hotline)                                  │
├───────────────────────────────────────────────────────────────────────────┤
│ HERO IMAGE (Ảnh Panorama góc rộng)                                        │
├──────────────────────────────────────────────────────┬────────────────────┤
│ GRID MÓN ĂN CHÍNH (Chiếm 2 cột bên trái)              │ SIDEBAR CỐ ĐỊNH    │
│ ┌─────────────────────────┬─────────────────────────┐ │ (Chiếm 1 cột phải) │
│ │         [Ảnh 1]         │         [Ảnh 2]         │ │                    │
│ ├─────────────────────────┼─────────────────────────┤ │ ┌────────────────┐ │
│ │         [Ảnh 3]         │         [Ảnh 4]         │ │ │ FORM ĐẶT BÀN   │ │
│ ├─────────────────────────┼─────────────────────────┤ │ │ (Gom gọn gàng) │ │
│ │         [Ảnh 5]         │         [Ảnh 6]         │ │ └────────────────┘ │
│ └─────────────────────────┴─────────────────────────┘ │ ┌────────────────┐ │
│                                                       │ │ BẢN ĐỒ MINI    │ │
│                                                       │ │ GOOGLE MAPS    │ │
│                                                       │ └────────────────┘ │
├──────────────────────────────────────────────────────┴────────────────────┤
│ FOOTER                                                                    │
└───────────────────────────────────────────────────────────────────────────┘
II. CSS SKELETON LAYOUT (MOBILE-FIRST)Dưới đây là cấu trúc CSS Layout thuần túy ứng dụng cấu trúc CSS Grid + Template Areas giúp dịch chuyển vị trí các thành phần cực kỳ mượt mà giữa các thiết bị mà không cần sửa HTML.1. Cấu trúc HTML KhungHTML<div class="restaurant-layout">
    <header class="header">Header</header>
    <section class="hero">Hero Image</section>
    <main class="menu-grid">Grid 6 Ảnh Món Ăn</main>
    <aside class="booking-form">Form Đặt Bàn</aside>
    <div class="map">Bản đồ Google Maps</div>
    <footer class="footer">Footer</footer>
</div>
2. Mã CSS Layout SkeletonCSS/* ==========================================================================
   1. GIAO DIỆN MẶC ĐỊNH CHO MOBILE (< 768px) - TRIỂN KHAI 1 CỘT DỌC
   ========================================================================== */
.restaurant-layout {
    display: grid;
    /* Định nghĩa dòng chảy xếp chồng từ trên xuống dưới */
    grid-template-areas: 
        "header"
        "hero"
        "menu"
        "form"
        "map"
        "footer";
    grid-template-columns: 1fr;
    gap: 15px;
    padding: 10px;
}

/* Áp tên vùng vào các class */
.header       { grid-area: header; }
.hero         { grid-area: hero; height: 40vh; }
.menu-grid    { grid-area: menu; display: grid; grid-template-columns: 1fr; gap: 10px; } 
.booking-form { grid-area: form; }
.map          { grid-area: map; height: 250px; }
.footer       { grid-area: footer; }


/* ==========================================================================
   2. BREAKPOINT TABLET (>= 768px) - NÂNG CẤP LƯỚI MÓN ĂN VÀ KHÔNG GIAN
   ========================================================================== */
@media (min-width: 768px) {
    .restaurant-layout {
        gap: 25px;
        padding: 20px;
    }

    /* Đổi Grid món ăn thành 2 cột trên Máy tính bảng */
    .menu-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}


/* ==========================================================================
   3. BREAKPOINT DESKTOP (>= 1024px) - TÁI CẤU TRÚC SANG 3 CỘT LAYOUT VÀ SIDEBAR
   ========================================================================== */
@media (min-width: 1024px) {
    .restaurant-layout {
        grid-template-columns: repeat(3, 1fr); /* Chia tổng không gian làm 3 cột bằng nhau */
        
        /* Tái định hình sơ đồ: Đẩy Form và Map sang cột 3 bên phải làm Sidebar cố định */
        grid-template-areas: 
            "header header header"
            "hero   hero   hero"
            "menu   menu   form"
            "menu   menu   map"
            "footer footer footer";
        gap: 30px;
        max-width: 1280px;
        margin: 0 auto;
    }

    /* Đổi Grid món ăn thành 2 cột lớn chiếm trọn vùng không gian "menu" (2/3 chiều rộng trang) */
    .menu-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    /* Tạo hiệu ứng dính (Sticky) cho Sidebar chứa Form đặt bàn khi cuộn chuột */
    .booking-form {
        position: sticky;
        top: 20px;
        align-self: start;
    }
}
