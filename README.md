# Observability in Kubernetes with Opentelemetry and Elasticsearch

Observability is crucial for maintaining an application in production. The goal of this repository is to create an observability system when deploying applications using Kubernetes.

## Technologies Used

- **OpenTelemetry**: Generates traces, metrics, and logs.
- **Node Exporter**: Collects metrics related to the state of the Kubernetes cluster.
- **Elasticsearch**: Centralizes traces, metrics, and logs in a single tool. It serves as a replacement for Zipkin or Jaeger for monitoring traces while also allowing log correlation without additional configuration.
- **QuestDB**: Used as a time-series database to store metrics instead of deploying an additional component like Prometheus.
- **Grafana**: Used for visualization, with QuestDB as the data source.

    ![image](./resources/observability_otel_elk_project_structure.png)

## Architecture Overview

1. **Tracing and Logging**: OpenTelemetry is used to generate and send traces, logs, and metrics to Elasticsearch. This setup enables automated correlation between logs and traces without requiring extra configuration.
2. **Cluster Metrics**: Node Exporter collects Kubernetes cluster metrics.
3. **Time-Series Metrics**: Instead of using Prometheus, this project stores metrics in QuestDB, demonstrating an alternative approach for monitoring.
4. **Application Instrumentation**:
   - A **Java/Spring Boot** application is instrumented to generate observability data.
   - A **Python** application is also instrumented, following the same procedure.

## Why Not Use Prometheus?

Prometheus is the standard monitoring solution, with extensive tutorials available. However, in this project, we assume an existing time-series database such as **Timescale, InfluxDB, or QuestDB** (in this case, QuestDB). By leveraging QuestDB, we avoid deploying an additional component.

## Visualization

Grafana is used for monitoring, configured to use QuestDB as the data source for querying and visualizing metrics.

## Getting Started

To set up and deploy the observability system, follow these steps:

1. Deploy the required components (Elasticsearch, QuestDB, Grafana).
2. Configure OpenTelemetry to send traces, logs, and metrics.
3. Instrument your applications in Java, Python, or other languages.
4. Use Grafana to visualize data stored in QuestDB.

This approach provides a unified observability solution tailored for Kubernetes deployments, simplifying traceability and monitoring without additional complexity.


