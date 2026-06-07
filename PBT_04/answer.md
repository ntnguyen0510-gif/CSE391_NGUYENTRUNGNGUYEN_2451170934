Cau A1:
Position	Vẫn chiếm chỗ trong flow?	        Tham chiếu vị trí	        Cuộn theo trang?	         Use case
static	            Co                         Theo dòng chảy tự nhiên          Co                   Bố cục văn bản, thẻ block/inline 
                                                    (Normal flow)                                    thông thường (mặc định).

relative        Có (Giữ nguyên                  Chính vị trí gốc ban đầu        Co                   Làm mốc tọa độ cho phần tử con absolute, hoặc 
            khoảng trống ban đầu)                   của nó                                           dịch chuyển nhẹ phần tử mà không làm lệch bố 
                                                                                                     cục xung quanh.
absolute        Không (Bị tách khỏi             Phần tử tổ tiên gần nhất        Có (Cuộn cùng       Làm các thẻ badge góc (như hình thông báo), 
                    normal flow)                 có position khác static        nội dung chứa nó)   dropdown menu, tooltip, hoặc nút bấm nằm đè 
                                                                                                    lên ảnh.
fixed       Không (Bị tách khỏi                 Khung nhìn trình duyệt          Không (Đứng yên     Thanh Navbar cố định trên cùng, nút "Back to 
                normal flow)                         (Viewport)                 khi cuộn)           Top" ở góc dưới, hoặc các hộp thoại Chatbot.

sticky	    Co                                  Đóng vai trò như relative rồi   Có (Nhưng dính lại  Tiêu đề cột của bảng (Table header), hoặc 
                                                chuyển thành fixed khi đạt      trong phạm vi       thanh menu phụ muốn ghim lại khi người dùng 
                                                ngưỡng cuộn                     của cha)            cuộn qua.

1. Khi nào absolute tham chiếu body?Phần tử có position: absolute sẽ tham chiếu đến body (chính xác hơn là initial containing block - khung nhìn đầu tiên của trang web) khi tất cả các phần tử tổ tiên bao bọc bên ngoài nó (cha, ông, cố...) đều có thuộc tính position: static (hoặc không khai báo thuộc tính position). Lúc này, nó không tìm được mốc tọa độ nào khác nên sẽ bám vào khung chuẩn của trang.
2. Khi nào absolute tham chiếu parent?Nó sẽ tham chiếu trực tiếp đến phần tử cha (parent) khi phần tử cha trực tiếp đó được thiết lập thuộc tính position có giá trị khác static (thường dùng nhất là position: relative, hoặc cũng có thể là absolute, fixed, sticky).
3. Giải thích khái niệm "nearest positioned ancestor"Ancestor (Tổ tiên): Là các phần tử bọc ngoài (cha, ông, ông cố,...) ngược dần lên trên cây thư mục HTML.Positioned (Đã định vị): Là bất kỳ phần tử nào có thuộc tính position mang giá trị khác với static (tức là có dùng relative, absolute, fixed, hoặc sticky).Nearest (Gần nhất): Phần tử đầu tiên tìm thấy khi đi ngược từ dưới lên.Tóm lại: "Nearest positioned ancestor" là phần tử chứa bên ngoài gần nó nhất có cài đặt thuộc tính position khác static. Phần tử này sẽ được chọn làm gốc tọa độ ($(0,0)$ nằm ở góc trên bên trái) để tính toán các khoảng cách top, bottom, left, right cho phần tử absolute bên trong. Nếu tìm mãi lên tới tận cùng mà không có ai, mốc tọa độ sẽ mặc định là cửa sổ trình duyệt.

