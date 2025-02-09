# Common Service
## Gateway service
- là một điểm truy cập duy nhất (single entry point) cho tất cả các yêu cầu từ bên ngoài vào hệ thống microservices.
- Nó đóng vai trò như một "cổng vào" để định tuyến (routing), xử lý và bảo mật các yêu cầu.
Example:
- [[Spring Cloud Gateway]]
- Netflix Zuul
- Kong

## Discovery service
- Nó đóng vai trò như một "danh bạ" lưu trữ thông tin về tất cả các dịch vụ đang hoạt động trong hệ thống.
Example 
- **[[Eureka]]**
- **Consul**
- **Zookeeper**

## Tracing
- Theo dõi luồng yêu cầu trong hệ thống
Example
- [[Zipkin]]
### Observable
- [[Micrometer]]
## Monitoring
- Thu thập và phân tích metrics để giám sát hệ thống
- While Prometheus excels at collecting and storing metrics, Grafana is our tool of choice for visualizing these metrics through insightful dashboards.
Example
- [[Prometheues]]
- [[Grafana]]

## ELK
- **Elasticsearch**:  Công cụ tìm kiếm phân tán
- **Kibana** là một công cụ trực quan hóa dữ liệu
- **Logstash** là một công cụ thu thập, xử lý và chuyển đổi dữ liệu trước khi gửi vào **Elasticsearch** hoặc các hệ thống lưu trữ khác

## Kafka
- Zookeeper 
- Schema-registry 
- Kafka Broker