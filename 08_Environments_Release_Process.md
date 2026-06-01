# 8. Environments & Release Process

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-05-29
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

## 8.6 Deployment Strategies

Choose the right strategy based on risk tolerance, rollback speed, and infrastructure support.

### Rolling Update (Default)

Gradually replace old instances with new ones. Zero downtime for stateless services.

```
v1 v1 v1 v1
→ v2 v1 v1 v1
→ v2 v2 v1 v1
→ v2 v2 v2 v1
→ v2 v2 v2 v2
```

**When to use:** Standard deployments for stateless services on Kubernetes.  
**Rollback:** `kubectl rollout undo deployment/<name>`  
**Risk:** Both versions run simultaneously — ensure backward compatibility.

---

### Blue/Green Deployment

Two identical environments: Blue (current) and Green (new). Traffic switches atomically.

```
           ┌──────────────┐
Traffic →  │  Blue (v1)   │  ← 100% live
           └──────────────┘
           ┌──────────────┐
           │  Green (v2)  │  ← idle, being tested
           └──────────────┘

After validation:
           ┌──────────────┐
           │  Blue (v1)   │  ← idle (keep for rollback)
           └──────────────┘
Traffic →  ┌──────────────┐
           │  Green (v2)  │  ← 100% live
           └──────────────┘
```

**When to use:** High-risk releases, database schema changes, major version upgrades.  
**Rollback:** Flip traffic back to Blue — near instant.  
**Cost:** Requires 2x infrastructure during deployment window.  
**Tools:** AWS ALB target group swap, Route 53 weighted routing, ArgoCD BlueGreen rollout.

---

### Canary Deployment

Route a small % of traffic to new version, gradually increase if metrics are healthy.

```
100% → v1
 95% → v1  +  5% → v2   ← monitor metrics
 80% → v1  + 20% → v2   ← still healthy?
  0% → v1  + 100% → v2  ← full rollout
```

**When to use:** Features with uncertain performance impact, high-traffic services.  
**Rollback:** Set canary weight to 0%, full traffic returns to stable.  
**Tools:** ArgoCD Rollouts, Flagger, AWS ALB weighted target groups, Istio.

**Canary success criteria (example):**
- Error rate < 1% on canary pods
- P99 latency within 10% of baseline
- No increase in 5xx responses
- Hold each stage for minimum 10 minutes before advancing

---

### Strategy Selection Guide

| Scenario | Recommended Strategy |
|---|---|
| Standard microservice update | Rolling Update |
| Breaking API change | Blue/Green |
| DB migration with backward compat | Blue/Green |
| New feature — uncertain load impact | Canary |
| Critical payment / auth service | Blue/Green or Canary |
| Hotfix / urgent patch | Rolling Update (fastest) |
| ML model update | Canary (A/B traffic split) |

---

## 8.7 Related Pages

- → Section 7: CI/CD Standards & Pipelines
- → Section 12: Incident Response & Postmortem
- → Section 17: Change Management & Approvals
- → Section 10: Observability (monitor canary metrics)
