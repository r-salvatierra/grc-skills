# MARIO Table Templates & Field Definitions

Supporting reference for `mario-sop.prompt.md`. Read during Step 4.

---

## Management Table

| Field | Value |
|-------|-------|
| Process Name | |
| Version | 1.0 |
| Effective Date | DD/MM/YYYY |
| Process Owner | [Role title — e.g. Cloud Operations Lead] |
| Approver | [Role title — e.g. IT Manager] |
| Review Cadence | Annually |
| Scope | [Which teams, systems, or scenarios this applies to] |
| Related Documents | [Jira ticket link + any referenced policies, SOPs, or forms] |

**Field rules:**
- Process Name: action-oriented noun phrase ("IP Address Access Review", not "Access Review")
- Version: start at 1.0; Confluence history tracks subsequent changes
- Process Owner and Approver: always a role/title, never a person's name
- Scope: be specific — name the teams, platforms, and note any explicit exclusions
- Related Documents: always include the source Jira ticket as the first entry

---

## Activities Table

| # | Activity | Responsible Role | Inputs | Outputs | Notes |
|---|----------|-----------------|--------|---------|-------|
| 1 | | | | | |
| 2 | | | | | |

**Column rules:**

| Column | Rule |
|--------|------|
| # | Sequential. Use 3a / 3b for parallel branches (e.g. approved vs rejected paths) |
| Activity | Start with an action verb. Describe *what* happens, not *who* does it. E.g. "Submit access request via JSM portal" |
| Responsible Role | Job title or team name. Never an individual's name |
| Inputs | What must exist before this step can start: documents, decisions, system states, completed prior steps |
| Outputs | What this step produces: a ticket, a notification, an approved record, a completed check |
| Notes | Optional: time constraints, exception handling, escalation triggers, tool-specific instructions |

**Good vs weak activity labels:**
- ✅ "Review flagged IP addresses against approved allowlist"
- ❌ "Do the review"
- ✅ "Raise JSM escalation ticket with rejection reason and supporting evidence"
- ❌ "Escalate if needed"

Granularity target: granular enough for an unfamiliar team member to execute the step independently, but not so granular it describes individual UI clicks.

---

## Resources Table

| Resource | Type | Used In Step # | Description |
|----------|------|----------------|-------------|
| | System | | |
| | Template | | |
| | Document | | |

**Resource types:**

| Type | Examples |
|------|---------|
| System | Jira Service Management, Confluence, GitHub, Active Directory, Azure AD |
| Template | Access Request Form, Escalation email template, Rejection Notice |
| Document | IP Allowlist policy, RBAC matrix, Network access policy |
| Tool | Monitoring dashboard, spreadsheet, CLI tool |

Every named system or tool mentioned in any Activity row must appear here. Include a Confluence page link or URL in the Description if one exists.
