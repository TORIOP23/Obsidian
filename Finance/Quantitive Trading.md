# Note
- Chia thành 3 phòng ban
- Tìm kiếm thử nghiệm
    - Tìm kiếm thông tin, dữ liệu vào chiến lược giao dịch mới
    - Thực hiện thử nghiệm các tính năng mới của các sàn giao dịch các sản phẩm tài chính
    - Thử nghiệm những chiến dịch giao dịch mới nhất
- Phân tích / chiến lược
- Thực thi / vận hành
- Giao dịch định lượng

## Định nghĩa
- Xây dựng chiến lược và thực hiện các giao dịch thông qua các phân tích định lượng dưới sự hỗ trợ của máy tính, máy móc và các công cụ số hóa (ví dụ như AI,... )
- Bài toán giải quyết các câu hỏi: Mua bao nhiêu?, Mua trong bao lâu?, Mua như thế nào?,...
## Các bước
- Thu thập, phân tích, xử lý dữ liệu
- Xây dựng thuật toán
- Kiểm tra lại thuật toán (backtest) và chạy mô hình giả lập (simulator)
- Ứng dụng mô hình vào giao dịch thực tế
- Tiếp tục kiểm tra, phát triển và vá lỗi cho thuật toán.
## Điểm mạnh
- Giúp thực hiện các giao dịch trên thị trường với tốc độ nhanh đến chóng mặt, cực kỳ logic và độ chính xác rất cao.
- Ngày nay, các từ ngữ (keyword) trong báo chí, các cuộc phỏng vấn, các cuộc hội thảo, thậm chí biểu cảm khuôn mặt của các nhà lãnh đạo cũng có thể được thu thập và xử lý ngay tức thì bởi các AI để tạo ra các quyết định giao dịch
- Trên thế giới có rất nhiều Hedge Fund nổi tiếng đã ứng dụng hiệu quả Quant trading và đạt được nhiều thành công, có thể kể đến một số cái tên như Renaissance Technologies, Two Sigma, AQR,…
- **Backtest chiến lược**: Quantitative Trading có khả năng Backtest dựa trên dữ liệu giá lịch sử, cho phép trader đo lường hiệu suất và tính khả thi của chiến lược. Từ đó quyết định sử dụng chiến lược vào thực chiến hay điều chỉnh lại cho phù hợp.
- **Quản lý rủi ro**: Các chiến lược Quant Trading thường kết hợp phương pháp quản lý rủi ro để giảm thiểu thua lỗ. Ví dụ như lệnh **`Stop Loss`** được đặt tự động để bán vị thế nếu giá giảm xuống dưới mức chấp nhận rủi ro của trader. Ngược lại, **`Take Profit`** sẽ tự động bán vị thế khi đạt được lợi nhuận kỳ vọng.
## Điểm yếu
- Các thuật toán sẽ chỉ chính xác ở một số thời điểm và hoàn cảnh nhất định, nếu trên thị trường có những thay đổi bất ngờ thì máy tính sẽ không có khả năng xử lý.
    - Thuật toán có thể đúng với thời điểm này nhưng lại sai tại các thời điểm khác (vì độ chính xác của các input luôn thay đổi)
- Ngoài ra, khả năng dự đoán của nó đối với các sự kiện có tác động lớn là rất thấp mặc dù vẫn luôn được đầu tư để phát triển và hoàn thiện.
- Hầu hết các giao dịch với Quant hiện nay vẫn bị giới hạn bởi các input và điều kiện do con người tạo ra, do đó các sự kiện mang tính ngẫu nhiên hay các sự kiện kiểu Thiên Nga Đen sẽ là thảm họa với Quant Trading vì máy tính gần như không thể xử lý được. Điển hình như năm 2020, các tác động bất ngờ của đại dịch Covid-19 đã khiến cho hoạt động của các Quant funds tỏ ra kém hiệu quả hơn nhiều so với các quỹ đầu tư thông thường.
- Quant Trading cũng gặp phải một thách thức khá lớn chính là ở tính bảo mật của thuật toán. Nếu một thuật toán nếu có quá nhiều người biết thì nó sẽ không còn chính xác nữa.
    - Nếu nhiều Quant Trader cũng xây dựng được thuật toán tương tự, khi cổ phiếu TCB gần chạm đỉnh cũ, hàng loạt máy tính sẽ cùng đặt lệnh mua vào, điều này có thể tạo ra một sự mất cân bằng.
    - Và thậm chí sẽ có nhiều người khác sử dụng Quant để counter, nghĩa là khi cổ phiếu TCB break đỉnh cũ, hàng loạt máy tính sẽ cùng đặt lệnh bán ra, như vậy input bị sai lệch và máy tính của những người mua vào có thể sẽ không xử lý kịp thời.
## Thuật ngữ

| Tiếng Anh  | Tiếng Việt   |
| ---------- | ------------ |
| Hedge Fund | Quỹ phòng hộ |
|            |              |
## Tham khảo
- [Join WorldQuant BRAIN](https://platform.worldquantbrain.com/)
- [Tập 28: Khách mời Công Hoàng - WorldQuant Việt Nam, phe vé, nghiên cứu tài chính định lượng, rủi ro](https://www.youtube.com/watch?v=jHGvG0ncdsk)