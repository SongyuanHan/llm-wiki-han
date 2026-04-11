# LLM Wiki — Schema & Conventions

This is a personal knowledge base built using Andrej Karpathy's LLM Wiki pattern.
The LLM (Claude) owns the `wiki/` layer entirely. You create pages, update them,
maintain cross-references, and keep everything consistent. The human curates sources
and asks questions.

## Directory Structure

```
raw/              Immutable source documents (never modify)
raw/assets/       Downloaded images and media
wiki/             LLM-generated wiki pages (you own this layer)
wiki/concepts/    Concept and topic pages
wiki/entities/    Entity pages (people, organizations, tools, etc.)
wiki/sources/     One summary page per ingested source
wiki/synthesis/   Cross-domain synthesis and analysis pages
wiki/templates/   Page templates
index.md          Content catalog — updated on every ingest
log.md            Chronological activity log — append only
```

## Page Format Conventions

Every wiki page must have YAML frontmatter with these fields:

```yaml
---
title: Page Title
type: concept | entity | source | synthesis
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources:
  - "[[source-page-slug]]"
tags: [tag1, tag2]
confidence: high | medium | speculative
status: active | superseded | archived
---
```

### Optional frontmatter fields
- `contradictions:` — list of known contradictions with other pages
- `open_questions:` — list of unresolved questions
- `related:` — list of `[[wikilinks]]` to related pages

## Cross-Referencing Rules

1. **Always use `[[wikilinks]]`** for internal references — this powers Obsidian's graph view.
2. **Every new page must be linked from at least one existing page** (no orphans).
3. **Cross-reference symmetry:** If page A links to page B, verify page B links back to A.
4. **Source provenance:** Every claim in the wiki must trace back to a `[[source-*]]` page.

## Operations

### Ingest Workflow

When the user provides a new source:

1. Save the raw source to `raw/` (if not already present). Use a descriptive slug filename.
2. Read and analyze the source.
3. Discuss key takeaways with the user.
4. Create a source summary page at `wiki/sources/source-<slug>.md`.
5. Create or update entity pages in `wiki/entities/`.
6. Create or update concept pages in `wiki/concepts/`.
7. Create or update synthesis pages in `wiki/synthesis/` if cross-domain insights emerge.
8. Update `index.md` — add all new/changed pages.
9. Append an entry to `log.md` with format: `## [YYYY-MM-DD] ingest | <title>`
10. A single source should touch 5–15 wiki pages.

### Query Workflow

When the user asks a question:

1. Read `index.md` first to find relevant pages.
2. Drill into relevant wiki pages. Do NOT fall back to raw sources during query — the wiki should be the compiled, sufficient artifact.
3. **Hard constraint — no fabrication.** If neither the wiki nor `raw/` contains the information needed to answer the question, you MUST NOT generate an answer from your training data or general knowledge. Instead, explicitly tell the user which specific parts of the question fall outside the wiki's current scope. For example: "Wiki 中不包含关于 X 的信息" or "关于 Y 的部分，wiki 中没有任何来源涉及此主题。"
4. If wiki pages are insufficient to answer the question, ask the user: "Wiki 中缺少部分信息，是否要检查 raw 源文件？"
   - **User says yes →** proceed with **check-ingest** action:
     a. Search `raw/` for relevant information that should have been captured.
     b. If found, analyze **why ingest missed it** (e.g., the concept was implicit, too granular, or the source summary template didn't prompt for this category of information).
     c. Present the findings to the user and ask:
        - **Whether to modify the ingest workflow** (e.g., add a new step, update the source template, broaden concept extraction) to prevent future misses.
        - **Whether to update the wiki now** with the found content (i.e., retroactively complete the ingest for this source).
     d. If the user approves changes, update `CLAUDE.md` ingest section or wiki pages accordingly, and append to `log.md`.
   - **User says no →** answer with whatever the wiki does contain, and explicitly state which parts cannot be answered: "关于 X，wiki 中暂无相关信息。"
5. **用中文生成回答内容。** All responses to the user must be in Chinese.
6. Synthesize an answer with `[[wikilink]]` citations. When referencing wiki content, cite the source page like `（来源：[[source-xxx]]）`.
7. When the answer involves comparing or synthesizing multiple pages, present it as a structured analysis with clear sections, not a flat list.
8. If the answer is substantial, **file it back into the wiki** as a new page (synthesis or concept). The filed page content remains in English (wiki pages are English); only the user-facing response is Chinese.
9. Update `index.md` and `log.md`.

### Lint Workflow

Periodically health-check the wiki:

1. **Contradictions** — find claims that conflict across pages.
2. **Stale claims** — find claims superseded by newer sources.
3. **Orphan pages** — pages with no inbound links.
4. **Missing pages** — concepts/entities mentioned but lacking their own page.
5. **Dead links** — `[[wikilinks]]` pointing to non-existent pages.
6. **Missing cross-references** — related pages that should link to each other.
7. **Incomplete metadata** — pages missing frontmatter fields.
8. **Empty sections** — pages with placeholder sections never filled in.
9. **Stale index** — index entries not matching actual pages.

Append lint results to `log.md` with format: `## [YYYY-MM-DD] lint`

## Naming Conventions

- Source pages: `source-<descriptive-slug>.md`
- Concept pages: `<descriptive-slug>.md`
- Entity pages: `<name>.md`
- Synthesis pages: `<descriptive-slug>.md`
- Filenames: lowercase, hyphens for spaces, no special characters

## Style Guidelines

- Write in clear, concise prose — not bullet-point dumps.
- Lead with the most important information.
- Use `[[wikilinks]]` liberally — the graph is the value.
- Mark uncertain claims with `[speculative]` or set `confidence: speculative`.
- When a new source contradicts an existing claim, flag it with a `> [!contradiction]` callout rather than silently overwriting.
- Keep pages focused — one concept or entity per page.

## Tools & Integrations

- **Obsidian** is the primary viewer — leverage wikilinks, graph view, backlinks.
- **Obsidian Web Clipper** for saving web articles to `raw/`.
- **Dataview plugin** — frontmatter enables dynamic queries.
- **Marp plugin** — for generating slide decks from wiki content.
- **Graph view** — the best way to see wiki structure at a glance.
