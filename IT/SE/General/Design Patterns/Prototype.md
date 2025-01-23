Prototype có nhiệm vụ khởi tạo một đối tượng bằng cách **clone** một đối tượng đã tồn tại thay vì khởi tạo với từ khoá **new**. Đối tượng mới là một bản sao có thể giống 100% với đối tượng gốc, chúng ta có thể thay đổi dữ liệu của nó mà không ảnh hưởng đến đối tượng gốc.

**Tác dụng:**
– Cải thiện **performance** (không sử dụng **new** để tạo ra một object mới)
– Giảm độ phức tạp cho việc khởi tạo đối tượng
– Giảm việc phân lớp, tránh việc tạo nhiều sub-class cho việc khởi tạo đối tượng
– Khởi tạo object mới bằng cách thay đổi cấu trúc hoặc một vài thuộc tính của object

Trong Java cung cấp mẫu prototype pattern này bằng việc implement interface **Cloneable** và sử dụng method **clone()** để tạo object có đầy đủ thuộc tính của đối tượng ban đầu.

Một Prototype Pattern gồm các thành phần cơ bản sau:
- **Prototype**: khai báo một class, interface hoặc abstract class cho việc clone chính nó.
- **ConcretePrototypes**: các lớp này thực thi interface (hoặc kế thừa từ lớp abstract) được cung cấp bởi Prototype để copy (nhân bản) chính bản thân nó. Các lớp này chính là thể hiện cụ thể phương thức clone(). Lớp này có thể không cần thiết nếu: Prototype là một class và nó đã implement việc clone chính nó.
- **Client**: tạo mới object bằng cách gọi Prototype thực hiện clone chính nó.
![[prototype.png]]

**ConcretePrototype:**
```java
public class Computer implements Cloneable {
    private String os;
    private String office;
    private String antivirus;
    private String browser;
    private String others;
 
    public Computer(String os, String office, String antivirus, String browser, String other) {
        super();
        this.os = os;
        this.office = office;
        this.antivirus = antivirus;
        this.browser = browser;
        this.others = other;
    }
 
    @Override
    protected Computer clone() {
        try {
            return (Computer) super.clone();
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }
        return null;
    }
 
    @Override
    public String toString() {
        return "Computer [os=" + os + ", office=" + office + ", antivirus=" + antivirus + ", browser=" + browser
                + ", others=" + others + "]";
    }
 
    public void setOthers(String others) {
        this.others = others;
    }
}
```

**Client:**
```java
public class Client {
 
    public static void main(String[] args) {
        Computer computer1 = new Computer("Window 10", "Word 2013", "BKAV", "Chrome v69", "Skype");
        Computer computer2 = computer1.clone();
        computer2.setOthers("Skype, Teamviewer, FileZilla Client");
 
        System.out.println(computer1);
        System.out.println(computer2);
    }
}

Output:
Computer [os=Window 10, office=Word 2013, antivirus=BKAV, browser=Chrome v69, other=Skype]
Computer [os=Window 10, office=Word 2013, antivirus=BKAV, browser=Chrome v69, other=Skype, Teamviewer, FileZilla Client]
```

Như vậy, computer có đầy đủ các giá trị được clone từ computer1 và chúng ta có thể thay đổi giá trị của computer2 mà không ảnh hưởng đến computer1.