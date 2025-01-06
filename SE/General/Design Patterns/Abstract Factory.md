**Abstract Factory** là phương pháp tạo ra một Super-factory dùng để tạo ra các Factory khác. Hay còn được gọi là Factory của các Factory.

Abstract Factory Pattern là một Pattern cấp cao hơn so với Factory Method Pattern.
Hãy tưởng tượng, Abstract factory như là một nhà máy lớn chứa nhiều nhà máy nhỏ, trong các nhà máy đó có những xưởng sản xuất, các xưởng đó tạo ra những sản phẩm khác nhau.

**Tác dụng:**
– Che giấu sự phức tạp của việc khởi tạo các đối tượng với người dùng (client), độc lập giữa việc khởi tạo đối tượng và hệ thống sử dụng,…
– Khi một **Factory Method** lớn (có quá nhiều sử lý if-else hay switch-case), chúng ta nên sử dụng theo mô hình **Abstract Factory** để dễ quản lý hơn (cách phân chia có thể là gom nhóm các sub-class cùng loại vào một Factory). – Hỗ trợ phân cấp giúp tạo ra cấu trúc dạng cây, trong đó một Abstract Factory cha có thể có nhiều Abstract Factory con, mỗi Factory con tạo ra một nhóm đối tượng cụ thể. – Dễ dàng thay đổi hoặc mở rộng nhóm đối tượng

Một Abstract Factory Pattern bao gồm các thành phần cơ bản sau:
- **AbstractFactory**: Khai báo dạng interface hoặc abstract class chứa các phương thức để tạo ra các đối tượng abstract.
- **ConcreteFactory**: Xây dựng, cài đặt các phương thức tạo các đối tượng cụ thể.
- **AbstractProduct**: Khai báo dạng interface hoặc abstract class để định nghĩa đối tượng abstract.
- **Product**: Cài đặt của các đối tượng cụ thể, cài đặt các phương thức được quy định tại AbstractProduct.
- **Client**: là đối tượng sử dụng AbstractFactory và các AbstractProduct.
![[abstract-factory.png]]
**Super Factory Class:**

```java
public class FurnitureFactory {
 
    private FurnitureFactory() {}
 
    // Returns a concrete factory object that is an instance of the
    // concrete factory class appropriate for the given architecture.
    public static FurnitureAbstractFactory getFactory(MaterialType materialType) {
        switch (materialType) {
        case FLASTIC:
            return new FlasticFactory();
        case WOOD:
            return new WoodFactory();
        default:
            throw new UnsupportedOperationException("This furniture is unsupported ");
        }
    }
}
```

**AbstractFactory:**

```java
public abstract class FurnitureAbstractFactory {
 
    public abstract Chair createChair();
 
    public abstract Table createTable();
     
}
```

**ConcreteFactories:**

```java
// FlasticFactory
public class FlasticFactory extends FurnitureAbstractFactory {
 
    @Override
    public Chair createChair() {
        return new PlasticChair();
    }
 
    @Override
    public Table createTable() {
        return new PlasticTable();
    }
 
}
```

```java
// WoodFactory
public class WoodFactory extends FurnitureAbstractFactory {
 
    @Override
    public Chair createChair() {
        return new WoodChair();
    }
 
    @Override
    public Table createTable() {
        return new WoodTable();
    }
}
```

**AbstractProduct và Products:**

_Chair:_
```java
public interface Chair {
    void create();
}
```

```java
public class PlasticChair implements Chair {
    @Override
    public void create() {
        System.out.println("Create plastic chair");
    }
}
```

```java
public class WoodChair implements Chair {
    @Override
    public void create() {
        System.out.println("Create wood chair");
    }
}
```

_Table:_
```java
public interface Table {
    void create();
}
```

```java
public class PlasticTable implements Table {
    @Override
    public void create() {
        System.out.println("Create plastic table");
    }
}
```

```java
public class WoodTable implements Table {
    @Override
    public void create() {
        System.out.println("Create wood table");
    }
}
```

_Material type:_
```java
public enum MaterialType {
    FLASTIC, WOOD
}
```

**Client:**

```java
public class Client {
 
    public static void main(String[] args) {
 
        FurnitureAbstractFactory factory = FurnitureFactory.getFactory(MaterialType.FLASTIC);
 
        Chair chair = factory.createChair();
        chair.create(); // Create plastic chair
 
        Table table = factory.createTable();
        table.create(); // Create plastic table
    }
}
```

Như vậy, phía Client chỉ cần gọi phương thức **FurnitureFactory.getFactory()** là có thể sử dụng được các dịch vụ của một Factory bất kỳ.

Khi hệ thống phát triển cần mở rộng thêm 1 nhà máy khác, chẳng hạn sản xuất hàng hóa bằng inox, thì đơn giản cần tạo thêm một class mới implement từ **FurnitureAbstractFactory**, và thêm vào logic khởi tạo Funiture trong **FurnitureFactory**. Nó không làm ảnh hưởng đến code ở phía **Client**.

Một ví dụ khác:
![[abstract-factory-2.png]]