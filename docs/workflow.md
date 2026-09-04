# EveryInfra Data Export workflow and acceptance criteria

## Intended outcome

A real, parseable file plus requested and delivered counts, the deduplication rule, stop reason and observed billing. A reported path is not a delivered artifact unless the file actually exists and passes validation.

## Execution contract

1. Confirm source, requested rows, selected fields, output format, destination and time or cost ceiling.
2. Discover the action schema with everyinfra_list_capabilities, including pagination and max_limit.
3. Estimate calls where the contract allows; obtain approval before material spending.
4. Use everyinfra_call_api with bounded retries and stop when the target, budget, final page or a non-advancing cursor is reached.
5. Deduplicate using a stable ID or a documented composite key; write the selected fields.
6. Verify file existence, non-empty content, parseability and actual row counts. Report requested versus delivered rows and all truncation causes.

## Failure handling

If discovery or catalog access fails, stop before a paid action. Read required fields from the current schema instead of copying a remembered payload. Report unavailable capabilities and denied account scopes as distinct conditions. Do not broaden keys, repeatedly retry a permanent error or substitute an unrelated mechanism without disclosure.

- No unlimited export, full-platform coverage or unbounded retry promise.
- Do not retry authorization, parameter, inventory or balance failures as transient errors.
- Do not silently fuzzy-deduplicate distinct records or flatten nested JSON without agreement.

## Worked request boundaries

### Scenario 1

> Plan a CSV export of up to the row limit I specify. Inspect supported fields, pagination and estimated calls before collecting data.

Accepted behavior: preserve the stated scope; discover the required contract and stop at the explicit no-action boundary. Any broader operation requires new authority.

### Scenario 2

> Export the approved records as JSON, preserving nested fields. Stop on a repeated cursor and report the partial result.

Accepted behavior: preserve the stated scope; discover the required contract and stop at the explicit no-action boundary. Any broader operation requires new authority.

### Scenario 3

> Check the resulting CSV for stable headers, duplicate keys and actual row count. Do not say the export is complete unless the file parses.

Accepted behavior: preserve the stated scope; discover the required contract and stop at the explicit no-action boundary. Any broader operation requires new authority.


These are illustrative prompts, not captured API responses or claims of successful live execution. They deliberately avoid guessed JSON payloads and fabricated prices. See [prompt acceptance fixtures](../examples/acceptance.json) for the offline safety assertions.

## Result review

A real, parseable file plus requested and delivered counts, the deduplication rule, stop reason and observed billing. A reported path is not a delivered artifact unless the file actually exists and passes validation.

Check original results rather than relying on the agent's summary alone. Preserve response status and evidence only to the extent safe; redact personal or secret fields. If billing is absent from the response, say it is not observable there rather than inferring a charge from HTTP success.

## Related decision

EveryData focuses on querying the product contract. Data Export owns the end-to-end bounded file outcome. The standalone skill includes the necessary discovery and collection instructions; another plugin checkout is not required.

Return to [README](../README.md) or [setup](setup.md).
