# 18. Metrics & KPIs

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead / SRE
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 18.1 How We Measure Success

We track metrics across four categories: **Reliability, Velocity, Security, and Team Health.** These are reviewed weekly, monthly, and quarterly to drive continuous improvement.

---

## 18.2 DORA Metrics (Delivery Performance)

> DORA metrics are the industry standard for measuring DevOps team performance.

| Metric | Description | Our Target | Current |
|---|---|---|---|
| **Deployment Frequency** | How often we deploy to production | Daily or multiple/week | _[fill in]_ |
| **Lead Time for Changes** | Time from commit to production | < 1 day | _[fill in]_ |
| **Change Failure Rate** | % of deployments causing incidents | < 5% | _[fill in]_ |
| **MTTR** | Mean time to restore service after incident | < 1 hour | _[fill in]_ |

---

## 18.3 Reliability Metrics

| Metric | Target | Measurement Tool |
|---|---|---|
| Uptime / Availability | 99.9% per critical service | Grafana / Datadog |
| P95 API Latency | < 500ms | Prometheus |
| P99 API Latency | < 1000ms | Prometheus |
| Error Rate | < 1% | Grafana |
| Alert Noise Rate | < 10 false positives/week | PagerDuty |
| On-call incidents per week | < 5 avg | PagerDuty |

---

## 18.4 Security Metrics

| Metric | Target |
|---|---|
| Critical vulnerabilities open > 24h | 0 |
| High vulnerabilities open > 7 days | 0 |
| Access reviews completed on schedule | 100% |
| Secrets rotated on schedule | 100% |
| Security scans passing in CI | 100% of pipelines |

---

## 18.5 Team Health Metrics

| Metric | Target | How Measured |
|---|---|---|
| Postmortems completed on time | 100% | Confluence tracking |
| Runbook coverage for all alerts | 100% | Manual audit |
| Team satisfaction score | > 4/5 | Quarterly survey |
| Learning budget utilization | > 80% | HR / Finance report |
| On-call toil hours per week | < 4 hours avg | On-call log |

---

## 18.6 Reporting Cadence

| Frequency | Report | Audience |
|---|---|---|
| **Weekly** | DORA metrics snapshot | DevOps team standup |
| **Monthly** | Full KPI dashboard review | DevOps team + EM |
| **Quarterly** | Trend report + OKR alignment | Engineering leadership |

---

## 18.7 KPI Dashboard

- Live KPI dashboard available at: `[Internal Grafana URL]`
- Dashboard includes: DORA metrics, reliability SLOs, security posture
- Dashboard source stored in `grafana-dashboards` repository

---

## 18.8 Related Pages

- → Section 10: Observability
- → Section 11: Alerts & Alerting Policy
- → Section 19: Meetings, Communications & SLAs
