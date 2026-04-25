Phần A:
Câu A1 (5đ) — HTTP & Browser; Đọc chương 01 (01_introduction_html_universe.md)
1. Khi bạn gõ https://shopee.vn vào trình duyệt và nhấn Enter, hãy liệt kê đúng thứ tự ít nhất 5 bước xảy ra (từ DNS lookup đến render):
B1:DNS lookup
B2:HTTP request
B3:HTTP response
B4:Tải tài nguyên phụ
B5:Render trang
2. Trong DevTools của Chrome, tab Network cho thấy thông tin gì? Hãy mở một trang web bất kỳ, chụp screenshot tab Network và đánh dấu (vẽ mũi tên/khoanh tròn) vào:
Status Code của request đầu tiên
Tổng thời gian load trang
Một request trả về file CSS
-Tab Network hiển thị toàn bộ các request mà trình duyệt gửi khi tải trang bao gồm
(HTML, CSS, JavaScript, hình ảnh, font, v.v.)

Câu A2 (5đ) — Semantic HTML; Đọc chương 4
Trang web trên bị Google đánh giá điểm SEO thấp vì nó lạm dụng quá nhiều thẻ <div>, không sử dụng các thẻ semantic.
Có 5 lỗi dưới đây: 
1. Không sử dụng thẻ cấu trúc ngữ nghĩa (Semantic tags) cho các vùng của trang:
-Sử dụng <div class="header">, <div class="main">, <div class="footer"> là sai chuẩn HTML5. Cần sử dụng các thẻ <header>, <main>, và <footer> để Google phân vùng trang web dễ dàng.
2. Thiếu thẻ điều hướng <nav> và sai cấu trúc danh sách:
-Menu hiện tại đang dùng các thẻ <div> lồng nhau. Để tối ưu SEO, các liên kết điều hướng nội bộ phải được đặt trong thẻ <nav>, và thông thường nên được cấu trúc bằng thẻ danh sách <ul> và <li>.
3. Không sử dụng thẻ Tiêu đề (Heading tags <h1> - <h6>):
-Tên sản phẩm "iPhone 16 Pro" đang được để trong <div class="title">. Google cực kỳ chú trọng vào các thẻ Heading (<h1>, <h2>, v.v.) để xác định từ khóa và chủ đề chính của trang. Việc thiếu Heading khiến trang web gần như tàng hình trước các truy vấn tìm kiếm.
4. Hình ảnh thiếu thuộc tính alt (Alternative text):
Thẻ <img src="iphone.jpg"> không có thuộc tính alt. Thuộc tính này rất quan trọng vì bot Google không thể "xem" ảnh, nó chỉ đọc chữ.
5. Nội dung sản phẩm không được nhóm đúng cách:
-Khối thông tin của một sản phẩm nên được đặt trong thẻ <article> (dành cho nội dung độc lập, có thể tách rời) hoặc <section> thay vì một thẻ <div class="product"> chung chung.
Code đã sửa:
<header>
    <div>ShopTLU</div>
    <nav>
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>

<main>
    <article>
        <h1>iPhone 16 Pro</h1>
        <p>25.990.000đ</p>
        <div>
            <img src="iphone.jpg" alt="Điện thoại iPhone 16 Pro chính hãng">
        </div>
    </article>
</main>

<footer>
    <p>© 2026 ShopTLU</p>
</footer>

Câu A3 (5đ) — Block vs Inline
Không chạy code, hãy vẽ tay (hoặc mô tả bằng text art) kết quả hiển thị của đoạn HTML sau. Giải thích tại sao.
TextArt:
Hộp 1
Text AText B
Hộp 2
Text CText D   <-- (Chữ "Text D" sẽ được in đậm)
Hộp 3
Giải thích:
-Thẻ <div> chúng tự động bắt đầu trên một dòng mới và chiếm toàn bộ chiều rộng của trang, bất cứ nội dung nào đứng trước hoặc đứng sau một thẻ <div> đều bị ép phải nằm ở dòng khác.(tức là sẽ tự động xuống dòng)
-Thẻ <span> và <strong> chúng chỉ chiếm một khoảng không gian vừa đúng bằng chiều rộng của đoạn chữ bên trong nó.(tức là inline được viết chung 1 dòng)

