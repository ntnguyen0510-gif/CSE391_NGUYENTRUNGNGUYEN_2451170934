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