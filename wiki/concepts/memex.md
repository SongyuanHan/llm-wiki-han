---
title: "Memex"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-karpathy-llm-wiki]]"
tags: [history, knowledge-management, vannevar-bush]
confidence: high
status: active
---

# Memex

> Vannevar Bush's 1945 vision of a personal, curated knowledge store with associative trails between documents.

## Summary

The **Memex** was proposed by Vannevar Bush in his 1945 essay "As We May Think." It envisioned a device that would store all of a person's books, records, and communications — but crucially, it would also store the **associative trails** between documents. The connections between items were as valuable as the items themselves.

Bush's vision was closer to the [[llm-wiki-pattern]] than to what the web became. The web is public and loosely structured; the Memex was **private, actively curated, with the connections between documents as the primary artifact**.

The part Bush couldn't solve was: **who does the maintenance?** Maintaining associative trails, updating cross-references, keeping the store consistent — this is tedious, manual work that doesn't scale. In the [[llm-wiki-pattern]], the LLM handles this. The cost of maintenance is near zero, which is what makes the vision finally practical.

Karpathy explicitly draws this connection in [[source-karpathy-llm-wiki|his article]]: "The idea is related in spirit to Vannevar Bush's Memex (1945) — a personal, curated knowledge store with associative trails between documents."

## Connections

- **Related concepts:** [[llm-wiki-pattern]], [[knowledge-compilation]]
- **Entities:** [[andrej-karpathy]]
- **Sources:** [[source-karpathy-llm-wiki]]

## Open Questions

- What would Bush think of the LLM-maintained version of his vision?
- Are there other historical precursors to the wiki pattern?
