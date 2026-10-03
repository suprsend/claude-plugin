# CLAUDE.md

This repo is the SuprSend plugin for Claude (chat on the web, desktop, and mobile, Cowork, and Claude Code). Its sibling, [`suprsend/agent-plugin`](https://github.com/suprsend/agent-plugin), is the same plugin in the Agent Plugins format for other clients. Keep the two in step: the skill text (`skills/suprsend/SKILL.md`) is the same file in both repos.

## Layout

| Path                              | Role                                                                                                                       |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `.claude-plugin/plugin.json`      | The plugin manifest (`name: suprsend`). The version is set here only, not in `marketplace.json`.                           |
| `.claude-plugin/marketplace.json` | The marketplace `suprsend` with one plugin, `source: "./"`.                                                                |
| `.mcp.json`                       | The hosted server, `{"type": "http", "url": "https://mcp.suprsend.com/mcp"}`. No auth fields: Claude finds OAuth itself.   |
| `skills/suprsend/SKILL.md`        | The one skill. The detailed skills stay on the server (`skill://` resources and `docs.get_skill`); do not copy them here.                          |

## Rules

- **No `bin/` folder and no stdio server.** Both block or break the plugin in chat on claude.ai and in Cowork.
- **No `${user_config.*}` in the server URL.** Chat ignores such a server.
- **Skill text is neutral and current.** It names only tools that the production server has. When the server adds, renames, or removes a tool that the skill names, change the skill in both repos.
- **Version:** raise `version` in `plugin.json` for every change that users must get. Claude updates a plugin only when its version changes.
- Check with `claude plugin validate .` before you push.
- Never add AI attribution to commits or pull requests.
