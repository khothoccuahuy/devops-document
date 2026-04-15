# 15. Security & Compliance

> **Document Status:** 🟡 Draft
> **Owner:** DevSecOps Engineer
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 15.1 Security Principles

- Security is **everyone's responsibility**, not just the security engineer's
- Follow the **principle of least privilege** for all access
- **Shift left:** catch vulnerabilities in development, not production
- All changes that touch security must have **DevSecOps review**

---

## 15.2 Security Practices in CI/CD

| Practice | Tool | Stage |
|---|---|---|
| Static code analysis (SAST) | SonarQube / Semgrep | CI — on every PR |
| Dependency vulnerability scan | Snyk / Dependabot | CI — on every PR |
| Container image scan | Trivy / Grype | CI — on build |
| Dynamic analysis (DAST) | OWASP ZAP | Staging environment |
| Secret detection | GitLeaks / TruffleHog | Pre-commit + CI |
| IaC security scan | Checkov / tfsec | CI — on IaC changes |

---

## 15.3 Compliance Requirements

| Standard | Applicability | Owner | Review Frequency |
|---|---|---|---|
| SOC 2 Type II | Cloud infrastructure | DevSecOps | Annual |
| ISO 27001 | Information security | DevSecOps + IT | Annual |
| GDPR | User data handling | DevSecOps + Legal | Ongoing |
| Internal security policy | All systems | DevOps Lead | Quarterly |

---

## 15.4 Security Audit Schedule

- **Quarterly:** Internal vulnerability assessment, access review
- **Bi-annual:** Penetration testing (external vendor)
- **Annual:** Full compliance audit

---

## 15.5 Vulnerability Management

1. Vulnerabilities discovered via scans are logged in Jira tagged `[SEC]`
2. Severity follows CVSS score:
   - **Critical** → fix within 24 hours
   - **High** → fix within 7 days
   - **Medium** → fix within 30 days
   - **Low** → fix within 90 days
3. Critical vulnerabilities escalate immediately to DevSecOps + DevOps Lead
4. All fixes must be verified by re-scan before closing

---

## 15.6 Security Training

- All DevOps engineers complete **security awareness training** annually
- DevSecOps engineer attends at least 1 security conference or training per year
- New joiners complete security onboarding in first 30 days (see Section 4)

---

## 15.7 Related Pages

- → Section 9: Secrets & Access Management
- → Section 7: CI/CD Standards & Pipelines
- → Section 17: Change Management & Approvals
