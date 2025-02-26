![[socket.png]]
- The same port number can be used by multiple sockets. So, there is no limit to the number of sockets in terms of ports
- A socket just a file. Socket xây dựng trên giao thức TCP và UDP
# Phân loại Socket
## Stream Socket
- **TCP**, dữ liệu chỉ được gửi khi đã có liên kết
- Tạo luồng dữ liệu 2 chiều đáng tin cậy và có trình tự.
### Web Socket
- Dùng HTTP để thiết lập kết nối
### [[RSocket]]
- TCP, WebSocket, Aeron
## Datagram Socket
- **UDP**, có thể hoạt động khi chưa kết nối với nhau.

## Unix Socket
- Trên cùng 1 máy tính. Diễn ra trong OS

# Reference
- [Interview Post](https://www.linkedin.com/posts/interview-ready_how-many-socket-connections-can-one-server-activity-7108811787973619712-chPT#:~:text=A%20socket%20is%20a%20logical,sockets%20in%20terms%20of%20ports.)