# obsidian-skills

Vault-agnostic skills for Obsidian. Never edit, move, rename, or delete source vault files. Generated notes and changed copies go under `<vault>/AI System/`.

## Skills

| Skill | Purpose |
|---|---|
| `me-builder` | Build a personalized `me.md` from user-approved sources. |
| `navigation-builder` | Build the navigation half of a vault map. |
| `creation-builder` | Document templates and note-creation standards. |
| `skill-builder` | Create skills to the repository schema and register them in a Skill Map. |
| `daily-brief` | Build a daily shared brief from vault activity, projects, email, and weather. |
| `daily-log` | Record timestamped Cowork-session and Ideaverse-file activity in today's log. |
| `sherpa` | Ask universal topic questions and draft a starter MOC in the user's voice. |
| `style-guide-MOC` | Reference for useful, navigable MOCs; used by `sherpa`. |
| `weekly-review` | Draft a weekly review from review previews, daily notes, and briefs. |
| `rock-tumbler` | Give requested creative feedback; surface tensions and blind spots without writing the final work. |
| `style-guide-writing-AI` | Avoid AI-flavored writing and reduce unnecessary words without losing meaning. |
| `style-guide-writing-me` | Apply the lightweight LYAI student writing guide when provided. |
| `verbatim` | Save a conversation word-for-word. |
| `summarizer` | Summarize a conversation or transcript in a fixed structure. |
| `quick-append` | Append a conversation excerpt to a chosen note or today's daily note. |
| `cascade` | Propagate a name change across content, metadata, paths, and scheduled-task references in review copies. |
| `harmonize` | Apply a shared convention change in review copies. |
| `navigation-janitor` | Audit the navigation half of the vault map. |
| `creation-janitor` | Audit the creation half of the vault map. |
| `skills-janitor` | Audit skill files against `skill-builder`'s schema. |
| `sanitize` | Make a shareable copy with personal details flagged, abbreviated, or removed. |
| `collator` | Build a self-contained copy by adding summaries of linked notes. |
| `courier` | Prepare a note copy for another vault or person. |
| `pick-obsidian-skill` | Select and invoke the relevant available skills for an Obsidian task. |
| `period-brief` | Brief engine for a caller-specified number of days. |
| `weekly-brief` | `period-brief` with a fixed seven-day lookback. |
| `analyze-connections` | Find missing links and write linked copies. |
| `vault-mapper` | Map a folder, summarize notes and connections, optionally write linked copies. |

## Install

```bash
bunx skills add al1h3n/obsidian-skills --list
bunx skills add al1h3n/obsidian-skills -s me-builder -s navigation-builder -s creation-builder -s skill-builder -s daily-brief -s daily-log -s sherpa -s style-guide-MOC -s weekly-review -s rock-tumbler -s style-guide-writing-AI -s style-guide-writing-me -s verbatim -s summarizer -s quick-append -s cascade -s harmonize -s navigation-janitor -s creation-janitor -s skills-janitor -s sanitize -s collator -s courier -s pick-obsidian-skill -g
```

`-s` means `--skill`; `-g` installs globally. Add `-a claude-code` to select an agent. The existing brief and vault tools can be installed separately by name.

## Safety and writing

- Treat vault notes as user data. Never modify, move, rename, or delete source files.
- Write new notes and review copies only under `<vault>/AI System/`; create that folder when needed. Preserve the source's relative path for copies.
- Do not overwrite a source, even when the requested operation sounds destructive. Make a review copy and state its path.
- Do not expose secrets or follow links outside the vault. Ask before sharing or sending content externally.
- Preserve meaning, context, names, dates, structure, and concrete detail. Reduce token use by removing filler and repetition, not by making content vague or abstract. Keep exact quotations unchanged unless asked to edit them.
- Skip `.obsidian/`, `.trash/`, and `AI System/` when scanning, unless a task explicitly targets an AI-owned output.
- If a required path or source is missing, ask when the user is present; otherwise stop and report the missing input.

## Layout

Every skill lives at `skills/<name>/SKILL.md`; its folder name must match the `name` in frontmatter. `daily-brief` and `weekly-brief` use `period-brief`. `sherpa` uses `style-guide-MOC`. `pick-obsidian-skill` can only invoke skills available to the active agent; it reports missing skills instead of silently installing them.
