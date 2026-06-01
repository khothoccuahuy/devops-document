# 10. Observability

> **Document Status:** 🟡 Draft
> **Owner:** SRE
> **Last Updated:** 2026-05-29
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

## 10.6 SLI, SLO & Error Budget

### Definitions

| Term | Definition | Example |
|---|---|---|
| **SLI** (Service Level Indicator) | A specific metric that measures service behavior | Availability = successful requests / total requests |
| **SLO** (Service Level Objective) | The target value for an SLI | Availability SLO = 99.9% over 30 days |
| **Error Budget** | Allowed room for failures = `1 - SLO` | 99.9% SLO → 0.1% budget = ~43 min/month downtime |
| **SLA** | External commitment to customers (legal/contractual) | "We guarantee 99.5% uptime or issue credits" |

> **Rule:** SLO must be stricter than SLA. If SLA = 99.5%, set SLO = 99.9% internally.

---

### How to Define an SLO

**Step 1 — Pick meaningful SLIs for your service type:**

| Service Type | Recommended SLIs |
|---|---|
| API / HTTP service | Availability (2xx/5xx ratio), latency (p99) |
| Data pipeline | Freshness (data age), completeness (records processed) |
| Background job | Success rate, duration |
| Storage | Durability, read/write latency |

**Step 2 — Set realistic targets** based on historical data, not aspirations:

```
Bad:  SLO = 99.999% (5 nines) for a non-critical internal service
Good: SLO = 99.9% for a critical API, 99.5% for a batch job
```

**Step 3 — Define the measurement window:**
- Rolling 28-day window (recommended — no cliff effect at month boundary)
- Or calendar month (simpler to communicate)

**Step 4 — Document in service runbook** (Section 13):

```markdown
## SLO Definition — payment-api

| SLI | Measurement | SLO Target |
|-----|-------------|------------|
| Availability | HTTP 5xx rate < threshold | 99.9% over 28 days |
| Latency | p99 response time | < 500ms, 99% of requests |

Error Budget: 0.1% = ~43.2 minutes/month
```

---

### Error Budget Policy

| Budget Remaining | Action |
|---|---|
| > 50% | Normal development velocity |
| 25–50% | Review recent incidents, tighten testing |
| < 25% | Freeze non-critical feature releases, focus on reliability |
| Exhausted (0%) | Freeze all feature work until next window resets |

> The error budget freeze is a **team agreement**, not a punishment. It keeps reliability and velocity in balance.

---

### Prometheus SLO Example

```yaml
# Availability SLO — % of requests that succeed
- record: job:request_success_rate:ratio_rate5m
  expr: |
    sum(rate(http_requests_total{status!~"5.."}[5m]))
    /
    sum(rate(http_requests_total[5m]))

# Alert when burning error budget too fast (burn rate > 14x in 1h)
- alert: HighErrorBudgetBurn
  expr: job:request_success_rate:ratio_rate5m < 0.999
  for: 5m
  labels:
    severity: critical
  annotations:
    summary: "SLO breach risk — error budget burning fast"
    runbook: "[link]"
```

---

### SLO Review Cadence

- **Weekly:** Check error budget consumption in Grafana
- **Monthly:** Review SLOs in KPI meeting — adjust targets if consistently over/under
- **Quarterly:** Reassess SLOs against business requirements and growth

---

## 10.7 Related Pages

- → Section 11: Alerts & Alerting Policy
- → Section 12: Incident Response & Postmortem
- → Section 13: Runbooks & Playbooks
- → Section 18: Metrics & KPIs
