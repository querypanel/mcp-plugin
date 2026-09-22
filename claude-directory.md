# Claude Connectors Directory submission

This file is the source copy and reviewer checklist for the remote QueryPanel MCP listing. Submit it through the Claude.ai organization portal. Claude does not accept a repository manifest for a remote connector.

## Connection

- Server URL: `https://mcp.querypanel.io/mcp`
- Transport: Streamable HTTP
- Connection type: Universal URL
- Authentication: OAuth 2.0 with dynamic client registration
- Protected resource metadata: `https://mcp.querypanel.io/.well-known/oauth-protected-resource/mcp`

## Listing

- Name: QueryPanel
- Tagline: Build tenant-safe analytics with your AI agent
- Slug: `querypanel`
- Categories: Developer Tools, Data and Analytics
- Documentation: https://querypanel.io/auth.md
- Privacy policy: https://querypanel.io/legal/privacy
- Support: csaba.ivancza@querypanel.io
- Company: QueryPanel
- Website: https://querypanel.io
- Icon: `assets/querypanel.svg`

### Description

QueryPanel lets your AI agent configure analytics for a SaaS product without bypassing your workspace permissions. Connect data sources, inspect schema context, generate and execute SQL, train business knowledge, and create charts or dashboards through one OAuth-protected MCP server.

The connector is designed for product and engineering teams building customer-facing analytics. Use `init_sdk` to scaffold QueryPanel's headful embed or headless Node SDK, then use the schema and chart tools to build analytics workflows. The server takes the workspace identity from the validated OAuth token, so tool arguments cannot switch organizations. Database credentials and private SDK keys are never returned by read tools.

## Use cases and data handling

- Configure an existing QueryPanel workspace and scaffold an SDK integration.
- Inspect schema metadata, generate SQL, and create charts or dashboards.
- Maintain data sources, schema knowledge, signing keys, and workspace members after explicit user approval.
- The connector reads and writes QueryPanel's first-party API on behalf of the OAuth user. It does not collect payment data or health data.
- It processes QueryPanel account, organization, schema metadata, query, and analytics configuration data. Database credentials are write-only and are not returned by list or read tools.

## Reviewer test instructions

Provide a dedicated QueryPanel reviewer account that belongs to a populated test organization before submission. Include the account email, password or SSO invitation instructions, organization name, and a sample datasource with non-sensitive data in the portal.

After connecting the reviewer account:

1. Run `list_datasources`.
2. Run `search_schema` with a datasource ID and a sample analytics question.
3. Run `generate_sql` with returned context chunks.
4. Run `execute_sql` with the generated SQL only after confirming the datasource is read-only or uses non-sensitive test data.
5. Run `list_charts` and `list_dashboards`.
6. Run every remaining tool with a dedicated disposable test resource where the tool writes or deletes state.

## Submission checklist

- Verify production `/health`, OAuth metadata, and Streamable HTTP transport.
- Verify every tool exposes a title and safety annotations in MCP Inspector.
- Run every tool end to end with the reviewer account.
- Complete the portal's data-handling, policy, and seven compliance acknowledgments.
- Monitor the submission dashboard and answer review feedback. Escalate delayed reviews to `mcp-review@anthropic.com`.
