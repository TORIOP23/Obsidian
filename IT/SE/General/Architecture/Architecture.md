# Application
### Model
- Data Repository -> LocalDataSource, RemoteDataSource

## MVC
- Phù hợp với web
- 3 thành View - Controller - Model, tương tác qua lại với nhau
- Việc cả View và Controller đều tương tác với model khiến cho việc test Model trở nên khó
## MVVM
- Phù hợp với mobile
- View - View Model - Model
- Dựa theo Observable design pattern (View - ViewModel)
- Rất nhiều View có thể lắng nghe sự thay đổi dữ liệu của ViewModel
- Cho phép nhiều View có thể lắng nghe cùng 1 ViewModel
## MVP
- Mô hình phù hợp với mobile tuy nhiên đã cũ.
- Presenter tương tác với View qua Interface, hạn chế là implement quá nhiều interface, khó kiểm soát
- Khác biệt với MVVM là cách View tương tác với VM (P)
	- View và Presenter quan hệ theo kiểu 1-1
	- View và VM quan hệ kiểu n - 1

# System
## [[Microservice]]
## Monolith

# Reference
- [MVC vs MVP vs MVVM](https://www.youtube.com/watch?v=8UgXf8NwFrk)