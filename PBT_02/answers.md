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
# nguồn tham chiếu:
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
![alt text](<screenshots/anh_CauA2.png.png>)