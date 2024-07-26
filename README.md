# Opentelemetry Stack

> Contains all data necessary to start a local OTEL environment

## Content
- Grafana
- Jaeger
- Prometheus

## How to use it
After starting all containers with `docker compose up -d`, the technologies will be accessible at the following URLs:
- Grafana: http://127.0.0.1:13654 (username: admin, password: admin)
- Prometheus: http://127.0.0.1:19876
- Jaeger: http://127.0.0.1:16686

To use Prometheus, you need to set all API endpoints in the prometheus.yml file before starting the container. Prometheus requires the `/metrics` endpoint on each API to gather the data necessary for the metric dashboard.

To use Jaeger, you need to configure the trace URL in each API. The Jaeger trace URL is `http://localhost:4317`.

To use Grafana, after logging in, you need to create a connection to Prometheus. To do this, go to the side menu > Connections > Add Connection, choose Prometheus, enter the URL `http://host.docker.internal:19876`, and set the HTTP method to GET.