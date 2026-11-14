---
name: skills-janitor
description: Audit skill files against the schema and safety rules defined by skill-builder.
---

# skills-janitor

Audit an explicitly scoped skill directory or repository. Use `skill-builder` as the schema reference.

- Check frontmatter, matching folder/name, trigger clarity, inputs, steps, output, failure behavior, and relevant safety limits.
- Flag duplication, contradictions, vague instructions, unsupported tool assumptions, and source-file risks.
- Do not silently rewrite skills or edit user files. Provide specific findings and proposed fixes.
- When working in an Obsidian vault, write the audit under `<vault>/AI System/`. In a repository, report findings unless the user explicitly requests a patch.
- Include files checked, issues by path, and scope limits. Do not claim a complete audit if files were inaccessible.
