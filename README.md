# Treeno memory for AI agents

Gives your AI agent a long-term memory that lives in your [Treeno](https://treeno.org) notes.
The agent keeps a short journal of your conversations, remembers facts about you, decisions,
important details and to-dos, and looks them up in later conversations. You can read and edit
all of it in the Treeno app (web, iOS, desktop) in the **🧠 AI memory** folder.

One repository, one plugin (`plugins/treeno`) for **Claude Code**, **ChatGPT** and **Codex**.

## Install

### Claude Code

```
/plugin marketplace add fivol/treeno-agent-plugin
/plugin install treeno@treeno
```

Restart Claude Code, run `/mcp`, choose **treeno** and sign in.

### ChatGPT

Settings → **Plugins** → **Add** → **Add a marketplace** → `fivol/treeno-agent-plugin`,
then install **Treeno memory** and sign in.

### Codex

```
codex plugin marketplace add fivol/treeno-agent-plugin
```

Then install **Treeno memory** from the plugin list and sign in.

On the Treeno consent screen pick **AI memory folder only** — the agent then sees nothing
but that folder.

## What it adds

- **MCP server** `treeno` (`https://api.treeno.org/mcp`, OAuth) with the memory tools
  `memory_context`, `memory_search`, `memory_write`, plus the regular Treeno tree tools.
- **Skill** `treeno-memory` telling the agent when to load, search and save memory.
- **SessionStart hook** (Claude Code and Codex) that reminds the agent to load its memory
  at the start of every session.

The rules for what gets saved (and what never is, like passwords and tokens) are served by
the Treeno server, so they improve without updating the plugin. Add your own rules in the
**📖 Rules for the agent** section of the memory folder — the agent follows them.

## Memory folder

```
🧠 AI memory
├─ 📖 Rules for the agent   your instructions for the agent
├─ 👤 About me              stable facts and preferences
├─ 🗂 Topics                decisions (📌) and notes per project or area
├─ 📓 Journal               one entry per meaningful conversation, by date
└─ ✅ To remember           commitments and deadlines
```

## Without the plugin

claude.ai, the Claude desktop and mobile apps, Cursor and other MCP clients connect to the same
server (`https://api.treeno.org/mcp`): in Treeno open **Access → AI agent** for step-by-step
setup and a ready prompt.

## Layout

```
.claude-plugin/marketplace.json   Claude Code marketplace
.agents/plugins/marketplace.json  ChatGPT / Codex marketplace
plugins/treeno/
├─ .claude-plugin/plugin.json     Claude Code manifest
├─ .mcp.json                      Claude Code MCP config
├─ plugin.json                    ChatGPT / Codex manifest (agent-plugins.org schema)
├─ mcp.json                       ChatGPT / Codex MCP config
├─ skills/treeno-memory/SKILL.md  shared skill
├─ hooks/hooks.json               shared SessionStart hook
└─ assets/logo.png
```

## Uninstall

Claude Code: `/plugin uninstall treeno@treeno`. ChatGPT / Codex: remove the plugin in the
plugin list. You can also disconnect the agent in Treeno under **Access → AI agent**.
