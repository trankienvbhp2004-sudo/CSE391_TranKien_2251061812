### PHẦN A
```
### Câu A1
# Nguồn tham chiếu
file 01_introduction_html_universe.md
phần: 1.1; 1.3; 4.3
---------------------------------------------------
1.
Các bước khi gõ https://shopee.vn:
-DNS Lookup → phân giải shopee.vn thành IP
-TCP Handshake → thiết lập kết nối (3 bước)
-TLS Handshake → mã hóa HTTPS
-HTTP Request → trình duyệt gửi yêu cầu GET
-HTTP Response → server trả HTML
-Tải tài nguyên phụ → CSS, JS, ảnh
-Render → tạo DOM + CSSOM → hiển thị trang

2.
Tab Network của Google Chrome cho biết:
-Danh sách tất cả request (HTML, CSS, JS, ảnh…)
-Status Code (200, 404, 500…)
-Thời gian load từng request và tổng thời gian
-Loại tài nguyên (document, css, js…)
-Kích thước file
-Waterfall (timeline tải tài nguyên)

# Minh họa tab Network
- Status Code request đầu tiên
- Tổng thời gian load trang
- Một request CSS
```

![alt text](<screenshots/anh_cau_A1.png>)


### Câu A2
# Nguồn tham chiếu: file 04_visible_part_html.md  Semantic HTML5 — "Thẻ có ý nghĩa"; Media — Ảnh, Video, Audio.
---------------------------------------------------
Trang web trên bị Google đánh giá SEO thấp chủ yếu vì thiếu tính semantic trong HTML.Dưới đây là 4 lỗi chính:
```
Dùng <div> cho header, menu, footer  
→ Các phần này nên dùng thẻ semantic như <header>, <nav>, <footer>.

Logo chỉ là text trong <div>  
→ Nên dùng thẻ heading (<h1>) hoặc <span> trong <a> để Google hiểu đây là tên thương hiệu/trang.

Tiêu đề sản phẩm trong <div>  
→ Nên dùng thẻ heading (<h2>, <h3>) để thể hiện nội dung quan trọng.

Ảnh sản phẩm thiếu thuộc tính alt  
→ Google không thể hiểu nội dung ảnh nếu không có mô tả.

Code sửa lại:
<header>
    <h1 class="logo"><a href="/">ShopTLU</a></h1>
    <nav class="menu">
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>

<main>
    <article class="product">
        <h2 class="title">iPhone 16 Pro</h2>
        <p class="price">25.990.000đ</p>
        <figure class="image">
            <img src="iphone.jpg" alt="iPhone 16 Pro ">
        </figure>
    </article>
</main>

<footer>
    <p>© 2026 ShopTLU</p>
</footer>

```
### Câu A3
```
Mô tả kết quả hiển thị:
<div> là thẻ khối (block element) → mỗi nội dung trong <div> sẽ xuống dòng riêng.
→ Kết quả: “Hộp 1”, “Hộp 2”, “Hộp 3” mỗi cái nằm trên một dòng.
<span> là thẻ nội tuyến (inline element) → các nội dung trong <span> sẽ nằm cùng dòng nếu không có gì ngắt dòng.
→ “Text A” và “Text B” sẽ hiển thị liền nhau trên cùng một dòng.
<strong> cũng là inline, nhưng mặc định trình duyệt sẽ hiển thị chữ đậm.
→ “Text D” sẽ nằm cùng dòng với “Text C”, nhưng được in đậm.
```
### Câu A4
# nguồn Tham chiếu 05_tables_hyperlinks.md;phần table-Bảng dữ liệu
---------------------------------------------------
```
***Sự khác nhau giữa <thead>, <tbody>, <tfoot>
<thead>: chứa phần đầu bảng – thường là hàng tiêu đề.
<tbody>: chứa phần nội dung chính của bảng – các hàng dữ liệu thực tế.
<tfoot>: chứa phần chân bảng – thường dùng để hiển thị tổng cộng, ghi chú, hoặc thông tin bổ sung.


***Lý do không nên dùng <table> để tạo layout trang web:
-Không đúng mục đích
<table> được thiết kế để hiển thị dữ liệu dạng bảng, không phải để bố cục trang.
Dùng sai ngữ nghĩa khiến Google đánh giá thấp về SEO.

-Khó bảo trì và mở rộng
Layout bằng bảng rất phức tạp, khó chỉnh sửa, thêm bớt nội dung.
Thay đổi nhỏ có thể phá vỡ toàn bộ cấu trúc.

-Ảnh hưởng đến Accessibility
Trình đọc màn hình (screen reader) sẽ hiểu layout như dữ liệu bảng → gây nhầm lẫn cho người khiếm thị.
Làm giảm trải nghiệm người dùng.

-Hiệu suất và responsive kém
Bảng không linh hoạt khi hiển thị trên thiết bị di động.
CSS Flexbox/Grid hiện đại giúp responsive dễ dàng hơn nhiều.
------------------------------------------------------------------
```
### PHẦN C

