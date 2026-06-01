# 22. Glossary & References

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Team
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 22.1 Glossary

| Term | Definition |
|---|---|
| **ADR** | Architecture Decision Record — documents a key design or technical decision |
| **Blue/Green Deployment** | Deployment strategy using two identical environments; traffic switches atomically between them |
| **Canary Deployment** | Gradual traffic shift to new version while monitoring metrics before full rollout |
| **Cosign** | Tool for signing and verifying container images as part of the Sigstore project |
| **CUR** | Cost and Usage Report — detailed AWS billing data for cost analysis |
| **Error Budget** | Allowed failure margin = `1 - SLO`. Exhausting it triggers a reliability freeze |
| **FinOps** | Cloud financial management practice — bringing financial accountability to cloud spending |
| **Infracost** | Tool that estimates cloud cost changes from Terraform diffs, shown in PRs |
| **Karpenter** | AWS-native Kubernetes node autoscaler that provisions right-sized nodes (including Spot) |
| **OIDC** | OpenID Connect — standard used for keyless, short-lived credential exchange between CI and cloud |
| **SBOM** | Software Bill of Materials — machine-readable inventory of all components in a software artifact |
| **Sigstore** | Open-source project providing free tools for signing software artifacts (Cosign, Fulcio, Rekor) |
| **SLSA** | Supply-chain Levels for Software Artifacts — security framework for artifact integrity |
| **SLI** | Service Level Indicator — specific metric measuring service behavior (e.g. availability %) |
| **SLO** | Service Level Objective — internal target value for an SLI (e.g. 99.9% availability) |
| **Spot Instance** | AWS EC2 instance using spare capacity at up to 90% discount; can be reclaimed with 2-min notice |
| **ArgoCD** | GitOps continuous delivery tool for Kubernetes |
| **CVSS** | Common Vulnerability Scoring System — standard for rating security vulnerabilities |
| **DAST** | Dynamic Application Security Testing — testing a running application for vulnerabilities |
| **DORA** | DevOps Research and Assessment — framework for measuring DevOps team performance |
| **DR** | Disaster Recovery — process of restoring systems after a catastrophic failure |
| **EKS** | Elastic Kubernetes Service — AWS managed Kubernetes |
| **Error Budget** | The allowed amount of downtime or errors before an SLO is breached |
| **GitOps** | Infrastructure and app management using Git as the single source of truth |
| **Helm** | Kubernetes package manager for deploying and managing applications |
| **IAM** | Identity and Access Management — controls who can access what resources |
| **IaC** | Infrastructure as Code — managing infrastructure through machine-readable config files |
| **IC** | Incident Commander — the person coordinating the response during an incident |
| **ICT** | Indochina Time (UTC+7) — the timezone used by our team in Ho Chi Minh City |
| **MTTR** | Mean Time to Recovery — average time to restore service after an incident |
| **OpsGenie** | On-call alerting and incident management platform |
| **PagerDuty** | On-call alerting platform used for escalation and incident notification |
| **Postmortem** | Blameless review of an incident to identify root cause and prevent recurrence |
| **RBAC** | Role-Based Access Control — access permissions assigned based on roles |
| **RFC** | Request for Comments — process for proposing, discussing, and deciding on changes |
| **RPO** | Recovery Point Objective — the maximum acceptable amount of data loss |
| **RTO** | Recovery Time Objective — the maximum acceptable time to restore a service |
| **Runbook** | Step-by-step operational guide for responding to a specific alert or task |
| **SAST** | Static Application Security Testing — scanning source code for vulnerabilities |
| **SLA** | Service Level Agreement — commitments made to other teams or stakeholders |
| **SLI** | Service Level Indicator — a specific measurable metric (e.g. uptime percentage) |
| **SLO** | Service Level Objective — the target value for an SLI (e.g. 99.9% uptime) |
| **SRE** | Site Reliability Engineer — focuses on availability, latency, and scalability |
| **Terraform** | Infrastructure as Code tool by HashiCorp |
| **Toil** | Repetitive, manual operational work that should be automated |
| **Vault** | HashiCorp secrets management and encryption tool |

