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