# AIMS Methodology Reference

> Companion file to `aims-policy.prompt.md`.
> Read when drafting documents to confirm clause requirements, mandatory contents, and Annex A controls.

---

## Mandatory Documented Information (ISO 42001 Clause 7.5)

These documents **must** exist for ISO 42001 conformance:

| # | Document | Clause | Shift Doc ID |
|---|---|---|---|
| 1 | AIMS Scope | 4.3 | POL-AI-001 (section) |
| 2 | AI Policy | 5.2 | POL-AI-001 |
| 3 | Risk Management Methodology | 6.1.1 | POL-AI-002 |
| 4 | Risk Assessment Results | 6.1.2 | FRM-AI-001 |
| 5 | Risk Treatment Results | 6.1.3 | FRM-AI-001 |
| 6 | Statement of Applicability | 6.1.3 | FRM-AI-002 |
| 7 | AI Risk Treatment Plan | 6.1.3 | PLN-AI-001 (section) |
| 8 | AI System Impact Assessment Results | 6.1.4 | FRM-AI-003 |
| 9 | AI Objectives | 6.2 | POL-AI-001 (section) |
| 10 | Evidence of Competence | 7.2 | HR records in Drata |
| 11 | Monitoring & Measurement Results | 9.1 | RPT-AI-XXX (recurring) |
| 12 | Internal Audit Programme | 9.2 | PRC-AI-001 (annex) |
| 13 | Internal Audit Results | 9.2 | FRM-AI-004 |
| 14 | Management Review Results | 9.3 | FRM-AI-006 |
| 15 | Nonconformities & Corrective Actions | 10.2 | FRM-AI-005 |

---

## Clause-by-Clause Requirements

### Clause 4 — Context
| Clause | What the document must contain |
|---|---|
| 4.1 | External issues (regulations, competition, ethics, climate); internal issues (governance, policies, objectives); Shift's AI roles (Provider / Producer / Internal User) |
| 4.2 | Interested parties list; their specific needs; which needs are addressed through AIMS |
| 4.3 | AIMS boundaries; AI systems in scope; explicit exclusions; documented as standalone or within AI Policy |
| 4.4 | Processes needed and their interactions; PDCA application |

### Clause 5 — Leadership
| Clause | What the document must contain |
|---|---|
| 5.1 | Evidence of top management commitment: AI Policy signed off, resources allocated, AIMS integrated into business processes |
| 5.2 | Strategic intent; objectives framework; commitment to requirements and continual improvement; communicated to all staff; available to interested parties; owner assigned |
| 5.3 | Responsibility for AIMS conformance; responsibility for AIMS performance reporting to top management; communicated within org |

### Clause 6 — Planning
| Clause | What the document must contain |
|---|---|
| 6.1.1 | Risk criteria (acceptable vs. unacceptable); actions for risks and opportunities; integration into AIMS processes |
| 6.1.2 | Repeatable risk assessment process; asset identification; risk sources (Annex C.3); likelihood + consequence scales; risk level calculation; evaluation against criteria; documented in Risk Register |
| 6.1.3 | Treatment options (avoid/reduce/transfer/accept); Annex A control selection; Statement of Applicability (all 38 controls, applicability, justification); Risk Treatment Plan (actions, owners, deadlines, resources); management approval |
| 6.1.4 | Impact assessment process; individual impacts (fairness, accountability, transparency, security/privacy, safety/health, financial, accessibility, human rights); societal impacts (environment, economic, government, health/safety, norms/culture); results documented |
| 6.2 | Measurable objectives; consistent with AI Policy; monitored and communicated; responsible person, resources, deadline, evaluation method per objective |
| 6.3 | Planned, structured change evaluation before implementing; assess why needed, operational impact, new risks introduced |

### Clause 7 — Support
| Clause | What the document must contain |
|---|---|
| 7.1 | Resources identified: data, tooling, system/computing, human; senior management responsible for provision |
| 7.2 | Competence requirements defined; evidence of competence kept (certificates, CVs, attendance records) |
| 7.3 | All staff aware of: AI Policy, their contribution to AIMS, consequences of non-conformance |
| 7.4 | What to communicate; when; to whom; how — internal and external |
| 7.5 | Document creation/update rules; identification, format, review/approval; availability, protection, version control, retention, disposal; external document control |

### Clause 8 — Operation
| Clause | What the document must contain |
|---|---|
| 8.1 | Process criteria established; controls implemented and monitored; planned and unplanned changes controlled; external services controlled |
| 8.2 | Risk assessments performed at planned intervals OR on significant change; results documented |
| 8.3 | Risk treatment plan implemented; effectiveness verified; new risks treated; plan updated when ineffective |
| 8.4 | Impact assessments at planned intervals OR on significant change; prior assessment reviewed and updated |

### Clause 9 — Performance Evaluation
| Clause | What the document must contain |
|---|---|
| 9.1 | What to monitor/measure; KPIs; methods; frequency; responsible persons; results documented |
| 9.2 | Annual audit programme; scope, criteria, auditor selection (no conflict of interest) per audit; audit plan; internal audit report; reported to management |
| 9.3 | Top management review: prior actions status, external/internal changes, interested party changes, AIMS performance, improvement opportunities; decisions documented |

