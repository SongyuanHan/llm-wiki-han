---
title: "Pipeline Pattern"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-adk-skill-patterns]]"
tags: [agent-skills, design-patterns, pipeline, workflow]
confidence: high
status: active
---

# Pipeline Pattern

> Enforces a strict sequential workflow with hard checkpoints and diamond gate conditions — the agent cannot skip steps or bypass validation.

## Summary

For complex tasks, you cannot afford skipped steps or ignored instructions. The **Pipeline** pattern enforces a strict, sequential workflow where the instructions themselves serve as the workflow definition.

Key mechanism: **diamond gate conditions** — explicit user-approval requirements before moving to the next phase. The agent is forbidden from proceeding until the user confirms the previous step's output. This prevents the agent from bypassing validation and presenting an unvalidated final result.

The pattern uses all optional directories:
- `references/` — loaded at specific steps where they're needed
- `assets/` — templates for output at specific stages
- `SKILL.md` — the workflow definition with gate conditions

This keeps the context window clean — the agent only loads what it needs at each step.

## When to Use

- Documentation generation pipelines
- Multi-step code generation with validation
- Any complex task where skipped steps cause failures
- Workflows requiring human-in-the-loop checkpoints

## Connections

- **Related patterns:** [[reviewer-pattern]] (often a step inside a Pipeline), [[generator-pattern]], [[inversion-pattern]]
- **Sources:** [[source-adk-skill-patterns]]
- **Related concepts:** [[llm-wiki-pattern]] (ingest workflow is a pipeline: read → summarize → update → index → log)
