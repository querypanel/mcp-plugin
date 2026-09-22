# QueryPanel for Cursor and Grok Bot

Use QueryPanel's official remote MCP server to configure a workspace, connect and document data sources, generate SQL, and build customer-facing charts and dashboards.

The plugin connects to:

```text
https://mcp.querypanel.io/mcp
```

It uses QueryPanel OAuth. Do not configure a database password, private SDK key, tenant identifier, or static API token in Cursor or Grok Bot.

## Install in Cursor

1. Install **QueryPanel** from the Cursor Marketplace.
2. Open the plugin settings and connect to QueryPanel when prompted.
3. Sign in and approve the QueryPanel OAuth consent screen for the workspace you want to use.
4. Start with a prompt such as:

   ```text
   Use QueryPanel to list my datasources, inspect the schema for the selected datasource,
   then generate SQL for monthly active users.
   ```

Cursor discovers the OAuth authorization server from the MCP protected-resource metadata. The plugin does not require variables because credentials are obtained through OAuth.

## Install in Grok Bot

Grok Bot discovers this integration through the Cursor Marketplace listing. Install the same **QueryPanel** plugin, complete the OAuth prompt, and use the same tools and prompts.

## Common prompts

```text
Use QueryPanel init_sdk with mode=headful. Generate a key only if needed,
save the private PEM to my secret manager, then write the embed-token route
and QuerypanelEmbedded page.
```

```text
List my datasources. For the selected datasource, search the schema, generate
SQL for weekly retained users, execute it, and save a chart after I approve it.
```

```text
Show the deployed dashboards in this workspace and summarize the most recent
query sessions.
```

## Security

- QueryPanel validates the OAuth access token before every MCP request.
- The authenticated organization is taken from the server-validated token. Tool arguments cannot select another organization.
- Database credentials and private SDK keys are not returned by list or read tools.
- Tools that create, update, or delete resources are marked with MCP safety annotations. Confirm the intended target before approving a write.
- The MCP endpoint applies a per-instance authenticated request limit. Production also requires an edge rate limit in the hosting provider.

## Support and privacy

- Setup reference: https://querypanel.io/auth.md
- Privacy policy: https://querypanel.io/legal/privacy
- Support: csaba.ivancza@querypanel.io
- License: [MIT](LICENSE)

## Package contents

This repository contains only the Marketplace connector for the hosted QueryPanel MCP server; it does not include the server implementation. The package root includes:

```text
├── .claude-plugin/plugin.json
├── .cursor-plugin/plugin.json
├── .mcp.json
├── assets/querypanel.svg
├── mcp.json
└── README.md
```
