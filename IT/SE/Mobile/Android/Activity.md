- Điểm vào tương tác với người dùng. Đại diện cho 1 màn hình duy nhất với giao diện người dùng
- 1 hoạt động cho các tương tác với hệ thống
    - Theo dõi những gì người dùng hiện quan tâm, hệ thống lưu trữ hoạt động
    - Biết quy trình sử dụng trước đó chứa các hoạt động đã dừng
    - Giúp ứng dụng xử lý quá trình khôi phục trạng thái trước khi bị tắt
    - Cung cấp 1 cách để các ứng dụng triển khai luồng người dùng lẫn nhau
### Vòng đời của Activity
![[activity-1.png]]
### Các phương thức trạng thái của Activity
![[activity-2.png]]
### saveInstanceState

Một trong các thành phần của trạng thái trong vòng đời của một Activity.
- Một loại dữ liệu không bền vững.
- Không được lưu trữ cụ thể trong đâu ngoài bộ nhớ RAM.
- Nó được sử dụng để truyền, phục hồi, lưu trạng thái của một Activity.
- Dữ liệu trong **savedInstanceState** được lưu dưới dạng **Bundle**.
- Được phục hồi khi phương thức **`onCreate`** và **`onRestoreSavedInstanceState`** được gọi.
- Được lưu trước `**onStop**`, với phương thức `**onSaveInstanceState**.`

<aside> 💡 Cả Activity sẽ bị destroy khi bị xoay màn hình

</aside>

- Lấy ví dụ đơn giản: Bạn viết một app máy tính bỏ túi đơn giản, chỉ có cộng trừ. Sau khi tính xong phép tính 2+3=5, bạn xoay màn hình, phép tính biến mất.