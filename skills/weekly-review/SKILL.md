---
name: weekly-review
description: Draft a weekly review from prior review previews, daily notes, and briefs.
---

# weekly-review

Review the current week's source notes and produce a weekly review preview.

## Rules
- Confirm the date range from the current date and the user's week convention; ask if unclear. Do not guess dates.
- Read prior `weekly-review-preview` notes, current-week daily notes, and daily briefs in the requested vault. Exclude `.obsidian/`, `.trash/`, and `AI System/` from source scans.
- Extract supported wins, unfinished work, decisions, patterns, and next steps. Separate facts from interpretations; cite source notes with wikilinks.
- Do not duplicate old items as current. Preserve concrete details and mark missing evidence.
- Use concise wording without filler or loss of meaning.
- Never edit source notes. Write `<vault>/AI System/weekly-review-preview/YYYY-[W]WW.md`; avoid overwriting an existing preview by creating a review copy.
- Report the date range, source coverage, and output path.
