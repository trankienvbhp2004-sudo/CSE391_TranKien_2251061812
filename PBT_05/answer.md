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