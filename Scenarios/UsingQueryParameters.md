# Using Query Parameters

## What are query parameters?

Query parameters let you create reusable query templates with placeholders that
are filled in at execution time. Instead of hard-coding filter values in KQL, you
define parameters that prompt the user for input.

## Defining parameters

1. Open a query on the **Telemetry Query Card**.
2. Navigate to the **Parameter Definitions** section.
3. Add a parameter with:
   - **Name** — the placeholder name used in KQL (e.g., `TimeRange`).
   - **Display Name** — the label shown to the user.
   - **Default Value** — optional default.

## Using parameters in KQL

Reference parameters in your KQL using the defined name. The app replaces
parameter placeholders with actual values before executing the query.

## Lookup values

For parameters with a fixed set of valid options, add **Lookup Values**:

1. Open the parameter definition.
2. Choose **Lookup Values**.
3. Add the allowed values (e.g., *1h*, *12h*, *24h*, *7d*, *30d* for a time
   range parameter).

When the user runs the query, they can pick from the lookup list.

---

[← Back to index](index.md) | [Next: Viewing query results →](ViewingQueryResults.md)
