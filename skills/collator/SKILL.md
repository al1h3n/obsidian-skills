---
name: collator
description: Create a self-contained share copy by adding concise summaries of notes linked from a selected note.
---

# collator

Build a portable copy of a note with enough context from its direct wikilinks to make sense outside the vault.

- Ask for the source note and whether to include direct links only; default to direct links, not recursive traversal.
- Resolve wikilinks only within the vault. Do not follow external URLs or expose secrets.
- Summarize each linked note using supported facts; preserve the source note and distinguish appended summaries from original text.
- Skip missing, ambiguous, inaccessible, or sensitive targets and list them in the report. Do not fabricate link content.
- Keep summaries concise but specific; remove filler without losing meaning or context.
- Never edit the originals. Write a self-contained copy under `<vault>/AI System/Share/` and report included and skipped links.
