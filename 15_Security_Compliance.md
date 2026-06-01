# 15. Security & Compliance

> **Document Status:** 🟡 Draft
> **Owner:** DevSecOps Engineer
> **Last Updated:** 2026-05-29
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

## 15.7 Software Supply Chain Security

> Supply chain attacks (e.g. SolarWinds, Log4Shell, XZ Utils) have made it critical to verify the integrity of every artifact in the build pipeline.

### Software Bill of Materials (SBOM)

An SBOM is a machine-readable inventory of all components, libraries, and dependencies in a software artifact.

**Why it matters:** Know exactly what's in your container images and applications — enables rapid response when a new CVE drops.

**Generate SBOM in CI pipeline:**

```yaml
# GitHub Actions — generate SBOM with Syft
- name: Generate SBOM
  uses: anchore/sbom-action@v0
  with:
    image: ${{ env.IMAGE_NAME }}:${{ env.IMAGE_TAG }}
    format: spdx-json
    output-file: sbom.spdx.json

- name: Upload SBOM as artifact
  uses: actions/upload-artifact@v4
  with:
    name: sbom
    path: sbom.spdx.json
```

**SBOM formats:**
- **SPDX** (ISO standard) — preferred for compliance
- **CycloneDX** — preferred for security tooling (Dependency-Track, etc.)

---

### Container Image Signing (Cosign / Sigstore)

Sign container images after build to ensure what's deployed is exactly what was built and scanned — not tampered with.

```yaml
# Sign image after push to ECR (keyless, using OIDC)
- name: Sign image with Cosign
  uses: sigstore/cosign-installer@v3

- name: Sign the container image
  env:
    COSIGN_EXPERIMENTAL: "true"  # Keyless signing
  run: |
    cosign sign --yes ${{ env.IMAGE_URI }}@${{ steps.build.outputs.digest }}
```

**Verify signature before deployment:**

```bash
cosign verify \
  --certificate-identity-regexp="https://github.com/your-org/your-repo" \
  --certificate-oidc-issuer="https://token.actions.githubusercontent.com" \
  $IMAGE_URI
```

> Integrate verification into ArgoCD / admission controller to **block unsigned images** from reaching production.

---

### SLSA Framework (Supply-chain Levels for Software Artifacts)

SLSA (pronounced "salsa") is a security framework for supply chain integrity. Adopt incrementally:

| Level | Requirements | What It Prevents |
|---|---|---|
| **SLSA 1** | Build process documented, provenance generated | Accidental mistakes |
| **SLSA 2** | Hosted build service, signed provenance | Tampering after build |
| **SLSA 3** | Hardened build environment, isolated builds | Compromised build system |
| **SLSA 4** | Two-party review, hermetic builds | Insider threats |

**Recommended target:** SLSA 2 for all production images (achievable with GitHub Actions + Cosign).

**Generate SLSA provenance:**

```yaml
- name: Generate SLSA provenance
  uses: slsa-framework/slsa-github-generator/.github/workflows/generator_container_slsa3.yml@v1
  with:
    image: ${{ env.IMAGE_NAME }}
    digest: ${{ steps.build.outputs.digest }}
```

---

### Supply Chain Security Checklist

```
CI Pipeline:
  ✅ SBOM generated on every build
  ✅ Container image scanned (Trivy/Grype) before push
  ✅ Image signed with Cosign after push
  ✅ Dependencies pinned to exact versions (not ranges)
  ✅ base images pinned by digest, not tag (e.g. ubuntu@sha256:...)

Registry:
  ✅ Only signed images allowed in production (admission policy)
  ✅ Images rescanned periodically for new CVEs

Third-party Actions / Orbs:
  ✅ Pin GitHub Actions to commit SHA, not tag
  ✅ Review and audit new Actions before adopting
```

---

## 15.8 Related Pages

- → Section 9: Secrets & Access Management
- → Section 7: CI/CD Standards & Pipelines
- → Section 17: Change Management & Approvals
- → Section 23: Cost Optimization & FinOps
