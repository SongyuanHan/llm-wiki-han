---
title: "Knowledge Compilation"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-karpathy-llm-wiki]]"
tags: [knowledge-management, compilation, ingest]
confidence: high
status: active
---

# Knowledge Compilation

> The process of reading raw sources once, extracting key information, and integrating it into a structured wiki — analogized to software compilation.

## Summary

In the [[llm-wiki-pattern]], **knowledge compilation** is the core operation that distinguishes the wiki approach from [[rag-vs-wiki|RAG]]. When a new source is ingested, the LLM doesn't just index it for later retrieval — it **compiles** the knowledge into the wiki. This means:

1. **Extracting key claims** — identifying the most important points, not just keywords.
2. **Creating a source summary** — a distilled page capturing the source's essence.
3. **Updating entity pages** — adding new information about people, organizations, tools mentioned.
4. **Updating concept pages** — revising existing concept descriptions to reflect new evidence.
5. **Flagging contradictions** — when new data conflicts with existing claims, creating a `> [!contradiction]` callout.
6. **Maintaining cross-references** — ensuring [[wikilinks]] connect related pages bidirectionally.
7. **Updating the index** — adding all new/changed pages to `index.md`.

A single source typically touches 5–15 wiki pages during compilation. This upfront cost pays for itself every time you query the wiki, because the knowledge doesn't need to be re-derived.

The analogy to software compilation is intentional: raw sources are source code, the wiki is the compiled binary, and queries execute against the compiled artifact — fast and complete.

## Key Principles

- Compile once, maintain continuously.
- Compilation touches many files — that's the value.
- Contradictions are flagged, not silently overwritten.
- The compiled artifact (wiki) is richer than any single source.

## Connections

- **Related concepts:** [[llm-wiki-pattern]], [[rag-vs-wiki]]
- **Sources:** [[source-karpathy-llm-wiki]]

## Open Questions

- How to handle sources that partially contradict earlier compilations?
- When should compilation be re-done (e.g., if the LLM improves)?
