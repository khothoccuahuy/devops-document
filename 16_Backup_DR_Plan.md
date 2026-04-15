# 16. Backup & DR Plan

> **Document Status:** 🟡 Draft
> **Owner:** SRE / DevOps Lead
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 16.1 Backup Policy

| Data Type | Backup Frequency | Retention | Storage |
|---|---|---|---|
| Databases (RDS / Postgres) | Daily automated + on-demand before deployments | 30 days | S3 (encrypted) |
| Object storage (S3) | Versioning enabled + cross-region replication | 90 days | S3 cross-region |
| Kubernetes configs | GitOps — all configs in Git | Indefinite | GitHub |
| Application logs | Streamed to centralized log store | 30 days hot / 1 year cold | S3 |
| Secrets (Vault) | Daily snapshot | 30 days | Encrypted S3 |

---

## 16.2 Recovery Objectives

| Metric | Definition | Target |
|---|---|---|
| **RTO** (Recovery Time Objective) | Maximum acceptable time to restore service | < 1 hour for P1 services |
| **RPO** (Recovery Point Objective) | Maximum acceptable data loss window | < 15 minutes for critical DBs |

---

## 16.3 Backup Verification

- Backups are tested **monthly** via automated restore to a sandbox environment
- Results logged in Confluence under `DEVOPS > Backup Verification`
- Any failed backup triggers a P2 alert immediately

---

## 16.4 Disaster Recovery Runbook

```
1. DECLARE DR EVENT
   └── Notify DevOps Lead and Engineering Manager

2. ASSESS SCOPE
   └── Which systems are affected? Single service or full region?

3. ACTIVATE STANDBY RESOURCES
   └── Spin up from IaC or failover to secondary region

4. RESTORE DATA
   └── Restore from latest verified backup
   └── Verify data integrity before proceeding

5. VALIDATE SERVICES
   └── Run smoke tests across all critical paths
   └── Confirm metrics and dashboards are healthy

6. COMMUNICATE
   └── Update status page
   └── Notify stakeholders and engineering leads

7. POST-DR REVIEW
   └── Document what happened
   └── Create Jira action items tagged [DR]
   └── Update DR plan with lessons learned
```

---

## 16.5 DR Drills

- DR drills conducted **bi-annually** (June and December)
- Scope: simulate full region failure for at least 1 critical service
- Results documented in Confluence under `DEVOPS > DR Drills`
- Action items tracked in Jira tagged `[DR]`

---

## 16.6 DR Contact List

| Role | Name | Contact |
|---|---|---|
| DR Lead | [Name] | [Slack / Phone] |
| DevOps Lead | [Name] | [Slack / Phone] |
| Engineering Manager | [Name] | [Slack / Phone] |
| Cloud Provider Support | AWS / GCP | [Support ticket URL] |

---

## 16.7 Related Pages

- → Section 12: Incident Response & Postmortem
- → Section 15: Security & Compliance
- → Section 10: Observability
