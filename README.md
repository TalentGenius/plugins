# TalentGenius plugin (dev preview)

Work your approved TalentGenius playbooks one task at a time from ChatGPT or Claude. This repository is a plugin marketplace for testers of the dev build. It is temporary: the production plugin will live in a different repository.

You need an invited TalentGenius account on the dev server.

## Where it works

| App | Prompt (automated) | Marketplace by hand | ZIP file |
| --- | --- | --- | --- |
| ChatGPT desktop app | Works | Works | Works |
| Claude Code (terminal, IDE, desktop Code tab) | Works | Works | Not applicable |
| claude.ai on the web and the Claude desktop app (chat) | Not possible, a chat cannot install plugins | Works | Works |
| ChatGPT on the web | Not possible | Not offered, the web page has no Add marketplace | Uploads, but the plugin is desktop-only |

The plugin cannot be installed from ChatGPT's website. Use the ChatGPT desktop app, or Claude.

## Install by prompt (automated)

Paste one of these into the app and let it do the work. It may ask you to approve commands.

**ChatGPT desktop app on a Mac:** start a new chat and paste:

```text
Install the "TalentGenius (dev)" plugin from our plugin marketplace on GitHub, TalentGenius/tgdev-plugin-d864a3fd2b. Run these two commands, then tell me in plain words whether it worked and what I still need to do to start using it:
1. /Applications/ChatGPT.app/Contents/Resources/codex-cli/bin/codex plugin marketplace add TalentGenius/tgdev-plugin-d864a3fd2b
2. /Applications/ChatGPT.app/Contents/Resources/codex-cli/bin/codex plugin add talentgenius-dev@talentgenius-preview
```

**ChatGPT desktop app on any system:** a shorter prompt also worked in testing.

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

## Install by hand

### Add the marketplace

- **ChatGPT desktop app:** Plugins, Add, Add a marketplace. Type `TalentGenius/tgdev-plugin-d864a3fd2b` in Source and press Add marketplace. Open the Personal tab, find the "TalentGenius (preview)" section and press + on the plugin. If the lists look unchanged, press the refresh button on the Plugins page.
- **Claude Code:** run `/plugin marketplace add https://github.com/TalentGenius/tgdev-plugin-d864a3fd2b.git`, then `/plugin install talentgenius-dev@talentgenius-preview`.
- **claude.ai on the web or the Claude desktop app:** Customize, Plugins, Add, Add marketplace, Add from a repository. Enter `TalentGenius/tgdev-plugin-d864a3fd2b` and press Sync. Leave "Sync automatically" on, so claude.ai keeps the plugin current. Add the plugin from the Discover list, then open its Connectors tab: if the TalentGenius connector is not Connected yet, connect it and sign in.

### Use the ZIP file

Download [talentgenius-dev.zip](https://github.com/TalentGenius/tgdev-plugin-d864a3fd2b/releases/latest/download/talentgenius-dev.zip). A ZIP copy does not update by itself, so prefer the marketplace when you can.

- **ChatGPT desktop app:** Plugins, Add, Upload plugin archive. Choose the ZIP, press Add plugin, then Install plugin.
- **claude.ai on the web or the Claude desktop app:** Customize, Plugins, Add, Upload plugin. Choose the ZIP, then open the plugin's Connectors tab, connect and sign in.

## After installing

Sign in to TalentGenius when the app asks. In the ChatGPT desktop app the sign-in button appears under Settings, Integrations, Plugins, MCPs, From plugins (use the plugin in a chat once if the entry is not there yet). Then start a new chat and ask "What is my next TalentGenius task?".

## Updates

- **ChatGPT desktop app:** the marketplace updates itself when the app starts. Settings, Integrations, Plugins, Marketplace also has an Upgrade button.
- **claude.ai:** updates arrive automatically while "Sync automatically" is on, or press Check for updates on the marketplace.
- **Claude Code:** auto-update is off by default for marketplaces you add. Turn it on under /plugin, Marketplaces, Enable auto-update, or run `/plugin marketplace update talentgenius-preview`.
- **ZIP copies:** do not update by themselves. In ChatGPT, open the plugin's page on chatgpt.com, choose the ... menu and Upload new version to replace the copy in place. Otherwise remove the ZIP copy and add the marketplace.

## Remove

Uninstall the plugin from the app's plugin list, then remove the marketplace. In Claude Code, `claude plugin marketplace remove talentgenius-preview` does both.
