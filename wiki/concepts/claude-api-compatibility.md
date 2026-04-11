---
title: "Claude API Compatibility"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-zhipuai-claude-api]]"
tags: [api-compatibility, claude-api, migration]
confidence: high
status: active
---

# Claude API Compatibility

> Third-party providers offering Claude API-compatible endpoints — enabling migration by swapping only the base URL and API key.

## Summary

**Claude API compatibility** refers to third-party AI providers exposing endpoints that match the Anthropic Claude API interface. This allows developers using the Anthropic SDK to switch providers by changing only two configuration values — the `base_url` and `api_key` — without modifying application code.

[[zhipuai|ZhipuAI]] is one such provider, offering a compatible endpoint at `https://open.bigmodel.cn/api/anthropic` that routes requests to their GLM family of models (glm-5, glm-4.7, glm-4.5-air, glm-4.5-flash). The migration path is:

```python
# Only change these two lines:
client = anthropic.Anthropic(
    api_key="your-zhipuai-api-key",
    base_url="https://open.bigmodel.cn/api/anthropic"
)
# Everything else stays the same
```

This pattern enables tools like Claude Code, Cursor, and Cline to work with non-Anthropic models through the same interface, reducing vendor lock-in and providing access to models with different cost/performance tradeoffs.

## Key Principles

- **Interface compatibility, not model equivalence.** The API shape is the same; the underlying model behavior differs.
- **Minimal migration cost.** Two config changes, zero code changes.
- **Ecosystem leverage.** The entire Anthropic SDK and tool ecosystem works unchanged.

## Connections

- **Related concepts:** [[llm-wiki-pattern]] (the wiki pattern uses Claude Code, which can run on compatible endpoints)
- **Entities:** [[zhipuai]], [[obsidian]]
- **Sources:** [[source-zhipuai-claude-api]]

## Open Questions

- How closely do compatible models match Claude's behavior on complex agent tasks?
- What are the known differences between the compatible interface and native Claude API?
