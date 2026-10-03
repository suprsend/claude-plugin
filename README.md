# SuprSend plugin for Claude

The official [SuprSend](https://suprsend.com) plugin for Claude: chat on the web, desktop, and mobile, Cowork, and Claude Code. It connects Claude to the **hosted SuprSend MCP server** and adds a skill that tells Claude how to use it. Claude can then work with your SuprSend account: users and their preferences, tenants, objects, subscriber lists, workflows, templates, events, and delivery data.

For VS Code, GitHub Copilot, Cursor, ChatGPT and Codex, Kiro, and the other [Agent Plugins](https://agent-plugins.org) clients, use [`suprsend/agent-plugin`](https://github.com/suprsend/agent-plugin).

## What you get

| Part           | What it does                                                                                                                                                                                                                            |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **MCP server** | `https://mcp.suprsend.com/mcp`, hosted by SuprSend: tools for users, objects, tenants, lists, preferences, events, schemas, workflows, templates, translations, messages, and delivery data (read-only SQL). Nothing runs on your computer. |
| **Skill**      | `suprsend`: when to use which tool, and to read the detailed SuprSend skill (workflow JSON, template content, SQL tables) from the server, directly or with `docs.get_skill`, before Claude writes one.                                                  |

You need no API key: you sign in with your SuprSend account (OAuth). Admins get every tool; members get the read-only tools. Claude sees only the workspaces that your account can open.

## Install

### Claude on the web, desktop, or mobile, and Cowork

1. Open **Customize → Plugins → Add → Add marketplace**, and enter `suprsend/claude-plugin`.
2. Install the **suprsend** plugin.
3. Open the plugin's **Connectors** tab, and connect **suprsend**. Sign in with your SuprSend account.

On Team and Enterprise plans, an owner may need to allow the connector first.

### Claude Code

```
/plugin marketplace add suprsend/claude-plugin
/plugin install suprsend@suprsend
```

Then sign in once: run `/mcp`, select **suprsend**, and choose **Authenticate**. A plugin that you install on claude.ai also appears in Claude Code as a synced plugin.

## Examples

```
List my SuprSend workspaces.
Why did user u_42 not get the "order-confirmed" email yesterday?
How many emails did we send per day last week, in production?
Opt user u_42 out of the newsletter category and stop SMS for them.
Make the static list beta-testers exactly the users in this CSV.
Create a workflow that sends the "welcome" email when the event USER_SIGNUP comes in.
```

## Limit the scope

To fix one workspace or a set of tools, connect a custom URL instead of the plugin's default:

- `https://mcp.suprsend.com/mcp/staging`: only the `staging` workspace.
- `https://mcp.suprsend.com/mcp?tools=users.*,lists.*`: only these tool groups.

## Support

- Docs: https://docs.suprsend.com
- Email: support@suprsend.com
- Security: see [SECURITY.md](SECURITY.md)

## Moving from `suprsend/claude-code-plugin`

This repo replaces [`suprsend/claude-code-plugin`](https://github.com/suprsend/claude-code-plugin). The old marketplace forwards to this plugin, so `/plugin marketplace update suprsend-marketplace` moves you here. For a clean setup, remove the old marketplace and add `suprsend/claude-plugin`.

## License

[MIT](LICENSE)
