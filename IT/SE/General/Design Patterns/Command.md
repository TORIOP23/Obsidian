- **Một lệnh là một _cuộc gọi phương thức_ được sửa đổi**
- _Các lệnh là sự thay thế hướng đối tượng cho các lệnh gọi lại._
- Khi bạn có một giao diện với một phương thức duy nhất không trả về bất cứ thứ gì, thì rất có thể đó là mẫu Lệnh.

```cpp
class Command
{
public:
  virtual ~Command() {}
  virtual void execute() = 0;
};
class JumpCommand : public Command
{
public:
  virtual void execute() { jump(); }
};

class FireCommand : public Command
{
public:
  virtual void execute() { fireGun(); }
};

//
class InputHandler
{
public:
  void handleInput();
  // Methods to bind commands...
private:
  Command* buttonX_;
  Command* buttonY_;
  Command* buttonA_;
  Command* buttonB_;
};
void InputHandler::handleInput()
{
  if (isPressed(BUTTON_X)) buttonX_->execute();
  else if (isPressed(BUTTON_Y)) buttonY_->execute();
  else if (isPressed(BUTTON_A)) buttonA_->execute();
  else if (isPressed(BUTTON_B)) buttonB_->execute();
}
```

- Có thể là AI phát command cho các đối tượng
- Sự phân tách ở đây giữa AI chọn lệnh và mã tác nhân thực hiện chúng mang lại cho chúng ta rất nhiều sự linh hoạt. Chúng tôi có thể sử dụng các mô-đun AI khác nhau cho các tác nhân khác nhau. Hoặc chúng ta có thể trộn và kết hợp AI cho các loại hành vi khác nhau. Muốn có một đối thủ hung hãn hơn? Chỉ cần bổ sung một AI mạnh mẽ hơn để tạo các lệnh cho nó. Trên thực tế, chúng tôi thậm chí có thể gắn AI vào nhân vật _của người chơi_ , điều này có thể hữu ích cho những thứ như chế độ demo mà trò chơi cần chạy trên chế độ lái tự động.
- Bằng cách thực hiện các lệnh điều khiển các đối tượng hạng nhất của tác nhân, chúng tôi đã loại bỏ sự kết hợp chặt chẽ của một cuộc gọi phương thức trực tiếp. Thay vào đó, hãy nghĩ về nó như một hàng đợi hoặc một luồng lệnh:
![[command-1.png]]
- Chúng tôi có thể lấy đầu vào của người chơi, đẩy qua mạng sang máy khác rồi phát lại. Đó là một phần quan trọng để tạo ra một trò chơi nhiều người chơi được nối mạng.

### Undo and Redo
- Hoàn tác được sử dụng trong một số trò chơi chiến lược, nơi bạn có thể quay lại các bước di chuyển mà bạn không thích.

```cpp
class MoveUnitCommand : public Command
{
public:
  MoveUnitCommand(Unit* unit, int x, int y)
  : unit_(unit),
    xBefore_(0),
    yBefore_(0),
    x_(x),
    y_(y)
  {}

  virtual void execute()
  {
    // Remember the unit's position before the move
    // so we can restore it.
    xBefore_ = unit_->x();
    yBefore_ = unit_->y();

    unit_->moveTo(x_, y_);
  }

  virtual void undo()
  {
    unit_->moveTo(xBefore_, yBefore_);
  }

private:
  Unit* unit_;
  int xBefore_, yBefore_;
  int x_, y_;
};
Command* handleInput()
{
  Unit* unit = getSelectedUnit();

  if (isPressed(BUTTON_UP)) {
    // Move the unit up one.
    int destY = unit->y() - 1;
    return new MoveUnitCommand(unit, unit->x(), destY);
  }

  if (isPressed(BUTTON_DOWN)) {
    // Move the unit down one.
    int destY = unit->y() + 1;
    return new MoveUnitCommand(unit, unit->x(), destY);
  }

  // Other moves...

  return NULL;
}
class Command
{
public:
  virtual ~Command() {}
  virtual void execute() = 0;
  virtual void undo() = 0;
};

```

- [**Memento patterns**](https://en.wikipedia.org/wiki/Memento_pattern)
- [**Persistent data structure**](https://en.wikipedia.org/wiki/Persistent_data_structure)
![[command-2.png]]
Redo có thể không phổ biến trong trò chơi, nhưng re-play thì có. Một triển khai ngây thơ sẽ ghi lại toàn bộ trạng thái trò chơi ở mỗi khung hình để nó có thể được phát lại, nhưng điều đó sẽ sử dụng quá nhiều bộ nhớ.

Thay vào đó, nhiều trò chơi ghi lại tập hợp các lệnh mà mọi thực thể thực hiện trên mỗi khung hình. Để replay trò chơi, động cơ chỉ cần chạy mô phỏng trò chơi bình thường, thực hiện các lệnh được ghi sẵn.
- Trong các ví dụ của chúng tôi, chúng tôi đã chọn rõ ràng tác nhân nào sẽ xử lý một lệnh. Trong một số trường hợp, đặc biệt là khi mô hình đối tượng của bạn có thứ bậc, nó có thể không được cắt và làm khô như vậy. Một đối tượng có thể phản hồi một lệnh, hoặc nó có thể quyết định xử lý lệnh đó trên một số đối tượng cấp dưới. Nếu bạn làm được điều đó, bạn đã có cho mình mẫu [Chain of Responsibility](http://en.wikipedia.org/wiki/Chain-of-responsibility_pattern)