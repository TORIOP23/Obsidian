
### [[Dagger & Hilt]]

## [[Navigation Component]]

- fastland
- **ANR** là viết tắt của Application Not Responding (Ứng dụng không phản hồi).
- Có 2 đơn vị là sp (_scalable pixels) và dp (density-independent pixels_ (DP)

## [[Activity]]
## Services
- Tổng quan
    - Là 1 điểm vào có mục đích chung để giữ cho ứng dụng chạy trong nền vì mọi lý do.
    - Nó là 1 thành phần chạy trong nền để thực hiện các hoạt động dài hoặc để thực hiện công việc cho các quy trình từ xa
    - Không cung cấp giao diện
    - Ví dụ: phát nhạc trong nền
    - 2 loại services: Start service và Bound service
- Service
    - onBind
    - onCreate
    Khai báo trong Manifest
    - `<service android:name=".ExampleService"/>`

## Broadcast receivers
- Broadcast receivers
    - Một thành phần cho phép hệ thống phân phối các sự kiện đến ứng dụng bên ngoài luồng người dùng thông thường để ứng dụng có thể phản hồi các thông báo truyền phát trên toàn hệ thống.
    - Vì bộ thu quảng bá là một mục khác được xác định rõ ràng trong ứng dụng nên hệ thống có thể phân phối quảng bá ngay cả với các ứng dụng hiện không chạy.
    - Vì vậy, ví dụ: một ứng dụng có thể lên lịch báo thức để đăng thông báo cho người dùng biết về một sự kiện sắp tới. Vì báo thức được gửi đến một  `BroadcastReceiver` trong ứng dụng nên ứng dụng không cần tiếp tục chạy cho đến khi báo thức kêu.
    - A broadcast receiver is just a _gateway_ to other components and is intended to do a very minimal amount of work.

## Content providers
- Content providers

## **Activate components**
- Một thông báo không đồng bộ được gọi là **Intent** kích hoạt ba trong số bốn loại thành phần: hoạt động, dịch vụ và bộ thu quảng bá
- **Intent**
    - Intent ****Explicit
        - Intent có đích đến rõ ràng (là các class khác), có thể bao gồm dữ liệu thêm (extra data)
        ```java
        Intent intent = new Intent(MainActivity.this, SecondActivity.class);
        
        intent.putExtra("Key", "Value");
        ```
        
    - Intent Implicit
        Dạng Intent mà có thể có nhiều đích đến xử lý nó: Ví dụ khi muốn mở 1 URL thì các trình duyệt web của điện thoại đều có thể bắt được Intent này
        ```java
        Intent i = new Intent(Intent.ACTION_VIEW, Uri.parse("<http://howkteam.com/>"));
        ```
        

Có các phương pháp riêng để kích hoạt từng loại thành phần:
- Bắt đầu một hoạt động hoặc cung cấp cho nó một việc gì đó mới để làm = cách passing **Intent** to `startActivity()` hoặc khi bạn muốn hoạt động trả về kết quả, `startActivityForResult().`
- Trên Android 5.0 (API cấp 21) trở lên, sử dụng **JobScheduler** lớp để lên lịch hành động. Đối với các phiên bản Android cũ hơn, Bắt đầu một dịch vụ hoặc đưa ra hướng dẫn mới cho một dịch vụ đang diễn ra bằng cách passing Intent to `startService().` Liên kết với dịch vụ bằng cách chuyển passing Intent to `bindService().`
- Bạn có thể bắt đầu truyền phát bằng cách truyền một Intentphương thức như sendBroadcast()hoặc sendOrderedBroadcast().
- Bạn có thể thực hiện truy vấn tới nhà cung cấp nội dung = cách gọi `query()` on a **ContentResolver.**