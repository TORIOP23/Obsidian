---
node_size: "6"
---
## [[UML]]
## Tools
- [Typst](https://typst.app/)
- Overleaf
- [[LaTex]]

# Requirements
- Problem Statement - Tài liệu mô tả bài toán
- Domain model - Tài liệu mô hình miền
- Use-Case Specification
    - Name
    - Brief description
    - Flow of Events
        - Normal basic flow
        - Alternative flow
    - Relationships
    - Activity diagrams
    - Use-Case diagrams
    - Special requirements
    - Pre-conditions
    - Post-conditions
    - Other diagrams
- Supplementary Specifications
    - Functionality
    - Usability
    - Reliability
    - Performance
    - Supportability
    - Design constraints
- Từ điển thuật ngữ (Glossary)
# Analysis
- Use-Case Specification mức chi tiết
- Tài liệu phân tích kiến trúc
- Tài liệu phân tích ca sử dụng
# Design
Thiết kế kiến trúc
- Tài liệu về xác định các phần tử thiết kế
- Tài liệu về xác định các cơ chế thiết kế
- Tài liệu mô tả kiến trúc thực thi
- Tài liệu mô tả kiến trúc phân tán

Thiết kế chi tiết
- Tài liệu thiết kế ca sử dụng
- Tài liệu thiết kế hệ thống con
- Tài liệu thiết kế cơ sở dữ liệu
- Tài liệu chương trình demo

### Model Driven Architecture (MDA)
- Computational Independent Model (CIM): Tập trung vào môi trường của hệ thống và các yêu cầu đối với hệ thống
- Platform Independent Model (PIM): Tập trung vào vận hành hệ thống, độc lập với nền tảng
- Platform Specific Model (PSM): Tập trung vào việc sử dụng chi tiết hệ thống trên nền tảng cụ thể

| Analysis                  | Design                                        |
| ------------------------- | --------------------------------------------- |
| Tập trung vào hiểu vấn đề | Tập trung vào tìm ra giải pháp                |
| Thiết kế ý tưởng          | Operations and attributes                     |
| Behavior                  | Performance                                   |
| System structure          | Close to real code                            |
| Functional requirements   | Object lifecycles, Nonfunctional requirements |
| A small model             | A large model                                 |

## Reference
- RUP - Rational Unified Process