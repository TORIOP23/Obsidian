- Distributed tracing system

# Transport
- Spans sent by the instrumented library must be transported from the services being traced to Zipkin collectors. There are three primary transports: HTTP, Kafka and Scribe.
# Components
## Zipkin Collector
- Once the trace data arrives at the Zipkin collector daemon, it is validated, stored, and indexed for lookups by the Zipkin collector.
## Storage
- Initially build to store data on Cassandra
- Support ElasticSearch and MySQL
## Zipkin Query Service
## Web UI
- No built0in authentication in the UI