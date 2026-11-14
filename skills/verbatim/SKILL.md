---
name: verbatim
description: Save an AI conversation word-for-word to an Obsidian note or review copy.
---

# verbatim

Preserve the provided conversation exactly. Do not summarize, correct, reorder, or remove content.

## Rules
- Ask for the destination note if not specified; default to today's daily note only when its path and format are clear.
- Preserve speaker labels, timestamps, formatting, and text exactly. Do not include content not provided or available in the conversation.
- Never edit an existing user note. Write a new note under `<vault>/AI System/` or a complete review copy at the mirrored path.
- If the source conversation is incomplete or unavailable, state that; do not reconstruct missing turns.
- Report the saved path.
