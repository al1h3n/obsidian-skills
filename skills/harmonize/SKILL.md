---
name: harmonize
description: Apply a user-requested convention change to notes that share the convention, using review copies.
---

# harmonize

Standardize one explicit convention across a scoped set of notes without changing the source vault.

## Inputs
Require the convention to change, its replacement, and scope. Ask for examples or exceptions when needed.

## Steps
1. Validate the vault and scope. Skip `.obsidian/`, `.trash/`, and `AI System/` during source scans.
2. Identify notes that actually use the convention. Exclude unrelated notes and preserve documented exceptions.
3. Apply only the requested change. Keep meaning, context, names, dates, and formatting outside the convention intact.
4. Write changed copies to `<vault>/AI System/` using mirrored relative paths. Never edit or rename source files.
5. Report changed and skipped counts, exception cases, and review-copy paths. Do not claim complete coverage if the scope was capped or inaccessible.
