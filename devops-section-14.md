# 14. On-Call Rotations & Escalation

> **Document Status:** 🟡 Draft
> **Owner:** SRE / DevOps Lead
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 14.1 On-Call Philosophy

- On-call is a **shared responsibility** — no single person carries it alone
- On-call engineers are **first responders**, not sole resolvers
- If you are overwhelmed, **escalate immediately** — no heroics
- On-call feedback is reviewed monthly to improve systems and reduce toil

---

## 14.2 On-Call Schedule

- Rotation: **Weekly** (Monday 09:00 ICT → Monday 09:00 ICT)
- Managed in: **PagerDuty / OpsGenie**
- Minimum 2 engineers per rotation (primary + secondary)
- New engineers shadow for 4 weeks before going on-call solo

| Week | Primary | Secondary |
|---|---|---|
| Week 1 | [Name] | [Name] |
| Week 2 | [Name] | [Name] |
| Week 3 | [Name] | [Name] |
| Week 4 | [Name] | [Name] |

---

## 14.3 Escalation Path

```
Alert Fires
  │
  ├── Primary On-Call (respond within 5 min for P1)
  │     │
  │     └── No response → Secondary On-Call (10 min)
  │           │
  │           └── No response → DevOps Lead (15 min)
  │                 │
  │                 └── No response → Engineering Manager (20 min)
```

---

## 14.4 On-Call Responsibilities

- Acknowledge alerts within SLA (P1: 5 min, P2: 30 min)
- Follow runbooks for known issues
- Declare incidents when needed (Section 12)
- Hand off clearly at end of rotation (open issues, ongoing investigations)
- Log all significant events in the on-call log

---

## 14.5 On-Call Compensation

- On-call compensation policy: _[refer to HR policy or add details here]_
- Swap requests must be agreed between engineers and approved by DevOps Lead at least **48 hours** in advance

---

## 14.6 Related Pages

- → Section 11: Alerts & Alerting Policy
- → Section 12: Incident Response & Postmortem
- → Section 13: Runbooks & Playbooks
