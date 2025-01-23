[Pub/Sub Made Easy](https://www.youtube.com/playlist?list=PLIivdWyY5sqKwVLe4BLJ-vlh9r9zCdOse)

- **Sender** được gọi là **publishers** và **Receiver** gọi là **Subscriber**
- **Topic**: là tên của tài nguyên (**resource**) chứa những tin nhắn được gửi lên bởi **publisher**.
- **Subscription**: Tên của tài nguyên đại diện cho các dòng tin nhắn từ một hoặc một topic cụ thể nào đó được chuyển (**delivered**) đến **Subscriber**.
- **Message**: tin nhắn – kết hợp giữa dữ liệu và các **attributes** mà **publisher** gửi lên topic và chuyển đến **subscribers**.
- **Message attribute**: Là các cặp key-value mà **publisher** có thể định nghĩa cho message. Ví dụ: **publisher** định nghĩa ra cặp key-value là **[ana.org/language_tag](http://ana.org/language_tag) = en**, và cặp key-value được gắn vào message để đánh dấu message này dành cho **subscriber** nói tiếng anh.
- Trong Cloud Pub/Sub có chứa nhiều **Topic**, một **Topic** có thể có nhiều **Subscription** , Mỗi **Subscripton** chứa nhiều **Message**
![[pub-sub-1.png]]
### Luồng hoạt động
1. **Pulisher** tạo **Topic** trên **Cloud Pub/Sub service** và gửi **messsage** lên **Topic**. một **messaage** chứa nội dung tin nhắn và có thể có thêm mô tả (**message attributes**) cho tin nhắn đó.
2. **Message** sẽ được lưu trữ tại **Message Storage** cho đến khi tin nhắn được chuyển đến cho **subscribers** và nhận được phản hồi kết quả từ **subscribers.**
3. **Cloud Pub/Sub** sẽ chuyển tiếp **message** từ **topic** đến hàng đợi của tất cả **subscriptions** của nó. Mỗi **subscriptions** sau khi được tin nhắn, nó sẽ đẩy (**push**) **message** đó về cho **subscriber**. Hoặc **subscriber** có thể tự kéo (**pull**) **message** từ một **subscription** nào đó.
4. **Subscriber** nhận được **message** đang chờ xử lý từ **subscription**. **Subscriber** sẽ xác nhận (**ACK**) từng tin nhắn từ **subscription** .
5. Khi **subscription** nhận được tin nhắn xác nhận (**ACK**) của **message** đó thì thì **message** đó sẽ được xóa khỏi hàng đợi của **subscription**
![[pub-sub-2.png]]
Cloud Pub/Sub là bất đồng bộ (**asynchronous**) và không có trạng thái (**stateless**). Một message được gửi từ **Publisher** đến **Subscription**. Ở đây, **Subscriber** sẽ có 2 cách để có được **message**:
- **Subscriber** kéo (**pull**) **message**: **Subscriber** chủ động lấy tin nhắn từ **subscription**, Mỗi lần lấy 1 **message** và chỉ cần thông qua giao thức http.
- **Subscription** đẩy (push) **message**: **Subscriber** sẽ nhận **message** thụ động từ **subscription**, lúc này phải chỉ cho **subscription** cần đẩy **message** về **Subscriber** nào và phải thông qua giao thức https.
Cloud Pub/Sub đảm bảo là **Subscriber** nhận ít nhất 1 message. Nguyên nhân do một phần do cơ chế xác nhận tin nhắn của nó, **Cloud Pub/Sub** xóa tin nhắn nếu nó nhận được phản hồi xác nhân (**ACK**). Nếu **Subscriber** nhận được **message** nhưng phản hồi chậm hoặc không phản hồi thì **message** đó sẽ được gửi lại lần nữa cho đến khi nhận được phản hồi.
Khi một **message** _không_ được gửi đến cho **subscriber** nào thì sẽ bị xóa sau thời gian là **7 ngày**. Do đó **Cloud Pub/Sub** không phải là nơi để mà lưu trữ **message**. Các bạn muốn lưu trữ lại **message** thì thêm 1 **subcription** để queue tin nhắn và 1 **Subscriber** lấy **message** để lưu. Bên dưới là một số service / application có thể làm **publisher** và **subscriber**.