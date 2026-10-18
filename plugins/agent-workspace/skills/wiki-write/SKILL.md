---
name: wiki-write
description: File a durable finding as a concept page in a workspace repo's wiki/ (an Open Knowledge Format bundle), with frontmatter, cited sources, index and log entries. Use when told to add findings to the wiki, "file durable concepts" or update wiki pages.
---

# Wiki write

The repo's own wiki guide (named in `AGENTS.md`, often `docs/wiki-maintenance.md` or `wiki/conventions.md`) wins over this skill. Use this when the repo has no guide or the guide leaves a gap.

## One concept per file

- File name: short kebab-case, in the folder that fits (`wiki/<Folder>/<name>.md`). Search the index first and update an existing page rather than adding a near-duplicate.
- Only durable facts. News, readings and full write-ups go in `docs/`.

## Page shape

```
---
type: Reference
title: Short title
description: One specific sentence; it becomes the index line.
tags: [topic, topic]
status: draft
generated:
  by: process:analysis
  at: 2026-01-01T00:00:00Z
sources:
  - id: short-id
    resource: https://example.com/page
    title: Page title
---

# Heading

Short plain sentences. Each claim ends with a footnote.[^short-id]

Links to related pages use relative paths, such as [Other](other.md).

[^short-id]: Page title
```

- `type` is `Reference` (a durable fact), `Guide` (setup steps) or `Playbook` (troubleshooting).
- Each footnote id matches a `sources[].id`, and its text equals that source's `title`.
- Say plainly when a source is ambiguous or a claim is untested.

## Index and log

- If `okf` is installed (`pip install git+https://github.com/xchewtoyx/okf-core`), run `okf index --bundle wiki --recurse` and `okf validate --bundle wiki`, and fix any errors.
- Otherwise add a line `* [Title](file.md) - description` to the folder's `index.md`, under the heading for the page's `type`.
- Add one line under today's date in `wiki/log.md`: `* **Creation**: what was added.` (or `**Update**`).
