# 12. Incident Response & Postmortem

> **Document Status:** 🟡 Draft
> **Owner:** SRE
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 12.1 Incident Response Process

```
Alert Fires / Issue Reported
  │
  ├── 1. DETECT — On-call engineer acknowledges within SLA
  ├── 2. ASSESS — Determine severity (P1–P4)
  ├── 3. DECLARE — Open incident channel #incident-YYYY-MM-DD
  ├── 4. COMMUNICATE — Notify stakeholders, update status page
  ├── 5. MITIGATE — Restore service (rollback, scale, patch)
  ├── 6. RESOLVE — Confirm resolution, close incident
  └── 7. POSTMORTEM — Conduct within 48 hours for P1/P2
```

---

## 12.2 Incident Roles

| Role | Responsibility |
|---|---|
| **Incident Commander (IC)** | Coordinates response, owns communication |
| **Technical Lead** | Leads investigation and mitigation |
| **Comms Lead** | Updates status page and stakeholders |
| **Scribe** | Documents timeline and actions in real-time |

---

## 12.3 Communication Templates

**Initial Notification:**
```
🔴 INCIDENT DECLARED — [Service Name]
Severity: P[1/2]
Impact: [What is affected]
Status: Investigating
IC: @name
Next update in: 15 minutes
```

**Resolution Notification:**
```
✅ INCIDENT RESOLVED — [Service Name]
Duration: [X hours Y minutes]
Root Cause: [Brief summary]
Postmortem: [Link — to be added]
```

---

## 12.4 Postmortem Process

- Postmortems are **blameless** — we fix systems, not people
- Required for all **P1 and P2** incidents
- Must be completed within **48 hours** of resolution
- Published to Confluence under `DEVOPS > Postmortems`

**Postmortem Template:**

```
## Incident Summary
- Date/Time:
- Duration:
- Severity:
- Services Affected:
- On-Call Engineer:

## Timeline
| Time  | Event                        |
|-------|------------------------------|
| HH:MM | Alert fired                  |
| HH:MM | IC declared incident         |
| HH:MM | Root cause identified        |
| HH:MM | Mitigation applied           |
| HH:MM | Incident resolved            |

## Root Cause Analysis
[Describe the root cause]

## What Went Well
-
-

## What Went Wrong
-
-

## Action Items
| Action | Owner | Due Date |
|--------|-------|----------|
|        |       |          |
```

---

## 12.5 Related Pages

- → Section 11: Alerts & Alerting Policy
- → Section 13: Runbooks & Playbooks
- → Section 14: On-Call Rotations & Escalation
