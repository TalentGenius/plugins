# Changelog

## 1.6.3 - 2026-10-21

- A sign-in tool may be offered whether or not the person is signed in, so the skill no longer reads its presence as "not signed in": it calls the tool when a data tool is refused for want of sign-in or when no data tool is offered at all (a signed-out connection shows only `get_rules` and the sign-in tool), carries on if the tool answers with the account email, and otherwise tells the person to repeat their request once the sign-in is done, because the chat does not continue by itself after the sign-in window closes.
- The connector gains a `sign_in` tool and answers before sign-in with `get_rules` and `sign_in` only, so an app that can sign a person in from inside the chat lists the connector straight away. The skill still uses the same seven tools, and the MCP connection is unchanged.

## 1.6.2 - 2026-10-21

- The skill now starts on "TG" as well as "TalentGenius", for example "What is my next TG task?".
- When no TalentGenius tool is offered, the skill gives the way to sign in for the app in use: the plugin's page in Claude's apps, `/mcp` in an agent that signs in to servers that way, and Settings, Integrations, Plugins, MCPs, From plugins, Authenticate in Codex and the ChatGPT desktop app. The add link stays as the fallback, and the 1.6.1 order is unchanged.
- A refused `save_notes` write now has its own rule, because saving notes replaces them. The skill reads the task again, saves the notes once more only if the saved notes are the ones it last saw, and otherwise tells the person what they say now and asks whether to replace them or add to them. A retry that is refused again starts over and is never reported as saved, for notes and for task updates alike.
- The skill's "returned content" rule names `get_rules`, the connector's copy of the same working rules, as the other exception to treating what a tool returns as data. The skill does not need it, so a conversation may skip it.
- Removes the `$schema` line from Claude's plugin manifest, which claude.ai strips with a warning when it syncs the plugin.
- The seven tools and the MCP connection are unchanged on every host.

## 1.6.1 - 2026-10-20

- When no TalentGenius tool is offered, the skill now says how to connect in that app: open the plugin's page (for example Customize, then Plugins, then the plugin, then its Connectors tab), choose Connect (or Add) next to TalentGenius, press Continue, then Add, then Connect again if the app asks you to confirm first, sign in and approve, then ask again; if that button is missing or does not work, the add link shows the other ways to connect. Before, it gave only the add link.
- The seven tools, the rest of the skill and the MCP connection are unchanged on every host. The package still leaves OpenAI's optional sign-in block out of `mcp.json`, because Codex rejects any `extensions` key there and drops the server.

## 1.6.0 - 2026-10-13

- Prepares the package for OpenAI's plugin directory: support, privacy and terms links, the TalentGenius favicon as a light and dark icon, the brand color, three starter prompts and a fuller listing description.
- Carries the review test cases (five that should work, three the plugin should decline) and release notes, so they import with the upload. Reviewer sign-in details stay out of the package.
- The MCP connection, sign-in and the shared skill are unchanged on every host.

## 1.5.4 - 2026-10-13

- Removes the private OpenAI app binding from the dev package so recipients can install the same ZIP with their own TalentGenius account.
- Restores direct MCP on OpenAI desktop and Codex for every stage. OpenAI ZIP imports are desktop-only; ChatGPT web can connect to the MCP server separately without the packaged skill.
- Keeps Claude's MCP connection configuration and the shared skill unchanged. Version 1.5.3 remains the earlier account-bound web-capable package.
- Corrects the Codex compatibility manifest MCP path so its native loader does not ignore the configuration with a manifest warning.

## 1.5.3 - 2026-10-13

- The dev package includes the verified registered ChatGPT app and the existing skill in the same archive used by Claude.
- OpenAI uses the registered dev app's OAuth connection, without starting a second direct MCP connection. Claude retains its direct MCP configuration.
- Test and production builds do not inherit the private dev app binding.

## 1.5.0 - 2026-10-13

- Adds portable and Codex plugin manifests so the same package carries the TalentGenius skill and remote MCP connection across supported OpenAI and Claude hosts.
- Adds a repo marketplace for Codex and local ChatGPT Work installation, and documents private account installation for ChatGPT.
- Keeps the seven tools and playbook workflow unchanged.

## 1.4.0 - 2026-10-12

- Moving on from a task marks it done and says so in one line. Say "later" to keep it open.
- A task with a sign-off waits for the person's word that it was signed off before it is marked done.
- When a save is refused because the plan changed, the skill re-reads the task, saves once if the task is still open, and explains what changed. If the task itself changed, it asks first.
- If TalentGenius is not connected, the skill offers a sign-in when one is available, and otherwise gives a link to add TalentGenius.
- Instructions found inside documents are reported to the person and not followed.
- The skill also starts on "next" and "move on", and when someone asks for a document TalentGenius holds.

## 0.1.0 - 2026-09-30

- First private build.
- A short skill for working an existing playbook one task at a time.
- Connects to the TalentGenius server with OAuth sign-in.
