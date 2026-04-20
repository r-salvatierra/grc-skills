---
mode: agent
description: Master context file for Shift Technology's ISO 42001 AI Management System (AIMS) implementation. Load this file at the start of any AIMS-related task — policy writing, project documentation, or presentations. Contains company identity, regulatory environment, governance structure, documentation conventions, and AIMS scope. Invoke with /aims-context or reference via #file in other AIMS prompts.
tools:
  - changes
  - codebase
---

# Shift Technology — AIMS Master Context

This file is a **dependency**, not a standalone agent. It is referenced by all other AIMS prompts via `#file:.github/prompts/aims-context.prompt.md`. Load it first and apply its content to everything produced in the session.

---

## 1. Company Identity

| Field | Value |
|---|---|
| **Company Name** | Shift Technology |
| **Industry** | InsurTech — AI-powered insurance claims, fraud detection, and decision automation |
| **Size** | Mid-market to Enterprise |
| **HQ** | Paris, France |
| **Operating Regions** | France, United States, Canada, United Kingdom, Ireland, Western EU, Mexico, Brazil, Singapore, Japan |

---

## 2. AI Roles (ISO 42001 Clause 4.1)

Shift Technology holds **three concurrent AI roles**. All AIMS documents must reflect all three where relevant.

| Role | Description |
|---|---|
| **AI Provider** | Delivers SaaS products with embedded ML/AI features to insurance customers |
| **AI Producer / Developer** | Builds AI models and agentic AI capabilities internally |
| **AI Customer (Internal)** | Uses AI tools internally to automate repetitive tasks and improve productivity |

---

## 3. Regulatory & Compliance Environment

All AIMS documents must be aware of and, where relevant, reference the following:

**AI & Privacy Regulations**
- **EU AI Act** — Shift's insurance AI products likely qualify as high-risk AI systems (claims assessment, fraud detection, credit scoring implications)
- **GDPR** — All EU personal data; already ISO 27701 certified
- **UK GDPR / DPA 2018** — UK operations
- **CCPA + US state privacy laws** — US operations
- **PIPEDA / Law 25** — Canada
- **PDPA** — Singapore
- **APPI** — Japan
- **LGPD** — Brazil
- **HDS (Hébergeur de Données de Santé)** — French health data hosting; already certified
- **HITRUST** — Already certified; must maintain alignment

**Existing Certifications (already held)**
- ✅ ISO 27001 — Information Security Management System
- ✅ ISO 27701 — Privacy Information Management
- ✅ HDS — French health data hosting
- ✅ HITRUST — US health information trust
- 🔄 ISO 42001 — AI Management System *(in implementation)*

> **Integration rule:** ISO 42001 controls must **cross-reference** existing ISO 27001 and ISO 27701 documentation. Do not rewrite security or privacy controls from scratch.

---

## 4. Governance Structure

> ⚠️ Roles marked `[TBD]` must be replaced when confirmed during the project charter phase.

| Role | Status | Notes |
|---|---|---|
| Top Management / AIMS Sponsor | `[TBD — CEO/CTO/CIO]` | Must be C-level; confirmed in Project Charter |
| AI Officer / AIMS Owner | `[TBD — AI Officer]` | Accountable for AIMS implementation and performance |
| AIMS Project Manager | `[TBD — Project Manager]` | Coordinates ISO 42001 implementation project |
| Security Team | Existing | Risk & compliance; ISO 27001 owners; key AIMS stakeholder |
| Legal Team | Existing | Privacy; ISO 27701 owners; multi-jurisdiction regulatory compliance |
| AIMS Project Team | `[TBD — defined in Project Charter]` | Cross-functional |

---

## 5. AIMS Scope

> ⚠️ Scope is not yet formally defined. Use the placeholder below in all documents until confirmed via Project Charter.

**Placeholder scope statement:**
> *"The scope of Shift Technology's AI Management System (AIMS) will be determined during the ISO 42001 implementation project, encompassing AI systems developed, provided, and used by Shift Technology. This document will be updated when the scope is formally approved by top management."*

**Expected coverage (to be confirmed):**
- Customer-facing AI features in Shift's insurance SaaS products
- Internally developed agentic AI systems
- Internal AI productivity tools and initiatives

---

## 6. Documentation Conventions

**Systems of record**

| Tool | Purpose |
|---|---|
| **Drata** | Primary GRC platform — system of record for all AIMS policies and evidence |
| **Confluence** | Secondary — synced from Drata for collaboration and visibility |
| **Jira** | Project management — `ISO 42001 Implementation` project already exists |

**Document numbering — AI-standalone series (separate from ISO 27001 numbering)**

| Code | Type | Example |
|---|---|---|
| `POL` | Policy | POL-AI-001 |
| `PRO` | Process | PRO-AI-001 |
| `PRC` | Procedure | PRC-AI-001 |
| `FRM` | Form / Template | FRM-AI-001 |
| `RPT` | Report | RPT-AI-001 |
| `PLN` | Plan | PLN-AI-001 |
| `CHR` | Charter | CHR-AI-001 |

**Version format:** `v[MAJOR].[MINOR]` — e.g. `v1.0`, `v1.1`, `v2.0`

**Standard document header (use on all AIMS documents)**
```
Document Title:   [Full Title]
Document ID:      [TYPE]-AI-[NNN]
Version:          v1.0
Status:           Draft | Under Review | Approved
Owner:            [TBD — AI Officer]
Approver:         [TBD — Top Management]
Last Reviewed:    [TBD — Date]
Next Review:      [TBD — Date + 1 year]
Classification:   Internal
Related Docs:     [List related document IDs]
```

**Placeholder format (searchable in Drata/Confluence)**
- `[TBD — AI Officer]` — unfilled role
- `[TBD — Scope confirmation required]` — scope-dependent content
- `[TBD — Date]` — dates not yet set
- `[REF: DOC-ID]` — documents not yet created

---

## 7. Writing Principles

Apply to **all** Shift AIMS documents regardless of type:

1. **Lean but compliant** — Write the minimum needed to satisfy ISO 42001. No padding.
2. **ISO 9001 structure** — Follow PDCA logic and standard section order: Purpose → Scope → References → Definitions → Requirements → Responsibilities → Records → Review.
3. **Cross-reference, don't duplicate** — Where ISO 27001 or 27701 controls exist, reference them by document ID.
4. **Placeholder discipline** — All TBDs use the exact formats above — they must be grep-able.
5. **Jurisdiction-aware** — Note regional variances explicitly rather than ignoring them.
6. **Role-aware** — Always consider Shift's triple AI role (Provider + Producer + Internal User).
7. **Tone** — Standard corporate: professional, clear, readable. Active voice. Tables over prose where possible.

---

## 8. ISO 42001 Shall / Should / May Convention

- **"shall"** — mandatory requirement
- **"should"** — recommended, not mandatory
- **"may"** — permitted option
- Never use **"must"** — use "shall" for ISO consistency
- Always write in **third person**: "The AI Officer shall..." not "You should..."
