# 6. Repo & Infrastructure Standards

> **Document Status:** 🟡 Draft
> **Owner:** Senior DevOps Engineer
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 6.1 Repository Structure

All repositories must follow this standard structure:

```
repo-name/
├── .github/                  # GitHub Actions workflows
│   └── workflows/
├── infra/                    # Terraform / IaC code
│   ├── modules/
│   └── environments/
│       ├── dev/
│       ├── staging/
│       └── prod/
├── src/                      # Application source (if applicable)
├── docs/                     # Architecture docs, ADRs
├── scripts/                  # Utility scripts
├── .gitignore
├── .pre-commit-config.yaml
├── Makefile                  # Common commands
└── README.md
```

---

## 6.2 Naming Conventions

| Resource | Format | Example |
|---|---|---|
| Repository | `team-service-type` | `devops-api-infra` |
| Branch | `type/short-description` | `feat/add-rds-module` |
| Terraform module | `terraform-provider-resource` | `terraform-aws-rds` |
| AWS resources | `env-team-resource-name` | `prod-devops-eks-cluster` |
| Docker image | `org/service:env-version` | `myorg/api:prod-1.2.3` |
| Kubernetes namespace | `env-team` | `prod-backend` |

---

## 6.3 Branch Strategy

We follow **GitHub Flow** for most repositories:

```
main (protected)
 └── feat/your-feature       ← develop here
 └── fix/your-bugfix
 └── chore/your-task
```

- `main` is always deployable
- All changes go through Pull Requests — no direct pushes to `main`
- PRs require at least **1 approval** from a peer reviewer
- CI must pass before merge

---

## 6.4 Infrastructure as Code Standards

- All infrastructure must be managed via **Terraform** (or Pulumi where agreed)
- No manual changes to cloud resources without a corresponding IaC change
- State files stored in remote backend (S3 + DynamoDB for AWS)
- Use **modules** for reusable components
- Always run `terraform plan` before `terraform apply`
- Tag all resources with: `env`, `team`, `owner`, `project`, `cost-center`

---

## 6.5 Code Review Standards

- All PRs must have a clear description, linked Jira ticket, and testing notes
- Reviewer checks: correctness, security, cost impact, documentation
- Large PRs (500+ lines) should be broken into smaller ones
- Use PR templates (see Section 21: Templates)

---

## 6.6 Related Pages

- → Section 5: Project Initiation Checklist
- → Section 7: CI/CD Standards & Pipelines
- → Section 21: Templates
