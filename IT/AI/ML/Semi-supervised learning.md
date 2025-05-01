## Self-Training
- Ý tưởng:
    - Bắt đầu với **một mô hình** huấn luyện trên **một lượng nhỏ dữ liệu có nhãn**.
    - Sau đó, **dùng chính mô hình đó** dự đoán nhãn cho **dữ liệu chưa có nhãn**.
    - Chọn ra những mẫu mà mô hình **dự đoán tự tin nhất** → **thêm chúng cùng với nhãn dự đoán** vào tập huấn luyện.
    - **Huấn luyện lại** mô hình với dữ liệu mở rộng.
- Quy trình này có thể lặp lại nhiều lần để cải thiện mô hình.
## Co-Training
- **Co-Training** cũng là kỹ thuật bán giám sát, nhưng dùng **hai mô hình** hoặc **hai cách nhìn khác nhau về dữ liệu** (gọi là **views**).
- Ý tưởng:
    - Dữ liệu phải có thể chia thành **hai tập thuộc tính độc lập** nhưng đều đủ để phân loại.
    - **Huấn luyện 2 mô hình riêng biệt** trên cùng dữ liệu nhưng theo 2 "view" khác nhau.
    - Sau đó:
        - Mỗi mô hình **gán nhãn** cho dữ liệu chưa nhãn **mà nó tự tin**.
        - **Giao nhãn đó cho mô hình còn lại** để huấn luyện thêm.
- Điều này giúp mô hình tránh khuynh hướng sai lệch vì mỗi mô hình học từ góc nhìn riêng.