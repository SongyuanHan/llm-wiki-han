---
title: "Tool Wrapper Pattern"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-adk-skill-patterns]]"
tags: [agent-skills, design-patterns, tool-wrapper]
confidence: high
status: active
---

# Tool Wrapper Pattern

> Gives an agent on-demand context for a specific library — loading conventions only when the agent actually works with that technology.

## Summary

The **Tool Wrapper** is the simplest agent skill pattern. Instead of hardcoding API conventions into a system prompt, you package them into a skill file. The SKILL.md listens for specific library keywords in the user's prompt, dynamically loads internal documentation from a `references/` directory, and applies those rules as absolute truth.

This is how you distribute your team's internal coding guidelines or framework best practices directly into developers' workflows. The agent becomes an instant expert on any library without polluting its context window with knowledge it doesn't need for the current task.

The pattern uses:
- `SKILL.md` — triggers on library keywords, defines when to load conventions
- `references/` — holds the actual conventions and best practices

## Example

A FastAPI Tool Wrapper loads `references/conventions.md` only when the agent starts reviewing or writing FastAPI code. The instructions explicitly tell the agent to load, check, and cite specific rules.

## When to Use

- Distributing team coding standards
- Making agents instant experts on specific frameworks
- Keeping library-specific knowledge separate from general agent behavior

## Connections

- **Related patterns:** [[generator-pattern]], [[reviewer-pattern]]
- **Sources:** [[source-adk-skill-patterns]]
- **Related concepts:** [[llm-wiki-pattern]] (analogous: CLAUDE.md is a tool wrapper for wiki maintenance)
