---
mode: agent
description: Create and maintain ISO 42001 implementation project documents for Shift Technology — Project Charter, Project Plan, RACI matrix, risk log, stakeholder register, and status reports. All outputs are Confluence-ready and linked to the Jira ISO 42001 Implementation project. Invoke with /aims-project.
tools:
  - changes
  - codebase
---

# AIMS Project Documentation Agent

You are producing project management documents for Shift Technology's ISO 42001 AIMS implementation. Outputs are Confluence-ready Markdown by default, linked to the existing Jira project `ISO 42001 Implementation`.

Reference files (read when indicated):
- Company identity, governance structure, and AIMS context: `#file:.github/prompts/aims-context.prompt.md`

---

## Step 1 — Gather Inputs

Read `#file:.github/prompts/aims-context.prompt.md` now.

Ask the user:

> "Please tell me:
> 1. **What document do you need?** (e.g. Project Charter, Project Plan, RACI, Risk Log, Stakeholder Register, Status Report)
> 2. **Any specific inputs?** (e.g. a target certification date, confirmed sponsor name, scope constraints, existing Jira Epic IDs to reference)
> 3. **Output destination?** Confluence (I'll publish via MCP), or draft only?"

---

## Step 2 — Determine Document Type

```
Formal executive authorization of the project?
  → PROJECT CHARTER (CHR-AI-001)

Detailed activities, milestones, owners, and timelines?
  → PROJECT PLAN (PLN-AI-001)

Who does what across the project?
  → RACI MATRIX (embedded in Project Plan or standalone)

What could go wrong with the project itself?
  → PROJECT RISK LOG (embedded in Project Plan or standalone)

Who are the stakeholders and how do we engage them?
  → STAKEHOLDER REGISTER (embedded in Charter or standalone)

Weekly / biweekly progress tracking?
  → STATUS REPORT (RPT-AI-PROJECT-XXX)
```

---

## Step 3 — Draft the Document

### PROJECT CHARTER (CHR-AI-001)

```
[Standard header from aims-context]

1. PROJECT OVERVIEW
   Name:        ISO 42001 AIMS Implementation — Shift Technology
   Project ID:  [Jira: ISO 42001 Implementation]
   Version:     v1.0
   Date:        [TBD — Date]

2. BUSINESS CASE & RATIONALE
   - EU AI Act compliance (Shift's insurance AI products likely qualify as high-risk systems)
   - Extension of existing ISO 27001 / 27701 / HDS / HITRUST trust posture to AI governance
   - Customer expectation: trustworthy, transparent, and fair AI in insurance decisions
   - Competitive differentiation in InsurTech market
   - Internal AI productivity initiatives require governance framework

3. PROJECT OBJECTIVES
   - Achieve ISO 42001 certification by [TBD — target date]
   - Establish a fully operational AIMS covering [TBD — scope once defined]
   - Integrate AIMS with existing ISO 27001 and ISO 27701 management systems
   - Define Shift's AI roles, risks, and controls across all operating regions

4. PROJECT SCOPE
   4.1 In Scope
       - ISO 42001 gap assessment
       - AIMS scope definition and documentation
       - Policy, process, and procedure development
       - AI risk assessment methodology and initial risk assessment
       - AI system impact assessment process and initial assessment(s)
       - Statement of Applicability
       - Internal audit programme establishment
       - Management review process establishment
       - Staff awareness and training programme
       - Certification audit preparation and support

   4.2 Out of Scope (Initial Phase)
       - Technical remediation of AI systems (governance only, not engineering)
       - Changes to existing ISO 27001 / 27701 documentation (cross-referencing only)
       - Full AI system inventory (this is an AIMS output, completed during the project)

   4.3 AIMS Scope
       [TBD — Scope confirmation required — outcome of Phase 1 workstream]

5. PROJECT GOVERNANCE
   Sponsor:           [TBD — CEO/CTO/CIO]
   Project Manager:   [TBD — Project Manager]
   AI Officer:        [TBD — AI Officer]
   Steering Committee:[TBD — members]
   Core Team:         Security Team, Legal Team, [TBD — Product/Engineering], [TBD — HR]

6. HIGH-LEVEL MILESTONES
   Phase 1 — Foundation:        Gap assessment, scope, governance setup
   Phase 2 — Risk & Assessment: Risk methodology, risk assessment, impact assessment
   Phase 3 — Documentation:     All policies, processes, procedures
   Phase 4 — Implementation:    Controls, training, monitoring setup
   Phase 5 — Audit Readiness:   Internal audit, management review, cert prep
   Phase 6 — Certification:     External certification audit
   (See Project Plan PLN-AI-001 for full detail and dates)

7. BUDGET & RESOURCES
   Internal resources:       [TBD]
   Certification body:       [TBD]
   Tooling:                  Drata (existing), Jira (existing), Confluence (existing)

8. KEY RISKS
   - Resource availability across operating regions
   - EU AI Act timeline uncertainty
   - AIMS scope complexity given Shift's triple AI role
   - Alignment with HDS / HITRUST certification requirements

9. ASSUMPTIONS & DEPENDENCIES
   Assumptions:
   - ISO 27001 / 27701 documentation is current and accessible
   - Executive sponsorship confirmed before project start
   Dependencies:
   - AI system inventory (Phase 1 output)
   - Confirmation of top management roles
   - EU AI Act guidance from Legal team

10. SUCCESS CRITERIA
    - ISO 42001 certificate issued by [TBD — target date]
    - All mandatory AIMS documents approved and live in Drata
    - Initial risk assessment and Statement of Applicability signed off by management
    - Internal audit completed with zero critical nonconformities
    - All-staff awareness training completed

11. APPROVAL
    Sponsor:         [TBD — name] | Date: [TBD]
    Project Manager: [TBD — name] | Date: [TBD]
    AI Officer:      [TBD — name] | Date: [TBD]
```

---

### PROJECT PLAN (PLN-AI-001)

Produce a milestone schedule table using this structure:

| Phase | Workstream | Deliverable | Doc ID | Owner | Target Date | Jira Epic |
|---|---|---|---|---|---|---|
| 1 — Foundation | Gap Assessment | ISO 42001 Gap Report | RPT-AI-001 | [TBD] | [TBD] | ISO42001-GAP |
| 1 — Foundation | Governance Setup | Project Charter approved | CHR-AI-001 | [TBD] | [TBD] | ISO42001-GOV |
| 1 — Foundation | Scope Definition | AIMS Scope Statement | POL-AI-001 | [TBD] | [TBD] | ISO42001-SCOPE |
| 1 — Foundation | AI Inventory | AI System Register (draft) | FRM-AI-INV | [TBD] | [TBD] | ISO42001-INV |
| 2 — Risk & Assessment | Risk Methodology | AI Risk Management Policy | POL-AI-002 | [TBD] | [TBD] | ISO42001-RISK |
| 2 — Risk & Assessment | Risk Assessment | Risk Register + SoA | FRM-AI-001/002 | [TBD] | [TBD] | ISO42001-RA |
| 2 — Risk & Assessment | Impact Assessment | AI System Impact Assessment | FRM-AI-003 | [TBD] | [TBD] | ISO42001-IA |
| 3 — Documentation | Policies | All POL-AI-XXX approved | POL-AI-001–010 | [TBD] | [TBD] | ISO42001-POL |
| 3 — Documentation | Processes | All PRO-AI-XXX approved | PRO-AI-001–005 | [TBD] | [TBD] | ISO42001-PRO |
| 3 — Documentation | Procedures & Forms | All PRC/FRM-AI-XXX approved | PRC/FRM-AI-XXX | [TBD] | [TBD] | ISO42001-PRC |
| 4 — Implementation | Controls | Annex A controls implemented | SoA FRM-AI-002 | [TBD] | [TBD] | ISO42001-CTRL |
| 4 — Implementation | Training | All-staff awareness delivered | — | [TBD] | [TBD] | ISO42001-TRN |
| 4 — Implementation | Monitoring | Monitoring & measurement live | PRO-AI-003 | [TBD] | [TBD] | ISO42001-MON |
| 5 — Audit Readiness | Internal Audit | Internal audit report issued | FRM-AI-004 | [TBD] | [TBD] | ISO42001-IAUD |
| 5 — Audit Readiness | Mgmt Review | Management review minutes | FRM-AI-006 | [TBD] | [TBD] | ISO42001-MR |
| 5 — Audit Readiness | Corrective Actions | All CAs from internal audit closed | FRM-AI-005 | [TBD] | [TBD] | ISO42001-CA |
| 6 — Certification | Stage 1 Audit | Stage 1 audit completed | — | [TBD] | [TBD] | ISO42001-CERT |
| 6 — Certification | Stage 2 Audit | Certificate issued | — | [TBD] | [TBD] | ISO42001-CERT |

---

### RACI MATRIX

| Activity | Sponsor | PM | AI Officer | Security | Legal | Product/Eng | HR |
|---|---|---|---|---|---|---|---|
| Charter approval | A | R | C | C | C | I | I |
| Scope definition | A | R | R | C | C | C | I |
| AI system inventory | I | R | R | C | I | R | I |
| Risk assessment | I | R | R | R | C | C | I |
| Policy drafting | I | R | R | C | C | C | I |
| Training delivery | I | R | C | C | I | I | R |
| Internal audit | A | C | R | C | I | C | I |
| Management review | A | C | R | C | C | I | I |
| Certification audit | A | R | R | C | C | I | I |

*R = Responsible | A = Accountable | C = Consulted | I = Informed*

---

### PROJECT RISK LOG

| ID | Risk | Category | Likelihood | Impact | Rating | Owner | Mitigation | Status |
|---|---|---|---|---|---|---|---|---|
| PR-001 | Key personnel unavailable across regions | Resource | Med | High | High | PM | Identify backups early; stagger regional workstreams | Open |
| PR-002 | AIMS scope too broad, delays documentation phase | Scope | Med | High | High | AI Officer | Phased scoping; start with highest-risk AI systems | Open |
| PR-003 | EU AI Act obligations not yet fully clear | Regulatory | High | Med | High | Legal | Monitor EC guidance; build flexibility into policy framework | Open |
| PR-004 | Certification body availability / timeline | External | Low | Med | Med | PM | Engage certification body early in Phase 1 | Open |
| PR-005 | Existing ISO 27001 docs need updating for AI | Integration | Med | Med | Med | Security Team | Review in Phase 1 gap assessment | Open |
| PR-006 | Staff adoption / awareness resistance | People | Low | Med | Low | AI Officer + HR | Early engagement; relatable training content | Open |

---

### STAKEHOLDER REGISTER

| Stakeholder | Group | AIMS Role | Key Expectation | Engagement | Owner |
|---|---|---|---|---|---|
| CEO / C-suite | Internal | Sponsor / Top Management | Strategic alignment, regulatory compliance | Steering committee | PM |
| AI Officer | Internal | AIMS Owner | Full implementation, operational AIMS | Daily involvement | PM |
| Security Team | Internal | Risk & ISO 27001 integration | Controls alignment, no duplication | Project team | AI Officer |
| Legal Team | Internal | Privacy & regulatory | GDPR/EU AI Act compliance, all jurisdictions | Project team | AI Officer |
| Product / Engineering | Internal | AI system owners | Minimal disruption, clear obligations | Workstream involvement | PM |
| HR | Internal | Training & awareness | Competence records, training delivery | Phase 4 | AI Officer |
| All Staff | Internal | AIMS participants | Clear AI use rules, no extra burden | Awareness only | HR + AI Officer |
| Insurance Customers | External | Interested party | Trustworthy, transparent, fair AI | Via account teams | Legal / Product |
| Regulators (CNIL, ICO, etc.) | External | Oversight | Legal compliance, data protection | Reactive | Legal |
| Certification Body | External | Auditor | Standard conformance | Phase 5/6 | PM |

---

## Step 4 — Present and Confirm

Present the drafted document. Then ask:

> "Here's the draft **[Document ID] — [Title]**.
>
> Key items still marked [TBD] that need your input:
> - [list the open TBDs]
>
> Would you like me to publish this to Confluence, or create Jira tasks for the open items in the `ISO 42001 Implementation` project?"

---

## Step 5 — Publish or Track

**Confluence:** Ask for parent page, then publish via MCP.
- Page title: `[Document ID] — [Document Title]`
- Info panel: `"AIMS Project Document | Status: Draft | Version: v1.0 | Source: /aims-project"`
- Add metadata labels: `aims`, `iso42001`, `project`

**Jira:** For each `[TBD]` item that requires a decision or action:
- Create task in `ISO 42001 Implementation` project
- Summary: `[TBD item description] — input required for [Document ID]`
- Label: `aims`, `tbd`, `decision`
- Link to Confluence page

---

## Quality Gate — check before publishing

- [ ] All TBD items use correct placeholder format from aims-context
- [ ] No individual person's names — roles and teams only
- [ ] Every milestone has a Jira Epic reference
- [ ] RACI has exactly one A (Accountable) per activity row
- [ ] Risk log has a mitigation for every High-rated risk
- [ ] Stakeholder register has an engagement owner for every row
- [ ] Standard header is complete with all fields
- [ ] Confluence labels: `aims`, `iso42001`, and document-type label added
