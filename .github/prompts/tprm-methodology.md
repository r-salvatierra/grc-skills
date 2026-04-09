# Vendor Security Assessment — Methodology

Reference this file in Copilot Chat alongside `vendor-assessment.prompt.md` to conduct
a structured, context-aware third-party vendor security assessment at SHIFT.

---

## Purpose

Assess a vendor's security posture in the context of how they are actually used:
- What data or systems of SHIFT's they can access
- How a compromise would impact SHIFT across four dimensions
- Whether their compliance evidence is adequate for that level of exposure

---

## Phase 1 — Intake: Required Inputs

All fields below are required before starting. If any are missing, ask for them.

### Q11 — Vendor Access to SHIFT Assets
Select all that apply:
- `SHIFT_SYSTEMS` — vendor can log into or query SHIFT systems
- `SHIFT_DATA` — SHIFT internal/operational data is shared with the vendor
- `CUSTOMER_DATA` — customer PII or sensitive records are shared with the vendor
- `NONE` — vendor has no direct data or system access (requires Q12 explanation)

### Q12 — If None, Explain
Free-text. What does the vendor provide if they have no data or system access?

### Q13–Q16 — Impact Scores (1–5 each)
| Question | Dimension |
|---|---|
| Q13 | Financial impact on SHIFT if vendor data/asset is compromised |
| Q14 | Reputational impact on SHIFT |
| Q15 | Regulatory impact on SHIFT |
| Q16 | Staff impact on SHIFT |

### Additional Context Required
- **Vendor type**: SaaS / On-Premises / Integration (API) / Professional Services / MSP
- **Hosting model**: Vendor-hosted / Customer-hosted / Hybrid
- **Integration depth**: None / One-way inbound / One-way outbound / Bidirectional / Admin or Privileged
- **Reports provided**: List what the vendor has supplied (SOC 2 Type I/II, ISO 27001 cert + SOA, pen test, CAIQ, self-assessment, none)

### Assessor Observation Notes
Brief free-text from the assessor — context not captured by the form (e.g., "sole-source supplier", "read-only API key only", "DPA already executed by legal", "vendor recently acquired"). Keep to 3–5 sentences.

---

## Phase 2 — Inherent Risk Scoring

### Step 1: Base Impact Score

Weighted average of Q13–Q16:

| Dimension | Weight |
|---|---|
| Financial (Q13) | 25% |
| Reputational (Q14) | 25% |
| Regulatory (Q15) | 30% |
| Staff (Q16) | 20% |

`Base Score = (Q13 × 0.25) + (Q14 × 0.25) + (Q15 × 0.30) + (Q16 × 0.20)`

### Step 2: Data Exposure Modifier (Q11)

Apply the highest applicable:

| Q11 Selection | Modifier |
|---|---|
| NONE | +0.0 |
| SHIFT_DATA only | +0.3 |
| SHIFT_SYSTEMS only | +0.5 |
| CUSTOMER_DATA (any combination) | +0.8 |
| CUSTOMER_DATA + SHIFT_SYSTEMS | +1.0 |

### Step 3: Integration Depth Modifier

| Depth | Modifier |
|---|---|
| None | +0.0 |
| One-way inbound (vendor pushes to SHIFT) | +0.1 |
| One-way outbound (SHIFT pushes to vendor) | +0.2 |
| Bidirectional | +0.4 |
| Admin / Privileged access | +0.7 |

### Inherent Risk Score

`Inherent Risk = Base Score + Data Modifier + Integration Modifier` (cap at 5.0)

### Inherent Risk Tiers

| Score | Tier |
|---|---|
| ≤ 1.5 | Low |
| 1.6–2.5 | Medium |
| 2.6–3.5 | High |
| 3.6–5.0 | Critical |

---

## Impact Scale Reference

### Q13 — Financial Impact

| Score | Description |
|---|---|
| 1 | Minimal financial loss |
| 2 | Minor financial loss |
| 3 | Moderate financial loss |
| 4 | Significant financial loss |
| 5 | Massive financial loss |

### Q14 — Reputational Impact

| Score | Description |
|---|---|
| 1 | Local media attention; quickly remedied |
| 2 | Local reputational damage |
| 3 | National short-term negative media coverage |
| 4 | National long-term negative media coverage / significant market share loss |
| 5 | International long-term negative media coverage / game-changing market share loss |

### Q15 — Regulatory Impact

