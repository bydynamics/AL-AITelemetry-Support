# Troubleshooting

## Connection issues

| Symptom | Possible cause | Resolution |
|---------|---------------|------------|
| "Test Connection failed" | Invalid connection string | Verify the connection string in Azure portal and re-enter it |
| "Test Connection failed" | Network restrictions | Ensure outbound HTTPS to `*.applicationinsights.azure.com` is allowed |
| Query returns no results | Wrong Application Insights resource | Confirm the connection string matches the resource linked to your BC environment |

## Query errors

| Symptom | Possible cause | Resolution |
|---------|---------------|------------|
| "Query syntax error" | Invalid KQL | Review the query in the KQL editor; check for typos or unsupported operators |
| "Request timed out" | Query too broad | Narrow the time range or add filters to reduce data volume |
| Empty results | Data not yet ingested | Application Insights has a short ingestion delay (typically 2–5 minutes) |

## Copilot issues

| Symptom | Possible cause | Resolution |
|---------|---------------|------------|
| Copilot action not visible | Copilot not enabled | Enable Copilot capabilities in the Business Central admin centre |
| "Copilot is not available" | Missing Copilot setup | Complete the Copilot setup on the AI Telemetry Setup page |
| Poor query quality | Vague prompt | Be more specific — include time ranges, table names, and filters |

## General tips

- Always check the **Telemetry Query Log** for execution details and error
  messages.
- Verify your permissions (see [Permissions](Permissions.md)).
- If issues persist, contact [support@bydynamics.com](mailto:support@bydynamics.com).

---

[← Back to index](index.md) | [Next: Permissions →](Permissions.md)
