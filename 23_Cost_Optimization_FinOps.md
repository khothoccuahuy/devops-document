# 23. Cost Optimization & FinOps

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Lead
> **Last Updated:** 2026-05-29
> **Confluence Space:** `DEVOPS`
> **Audience:** DevOps Engineers, SREs, Engineering Managers

---

## 23.1 FinOps Principles

Cloud cost is a **shared engineering responsibility** — not just Finance or Management.

- **Visibility first:** You cannot optimize what you cannot see
- **Everyone owns costs:** Engineers who provision resources are accountable for their cost
- **Optimize continuously:** Cost review is part of regular engineering work, not a one-off
- **Balance cost vs reliability:** Never sacrifice SLOs for cost savings
- **Tag everything:** Untagged resources cannot be attributed or optimized

---

## 23.2 Tagging Strategy

All cloud resources **must** be tagged. Without tags, cost attribution is impossible.

### Required Tags

| Tag Key | Values | Purpose |
|---|---|---|
| `env` | `dev`, `staging`, `prod` | Environment attribution |
| `team` | `devops`, `backend`, `frontend`, etc. | Team cost allocation |
| `project` | e.g. `payment-service` | Project attribution |
| `owner` | e.g. `john.doe` | Individual accountability |
| `cost-center` | e.g. `CC-1001` | Finance reporting |
| `managed-by` | `terraform`, `manual`, `helm` | IaC compliance tracking |

### Enforce Tags via Policy

```hcl
# Terraform — enforce required tags
variable "required_tags" {
  type = map(string)
  default = {
    env        = ""
    team       = ""
    project    = ""
    owner      = ""
    cost-center = ""
  }
}

# AWS — use Service Control Policy (SCP) to block untagged resource creation
# GCP — use Organization Policy constraints/compute.requireOsLogin
```

> ⚠️ Run **monthly tag compliance reports** via AWS Config or AWS Cost Explorer Tag Editor. Resources untagged for >7 days trigger a P4 alert.

---

## 23.3 Cost Visibility & Tooling

| Tool | Purpose |
|---|---|
| AWS Cost Explorer | Breakdown by service, tag, account, region |
| AWS Cost & Usage Report (CUR) | Detailed billing data for custom analysis |
| AWS Budgets | Alerts when spend exceeds threshold |
| Infracost | Estimate Terraform cost changes in PRs |
| Kubecost | Kubernetes namespace/pod cost breakdown |
| CloudHealth / Apptio | Multi-cloud cost management (if multi-cloud) |

### Infracost in CI — Cost Visibility on Every PR

```yaml
# .github/workflows/infracost.yml
- name: Setup Infracost
  uses: infracost/actions/setup@v2

- name: Generate Infracost diff
  run: |
    infracost diff --path=./infra \
      --format=json \
      --out-file=/tmp/infracost.json

- name: Post Infracost comment
  uses: infracost/actions/comment@v2
  with:
    path: /tmp/infracost.json
    behavior: update  # Update existing PR comment
```

This adds a cost estimate diff to every PR touching infrastructure — engineers see cost impact before merge.

---

## 23.4 Budget Alerts

Set budget alerts at **multiple thresholds** to avoid bill shock.

### AWS Budget Setup

| Budget | Threshold | Alert Channel |
|---|---|---|
| Monthly total spend | 80% of budget | Email + Slack `#devops` |
| Monthly total spend | 100% of budget | Email + Slack `#devops` + DevOps Lead |
| Monthly total spend | 120% of budget | Email + PagerDuty (P2) |
| Per-service anomaly | 3x daily average | Slack `#devops` |

```hcl
# Terraform — AWS Budget with alerts
resource "aws_budgets_budget" "monthly" {
  name         = "monthly-total-budget"
  budget_type  = "COST"
  limit_amount = "1000"
  limit_unit   = "USD"
  time_unit    = "MONTHLY"

  notification {
    comparison_operator        = "GREATER_THAN"
    threshold                  = 80
    threshold_type             = "PERCENTAGE"
    notification_type          = "ACTUAL"
    subscriber_email_addresses = ["devops-lead@company.com"]
  }
}
```

> Enable **AWS Cost Anomaly Detection** for automated anomaly alerts — it uses ML to detect unusual spend patterns.

---

## 23.5 Rightsizing & Waste Elimination

### Compute (EC2 / EKS Nodes)

- Use **AWS Compute Optimizer** to get rightsizing recommendations
- Review underutilized instances (< 20% avg CPU over 14 days) monthly
- Move long-running stable workloads to **Reserved Instances** or **Savings Plans**

