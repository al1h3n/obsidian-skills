---
name: cascade
description: Propagate a user-requested name change across note text, frontmatter, paths, and scheduled-task references in review copies.
---

# cascade

Prepare a name-change preview across an explicitly scoped vault. Never perform in-place edits or renames.

## Inputs
Require the old name, new name, and scope. Ask if any are missing. Confirm whether matches should be exact, case-insensitive, or include aliases.

## Steps
1. Validate vault and scope. Exclude `.obsidian/`, `.trash/`, and `AI System/` from source scans.
2. Find candidate body text, frontmatter, filenames, and available scheduled-task references. Do not access external systems without an authorized integration.
3. Distinguish exact matches from ambiguous or incidental matches. Do not rewrite history files; skip them and report the count.
4. Prepare changed copies under `<vault>/AI System/`, mirroring relative paths. For path changes, create proposed destination copies; never move or rename source files.
5. Preserve formatting and unrelated content. Report each proposed change and ambiguous match for review.
