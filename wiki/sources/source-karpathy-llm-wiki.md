---
title: "Karpathy's LLM Wiki Pattern"
type: source
created: 2026-04-11
updated: 2026-04-11
source_type: article
source_url: "https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f"
tags: [llm-wiki, knowledge-management, rag, personal-knowledge-base]
---

# Karpathy's LLM Wiki Pattern

> A manifesto for building persistent, LLM-maintained personal knowledge bases that compound over time.

## Bibliography

- **Author(s):** Andrej Karpathy
- **Date:** 2026-04-04
- **URL:** https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- **Type:** Article / Gist

## Summary

Karpathy proposes a fundamental shift in how we use LLMs with documents. Instead of the dominant RAG pattern — where an LLM retrieves and re-derives answers from raw documents on every query — he advocates for having the LLM **incrementally build and maintain a persistent wiki** of structured, interlinked markdown files.

The wiki sits between you and the raw sources. When you add a new source, the LLM reads it, extracts key information, and integrates it into the existing wiki: updating entity pages, revising summaries, flagging contradictions, and strengthening the evolving synthesis. The knowledge is compiled once and kept current, not re-derived on every query.

The key insight is that the wiki is a **persistent, compounding artifact**. The cross-references already exist. The contradictions have already been flagged. The synthesis already reflects everything you've read. This makes subsequent queries vastly more efficient and nuanced than re-deriving everything from scratch.

Three layers form the architecture: **raw sources** (immutable, never modified), **the wiki** (LLM-owned, constantly updated), and **the schema** (a configuration file like `CLAUDE.md` that tells the LLM how to maintain the wiki). Three operations drive the system: **ingest** (add sources), **query** (ask questions, file good answers back), and **lint** (health-check the wiki periodically).

The pattern applies broadly: personal knowledge management, deep research, reading companion wikis, team/business knowledge bases, competitive analysis, due diligence, trip planning, course notes, and hobby deep-dives.

Karpathy connects this to Vannevar Bush's [[memex]] (1945) — a vision of personal, curated knowledge with associative trails. The part Bush couldn't solve was maintenance. The LLM handles that.

## Key Claims

1. **RAG has no accumulation.** Every query re-derives knowledge from scratch. The wiki pattern compiles once and keeps current. — _central thesis of the article_
2. **The maintenance burden is the bottleneck.** Humans abandon wikis because bookkeeping grows faster than value. LLMs make maintenance near-zero cost. — _pragmatic argument_
3. **Good answers should be filed back.** Queries produce valuable artifacts (comparisons, analyses, connections) that compound when saved as wiki pages. — _design principle_
4. **The index file scales surprisingly well.** At moderate scale (~100 sources, hundreds of pages), an index.md file avoids the need for embedding-based RAG infrastructure. — _practical observation_
5. **A single source touches 10–15 wiki pages.** The cross-referencing and integration is what makes the wiki valuable, not just the summary. — _operational guideline_

## Notable Quotes

> "The wiki is a persistent, compounding artifact. The cross-references are already there. The contradictions have already been flagged."

> "Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase."

> "The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping."

## Entities Mentioned

- [[andrej-karpathy]]
- [[obsidian]]

## Concepts Introduced

- [[llm-wiki-pattern]]
- [[rag-vs-wiki]]
- [[knowledge-compilation]]
- [[memex]]

## Connections

- **Contradicts:** _(none yet)_
- **Extends:** [[memex]] — applies Bush's 1945 vision with LLM-maintained associative trails
- **Related sources:** _(none yet)_
