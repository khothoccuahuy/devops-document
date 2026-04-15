# 7. CI/CD Standards & Pipelines

> **Document Status:** 🟡 Draft
> **Owner:** Senior DevOps Engineer
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 7.1 Overview

All services must have an automated CI/CD pipeline. Our standard toolchain is:

| Stage | Tool |
|---|---|
| Source Control | GitHub / GitLab |
| CI | GitHub Actions / GitLab CI |
| Container Registry | AWS ECR / Docker Hub |
| CD | ArgoCD / GitHub Actions |
| IaC Deployment | Terraform Cloud / GitHub Actions |

---

## 7.2 CI Pipeline Standards

Every CI pipeline must include these stages in order:

```
Trigger (Push / PR)
  │
  ├── 1. Lint & Format Check
  ├── 2. Unit Tests
  ├── 3. Security Scan (SAST / Dependency Check)
  ├── 4. Build (Docker image or artifact)
  ├── 5. Integration Tests (if applicable)
  └── 6. Push artifact to registry (on merge to main)
```

---

## 7.3 CD Pipeline Standards

```
Merge to main
  │
  ├── Deploy to DEV (automatic)
  │     └── Smoke tests
  ├── Deploy to STAGING (automatic or manual gate)
  │     └── Integration / regression tests
  └── Deploy to PRODUCTION (manual approval required)
        └── Post-deploy health check
        └── Notify #deployments Slack channel
```

---

## 7.4 Pipeline Rules

- All pipelines must be defined **as code** (YAML in the repository)
- Secrets must never be hardcoded — use CI secret variables or Vault
- Failed pipelines must **block** deployments — never bypass without approval
- Pipeline duration targets: CI < 10 min, CD to staging < 15 min
- All pipeline changes must go through PR review

---

## 7.5 Rollback Strategy

- Every deployment must support **one-click rollback**
- For Kubernetes: use `helm rollback` or ArgoCD rollback
- For Lambda/serverless: use versioning and alias switching
- Rollback must be documented in the deployment runbook (Section 13)

---

## 7.6 Related Pages

- → Section 6: Repo & Infrastructure Standards
- → Section 8: Environments & Release Process
- → Section 13: Runbooks & Playbooks
