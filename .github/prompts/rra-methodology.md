# RRA Methodology Reference

Supporting reference for `rra.prompt.md`. Read during Steps 2 and 5.

---

## STRIDE Threat Categories

| Category | Stands For | What It Means | Example |
|----------|-----------|---------------|---------|
| S | Spoofing | Attacker impersonates a user, system, or service | Forged auth tokens, fake API caller |
| T | Tampering | Unauthorised modification of data or code | Manipulating API requests, altering DB records |
| R | Repudiation | Denying an action occurred; lack of audit trail | No logging of privileged actions |
| I | Information Disclosure | Exposure of data to unauthorised parties | PII in error messages, unencrypted storage |
| D | Denial of Service | Disrupting availability of a system or feature | Rate limit bypass, resource exhaustion |
| E | Elevation of Privilege | Gaining higher permissions than intended | IDOR, broken access control, SSRF |

Map every identified threat to one or more STRIDE categories.

---

## OWASP Top 10 (2021) — Apply Where Relevant

| # | Category | Common in |
|---|----------|-----------|
| A01 | Broken Access Control | APIs, multi-tenant systems |
| A02 | Cryptographic Failures | Data storage, data in transit |
| A03 | Injection | SQL, NoSQL, command injection |
| A04 | Insecure Design | Architecture and design phase |
| A05 | Security Misconfiguration | Cloud services, default settings |
| A06 | Vulnerable & Outdated Components | Dependencies, third-party libraries |
| A07 | Identification & Authentication Failures | Login flows, session management |
| A08 | Software & Data Integrity Failures | CI/CD pipelines, update mechanisms |
| A09 | Security Logging & Monitoring Failures | Audit trails, alerting |
| A10 | Server-Side Request Forgery (SSRF) | Internal network access via app |

---

## Risk Matrix

Combine Likelihood and Impact to derive Risk Level:

| Likelihood \ Impact | Low | Medium | High |
|--------------------|-----|--------|------|
| **High** | Medium | High | High |
| **Medium** | Low | Medium | High |
| **Low** | Low | Low | Medium |

**Likelihood guidance:**
- **High** — Attack is common, well-documented, low skill required, or system is internet-facing with this exposure
- **Medium** — Requires some skill or specific conditions; plausible but not routine
- **Low** — Requires significant skill, access, or insider knowledge; unlikely in practice

**Impact guidance:**
- **High** — Regulatory breach, significant data exposure (PII/credentials at scale), service outage affecting users, reputational damage
- **Medium** — Limited data exposure, degraded service, recoverable incident with moderate effort
- **Low** — Minimal data exposure, negligible service impact, easily recoverable

---

## Clarifying Question Bank

Use this bank in Step 3 to select only the questions that are genuinely unclear from the source material. Never ask more than 5.

### Scope & System
- What is the primary business function of this system/feature?
- Is this a new build, a modification to an existing system, or a third-party integration?
- Who are the user types — internal staff only, external customers, or both?
- What is the deployment environment — cloud (which provider/region?), on-prem, or hybrid?

### Data
- Does this system process, store, or transmit any PII? If so, what types (name, email, financial, health, etc.)?
- Are credentials, secrets, or API keys stored or handled by this system?
- Is any data shared with third parties or external services?
- What is the data retention period, and is there a deletion/anonymisation process?

### Authentication & Access
- How are users authenticated — internal IdP, external OAuth, SSO, API key?
- Is there role-based access control? If so, what roles exist and what can each do?
- Are there any privileged or admin functions? Who has access to them?
- Is there multi-tenancy — could one user's actions affect another user's data?

### Infrastructure & Dependencies
- What external services or APIs does this system depend on?
- Are there any third-party libraries or components with known vulnerability history?
- Is there a WAF, rate limiting, or DDoS protection in front of this system?
- How are secrets and environment variables managed (e.g. vault, env files, CI/CD secrets)?

### Existing Controls
- Is data encrypted at rest and in transit?
- Are there existing audit logs for privileged actions?
- Has this system or a predecessor undergone a previous security review or pentest?
- Are there automated security scans (SAST, DAST, dependency scanning) in the CI/CD pipeline?

---

## Sensitivity Classification

| Level | Definition | Examples |
|-------|-----------|---------|
| Public | No harm if disclosed | Marketing content, public docs |
| Internal | Intended for staff only | Internal processes, team data |
| Confidential | Significant harm if disclosed | Customer PII, credentials, financial data |
| Restricted | Severe harm if disclosed | Health records, legally privileged data, auth secrets |

---

## References to Include in Published Page

- [Mozilla's Rapid Risk Assessment](https://infosec.mozilla.org/guidelines/risk/rapid_risk_assessment.html)
- [STRIDE threat model](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats)
- [OWASP Risk Rating Methodology](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology)
- [MITRE ATT&CK](https://attack.mitre.org/)
