# 8. Environments & Release Process

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 8.1 Environment Overview

| Environment | Purpose | Access | Deployment Trigger |
|---|---|---|---|
| **dev** | Development & testing | All engineers | Auto on merge to `dev` branch |
| **staging** | Pre-production validation | Engineers + QA | Auto on merge to `main` |
| **production** | Live system | DevOps + Leads only | Manual approval required |

---

## 8.2 Release Process

```
1. Developer raises PR → Code Review → Merge to main
2. CI pipeline runs automatically
3. Auto-deploy to staging
4. QA / smoke tests pass
5. DevOps Lead or Senior Engineer approves production release
6. Deploy to production
7. Post-deploy health checks run
8. Notify stakeholders via Slack #deployments
```

---

## 8.3 Release Windows

| Environment | Allowed Times |
|---|---|
| dev | Anytime |
| staging | Anytime during business hours |
| production | Tuesday–Thursday, 10:00–16:00 ICT (avoid Mondays and Fridays) |

> ⚠️ **Freeze Periods:** No production deployments during major sales events, public holidays, or as announced by the Engineering Manager.

---

## 8.4 Hotfix Process

1. Create branch from `main`: `hotfix/issue-description`
2. Fix, test, and raise PR with `[HOTFIX]` label
3. Fast-track review (minimum 1 approver)
4. Deploy directly to production with on-call engineer present
5. Backport fix to other branches if needed
6. Document in incident log (Section 12)

---

## 8.5 Release Notes

- Every production release must have a brief release note posted to `#deployments`
- Format: **What changed | Who deployed | Rollback plan**

---

## 8.6 Related Pages

- → Section 7: CI/CD Standards & Pipelines
- → Section 12: Incident Response & Postmortem
- → Section 17: Change Management & Approvals
