# 24. Learning Resources & Reference Library

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-05-29
> **Confluence Space:** `DEVOPS`
> **Audience:** All DevOps Members — Junior to Senior

---

## 24.1 How to Use This Section

This section is the **canonical reference list** for learning DevOps skills. Resources are curated for quality, depth, and relevance — not quantity. Each domain lists:

- 📖 **Official Docs** — always the source of truth
- 📚 **Books** — deep foundational knowledge
- 🎓 **Courses** — structured learning paths
- 🔗 **Practical References** — cheatsheets, guides, and community resources

> **Rule:** When in doubt, read the official documentation first. Blog posts and tutorials go stale; official docs do not.

---

## 24.2 Linux & Shell Fundamentals

> Foundation for everything. Non-negotiable for all DevOps engineers.

### 📖 Official Docs
- [Linux man pages online](https://man7.org/linux/man-pages/) — authoritative reference for every command
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html) — complete Bash language reference
- [The Linux Kernel documentation](https://www.kernel.org/doc/html/latest/) — for deep systems understanding

### 📚 Books
| Title | Author | Level | Focus |
|---|---|---|---|
| *The Linux Command Line* | William Shotts | Beginner | CLI, shell, scripting |
| *Linux Bible* | Christopher Negus | Beginner–Mid | Comprehensive Linux admin |
| *How Linux Works* | Brian Ward | Mid | Internals, boot, kernel |
| *The Art of Unix Programming* | Eric S. Raymond | Senior | Unix philosophy & design |

### 🎓 Courses
- [Linux Foundation — Introduction to Linux (LFS101)](https://training.linuxfoundation.org/training/introduction-to-linux/) — free, well-structured
- [Linux Survival](https://linuxsurvival.com/) — interactive beginner practice
- [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/) — learn Linux by solving challenges

### 🔗 Practical References
- [explainshell.com](https://explainshell.com/) — paste any command, get it explained piece by piece
- [tldr pages](https://tldr.sh/) — simplified man pages with practical examples
- [Bash Cheatsheet — devhints.io](https://devhints.io/bash)

---

## 24.3 Bash Scripting

### 📖 Official Docs
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html)
- [Advanced Bash-Scripting Guide](https://tldp.org/LDP/abs/html/) — comprehensive free book online

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Classic Shell Scripting* | Robbins & Beebe | Mid |
| *Shell Scripting: Expert Recipes for Linux, Bash and more* | Steve Parker | Mid–Senior |

### 🔗 Practical References
- [ShellCheck](https://www.shellcheck.net/) — online linter for shell scripts, catches common bugs
- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html) — industry standard style conventions
- [Bash Pitfalls](https://mywiki.wooledge.org/BashPitfalls) — common mistakes and how to avoid them
- [commandlinefu.com](https://www.commandlinefu.com/) — community-sourced one-liners

---

## 24.4 Git & Version Control

### 📖 Official Docs
- [Official Git Documentation](https://git-scm.com/doc)
- [Pro Git Book](https://git-scm.com/book/en/v2) — free, comprehensive, written by Git maintainers

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Pro Git* | Scott Chacon & Ben Straub | All levels — free online |
| *Git for Teams* | Emma Jane Hogbin Westby | Mid |

### 🎓 Courses
- [Learn Git Branching](https://learngitbranching.js.org/) — interactive visual playground, highly recommended
- [GitHub Skills](https://skills.github.com/) — official GitHub interactive labs
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials) — well-written conceptual guides

### 🔗 Practical References
- [Git Cheatsheet — GitHub](https://education.github.com/git-cheat-sheet-education.pdf)
- [Oh Shit, Git!](https://ohshitgit.com/) — how to recover from common mistakes
- [Conventional Commits](https://www.conventionalcommits.org/) — commit message standard used in most teams

---

## 24.5 Docker & Containerization

### 📖 Official Docs
- [Docker Official Documentation](https://docs.docker.com/) — Dockerfile reference, Compose, networking
- [Docker Hub](https://hub.docker.com/) — official base images
- [OCI Image Spec](https://github.com/opencontainers/image-spec) — understanding the container image standard

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Docker Deep Dive* | Nigel Poulton | Beginner |
| *Docker in Practice* | Miell & Hobday | Mid |
| *Container Security* | Liz Rice | Senior |

### 🎓 Courses
- [Play with Docker Classroom](https://training.play-with-docker.com/) — free browser-based Docker tutorials (labs.play-with-docker.com đã ngừng hoạt động)
- [Docker Getting Started Guide](https://docs.docker.com/get-started/) — official hands-on tutorial from Docker
- [A Cloud Guru — Docker Deep Dive](https://acloudguru.com/) — structured video course

### 🔗 Practical References
- [Dockerfile Best Practices — Docker](https://docs.docker.com/build/building/best-practices/)
- [Dive](https://github.com/wagoodman/dive) — tool to explore Docker image layers and reduce size
- [hadolint](https://hadolint.github.io/hadolint/) — Dockerfile linter
- [Docker Compose file reference](https://docs.docker.com/reference/compose-file/)

---

## 24.6 Kubernetes

### 📖 Official Docs
- [Kubernetes Official Documentation](https://kubernetes.io/docs/) — concepts, tasks, API reference
- [kubectl reference](https://kubernetes.io/docs/reference/kubectl/) — every command explained
- [Kubernetes Blog](https://kubernetes.io/blog/) — official announcements and deep dives
- [CNCF Glossary](https://glossary.cncf.io/) — cloud native terminology

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Kubernetes in Action* | Marko Lukša | Mid — best comprehensive book |
| *The Kubernetes Book* | Nigel Poulton | Beginner |
| *Production Kubernetes* | Josh Rosso et al. | Senior |
| *Kubernetes Patterns* | Bilgin Ibryam & Roland Huß | Senior |
| *Managing Kubernetes* | Brendan Burns & Craig Tracey | Senior |

### 🎓 Courses & Certifications
- [Killer.sh](https://killer.sh/) — CKA/CKAD/CKS exam simulator, closest to real exam
- [KodeKloud](https://kodekloud.com/) — hands-on labs, highly rated for CKA prep
- [Linux Foundation CKA](https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/) — official certification
- [Linux Foundation CKAD](https://training.linuxfoundation.org/certification/certified-kubernetes-application-developer-ckad/) — developer-focused cert

### 🔗 Practical References
- [kubectl Quick Reference](https://kubernetes.io/docs/reference/kubectl/quick-reference/)
- [k9s](https://k9scli.io/) — terminal UI for Kubernetes clusters
- [Helm Docs](https://helm.sh/docs/) — Kubernetes package manager
- [Kustomize Docs](https://kustomize.io/) — template-free Kubernetes config management
- [Awesome Kubernetes](https://github.com/ramitsurana/awesome-kubernetes) — curated resource list

---

## 24.7 Terraform & Infrastructure as Code

### 📖 Official Docs
- [Terraform Documentation](https://developer.hashicorp.com/terraform/docs) — language, CLI, providers
- [Terraform Registry](https://registry.terraform.io/) — providers, modules
- [AWS Provider Docs](https://registry.terraform.io/providers/hashicorp/aws/latest/docs) — every AWS resource documented
- [Terraform Language Reference](https://developer.hashicorp.com/terraform/language) — HCL syntax reference

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Terraform: Up & Running* | Yevgeniy Brikman | All levels — **must-read** |
| *Infrastructure as Code* | Kief Morris | Mid–Senior — tool-agnostic concepts |

### 🎓 Courses & Certifications
- [HashiCorp Learn](https://developer.hashicorp.com/terraform/tutorials) — free official tutorials with hands-on labs
- [HashiCorp Terraform Associate Certification](https://www.hashicorp.com/certification/terraform-associate)
- [KodeKloud Terraform](https://kodekloud.com/courses/terraform/) — practical labs

### 🔗 Practical References
- [terraform-best-practices.com](https://www.terraform-best-practices.com/) — community best practices guide
- [tflint](https://github.com/terraform-linters/tflint) — Terraform linter
- [Trivy — IaC Scanning](https://trivy.dev/docs/latest/scanner/misconfiguration/) — IaC security scanning (tfsec đã được merge vào Trivy)
- [Checkov](https://www.checkov.io/) — policy-as-code for Terraform
- [Infracost](https://www.infracost.io/) — cost estimation for Terraform changes
- [Terragrunt](https://terragrunt.gruntwork.io/) — DRY wrapper for Terraform at scale

---

## 24.8 AWS (Amazon Web Services)

### 📖 Official Docs
- [AWS Documentation](https://docs.aws.amazon.com/) — authoritative reference for all services
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/) — 6 pillars: Operational Excellence, Security, Reliability, Performance, Cost, Sustainability
- [AWS Architecture Center](https://aws.amazon.com/architecture/) — reference architectures and patterns
- [AWS CLI Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html)

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *AWS Certified Solutions Architect Study Guide* | Piper & Clinton | Mid |
| *Serverless Architectures on AWS* | Poccia | Mid |
| *AWS Security* | Dylan Shields | Senior |

### 🎓 Courses & Certifications
| Certification | Level | Notes |
|---|---|---|
| [AWS Cloud Practitioner](https://aws.amazon.com/certification/certified-cloud-practitioner/) | Foundational | Good for non-technical roles |
| [AWS Solutions Architect Associate](https://aws.amazon.com/certification/certified-solutions-architect-associate/) | Associate | **Recommended first cert** for DevOps |
| [AWS DevOps Engineer Professional](https://aws.amazon.com/certification/certified-devops-engineer-professional/) | Professional | Core cert for the team |
| [AWS SysOps Administrator](https://aws.amazon.com/certification/certified-sysops-admin-associate/) | Associate | Operations focus |

- [A Cloud Guru](https://acloudguru.com/) — strong AWS course catalog
- [Tutorials Dojo](https://tutorialsdojo.com/) — best AWS practice exams, very close to real exam
- [AWS Skill Builder](https://skillbuilder.aws/) — official AWS learning platform, some free content

### 🔗 Practical References
- [AWS Cheatsheet — Tutorials Dojo](https://tutorialsdojo.com/aws-cheat-sheets/)
- [AWS Icons](https://aws.amazon.com/architecture/icons/) — official architecture diagram icons
- [CloudFormation / CDK Docs](https://docs.aws.amazon.com/cloudformation/)
- [AWS Samples GitHub](https://github.com/aws-samples) — official reference implementations

---

## 24.9 CI/CD & GitOps

### 📖 Official Docs
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/)
- [ArgoCD Documentation](https://argo-cd.readthedocs.io/)
- [Flux Documentation](https://fluxcd.io/docs/)
- [Tekton Documentation](https://tekton.dev/docs/)

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Continuous Delivery* | Humble & Farley | Mid–Senior — foundational CD book |
| *GitOps and Kubernetes* | Yuen, Castellanos, Dominguez | Mid |

### 🔗 Practical References
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)
- [ArgoCD Best Practices](https://argo-cd.readthedocs.io/en/stable/operator-manual/best_practices/)
- [OpenGitOps Principles](https://opengitops.dev/) — vendor-neutral GitOps specification

---

## 24.10 Monitoring, Observability & Alerting

### 📖 Official Docs
- [Prometheus Documentation](https://prometheus.io/docs/)
- [Grafana Documentation](https://grafana.com/docs/)
- [OpenTelemetry Documentation](https://opentelemetry.io/docs/) — tracing, metrics, logs
- [Datadog Documentation](https://docs.datadoghq.com/)
- [Elastic (ELK) Documentation](https://www.elastic.co/guide/)
- [Loki Documentation](https://grafana.com/docs/loki/)

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Prometheus: Up & Running* | Brazil & Sloane | Mid |
| *Observability Engineering* | Majors, Fong-Jones, Miranda | Senior — **must-read for SREs** |
| *Distributed Systems Observability* | Cindy Sridharan | Mid–Senior — free online |

### 🔗 Practical References
- [PromQL Cheatsheet](https://promlabs.com/promql-cheat-sheet/)
- [Grafana Dashboard Examples](https://grafana.com/grafana/dashboards/)
- [Awesome Prometheus](https://github.com/warpnet/awesome-prometheus)
- [SLO Generator — Google](https://github.com/google/slo-generator)

---

## 24.11 Site Reliability Engineering (SRE)

### 📖 Official Docs / Free Books
- [Google SRE Book](https://sre.google/sre-book/table-of-contents/) — **the** foundational SRE text, free online
- [Google SRE Workbook](https://sre.google/workbook/table-of-contents/) — practical implementation guide, free online
- [Google Building Secure & Reliable Systems](https://sre.google/books/building-secure-reliable-systems/) — free online

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Site Reliability Engineering* | Beyer, Jones, Petoff, Murphy (Google) | Mid–Senior |
| *The Site Reliability Workbook* | Beyer et al. (Google) | Mid–Senior |
| *Seeking SRE* | Blank-Edelman | Senior — diverse perspectives |

---

## 24.12 DevOps Culture & Practices

### 📚 Books — Must-Read List
| Title | Author | Why Read It |
|---|---|---|
| *The Phoenix Project* | Kim, Behr, Spafford | DevOps culture through narrative — start here |
| *The Unicorn Project* | Gene Kim | Developer perspective on DevOps transformation |
| *The DevOps Handbook* | Kim, Humble, Debois, Willis | Comprehensive DevOps practices framework |
| *Accelerate* | Forsgren, Humble, Kim | Science behind DevOps — DORA metrics origin |
| *Team Topologies* | Skelton & Pais | How to structure teams for fast flow |
| *An Elegant Puzzle* | Will Larson | Engineering management in fast-moving orgs |

### 🔗 Communities & Blogs
- [DevOps Vietnam Community](https://www.facebook.com/groups/DevOpsVietnam/) — active Vietnamese DevOps community
- [CNCF Blog](https://www.cncf.io/blog/) — cloud native news and deep dives
- [The New Stack](https://thenewstack.io/) — cloud native and DevOps articles
- [Martin Fowler's Blog](https://martinfowler.com/) — architecture and software delivery patterns
- [Brendan Gregg's Blog](https://www.brendangregg.com/) — Linux performance and systems deep dives

---

## 24.13 Security & DevSecOps

### 📖 Official Docs
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks/) — hardening guides for Linux, Kubernetes, Docker, AWS
- [Sigstore Documentation](https://docs.sigstore.dev/)
- [SLSA Framework](https://slsa.dev/)

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Container Security* | Liz Rice | Mid–Senior |
| *Hacking Kubernetes* | Martin & Hausenblas | Senior |
| *Cloud Native Security* | Garrison & Kumar | Senior |

### 🎓 Courses
- [Certified Kubernetes Security Specialist (CKS)](https://training.linuxfoundation.org/certification/certified-kubernetes-security-specialist/) — advanced security cert
- [SANS DevSecOps courses](https://www.sans.org/) — professional security training

---

## 24.14 Networking Fundamentals

### 📖 Official Docs
- [AWS Networking Documentation](https://docs.aws.amazon.com/vpc/)
- [Cloudflare Learning Center](https://www.cloudflare.com/learning/) — DNS, TLS, CDN, networking concepts explained simply
- [Istio Documentation](https://istio.io/latest/docs/) — service mesh

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Computer Networks* | Tanenbaum & Wetherall | Beginner–Mid — fundamentals |
| *TCP/IP Illustrated* | Stevens | Senior — deep protocol understanding |

### 🔗 Practical References
- [Subnet Calculator](https://www.subnet-calculator.com/)
- [DNS Lookup Tools — MXToolbox](https://mxtoolbox.com/)
- [What happens when you type a URL](https://github.com/alex/what-happens-when) — famous deep dive

---

## 24.15 Python for DevOps

### 📖 Official Docs
- [Python Official Documentation](https://docs.python.org/3/)
- [boto3 Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) — AWS SDK for Python

### 📚 Books
| Title | Author | Level |
|---|---|---|
| *Automate the Boring Stuff with Python* | Al Sweigart | Beginner — free online |
| *Python for DevOps* | Gift, Behrman, Deza, Gheorghiu | Mid — DevOps-specific use cases |
| *Fluent Python* | Luciano Ramalho | Senior — deep Python internals |

### 🔗 Practical References
- [Real Python](https://realpython.com/) — high-quality Python tutorials
- [Python DevOps Cookbook](https://github.com/noahgift/python-devops-cookbook) — examples repo

---

## 24.16 Learning Path by Role & Level

### 🟢 Junior DevOps Engineer — First 6 Months
```
Month 1–2: Linux CLI → Bash scripting → Git
Month 3–4: Docker → AWS fundamentals (Cloud Practitioner)
Month 5–6: Kubernetes basics → Terraform basics → CI/CD concepts
Certification target: AWS Solutions Architect Associate
```

### 🟡 Mid-Level DevOps Engineer — Year 1–2
```
Quarter 1: Kubernetes deep dive → CKA certification
Quarter 2: Terraform advanced (modules, state management, workspaces)
Quarter 3: Observability (Prometheus, Grafana, OpenTelemetry)
Quarter 4: Security practices → AWS DevOps Professional cert
```

### 🔴 Senior DevOps Engineer / SRE
```
- SRE Book + Workbook (Google)
- Observability Engineering book
- Production Kubernetes book
- Kubernetes Security (CKS certification)
- FinOps practices (Section 23)
- Team Topologies + Accelerate (leadership & org design)
```

---

## 24.17 Related Pages

- → Section 3: Skills & Learning Roadmap
- → Section 4: Onboarding & 30/60/90 Plan
- → Section 22: Glossary & References
- → Section 23: Cost Optimization & FinOps
