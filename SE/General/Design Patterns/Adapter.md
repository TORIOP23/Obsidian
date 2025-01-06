**Adapter Pattern** cho phép các inteface (giao diện) _không liên quan tới nhau_ có thể làm việc cùng nhau. Đối tượng giúp kết nối các interface gọi là Adapter.

**Tác dụng:** Adapter Pattern giữ vai trò **trung gian** giữa hai lớp, **chuyển đổi** interface của một hay nhiều lớp có sẵn thành một interface khác, thích hợp cho lớp đang viết. Điều này cho phép các lớp có các interface khác nhau có thể dễ dàng giao tiếp tốt với nhau thông qua interface trung gian, không cần thay đổi code của lớp có sẵn cũng như lớp đang viết.

Một Adapter Pattern bao gồm các thành phần cơ bản sau:
- **Adaptee**: định nghĩa interface không tương thích, cần được tích hợp vào.
- **Adapter**: lớp tích hợp, giúp interface không tương thích tích hợp được với interface đang làm việc. Thực hiện việc chuyển đổi interface cho Adaptee và kết nối Adaptee với Client.
- **Target**: một interface chứa các chức năng được sử dụng bởi Client (domain specific).
- **Client**: lớp sử dụng các đối tượng có interface Target.

Có hai cách để thực hiện Adapter Pattern dựa theo cách cài đặt (implement) của chúng:
- **Object Adapter – Composition** (Chứa trong) tốt hơn
![[object-adapter.png]]
- **Class Adapter – Inheritance** (Kế thừa)
![[class-adapter.png]]
Ví dụ: Ứng dụng Translation
![[adapter-example.png]]
**JapaneseAdaptee:** interface hoặc class được người Nhật sử dụng để nhận message được chuyển đổi từ thông dịch viên (Translator).

```java
public class JapaneseAdaptee {

    public void receive(String words) {
        System.out.println("Retrieving words from Adapter ...");
        System.out.println(words);
    }
}
```

**TranslatorAdapter:**

```java
public class TranslatorAdapter implements VietnameseTarget {
 
    private JapaneseAdaptee adaptee;
 
    public TranslatorAdapter(JapaneseAdaptee adaptee) {
        this.adaptee = adaptee;
    }
 
    @Override
    public void send(String words) {
        System.out.println("Reading Words ...");
        System.out.println(words);
        String vietnameseWords = this.translate(words);
        System.out.println("Sending Words ...");
        adaptee.receive(vietnameseWords);
    }
 
    private String translate(String vietnameseWords) {
        System.out.println("Translated!");
        return "こんにちは";
    }
}
```

**VietnameseTarget:**

```java
public interface VietnameseTarget {
    void send(String words);
}
```

**VietnameseClient:**

```java
public class VietnameseClient {
 
    public static void main(String[] args) {
        VietnameseTarget client = new TranslatorAdapter(new JapaneseAdaptee());
        client.send("Xin chào");
    }
}

Output:
Reading Words ...
Xin chào
Translated!
Sending Words ...
Retrieving words from Adapter ...
こんにちは
```