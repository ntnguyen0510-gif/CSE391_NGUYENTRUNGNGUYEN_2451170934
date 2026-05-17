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

