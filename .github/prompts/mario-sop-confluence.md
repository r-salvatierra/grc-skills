# Confluence Publishing Reference

Supporting reference for `mario-sop.prompt.md`. Read during Step 6.

---

## Storage Format (required for MCP API calls)

Always use **storage format** (XML-based) when publishing via MCP — not wiki markup.

### Table
```xml
<table>
  <tbody>
    <tr>
      <th><p>Column Header</p></th>
      <th><p>Column Header</p></th>
    </tr>
    <tr>
      <td><p>Value</p></td>
      <td><p>Value</p></td>
    </tr>
  </tbody>
</table>
```
All `<th>` and `<td>` content must be wrapped in `<p>` tags.

### Info Panel
```xml
<ac:structured-macro ac:name="info" ac:schema-version="1">
  <ac:rich-text-body>
    <p>This is an internal SOP. For the simplified process overview, see the diagram below.</p>
  </ac:rich-text-body>
</ac:structured-macro>
```

### Mermaid Diagram Macro
```xml
<ac:structured-macro ac:name="mermaid" ac:schema-version="1">
  <ac:plain-text-body><![CDATA[
flowchart TD
    Start([Process starts]) --> A[Step 1]
    A --> End([Process ends])
  ]]></ac:plain-text-body>
</ac:structured-macro>
```
⚠️ Requires the Mermaid Diagrams app installed on the Confluence instance. Ask the user to confirm if unsure.

---

## Page Assembly Order

```
1. Info panel
2. <h2>Management</h2>  +  Management table
3. <hr/>
4. <h2>Activities &amp; Resources</h2>  +  Activities table
5. <hr/>
6. <h2>Resources</h2>  +  Resources table
7. <hr/>
8. <h2>Employee Process Overview</h2>  +  Mermaid macro
```

---

## Page Title Convention

Format: `SOP – [Process Name]` — em dash (–), not a hyphen (-).

Examples:
- `SOP – IP Address Access Review`
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
