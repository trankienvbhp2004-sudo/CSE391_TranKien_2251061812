# Phần A
# Câu A1
# nguồn tham chiếu: phần Form cơ bản — Anatomy / 07_forms_interactive.md

1. type="email" → Ô nhập text, tự kiểm tra có @ → Dùng cho form đăng ký
2. type="password" -> ô nhập tẽt nhưng có ký tự hiển thị dấu *, thường kết hợp với pattern/maxlength->dùng cho form đăng nhập
3. type="number"-> ô nhập số, chỉ phép nhập số->chọn số lượng sản phẩm trong giỏ hàng 
4. type="tel"-> ô nhập text, có thể dùng pattern->nhập số điện thoại để giao hàng
5. type="url"->ô nhập text, kiểm tra định dạng URL hợp lệ(http hoặc https)->nhập link website của nhà cung cấp hoặc đối tác
6. type="date"->hiển thị calendar picker, chỉ cho phépchọn ngày hợp lệ->chọn ngày giaohàng hoặc ngày sinh khi đăng ký
7 type="time"-> hiển thị đồng hồ chọn giờ, chỉ cho phép nhậpgiờ hợp lệ->chọn khung giờ giao hàng.
8. type="color"-> hiển thị bảng chọn màu , giá trị trả về là mã màu hex->chọn màu sản phẩm
9. type="range"->thanh trượt(slider), giá trị trả về nằm trong khoảng min-max->chọn khoảng giá sản phẩm khi lọc
10. type="file"->nút chọn file từ máy tính, kiểm tra có file được chọn , có thể giới hạn loại file->khách upload ảnh để đổi trả hàng
# Câu A2
# nguồn tham chiếu: phần Các input types HTML5 file 07_forms_interactive.md
-trường hợp 1 thì fỏm sẽ không submit được và web báo lỗi.
 Vì thuộc tính required kiểm tra rỗng , nếu không có gì thì validation thát bại

-Trường hợp 2:  Form không submit được. Trình duyệt báo lỗi 
Vì với type="email", trình duyệt kiểm tra định dạng email hợp lệ(thiếu @)

Trường hợp 3:  Trình duyệt báo lỗi vì giá trị vượt quá max=10.
Với type="number", trình duyệt kiểm tra giá trị nằm trong khoảng min–max. 15 > 10 nên invalid.

Trường hợp 4: Form không submit được. Trình duyệt báo lỗi vì không khớp pattern.
```
Giải thích: Pattern yêu cầu đúng 10 chữ số ([0-9]{10}). “abc123” chứa chữ cái và chỉ có 3 số, không hợp lệ.
```

Trường hợp 5: Form không submit được. Trình duyệt báo lỗi vì độ dài < 8 ký tự.

Giải thích: Thuộc tính minlength yêu cầu ít nhất 8 ký tự, nhưng “123” chỉ có 3 ký tự.

# kêts quả thực tế hoàn toàn trùng khớp với dự đoán trước đó =D
![alt text](<screenshots/anh_CauA2.png>)

# Câu A3
# tham khảo phần Accesibility file 07_forms_interactive.md
```
1. Screen reader đọc nội dung của thẻ <label> và liên kết nó với input có id="email".

Nhờ vậy, người khiếm thị sẽ nghe được “Email” trước khi nhập dữ liệu, thay vì chỉ nghe “edit box” chung chung.

Điều này giúp họ hiểu rõ mục đích của ô nhập, tăng khả năng tiếp cận và giảm nhầm lẫn.
2. Dùng khi có nhóm các input liên quan cùng một chủ đề.

<fieldset> tạo khung nhóm, <legend> mô tả nội dung của nhóm.
3.``` aria-label dùng để cung cấp mô tả cho thành phần không có văn bản hiển thị rõ ràng (ví dụ: icon button chỉ có hình ảnh, không có text).

Nếu đã có <label> thì không nên dùng aria-label vì:

<label> là cách chuẩn, được hỗ trợ tốt nhất cho cả SEO lẫn accessibility.

Dùng cả hai có thể gây xung đột hoặc khiến screen reader đọc trùng lặp.
```
# Câu A4-Media
1. giảm thời gian tải trang ban đầu, tiết kiệm băng thông, tăng hiệu suất cho trang có nhiều ảnh (ví dụ trang sản phẩm).
Khi KHÔNG nên dùng: với ảnh quan trọng hiển thị ngay khi mở trang (logo, banner chính, ảnh hero), vì nếu lazy load thì người dùng sẽ thấy trễ hoặc trống.
2. Trình duyệt khác nhau hỗ trợ định dạng video khác nhau.
Cung cấp nhiều <source> giúp đảm bảo video chạy được trên hầu hết trình duyệt.
-3 format phổ biến: MP4 (H.264), WebM, Ogg/Theora.
3. Ý nghĩa: cung cấp văn bản thay thế cho ảnh, giúp screen reader đọc cho người khiếm thị, đồng thời hiển thị khi ảnh không tải được.

Viết alt tốt cho 3 trường hợp:

Ảnh sản phẩm iPhone 16 → alt="iPhone 16 màu đen, mặt trước và sau"

Ảnh trang trí (decorative) → alt="" (để screen reader bỏ qua, tránh gây nhiễu)

Ảnh biểu đồ doanh thu Q1/2026 → alt="Biểu đồ cột doanh thu quý 1 năm 2026, doanh thu tăng 20% so với quý trước".
# Câu A5
1. Cách 1 phù hợp cho ảnh đơn giản, chỉ cần alt để hỗ trợ accessibility.
Ví dụ thực tế:Ảnh logo thương hiệu ở góc trang web → alt="Logo Apple"

2. Cách 2 phù hợp cho ảnh cần thêm ngữ cảnh hoặc thông tin chi tiết, giúp người dùng (và cả screen reader) hiểu rõ hơn nội dung ảnh.
Ví dụ thực tế:Trang sản phẩm E-Commerce: ảnh iPhone kèm chú thích giá bán → figcaption="iPhone 16 Pro Max — 25.990.000đ"

