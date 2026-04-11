---
title: "LLM Wiki Pattern"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-karpathy-llm-wiki]]"
tags: [llm-wiki, knowledge-management, pattern]
confidence: high
status: active
---

# LLM Wiki Pattern

> A pattern where LLMs incrementally build and maintain a persistent, structured wiki — instead of re-deriving knowledge from raw sources on every query.

## Summary

The LLM Wiki pattern, proposed by [[andrej-karpathy]], replaces the dominant [[rag-vs-wiki|RAG]] approach with a **compile-and-maintain** model. Instead of retrieving from raw documents at query time, the LLM maintains a living wiki of interlinked markdown pages that sits between you and your sources.

The wiki has three layers: **raw sources** (immutable documents you curate), **the wiki** (LLM-generated pages the LLM owns and maintains), and **the schema** (a configuration document like `CLAUDE.md` that codifies conventions and workflows). The human curates sources and asks questions; the LLM does all the bookkeeping.

Three operations drive the system:
- **Ingest** — add a new source; the LLM reads it, creates a summary, updates entity/concept pages, flags contradictions, and updates the index.
- **Query** — ask a question; the LLM searches the wiki, synthesizes an answer, and files valuable answers back as new pages.
- **Lint** — periodically health-check the wiki for contradictions, orphans, stale claims, and missing cross-references.

A single ingested source typically touches 5–15 wiki pages. The cross-referencing and integration is what makes the wiki compound in value over time.

## Key Principles

- **The wiki is a persistent, compounding artifact** — cross-references accumulate, contradictions get flagged, synthesis deepens.
- **Knowledge is compiled once, then maintained** — not re-derived on every query.
- **Good answers become wiki pages** — explorations compound just like ingested sources.
- **The LLM owns the wiki layer** — the human never (or rarely) writes wiki pages directly.
- **The schema co-evolves** — `CLAUDE.md` grows as you discover what works for your domain.

## Connections

- **Related concepts:** [[rag-vs-wiki]], [[knowledge-compilation]], [[memex]]
- **Entities:** [[andrej-karpathy]], [[obsidian]]
- **Sources:** [[source-karpathy-llm-wiki]]

## Open Questions

- How does the pattern scale beyond ~100 sources? At what point does the index-file approach break down?
- How to mitigate persistent errors — when wrong claims get baked into the wiki?
