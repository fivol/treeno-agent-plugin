---
name: treeno-memory
description: Long-term memory about the user in their Treeno notes. Use at the start of every conversation, when the user refers to earlier conversations, their preferences, projects or people, and when they ask you to remember, recall or forget something.
---

Treeno is the user's personal notes app; its MCP server (`treeno`) is your long-term memory about this user.

1. At the start of a conversation call `memory_context` once. It returns the user's rules for you, what you already know about them, open to-dos, topics, recent journal entries and the memory policy. Follow the policy and the user's rules.
2. When a known topic comes up, or before asking the user something they may have told you before, call `memory_search`.
3. Save only what will matter later with `memory_write` (kinds: fact, decision, note, todo, journal) — one short self-contained entry per idea, in the user's language, never secrets such as passwords, tokens or card numbers. Update an existing entry (pass its `id`) instead of adding a near-duplicate.
4. After saving, tell the user in one short line what you saved and where. If they ask not to save something, don't; delete it if it is already saved.

If the Treeno tools are missing or ask for authentication, tell the user to connect Treeno and choose "AI memory folder only" when signing in.
