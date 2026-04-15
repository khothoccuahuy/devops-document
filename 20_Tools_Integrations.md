# 20. Tools & Integrations

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 20.1 Core Tool Stack

| Category | Tool | Purpose | Access Method |
|---|---|---|---|
| **Cloud** | AWS / GCP | Infrastructure hosting | IAM role via SSO |
| **IaC** | Terraform | Infrastructure as code | GitHub + Terraform Cloud |
| **Container Orchestration** | Kubernetes (EKS/GKE) | Container management | kubectl + AWS console |
| **CI/CD** | GitHub Actions / ArgoCD | Build & deploy automation | GitHub |
| **Metrics & Dashboards** | Prometheus + Grafana | Metrics visualization | Internal URL |
| **Logging** | ELK Stack / Loki | Centralized log management | Internal URL |
| **Tracing** | Jaeger / Tempo | Distributed tracing | Internal URL |
| **Alerting** | PagerDuty | On-call alerting & escalation | pagerduty.com |
| **Secrets** | HashiCorp Vault | Secrets management | Internal URL |
| **Container Registry** | AWS ECR | Docker image registry | AWS console |
| **Source Control** | GitHub | Code & IaC repository | github.com/org |
| **Project Management** | Jira | Task and sprint tracking | jira.company.com |
| **Documentation** | Confluence | Team wiki & runbooks | confluence.company.com |
| **Communication** | Slack | Team messaging | slack.com |
| **DNS** | Route 53 / Cloudflare | DNS management | AWS / Cloudflare console |
| **Security Scanning** | Trivy / Snyk | Vulnerability detection | CI pipeline |
| **Cost Management** | AWS Cost Explorer | Cloud cost tracking | AWS console |

---

## 20.2 Tool Access Levels

| Tool | Read | Write | Admin |
|---|---|---|---|
| AWS Console | All engineers | DevOps engineers | DevOps Lead |
| GitHub | All engineers | All engineers | DevOps Lead |
| Terraform Cloud | All engineers | DevOps engineers | DevOps Lead |
| Grafana | All engineers | DevOps / SRE | DevOps Lead |
| Vault | Services (via role) | DevSecOps | DevOps Lead |
| PagerDuty | All engineers | SRE / DevOps Lead | DevOps Lead |
| Jira | All teams | All teams | EM / DevOps Lead |
| Confluence | All teams | All teams | EM / DevOps Lead |

---

## 20.3 Access Request Process

1. Raise a Jira ticket tagged `[ACCESS]`
2. Specify: tool name, access level needed, business justification, duration (if temporary)
3. Assigned to DevOps Lead for approval
4. Access provisioned within SLA (see Section 19)
5. Access logged in the access audit register

---

## 20.4 Tool Onboarding Checklist (New Members)

- [ ] GitHub account added to org and relevant teams
- [ ] AWS / GCP access provisioned via IAM role
- [ ] Jira account created and added to DevOps board
- [ ] Confluence account created and space access granted
- [ ] Slack added to all required channels (see Section 19)
- [ ] PagerDuty account created and added to rotation schedule
- [ ] Grafana viewer access granted
- [ ] Vault access configured for required secrets
- [ ] kubectl configured for dev and staging clusters
- [ ] Local tools installed: `terraform`, `kubectl`, `helm`, `aws-cli`, `docker`

---

## 20.5 Tool Evaluation Process

When proposing a new tool:
1. Raise a Confluence RFC page (template in Section 21)
2. Include: problem statement, proposed tool, alternatives considered, cost, security implications
3. Present to team for discussion (Tech Share or async review)
4. Decision logged in Section 22 (Decision Log)
5. If approved: pilot in dev environment first, then roll out with documentation

---

## 20.6 Tool Deprecation Process

1. Announce deprecation in `#devops` with at least **30 days notice**
2. Migrate all dependencies to the replacement tool
3. Update all runbooks, pipelines, and documentation
4. Revoke all access and decommission
5. Log in Section 22 (Decision Log)

---

## 20.7 Related Pages

- → Section 6: Repo & Infrastructure Standards
- → Section 9: Secrets & Access Management
- → Section 21: Templates
