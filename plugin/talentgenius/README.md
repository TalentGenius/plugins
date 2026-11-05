# TalentGenius

TalentGenius turns a goal into a playbook: a plan of tasks, each with steps for you, for AI, or for a sign-off. This plugin lets you work a playbook you already have inside your AI assistant. It walks you through one task at a time, shows the prompt for each AI step, runs it when you say yes, and saves your progress so you can pick up later.

## Install

In Claude Code, run:

```text
/plugin install talentgenius --marketplace TalentGenius/plugins
```

Then run `/mcp`, pick TalentGenius, and sign in with your TalentGenius account.

## Try it

- "Connect to my TalentGenius playbooks."
- "What is my next TalentGenius task?"
- "Show me my TalentGenius playbooks."

## How it connects

Claude connects directly through the package's `.mcp.json`. OpenAI desktop and Codex connect to the same endpoint through the package's portable MCP configuration. Each person signs in with their own TalentGenius account through OAuth; the assistant holds the sign-in token, not the plugin. The package contains no account-specific app binding. Everything runs on TalentGenius servers. The plugin contains no local code, no hooks and no scripts.

The endpoint is `https://mcp.talentgenius.io/mcp`.

## What data is sent

Only what you ask about your playbooks. Your requests, such as listing your playbooks, opening the current task, or marking a task done, go to the TalentGenius server, and so do the notes you choose to save. When a task needs one of your documents, its contents are returned by the server to your AI assistant for that conversation; nothing is uploaded from your machine.

## Access

Accounts are invite-only at launch. If your email is not on the list you will see a waitlist page, and the sign-in will be declined. New playbooks are created on the web at <https://app.talentgenius.io/new>.

## Privacy and support

- Privacy policy: <https://talentgenius.io/legal/privacy-policy>
- Terms: <https://talentgenius.io/legal/terms-conditions>
- Support: <https://talentgenius.io/contact> or <support@talentgenius.io>
