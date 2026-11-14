---
name: me-builder
description: Build or refresh a concise, user-approved personal profile note for an Obsidian assistant.
---

# me-builder

Create a useful `me.md` that helps an assistant adapt to the user's work and preferences.

## Rules
- Ask for the vault root or use the current directory only when it contains `.obsidian/`.
- Use only user-provided facts and sources the user explicitly approves. Do not infer identity, values, health, relationships, or preferences from incidental notes.
- Draft from clear, stable facts: name/pronouns if offered, roles, goals, active context, preferences, and boundaries. Omit unsupported or sensitive details.
- Keep it brief and concrete. Remove filler and repetition without changing meaning or making facts abstract. Preserve exact names and requested wording.
- Never edit a source note. Write `<vault>/AI System/me.md`; if it exists, write a review copy at `<vault>/AI System/me.review.md` unless the user approves replacement of this AI-owned file.
- Show the saved path and unresolved questions. Do not claim facts the user has not confirmed.
