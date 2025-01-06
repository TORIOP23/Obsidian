- Virtual Constructor
- **Factory Method** là một mẫu thiết kế sáng tạo cung cấp giao diện để tạo các đối tượng trong lớp cha, nhưng cho phép các lớp con thay đổi kiểu đối tượng sẽ được tạo.

# Factory Method

- **Ngữ cảnh**: Tạo một framework cho ứng dụng đa cửa sổ. Hai phần tử chính trong ứng dụng này là Application và Document (đều là trừu tượng). Người dùng framework phải kế thừa hai lớp này để viết ứng dụng. Application tạo và quản lý Document. Vì Document được kế thừa về sau nên Application không biết được lớp con của Document.
- **Vấn đề**: _Application tạo và quản lý lớp con (chưa biết) của Document_
- **Phương án**: định nghĩa interface để tạo đối tượng nhưng để cho lớp con xác định lớp nào sẽ được sử dụng (để tạo đối tượng)
- **Tác dụng**:
	- Tách biệt việc tạo đối tượng và sử dụng đối tượng và giảm sự phụ thuộc giữa các **lớp sử dụng** (StudentManager) và **lớp cụ thể** (PrimaryStudent, SecondaryStudent, HighStudent, CollegeStudent).
	- Mở rộng và tái sử dụng code dễ dàng
	- Che giấu thông tin chi tiết về cách khởi tạo đối tượng khỏi các client sử dụng nó
	- Dễ dạng quản lý _life cycle_ của các Object

Một Factory Pattern bao gồm các thành phần cơ bản sau:
- **Super Class**: môt supper class trong Factory Pattern có thể là một **interface**, **abstract class** hay một **class** thông thường.
- **Sub Classes**: các sub class sẽ implement các phương thức của **supper class** theo nghiệp vụ riêng của nó.
- **Factory Class**: một class chịu tránh nhiệm khởi tạo các đối tượng **sub class** dựa theo tham số đầu vào. Lưu ý: lớp này là **Singleton** [](https://gpcoder.com/4190-huong-dan-java-design-pattern-singleton/)hoặc cung cấp một **public static method** cho việc truy xuất và khởi tạo đối tượng. Factory class sử dụng if-else hoặc switch-case để xác định class con đầu ra.
![[fatory-method.png]]

Chương trình được cài đặt theo Factory Pattern như sau:

**Super Class:**
```java
//Document
public interface Bank {
    String getBankName();
}
```

**Sub Classes:**
```java
public class TPBank implements Bank {
 
    @Override
    public String getBankName() {
        return "TPBank";
    }
 
}
```

```java
public class VietcomBank implements Bank {
 
    @Override
    public String getBankName() {
        return "VietcomBank";
    }
 
}
```

**Factory class:**
```java
//Application
public class BankFactory {
 
    private BankFactory() {}
 
    //factory method
    public static final Bank getBank(BankType bankType) {
        switch (bankType) {
 
        case TPBANK:
            return new TPBank();
 
        case VIETCOMBANK:
            return new VietcomBank();
 
        default:
            throw new IllegalArgumentException("This bank type is unsupported");
        }
    }
 
}
```

**Bank type:**
```java
public enum BankType {
    VIETCOMBANK, TPBANK;
}
```

**Client:**
```java
public class Client {
 
    public static void main(String[] args) {
        Bank bank = BankFactory.getBank(BankType.TPBANK);
        System.out.println(bank.getBankName()); // TPBank
    }
}
```

Như vậy, phía client chỉ cần gọi duy nhất một phương thức **BankFactory.getBank()** là có thể sử dụng được dịch vụ của một ngân hàng bất kỳ.

Khi hệ thống muốn cung cấp thêm dịch vụ của một ngân hàng khác, chẳng hạn VietinBank, thì cần tạo thêm một class mới implement từ interface Bank (super class), và thêm vào logic khởi tạo Bank trong BankFactory là xong. Nó không làm ảnh hưởng đến code ở phía Client.