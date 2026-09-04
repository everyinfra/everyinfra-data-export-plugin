# Install EveryInfra Data Export and configure access

This repository packages one skill, `everyinfra-bulk-data-export`, as a `everyinfra-data-export` plugin. It has no runtime package dependencies or sibling-repository imports. You need a compatible agent host, an EveryInfra account for authenticated operations and the appropriate product scopes. Local packaging validation is not a live service test.

## Install from the GitHub source repository

```bash
codex plugin marketplace add everyinfra/everyinfra-data-export-plugin
codex plugin add everyinfra-data-export@everyinfra-data-export-plugin
```

For Claude Code:

```bash
claude plugin marketplace add everyinfra/everyinfra-data-export-plugin
claude plugin install everyinfra-data-export@everyinfra-data-export-plugin
```

These are source-repository installation paths. An installable repository catalog is distinct from a listing in a host's official marketplace. No account credential or paid API operation is included in installation.

## Local Codex installation

From the root of this checkout, add this repository-local marketplace only if it is not already configured, then install the plugin:

```bash
codex plugin marketplace add .
codex plugin add everyinfra-data-export@everyinfra-data-export-plugin
```

These commands change your own host configuration. Review the plugin and permissions first. Start a new task after installation if the host has not picked up the new skill. The preparation process does not run these commands or replace an existing plugin.

## Local Claude Code installation

From this checkout:

```bash
claude plugin marketplace add .
claude plugin install everyinfra-data-export@everyinfra-data-export-plugin
```

Review the marketplace before installing. The repository also includes a Cursor plugin manifest, but it is not evidence of Cursor marketplace approval or a completed live installation. Follow the current host's supported local plugin import flow.

## Service connection

This is a **skills-only package**: it does not register another remote MCP server, create a credential or alter your account scopes. Several standalone skills can reuse one approved EveryInfra connection. Install only the capabilities you need; installing two skills does not isolate their access to the shared server.

For MCP operations, first inspect your existing host configuration. Reuse a working EveryInfra connection rather than registering duplicates. If none exists, obtain an appropriate API key through your normal account workflow, make `EVERYINFRA_API_KEY` available through your approved secret mechanism, and configure a streamable HTTP connection to `https://api.everyinfra.com/mcp`.

Codex supports this setup command; it references the environment-variable name, not the secret value:

```bash
codex mcp add everyinfra --url https://api.everyinfra.com/mcp --bearer-token-env-var EVERYINFRA_API_KEY
```

For Claude Code or Cursor, configure the same endpoint using that host's supported secret handling. Do not paste real keys into the repository, a chat, a command transcript or a URL. Confirm tool discovery before an authenticated or paid call. Missing tools or denied scopes are setup failures, not permission to expand access.

## Readiness and first use

1. Confirm the host loaded exactly the intended skill.
2. Confirm required tool or REST catalog access without a paid operation.
3. Check current required parameters, availability, account scope and pricing where exposed.
4. Try a discovery-only prompt from the examples.
5. Authorize the exact paid or external action separately when required.

The existing EveryInfra all-in-one plugin can contain the same skill. Prefer either the bundle or the corresponding standalone skill to avoid duplicate instructions; never uninstall an existing package without reviewing what else uses it. Package separation is not a security boundary.

## Publication and compatibility

A public source repository does not establish an official marketplace listing, completed installation in every host or an end-to-end paid API test. Use the GitHub source instructions above, or the local checkout instructions for development. See the root release checklist before publishing a tagged release or archive.
