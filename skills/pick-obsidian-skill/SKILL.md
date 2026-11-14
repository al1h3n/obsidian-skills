---
name: pick-obsidian-skill
description: Select and invoke the most relevant available Obsidian skill or small skill sequence for the user's task.
---

# pick-obsidian-skill

Route Obsidian and vault tasks to skills from this repository. Invoke skills available to the active agent; do not install or activate tools without user approval.

## Selection
- Building a personal profile: `me-builder`.
- Vault navigation map: `navigation-builder`; note templates and standards: `creation-builder`; both: use both builders.
- New or revised skill: `skill-builder`; audit skills: `skills-janitor`.
- Daily brief: `daily-brief`; daily activity log: `daily-log`; weekly synthesis: `weekly-review` or `weekly-brief` when a fixed seven-day brief is requested; custom date span: `period-brief`.
- Topic exploration/MOC: `sherpa` and `style-guide-MOC`.
- Creative feedback: `rock-tumbler`.
- Save conversation exactly: `verbatim`; summarize: `summarizer`; append excerpt: `quick-append`.
- Propagate a name: `cascade`; standardize a convention: `harmonize`; audit maps: `navigation-janitor` or `creation-janitor`.
- Share a note: `sanitize` for privacy, `collator` for linked-note context, `courier` for transfer preparation. Combine only as needed and with user consent.
- Find note links: `analyze-connections`; map a folder: `vault-mapper`.

## Behavior
- Select the smallest set that fully covers the task. Load the relevant style guide when requested or required by a selected skill.
- Follow each skill's constraints and order. Never edit source vault files; generated notes and changed copies go only under `<vault>/AI System/`.
- If a selected skill is unavailable, report its name and provide the repository install command or offer an available alternative. Do not claim to have installed or run it.
- Ask only for missing information that blocks safe work. Do not make changes beyond the user's request.
- For mixed requests, distinguish analysis, draft creation, and external sharing; get approval before sharing.