Câu A4 (5đ) — Table
Đọc chương 05. Giải thích sự khác nhau giữa <thead>, <tbody>, <tfoot>. Tại sao KHÔNG NÊN dùng table để tạo layout trang web? (Ghi rõ ít nhất 3 lý do)
1. Sự khác nhau giữa <thead>, <tbody>, <tfoot>
-Ba thẻ này được dùng để chia cấu trúc của một bảng (<table>) thành 3 phần rõ ràng mang tính ngữ nghĩa (semantic):
<thead> (Table Header): Phần đầu bảng. Nơi chứa các ô tiêu đề cột (ví dụ: STT, Họ tên, Giá tiền).
<tbody> (Table Body): Phần thân bảng. Nơi chứa toàn bộ dữ liệu nội dung chính của bảng. Một bảng có thể có nhiều <tbody>.
<tfoot> (Table Footer): Phần chân bảng. Nơi chứa các dòng tổng kết, ghi chú ở cuối (ví dụ: Tổng cộng, Trung bình, Thành tiền).
2. Tại sao KHÔNG NÊN dùng Table để tạo Layout trang web?
-Không hỗ trợ Responsive (Kém linh hoạt)
-Ảnh hưởng xấu đến SEO và Accessibility (Khả năng tiếp cận)
-Code cồng kềnh, cực kỳ khó bảo trì

Bài B3 (15đ) — Debug HTML
Lỗi 1: Dòng 1 — Khai báo DOCTYPE thiếu/sai cú pháp — Cần khai báo chuẩn HTML5. Sửa <!DOCTYPE> thành <!DOCTYPE html>.
Lỗi 2: Dòng 1 — Thẻ <html> thiếu thuộc tính ngôn ngữ (Semantic) — Trình duyệt và máy quét SEO cần biết ngôn ngữ trang web. Sửa <html> thành <html lang="vi">.
Lỗi 3: Dòng 2 — Thiếu thẻ đóng của tiêu đề — Thẻ <title> chưa được đóng. Sửa thành <title>Trang web</title>.
Lỗi 4: Dòng 3 — Sai chuẩn ghi giá trị charset — Giá trị đúng của bảng mã phải có dấu gạch ngang. Sửa charset="utf8" thành charset="utf-8".
Lỗi 5: Dòng 4 — Sai cú pháp thẻ đóng <h1> — Bạn đang dùng hai thẻ mở <h1>...<h1>. Sửa thẻ thứ hai thành thẻ đóng </h1>.
Lỗi 6: Dòng 4 & 6 — Lỗi cấu trúc Semantic (H1 nằm ngoài Header) — Tiêu đề chính của trang nên nằm trong phần <header>. Hãy di chuyển dòng <h1>Welcome to ShopTLU</h1> vào bên trong cặp thẻ <header>.
Lỗi 7: Dòng 8 — Sai cú pháp thẻ đóng <a> — Bạn dùng sai thẻ đóng <a>...<a>. Sửa phần tử thứ hai thành </a>.
Lỗi 8: Dòng 16 — Thiếu thuộc tính alt cho hình ảnh (Lỗi Semantic/Accessibility) — Thẻ <img> bắt buộc phải có thuộc tính alt (văn bản thay thế) và giá trị nên để trong ngoặc kép. Sửa <img src=iphone.jpg> thành <img src="iphone.jpg" alt="Điện thoại iPhone 16 Pro">.
Lỗi 9: Dòng 18 — Lỗi lồng chéo thẻ sai quy tắc (Nesting Error) — Thẻ <b> mở bên trong thẻ <p>, nhưng lại đóng ở bên ngoài. Ngoài ra, dùng thẻ <strong> sẽ mang tính ngữ nghĩa tốt hơn thẻ <b>. Sửa <p>Giá: <b>25.990.000đ</p></b> thành <p>Giá: <strong>25.990.000đ</strong></p>.
Lỗi 10: Dòng 24, 25, 26 — Dùng sai thẻ cho phần Tiêu đề Bảng (Semantic) — Dòng tiêu đề của bảng phải dùng thẻ <th> (Table Heading) thay vì <td> (Table Data). Sửa <td>Tên</td> thành <th>Tên</th> (Đồng thời nên bọc dòng này trong thẻ <thead> cho chuẩn cấu trúc).
Lỗi 11: Dòng 36 — Lạm dụng thẻ <main> (Lỗi Semantic nghiêm trọng) — Theo chuẩn HTML5, mỗi trang web chỉ được phép có duy nhất MỘT thẻ <main> hiển thị nội dung chính. Khối này chứa nội dung của thanh bên (Sidebar), nên thay vì dùng <main>, hãy đổi thành thẻ <aside>.
Lỗi 12: Dòng 41 — Thiếu thẻ đóng văn bản </p> — Sửa <p>Copyright 2026 thành <p>Copyright 2026</p>.

