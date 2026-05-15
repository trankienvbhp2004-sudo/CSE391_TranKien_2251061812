### Phần A
# Câu A1
| **Position** | **Vẫn chiếm chỗ trong flow?** | **Tham chiếu vị trí** | **Cuộn theo trang?** | **Use case** |
|--------------|-------------------------------|-----------------------|----------------------|--------------|
| static       |  Có                         | Theo flow bình thường    |  Có                   | Mặc định, không định vị đặc biệt          |
|--------------|-----------------------------|--------------------------|-----------------------|-------------------------------------------|
| relative     |  Có                         | Chính nó (so với static) |  Có                   |  Dịch chuyển nhẹ, tạo anchor cho absolute |
|--------------|-----------------------------|--------------------------|-----------------------|-------------------------------------------|
| absolute     |  Không                      | Cha gần nhất có position khác static|  Có        | Tooltip, popup, đặt phần tử chính xác     |
|--------------|-----------------------------|--------------------------|-----------------------|-------------------------------------------|
| fixed        |  Không                      | Viewport                 |  Không                | Thanh menu cố định, nút Back to top       |
|--------------|-----------------------------|--------------------------|-----------------------|-------------------------------------------|
| sticky       |  Có (ban đầu)               | Vị trí gốc,sau đó tham   | Có                    | Header dính, cột table dính khi cuộn      |
|              |                             |chiếu viewport khi cuộn   |                       |                                           |
|--------------|-----------------------------|--------------------------|-----------------------|----------------------------------------| 

Giải thích ngắn gọn

Static: mặc định, không thể dùng top/left.
Relative: vẫn giữ chỗ, nhưng có thể dịch chuyển.
Absolute: thoát khỏi flow, định vị theo cha có position.
Fixed: thoát khỏi flow, định vị theo viewport, không cuộn.
Sticky: kết hợp relative + fixed, dính khi cuộn đến ngưỡng.       

1. Khái niệm "nearest positioned ancestor"
Một phần tử có position: absolute sẽ thoát khỏi flow và được định vị dựa trên tổ tiên gần nhất (ancestor) có position khác static.
Nếu không tìm thấy ancestor nào có position: relative, absolute, fixed, hoặc sticky, thì nó sẽ tham chiếu theo viewport / <html> / <body> 
2. Khi nào absolute tham chiếu body/viewport?
Khi tất cả các phần tử cha đều có position: static (mặc định).
3. Khi nào absolute tham chiếu parent?
Khi parent có position: relative, absolute, fixed, hoặc sticky.
# CÂu A2
1. Flex với flex: 1
css
.container { display: flex; }
.item { flex: 1; }
4 items → mỗi item chiếm 1/4 chiều rộng container.

Bố cục:

Code
[ item1 ][ item2 ][ item3 ][ item4 ]
2. Flex-wrap với width + margin
css
.container { display: flex; flex-wrap: wrap; }
.item { width: 45%; margin: 2.5%; }
Mỗi item chiếm 45% + 2.5% + 2.5% = 50% chiều rộng.

6 items → xếp thành 3 hàng, 2 cột.

Bố cục:

Code
[ item1 ][ item2 ]
[ item3 ][ item4 ]
[ item5 ][ item6 ]
3. Flex với justify-content + align-items
css
.container { display: flex; justify-content: space-between; align-items: center; }
3 items → nằm trên 1 hàng, cách đều nhau theo chiều ngang, căn giữa theo chiều dọc.

Bố cục:

Code
item1       item2       item3
4. Grid với 3 cột cố định
css
.container { display: grid; grid-template-columns: 200px 1fr 200px; gap: 20px; }
3 items → mỗi item nằm trong một cột:

Cột 1: 200px

Cột 2: chiếm phần còn lại (1fr)

Cột 3: 200px

Bố cục:

Code
[ item1 ][      item2 (giãn)      ][ item3 ]
5. Grid repeat(3, 1fr)
css
.container { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
3 cột bằng nhau.

7 items → xếp thành 3 hàng:

Hàng 1: item1, item2, item3

Hàng 2: item4, item5, item6

Hàng 3: item7 (chỉ chiếm cột đầu tiên)

Bố cục:

Code
[ item1 ][ item2 ][ item3 ]
[ item4 ][ item5 ][ item6 ]
[ item7 ]
 Tóm lại:

Trường hợp 1: 1 hàng, 4 cột bằng nhau

Trường hợp 2: 3 hàng, 2 cột

Trường hợp 3: 1 hàng, 3 item cách đều

Trường hợp 4: 1 hàng, 3 cột (200px – giãn – 200px)

Trường hợp 5: 3 hàng, 3 cột, item cuối nằm hàng 3 cột 1
