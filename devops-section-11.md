# 11. Alerts & Alerting Policy

> **Document Status:** 🟡 Draft
> **Owner:** SRE
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 11.1 Alerting Philosophy

> _"Every alert must be actionable. If an alert fires and no one knows what to do, it should not exist."_

- Alerts must map to **user impact** or **imminent risk**
- Alerts must have a corresponding **runbook** (Section 13)
- Avoid alert fatigue — review and prune alerts quarterly

---

## 11.2 Alert Severity Levels

| Severity | Description | Response Time | Notify |
|---|---|---|---|
| 🔴 **P1 - Critical** | Production down, data loss, security breach | Immediate (< 5 min) | On-call + DevOps Lead |
| 🟠 **P2 - High** | Major degradation, significant user impact | < 30 min | On-call engineer |
| 🟡 **P3 - Medium** | Partial degradation, workaround available | < 4 hours | Team Slack channel |
| 🟢 **P4 - Low** | Minor issue, no user impact | Next business day | Jira ticket |

---

## 11.3 Alerting Rules Standards

Every alert must have:
- **Name:** Clear, descriptive (e.g. `PaymentAPIHighErrorRate`)
- **Condition:** Specific threshold with duration (e.g. error rate > 5% for 5 minutes)
- **Severity:** P1–P4
- **Runbook link:** Direct link to the relevant runbook
- **Labels:** `service`, `env`, `team`

---

## 11.4 Notification Channels

| Severity | Channel |
|---|---|
| P1 | PagerDuty (phone call) + `#incidents` Slack |
| P2 | PagerDuty (push notification) + `#incidents` Slack |
| P3 | `#alerts` Slack |
| P4 | Jira ticket auto-created |

---

## 11.5 Alert Review Process

- Alerts reviewed **monthly** in team meeting
- Any alert that fired but required no action → candidate for removal or adjustment
- New alerts must be reviewed by SRE before activation

---

## 11.6 Related Pages

- → Section 10: Observability
- → Section 12: Incident Response & Postmortem
- → Section 13: Runbooks & Playbooks
- → Section 14: On-Call Rotations & Escalation
