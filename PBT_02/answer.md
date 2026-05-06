Câu A1 (5đ) — Input Types
Liệt kê 10 input types khác nhau trong HTML5, cho mỗi type:
1. type="email"
Giao diện: Một ô nhập văn bản bình thường; trên thiết bị di động sẽ hiển thị bàn phím có sẵn phím @ và dấu chấm ..
Validation: Tự động kiểm tra định dạng chuỗi nhập vào có cấu trúc của một email (phải có ký tự @ và tên miền).
Use case: Dùng trong form Đăng nhập hoặc Đăng ký tài khoản khách hàng.
2. type="password"
Giao diện: Các ký tự nhập vào sẽ bị ẩn đi (thay bằng dấu chấm hoặc dấu sao).
Validation: Không có validation định dạng mặc định, nhưng giúp bảo mật tránh bị nhìn trộm.
Use case: Dùng để nhập Mật khẩu khi thanh toán hoặc thiết lập tài khoản.
3. type="number"
Giao diện: Ô nhập kèm theo hai nút mũi tên lên/xuống (spinner) ở góc phải để tăng/giảm giá trị.
Validation: Chỉ cho phép nhập số; có thể giới hạn khoảng bằng thuộc tính min, max và bước nhảy step.
Use case: Dùng để khách hàng chọn Số lượng sản phẩm muốn thêm vào giỏ hàng.
4. type="tel"
Giao diện: Ô nhập văn bản; trên di động sẽ tự động kích hoạt bàn phím số (numeric keypad).
Validation: Không tự động kiểm tra định dạng cụ thể (do chuẩn số điện thoại quốc tế rất đa dạng), thường kết hợp với thuộc tính pattern.
Use case: Dùng để nhập Số điện thoại nhận hàng trong trang Checkout.
5. type="date"
Giao diện: Hiển thị một trình chọn lịch (Date picker) trực quan để người dùng nhấn chọn ngày/tháng/năm.
Validation: Ép kiểu dữ liệu trả về theo định dạng YYYY-MM-DD.
Use case: Dùng để chọn Ngày sinh khách hàng để nhận ưu đãi thành viên hoặc Ngày hẹn giao hàng.
6. type="color"
Giao diện: Một ô màu hiển thị màu đang chọn; khi nhấn vào sẽ mở bảng chọn màu (Color palette) của hệ điều hành.
Validation: Luôn trả về giá trị mã màu Hex (ví dụ: #ff0000).
Use case: Dùng trong tính năng Bộ lọc tìm kiếm (Filter) để khách hàng chọn màu sắc quần áo/phụ kiện yêu thích.
7. type="range"
Giao diện: Một thanh trượt (slider) cho phép người dùng kéo để chọn giá trị trong một khoảng.
Validation: Giới hạn giá trị nằm trong khoảng min và max định sẵn.
Use case: Dùng để thiết lập Bộ lọc khoảng giá (Price Range) (ví dụ: từ 0đ đến 10.000.000đ).
8. type="file"
Giao diện: Một nút bấm kèm dòng chữ "Choose File" hoặc "Chưa chọn tệp nào".
Validation: Có thể giới hạn loại file (ảnh, pdf...) thông qua thuộc tính accept.
Use case: Dùng để khách hàng Tải ảnh hóa đơn chuyển khoản hoặc ảnh sản phẩm khi Viết đánh giá (Review).
9. type="search"
Giao diện: Tương tự ô text nhưng thường có thêm nút "x" nhanh để xóa sạch nội dung đã nhập; tối ưu hóa cho thanh tìm kiếm.
Validation: Không có validation đặc biệt.
Use case: Dùng làm Thanh tìm kiếm sản phẩm ở đầu trang web.
10. type="checkbox"
Giao diện: Một ô vuông nhỏ cho phép tích chọn hoặc bỏ chọn.
Validation: Có thể dùng thuộc tính required để buộc người dùng phải tích vào.
Use case: Dùng để khách hàng tích chọn "Tôi đồng ý với điều khoản dịch vụ" trước khi thanh toán.

Câu A3 (5đ) — Accessibility
Đọc phần Accessibility trong chương 07. Giải thích:
1. Tại sao <label for="email"> quan trọng cho Screen Reader?
Nếu bạn chỉ dùng thẻ <span> hoặc <div> để đặt tên bên cạnh ô nhập liệu, người dùng bình thường có thể thấy, nhưng Screen Reader (trình đọc màn hình) sẽ không hiểu chúng có liên quan đến nhau.

Tạo liên kết logic: Thuộc tính for trong thẻ <label> phải khớp với id của thẻ <input>. Khi người dùng dùng phím Tab để di chuyển vào ô nhập liệu, Screen Reader sẽ đọc to nội dung của nhãn đó (ví dụ: "Email, edit text"). Nếu không có sự liên kết này, nó chỉ đọc là "Edit text, blank", người dùng sẽ không biết phải nhập cái gì.
Mở rộng vùng tương tác: Khi có thẻ <label>, người dùng nhấn chuột vào chữ "Email" thì con trỏ cũng sẽ tự động nhảy vào ô input. Điều này cực kỳ hữu ích cho người dùng có vấn đề về vận động tinh (khó bấm chính xác vào ô vuông nhỏ).

2. Khi nào dùng <fieldset> và <legend>?
Hai thẻ này dùng để nhóm các phần tử có liên quan chặt chẽ trong một form lớn, giúp phân chia bố cục mạch lạc về cả thị giác lẫn cấu trúc dữ liệu.
<fieldset>: Dùng để bao quanh một nhóm các trường nhập liệu có cùng mục đích.
<legend>: Là tiêu đề của nhóm đó.
Ví dụ cụ thể trong E-commerce: Khi thanh toán, bạn thường có hai nhóm thông tin riêng biệt là "Địa chỉ nhận hàng" và "Phương thức thanh toán".

HTML
<form>
  <fieldset>
    <legend>Thông tin giao hàng</legend>
    <label for="name">Họ tên:</label>
    <input type="text" id="name">
    <br>
    <label for="address">Địa chỉ:</label>
    <input type="text" id="address">
  </fieldset>
  <fieldset>
    <legend>Phương thức thanh toán</legend>
    <input type="radio" id="cod" name="pay" value="cod">
    <label for="cod">Thanh toán khi nhận hàng (COD)</label>
    <br>
    <input type="radio" id="card" name="pay" value="card">
    <label for="card">Thẻ tín dụng</label>
  </fieldset>
</form>

3. aria-label dùng khi nào?
aria-label là một thuộc tính dùng để cung cấp một nhãn văn bản ẩn cho các phần tử không có nhãn hiển thị trên màn hình.
Dùng khi nào: Thường dùng cho các nút chỉ có biểu tượng (Icon button). Ví dụ: Nút đóng cửa sổ (dấu X), nút tìm kiếm (hình kính lúp), hoặc các nút mạng xã hội (logo Facebook).

Ví dụ: <button aria-label="Đóng cửa sổ">X</button>. Lúc này, Screen Reader sẽ đọc là "Đóng cửa sổ button" thay vì chỉ đọc "X button".
Tại sao KHÔNG nên dùng aria-label khi đã có <label>?
Việc lạm dụng cả hai sẽ gây ra sự dư thừa và đôi khi là xung đột:
1. Gây nhiễu: Screen Reader có thể đọc cả hai nhãn hoặc ưu tiên nhãn này bỏ nhãn kia, khiến người dùng bối rối.
2. Nguyên tắc ưu tiên: HTML thuần (<label>) luôn được ưu tiên vì nó có tính tương tác cao (như đã nói ở mục 1: nhấn vào chữ thì nhảy vào ô input). aria-label không có tính năng này, nó chỉ là một "mẩu ghi chú" bằng giọng nói.
3. Khả năng dịch thuật: Các công cụ dịch trang web tự động (như Google Translate) thường dịch nội dung trong thẻ <label> nhưng có thể bỏ qua các thuộc tính ẩn như aria-label.

Câu A4 (5đ) — Media
1. Giải thích thuộc tính loading="lazy" trên thẻ <img>. Nó cải thiện gì? Khi nào KHÔNG nên dùng?
Giải thích: Đây là cơ chế Lazy Loading (tải chậm) bản gốc của trình duyệt. Thay vì tải tất cả ảnh ngay khi trang web vừa mở, trình duyệt sẽ trì hoãn việc tải các ảnh nằm ngoài khung hình (viewport) cho đến khi người dùng cuộn trang xuống gần vị trí của ảnh đó.
-Cải thiện:
Tốc độ tải trang (LCP): Giảm dung lượng dữ liệu phải tải ban đầu, giúp trang web hiện thị nhanh hơn.
Tiết kiệm băng thông: Cực kỳ quan trọng cho người dùng sử dụng mạng 3G/4G/5G giới hạn dung lượng.
-Khi nào KHÔNG nên dùng:
Không dùng cho ảnh ở đầu trang (Above the fold) như Banner chính, Logo hoặc ảnh sản phẩm đầu tiên. Nếu dùng lazy load ở đây, ảnh sẽ xuất hiện trễ, tạo cảm giác trang web bị "giật" hoặc trống trải.
2. Tại sao nên cung cấp nhiều <source> trong thẻ <video>? Liệt kê ít nhất 3 format video web phổ biến.
-Thẻ <video> và các Source
Tại sao cần nhiều <source>: Mỗi trình duyệt (Chrome, Safari, Firefox) hỗ trợ các bộ giải mã (codec) khác nhau. Cung cấp nhiều source giúp trình duyệt tự chọn định dạng tốt nhất mà nó hỗ trợ, đảm bảo video luôn chạy được trên mọi thiết bị.
3 Format video web phổ biến:
1. MP4 (H.264): Phổ biến nhất, hỗ trợ gần như 100% các thiết bị và trình duyệt.
2. WebM (VP9/AV1): Do Google phát triển, dung lượng nhẹ hơn MP4 nhưng chất lượng tương đương, rất tốt cho Chrome/Android.
3. Ogg (Theora): Một định dạng mã nguồn mở, thường dùng làm phương án dự phòng.

3. Thuộc tính alt trên <img> dùng để làm gì? 
Công dụng:
-Hiển thị thay thế nếu ảnh bị lỗi đường dẫn.
-Hỗ trợ Screen Reader đọc nội dung ảnh cho người khiếm thị.
-Giúp Google hiểu nội dung ảnh để xếp hạng SEO tốt hơn.

Câu A5 (5đ) — So sánh <figure> vs <img>
<!-- Cách 1 -->
<img src="product.jpg" alt="iPhone">

<!-- Cách 2 -->
<figure>
    <img src="product.jpg" alt="iPhone 16 Pro Max 256GB Titan">
    <figcaption>iPhone 16 Pro Max — 25.990.000đ</figcaption>
</figure>
Khi nào dùng Cách 1, khi nào dùng Cách 2? Cho 2 ví dụ thực tế cho mỗi cách.

1. Cách 1: Chỉ sử dụng thẻ <img>
Khi nào dùng:
Dùng khi hình ảnh là một phần nội dung trực tiếp hoặc mang tính trang trí, không cần chú thích tách biệt. Nếu thiếu hình ảnh này, đoạn văn hoặc nội dung xung quanh có thể bị mất đi ý nghĩa hoặc trở nên khó hiểu.
Ví dụ 1 (Logo thương hiệu): Trên thanh Header của trang E-commerce, logo chỉ cần thẻ <img> với alt="Tên cửa hàng". Nó không cần chú thích bên dưới.
Ví dụ 2 (Icon tiện ích): Các icon nhỏ bên cạnh chữ như hình chiếc xe tải bên cạnh dòng chữ "Giao hàng miễn phí". Đây là ảnh bổ trợ cho text.
2. Cách 2: Sử dụng bộ thẻ <figure> và <figcaption>
Khi nào dùng:
Dùng khi hình ảnh là một đơn vị nội dung độc lập (self-contained). Đặc điểm quan trọng nhất là bạn có thể di chuyển khối <figure> này sang vị trí khác (ví dụ: xuống cuối trang hoặc sang một sidebar) mà không làm hỏng dòng chảy logic của bài viết.
<figure>: Nhóm hình ảnh và mô tả lại thành một khối.
<figcaption>: Cung cấp chú thích rõ ràng, giúp người dùng (và Google) hiểu rõ ngữ cảnh của ảnh đó.
Ví dụ 1 (Danh sách sản phẩm): Trong trang chi tiết sản phẩm, một bức ảnh chụp cận cảnh các cổng kết nối của iPhone kèm chú thích: "Cổng USB-C mới hỗ trợ tốc độ truyền dữ liệu nhanh hơn".
Ví dụ 2 (Minh họa trong Blog): Trong bài viết "Đánh giá camera iPhone 16", bạn đăng một tấm ảnh chụp đêm và dùng <figcaption> để ghi: "Ảnh chụp chế độ Ban đêm (Night Mode) với thời gian phơi sáng 3 giây".