| Score | Description |
|---|---|
| 1 | Not reportable to regulator |
| 2 | Reportable incident to regulator; no follow-up required |
| 3 | Report of breach to regulator with immediate correction to be implemented |
| 4 | Report to regulator requiring major corrective action project |
| 5 | Significant prosecution, fines, litigation including class actions, incarceration of leaders |

### Q16 — Staff Impact

| Score | Description |
|---|---|
| 1 | Isolated staff dissatisfaction |
| 2 | General staff morale problems and increase in turnover |
| 3 | Widespread staff morale problems and high turnover |
| 4 | Some senior managers leave; high turnover of experienced staff; not perceived as employer of choice |
| 5 | Multiple senior leaders leave |

---

## Phase 3 — Vendor Classification and Minimum Evidence Bar

### Minimum Evidence by Vendor Type and Exposure

| Vendor Type | Exposure Level | Minimum Acceptable Evidence |
|---|---|---|
| SaaS | Customer data | SOC 2 Type II (≤12 months) |
| SaaS | SHIFT data or systems only | SOC 2 Type II or ISO 27001 cert |
| Integration (API) | Customer data | SOC 2 Type II + pen test |
| Integration (API) | SHIFT data or systems only | SOC 2 Type II or ISO 27001 |
| On-Premises | Any | ISO 27001 cert + SOA + vulnerability scan |
| Professional Services / MSP | System access | SOC 2 or ISO 27001 + background checks |
| Professional Services | No system access | DPA + self-assessment |
| Any | NONE / no access | Contractual controls only; no report required |

---

## Phase 4 — Report Analysis

### SOC 2 Type II — Key Focus Areas

Always check these regardless of vendor type:
- **Report metadata**: Auditor, coverage period end date (flag if >12 months ago), audit opinion (clean / qualified / adverse)
- **CC6 — Logical Access**: MFA enforced, least privilege, role-based access, periodic access reviews, offboarding process
- **CC7 — System Operations**: Monitoring, anomaly detection, incident handling
- **CC8 — Change Management**: Formal change control process
- **CC9 — Risk Mitigation**: Vendor's own subprocessor/third-party management
- **Exceptions**: List every exception noted; a qualified opinion is not a clean report
- **Subprocessors**: All listed individually and in-scope? Flag any carved-out
- **CUECs**: Complementary User Entity Controls — obligations placed on SHIFT that must be confirmed as met

Additional Trust Service Categories (check if in scope):
- **Availability (A)**: SLA, BCP, disaster recovery — relevant when vendor hosts a critical service
- **Confidentiality (C)**: Data handling, encryption, DLP — relevant when customer data is shared
- **Privacy (P)**: Data subject rights, retention, consent — relevant for any PII

### SOC 2 Type I

Same checks as Type II, but note: this is design-only assessment — not evidence controls operated effectively over time. Not acceptable for customer data or High/Critical risk vendors.

### ISO 27001 Certificate + SOA

**Certificate checks:**
- Certification body is accredited (UKAS, DAkkS, ANAB, JAS-ANZ, etc.)
- Certificate is current and not expired
- Scope statement covers the vendor's service to SHIFT

**SOA focus areas** — check that applicable controls are marked **Implemented**, not just Applicable:

| ISO Section | Topic | Relevant When |
|---|---|---|
| A.5.15–A.5.18 | Access Control / IAM | Vendor has system access |
| A.8.24 | Cryptography | Customer data shared |
| A.8.8–A.8.19 | Operations / Vuln Management | Any access; on-prem especially |
| A.5.24–A.5.28 | Incident Management | Always — check breach notification SLA |
| A.5.19–A.5.22 | Supplier Relationships | Check vendor's own third-party controls |
| A.5.31–A.5.36 | Compliance | Regulatory impact ≥3 |

Flag: any control marked Applicable but NOT Implemented.

### Penetration Test Report

