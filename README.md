# obsidian-skills

Light agent skills for Obsidian vaults. Vault-agnostic. Never edit user files: output goes to `<vault>/AI System/`.

| Skill | Does |
|---|---|
| `daily-brief` | Recent notes + weather + email into one dated brief |
| `analyze-connections` | Finds missing `[[links]]`, writes linked copies |

## Install

```bash
bunx skills add al1h3n/obsidian-skills --list
bunx skills add al1h3n/obsidian-skills -s daily-brief -s analyze-connections -g
```

`-s` = `--skill`. `-g` = global, one install serves every vault. Add `-a claude-code` to pick an agent.

## Layout

```
skills/
  daily-brief/SKILL.md
  analyze-connections/SKILL.md
```

Folder name must equal `name` in SKILL.md frontmatter.

## Use

- `daily-brief`: give vault path(s). First run asks city and email source, saves to `AI System/daily-brief.config.md`.
- `analyze-connections`: give vault and folder path. Review copies in `AI System/`, copy over originals by hand.
