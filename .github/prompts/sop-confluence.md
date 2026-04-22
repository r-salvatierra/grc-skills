# Confluence Publishing Reference

Supporting reference for `sop-writer.prompt.md`. Read during Step 6.

---

## Storage Format (required for MCP API calls)

Always use **storage format** (XML-based) when publishing via MCP — not wiki markup.

---

## Page Assembly Order

```
1. Info panel
2. Header block (as a table)
3. <hr/>
4. <h2>Process</h2>  +  Numbered step list
5. <hr/>  (only if Notes section exists)
6. <h2>Notes</h2>  +  Notes content  (only if Notes section exists)
7. <hr/>
8. <h2>Process Overview</h2>  +  Mermaid macro
```

---

## Storage Format Examples

### Info Panel
```xml
<ac:structured-macro ac:name="info" ac:schema-version="1">
  <ac:rich-text-body>
    <p>This is an internal process document. For a visual overview, see the diagram at the bottom of this page.</p>
  </ac:rich-text-body>
</ac:structured-macro>
```

### Header Block (rendered as a two-column table)
```xml
<table>
  <tbody>
    <tr>
      <th><p>Field</p></th>
      <th><p>Value</p></th>
    </tr>
    <tr>
      <td><p>Process Name</p></td>
      <td><p>Security Questionnaire Request</p></td>
    </tr>
    <tr>
      <td><p>Version</p></td>
      <td><p>1.0</p></td>
    </tr>
    <tr>
      <td><p>Effective Date</p></td>
      <td><p>22/04/2025</p></td>
    </tr>
    <tr>
      <td><p>Process Owner</p></td>
      <td><p>Sales Operations Lead</p></td>
    </tr>
    <tr>
      <td><p>Scope</p></td>
      <td><p>Applies to all renewal DDQs, annual DDQs, and RFP/RFI security questionnaires managed in AutoRFP.</p></td>
    </tr>
    <tr>
      <td><p>Source</p></td>
      <td><p><a href="https://jira.example.com/browse/IT-456">IT-456</a></p></td>
    </tr>
  </tbody>
</table>
```

All `<th>` and `<td>` content must be wrapped in `<p>` tags.

### Numbered Step (with sub-bullets)
```xml
<ol>
  <li>
    <p><strong>Submit an Assistance Request in Salesforce (AE / CSM / PM / Solution Consultant)</strong></p>
    <ul>
      <li><p>Use the Assistance Request form — refer to the <a href="[link]">submission guide</a> for instructions.</p></li>
      <li><p>Attach all relevant materials: questionnaire, client instructions, and priority context.</p></li>
      <li><p>Requests submitted outside Salesforce will not be accepted.</p></li>
    </ul>
  </li>
  <li>
    <p><strong>Create a dedicated AutoRFP workspace (Sales Operations)</strong></p>
    <ul>
      <li><p>Upload all client-provided documents and questionnaires.</p></li>
    </ul>
  </li>
</ol>
```

### Mermaid Diagram Macro
```xml
<ac:structured-macro ac:name="mermaid" ac:schema-version="1">
  <ac:plain-text-body><![CDATA[
flowchart TD
    Start([Process starts])
    --> A["1. Submit Assistance Request\n(AE / CSM / PM / SC)"]
    --> B["2. Create AutoRFP Workspace\n(Sales Operations)"]
    --> C{"Capacity available?"}
    C -- Yes --> D["3. Complete Questionnaire\n(Project Team)"]
    C -- No --> E["3a. Notify Sales Ops\nof Adjustment\n(Security)"]
    E --> D
    D --> End([Process ends])
  ]]></ac:plain-text-body>
</ac:structured-macro>
```

⚠️ Requires the Mermaid Diagrams app installed on the Confluence instance. Ask the user to confirm if unsure.

---

## Page Title Convention

Format: `SOP – [Process Name]` — em dash (–), not a hyphen (-).

Examples:
- `SOP – Security Questionnaire Request`
- `SOP – New Employee Onboarding`
- `SOP – Incident Escalation and Response`

---

## MCP Call Patterns

### Find the parent page ID
Search by title before creating. Store the ID for the session.

### Create a new page
```json
{
  "type": "page",
  "title": "SOP – [Process Name]",
  "space": { "key": "IT" },
  "ancestors": [{ "id": "PARENT_PAGE_ID" }],
  "body": {
    "storage": {
      "value": "[full storage format XML]",
      "representation": "storage"
    }
  }
}
```

### Update an existing page
Fetch the current page first to get its version number, then:
```json
{
  "version": { "number": CURRENT_VERSION + 1 },
  "title": "SOP – [Process Name]",
  "body": {
    "storage": {
      "value": "[full storage format XML]",
      "representation": "storage"
    }
  }
}
```
⚠️ Omitting the correct version number causes a 409 Conflict error.

---

## Common Errors

| Error | Cause | Fix |
|-------|-------|-----|
| 409 Conflict | Wrong version number on update | Fetch current version first, increment by 1 |
| 400 Bad Request | Malformed XML | Check all `<td>` and `<th>` cells contain `<p>` tags |
| 404 Not Found | Wrong space key or parent page ID | Re-search for parent page to confirm ID |
| Mermaid not rendering | App not installed | Ask user to confirm Mermaid app is installed |
