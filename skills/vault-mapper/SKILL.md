---
name: vault-mapper
description: Map notes in an Obsidian vault folder, summarize their topics and connections, and optionally add reviewed missing wikilinks in AI-owned copies.
---

# vault-mapper

Map a requested vault folder so the user can navigate notes they have forgotten or do not know. Summarize each processed note and identify clear connections. Optionally add conservative wikilinks to copies under `AI System/`; never change originals.

## Style

Drop: filler (just/really/basically/actually/simply), pleasantries (sure/certainly/of course/happy to), hedging. Fragments OK. Short synonyms (big not extensive, fix not "implement a solution for"). No causal arrows (→). Do not invent abbreviations. Use exact technical terms. Leave code and quoted errors unchanged.

## Hard rules

- Never edit, move, rename, or delete existing vault files.
- Write only inside `<vault>/AI System/`. Create that folder if missing. Files there are AI-owned and may be overwritten.
- When writing a linked copy, mirror the original relative path: `Projects/x.md` becomes `AI System/Projects/x.md`.
- Write a linked copy only if at least one link or Related entry was added. Never create identical copies.
- Skip `AI System/`, `.obsidian/`, and `.trash/` everywhere, including nested folders.
- A wrong link costs more than a missed link. Add only unambiguous links; when unsure, skip.
- Do not follow links outside the vault or expose secrets. Summaries should contain only note content relevant to the map.
- In a loop run with no user available, never block. If the required path is missing, stop and report `path missing`.

## Inputs

- `vault`: absolute vault root containing `.obsidian/`. Default to the current directory only when it contains `.obsidian/`.
- `path`: folder to map, relative to the vault. Required. If missing and the user is present, ask for it. If missing and no user is available, stop and report `path missing`.
- `since`: include only notes modified in the last N days. Default: all notes under `path`.
- `cap`: maximum notes to process. Default: 100. Process newest first and report how many matching notes were left over.
- `links`: whether to add missing links in AI-owned copies. Default: yes. If no, map only; do not write note copies.

Resolve explicit user values first. Do not silently substitute a different folder if the requested path does not exist or is not inside the vault.

## Steps

1. Validate the vault and requested folder. Confirm `.obsidian/` exists at the vault root, and the resolved path stays inside the vault. Do not scan if validation fails.
2. Build an index of all Markdown notes in the vault, excluding skipped directories. Include title (filename without `.md`), relative path, aliases, and tags from frontmatter. Read frontmatter only for notes outside the requested folder. Do not read their bodies.
   - Parse YAML `aliases` and `tags` lists, including simple inline lists. Treat malformed or uncertain frontmatter values as unavailable; do not guess.
   - Normalize title and alias keys case-insensitively. If a key maps to more than one note, mark it ambiguous and do not use it as a link target.
   - Ignore keys shorter than four characters, generic keys (`index`, `notes`, `todo`, `inbox`, `home`, `readme`, `untitled`, `daily`), and date-only titles.
3. Find Markdown notes under the requested path, excluding skipped directories. Apply `since` if set, then sort newest first and process at most `cap`. Count matching notes not processed as leftovers. Do not read notes outside this capped candidate set beyond their frontmatter.
4. Read each candidate note sufficiently to identify its subject and main points. Record its existing wikilinks and tags. Summarize only facts supported by the note; keep descriptions concise and distinguish a note's content from inference.
5. Identify connections between each candidate and other indexed notes:
   - Match title and alias keys case-insensitively as whole words, longest key first.
   - For existing links, resolve the target conservatively. Do not add a link to a note that is already linked anywhere in the candidate.
   - If `links: yes`, consider only clear plain-text mentions outside frontmatter, fenced code, inline code, existing `[[...]]`, Markdown links, URLs, heading lines, and tags. Do not link a note to itself.
   - Add only the first eligible mention per target in a note and at most 10 inline links per note. When matched text equals the target title, use `[[Title]]`; otherwise use `[[Title|matched text]]`. If a path-qualified link is needed to disambiguate, use the target's vault-relative path without `.md` only when the target is otherwise certain.
   - Tags may suggest related notes, but do not claim a connection based only on a generic tag. Count frontmatter and inline tags case-insensitively. Ignore any tag present in more than 25% of indexed notes.
   - A target qualifies for `## Related` only when the candidate and target share at least two non-ignored tags and the target is not already linked. Add no more than five entries per note. Do not add duplicate entries. Add to an existing `## Related` section if present; otherwise append a new section at the end.
6. If links are enabled, write only changed candidate notes to `AI System/<relative path>`. Preserve original content, line endings, and frontmatter; make no other content edits. Do not copy unchanged notes. If links are disabled, write no note files.
7. Report every processed note in a Markdown table. Use concise, factual descriptions and vault-relative paths. Include the number of links added per note when links are enabled. Report the total matching notes, processed count, links added, and leftover count after the table. If there are no candidates, report that clearly.

## Report

Use this table shape. The path is relative to the vault, not an absolute machine path.

| Note | Description | Relative path |
|---|---|---|
| `Situation in London` | News about London and events from the previous month. Links added: 2. | `Projects/Situation in London.md` |
| `Index` | Main rules and information about the notes. Links added: 0. | `Index.md` |

Descriptions must be based on the note itself. Do not call a note an index, project, or summary unless its content supports that label. If no links were added, omit the `Links added` phrase. Include counts after the table, for example: `Processed 2 of 8 notes; 2 links added; 6 left over.`