Cau A2:
TH1:
+-------------------------------------------------------+
| [ Item 1 ]  |  [ Item 2 ]  |  [ Item 3 ]  |  [ Item 4 ]|
+-------------------------------------------------------+
TH2:
+-------------------------------------------------------+
|  (2.5%) [  Item 1  ] (2.5%) (2.5%) [  Item 2  ] (2.5%)| -> Hàng 1
|                                                       |
|  (2.5%) [  Item 3  ] (2.5%) (2.5%) [  Item 4  ] (2.5%)| -> Hàng 2
|                                                       |
|  (2.5%) [  Item 5  ] (2.5%) (2.5%) [  Item 6  ] (2.5%)| -> Hàng 3
+-------------------------------------------------------+
TH3:
+-------------------------------------------------------+
|                                                       |
| [ Item 1 ]             [ Item 2 ]             [ Item 3 ]
|                                                       |
+-------------------------------------------------------+
TH4:
+-------------------------------------------------------+
| <200px> |  20px  |       < Co giãn tự do >       |  20px  | <200px> |
| [Item 1]|  gap   |           [ Item 2 ]          |  gap   | [Item 3]|
+-------------------------------------------------------+
TH5:
+-------------------------------------------------------+
|    [ Item 1 ]    |gap|    [ Item 2 ]    |gap|    [ Item 3 ]    | -> Hàng 1
|-------------------------------------------------------|
|    [ Item 4 ]    |gap|    [ Item 5 ]    |gap|    [ Item 6 ]    | -> Hàng 2
|-------------------------------------------------------|
|    [ Item 7 ]    |            (Trống)   |            (Trống)   | -> Hàng 3
+-------------------------------------------------------+

Phần C:
Câu C1:
Tình huống 1: Navigation bar ngang (logo + menu + buttons)
Lựa chọn: Flexbox

Giải thích: Thanh điều hướng (Navbar) là layout 1 chiều (chiều ngang). Các phần tử bên trong có kích thước nội dung không cố định (phụ thuộc vào độ dài chữ của từng chữ Home, Products, Contact...). Flexbox là công cụ hoàn hảo để xử lý căn chỉnh trục ngang, tự động kéo giãn khoảng cách bằng justify-content: space-between và căn giữa trục dọc hoàn hảo bằng align-items: center.

Tình huống 2: Lưới ảnh Instagram (3 cột đều nhau, số ảnh không biết trước)
Lựa chọn: Grid

Giải thích: Đây là layout 2 chiều dạng lưới (hàng và cột) cần sự đồng đều tuyệt đối. Với Grid, bạn chỉ cần định nghĩa số cột cố định bằng grid-template-columns: repeat(3, 1fr);. Khi số lượng ảnh tăng lên và không biết trước, CSS Grid sẽ tự động tạo thêm các hàng mới (implicit grid) và xếp các ảnh vào đúng vị trí tăm tắp mà không cần tính toán thủ công hay lo bị vỡ dòng.

Tình huống 3: Layout blog (Main content + Sidebar)
Lựa chọn: Grid (hoặc Flexbox đều được, nhưng Grid tối ưu hơn cho cấu trúc tổng thể)

Giải thích: Đây là bố cục trang lớn (macro layout). Dùng Grid giúp bạn định hình rõ ràng bộ khung của trang web bằng cách phân chia không gian cột cố định cho Sidebar (ví dụ: 250px) và phần còn lại cho Main Content (1fr). Khi thiết kế responsive (giao diện điện thoại), bạn có thể dễ dàng chuyển Sidebar xuống dưới Main Content chỉ bằng cách thay đổi cấu trúc Grid, tránh được việc các khối bị đẩy lệch hướng ngoài ý muốn.

Tình huống 4: Footer với 4 cột thông tin
Lựa chọn: Kết hợp cả hai (hoặc chọn 1 trong 2 tùy mục đích responsive)

Bố cục tổng thể 4 cột: Dùng Grid với grid-template-columns: repeat(4, 1fr); để đảm bảo 4 khối nội dung lớn luôn có độ rộng bằng nhau tuyệt đối trên màn hình máy tính.

Nội dung bên trong mỗi cột: Dùng Flexbox hướng dọc (flex-direction: column;) để xếp các đường link (Về chúng tôi, Liên hệ...) thẳng hàng từ trên xuống dưới và dễ dàng quản lý khoảng cách bằng thuộc tính gap.

Tình huống 5: Card sản phẩm (Ảnh trên, text giữa, nút dưới — nút luôn dính đáy)
Lựa chọn: Flexbox

Giải thích: Bản thân một thẻ card sản phẩm đơn lẻ là layout 1 chiều hướng dọc (flex-direction: column;). Flexbox giải quyết bài toán "nút dính đáy" cực kỳ thanh thoát bằng cách thiết lập margin-top: auto; cho nút bấm (hoặc flex-grow: 1; cho phần text ở giữa). Lúc này, dù tiêu đề sản phẩm dài hay ngắn, phần không gian thừa sẽ tự động bị đẩy ra, ép nút bấm luôn nằm sát cạnh dưới của Card tạo nên sự đồng đều.

