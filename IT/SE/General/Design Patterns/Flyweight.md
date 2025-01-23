Đây là kiểu thiết lập thế giới khác mà chúng tôi mơ ước với tư cách là nhà phát triển trò chơi và những cảnh như thế này thường được kích hoạt bởi một mẫu có tên không thể khiêm tốn hơn: Flyweight khiêm tốn.

### Forest for the Trees
- Khi bạn có cả một rừng cây riêng lẻ lấp đầy màn hình, tất cả những gì mà một lập trình viên đồ họa nhìn thấy là hàng triệu đa giác mà họ sẽ phải bằng cách nào đó xúc vào GPU sau mỗi sáu mươi giây.
- Chúng ta đang nói về hàng nghìn cây, mỗi cây có hình học chi tiết chứa hàng nghìn đa giác. Ngay cả khi bạn có đủ _bộ nhớ_ để mô tả khu rừng đó, để hiển thị nó, dữ liệu đó phải vượt qua bus từ CPU đến GPU.

Each tree has a bunch (loạt) of bits associated with it:
- A mesh (lưới) of polygons that define the shape of the trunk (thân cây), branches, and greenery.
- Textures for the bark (vỏ) and leaves.
- Its location and orientation in the forest.
- Tuning parameters like size and tint so that each tree looks different. (Điều chỉnh các tham số như kích thước và tông màu để mỗi cây trông khác nhau)

```cpp
class Tree
{
private:
  Mesh mesh_;
  Texture bark_;
  Texture leaves_;
  Vector position_;
  double height_;
  double thickness_;
  Color barkTint_;
  Color leafTint_;
};
```

- Đó là rất nhiều dữ liệu, lưới và kết cấu đặc biệt lớn. Cả một rừng các đối tượng này là quá nhiều để ném vào GPU trong một khung hình. May mắn thay, có một thủ thuật dành cho thời gian để xử lý điều này.
- Quan sát chính là mặc dù có thể có hàng ngàn cây trong rừng, chúng hầu hết trông giống nhau. Chúng có thể sẽ sử dụng cùng một loại lưới và kết cấu. Điều đó có nghĩa là hầu hết các trường trong các đối tượng này đều _giống nhau_ giữa tất cả các trường hợp đó.
![[flyweight.png]]
- Chúng ta có thể mô hình hóa điều đó một cách rõ ràng bằng cách chia đôi đối tượng. Đầu tiên, chúng tôi lấy ra dữ liệu mà tất cả các cây có điểm chung và chuyển nó vào một lớp riêng biệt:

```cpp
class TreeModel
{
private:
  Mesh mesh_;
  Texture bark_;
  Texture leaves_;
};
```

Trò chơi chỉ cần một cái duy nhất trong số này, vì không có lý do gì để có những mắt lưới và kết cấu giống nhau trong bộ nhớ cả nghìn lần. Sau đó, mỗi _trường hợp_ của một cây trên thế giới có một _tham chiếu_ đến được chia sẻ đó `TreeModel`. Những gì còn lại `Tree`là trạng thái cụ thể:

```cpp
class Tree
{
private:
  TreeModel* model_;

  Vector position_;
  double height_;
  double thickness_;
  Color barkTint_;
  Color leafTint_;
};
```
![[flyweight-2.png]]
Điều này là tốt và tốt cho việc lưu trữ nội dung trong bộ nhớ chính, nhưng điều đó không giúp ích cho việc hiển thị. Trước khi khu rừng này xuất hiện trên màn hình, nó phải chuyển sang GPU. Chúng tôi cần diễn đạt chia sẻ tài nguyên này theo cách mà cạc đồ họa hiểu được.

