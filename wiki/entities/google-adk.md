---
title: "Google Agent Development Kit (ADK)"
type: entity
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-adk-skill-patterns]]"
tags: [tool, google, agent-framework, adk]
---

# Google Agent Development Kit (ADK)

> Google's open-source framework for building AI agents, with native support for the SKILL.md skill specification.

## Overview

Google ADK (Agent Development Kit) is a framework for building AI agents that standardizes on the **SKILL.md** specification — a markdown-based format for defining agent skills. Over 30 agent tools (Claude Code, Gemini CLI, Cursor) share this same layout, making the format a de facto standard.

ADK's `SkillToolset` provides **progressive disclosure** — agents only spend context tokens on the exact patterns they need at runtime. This is what enables the pattern composition described in [[source-adk-skill-patterns]]: a Pipeline can include a Reviewer step without loading all reviewer context upfront.

The SKILL.md format uses optional directories:
- `references/` — external documents loaded on demand
- `assets/` — templates and static resources
- `SKILL.md` — the skill definition with metadata and instructions

## Key Contributions

- Open-source skill specification adopted by 30+ tools
- Progressive disclosure for efficient context management
- Pattern composition (skills can combine multiple design patterns)

## Connections

- **Related entities:** [[obsidian]] (part of the same agent tool ecosystem)
- **Concepts:** [[tool-wrapper-pattern]], [[generator-pattern]], [[reviewer-pattern]], [[inversion-pattern]], [[pipeline-pattern]]
- **Sources:** [[source-adk-skill-patterns]]

## References

- Documentation: https://google.github.io/adk-docs/
