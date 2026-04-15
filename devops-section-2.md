# 2. Roles & Responsibilities

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`
> **Audience:** All DevOps Members, Engineering Managers, HR

---

## 2.1 Team Structure Overview

The DevOps team operates as a **platform and enablement team**, supporting all engineering squads across the organization. We are structured to balance operational reliability with continuous delivery capabilities.

```
Org Chart (Simplified)

Engineering Manager
└── DevOps Lead
    ├── Senior DevOps Engineer(s)
    │   └── DevOps Engineer(s)
    ├── Site Reliability Engineer (SRE)
    └── DevSecOps / Security Engineer
```

---

## 2.2 Role Definitions

### 🧑‍💼 DevOps Lead
| Field | Details |
|---|---|
| **Reports To** | Engineering Manager |
| **Level** | Senior / Staff |
| **Headcount** | 1 |

**Responsibilities:**
- Own the overall DevOps strategy and roadmap
- Define standards for infrastructure, CI/CD, and security
- Coordinate with Engineering Managers and Tech Leads across squads
- Review and approve major architectural and infrastructure changes
- Drive hiring, onboarding, and team culture
- Represent DevOps in cross-functional planning meetings

---

### ⚙️ Senior DevOps Engineer
| Field | Details |
|---|---|
| **Reports To** | DevOps Lead |
| **Level** | Senior |
| **Headcount** | 2–3 |

**Responsibilities:**
- Design and maintain CI/CD pipelines and infrastructure automation
- Lead technical implementation of platform improvements
- Mentor junior and mid-level engineers
- Conduct architecture reviews and code reviews for infra changes
- Own specific domains (e.g. Kubernetes, Networking, Observability)
- Participate in on-call rotation and incident response

---

### 🔧 DevOps Engineer
| Field | Details |
|---|---|
| **Reports To** | Senior DevOps Engineer / DevOps Lead |
| **Level** | Mid-Level |
| **Headcount** | 3–5 |

**Responsibilities:**
- Build, maintain, and improve CI/CD pipelines
- Manage cloud infrastructure (provisioning, scaling, cost optimization)
- Support development teams with environment and deployment issues
- Write and maintain infrastructure-as-code (Terraform / Pulumi / Ansible)
- Participate in on-call rotation
- Document processes and runbooks

---

### 🛡️ Site Reliability Engineer (SRE)
| Field | Details |
|---|---|
| **Reports To** | DevOps Lead |
| **Level** | Mid / Senior |
| **Headcount** | 1–2 |

**Responsibilities:**
- Define and monitor SLOs, SLIs, and error budgets
- Lead incident response and postmortem processes
- Improve system reliability, latency, and availability
- Build observability tooling (dashboards, alerting, tracing)
- Work closely with development teams on reliability best practices
- Own the on-call escalation framework

---

### 🔐 DevSecOps / Security Engineer
| Field | Details |
|---|---|
| **Reports To** | DevOps Lead |
| **Level** | Mid / Senior |
| **Headcount** | 1 |

**Responsibilities:**
- Embed security practices into CI/CD pipelines (SAST, DAST, dependency scanning)
- Manage secrets, access control, and credential policies
- Conduct regular security audits and vulnerability assessments
- Ensure compliance with internal policies and external regulations
- Maintain documentation for security and compliance (Section 15)
- Respond to security incidents alongside the SRE team

---

## 2.3 RACI Matrix

> **R** = Responsible | **A** = Accountable | **C** = Consulted | **I** = Informed

| Task | DevOps Lead | Senior DevOps Eng | DevOps Eng | SRE | DevSecOps |
|---|---|---|---|---|---|
| Define infrastructure standards | A | R | C | C | C |
| CI/CD pipeline changes | A | R | R | I | C |
| Production deployments | A | C | R | C | I |
| Incident response | A | C | I | R | C |
| Security audit & compliance | A | I | I | C | R |
| On-call rotation | A | R | R | R | I |
| Runbook creation | C | A | R | R | C |
| New member onboarding | A | R | R | I | I |
| Cost optimization | A | R | R | I | I |
| Postmortem facilitation | I | C | I | R | I |

---

## 2.4 Team Member Directory

> 📝 **Note:** Update this table when team changes occur. Keep it current.

| Name | Role | Squad Focus | Slack Handle | Email | On-Call? |
|---|---|---|---|---|---|
| _[Name]_ | DevOps Lead | All | @name | name@company.com | ✅ |
| _[Name]_ | Senior DevOps Engineer | CI/CD & Pipelines | @name | name@company.com | ✅ |
| _[Name]_ | Senior DevOps Engineer | Kubernetes & Infra | @name | name@company.com | ✅ |
| _[Name]_ | DevOps Engineer | Cloud & Provisioning | @name | name@company.com | ✅ |
| _[Name]_ | SRE | Reliability & Alerting | @name | name@company.com | ✅ |
| _[Name]_ | DevSecOps Engineer | Security & Compliance | @name | name@company.com | ⬜ |

---

## 2.5 Team Norms & Expectations

- **Ownership:** Every engineer owns their work end-to-end — from code to production
- **Availability:** Core hours are `09:00–18:00 ICT (UTC+7)`. Async communication is encouraged outside these hours
- **On-Call:** Rotating weekly. Schedule managed in PagerDuty / OpsGenie
- **Code Reviews:** All infrastructure changes require at least **1 peer review** before merging
- **Escalation:** When in doubt, escalate early — not late

---

## 2.6 Related Pages

- → Section 1: Introduction & Goals
- → Section 3: Skills & Learning Roadmap
- → Section 4: Onboarding & 30/60/90 Plan
- → Section 14: On-Call Rotations & Escalation
- → Section 19: Meetings, Communications & SLAs
