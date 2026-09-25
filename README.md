# Treeno memory for Claude Code

Gives Claude Code a long-term memory that lives in your [Treeno](https://treeno.org) notes.
Claude keeps a short journal of your sessions, remembers facts about you, decisions,
important details and to-dos, and looks them up in later sessions. You can read and edit
all of it in the Treeno app (web, iOS, desktop) in the **🧠 AI memory** folder.

## Install

In Claude Code:

```
/plugin marketplace add fivol/treeno-claude-plugin
/plugin install treeno@treeno
```

Restart Claude Code, run `/mcp`, choose **treeno** and sign in. On the Treeno consent
screen pick **AI memory folder only** — Claude then sees nothing but that folder.

## What it adds

- **MCP server** `treeno` (`https://api.treeno.org/mcp`, OAuth) with the memory tools
  `memory_context`, `memory_search`, `memory_write`, plus the regular Treeno tree tools.
- **SessionStart hook** that reminds Claude to load its memory at the start of every
  session.

The rules for what gets saved (and what never does, like passwords and tokens) are served
by the Treeno server, so they improve without updating the plugin. Add your own rules in
the **📖 Rules for the agent** section of the memory folder — Claude follows them.

## Memory folder

```
🧠 AI memory
├─ 📖 Rules for the agent   your instructions for Claude
├─ 👤 About me              stable facts and preferences
├─ 🗂 Topics                decisions (📌) and notes per project or area
├─ 📓 Journal               one entry per meaningful session, by date
└─ ✅ To remember           commitments and deadlines
```

## Other agents

claude.ai, the Claude desktop and mobile apps, ChatGPT and Cursor connect to the same
server: in Treeno open **Access → AI agent** for step-by-step setup and a ready prompt.

## Uninstall

```
/plugin uninstall treeno@treeno
```

To sign out without uninstalling, run `/mcp`, choose **treeno** and clear its authentication.
