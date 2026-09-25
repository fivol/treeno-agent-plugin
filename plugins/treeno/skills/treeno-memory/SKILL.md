---
name: treeno-memory
description: Long-term memory about the user in their Treeno notes. Use at the start of a conversation; when the user refers to earlier work ("continue where we left off", "as I told you", "what do you know about me"); when they ask to remember, save, recall or forget something; and when a decision is settled or a piece of work is finished.
---

Treeno is the user's personal notes app; its MCP server (`treeno`) is your long-term memory about this user.

Recall
- Call `memory_context` at the start of a conversation and whenever the user refers to earlier work. It returns the user's rules for you, what you already know about them, open to-dos, topics, recent journal entries and the memory policy. Follow the policy and the user's rules.
- Call `memory_search` when a known topic comes up, or before asking the user something they may have told you before.

Save with `memory_write` at explicit moments, not at the end of the chat:
- the user says "remember this" / "save this decision";
- a decision is settled (`decision`, with the reason, under a topic);
- you learn a stable fact about the user (`fact`);
- a detail will be needed again (`note`, under a topic);
- a commitment or deadline appears (`todo`);
- a meaningful piece of work is finished (`journal`: one line plus 2-6 short details).
One short self-contained entry per idea, in the user's language, never secrets such as passwords, tokens or card numbers. Update an existing entry (pass its `id`) instead of adding a near-duplicate; retrying the same write is safe.

After saving, tell the user in one short line what you saved, with the link from the result ("Saved to Treeno: … → <link>").

Forget: when the user says "forget this" or "don't save that", remove the entry with `memory_delete`.

If the Treeno tools are missing or ask for authentication, tell the user to connect Treeno and choose "AI memory folder only" when signing in.
