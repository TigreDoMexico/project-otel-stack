# Opentelemetry Stack

> Contains all data necessary to start a local OTEL environment

## Content
- Grafana
- Jaeger
- Prometheus
- OTel Collector

## How to use it
After starting all containers with `docker compose up -d`, the technologies will be accessible at the following URLs:
- Grafana: http://127.0.0.1:13654 (username: admin, password: admin)
- Prometheus: http://127.0.0.1:19876
- Jaeger: http://127.0.0.1:16686
- OTel Collector: http://localhost:4317

Everything begins with the OTel Collector. It is responsible for gathering all API data related to logs, metrics, and traces, and directing this information to the appropriate services (Prometheus and Jaeger). To use the collector, each API must be configured to point to the URL `http://localhost:4317`.

Prometheus requires the `/metrics` endpoint on each API to collect the data needed for the metrics dashboard.

Jaeger collects all traces sent by the OTel Collector

To use Grafana, after logging in, you need to create a connection to Prometheus. To do this, go to *Side Menu > Connections > Add Connection,* choose Prometheus, enter the URL `http://host.docker.internal:19876`, and set the HTTP method to GET.