---
name: navigation-janitor
description: Audit the navigation section of a vault map for broken paths, stale links, and inconsistencies.
---

# navigation-janitor

Audit the navigation map against the current vault. Identify drift; do not silently repair source files.

- Validate the vault root and locate the navigation map, defaulting to `<vault>/AI System/Vault Map/navigation.md` only if present.
- Check referenced paths and note titles against the scoped vault. Skip `.obsidian/`, `.trash/`, and unrelated AI outputs.
- Flag missing, ambiguous, duplicate, or misleading entries. Keep verified entries and preserve user-authored intent.
- Do not change source notes. Write proposed corrections to `<vault>/AI System/Vault Map/navigation.audit.md`.
- Report checks performed, scope limits, findings, and output path. If no map exists, report `navigation map missing`.
