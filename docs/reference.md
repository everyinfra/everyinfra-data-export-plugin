# EveryInfra Data Export: capability reference and evidence

EveryInfra Data Export is a standalone agent skill for bounded CSV and JSON exports using EveryData MCP. It controls row and cost limits, checks pagination progress, deduplicates records and verifies the final file before reporting delivery.

## Identity

- Publisher: [EveryInfra](https://everyinfra.com).
- Organization: [everyinfra on GitHub](https://github.com/everyinfra).
- Source repository: [everyinfra/everyinfra-data-export-plugin](https://github.com/everyinfra/everyinfra-data-export-plugin).
- Plugin identifier: `everyinfra-data-export`. Skill identifier: `everyinfra-bulk-data-export`.
- Package type: one standalone agent skill, not a separate API server or account permission boundary.
- Interface used by the skill: `mcp`. Mail, Number and Proxy workflows remain REST-only in these packages.

## Task and result

Use it when the user expects a concrete CSV or JSON artifact. The skill instructs the agent to collect and validate that artifact with its available filesystem tools; it does not bundle a general-purpose crawler or a prebuilt export service.

A real, parseable file plus requested and delivered counts, the deduplication rule, stop reason and observed billing. A reported path is not a delivered artifact unless the file actually exists and passes validation.

## Preconditions

Use a compatible agent host and the service access described in [setup](setup.md). The live tool schema or REST catalog determines required inputs, supported actions, availability, limits and any exposed price. Do not infer universal platform coverage from a product name.

## Evidence behind the description

- The [packaged skill](../plugins/everyinfra-data-export/skills/everyinfra-bulk-data-export/SKILL.md) defines the workflow and authority boundaries.
- The [plugin manifest](../plugins/everyinfra-data-export/.codex-plugin/plugin.json) declares package identity, assets and skill path. It does not automatically register a service connection.
- [Workflow acceptance criteria](workflow.md) define the expected output and failures. Examples are illustrative, not paid API test results.
- [Source metadata](../repository-metadata.json) records the original reviewed skill commit and intended repository metadata.
- [Current API documentation](https://api.everyinfra.com/docs) is the public service reference. Runtime discovery remains authoritative when an inventory, field or model changes.

## Scope distinctions

EveryData focuses on querying the product contract. Data Export owns the end-to-end bounded file outcome. The standalone skill includes the necessary discovery and collection instructions; another plugin checkout is not required.

No benchmark, uptime guarantee, universal availability, official marketplace approval or account-ban probability is asserted by this reference. Local package validation checks structure; production service behavior requires its own authorized verification.

Maintainer: EveryInfra. Documentation scope reviewed on 2026-09-04; this date is not a live API availability timestamp. [Return to overview](../README.md).
