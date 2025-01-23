- The same port number can be used by multiple sockets. So, there is no limit to the number of sockets in terms of ports
- A socket just a file. 
![[socket.png]]
- Socket chính là cửa giao tiếp giữa tần ứng dụng và tầng giao vận
- Socket là giao diện do ứng dụng tạo ra trên máy trạm, quản lí bởi hệ điều hành qua đó các ứng dụng có thể gửi/nhận thông điệp đến/từ các ứng dụng khác. Ở đó, Socket sẽ được ràng buộc với một mã số cổng (Port Number) để giúp tầng giao vận định danh được ứng dụng nhận/gửi thông điệp.
- Ở TCP (Transmission Control Protocol) và UDP (User Datagram Protocol)
- 3 loại sockets
    - Stream Socket (TCP): tạo luồng dữ liệu 2 chiều đáng tin cậy có trình tự và k trùng lặp, dữ liệu chỉ được gửi/ nhắn khi đã có liên kết
    - Datagram Socket (UDP): Có thể nhận dữ liệu không theo trình tự, trùng lặp.
    - Multicast Socket : cho phép dữ liệu được gửi đến nhiều bên nhận 1 lúc.
    - ![[socket-2.png]]
- với số cổng là một số ngẫu nhiên lớn hơn 1024 ( trong một số hệ thống yêu cầu đặc quyền quản trị để ràng buộc số cổng < 1024)
## Reference
- [Interview Post](https://www.linkedin.com/posts/interview-ready_how-many-socket-connections-can-one-server-activity-7108811787973619712-chPT#:~:text=A%20socket%20is%20a%20logical,sockets%20in%20terms%20of%20ports.)