### **A Thousand Instances**
- Để giảm thiểu lượng dữ liệu chúng tôi phải đẩy đến GPU, chúng tôi muốn có thể gửi dữ liệu được chia sẻ `TreeModel` - chỉ _một lần_ . Sau đó, một cách riêng biệt, chúng tôi đẩy qua dữ liệu duy nhất của mỗi cá thể cây - vị trí, màu sắc và tỷ lệ của nó. Cuối cùng, chúng tôi nói với GPU, "Sử dụng một mô hình đó để hiển thị từng trường hợp này."
- Fortunately, today’s graphics APIs and cards support exactly that. The details are fiddly and out of the scope of this book, but both Direct3D and OpenGL can do something called [_instanced rendering_](http://en.wikipedia.org/wiki/Geometry_instancing).
- Trong cả hai API, bạn cung cấp hai luồng dữ liệu. Đầu tiên là khối dữ liệu phổ biến sẽ được hiển thị nhiều lần - lưới và kết cấu trong ví dụ cây trồng của chúng tôi. Thứ hai là danh sách các cá thể và các tham số của chúng sẽ được sử dụng để thay đổi đoạn dữ liệu đầu tiên đó mỗi khi nó được vẽ. With a single draw call, an entire forest grows.

### The Flyweight Pattern
- Bây giờ chúng ta đã có một ví dụ cụ thể dưới đây, tôi có thể hướng dẫn bạn qua mô hình chung. Flyweight, giống như tên gọi của nó, phát huy tác dụng khi bạn có những đồ vật cần trọng lượng nhẹ hơn, thường là do bạn có quá nhiều đồ vật trong số đó.
- Với kết xuất cài đặt, không quá nhiều mà chúng chiếm quá nhiều bộ nhớ vì chúng mất quá nhiều _thời gian_ để đẩy từng cây riêng biệt qua bus tới GPU, nhưng ý tưởng cơ bản là như nhau.
- Mẫu giải quyết điều đó bằng cách tách dữ liệu của một đối tượng thành hai loại. Loại dữ liệu đầu tiên là những thứ không dành riêng cho một phiên bản duy nhất _của_ đối tượng đó và có thể được chia sẻ trên tất cả chúng. Gang of Four gọi đây là trạng thái _nội tại_ , nhưng tôi thích nghĩ về nó như là thứ "không có ngữ cảnh". Trong ví dụ ở đây, đây là hình học và kết cấu của cây.
- Phần còn lại của dữ liệu là trạng thái _bên ngoài_ , thứ duy nhất cho trường hợp đó. Trong trường hợp này, đó là vị trí, tỷ lệ và màu sắc của từng cây. Cũng giống như trong đoạn mã mẫu ở trên, mẫu này tiết kiệm bộ nhớ bằng cách chia sẻ một bản sao của trạng thái nội tại ở mọi nơi có đối tượng xuất hiện.
- Từ những gì chúng ta đã thấy cho đến nay, điều này có vẻ giống như chia sẻ tài nguyên cơ bản, hầu như không đáng được gọi là một khuôn mẫu. Đó là một phần bởi vì trong ví dụ này ở đây, chúng tôi có thể đưa ra một danh tính riêng biệt rõ ràng _cho_ trạng thái được chia sẻ: the `TreeModel`.

### **A Place To Put Down Roots**
Mặt đất mà những cây này đang phát triển cũng cần được thể hiện trong trò chơi của chúng tôi. Có thể có những mảng cỏ, bụi bẩn, đồi, hồ, sông và bất cứ địa hình nào khác mà bạn có thể mơ ước. Chúng tôi sẽ làm cho nền _gạch dựa trên_ mặt đất : bề mặt của thế giới là một mạng lưới khổng lồ các ô gạch nhỏ. Mỗi viên gạch được phủ trên một loại địa hình.

Mỗi loại địa hình có một số thuộc tính ảnh hưởng đến lối chơi:

- Chi phí di chuyển xác định tốc độ người chơi có thể di chuyển qua nó.
- Một lá cờ cho dù đó là địa hình nhiều nước có thể đi qua bằng thuyền.
- A texture used to render it.

Bởi vì chúng tôi là những lập trình viên trò chơi hoang tưởng về hiệu quả, không có cách nào chúng tôi lưu trữ tất cả trạng thái đó trong mỗi ô trên thế giới. Thay vào đó, một cách tiếp cận phổ biến là sử dụng enum cho các loại địa hình:

```c
enum Terrain
{
  TERRAIN_GRASS,
  TERRAIN_HILL,
  TERRAIN_RIVER
  // Other terrains...
};
class World
{
private:
  Terrain tiles_[WIDTH][HEIGHT];
};

int World::getMovementCost(int x, int y)
{
  switch (tiles_[x][y])
  {
    case TERRAIN_GRASS: return 1;
    case TERRAIN_HILL:  return 3;
    case TERRAIN_RIVER: return 2;
      // Other terrains...
  }
}

bool World::isWater(int x, int y)
{
  switch (tiles_[x][y])
  {
    case TERRAIN_GRASS: return false;
    case TERRAIN_HILL:  return false;
    case TERRAIN_RIVER: return true;
      // Other terrains...
  }
}
```

- Bạn có được ý tưởng. Điều này hiệu quả, nhưng tôi thấy nó xấu xí. Tôi nghĩ về chi phí di chuyển và độ ẩm ướt là _dữ liệu_ về địa hình, nhưng ở đây nó được nhúng trong mã. Tệ hơn nữa, dữ liệu cho một loại địa hình đơn lẻ bị bôi nhọ qua một loạt các phương pháp. Sẽ thực sự tuyệt vời nếu tất cả những điều đó được gói gọn lại với nhau. Rốt cuộc, đó là những gì các đối tượng được thiết kế.

```cpp
class Terrain
{
public:
  Terrain(int movementCost,
          bool isWater,
          Texture texture)
  : movementCost_(movementCost),
    isWater_(isWater),
    texture_(texture)
  {}

  int getMovementCost() const { return movementCost_; }
  bool isWater() const { return isWater_; }
  const Texture& getTexture() const { return texture_; }

private:
  int movementCost_;
  bool isWater_;
  Texture texture_;
};
```

Bạn sẽ nhận thấy rằng tất cả các phương pháp ở đây là `const`. Đó không phải là ngẫu nhiên. Vì cùng một đối tượng được sử dụng trong nhiều ngữ cảnh, nếu bạn sửa đổi đối tượng đó, các thay đổi sẽ xuất hiện đồng thời ở nhiều nơi.

Đó có lẽ không phải là điều bạn muốn. Chia sẻ các đối tượng để tiết kiệm bộ nhớ phải là cách tối ưu hóa để không ảnh hưởng đến hoạt động hiển thị của ứng dụng. Do đó, các đối tượng Flyweight hầu như luôn luôn bất biến.