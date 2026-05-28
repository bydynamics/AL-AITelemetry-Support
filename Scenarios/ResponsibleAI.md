# Responsible AI: AI Telemetry Copilot Features

> **Last updated**: May 2026
> **Applies to**: AI Telemetry for Microsoft Dynamics 365 Business Central

---

## What is AI Telemetry's Copilot feature?

AI Telemetry includes a Copilot-powered feature that generates KQL (Kusto Query
Language) queries from natural language descriptions. Users describe what
telemetry data they want to find, and Copilot translates that description into a
KQL query that can be executed against Azure Application Insights.

## What can it do?

- Generate new KQL queries from a natural language prompt.
- Refine existing KQL queries based on a natural language instruction (e.g.,
  "add a filter for the last 7 days").
- Generate parameter lookup values for parameterized queries.

## What is it intended for?

The feature is intended to help Business Central administrators, consultants, and
developers write KQL queries faster — especially users who are not fluent in KQL
syntax. It lowers the barrier to telemetry analysis by letting users express
their intent in everyday language.

## What are its limitations?

- **Queries may be incorrect or suboptimal.** The AI model generates KQL based on
  pattern matching and training data. It may produce queries with syntax errors,
  logical mistakes, or inefficient patterns.
- **No guaranteed accuracy.** The model does not execute or validate queries. It
  does not have access to your actual data schema or table contents at generation
  time.
- **Business Central telemetry knowledge is based on training data.** The model's
  knowledge of BC-specific event IDs, custom dimensions, and telemetry structure
  may be incomplete or outdated.
- **Complex queries may require manual refinement.** Multi-step analytical
  queries, advanced aggregations, or uncommon telemetry signals may need manual
  editing after generation.
- **Natural language ambiguity.** Vague or ambiguous prompts may produce
  unexpected queries. More specific prompts yield better results.

## What data does the AI process?

| Data sent to the AI model | Data NOT sent |
|---------------------------|---------------|
| Your natural language prompt text | Your telemetry data |
| The current KQL query (when refining) | Your Application Insights connection credentials |
| Query parameter names and definitions | Query results or row-level data |
| | User names, customer data, or business data |

The AI model receives only the prompt and query context needed to generate KQL.
No telemetry data, credentials, or business data leaves your environment.

## How does the AI model work?

AI Telemetry uses the Azure OpenAI Service through Business Central's built-in
Copilot platform (the AL `PromptDialog` framework). The system prompt instructs
the model about:

- Available Application Insights tables and their schemas.
- Common Business Central telemetry event IDs and custom dimensions.
- KQL best practices and output formatting rules.

The model generates a KQL query string as its response, which is then presented
to the user for review.

## Human oversight and control

- **Review before execution.** Generated queries are always shown to the user
  before execution. The user must explicitly choose to accept and run the query.
- **Edit capability.** Users can freely edit any generated query in the KQL
  editor before executing it.
- **Discard option.** Users can discard a generated query at any time without
  side effects.
- **No automatic execution.** Copilot never executes queries automatically. A
  human decision is always required.
- **Read-only queries.** The app only executes read queries against Application
  Insights. It cannot modify or delete telemetry data.

## Best practices for users

1. **Always review generated queries** before executing — check that the tables,
   filters, and time ranges make sense.
2. **Be specific in your prompts** — include time ranges, table names, and filter
   criteria when possible.
3. **Start with small time ranges** — use "last 1 hour" or "last 24 hours"
   before querying longer periods to avoid timeouts.
4. **Iterate** — if the first result isn't right, use the refinement feature to
   adjust rather than starting over.
5. **Validate against known data** — when testing a new query, cross-check
   results with the Azure portal to confirm correctness.

## Reporting issues

If you encounter a Copilot-generated query that is clearly wrong, misleading, or
produces harmful output, please report it:

- **Email:** [support@bydynamics.com](mailto:support@bydynamics.com)
- **GitHub Issues:** [AL-AITelemetry-Support](https://github.com/bydynamics/AL-AITelemetry-Support/issues)

Include the prompt you used and the generated query so we can improve the system.

---

[← Back to index](index.md)
