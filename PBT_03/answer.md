1. Inline CSS (CSS trực tiếp)
Cách này viết các quy tắc CSS trực tiếp vào thuộc tính style của thẻ HTML.
Ví dụ:
HTML
<h1 style="color: blue; font-size: 20px;">Tiêu đề màu xanh</h1>
Ưu điểm: Nhanh, tiện khi muốn test nhanh một thuộc tính hoặc áp dụng cho duy nhất một phần tử mà không muốn viết thêm code ở nơi khác.
Nhược điểm: Làm code HTML trở nên rối rắm, khó bảo trì. Không thể tái sử dụng định dạng cho các phần tử khác.
Khi nào nên dùng: Khi cần thay đổi kiểu dáng nhanh cho một phần tử đơn lẻ hoặc khi viết Email HTML.
2. Internal CSS (CSS nội bộ)
Sử dụng thẻ <style> đặt bên trong thẻ <head> của file HTML.

Ví dụ:
HTML
<head>
    <style>
        p {
            color: red;
            line-height: 1.5;
        }
    </style>
</head>
Ưu điểm: Quản lý toàn bộ CSS của một trang tại một nơi duy nhất. Không cần tạo file bên ngoài.
Nhược điểm: Chỉ có tác dụng trên đúng file HTML đó. Nếu website có nhiều trang (index, contact, about), bạn sẽ phải copy đoạn code này sang từng trang, gây tốn thời gian và khó cập nhật đồng bộ.
Khi nào nên dùng: Khi bạn làm một trang web đơn lẻ (Landing Page) hoặc trang web có cấu trúc CSS riêng biệt hoàn toàn với phần còn lại của hệ thống.
3. External CSS (CSS bên ngoài)
Viết CSS vào một file riêng biệt (đuôi .css) và nhúng vào HTML qua thẻ <link>.