Bài B4: Phân tích trang web thegioididong.com

1. Phân tích Semantic HTML5 trên trang chủ
(Xem ảnh B4.1.png đính kèm)
1)3 thẻ Semantic HTML5 mà trang đang sử dụng:**
1. Thẻ <header>: Nằm ở phần trên cùng của trang, chứa khu vực logo, thanh tìm kiếm và giỏ hàng.
2. Thẻ <section>: Được dùng để bọc khu vực chứa các banner khuyến mãi nổi bật nằm ngay bên dưới header.
3. Thẻ <footer>: Nằm ở dưới cùng của trang, chứa thông tin liên hệ, tổng đài hỗ trợ và các chính sách bảo hành.
2)2 thẻ KHÔNG dùng đúng chuẩn Semantic (Lỗi lạm dụng):**
1. Thanh menu điều hướng chính: Trang web lạm dụng thẻ <div> để bọc các menu danh mục sản phẩm (như Điện thoại, Laptop) thay vì dùng thẻ <nav> chuẩn Semantic.
2. Các nút bấm tương tác: Một số vị trí dùng thẻ <span> hoặc <div> lồng nhau để làm nút bấm (bắt sự kiện click để chuyển trang), đúng chuẩn thì phải dùng thẻ <a> hoặc <button>.

Câu C1 (10đ) — Thiết kế cấu trúc
<header>
    <nav aria-label="Menu chính">
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/dien-thoai">Điện thoại</a></li>
        </ul>
    </nav>
</header>

<main>

    <nav aria-label="Breadcrumb">
        <ol>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/dien-thoai">Điện thoại</a></li>
            <li aria-current="page">iPhone 16</li>
        </ol>
    </nav>

    <article class="product-detail">
        
        <section class="gallery">
            <figure>
                <img src="main.jpg" alt="Ảnh chính sản phẩm">
            </figure>
            
            <ul>
                <li><img src="thumb1.jpg" alt="Ảnh phụ 1"></li>
                <li><img src="thumb2.jpg" alt="Ảnh phụ 2"></li>
                <li><img src="thumb3.jpg" alt="Ảnh phụ 3"></li>
                <li><img src="thumb4.jpg" alt="Ảnh phụ 4"></li>
            </ul>
        </section>

        <section class="info">
            <h1>iPhone 16 Pro Max 256GB</h1>
            
            <p>Giá: 
                <strong>29.990.000đ</strong>
            </p>
            
            <p>Đánh giá: ⭐⭐⭐⭐⭐ (150 đánh giá)</p>
            <p>Mô tả: Điện thoại xịn nhất của Apple năm nay...</p>
            
            <button type="button">Mua ngay</button>
        </section>

        <section class="specs">
            <h2>Thông số kỹ thuật</h2>
            <table>
                <tbody>
                    <tr>
                        <th scope="row">Màn hình</th>
                        <td>6.7 inch, OLED</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section class="reviews">
            <h2>Đánh giá từ khách hàng</h2>
            
            <article class="review-item">
                <header>
                    <h3>Khách hàng A</h3>
                    <time datetime="2026-04-25">Ngày 25/04/2026</time>
                </header>
                <p>Máy mượt, chụp ảnh siêu đẹp!</p>
            </article>
        </section>

    </article>

    <aside class="related-products">
        <h2>Sản phẩm tương tự</h2>
        <ul>
            <li>
                <article>
                    <h3><a href="#">iPhone 15 Pro</a></h3>
                    <p>25.990.000đ</p>
                </article>
            </li>
        </ul>
    </aside>

</main>

<footer>
    <p>&copy; 2026 Cửa hàng của Nguyên</p>
</footer>


 