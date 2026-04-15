# 5. Project Initiation Checklist

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 5.1 Purpose

Before any new project, service, or infrastructure component is started, this checklist must be completed. It ensures every initiative is properly planned, secured, and observable from day one.

---

## 5.2 Pre-Project Checklist

### 📋 Planning
- [ ] Project name, owner, and stakeholders defined
- [ ] Jira epic created and linked to roadmap
- [ ] Confluence page created under correct space
- [ ] Architecture diagram drafted (even rough)
- [ ] Estimated timeline and milestones agreed

### ☁️ Infrastructure
- [ ] Cloud account / project created or identified
- [ ] Tagging strategy applied (team, environment, cost-center)
- [ ] Infrastructure-as-code repo initialized
- [ ] Environments planned: `dev`, `staging`, `production`
- [ ] Cost estimate reviewed and approved

### 🔐 Security
- [ ] IAM roles and permissions defined (least privilege)
- [ ] Secrets management strategy confirmed (Vault / AWS Secrets Manager)
- [ ] Network security groups / firewall rules reviewed
- [ ] Security scan added to CI/CD pipeline

### 🚀 CI/CD
- [ ] Repository created with branch protection rules
- [ ] CI pipeline template applied
- [ ] CD pipeline defined for each environment
- [ ] Deployment runbook drafted

### 📊 Observability
- [ ] Logging strategy defined (log format, log level, destination)
- [ ] Metrics defined and Grafana dashboard created
- [ ] Alerting rules configured (see Section 11)
- [ ] Tracing enabled (where applicable)

### 📄 Documentation
- [ ] README written in the repository
- [ ] Architecture decision records (ADRs) started
- [ ] Runbook created or planned
- [ ] Confluence page updated with project overview

---

## 5.3 Project Approval Sign-Off

| Reviewer | Role | Sign-Off |
|---|---|---|
| _[Name]_ | DevOps Lead | ⬜ Pending |
| _[Name]_ | Tech Lead | ⬜ Pending |
| _[Name]_ | Security Engineer | ⬜ Pending |
| _[Name]_ | Engineering Manager | ⬜ Pending |

---

## 5.4 Related Pages

- → Section 6: Repo & Infrastructure Standards
- → Section 7: CI/CD Standards & Pipelines
- → Section 9: Secrets & Access Management
- → Section 10: Observability
