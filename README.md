# TalentGenius plugins

This repository is the plugin marketplace of TalentGenius, Inc. ([talentgenius.io](https://talentgenius.io)). It is published by the TalentGenius organization on GitHub, which is verified for talentgenius.io. The address to install from is <https://github.com/TalentGenius/plugins>.

The plugin lets you work your approved TalentGenius playbooks one task at a time from ChatGPT or Claude. The plugin is `talentgenius`.

Accounts are invite-only. If a sign-in ends with access denied, your email has not been invited yet.

**Easiest:** sign in to <https://app.talentgenius.io/plugin>, pick your app and follow the page. The sections below say the same thing.

## Claude desktop app, Code tab (Mac, Windows, Linux): recommended

In the Claude desktop app's Code tab, start a new session in any folder, type `run this` and paste this under it. It installs the plugin, opens your browser to sign in (sign in to TalentGenius and press Allow) and starts a session that is ready to use.

```text
Set up TalentGenius for me, so I can work my TalentGenius playbooks here. TalentGenius/plugins (https://github.com/TalentGenius/plugins) is the plugin marketplace of TalentGenius, Inc., published by its GitHub organization, which GitHub shows as verified for talentgenius.io. Do these in order:

1. Run: "${CLAUDE_CODE_EXECPATH:-claude}" plugin install talentgenius --marketplace TalentGenius/plugins --scope user
   If a permission or safety check blocks it, tell me so in one line and ask me once whether to install the talentgenius plugin from github.com/TalentGenius/plugins; when I say yes, run it again. If it says the option or command is unknown, tell me to update the Claude app and stop. If an organization or managed-settings policy refuses it, tell me my Claude admin has to allow the TalentGenius marketplace and stop.

2. Sign me in. The terminal pane does not have CLAUDE_CODE_EXECPATH, so first get your own full path by running echo "$CLAUDE_CODE_EXECPATH" in your shell (if it is empty, use claude). Then, in the terminal pane, run that path in quotes, followed by: mcp login plugin:talentgenius:talentgenius
   In PowerShell, put & before the quoted path.
   It opens my browser; if it does not, show me the link it prints. Tell me to sign in to TalentGenius and press Allow, then wait until it prints "Authenticated". If it ends with access denied, tell me my email has to be invited to TalentGenius first and stop. If the login command fails any other way, tell me to type /mcp in this chat, pick TalentGenius, sign in and press Allow.

3. Start a new session for me whose first message is "Show me my TalentGenius playbooks", and tell me to open it. If you cannot start one, tell me to open a new session and type that.
```

By hand: `/plugin marketplace add https://github.com/TalentGenius/plugins.git`, then `/plugin install talentgenius@talentgenius-preview`, then `/mcp` to sign in.

## ChatGPT desktop app (Mac, Windows): recommended

Switch to **Codex mode** (the dropdown at the top of the sidebar); Chat and Work modes do not see the tools. Start a new chat, paste this and approve its commands if it asks:

```text
Install the TalentGenius plugin from GitHub. It is not in the ChatGPT plugin directory, so do not search there. Do these in order:
1. Run: codex plugin marketplace add TalentGenius/plugins
2. Run: codex plugin add talentgenius@talentgenius-preview
3. Connect to my TalentGenius playbooks.
If the codex command is not found, add the plugin marketplace TalentGenius/plugins from GitHub and install talentgenius with your plugin tools instead.
```

If it asks you to sign in, sign in to TalentGenius and press **Allow**. If it says TalentGenius is not connected, open Settings, Integrations, Plugins, MCPs, From plugins, press **Authenticate** next to TalentGenius, sign in and press **Allow**, then ask "Connect to my TalentGenius playbooks" in a new chat.

By hand: Plugins, Add, Add a marketplace, type `TalentGenius/plugins` and press Add marketplace. On the Personal tab, in the "TalentGenius (preview)" section, press + on the plugin.

## Claude on the web, in Chat or Cowork, or on your phone

Add it to your Claude account once and it works wherever you use that account.

1. Customize, Connectors, Add, Add custom connector. Name it `TalentGenius`, paste `https://mcp.talentgenius.io/mcp` and press Continue.
2. Under Authentication choose **Sign in when needed**, then press Add.
3. In a new chat ask "Connect to my TalentGenius playbooks". Press **Connect** on the card Claude shows, sign in to TalentGenius and press **Allow**, then ask again.

On a Team or Enterprise plan an Owner adds the connector for the organization (Organization settings, Connectors), and members connect with their own account.

## ChatGPT website (chatgpt.com)

The website cannot install plugins, so add the server by itself. You get the tools without the guide.

1. Plugins, Add, Add custom MCP server.
2. Name it `TalentGenius`, paste `https://mcp.talentgenius.io/mcp` as the Server URL, leave Authentication on OAuth, tick "I understand and want to continue" and press Create as a plugin.
3. Press Connect, sign in to TalentGenius and press **Allow**.
4. In a new chat type `@TalentGenius`, pick it and ask "Connect to my TalentGenius playbooks".

## ZIP, if the marketplace is blocked (ChatGPT desktop app)

Download [talentgenius.zip](https://github.com/TalentGenius/plugins/releases/latest/download/talentgenius.zip), then Plugins, Add, Upload plugin archive, Add plugin, Install plugin. A ZIP copy does not update by itself.

## Updates and removal

- **Updates:** the ChatGPT desktop app updates the marketplace when it starts. Claude Code does not by default: run `/plugin marketplace update talentgenius-preview`, or turn on auto-update under /plugin, Marketplaces.
- **Remove the plugin:** uninstall it from the app's plugin list, then remove the marketplace. In Claude Code, `claude plugin marketplace remove talentgenius-preview` does both.
- **Remove the connector (Claude):** Customize, Connectors, TalentGenius, Disconnect, then the ... menu, Remove.
- **Remove the server (chatgpt.com):** Settings, Plugins, TalentGenius, Delete app.
