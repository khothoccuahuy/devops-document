# 13. Runbooks & Playbooks

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Team
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 13.1 What Is a Runbook?

A runbook is a **step-by-step procedure** for handling a specific operational task or incident. It removes guesswork during high-pressure situations.

- **Runbook:** Reactive — how to respond to a specific alert or issue
- **Playbook:** Proactive — how to perform a repeatable operational task

---

## 13.2 Runbook Template

```markdown
# Runbook: [Alert or Task Name]

**Service:** [Service name]
**Alert:** [Alert name that triggers this runbook]
**Severity:** P[1/2/3/4]
**Owner:** [Team or person]
**Last Updated:** YYYY-MM-DD

## Symptoms
- What does the alert look like?
- What do users experience?

## Possible Causes
1. Cause A
2. Cause B

## Investigation Steps
1. Check dashboard: [link]
2. Run command: `kubectl get pods -n namespace`
3. Check logs: `kubectl logs pod-name`

## Resolution Steps
1. If cause A → do X
2. If cause B → do Y
3. If unsure → escalate to [person/channel]

## Rollback Steps
1. Step 1
2. Step 2

## Escalation
- Escalate to: @on-call-engineer → @devops-lead
- Escalation channel: #incidents

## Related Links
- Dashboard: [link]
- Alert rule: [link]
- Postmortem history: [link]
```

---

## 13.3 Runbook Index

| Runbook | Service | Severity | Link |
|---|---|---|---|
| High CPU on EKS nodes | Kubernetes | P2 | [Link] |
| Database connection pool exhausted | RDS | P1 | [Link] |
| CI/CD pipeline stuck | GitHub Actions | P3 | [Link] |
| Certificate expiry warning | All services | P2 | [Link] |
| Deploy rollback procedure | All services | P1 | [Link] |
| Disk space critical | All nodes | P2 | [Link] |

---

## 13.4 Runbook Standards

- Every alert in Section 11 must have a linked runbook
- Runbooks reviewed and tested **quarterly**
- All engineers are expected to contribute and update runbooks
- Outdated runbooks must be flagged with `⚠️ Needs Review`

---

## 13.5 Related Pages

- → Section 11: Alerts & Alerting Policy
- → Section 12: Incident Response & Postmortem
- → Section 10: Observability
