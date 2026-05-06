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