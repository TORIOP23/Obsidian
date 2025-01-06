- Là một mẫu thiết kế cấu trúc cho phép bạn bố cục các đối tượng thành cấu trúc cây và sau đó làm việc với các cấu trúc này như thể chúng là các đối tượng riêng lẻ.

### **Intent**
- Soạn các đối tượng thành cấu trúc cây để biểu diễn phân cấp toàn bộ phần. Composite cho phép khách hàng xử lý các đối tượng riêng lẻ và bố cục của các đối tượng một cách đồng nhất.
- Recursive composition
- "Thư mục chứa các mục nhập, mỗi mục có thể là một thư mục."
- 1-to-many "has a" up the "is a" hierarchy

### **Problem**
- Ứng dụng cần thao tác một tập hợp phân cấp của các đối tượng "nguyên thủy" và "hỗn hợp". Xử lý một đối tượng nguyên thủy được xử lý theo một cách và xử lý một đối tượng hỗn hợp được xử lý theo cách khác. Việc phải truy vấn "loại" của từng đối tượng trước khi cố gắng xử lý nó là điều không mong muốn.
![[composite.png]]
- Giả sử bạn quyết định tạo một hệ thống đặt hàng sử dụng các lớp này. Đơn đặt hàng có thể chứa các sản phẩm đơn giản mà không có bất kỳ bao bì nào, cũng như các hộp chứa các sản phẩm ... và các hộp khác. Làm thế nào bạn xác định được tổng giá của một đơn đặt hàng như vậy?

### **Solution**
- Mẫu Composite đề xuất rằng bạn làm việc với `Products`và `Boxes`thông qua một giao diện chung khai báo một phương pháp tính tổng giá.
- Phương pháp này sẽ hoạt động như thế nào? Đối với một sản phẩm, nó chỉ đơn giản là trả lại giá của sản phẩm. Đối với một hộp, nó sẽ xem xét từng mục trong hộp, hỏi giá của nó và sau đó trả về tổng số cho hộp này. Nếu một trong những mặt hàng này là một hộp nhỏ hơn, hộp đó cũng sẽ bắt đầu xem xét nội dung của nó, v.v., cho đến khi giá của tất cả các thành phần bên trong được tính. Một hộp thậm chí có thể thêm một số chi phí bổ sung vào giá cuối cùng, chẳng hạn như chi phí đóng gói.