---
name: quick-append
description: Prepare a conversation excerpt for a note, defaulting to today's daily note when available.
---

# quick-append

Append only the requested conversation chunk. Preserve its meaning and useful context; do not summarize unless asked.

## Rules
- Use the named destination. Otherwise use today's daily note only when its path and format are clear.
- Never change an existing user note. Produce a complete review copy under `<vault>/AI System/` at the mirrored relative path, with the chunk appended in the note's established format.
- Do not duplicate content already present in the destination. Preserve exact quotations when requested.
- If the destination cannot be identified, ask. If no user is available, stop and report `destination missing`.
- Report the review-copy path.
