# 10. Observability

> **Document Status:** 🟡 Draft
> **Owner:** SRE
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 10.1 The Three Pillars

| Pillar | What It Answers | Our Tool |
|---|---|---|
| **Logs** | What happened? | ELK Stack / Loki / CloudWatch |
| **Metrics** | How is the system performing? | Prometheus + Grafana |
| **Traces** | Where is the bottleneck? | Jaeger / AWS X-Ray / Tempo |

---

## 10.2 Logging Standards

- All services must emit **structured JSON logs**
- Required log fields: `timestamp`, `level`, `service`, `trace_id`, `message`
- Log levels: `DEBUG` (dev only), `INFO`, `WARN`, `ERROR`, `FATAL`
- Logs must be shipped to centralized logging platform — no local-only logs
- Log retention: 30 days hot, 1 year cold (S3 / archive)

**Example log format:**
```json
{
  "timestamp": "2026-04-05T09:00:00Z",
  "level": "ERROR",
  "service": "payment-api",
  "trace_id": "abc123",
  "message": "Failed to process payment",
  "error": "connection timeout"
}
```

---

## 10.3 Metrics Standards

- Every service must expose a `/metrics` endpoint (Prometheus format)
- **Golden Signals** must be monitored for every service:
  - **Latency** — how long requests take
  - **Traffic** — requests per second
  - **Errors** — error rate
  - **Saturation** — resource utilization (CPU, memory, disk)
- Dashboards must be created in Grafana and linked in the service runbook

---

## 10.4 Distributed Tracing

- All inter-service calls must include **trace context headers**
- Use OpenTelemetry SDK for instrumentation
- Traces must be visible in Jaeger / Tempo dashboards
- Sampling rate: 100% in dev/staging, 10% in production (adjust per service)

---

## 10.5 Dashboard Standards

- Every service must have a Grafana dashboard
- Dashboard must include: error rate, latency (p50/p95/p99), throughput, saturation
- Dashboards stored as code in the `grafana-dashboards` repository
- Dashboard link must be added to the service runbook

---

## 10.6 Related Pages

- → Section 11: Alerts & Alerting Policy
- → Section 12: Incident Response & Postmortem
- → Section 13: Runbooks & Playbooks
