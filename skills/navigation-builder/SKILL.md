---
name: navigation-builder
description: Build the navigation section of an Obsidian vault map from approved vault notes.
---

# navigation-builder

Create a compact guide that helps an assistant find relevant notes. This builds navigation only; use `creation-builder` for templates and standards.

## Rules
- Validate the vault root and requested scope. Exclude `.obsidian/`, `.trash/`, and `AI System/` from source scans.
- Index note titles, paths, aliases, and clear subject matter. Read only enough content to classify notes; do not infer connections from filenames alone.
- Group by existing folders or well-supported themes. Include useful entry points, paths, and disambiguation notes. Keep labels specific.
- Preserve exact paths and names. Do not move or edit source notes.
- Write `<vault>/AI System/Vault Map/navigation.md`. If it exists, make a review copy instead of replacing it.
- Report scope, note count, output path, and any ambiguous titles.
