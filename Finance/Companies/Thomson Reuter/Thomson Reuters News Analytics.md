---
cssclasses:
  - wide
---
# Description
- **Phân tích tin tức tự động**:
  - Xử lý trong mili giây, tạo tín hiệu mua/giữ/bán theo thời gian thực.
  - Áp dụng cho hàng nghìn công ty, hỗ trợ chiến lược định lượng.

- **Theo dõi tâm lý thị trường liên tục**:
  - Hiểu sâu hơn về mức độ đưa tin và danh tiếng thị trường.
  - Hỗ trợ quyết định giao dịch, đầu tư, quản lý rủi ro, phân bổ tài sản.

- **Chấm điểm tin tức theo các tiêu chí**:
  - Cảm xúc (tích cực, tiêu cực, trung lập).
  - Mức độ liên quan.
  - Khối lượng tin tức.
  - Tính độc đáo.
  - Phân tích tiêu đề (hành động môi giới, bình luận giá, tin độc quyền...).

- **Siêu dữ liệu phong phú**:
  - Hơn 80 trường dữ liệu: mã công ty, mã chủ đề, giai đoạn tin tức, phân loại ngành/địa lý, liên kết bài viết tương tự.

- **Ưu điểm nổi bật**:
  - Phủ sóng hơn 25.000 cổ phiếu và 40 chủ đề hàng hóa/năng lượng.
  - Linh hoạt triển khai: tại chỗ, đám mây hoặc tích hợp với nền tảng Quantitative Analytics.
  - Tích hợp vào hệ sinh thái giao dịch định lượng: hỗ trợ nghiên cứu, kiểm tra chiến lược và giao dịch dựa trên sự kiện.
# Text Scoring and metadata
![[TRNA.png]]

| Field                       | Description                                                                                                                |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------- |
| Item Type                   | Alert, Article, Updates, Corrections                                                                                       |
| Item Genre                  | Classification of the story, i.e., interview, exclusive, wrap-up, etc.                                                     |
| Headline                    | Alert or headline text                                                                                                     |
| Relevance                   | 0 – 1.0                                                                                                                    |
| Prevailing Sentiment        | 1, 0, -1                                                                                                                   |
| Positive, Neutral, Negative | Provides more detailed sentiment indication                                                                                |
| Location of 1st Mention     | Sentence location of the first time the item is mentioned                                                                  |
| Total Sentences             | Used for article length                                                                                                    |
| Number of Companies         | How many companies are tagged to the item                                                                                  |
| Number of Words/Tokens      | How many words/tokens are about the company                                                                                |
| Total Words/Tokens          | Total words/tokens in the news item                                                                                        |
| Broker Action               | Denotes broker actions: upgrade, downgrade, maintain, undefined or whether it is the broker itself                         |
| Price/Market Commentary     | Used to flag items describing pricing/market commentary                                                                    |
| Item Count                  | How many items have been published on a company over different time periods                                                |
| Linked Count                | Denotes level of repetition from 12 hours to 7 days                                                                        |
| Topic Codes                 | Describes what the story is about, i.e. RCH=Research; RES=Results; RESF=Results Forecast; MRG=Mergers & Acquisitions, etc. |
| Other Companies             | What are the other companies tagged to the article                                                                         |
| Other Metadata              | Index IDs, linked references, story chains, etc.                                                                           |
