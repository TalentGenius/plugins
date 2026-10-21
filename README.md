# TalentGenius plugin (dev preview)

Work your approved TalentGenius playbooks one task at a time from ChatGPT or Claude. This repository is a plugin marketplace for testers of the dev build. It is temporary: the production plugin will live in a different repository.

You need an invited TalentGenius account on the dev server.

## Pick your route

| Where you use it | What to install | How |
| --- | --- | --- |
| ChatGPT desktop app | The plugin, from this marketplace | Paste a prompt; by hand as a backup |
| Claude Code (terminal, IDE, or the Code tab of the Claude desktop app) | The plugin, from this marketplace | Paste a prompt; by hand as a backup |
| claude.ai on the web (and the chat tab of the Claude desktop app) | The TalentGenius MCP server only | Add a custom connector by hand |
| ChatGPT on the web (chatgpt.com) | The TalentGenius MCP server only | Add a custom MCP server by hand |

The plugin is the TalentGenius skill plus the MCP server. On the web, pasting a prompt does not work: claude.ai's chat has no tool for it, and on chatgpt.com the prompt builds a plugin that only the desktop app can use. So on the web you add the MCP server by itself, which gives you the tools without the plugin's skill. That is a step down; if you also use a desktop app, install the plugin there too.

In the ChatGPT desktop app, use Codex mode (the dropdown at the top of the sidebar switches between ChatGPT and Codex). In a check on version 1.6.1, Codex mode saw the skill and the tools, the ChatGPT product's Work mode saw the skill but no tools, and its Chat mode saw neither.

## Desktop: install the plugin by prompt

Paste one of these into the app and let it do the work. It may ask you to approve commands.

**ChatGPT desktop app on a Mac:** switch to Codex mode, start a new chat and paste:

```text
Install the "TalentGenius (dev)" plugin from our plugin marketplace on GitHub, TalentGenius/tgdev-plugin-d864a3fd2b. Run these two commands, then tell me in plain words whether it worked and what I still need to do to start using it:
1. /Applications/ChatGPT.app/Contents/Resources/codex-cli/bin/codex plugin marketplace add TalentGenius/tgdev-plugin-d864a3fd2b
2. /Applications/ChatGPT.app/Contents/Resources/codex-cli/bin/codex plugin add talentgenius-dev@talentgenius-preview
```

**ChatGPT desktop app on any system:** in Codex mode, a shorter prompt also worked in testing.

```text
Install the TalentGenius (dev) plugin from the plugin marketplace TalentGenius/tgdev-plugin-d864a3fd2b.
```

**Claude Code:** start a session and paste:

```text
Install the "TalentGenius (dev)" plugin from our plugin marketplace on GitHub. Run these two commands, then tell me in plain words whether it worked and what I still need to do to start using it:
1. claude plugin marketplace add https://github.com/TalentGenius/tgdev-plugin-d864a3fd2b.git
2. claude plugin install talentgenius-dev@talentgenius-preview
```

Then restart Claude Code or run `/reload-plugins`.

Claude Code on the web (claude.ai/code) runs in a temporary cloud container, so an install by prompt there does not last.

### By hand, if the prompt does not work

- **ChatGPT desktop app:** Plugins, Add, Add a marketplace. Type `TalentGenius/tgdev-plugin-d864a3fd2b` in Source and press Add marketplace. Open the Personal tab, find the "TalentGenius (preview)" section and press + on the plugin. If the lists look unchanged, press the refresh button on the Plugins page.
- **Claude Code:** run `/plugin marketplace add https://github.com/TalentGenius/tgdev-plugin-d864a3fd2b.git`, then `/plugin install talentgenius-dev@talentgenius-preview`.
- **ZIP file (ChatGPT desktop app):** download [talentgenius-dev.zip](https://github.com/TalentGenius/tgdev-plugin-d864a3fd2b/releases/latest/download/talentgenius-dev.zip), then Plugins, Add, Upload plugin archive. Choose the ZIP, press Add plugin, then Install plugin. A ZIP copy does not update by itself, so prefer the marketplace.

## After installing the plugin

Sign in to TalentGenius when the app asks. In the ChatGPT desktop app the sign-in button appears under Settings, Integrations, Plugins, MCPs, From plugins (use the plugin in a chat once if the entry is not there yet). Then start a new chat (in Codex mode in the ChatGPT desktop app) and ask "What is my next TalentGenius task?".

## Web: add the MCP server by hand

The server address is `https://mcp-we-dev.talentgenius.dev/mcp`. Both routes may open a TalentGenius sign-in: choose your TalentGenius account and press Allow.

### claude.ai

1. Customize, Connectors, Add, Add custom connector.
2. Name it `TalentGenius (dev)`, paste the address, press Continue, then press Add on the next screen (leave "Sign in now" and "Use Claude's published identity" selected).
3. Press Connect, sign in to TalentGenius and press Allow.
4. Optional: open the connector and set "Read-only tools" to "Always allow", so Claude does not ask before every read.
5. Start a new chat and ask "What is my next TalentGenius task?".

### ChatGPT (chatgpt.com)

1. Plugins, Add, Add custom MCP server.
2. Name it `TalentGenius (dev)`, paste the address as the Server URL, leave Authentication on OAuth, tick "I understand and want to continue" and press Create as a plugin.
3. Press Connect in the dialog that follows. If a TalentGenius sign-in page opens, choose your account and press Allow.
4. In a new chat in Chat or Work mode, type `@TalentGenius`, pick it from the list and ask "What is my next TalentGenius task?".

## Updates

- **ChatGPT desktop app:** the marketplace updates itself when the app starts. Settings, Integrations, Plugins, Marketplace also has an Upgrade button.
- **Claude Code:** auto-update is off by default for marketplaces you add. Turn it on under /plugin, Marketplaces, Enable auto-update, or run `/plugin marketplace update talentgenius-preview`.
- **Web (MCP server):** nothing to update, the connection always uses the current server. If ChatGPT's tool list ever looks stale, open the plugin under Settings, Plugins and press Refresh tools.
- **ZIP copies:** do not update by themselves. In ChatGPT, open the plugin's page on chatgpt.com, choose the ... menu and Upload new version to replace the copy in place. Otherwise remove the ZIP copy and add the marketplace.

## Remove

- **Plugin (desktop):** uninstall it from the app's plugin list, then remove the marketplace. In Claude Code, `claude plugin marketplace remove talentgenius-preview` does both.
- **claude.ai:** Customize, Connectors, TalentGenius (dev), Disconnect, then the ... menu, Remove.
- **ChatGPT web:** Settings, Plugins, TalentGenius (dev), Delete app.
