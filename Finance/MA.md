# SMA (MA)
- Simple Moving Average - Đường trung bình động đơn giản  
$$
SMA = \frac{P_1 + P_2 + \dots + P_n}{n}
$$
Trong đó
- $P_1, P_2, \dots, P_n$ là giá đóng cửa của tài sản trong n phiên giao dịch gần nhất.
- n là số chu kỳ (thường là 10, 20, 50, 100 hoặc 200 ngày).
# EMA
- Exponential Moving Average - Đường trung bình động hàm mũ
- Đặt trọng số cao hơn cho các dữ liệu gần đây
$$
EMA_t=\alpha\times P_t + (1-\alpha)\times EMA_{t-1} 
$$
Trong đó
- $EMA_t$​ là giá trị EMA tại thời điểm hiện tại.
- $P_t$​ là giá đóng cửa tại thời điểm hiện tại.
- $EMA_{t-1}$​ là giá trị EMA của ngày trước đó.
- $\alpha$ là hệ số làm mịn, được tính theo công thức:$$\alpha = \frac{2}{n+1}$$​Với **n** là số chu kỳ (thường dùng các giá trị như 10, 20, 50, 100 hoặc 200 ngày).
Example
- **EMA 50 & EMA 200** thường được dùng để xác định xu hướng dài hạn.
- **EMA 9 & EMA 21** được dùng trong giao dịch ngắn hạn.
# MACD
- Moving Average Convergence Divergence
- Trung bình động hội tụ phân kỳ
$$MACD=EMA(12)-EMA(26)$$
### Signal line
- EMA(9) của đường MACD
### Histogram MACD
- Đường MACD - Đường tín hiệu