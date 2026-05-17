### PHẦN A
# Câu A1
```
Thẻ <meta viewport> chuẩn
<meta name="viewport" content="width=device-width initial-scale=1.0">

Giải thích từng thuộc tính
-width=device-width: đặt chiều rộng viewport bằng đúng chiều rộng màn hình thiết bị. Nếu thiếu, trình duyệt (như Safari trên iPhone) sẽ giả định trang web có chiều rộng mặc định ~980px rồi thu nhỏ lại.
-initial-scale=1.0: tỷ lệ zoom ban đầu là 1:1, nghĩa là không phóng to hay thu nhỏ khi tải trang.

 Nếu thiếu thẻ này, iPhone sẽ hiển thị trang web như trên màn hình desktop thu nhỏ, chữ và nút rất bé, người dùng phải zoom để đọc. Đây là lý do thẻ viewport cực kỳ quan trọng cho thiết kế web di động.
 | Cách tiếp cận | Đặc điểm | Ví dụ CSS với breakpoint 768px |
| --- | --- | --- |
| **[Mobile-First](ca://s?q=Mobile_First_la_gi)** | Bắt đầu từ giao diện di động, sau đó mở rộng cho màn hình lớn bằng ``min-width``. | ``css\\n/* ``Mobile ``mặc ``định ``*/\\nbody ``{ ``font-size: ``14px; ``}\\n\\n/* ``Desktop ``≥768px ``*/\\n@media ``(min-width: ``768px) ``{\\n ``body ``{ ``font-size: ``16px; ``}\\n}\\n`` |
| **[Desktop-First](ca://s?q=Desktop_First_la_gi)** | Bắt đầu từ giao diện desktop, sau đó thu gọn cho màn hình nhỏ bằng ``max-width``. | ``css\\n/* ``Desktop ``mặc ``định ``*/\\nbody ``{ ``font-size: ``16px; ``}\\n\\n/* ``Mobile ``≤768px ``*/\\n@media ``(max-width: ``768px) ``{\\n ``body ``{ ``font-size: ``14px; ``}\\n}\\n`` |

Tại sao Mobile-First được khuyên dùng?
Phù hợp xu hướng: phần lớn người dùng truy cập web bằng điện thoại.

Tối ưu hiệu năng: tải trước giao diện nhẹ cho mobile, sau đó thêm CSS cho màn hình lớn.

Dễ bảo trì: logic mở rộng (progressive enhancement) rõ ràng hơn so với việc phải “thu nhỏ” từ desktop xuống mobile.

SEO & UX tốt hơn: Google ưu tiên trang web thân thiện di động.
 ```
 #  Câu A2
 ```
 | **[Breakpoint](ca://s?q=Bootstrap_breakpoints)** | **Kích thước (px)** | **Thiết bị đại diện** | **Ví dụ lưới sản phẩm** |
| --- | --- | --- | --- |
| **Extra small (xs)** | ``<576px`` | Điện thoại nhỏ | 1 cột |
| **Small (sm)** | ``≥576px`` | Điện thoại lớn | 2 cột |
| **Medium (md)** | ``≥768px`` | Máy tính bảng | 3 cột |
| **Large (lg)** | ``≥992px`` | Laptop nhỏ | 4 cột |
| **Extra large (xl)** | ``≥1200px`` | Laptop lớn / màn hình desktop | 5 cột |
| **XXL (xxl)** | ``≥1400px`` | Màn hình rất lớn | 6 cột |

Giải thích cách dùng
-Mobile-First: mặc định CSS cho màn hình nhỏ, sau đó dùng min-width để mở rộng. Ví dụ: sản phẩm hiển thị 1 cột trên điện thoại, tăng dần lên 2–6 cột khi màn hình lớn hơn.
-Desktop-First: mặc định CSS cho màn hình lớn, rồi dùng max-width để thu gọn xuống mobile. Ít được khuyên dùng vì khó bảo trì.

Tại sao quan trọng?
-Người dùng di động chiếm đa số → thiết kế từ mobile trước giúp trải nghiệm tốt hơn.
-Tối ưu hiệu năng: tải ít CSS cho mobile, thêm CSS khi cần cho desktop.
-Dễ mở rộng: logic “progressive enhancement” rõ ràng.
```
# Câu A3
```
| **Chiều rộng màn hình** | **.container width** | **Giải thích** |
| --- | --- | --- |
| **375px (iPhone SE)** | 100% (≈375px) | <576px → mặc định ``width: ``100%``. |
| **600px** | 540px | ≥576px nhưng <768px → áp dụng rule đầu tiên. |
| **800px** | 720px | ≥768px nhưng <992px → áp dụng rule thứ hai. |
| **1000px** | 960px | ≥992px nhưng <1200px → áp dụng rule thứ ba. |
| **1400px** | 1140px | ≥1200px → áp dụng rule cuối cùng. |
```
# Câu A4

1. Variables
Cho phép định nghĩa biến để tái sử dụng giá trị (màu sắc, font-size, spacing…).

Ví dụ:
scss
$primary-color: #3498db;

button {
  background-color: $primary-color;
}
2. Nesting
Viết CSS lồng nhau theo cấu trúc HTML, giúp code gọn gàng và dễ đọc.

Ví dụ:
scss
nav {
  ul {
    list-style: none;
    li {
      display: inline-block;
      a {
        text-decoration: none;
        color: blue;
      }
    }
  }
}
3. Mixins
Định nghĩa khối CSS tái sử dụng, có thể truyền tham số.

Ví dụ:
scss
@mixin flex-center($gap: 10px) {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: $gap;
}

.container {
  @include flex-center(20px);
}
4. @extend / Inheritance
Cho phép một selector kế thừa thuộc tính từ selector khác.

Ví dụ:
scss
.message {
  padding: 10px;
  border: 1px solid #ccc;
}

.success {
  @extend .message;
  border-color: green;
}

Tại sao trình duyệt KHÔNG đọc được file .scss?
SCSS là ngôn ngữ tiền xử lý (preprocessor), không phải CSS thuần.
Trình duyệt chỉ hiểu CSS, không hiểu cú pháp SCSS.

 Cần bước biên dịch (compile) SCSS → CSS bằng công cụ như Sass CLI, Webpack, Gulp, hoặc tích hợp trong framework (React, Angular, Vue…).