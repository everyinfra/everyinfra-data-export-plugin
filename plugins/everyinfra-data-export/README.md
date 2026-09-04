# EveryInfra Data Export plugin

Export supported public data to CSV or JSON with EveryData MCP. Bound rows and cost, track pagination, deduplicate by stable keys and validate the delivered file.

This package contains only `everyinfra-bulk-data-export`. It is a skills-only plugin: configure the approved EveryInfra service connection in the host before using it. It does not install other skills, register a new MCP server or broaden API permissions.

A real, parseable file plus requested and delivered counts, the deduplication rule, stop reason and observed billing. A reported path is not a delivered artifact unless the file actually exists and passes validation.

- No unlimited export, full-platform coverage or unbounded retry promise.
- Do not retry authorization, parameter, inventory or balance failures as transient errors.
- Do not silently fuzzy-deduplicate distinct records or flatten nested JSON without agreement.

Repository documentation and installation guidance accompany the source checkout. Current API documentation: https://api.everyinfra.com/docs
