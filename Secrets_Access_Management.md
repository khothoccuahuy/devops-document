# 9. Secrets & Access Management

> **Document Status:** 🟡 Draft
> **Owner:** DevSecOps Engineer
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 9.1 Principles

- **Never hardcode secrets** in code, configs, or CI/CD pipelines
- **Least privilege:** every role and service gets only the access it needs
- **Rotate regularly:** credentials must be rotated on schedule or after any suspected exposure
- **Audit everything:** all access must be logged and auditable

---

## 9.2 Secrets Management Tools

| Use Case | Tool |
|---|---|
| Application secrets | HashiCorp Vault / AWS Secrets Manager |
| CI/CD pipeline secrets | GitHub Actions Secrets / GitLab CI Variables |
| Cloud credentials | IAM Roles (no long-lived keys) |
| SSH keys | SSH Certificate Authority (Vault SSH) |
| Database passwords | Vault dynamic secrets |

---

## 9.3 Access Control Policy

- All cloud access via **IAM roles** — no shared accounts or root access
- MFA required for all human access to production
- Service accounts must use **short-lived tokens** where possible
- Access reviews conducted **quarterly** by DevOps Lead
- Offboarding checklist must revoke all access within **24 hours** of departure

---

## 9.4 Secret Rotation Schedule

| Secret Type | Rotation Frequency |
|---|---|
| Database passwords | Every 90 days |
| API keys (3rd party) | Every 90 days or on personnel change |
| Cloud IAM keys (if used) | Every 30 days |
| SSH keys | Every 180 days |
| TLS certificates | Auto-renewed via Let's Encrypt / ACM |

---

## 9.5 Incident Response for Credential Exposure

1. **Immediately revoke** the exposed credential
2. Notify DevOps Lead and Security Engineer
3. Audit logs for unauthorized usage
4. Rotate all related secrets
5. Document in incident log (Section 12)
6. Conduct postmortem to prevent recurrence

---

## 9.6 Related Pages

- → Section 15: Security & Compliance
- → Section 12: Incident Response & Postmortem
- → Section 17: Change Management & Approvals