### Câu C1
```
<header> <!-- header: chứa phần đầu trang (logo, menu, branding) -->
    <nav aria-label="main navigation"> <!-- nav: dùng cho khu vực chứa các link điều hướng chính -->
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>

<nav aria-label="breadcrumb"> <!-- nav: cũng là điều hướng nhưng dùng riêng cho breadcrumb -->
    <ol> <!-- ol: breadcrumb có thứ tự phân cấp (từ cha → con) -->
        <li><a href="/">Trang chủ</a></li>
        <li><a href="/phones">Điện thoại</a></li>
        <li>iPhone 16</li>
    </ol>
</nav>

<main> <!-- main: chứa nội dung chính duy nhất của trang -->
    <section class="gallery"> <!-- section: nhóm nội dung cùng chủ đề (ảnh sản phẩm) -->
        <!-- figure: dùng cho nội dung độc lập như ảnh + có thể có chú thích -->
        <figure><img src="img1.jpg" alt="Ảnh sản phẩm"></figure>
        ...
    </section>
    <section class="info"> <!-- section: nhóm thông tin chi tiết của sản phẩm -->
        <h1>Tên sản phẩm</h1> <!-- h1: tiêu đề chính quan trọng nhất của trang -->
        <p class="price">Giá</p> <!-- p: đoạn văn bản ngắn (giá là text, không phải heading) -->
        <div class="rating">Đánh giá sao</div> <!-- div: dùng khi không có thẻ semantic phù hợp -->
        <p class="description">Mô tả sản phẩm</p> <!-- p: nội dung mô tả dạng văn bản -->
    </section>
    <section class="specs"> <!-- section: nhóm nội dung thông số kỹ thuật -->
        <h2>Thông số kỹ thuật</h2>
        <table> <!-- table: dùng khi dữ liệu có dạng bảng (hàng/cột rõ ràng) -->
            <thead> <!-- thead: phần tiêu đề của bảng -->
                <tr><th>Thông số</th><th>Chi tiết</th></tr>
            </thead>
            <tbody> <!-- tbody: phần dữ liệu chính của bảng -->
                <tr><td>Màn hình</td><td>...</td></tr>
            </tbody>
        </table>
    </section>
    <section class="reviews"> <!-- section: nhóm các đánh giá -->
        <h2>Đánh giá</h2>
        <article> <!-- article: mỗi bình luận là 1 nội dung độc lập, có thể tách riêng -->
            <h3>Người dùng A</h3>
            <p>Nội dung bình luận...</p>
        </article>
    </section>
    <aside class="sidebar"> <!-- aside: nội dung phụ, liên quan nhưng không phải chính (gợi ý sản phẩm) -->
        <h2>Sản phẩm tương tự</h2>
        <ul>
            <li><a href="#">Sản phẩm 1</a></li>
            ...
        </ul>
    </aside>
</main>

<footer> <!-- footer: chứa thông tin cuối trang (bản quyền, liên hệ,...) -->
    <p>© 2026 ShopTLU</p>
</footer>

### Câu C2
Nói rằng chỉ cần <div> cho mọi thứ là bỏ qua nhiều lợi ích thực tế của semantic HTML.

Thứ nhất, về SEO: công cụ tìm kiếm dựa vào cấu trúc semantic để hiểu nội dung. Nếu trang có <header>, <nav>, <article>, Google sẽ nhận diện rõ đâu là điều hướng, đâu là nội dung chính. Ngược lại, toàn <div> khiến việc phân tích khó khăn, thứ hạng dễ bị giảm.

Thứ hai, về Accessibility: trình đọc màn hình cho người khiếm thị dựa vào các landmark semantic. Ví dụ, <nav> được đọc là “navigation”, giúp họ biết đang ở menu. Nếu chỉ là <div>, trải nghiệm sẽ kém đi rõ rệt.

Ví dụ cụ thể: một trang tin tức dùng <article> cho từng bài viết. Công cụ tìm kiếm sẽ index từng bài độc lập, và người dùng có thể nhảy nhanh giữa các bài bằng trình đọc màn hình. Nếu thay bằng <div>, cả SEO lẫn khả năng tiếp cận đều giảm.

Tất nhiên, <div> vẫn có chỗ đứng. Khi chỉ cần một container để nhóm nội dung cho mục đích trình bày, chẳng hạn <div class="grid-container"> để áp dụng CSS Grid, thì dùng <div> là hợp lý.

Tóm lại, semantic HTML không phải “tốn thời gian” mà là cách viết chuyên nghiệp, giúp trang vừa thân thiện với máy tìm kiếm, vừa dễ tiếp cận cho nhiều đối tượng.

```
### Phần B
# câu B3
```
Lỗi 1: Dòng 1 — <!DOCTYPE> thiếu loại tài liệu — Sửa thành <!DOCTYPE html>
Lỗi 2: Dòng 5 — <title> không đóng thẻ — Thêm </title>
Lỗi 3: Dòng 6 — charset="utf8" sai chuẩn — Sửa thành charset="utf-8"
Lỗi 4: Dòng 9 — <h1> không đóng đúng — Sửa thành </h1>
Lỗi 5: Dòng 13 — <a> không đóng đúng — Sửa thành </a>
Lỗi 6: Dòng 21 — <img src=iphone.jpg> thiếu dấu ngoặc kép và alt — Sửa thành <img src="iphone.jpg" alt="iPhone 16 Pro">
Lỗi 7: Dòng 23 — Thẻ <b> và <p> lồng sai thứ tự — Sửa thành <p>Giá: <b>25.990.000đ</b></p>
Lỗi 8: Dòng 29 — Bảng thiếu <thead>/<tbody> và dùng <td> cho tiêu đề — Sửa thành <th> trong <thead>
Lỗi 9: Dòng 38 — Có 2 thẻ <main> (không hợp lệ) — Sửa thẻ thứ hai thành <aside>
Lỗi 10: Dòng 43 — <p> trong footer không đóng — Thêm </p>
Lỗi 11: Dòng 44 — </footer> không khớp vì <p> chưa đóng — Đã sửa bằng cách đóng <p> trước
Lỗi 12: Dòng 45 — </body> thiếu </html> — Thêm </html> cuối file
