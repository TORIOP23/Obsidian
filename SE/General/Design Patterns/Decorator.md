**Decorator Pattern** cho phép người dùng thêm chức năng mới vào đối tượng hiện tại mà không muốn ảnh hưởng đến các đối tượng khác.

Kiểu thiết kế này có cấu trúc hoạt động như một lớp bao bọc (wrap) cho lớp hiện có. Mỗi khi cần thêm tính năng mới, đối tượng hiện có được wrap trong một đối tượng mới (decorator class).

Decorator pattern sử dụng **composition (has-a)** thay vì inheritance (is-a) để mở rộng đối tượng. Decorator pattern còn được gọi là **Wrapper** hay **Smart Proxy**.

**Tác dụng:**
- Tăng cường khả năng mở rộng của đối tượng, bởi vì những thay đổi được thực hiện bằng cách implement trên các lớp mới.
- Client sẽ không nhận thấy sự khác biệt khi bạn đưa cho nó một wrapper thay vì đối tượng gốc.
- Một đối tượng có thể được bao bọc bởi nhiều wrapper cùng một lúc.
- Cho phép thêm hoặc xóa tính năng của một đối tượng lúc thực thi (run-time).
![[decorator-1.png]]
Các thành phần trong mẫu thiết kế Decorator:
- **Component**: là một interface quy định các method chung cần phải có cho tất cả các thành phần tham gia vào mẫu này.
- **ConcreteComponent**: là lớp hiện thực (implements) các phương thức của Component.
- **Decorator**: là một abstract class dùng để duy trì một tham chiếu của đối tượng Component và đồng thời cài đặt các phương thức của Component interface.
- **ConcreteDecorator**: là lớp hiện thực (implements) các phương thức của Decorator, nó cài đặt thêm các tính năng mới cho Component.
- **Client**: đối tượng sử dụng Component.

**Ví dụ**: Xây dựng ứng dụng trong đó có chức năng gửi thông báo qua **nhiều kênh khác nhau** và có thể gửi qua **nhiều kênh cho** **cùng 1 thông điệp** cũng như gửi **nhiều loại thông báo cùng một lúc**.
![[decorator-2.png]]
![[decorator-3.png]]