- Test date (flag if >24 months old; prefer ≤12 months)
- Testing firm is independent (not vendor's own team)
- Scope includes the systems/APIs that SHIFT integrates with
- All Critical (CVSS ≥9.0) and High (CVSS ≥7.0) findings resolved
- Re-test conducted after remediation?

### CAIQ (Cloud Security Alliance Questionnaire)

Self-declared only — not independently verified. Acceptable as supplementary evidence; not acceptable as sole evidence for customer data or High/Critical vendors. Key domains: IAM, DSP (data security/privacy), LOG (logging/monitoring), CEK (cryptography).

### Self-Assessment / Questionnaire Only

No independent verification. Control score capped at 2. Require contractual DPA and right-to-audit clause as compensating controls.

---

## Phase 5 — Control Effectiveness Score

### Scoring Table

| Evidence | Max Control Score |
|---|---|
| SOC 2 Type II — clean, ≤12 months | 5 |
| SOC 2 Type II — minor exceptions, current | 4 |
| SOC 2 Type II — qualified opinion or 12–24 months old | 3 |
| SOC 2 Type I — clean, current | 3 |
| ISO 27001 cert + SOA — current, broad scope | 3–4 |
| CAIQ only | 2 |
| Self-assessment / questionnaire only | 2 |
| No evidence provided | 0 |
| Any report >24 months old | max 1 |

### Modifiers

| Condition | Adjustment |
|---|---|
| Report >12 months old | Cap control score at 3 |
| Report >24 months old | Cap control score at 1 |
| Vendor startup (<3 years, no independent audit) | Cap control score at 2 |
| Vendor had public breach in last 36 months | +0.5 to inherent risk score |
| DPA in place | −0.1 to residual score |
| Right-to-audit clause in contract | −0.1 to residual score |
| Sole-source vendor | Flag for escalation regardless of tier |

---

## Phase 6 — Residual Risk and Decision

### Control Reduction Table

| Control Score | Risk Reduction |
|---|---|
| 5 | −2.0 |
| 4 | −1.5 |
| 3 | −1.0 |
| 2 | −0.5 |
| 1 | −0.2 |
| 0 | −0.0 |

`Residual Risk = MAX(Inherent Risk − Control Reduction, 1.0)`

Apply qualitative modifiers after calculation.

### Decision Framework

| Residual Score | Tier | Decision |
|---|---|---|
| ≤ 1.5 | Low | APPROVE — Annual review |
| 1.6–2.5 | Medium | APPROVE WITH CONDITIONS — 6-month review; DPA required |
| 2.6–3.5 | High | CONDITIONAL — Remediation required within 90 days; 3-month review |
| 3.6–5.0 | Critical | ESCALATE / REJECT — Senior sign-off and remediation plan required before proceeding |

---

## Output Template

Produce the observation note in this structure exactly:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VENDOR SECURITY ASSESSMENT — OBSERVATION NOTE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Vendor Name      : [Name]
Assessment Date  : [Date]
Assessed By      : [Name / Role]
Next Review      : [Date or trigger]

── VENDOR PROFILE ──────────────────────────────
Type             : [SaaS / Integration / On-Prem / Services / MSP]
Hosting          : [Vendor-hosted / Customer-hosted / Hybrid]
Data/Access      : [SHIFT Systems / SHIFT Data / Customer Data / None]
Integration Depth: [None / One-way / Bidirectional / Admin]

── INHERENT RISK ───────────────────────────────
Financial Impact : [1–5] — [label from Q13 scale]
Reputational     : [1–5] — [label from Q14 scale]
Regulatory       : [1–5] — [label from Q15 scale]
Staff            : [1–5] — [label from Q16 scale]
Data Modifier    : [+value]
Integration Mod  : [+value]
Inherent Score   : [X.X] → [LOW / MEDIUM / HIGH / CRITICAL]

── EVIDENCE REVIEWED ───────────────────────────
[Each document on its own line: type, auditor/certifier, date, coverage period, clean or exceptions noted]

── CONTROL ASSESSMENT ──────────────────────────
[Per trust category or ISO control domain: what was reviewed, key findings, exceptions or gaps observed. 2–4 sentences per area.]

── GAPS & EXCEPTIONS ───────────────────────────
1. [Description] — [High / Medium / Low] — [Recommended action]

── ASSESSOR OBSERVATIONS ───────────────────────
[3–5 sentences of practitioner context. Include anything from the assessor notes field that affects the decision.]

── RESIDUAL RISK ────────────────────────────────
Control Score    : [X / 5]
Residual Score   : [X.X] → [LOW / MEDIUM / HIGH / CRITICAL]
Decision         : [APPROVE / APPROVE WITH CONDITIONS / ESCALATE / REJECT]

── CONDITIONS / ACTIONS ─────────────────────────
1. [Action] — Owner: [Role] — Due: [Timeframe]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Hard Rules — Never Override

- Do not approve customer data access without SOC 2 Type II.
- Flag any report where the coverage period ended more than 12 months ago.
- A qualified SOC 2 opinion is not a clean report — list every exception.
- Subprocessors carved out of audit scope must be flagged.
- If no evidence is provided, residual risk = inherent risk (zero reduction).
- If Q11 = NONE: stop at classification. Produce a brief note. No report review required.
