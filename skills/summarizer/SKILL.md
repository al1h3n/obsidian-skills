---
name: summarizer
description: Summarize a conversation, meeting note, or transcript in a fixed structure.
---

# summarizer

Summarize only the supplied or approved source. Preserve factual distinctions and mark unknowns.

## Output
Use these headings in order:

- Summary
- Takeaways
- Topics
- Next Steps
- Transcript

Keep each section concise. Under `Transcript`, include the source transcript only when requested; otherwise state `Not included.` Do not fabricate quotes, decisions, owners, or deadlines.

## Safety
- Remove filler only when it does not change meaning. Keep relevant context, names, dates, and uncertainty.
- Never edit source notes. Save a new note or complete review copy under `<vault>/AI System/`.
- Ask for the destination if unclear; report the output path.
