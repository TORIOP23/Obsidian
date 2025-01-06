Proxy Pattern là mẫu thiết kế mà ở đó tất cả các truy cập trực tiếp đến một đối tượng nào đó sẽ được _**chuyển hướng vào một đối tượng trung gian**_ (Proxy Class).

Proxy giải quyết vấn đề security, perfomance, validation,…

**Tác dụng:**
- Cãi thiện Performance thông qua lazy loading, chỉ tải các tài nguyên khi chúng được yêu cầu.
- Nó cung cấp sự bảo vệ cho đối tượng thực từ thế giới bên ngoài.
- Giảm chi phí khi có nhiều truy cập vào đối tượng có chi phí khởi tạo ban đầu lớn.
- Dễ nâng cấp, bảo trì.

Proxy Pattern còn được gọi là **Surrogate** (thay thế) hoặc **Placeholder** (trình giữ chỗ).
![[proxy-1.png]]
Proxy Pattern có những đặc điểm chung sau đây:
- Cung cấp mức truy cập gián tiếp vào một đối tượng.
- Tham chiếu vào đối tượng đích và chuyển tiếp các yêu cầu đến đối tượng đó.
- Cả Proxy và đối tượng đích đều kế thừa hoặc thực thi chung một lớp giao diện. Mã máy dịch cho lớp giao diện thường “nhẹ” hơn các lớp cụ thể và do đó có thể giảm được thời gian tải dữ liệu giữa server và client.
![[proxy-2.png]]
Các thành phần tham gia vào mẫu Proxy Pattern:
- **Subject** : là một interface định nghĩa các phương thực để giao tiếp với client. Đối tượng này xác định giao diện chung cho RealSubject và Proxy để Proxy có thể được sử dụng bất cứ nơi nào mà RealSubject mong đợi.
- **Proxy** : là một class sẽ thực hiện các bước kiểm tra và gọi tới đối tượng của class service thật để thực hiện các thao tác sau khi kiểm tra. Nó duy trì một tham chiếu đến RealSubject để Proxy có thể truy cập nó. Nó cũng thực hiện các giao diện tương tự như RealSubject để Proxy có thể được sử dụng thay cho RealSubject. Proxy cũng điều khiển truy cập vào RealSubject và có thể tạo hoặc xóa đối tượng này.
- **RealSubject** : là một class service sẽ thực hiện các thao tác thực sự. Đây là đối tượng chính mà proxy đại diện.
- **Client** : Đối tượng cần sử dụng RealSubject nhưng thông qua Proxy.

Abstract Factory