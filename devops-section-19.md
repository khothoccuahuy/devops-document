# 19. Meetings, Communications & SLAs

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 19.1 Regular Meetings

| Meeting | Frequency | Duration | Attendees | Purpose |
|---|---|---|---|---|
| Daily Standup | Daily (Mon–Fri) | 15 min | All DevOps | Progress, blockers, coordination |
| Sprint Planning | Bi-weekly | 1 hour | All DevOps | Plan upcoming sprint work |
| Sprint Retrospective | Bi-weekly | 45 min | All DevOps | What went well/badly, improve |
| KPI Review | Monthly | 1 hour | DevOps + EM | Review metrics, trends, OKRs |
| On-Call Handoff | Weekly | 15 min | Outgoing + incoming on-call | Transfer open issues |
| Alert Review | Monthly | 30 min | SRE + DevOps | Prune and improve alerting |
| 1:1 (Lead ↔ Engineer) | Bi-weekly | 30 min | Lead + each engineer | Career, feedback, blockers |
| Tech Share | Monthly | 45 min | All DevOps | Knowledge sharing, demos |

---

## 19.2 Meeting Norms

- All meetings must have an **agenda** shared at least 24 hours in advance
- Meeting notes posted to Confluence within **24 hours**
- Decisions must be documented — if it's not written down, it didn't happen
- Cameras on for all video calls (unless bandwidth issues)
- Start and end on time — respect everyone's schedule

---

## 19.3 Communication Channels

| Channel | Platform | Purpose |
|---|---|---|
| `#devops` | Slack | General team discussion |
| `#incidents` | Slack | Incident coordination (P1/P2 only) |
| `#alerts` | Slack | Automated alert notifications |
| `#deployments` | Slack | Deployment notifications and release notes |
| `#devops-wins` | Slack | Celebrate achievements, certifications, milestones |
| `#devops-random` | Slack | Non-work chat and team bonding |
| Email | Gmail / Outlook | Formal communication, external stakeholders |
| Jira | Atlassian | Task tracking, change requests, incident tickets |
| Confluence | Atlassian | Documentation, runbooks, postmortems |

---

## 19.4 Communication Norms

- Default to **async** communication — not every message needs an immediate reply
- Use **threads** in Slack to keep channels clean and searchable
- Tag people with `@name` only when **action is required** from them specifically
- For urgent issues outside business hours, use **PagerDuty** — not Slack DMs
- Core hours: `09:00–18:00 ICT (UTC+7)` — async is encouraged outside these hours
- Respond to Slack messages within **4 business hours** during core hours

---

## 19.5 SLAs — Commitments to the Organization

These are the service level agreements our team commits to for internal stakeholders:

| Request Type | Response Time | Resolution Time |
|---|---|---|
| Production incident (P1) | 5 minutes | < 1 hour |
| High severity issue (P2) | 30 minutes | < 4 hours |
| Medium severity issue (P3) | 2 business hours | < 1 business day |
| New environment provisioning | 1 business day | 3 business days |
| Access request | 4 business hours | 1 business day |
| CI/CD pipeline issue | 2 business hours | 1 business day |
| New pipeline setup | 1 business day | 5 business days |
| General support request | 1 business day | 3 business days |
| Documentation request | 2 business days | 5 business days |

> ⚠️ SLAs apply during business hours `09:00–18:00 ICT` unless P1/P2 incidents which are 24/7.

---

## 19.6 Escalation for SLA Breaches

If a request is not resolved within the SLA:
1. Requester pings the assigned engineer directly in Slack
2. If no response within 1 hour → escalate to DevOps Lead
3. DevOps Lead resolves or re-assigns within 2 hours
4. Chronic SLA breaches reviewed in monthly KPI meeting

---

## 19.7 Related Pages

- → Section 2: Roles & Responsibilities
- → Section 14: On-Call Rotations & Escalation
- → Section 18: Metrics & KPIs