### Clause 10 — Improvement
| Clause | What the document must contain |
|---|---|
| 10.1 | Continual improvement of suitability, adequacy, effectiveness; improvement sources identified; ownership assigned |
| 10.2 | NC identification; root cause analysis; corrective action implemented; effectiveness reviewed; AIMS updated if needed; evidence kept |

---

## Annex A — All 38 Controls

| Control | Topic | Core Obligation |
|---|---|---|
| A.2.2 | AI Policy | Document policy for AI development/use |
| A.2.3 | Policy Alignment | Align AI policy with other org policies (security, privacy, quality) |
| A.2.4 | Policy Review | Review at planned intervals |
| A.3.2 | AI Roles | Define and allocate AI roles and responsibilities |
| A.3.3 | Reporting Concerns | Process to report concerns throughout AI lifecycle |
| A.4.2 | Resource Documentation | Identify and document all AI system resources |
| A.4.3 | Data Resources | Document data resources: provenance, quality, bias, retention |
| A.4.4 | Tooling Resources | Document ML models, algorithms, tools used |
| A.4.5 | System & Computing | Document hardware, cloud/on-prem, environmental impact |
| A.4.6 | Human Resources | Document competences needed per lifecycle stage |
| A.5.2 | Impact Assessment Process | Establish and maintain impact assessment process |
| A.5.3 | Impact Assessment Records | Document and retain results |
| A.5.4 | Individual Impacts | Assess: fairness, accountability, transparency, privacy, safety, financial, accessibility, human rights |
| A.5.5 | Societal Impacts | Assess: environment, economic, governance, health/safety, norms/culture |
| A.6.1.2 | Dev Objectives | Document objectives for responsible AI development |
| A.6.1.3 | Dev Process | Define responsible design and development process |
| A.6.2.2 | Requirements & Specs | Document requirements for new/enhanced AI systems |
| A.6.2.3 | Design & Dev Docs | Document design decisions and choices |
| A.6.2.4 | Verification & Validation | Define V&V measures and release criteria |
| A.6.2.5 | Deployment | Document deployment plan and pre-deployment requirements |
| A.6.2.6 | Operation & Monitoring | Define ongoing operation, monitoring, repair, and support |
| A.6.2.7 | Technical Documentation | Provide tech docs to relevant interested parties |
| A.6.2.8 | Event Logging | Determine when event logging is required and what to log |
| A.7.2 | Data Management | Define data management processes for AI |
| A.7.3 | Data Acquisition | Document data acquisition, sources, selection criteria |
| A.7.4 | Data Quality | Define and ensure data quality requirements |
| A.7.5 | Data Provenance | Track origin and transformation of data |
| A.7.6 | Data Preparation | Define data preparation methods and criteria |
| A.8.2 | User Documentation | Provide necessary information to AI system users |
| A.8.3 | External Reporting | Enable external parties to report adverse impacts |
| A.8.4 | Incident Communication | Plan for communicating incidents to users |
| A.8.5 | Interested Party Info | Define obligations to report to interested parties |
| A.9.2 | Responsible Use Process | Define process for responsible AI use |
| A.9.3 | Use Objectives | Document objectives for responsible use |
| A.9.4 | Intended Use | Ensure AI systems used per documentation |
| A.10.2 | Responsibility Allocation | Allocate responsibilities across AI lifecycle parties |
| A.10.3 | Suppliers | Process to ensure suppliers align with responsible AI approach |
| A.10.4 | Customers | Consider customer expectations in responsible AI approach |

---

## ISO 27001 / 27701 Integration Points

Use these to avoid duplicating existing Shift controls:

| ISO 42001 Area | Reference Existing Shift Doc |
|---|---|
| Risk methodology (6.1) | Align with Shift ISO 27001 risk assessment methodology |
| Privacy controls (A.5.4, A.7) | Reference Shift ISO 27701 privacy controls |
| Security controls (A.6.1.2, A.6.2.6) | Reference Shift ISO 27001 Annex A controls |
| Document control (7.5) | Align with existing Shift document control procedure |
| Internal audit (9.2) | Integrate with existing Shift ISO 27001 audit programme |
| Corrective action (10.2) | Use same Shift CA process if suitable |
| Competence (7.2) | Extend existing HR/training records for AI-specific competences |

---

## Risk Scales (Default — Align to Shift's Existing Methodology)

**Likelihood**
| Level | Description |
|---|---|
| Low | Unlikely given existing controls and context |
| Medium | Possible; has occurred in similar systems |
| High | Likely; known vulnerability or precedent exists |

**Consequence** (consider: company, individuals, societies)
| Level | Description |
|---|---|
| Low | Minimal impact; easily recoverable |
| Medium | Moderate harm; requires effort to remediate |
| High | Significant harm; regulatory, reputational, or safety impact |

**Risk Level Matrix**
| | Low Consequence | Medium Consequence | High Consequence |
|---|---|---|---|
| **Low Likelihood** | Low | Low | Medium |
| **Medium Likelihood** | Low | Medium | High |
| **High Likelihood** | Medium | High | High |
