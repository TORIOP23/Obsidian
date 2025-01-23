
- Singleton cho nhiều đối tượng
```java
public class Singleton { 
	private static Singleton[] instances = new Singleton[numOfInstances]; 
	private Singleton() { //constr } 
	public static Singleton getInstance(int id) { 
		if (instances[id] == null) { 
		instances[id] = new Singleton(); 
		} 
		return instances[id]; 
	} 
}
```

- **Ngữ cảnh**: Trong một số ứng dụng, việc **chỉ có duy nhất một đối tượng** (của một lớp đặc biệt nào đó) được tạo ra là rất quan trọng. Ví dụ: kết nối DB, Window manager, file system, Shared resource, Logger, Configuration, Caching,…
- **Vấn đề**: Làm thế nào để chúng ta có thể đảm bảo chỉ duy nhất 1 đối tượng thuộc một lớp nào đó được tạo ra và có thể _truy xuất_ được instance duy nhất đó **mọi lúc mọi nơi** trong chương trình?
- **Giải pháp**: 
	- Lớp có phương thức khởi tạo là private
	- Phương thức getInstance() được sử dụng để tạo đối tượng
	- Trong lần gọi đầu tiên, phương thức getInstance() này sẽ tạo ra một đối tượng
	- Trong những lần gọi tiếp theo, getInstance() không tạo thêm đối tượng mà chỉ trả về đối tượng đã tạo ra
- **Tác dụng**:
	- Đảm bảo chỉ tồn tại một instance của class dùng Singleton
	- Truy cập toàn cục instance duy nhất đó
	- Chia sẻ, duy trì một trạng thái nhất quán và tránh việc trùng lặp dữ liệu
	- Tiết kiệm tài nguyên bằng cách tránh việc tạo ra nhiều instance của một class
- Cài đặt:

Có rất nhiều cách implement cho Singleton, thường thì nên sử dụng **BillPughSingleton** vì có hiệu suất cao, sử dụng **LazyInitializedSingleton** cho những ứng dụng chỉ làm việc với ứng dụng **single-thread** và sử dụng **DoubleCheckLockingSingleton** khi làm việc với ứng dụng **multi-thread**.

Tùy theo trường hợp cụ thể, bạn hãy chọn cho mình cách implement phù hợp.

```java
public class LazyInitializedSingleton {
 
    private static LazyInitializedSingleton instance;
 
    private LazyInitializedSingleton() {
    }
 
    public static LazyInitializedSingleton getInstance() {
        if (instance == null) {
            instance = new LazyInitializedSingleton();
        }
        return instance;
    }

    public doSomething() {
       // TODO
    }
}
```

```java
public class DoubleCheckLockingSingleton {
 
    private static volatile DoubleCheckLockingSingleton instance;
 
    private DoubleCheckLockingSingleton() {
    }
 
    public static DoubleCheckLockingSingleton getInstance() {
        // Do something before get instance ...
        if (instance == null) {
            // Do the task too long before create instance ...
            // Block so other threads cannot come into while initialize
            synchronized (DoubleCheckLockingSingleton.class) {
                // Re-check again. Maybe another thread has initialized before
                if (instance == null) {
                    instance = new DoubleCheckLockingSingleton();
                }
            }
        }
        // Do something after get instance ...
        return instance;
    }
}
```

```java
public class BillPughSingleton {
 
    private BillPughSingleton() {
    }
 
    public static BillPughSingleton getInstance() {
        return SingletonHelper.INSTANCE;
    }
 
    // static nested class
    private static class SingletonHelper {
        private static final BillPughSingleton INSTANCE = new BillPughSingleton();
    }
}
```