Ví dụ:
File style.css
CSS
body { background-color: #f4f4f4; }
.content { margin: 20px; }
File index.html:
HTML
        <head>
            <link rel="stylesheet" href="style.css">
        </head>
        ```
Ưu điểm: Cách làm chuyên nghiệp nhất. Giúp code HTML sạch sẽ, dễ bảo trì. Một file CSS có thể dùng cho hàng nghìn trang web khác nhau. Tốc độ tải trang nhanh hơn nhờ cơ chế lưu bộ nhớ đệm (cache).
Nhược điểm: Tốn thêm một yêu cầu HTTP (request) để tải file CSS về (tuy nhiên rủi ro này rất nhỏ so với lợi ích).
Khi nào nên dùng: Luôn luôn nên dùng cho các dự án thực tế và website có nhiều hơn một trang.

Câu hỏi thêm: Cách nào "thắng"?
Nếu cùng một phần tử chịu tác động của cả 3 cách với các giá trị khác nhau, thứ tự ưu tiên (Specificity) sẽ quyết định như sau:
Kết quả: Inline CSS sẽ "thắng" (có mức ưu tiên cao nhất).
Giải thích:
Trình duyệt ưu tiên dựa trên độ cụ thể của bộ chọn và vị trí khai báo:
1.  Inline CSS: Có mức ưu tiên cao nhất vì nó gắn trực tiếp vào phần tử, trình duyệt coi đây là chỉ thị cụ thể nhất.
2.  Internal và External CSS: Hai cách này có mức ưu tiên ngang nhau. Nếu cùng tác động vào 1 phần tử, cái nào được trình duyệt đọc sau cùng (viết thấp hơn trong file HTML) sẽ thắng (quy tắc ghi đè từ trên xuống dưới). 
*Thông thường, thẻ <style> (Internal) hay đặt sau thẻ <link> (External) nên ta hay thấy Internal đè External, nhưng bản chất chúng là bằng vai vế.


Câu A2:
1. h1 → Chọn: <h1>ShopTLU</h1>
2. .price → Chọn: <p class="price">25.990.000đ</p> và <p class="price">45.990.000đ</p>
3.#app header → Chọn: <header class="top-bar dark">...</header> (toàn bộ khối header)
4.nav a:first-child → Chọn: <a href="/" class="active">Home</a>
5. .product.featured h2 → Chọn: <h2>MacBook Pro</h2>
6. article > p → Chọn: Tất cả 4 thẻ <p> nằm trực tiếp trong 2 thẻ <article> (Giá tiền và Mô tả)
7. a[href="/"] → Chọn: <a href="/" class="active">Home</a>
8. .top-bar.dark h1 → Chọn: <h1>ShopTLU</h1>

Câu A3:
Trường hợp 1: content-box (mặc định)
Trong chế độ này, width chỉ tính cho phần nội dung (content). Padding và Border sẽ cộng thêm vào bên ngoài.
Chiều rộng hiển thị (Visible Width): 400 (width) + 20 (left padding) + 20 (right padding) + 5 (left border) + 5 (right border) = 450px
Không gian chiếm trên trang (Total Space): 450 (visible width) + 10 (left margin) + 10 (right margin) = 470px
Trường hợp 2: border-box
Trong chế độ này, width bao gồm cả content, padding và border. Trình duyệt sẽ tự co phần content lại.
Chiều rộng hiển thị (Visible Width): Bằng chính giá trị khai báo = 400px
Kích thước content thực tế: 400 - (20 * 2) padding - (5 * 2) border = 350px
Không gian chiếm trên trang (Total Space): 400 (visible width) + 10 (left margin) + 10 (right margin) = 420px
Trường hợp 3: Margin collapse (Gộp lề)
Khoảng cách giữa box-a và box-b: 40px (Lấy giá trị lớn nhất trong hai margin).
Giải thích tại sao KHÔNG PHẢI 65px: Đây là cơ chế Margin Collapse trong CSS. Khi hai margin dương chạm nhau, trình duyệt sẽ chọn giá trị lớn nhất (40px > 25px) để làm khoảng cách chung nhằm tránh tạo ra những khoảng trống quá lớn giữa các khối.
Nâng cao: Margin âm
Nếu .box-a có margin-bottom: -10px và .box-b có margin-top: 40px:
Khoảng cách = 30px
Quy tắc: Khi có một margin dương và một margin âm, khoảng cách thực tế sẽ là tổng đại số của chúng (40px - 10px = 30px).

Câu A4:
1. Tính Specificity Score (a, b, c)
Để tính điểm ưu tiên, ta chia làm 3 cột:
a (ID selectors): Các selector bắt đầu bằng dấu #.
b (Classes, Attributes, Pseudo-classes): Các selector bắt đầu bằng dấu . hoặc [].
c (Elements, Pseudo-elements): Các thẻ HTML (như p, div, h1).

2. Element sẽ có màu gì? Giải thích
Kết quả: Element sẽ có màu đỏ (Red).
Giải thích: So sánh các điểm số ở trên:
Rule C có điểm (1, 0, 0) cao nhất vì nó chứa một ID selector.
Trong CSS, 1 điểm ở cột a (ID) luôn thắng bất kỳ số lượng điểm nào ở cột b và c. Vì vậy, Rule C (100) > Rule D (11) > Rule B (10) > Rule A (1).

3. Nếu thêm Inline Style màu cam (orange)
Kết quả: Element sẽ có màu cam (Orange).
Giải thích: Inline Style (viết trực tiếp vào thuộc tính style của thẻ HTML) có độ ưu tiên cao hơn tất cả các bộ chọn trong file CSS bên ngoài hoặc trong thẻ <style>. Nó tương đương với mức điểm (1, 0, 0, 0) trong thang đo mở rộng.

4. Nếu Rule A thêm !important
Kết quả: Element sẽ có màu đen (Black).
Giải thích:
!important không phải là một selector, nhưng nó là một "lệnh cưỡng ép" ghi đè mọi quy tắc Specificity thông thường.
Khi có !important, trình duyệt sẽ bỏ qua điểm số (a, b, c) và áp dụng ngay giá trị đó. Ngay cả Inline Style cũng sẽ bị đánh bại bởi một Rule trong file CSS có gắn !important (trừ khi chính Inline Style đó cũng có !important).

Câu B1:
Trong file style.css, có 5 loại Selector sau:
Universal Selector (*): Dùng để reset box-sizing cho toàn bộ trang.
Element Selector (body, header, table): Định dạng trực tiếp các thẻ HTML cơ bản.
Class Selector (.active): Dùng để làm nổi bật liên kết của trang hiện hành.
ID Selector (#toi, #lien-he): Định dạng cụ thể cho các khối nội dung độc nhất.
Pseudo-class Selector (:hover, :nth-child(even)): Tạo hiệu ứng tương tác cho bảng và menu điều hướng.

Câu B3:
Kết quả hiển thị:
Màu cuối cùng: Màu tím (Purple).
Tại sao? Vì selector #demo.text có điểm specificity cao nhất (1, 1, 0). Trong CSS, điểm ở cột ID (a) quan trọng hơn cột Class (b), và cột Class quan trọng hơn cột Element (c). Do có 1 ID và 1 Class nên nó đánh bại tất cả các rules còn lại.

-Thay đổi thứ tự Rules
Kết quả có đổi không? KHÔNG.
Giải thích: Specificity là quy tắc ưu tiên dựa trên "trọng lượng" của bộ chọn. Trình duyệt chỉ xét đến thứ tự viết trước/sau (quy tắc Cascade) khi hai bộ chọn có điểm specificity bằng nhau. Ví dụ: Nếu bạn đổi chỗ .text và [class~="highlight"] (cùng điểm 0,1,0), màu sắc sẽ thay đổi. Nhưng với các bộ chọn khác điểm nhau, bộ chọn điểm cao hơn luôn thắng dù nằm ở bất kỳ đâu trong file.


Phần C:
Câu C1:
1. Tính toán chiều rộng thực tế (content-box)
Mặc định, trình duyệt sử dụng chế độ box-sizing: content-box. Với chế độ này, width chỉ tính cho phần nội dung, bạn phải cộng thêm padding và border để ra tổng chiều rộng mà phần tử chiếm dụng trên màn hình.
Sidebar: 300px (width) + 20px (padding trái) + 20px (padding phải) + 1px (border trái) + 1px (border phải) = 342px.
Content: 660px (width) + 30px (padding trái) + 30px (padding phải) + 1px (border trái) + 1px (border phải) = 722px.
2. Giải thích tại sao layout bị vỡ
Tổng chiều rộng thực tế của cả hai khối là:
342px (Sidebar) + 722px (Content) = 1064px.
Trong khi đó, thẻ cha .container chỉ rộng 960px. Vì tổng kích thước của hai khối con (1064px) lớn hơn kích thước thẻ cha (960px), nên không đủ chỗ để chúng nằm cùng một hàng. Do đó, phần tử content bị đẩy xuống dòng dưới.
3. Hai cách sửa lỗi
Cách 1: Sử dụng box-sizing: border-box (Khuyên dùng)
Cách này giúp thuộc tính width bao gồm luôn cả padding và border, bạn không cần làm toán trừ phức tạp.
Sidebar: width: 300px;
Content: width: 660px;
(Tổng 960px vừa khít container).
Cách 2: Tính toán thủ công (Giữ nguyên content-box)
Phải trừ đi phần padding và border khỏi giá trị width ban đầu.
Sidebar mới: 300px - 40px (padding) - 2px (border) = 258px.
Content mới: 660px - 60px (padding) - 2px (border) = 598px.

Câu C2:
1. "Sản phẩm A" (h2)
Font-size: 20px
Quá trình: Trình duyệt tìm thấy quy tắc .card .title có độ ưu tiên (Specificity) là (0, 2, 0). Điểm này cao hơn các giá trị kế thừa từ .container (0, 1, 0) hay body (0, 0, 1). Do đó, kích thước 20px được áp dụng.
Color: green
Quá trình: Có một cuộc tranh chấp giữa #featured .title (điểm cực cao: 1, 1, 0) và .highlight (điểm thấp hơn: 0, 1, 0). Tuy nhiên, quy tắc .highlight có gắn từ khóa !important. Trong CSS Cascade, !important là cấp độ ưu tiên cao nhất, ghi đè lên tất cả các thang đo điểm số thông thường. Vì vậy, màu xanh lá cây thắng.
2. "Mô tả sản phẩm" (p nằm trong card featured)
Color: blue
Quá trình: Thẻ p này không được gán màu trực tiếp bởi bất kỳ Selector nào, nhưng nó có quy tắc .card p { color: inherit; }.
Giải thích: Thuộc tính inherit bắt buộc phần tử phải lấy giá trị từ thẻ cha trực tiếp của nó. Thẻ cha ở đây là <div class="card" id="featured">. Thẻ này nhận màu blue từ quy tắc .card { color: blue; }. Kết quả là đoạn văn thừa hưởng màu xanh dương.
3. "Sản phẩm B" (h2)
Font-size: 20px
Quá trình: Tương tự như sản phẩm A, thẻ h2 này khớp với Selector .card .title. Vì điểm Specificity (0, 2, 0) của quy tắc này mạnh hơn các giá trị bao quanh, nó áp dụng mức 20px.
Color: blue
Quá trình: Thẻ h2 này không có class .highlight và cũng không nằm trong ID #featured. Do đó, nó không có quy tắc màu trực tiếp nào. Theo cơ chế kế thừa mặc định của các thuộc tính văn bản, nó lấy màu từ thẻ cha gần nhất là .card. Vì .card có màu blue, nên tiêu đề này cũng hiện màu xanh dương.
4. "Mô tả sản phẩm B" (p.highlight)
Color: green
Quá trình: Ở đây có sự tranh chấp giữa:
Tính kế thừa từ thẻ cha .card (màu blue).
Quy tắc .card p { color: inherit; } (cũng trỏ về màu blue).
Quy tắc .highlight { color: green !important; } (nhắm trực tiếp vào chính nó).
Giải thích: Quy tắc nhắm trực tiếp vào phần tử (.highlight) luôn thắng các quy tắc kế thừa. Hơn nữa, sự hiện diện của !important đảm bảo màu xanh lá cây sẽ ghi đè mọi thứ khác.