| Purchase Option | Savings vs On-Demand | Best For |
|---|---|---|
| On-Demand | 0% | Dev/test, unpredictable workloads |
| Savings Plans (1yr) | ~30% | Stable production compute |
| Savings Plans (3yr) | ~50% | Very stable, long-term workloads |
| Spot Instances | ~70–90% | Batch jobs, CI runners, non-critical |

### Kubernetes Cost Optimization

```yaml
# Always set resource requests AND limits
resources:
  requests:
    cpu: "100m"
    memory: "128Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"
```

- No resource requests = pod may land on overloaded node, driving node scale-up
- Use **Vertical Pod Autoscaler (VPA)** in recommendation mode to right-size requests
- Use **Karpenter** (AWS) for intelligent node provisioning — consolidates pods, uses Spot where safe
- Enable **cluster autoscaler** with scale-down delay tuned to workload

### Storage

- Review unattached EBS volumes monthly — delete or snapshot
- Enable **S3 Intelligent-Tiering** for objects with unpredictable access patterns
- Set **S3 lifecycle policies** to move old objects to Glacier / Deep Archive

```hcl
resource "aws_s3_bucket_lifecycle_configuration" "logs" {
  bucket = aws_s3_bucket.logs.id

  rule {
    id     = "log-retention"
    status = "Enabled"

    transition {
      days          = 30
      storage_class = "STANDARD_IA"
    }
    transition {
      days          = 90
      storage_class = "GLACIER"
    }
    expiration {
      days = 365
    }
  }
}
```

### Common Waste Sources

| Waste Type | Detection | Action |
|---|---|---|
| Idle EC2 instances | Cost Explorer + CloudWatch | Stop or terminate |
| Unattached EBS volumes | AWS Trusted Advisor | Snapshot + delete |
| Old snapshots | Cost Explorer | Delete snapshots > retention policy |
| Oversized RDS instances | Performance Insights | Downsize to right-size |
| NAT Gateway data transfer | Cost Explorer | Evaluate VPC endpoints for S3/DynamoDB |
| Unused Elastic IPs | AWS Console | Release unattached EIPs |
| Dev/staging running 24/7 | Scheduler | Auto-stop outside business hours |

---

## 23.6 Dev/Staging Cost Controls

Non-production environments often account for 30–50% of cloud spend unnecessarily.

**Auto-shutdown for dev/staging:**

```python
# Lambda function — stop non-prod instances outside business hours
import boto3

def lambda_handler(event, context):
    ec2 = boto3.client('ec2', region_name='ap-southeast-1')
    
    # Stop instances tagged env=dev or env=staging
    filters = [
        {'Name': 'tag:env', 'Values': ['dev', 'staging']},
        {'Name': 'instance-state-name', 'Values': ['running']}
    ]
    
    instances = ec2.describe_instances(Filters=filters)
    instance_ids = [
        i['InstanceId']
        for r in instances['Reservations']
        for i in r['Instances']
    ]
    
    if instance_ids:
        ec2.stop_instances(InstanceIds=instance_ids)
        print(f"Stopped {len(instance_ids)} dev/staging instances")
```

Schedule: Stop at 20:00 ICT, start at 08:00 ICT weekdays. Off all weekend.  
Estimated savings: **~65% reduction** in dev/staging compute costs.

---

## 23.7 Cost Review Process

### Weekly (DevOps team)
- Review AWS Cost Explorer for anomalies vs previous week
- Check if any budget alert was triggered
- Review Kubecost for namespace-level spend trends

### Monthly (DevOps + Engineering Manager)
- Review total cloud spend vs budget
- Identify top 5 cost drivers
- Review rightsizing recommendations from Compute Optimizer
- Check for waste (idle resources, unattached volumes, old snapshots)
- Update cost forecast for next month

### Quarterly (Engineering Leadership)
- Review Reserved Instance / Savings Plans coverage
- Evaluate architecture changes for cost efficiency (e.g. move batch to Spot, move storage to cheaper tier)
- Assess FinOps maturity and set cost reduction targets for next quarter

---

## 23.8 Cost KPIs

| Metric | Target | Measured By |
|---|---|---|
| Cloud spend vs budget | ≤ 100% of budget | AWS Budgets |
| Cost per deployment | Trending down QoQ | Custom metric |
| Savings Plans coverage | > 70% of eligible compute | AWS Cost Explorer |
| Untagged resources | 0% | AWS Config |
| Dev/staging cost as % of total | < 20% | Cost Explorer tags |
| Waste elimination (monthly) | Identify & act on top 3 items | Monthly review |

---

## 23.9 Related Pages

- → Section 6: Repo & Infrastructure Standards (tagging in IaC)
- → Section 5: Project Initiation Checklist (cost estimate required)
- → Section 18: Metrics & KPIs
- → Section 15: Security & Compliance
