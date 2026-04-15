# 17. Change Management & Approvals

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 17.1 Purpose

Change management ensures that all modifications to production systems are planned, reviewed, and traceable. It reduces risk while keeping delivery speed high.

---

## 17.2 Change Types

| Type | Description | Approval Required |
|---|---|---|
| **Standard** | Pre-approved, low-risk, routine changes | No — follow checklist |
| **Normal** | Planned changes with known risk | Yes — 1 approver (peer) |
| **Major** | High-impact or large-scope changes | Yes — DevOps Lead + Tech Lead |
| **Emergency** | Hotfix or critical patch | Yes — 1 approver (post-hoc accepted for P1) |

---

## 17.3 Change Request Process

```
1. Create a Jira ticket tagged [CHANGE]
2. Fill in:
   - Description of the change
   - Risk assessment (low / medium / high)
   - Rollback plan
   - Testing evidence
3. Assign to approver(s) based on change type
4. Schedule deployment within release window (Section 8)
5. Execute change and document the result
6. Close Jira ticket with outcome notes
```

---

## 17.4 Change Risk Assessment

| Risk Level | Criteria | Example |
|---|---|---|
| **Low** | Config change, no downtime, instant rollback | Update env variable |
| **Medium** | New feature flag, DB migration with backward compat | Add index to table |
| **High** | Schema breaking change, infrastructure replacement | Replace load balancer |
| **Critical** | Full data migration, multi-system impact | DB engine upgrade |

---

## 17.5 Rollback Requirements

Every change request must include a rollback plan that answers:
- How do we detect that the change caused an issue?
- What are the exact steps to revert?
- Who is responsible for executing the rollback?
- How long will the rollback take?

---

## 17.6 Change Freeze Periods

No changes to production during:
- Company-wide freeze periods (announced by Engineering Manager)
- Major business events (product launches, peak traffic periods)
- Vietnamese public holidays unless explicitly approved by DevOps Lead
- Last 2 business days of each quarter (financial close period)

---

## 17.7 Change Log

All production changes are logged automatically via CI/CD pipeline notifications to `#deployments`. A manual change log is maintained in Confluence for non-automated changes.

| Date | Change | Type | Approved By | Outcome |
|---|---|---|---|---|
| 2026-04-05 | _[Example entry]_ | Normal | [Name] | ✅ Success |

---

## 17.8 Related Pages

- → Section 8: Environments & Release Process
- → Section 7: CI/CD Standards & Pipelines
- → Section 12: Incident Response & Postmortem