C2:
Lỗi 1: Cards không đều chiều cao — nút "Mua" bị nhảy lên/xuống
1. Nguyên nhân
Thừa hưởng từ tính năng mặc định của Flexbox (align-items: stretch), các thẻ .card trên cùng một hàng thực chất có chiều cao bằng nhau. Tuy nhiên, nội dung bên trong mỗi card (như độ dài tiêu đề h3, đoạn mô tả) lại ngắn dài khác nhau.

Bản thân thẻ .card chưa được kích hoạt Flexbox, khiến các phần tử con bên trong xếp theo dạng Block thông thường từ trên xuống. Vì vậy, ở những card có tiêu đề ngắn, khoảng trống phía dưới sẽ bị bỏ thừa và nút .btn bị kéo dịch lên trên, không thẳng hàng với card bên cạnh.

2. Code sửa
Để xử lý, chúng ta cần biến bản thân mỗi .card thành một Flex container hướng dọc (flex-direction: column) và áp dụng tuyệt chiêu margin-top: auto cho nút .btn.

CSS
/* Container giữ nguyên */
.card-container { 
    display: flex; 
    flex-wrap: wrap; 
}

/* SỬA TẠI ĐÂY: Biến card thành flex hướng dọc */
.card { 
    width: 30%; 
    margin: 1.5%; 
    display: flex;
    flex-direction: column; /* Xếp nội dung theo cột */
}

.card img { width: 100%; }
.card h3 { font-size: 18px; }

/* SỬA TẠI ĐÂY: Ép nút luôn dính vào đáy card */
.card .btn { 
    padding: 10px; 
    margin-top: auto; /* Tự động đẩy phần không gian trống lên trên, ép nút xuống đáy */
}
Lỗi 2: Items muốn nằm giữa cả ngang lẫn dọc trong container 100vh, nhưng vẫn dính góc trái trên
1. Nguyên nhân
Thuộc tính text-align: center chỉ có tác dụng căn giữa văn bản nội dòng (inline-text) hoặc các phần tử inline bên trong .hero-content, chứ nó không có khả năng căn giữa chính khối .hero-content so với công cụ cha .hero.

Bạn đã khai báo .hero { display: flex; } nhưng lại chưa hề cấu hình quy tắc căn chỉnh nào cho trục chính (trục ngang) và trục phụ (trục dọc) của Flexbox, khiến các phần tử con mặc định xếp về góc trái trên (flex-start).

2. Code sửa
Sử dụng bộ đôi quyền lực justify-content: center (căn giữa trục ngang) và align-items: center (căn giữa trục dọc) trực tiếp trên Flex container cha (.hero).

CSS
.hero {
    height: 100vh;
    display: flex;
    /* SỬA TẠI ĐÂY: Thêm 2 thuộc tính căn giữa của Flexbox */
    justify-content: center; /* Căn giữa theo chiều ngang */
    align-items: center;     /* Căn giữa theo chiều dọc */
}

.hero-content {
    text-align: center; /* Giữ lại để căn giữa các dòng chữ bên trong chính nó */
}
Lỗi 3: Sidebar bị co lại khi content quá dài
1. Nguyên nhân
Trong cơ chế của Flexbox, các phần tử con (Flex items) mặc định có thuộc tính flex-shrink: 1. Điều này có nghĩa là khi vùng không gian của phần tử .content quá lớn (do text dài, ảnh to), Flexbox sẽ cố gắng bóp nghẹt (co cụm) kích thước của các phần tử xung quanh để tránh làm tràn container cha.

Do đó, dù bạn đặt width: 250px cho .sidebar, nó vẫn bị tước đoạt không gian và co nhỏ lại dưới mức 250px.

2. Code sửa
Cấm không cho phép vùng .sidebar bị co giãn bằng cách thiết lập thuộc tính flex-shrink: 0.

CSS
.layout { 
    display: flex; 
}

/* SỬA TẠI ĐÂY: Khóa cứng kích thước Sidebar */
.sidebar { 
    width: 250px; 
    flex-shrink: 0; /* Bảo vệ Sidebar, giá trị 0 nghĩa là tuyệt đối không bị co lại */
}

.content { 
    flex: 1; 
}
