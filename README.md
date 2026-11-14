# obsidian-skills

Light agent skills for Obsidian vaults. Vault-agnostic. Never edit user files: output goes to `<vault>/AI System/`.

| Skill | Does |
|---|---|
| `period-brief` | Reusable brief engine for a caller-specified number of days |
| `daily-brief` | `period-brief` with a fixed 1-day lookback |
| `weekly-brief` | `period-brief` with a fixed 7-day lookback |
| `analyze-connections` | Finds missing `[[links]]`, writes linked copies |
| `vault-mapper` | Maps a vault folder, summarizes notes and connections, optionally writes linked copies |

## Install

```bash
bunx skills add al1h3n/obsidian-skills --list
bunx skills add al1h3n/obsidian-skills -s period-brief -s daily-brief -s weekly-brief -s analyze-connections -s vault-mapper -g
```

`-s` = `--skill`. `-g` = global, one install serves every vault. Add `-a claude-code` to pick an agent.

## Layout

```
skills/
  period-brief/SKILL.md
  daily-brief/SKILL.md
  weekly-brief/SKILL.md
  analyze-connections/SKILL.md
  vault-mapper/SKILL.md
```

Folder name must equal `name` in SKILL.md frontmatter. The daily and weekly entry points rely on the `period-brief` skill, so install it alongside either wrapper.

## Use

- `period-brief`: provide a number of days and vault path(s). First run asks for city and email source, saves setup in `AI System/period-brief.config.md`.
- `daily-brief`: fixed 1-day period; uses the same brief engine and configuration.
- `weekly-brief`: fixed 7-day period; uses the same brief engine and configuration.
- `analyze-connections`: give vault and folder path. Review copies in `AI System/`, copy over originals by hand.
- `vault-mapper`: give vault and folder path. Review a map of notes and their connections, optionally writing AI-owned linked copies in `AI System/`.

