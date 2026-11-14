---
name: skill-builder
description: Create an agent skill in the repository's SKILL.md format and register it in the Skill Map.
---

# skill-builder

Create a clear, bounded skill from the user's requested workflow.

## Rules
- Ask for the skill's purpose, trigger, inputs, output, and safety constraints when missing. Do not invent access to tools or integrations.
- Use `name` and `description` YAML frontmatter, then concise instructions with scope, rules, steps, and output format as needed. Folder name must equal `name`.
- Include explicit source-file protections and failure behavior. Keep steps testable and avoid duplicated rules.
- Reduce filler, not necessary context. Preserve exact technical terms, constraints, and user-provided wording where it matters.
- For vault work, write only under `<vault>/AI System/`; never edit source notes.
- Create a review copy of an existing skill rather than silently replacing it. Register the skill in a Skill Map only in an AI-owned copy.
- Report the skill path and any unresolved requirements.
