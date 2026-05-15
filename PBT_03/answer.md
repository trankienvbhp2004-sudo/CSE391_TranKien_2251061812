### Phần A
# Câu A1
```
3 cách nhúng css:
1. Inline CSS
-vd code:
<p style="color: red; font-size: 18px;">Xin chào!</p>

Ưu điểm:
Nhanh, dễ áp dụng cho một phần tử cụ thể.
Không cần file ngoài.

Nhược điểm:
Khó bảo trì khi có nhiều phần tử.
Mã HTML bị rối, thiếu tách biệt giữa nội dung và trình bày.
Khi nên dùng:
Chỉ áp dụng cho một vài phần tử nhỏ, thử nghiệm nhanh.
2. Internal CSS
Ví dụ:

html
<head>
  <style>
    p {
      color: blue;
      font-size: 20px;
    }
  </style>
</head>
<body>
  <p>Xin chào!</p>
</body>
Ưu điểm:
Dễ quản lý trong cùng một file HTML.
Không cần file CSS riêng.

Nhược điểm:
Không tái sử dụng cho nhiều trang.
File HTML dài và khó tối ưu.
Khi nên dùng:
Trang web nhỏ, chỉ có một vài trang.

3. External CSS
vd code:

html
<head>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <p>Xin chào!</p>
</body>

Ưu điểm:
Tách biệt rõ ràng giữa nội dung và trình bày.
Tái sử dụng cho nhiều trang.
Dễ bảo trì, dễ mở rộng.

Nhược điểm:
Cần thêm file CSS ngoài.
Nếu file CSS bị lỗi hoặc không tải được, giao diện sẽ mất định dạng.

Khi nên dùng:
Dự án lớn, nhiều trang web, cần quản lý thống nhất.
***
câu hỏi thêm:
nó sẽ dựa vào quy tắc ưu tiên
 Inline CSS có độ ưu tiên cao nhất.

Internal và External CSS có cùng mức, nhưng xét theo thứ tự xuất hiện (CSS viết sau sẽ ghi đè CSS viết trước).

Ngoài ra, còn phụ thuộc vào độ đặc hiệu selector (ví dụ: id > class > tag).
```
# Câu A2
```
Dựa trên HTML đã cho, ta phân tích từng selector:

h1  
→ Chọn: ShopTLU

.price  
→ Chọn: 25.990.000đ và 45.990.000đ

#app header  
→ Chọn toàn bộ <header class="top-bar dark"> ... </header>  
(bao gồm ShopTLU và các link Home, Products, About)

nav a:first-child  
→ Chọn: Home

.product.featured h2  
→ Chọn: MacBook Pro

article > p  
→ Chọn tất cả <p> là con trực tiếp của <article>:

25.990.000đ

Mô tả sản phẩm... (iPhone 16)

45.990.000đ

Mô tả sản phẩm... (MacBook Pro)

a[href="/"]  
→ Chọn: Home

.top-bar.dark h1  
→ Chọn: ShopTLU
```
# câu A3
1. Trường hợp 1: content-box
css
.box-1 {
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
Chiều rộng hiển thị (render):  
400+20+20+5+5=450 px
(content + padding trái/phải + border trái/phải)

Không gian chiếm trên trang:  
450+10+10=470 px
(bao gồm margin trái/phải)

2. Trường hợp 2: border-box
css
.box-2 {
    box-sizing: border-box;
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
Chiều rộng hiển thị (render):  
= 400 px (bao gồm content + padding + border trong tổng width)

Kích thước content thực tế:  
400−(20+20)−(5+5)=350 px

Không gian chiếm trên trang:  
400+10+10=420 px

3. Trường hợp 3: Margin collapse
css
.box-a { margin-bottom: 25px; }
.box-b { margin-top: 40px; }
Khoảng cách giữa box-a và box-b:  
= 40px (không cộng dồn, mà lấy giá trị lớn hơn)

Giải thích:  
Đây là hiện tượng margin collapse. Khi hai margin dọc (vertical margins) gặp nhau, chúng không cộng lại mà chỉ lấy giá trị lớn nhất.

Nâng cao: Margin âm
css
.box-a { margin-bottom: -10px; }
.box-b { margin-top: 40px; }
Khoảng cách giữa box-a và box-b:  
= 40+(−10)=30 px

Giải thích:  
Khi có margin âm, trình duyệt sẽ tính toán bằng cách cộng giá trị dương với giá trị âm, dẫn đến khoảng cách nhỏ hơn.

# Câu A4
```
Ta có element:

html
<p class="price" id="main-price">...</p>
1. Tính specificity score (a, b, c)
Rule A: p  
→ (0, 0, 1)
(0 ID, 0 class, 1 element)

Rule B: .price  
→ (0, 1, 0)
(0 ID, 1 class, 0 element)

Rule C: #main-price  
→ (1, 0, 0)
(1 ID, 0 class, 0 element)

Rule D: p.price  
→ (0, 1, 1)
(0 ID, 1 class, 1 element)

2. Element sẽ có màu gì?
Rule C (#main-price { color: red; }) có specificity cao nhất (1,0,0).
-> Kết quả: màu đỏ

3. Nếu thêm inline style
html
<p class="price" id="main-price" style="color: orange;">...</p>
Inline style có specificity đặc biệt: (1,0,0,0) — cao hơn tất cả các rule CSS.
-> Kết quả: màu cam (orange)

4. Nếu Rule A thêm !important
css
p { color: black !important; }
!important sẽ ghi đè tất cả các rule khác, kể cả inline style (trừ khi inline style cũng có !important).
-> Kết quả: màu đen (black)

Giải thích:  
Cơ chế ưu tiên CSS:

!important > inline style > ID selector > class selector > element selector.

Nếu nhiều rule cùng !important, thì xét tiếp specificity và thứ tự xuất hiện.
```

### Phần C
# Câu C1
 1. Chiều rộng thực tế của sidebar
css
.sidebar {
    width: 300px;
    padding: 20px;   /* 20px trái + 20px phải */
    border: 1px;     /* 1px trái + 1px phải */
}
Content: 300px

Padding: 40px

Border: 2px
 Tổng = 342px

2. Chiều rộng thực tế của content
css
.content {
    width: 660px;
    padding: 30px;   /* 30px trái + 30px phải */
    border: 1px;     /* 1px trái + 1px phải */
}
Content: 660px

Padding: 60px

Border: 2px
 Tổng = 722px

3. Tại sao layout bị vỡ
Container: 960px

Sidebar + Content: 342px + 722px = 1064px

960px → Content bị đẩy xuống dòng mới vì không đủ chỗ.

4. Hai cách sửa khác nhau
Cách 1: Dùng border-box
css
.sidebar, .content {
    box-sizing: border-box;
}
Khi đó:

Sidebar = 300px (bao gồm padding + border)

Content = 660px (bao gồm padding + border)

Tổng = 960px → vừa khít container

Cách 2: Không dùng border-box (giữ content-box)
Giảm width để trừ padding + border:

css
.sidebar {
    width: 258px; /* 300 - 40 - 2 */
}
.content {
    width: 598px; /* 660 - 60 - 2 */
}
Sidebar = 258 + 40 + 2 = 300px

Content = 598 + 60 + 2 = 660px

Tổng = 960px → vừa khít container
# câu C2
1. "Sản phẩm A" (h2 trong card featured)
Font-size:

body { font-size: 16px; } → mặc định 16px

.container { font-size: 14px; } → kế thừa xuống card

.card .title { font-size: 20px; } → áp dụng trực tiếp
 20px

Color:

body { color: #333; } → mặc định

.card { color: blue; } → kế thừa cho con

#featured .title { color: red; } → áp dụng trực tiếp

.highlight { color: green !important; } → ghi đè tất cả
 Xanh lá (green)

2. "Mô tả sản phẩm" (p trong card featured)
Color:

body { color: #333; } → mặc định

.card { color: blue; } → áp dụng cho card, kế thừa xuống p

.card p { color: inherit; } → kế thừa từ cha .card (blue)
 Xanh dương (blue)

3. "Sản phẩm B" (h2 trong card thường)
Font-size:

body { font-size: 16px; }

.container { font-size: 14px; } → kế thừa xuống card

.card .title { font-size: 20px; } → áp dụng trực tiếp


Color:

body { color: #333; }

.card { color: blue; } → kế thừa xuống h2

.card .title không có color, chỉ font-size
 Xanh dương (blue)

4. "Mô tả sản phẩm B" (p.highlight)
Color:

.card { color: blue; } → kế thừa

.card p { color: inherit; } → kế thừa từ cha (blue)

.highlight { color: green !important; } → ghi đè tất cả
 Xanh lá (green)
 