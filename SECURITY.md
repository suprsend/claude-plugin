# Security

## Reporting a vulnerability

Do not open a public issue. Email [security@suprsend.com](mailto:security@suprsend.com) with the details. We answer within 48 hours.

## How the plugin handles access

- The plugin holds no credentials. `.mcp.json` has only the server URL, `https://mcp.suprsend.com/mcp`.
- You sign in with your SuprSend account (OAuth 2.1). Claude stores and renews the login. To revoke it, disconnect the connector (chat, Cowork) or clear the login in `/mcp` (Claude Code).
- The server acts with your account and role. Members get only the read-only tools, and every tool reaches only the workspaces that your account can open.
- Tools that change data or send notifications are marked as such, so Claude asks you before it runs them.
- The skill is text only. It runs no code and makes no calls.
