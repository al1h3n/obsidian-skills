---
name: creation-janitor
description: Audit the creation section of a vault map against existing templates and note standards.
---

# creation-janitor

Check whether documented creation guidance matches the vault's existing templates and conventions.

- Locate `<vault>/AI System/Vault Map/creation.md` or ask for its path. Validate the vault root.
- Compare claims with relevant templates, frontmatter, and approved instruction notes. Cite exact paths; distinguish explicit rules from patterns.
- Flag missing, stale, contradictory, or unsupported guidance. Do not invent standards or edit source templates.
- Write findings and proposed corrections to an AI-owned audit note under `<vault>/AI System/`.
- Report scope and output path. If the guide or source material is unavailable, state what could not be checked.
