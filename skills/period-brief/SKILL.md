---
name: period-brief
description: Build a concise brief from Obsidian vault activity over a specified number of days. Reusable engine for daily-brief, weekly-brief, and custom-period briefs.
---

# period-brief

Build one concise brief for a caller-specified lookback period. The period is a positive whole number of days. Read-only on source vault files.

## Argument

- Required: `<days>` — number of days to look back, e.g. `1`, `7`, or `30`.
- If invoked by `daily-brief`, use exactly `1` day.
- If invoked by `weekly-brief`, use exactly `7` days.
- For a direct invocation with no valid argument, ask the user for the number of days. In a loop run, do not block: use 3 days and note the fallback in the brief.
- Use the period from the start of the day N days before today through today. Use the same period for note changes, completed work, and new email. State the actual date range in the brief.

## Style

Drop filler (just/really/basically/actually/simply), pleasantries, and hedging. Fragments OK. Prefer short words and concise lines. Preserve proper names and exact dates.

## Hard rules

- Never edit, move, rename, or delete existing vault files.
- Write only inside `<vault>/AI System/`. Create the output folder if missing. Files there are AI-owned and may be overwritten.
- Skip `AI System/`, `.obsidian/`, and `.trash/` when scanning.
- In a loop run with no user to answer, never block. Note missing setup in the brief and continue.
- Only report facts found in vault notes, email, or weather. Do not invent plans or details.

## Inputs

Resolve values in this order: user message, `<first vault>/AI System/period-brief.config.md`, then ask the user.

- `days`: required period argument.
- `vaults`: absolute vault paths. Default to the current directory if it contains `.obsidian/`.
- `scan`: folders holding personal projects, tasks, and daily notes. Default to the whole vault.
- `city`: used for weather.
- `email`: source (Gmail, Outlook, GitHub, or other).

For a daily-brief invocation, if the period config is absent, also read the legacy `<first vault>/AI System/daily-brief.config.md` before asking. Do not overwrite or migrate the legacy file automatically.

When values are missing and a user is present, ask once with all missing setup questions in one message. Save answers to `AI System/period-brief.config.md` as `key: value` lines. Next runs reuse the config without re-asking. Do not ask for `days` if the caller supplied it.

## Steps

1. Get today's date by running `date +%F`; never guess. Calculate and record the inclusive date range for the requested period.
2. Find recent Markdown notes in each vault, honoring configured scan folders:
   `find "$V" -type f -name '*.md' -mtime -N -not -path '*/.obsidian/*' -not -path '*/.trash/*' -not -path '*/AI System/*'`
   Replace `N` with the requested days. Sort newest first and cap at 25 notes per vault.
3. Extract rather than read whole notes. Per note, grep for:
   `grep -nE '^\\s*- \\[ \\]|[0-9]{4}-[0-9]{2}-[0-9]{2}|due::|scheduled::|#(todo|plan|meeting|code|dev)'`
   Record the first heading too. Read at most 80 lines only when matching lines are unclear. Include completed work from the period in the `Recent:` line; do not list completed tasks as outstanding plans.
4. Weather: use an available weather tool or web search for the configured city. For a multi-day period, report the forecast for the next available days within the period or the period's relevant dates, and label the dates clearly. One concise line. If city is unknown and there is no user, write `City not set.` If no reliable forecast is available for the requested dates, say so; do not imply a forecast covers the whole period.
5. Email: check available tools for email (Gmail, Outlook, IMAP, or GitHub notifications).
   - If connected, fetch new messages within the requested date range, max 10. Include sender, subject, and a one-line gist. Skip newsletters and promotions.
   - If not connected and a user is present, ask which email source to use. Suggest the Gmail integration for Google mail; use GitHub notifications for repo-based work. Save the answer in config.
   - If not connected and there is no user, write `Email not connected.`
6. Classify unfinished items:
   - Major: important/high-priority items (`#important`, `priority:: high`) or items dated within the requested period involving travel, visa, a meeting with a named person, deadline, event, money, or launch. Sort by date, soonest first.
   - Minor: personal errands, small edits, and other low-stakes items without a fixed date.
   - Coding: implementation, fixes, refactors, bugs, PRs, repository work, deployments, tests, `#code`/`#dev` tags, or notes in code-project folders.
   - If an item fits multiple categories, use the highest priority: Major, then Coding, then Minor. Skip done tasks except for a short summary in `Recent:`.
7. Write the brief to `<first vault>/AI System/period-brief/YYYY-MM-DD-Nd.md`, where the date is today and `N` is the requested number of days. This keeps different periods for the same date distinct.

## Format

Use exactly these headers, in this order. Keep empty sections and put one line inside each.

```markdown
---
generated-by: period-brief
date: YYYY-MM-DD
period-days: N
period-start: YYYY-MM-DD
period-end: YYYY-MM-DD
---
# Period brief YYYY-MM-DD (N days)
Recent: N notes changed in N days (YYYY-MM-DD to YYYY-MM-DD). Main: [[Note A]], [[Note B]]. Done: short list.

## Date and weather
Weekday, YYYY-MM-DD. Forecast dates and conditions, if available.

## New emails
- Sender: subject. Gist.

## Major plans
- Date: plan. [[Source note]]

## Minor plans
- Plan. [[Source note]]

## Coding tasks
- Task. [[Source note]]
```

Empty text: emails `No new emails.`; date/weather `Weather unavailable.` or `City not set.`; plans `Nothing planned.`

Rules:
- One line per item. Most urgent first. Max 7 items per section, then `+N more`.
- Cite the source note as `[[wikilink]]`. For multi-vault scans, add `(vault-name)`.
- The `Recent:` line reports the total changed-note count, the requested period, up to two main note links, and a short done summary when found. If none changed: `Recent: No notes changed in N days (YYYY-MM-DD to YYYY-MM-DD).`
- Do not claim a forecast for dates the weather source does not cover.

## Reply

If the user asked interactively, show the brief content and its saved path. In a loop run, return the path only.
