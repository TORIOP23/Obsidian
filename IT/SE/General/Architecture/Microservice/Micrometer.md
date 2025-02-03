# Micrometer
# Micrometer tracing
## Definition
- **Span**: basic unit of work
- **Trace**: set of spans forming a tree-like structure
- **Annotation/Event**: Used to record
- **Tracer**: a library handles the lifecycle of a span. Pick 1 of 
	- **OpenZipkin Brave**
	- **OpenTelemetry**
- **Tracing context**: trace identifier, span identifier, and so on
- **Log correlation**
- **Latency analysis tool**
- **Reposter**
	- **Tanzu Observability by Wavefront**
	- **OpenZipkin Zipkin**
![[trace-id.jpg]]