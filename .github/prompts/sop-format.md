# SOP Format Reference

Supporting reference for `sop-writer.prompt.md`. Read during Step 4.

---

## Header Block

```
**Process Name:**   [Clear noun phrase — e.g. "Security Questionnaire Request"]
**Version:**        1.0
**Effective Date:** DD/MM/YYYY
**Process Owner:**  [Role title — e.g. Sales Operations Lead]
**Scope:**          [Which teams, request types, or systems this applies to. Name explicit exclusions if relevant.]
**Source:**         [Jira ticket link]
```

**Rules:**
- Process Name is an action-oriented noun phrase, not a verb phrase. "Security Questionnaire Request", not "How to Request a Security Questionnaire".
- Owner is always a role or team name, never an individual's name.
- Scope must be specific — name the teams, document types, and platforms it applies to.

---

## Numbered Step List

Each step follows this pattern:

```
**[#]. [Action statement] ([Owner])**
- [Detail, exception, or link — only if needed]
- [Detail, exception, or link — only if needed]
```

### Examples — Good vs Weak

| ✅ Good | ❌ Weak |
|---------|---------|
| `**1. Submit an Assistance Request in Salesforce (AE / CSM / PM / Solution Consultant)**` | `**1. Send a request**` |
| `**2. Create a dedicated AutoRFP workspace (Sales Operations)**` | `**2. Set up the workspace**` |
| `**3. Assign a Request Owner and required collaborators (Sales Operations)**` | `**3. Assign someone**` |

### Step granularity target
- Granular enough for an unfamiliar team member to execute independently
- Not so granular it describes individual UI clicks
- Sub-bullets are for exceptions, links to guides, or important constraints — not for restating the step

### Decision branches
When a step has a conditional path, use a lettered sub-step:

```
**3. Check capacity against priority tier (Security)**
- If capacity allows → proceed to Step 4
- If adjustment needed → go to Step 3a

**3a. Notify Sales Operations of deadline or queue adjustment (Security)**
- Then return to Step 4
```

---

## Notes Section (optional)

Use a Notes section only when there are standing callouts that don't belong inside any single step:

```
## Notes
- Requests submitted outside Salesforce will not be accepted.
- All questionnaires must be managed in AutoRFP — no exceptions.
- For escalation contacts, refer to [link].
```

Keep it short. If a note applies to one step only, put it as a sub-bullet on that step instead.

---

## Full Example — Security Questionnaire Request SOP

---

**Process Name:**   Security Questionnaire Request
**Version:**        1.0
**Effective Date:** 22/04/2025
**Process Owner:**  Sales Operations Lead
**Scope:**          Applies to all renewal DDQs, annual DDQs, and RFP/RFI security questionnaires. All questionnaires must be managed in AutoRFP.
**Source:**         [IT-456](https://jira.example.com/browse/IT-456)

---

**1. Submit an Assistance Request in Salesforce (AE / CSM / PM / Solution Consultant)**
- Use the Assistance Request form — refer to the [submission guide](link) for step-by-step instructions.
- Attach all relevant materials: questionnaire, client instructions, and any priority context.
- Requests submitted outside Salesforce will not be accepted.

**2. Create a dedicated AutoRFP workspace (Sales Operations)**
- Upload all client-provided documents and questionnaires.
- Review request completeness and confirm the priority tier.

**3. Assign a Request Owner and required collaborators (Sales Operations)**
- Collaborators may include Security, Legal, or HR depending on the questionnaire scope.
- Refer to the [Sales Ops AutoRFP Intake Guide](link) for detailed setup steps.

**4. Check capacity and proceed or adjust (Security)**
- If capacity allows per priority tier → proceed to Step 5.
- If adjustment is needed → notify Sales Operations of the revised deadline or queue position, then proceed to Step 5.

**5. Complete and update responses in AutoRFP (Project Team)**
- Security checks capacity and may adjust deadlines or queue order based on priority tier.
- All responses are entered directly in AutoRFP — no offline edits.

**6. Conduct security review (Security)**
- If additional review is needed → return to Step 5.
- If review is complete → proceed to Step 7.

**7. Final QA and delivery (Sales Operations)**
- Confirm all sections are complete before sending to the client.

---

## What to Omit

The following should **not** appear in the process document:
- Inputs/Outputs columns or tables
- MARIO Management table
- Resources table
- Role responsibility matrices (RACI)
- Anything the reader would skip

If governance metadata is needed (version history, approver sign-off), it belongs in the Confluence page properties — not in the body of the SOP.