---

## 22.2 Key External References

| Resource | Description | URL |
|---|---|---|
| Google SRE Book | Foundational SRE practices from Google | https://sre.google/sre-book/table-of-contents/ |
| Google SRE Workbook | Practical SRE implementation guide | https://sre.google/workbook/table-of-contents/ |
| The DevOps Handbook | Core DevOps principles and practices | https://itrevolution.com/the-devops-handbook/ |
| DORA Metrics | Industry standard DevOps performance metrics | https://dora.dev |
| Terraform Docs | Official Terraform documentation | https://developer.hashicorp.com/terraform/docs |
| Kubernetes Docs | Official Kubernetes documentation | https://kubernetes.io/docs |
| AWS Well-Architected | AWS best practices framework | https://aws.amazon.com/architecture/well-architected/ |
| OWASP Top 10 | Top 10 web application security risks | https://owasp.org/www-project-top-ten/ |
| CNCF Landscape | Cloud native technology landscape | https://landscape.cncf.io |
| OpenTelemetry | Observability framework for tracing and metrics | https://opentelemetry.io/docs/ |
| ArgoCD Docs | GitOps CD tool documentation | https://argo-cd.readthedocs.io |

---

## 22.3 Internal References

| Document | Confluence Location |
|---|---|
| All DevOps runbooks | `Confluence > DEVOPS > Runbooks` |
| Postmortem archive | `Confluence > DEVOPS > Postmortems` |
| DR drill records | `Confluence > DEVOPS > DR Drills` |
| Architecture diagrams | `Confluence > DEVOPS > Architecture` |
| Backup verification logs | `Confluence > DEVOPS > Backup Verification` |
| Grafana dashboards | `[Internal Grafana URL]` |
| Jira DevOps board | `[Internal Jira URL]` |
| On-call log | `[Internal PagerDuty / OpsGenie URL]` |
| Access audit register | `Confluence > DEVOPS > Access Audit` |

---

## 22.4 Decision Log

> Log all major team decisions here for traceability.

| Date | Decision | Context | Made By | Status |
|---|---|---|---|---|
| 2026-04-05 | Adopt Terraform as standard IaC tool | Standardize infra management across all teams | DevOps Lead | ✅ Active |
| 2026-04-05 | Use GitHub Actions as primary CI platform | Consolidate CI tooling, reduce maintenance overhead | DevOps Lead | ✅ Active |
| 2026-04-05 | Standardize on EKS for container orchestration | Leverage managed Kubernetes on AWS | DevOps Team | ✅ Active |
| 2026-04-05 | Use PagerDuty for on-call alerting | Centralize escalation and on-call scheduling | DevOps Lead | ✅ Active |
| 2026-04-05 | Adopt blameless postmortem culture | Improve psychological safety and incident learning | DevOps Lead + EM | ✅ Active |

---

## 22.5 Handbook Changelog

> Track major updates to this handbook.

| Date | Section Updated | Change Summary | Updated By |
|---|---|---|---|
| 2026-04-05 | All sections | Initial handbook created | DevOps Lead |
| 2026-05-29 | Section 8 | Added Deployment Strategies (Blue/Green, Canary, Rolling) | DevOps Lead |
| 2026-05-29 | Section 9 | Added OIDC-based CI/CD authentication (keyless) | DevOps Lead |
| 2026-05-29 | Section 10 | Added SLI/SLO/Error Budget guide with Prometheus examples | DevOps Lead |
| 2026-05-29 | Section 15 | Added Supply Chain Security (SBOM, Cosign, SLSA) | DevOps Lead |
| 2026-05-29 | Section 23 | New section: Cost Optimization & FinOps | DevOps Lead |
| 2026-05-29 | Section 24 | New section: Learning Resources & Reference Library | DevOps Lead |

---

_✅ End of DevOps Team Handbook — All 24 Sections Complete_

_This document is a living handbook. Keep it updated, keep it useful._
_For questions or contributions, contact the DevOps Lead or raise a Jira ticket tagged `[DOC]`_
