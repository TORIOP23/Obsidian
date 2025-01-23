- BlockChain có thể hiểu là cách ghi chép thông tin vào sổ cái. Nó được lập trình để ghi chép và theo dõi bất cứ thứ gì, chẳng hạn như: giao dịch tài chính hồ sơ y tế, ....
- Thông tin được lưu trong BlockChain được công khai cho tất cả thành viên trong mạng lưới. Bảo đảm thông tin được minh mạch chính xác
- BlockChain được lưu giữ thông tin trong các khối, các khối được liên kết với nhau theo thời gian thực để tạo thành 1 chuỗi liên tục
    - Nếu một thông tin đã được lưu trữ thành công trên 1 khối rồi thì khối đó sẽ không cho phép bất cứ ai chỉnh sửa được nữa, vì thế nếu muốn chỉnh sửa thông tin đó chỉ có 1 cách duy nhất là lưu thông tin trên 1 khối mới kèm theo thông tin của người đã chỉnh sửa và thời gian cụ thể
    - Để 1 khối mới có đủ điều kiện để thêm vào chuỗi nó phải trải qua vài bước xử lý (1 câu đố mật mã, chia sẻ kết quả - bằng chứng công việc, kiểm chứng bằng chứng công việc
- Loại bỏ người hoặc dịch vụ trung gian
- Solidity
- Vấn đề: sổ cái tập trung truyền thống
- → Số cái phân tán: Blockchain

Blockchain là 1 cơ sở dữ liệu phân tán ghi lại giao dịch được phân phối, xác thực và duy trì trên toàn thế giới bởi 1 mạng lưới máy vi tính
- Thay vì 1 cơ quan trung ương duy nhất như ngân hàng, 1 cộng đồng lớn sẽ giám sát các bản ghi trong Blockchain và không cá nhân nào có quyền kiểm soát các hồ sơ này.
- Bản chất mô hình hoạt động của Blockchain là cuốn sổ cái điện tử được phân phối trên hệ thống máy tính phi tập trung, lưu trữ thông tin về các giao dịch và đảm bảo lịch sử giao dịch đó không thể bị thay đổi.

### Kiến trúc 5 tầng
Application and Presentation Layer
- Smart Contract, Chaincode, DApps, UI
Consensus Layer
- Pow, Pos. DPos, PoET, PBFT
- Lớp đồng thuận chịu trách nhiệm đạt được sự thỏa thuận giữa các nút
Network Layer
- Peer-to-Peer
Data Layer
- Digital Signature, Harsh, Merkel Tree, Transactions
Hardware/Infrastructure Layer
- Virtua Machine, Containers, Mining Rig
### Phân loại: 4 loại
![[blockchain-1.png]]
Public chain:
- là một nền tảng mà bất kỳ ai cũng có quyền truy cập và ghi dữ liệu trên chuỗi. Vd: Ethereum , BSC

Private chain:
- là nền tảng chỉ cho phép người dùng được đọc dữ liệu, không có quyền ghi. Quyền ghi này sẽ thuộc về một tổ chức thứ 3 hoàn toàn đáng tin cậy. Vd: Ripple, Hyperledger

Consortium chain:
- là chuỗi khối được phép được quản lý bởi một nhóm các tổ chức, thay vì một thực thể, như trong trường hợp chuỗi khối riêng tư. Vd: R3 Corda, Global Shipping Business Network Consortium

Hybrid chain:
- là chuỗi khối được kiểm soát bởi một tổ chức duy nhất, nhưng với mức độ giám sát được thực hiện bởi chuỗi khối công khai, được yêu cầu để thực hiện các xác thực giao dịch nhất định. Vd: IBM Food Trust.

### Cấu trúc hoạt động
![[blockchain-2.png]]
- Tạo 1 giao dịch (user sử dụng public và private key của họ)
- Xác thực giao dịch, phân phối đến toàn bộ node trên toàn bộ thế giới. Tất cả các node sẽ kiểm tra tính hợp lệ giao dịch đó
- Tạo 1 khối mới
- Chèn khối vào mạng

### Khối
Gồm 3 phần chính
- Dữ liệu
- Hash của khối hiện tại
- Hash của khối trước đó

Cấu trúc của chuỗi khối
- Header: Định danh block, chứa metadata của block
- Previous Block Address: chứa địa chỉ/ mã băm của block cha
- Timestamp: thời gian hệ thống thêm block vào
- Nonce: 1 số ngẫu nhiên được tính toán
- ## Merkel Root: Hàm băm cuối cùng chính của cây Merkle đại diện cho mọi phần giao dịch tạo nên khối

### Cách tạo khối
- Quá trình tạo một block được gọi là khai thác (mining) và nó liên quan đến việc giải một câu đố toán học phức tạp đòi hỏi sức mạnh tính toán đáng kể.
- Những người khai thác (miner) cạnh tranh với nhau để trở thành người đầu tiên giải được câu đố và thêm khối tiếp theo vào chuỗi khố

### Thuật toán đồng thuận
![[blockchain-3.png]]
- **Proof of Work (PoW)** hay còn gọi là bằng chứng công việc. Với cơ chế đồng thuận này, các node sẽ sử dụng sức mạnh máy tính để giải các bài toán tạo ra mã hash.
- **Proof of Stake (PoS)** hay còn gọi là bằng chứng cổ phần. Thay vì sử dụng sức mạnh máy tính, Proof of Stake yêu cầu các node tham gia xác thực giao dịch phải đặt cược (stake) một số lượng nhất định native token của blockchain để giành quyền tham gia xác thực và tạo khối.
- **Delegated Proof of Stake (DPoS)** hay còn gọi là bằng chứng uỷ quyền cổ phần, là phiên bản phát triển của Proof of Stake.
- **Byzantine Fault Tolerance** (hay Hệ thống chịu lỗi Byzantine - BFT) là hệ thống có thể giải quyết được vấn đề của bài toán Byzantine. Điều này có nghĩa là hệ thống BFT có thể tiếp tục hoạt động ngay cả khi một số node bị lỗi hoặc thực hiện hành động gây hại cho mạng chung.
- **Proof of History (PoH)** hay còn gọi là bằng chứng lịch sử. Thay vì xét theo logic, PoH sử dụng timeline giao dịch làm tài liệu tham khảo.

### Smart Contract - hợp đồng thông minh
- Hợp đồng thông minh (Smart contract) là các chương trình chạy trên blockchain. Hợp đồng thông minh cũng giống như một hợp đồng kỹ thuật số bị bắt buộc thực hiện bởi một bộ quy tắc cụ thể. Các quy tắc này do bộ mã máy tính xác định trước mà tất cả các nút (node) trong mạng đều phải sao chép và thực thi các quy tắc đó.
- Smart Contract chỉ là một đoạn mã chạy trên một hệ thống phân tán, cho phép tạo ra các giao thức Permissionless (không cần trao quyền).

Cách thức hoạt động
- Hợp đồng thông minh hoạt động như một chương trình tất định. Nó sẽ thực thi một tác vụ cụ thể trong trường hợp thỏa mãn các điều kiện nhất định.
- Hợp đồng thông minh chịu trách nhiệm thực thi và quản lý các hoạt động diễn ra trên blockchain khi những người dùng (address) tương tác với nhau 
### Ứng dụng phi tập trung DAPP

- là các chương trình hoặc ứng dụng kỹ thuật số chạy trên chuỗi khối hoặc mạng máy tính ngang hàng.
- Các ứng dụng này về cơ bản được phân cấp ở mức độ lớn và không thể bị kiểm soát bởi một cơ quan duy nhất.

Tính năng
- Mã nguồng mở
- Quyền riêng tư: Để triển khai và tương tác với DApp, user không cần cung cấp danh tính ở thế giới thực.
- Phi tập trung và an toàn hơn nhờ mật mã: Tất cả thông tin của DApp đều được bảo mật bằng mật mã và được lưu trữ trên một blockchain công khai, phi tập trung, được vận hành bởi nhiều người dùng (hoặc các node).
- Vận hành một cách độc lập: Dapp chạy độc lập mà không cần sự tham gia của bên thứ ba