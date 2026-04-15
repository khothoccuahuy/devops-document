# 21. Templates

> **Document Status:** 🟡 Draft
> **Owner:** DevOps Team
> **Last Updated:** 2026-04-05
> **Confluence Space:** `DEVOPS`

---

## 21.1 Pull Request Template

> Save as `.github/pull_request_template.md` in each repository.

```markdown
## Summary
[What does this PR do? Why is it needed?]

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Infrastructure change
- [ ] Configuration update
- [ ] Documentation update
- [ ] Security fix
- [ ] Refactor / cleanup

## Jira Ticket
[PROJ-XXX](https://jira.company.com/browse/PROJ-XXX)

## Changes Made
-
-
-

## Testing Done
- [ ] Tested in dev environment
- [ ] Tested in staging environment
- [ ] Existing tests pass
- [ ] New tests added (if applicable)

## Rollback Plan
[How to revert this change if it causes issues]

## Screenshots / Logs (if applicable)
[Attach evidence of testing]

## Checklist
- [ ] Code reviewed by at least 1 peer
- [ ] No secrets or credentials hardcoded
- [ ] Documentation updated (README, runbook, Confluence)
- [ ] Alerts / dashboards updated (if applicable)
- [ ] Runbook updated (if applicable)
```

---

## 21.2 RFC (Request for Comments) Template

> Use for proposing new tools, processes, or architectural changes.

```markdown
## RFC: [Title]

**Author:** [Name]
**Date:** YYYY-MM-DD
**Status:** Draft | Under Review | Approved | Rejected
**Jira Ticket:** [PROJ-XXX]

---

## Problem Statement
[What problem are we solving? Why does it matter?]

## Proposed Solution
[Describe your proposed approach in detail]

## Alternatives Considered

### Option A — [Name]
- **Pros:** ...
- **Cons:** ...

### Option B — [Name]
- **Pros:** ...
- **Cons:** ...

## Impact & Risks
| Area | Impact | Mitigation |
|------|--------|------------|
| Cost | [High/Med/Low] | |
| Security | [High/Med/Low] | |
| Reliability | [High/Med/Low] | |
| Team effort | [High/Med/Low] | |

## Implementation Plan
1. Step 1
2. Step 2
3. Step 3

## Success Criteria
[How do we know this worked? What metrics will we track?]

## Decision & Outcome
[Filled in after team discussion]

**Decision made by:** [Name(s)]
**Date decided:** YYYY-MM-DD
```

---

## 21.3 Architecture Decision Record (ADR) Template

> Use to document significant technical decisions. Store in `docs/adr/` in the repository.

```markdown
## ADR-[NUMBER]: [Title]

**Date:** YYYY-MM-DD
**Status:** Proposed | Accepted | Deprecated | Superseded by ADR-[X]
**Author:** [Name]

---

## Context
[What is the situation that requires a decision?
What constraints or requirements exist?]

## Decision
[What have we decided to do?
Be specific and clear.]

## Consequences

### Positive
-
-

### Negative
-
-

### Risks
-
-

## Alternatives Rejected
1. [Option] — rejected because [reason]
2. [Option] — rejected because [reason]
```

---

## 21.4 Runbook Template

> See **Section 13.2** for the full runbook template.

---

## 21.5 Postmortem Template

> See **Section 12.4** for the full postmortem template.

---

## 21.6 On-Call Handoff Template

> Used every Monday during the weekly on-call rotation handoff.

```markdown
## On-Call Handoff — Week of [YYYY-MM-DD]

**Outgoing On-Call:** [Name]
**Incoming On-Call:** [Name]

---

## Open Incidents / Issues
| Issue | Status | Next Action | Owner |
|-------|--------|-------------|-------|
| | | | |

## Alerts to Watch
- [Alert name] — context and what to look for

## Deployments This Week
- [Service] deployed on [date] — any known risks?

## Systems Under Observation
- [System] — reason for monitoring

## Notes for Incoming On-Call
[Anything else the incoming engineer should know]
```

---

## 21.7 Access Request Template

> Use when raising a Jira `[ACCESS]` ticket.

```markdown
## Access Request

**Requester:** [Name]
**Date:** YYYY-MM-DD
**Tool / System:** [Tool name]
**Access Level:** Read | Write | Admin
**Duration:** Permanent | Temporary (until YYYY-MM-DD)

## Business Justification
[Why do you need this access? What will you use it for?]

## Approved By
[DevOps Lead name — to be filled in on approval]
```

---

## 21.8 Related Pages

- → Section 6: Repo & Infrastructure Standards
- → Section 12: Incident Response & Postmortem
- → Section 13: Runbooks & Playbooks
- → Section 20: Tools & Integrations
