---
title: "RAG vs Wiki"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-karpathy-llm-wiki]]"
tags: [rag, llm-wiki, retrieval, comparison]
confidence: high
status: active
---

# RAG vs Wiki

> RAG (Retrieve and Generate) re-derives knowledge from scratch on every query. The wiki pattern compiles knowledge once and keeps it current.

## Summary

Most people's experience with LLMs and documents is **RAG**: upload files, retrieve relevant chunks at query time, generate an answer. This works but has a fundamental limitation — there is **no accumulation**. Ask a subtle question requiring synthesis across five documents, and the LLM must find and piece together fragments every single time. Nothing is built up. Systems like NotebookLM, ChatGPT file uploads, and most RAG pipelines work this way.

The [[llm-wiki-pattern]] takes a different approach. Instead of retrieving from raw documents at query time, the LLM incrementally builds a **persistent wiki** of structured, interlinked pages. Knowledge is **compiled once** (during ingest) and then **maintained** (during lint). At query time, the LLM reads already-synthesized wiki pages — the cross-references are already there, the contradictions already flagged.

The difference is not just efficiency — it's **quality**. A wiki that reflects everything you've read produces more nuanced answers than retrieving fragments from raw documents. The synthesis compounds.

| Dimension | RAG | Wiki Pattern |
|-----------|-----|-------------|
| Knowledge state | Re-derived each query | Compiled and maintained |
| Cross-references | None (raw chunks) | Rich [[wikilinks]] |
| Contradiction handling | None (each query is isolated) | Flagged and tracked |
| Accumulation | None | Compounding over time |
| Maintenance cost | Zero (no artifact to maintain) | Near-zero (LLM does it) |
| Scale mechanism | Vector search over embeddings | Index file → search engine |

## Connections

- **Related concepts:** [[llm-wiki-pattern]], [[knowledge-compilation]]
- **Sources:** [[source-karpathy-llm-wiki]]

## Open Questions

- At what scale does the index-file approach become insufficient vs. vector search?
- Can RAG and wiki approaches be combined effectively (wiki for context, RAG for verification)?
