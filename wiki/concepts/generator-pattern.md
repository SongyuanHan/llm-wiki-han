---
title: "Generator Pattern"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-adk-skill-patterns]]"
tags: [agent-skills, design-patterns, generator]
confidence: high
status: active
---

# Generator Pattern

> Enforces consistent output through a fill-in-the-blank process — the agent orchestrates a template, style guide, and user input to produce structured documents.

## Summary

While the [[tool-wrapper-pattern|Tool Wrapper]] applies knowledge, the **Generator** enforces consistent output. It solves the problem of agents generating different document structures on every run by orchestrating a fill-in-the-blank process.

The pattern uses:
- `assets/` — holds the output template (the blank to fill)
- `references/` — holds the style guide (the grammar rules)
- `SKILL.md` — acts as a project manager, coordinating retrieval and step-by-step execution

The agent loads the template, reads the style guide, asks the user for missing variables, and populates the document. This is practical for generating predictable API documentation, standardizing commit messages, or scaffolding project architectures.

## When to Use

- Generating consistent documentation
- Standardizing output formats across team members
- Scaffolding project structures
- Any task where output structure must be predictable

## Connections

- **Related patterns:** [[tool-wrapper-pattern]], [[inversion-pattern]] (Inversion can precede generation to gather variables), [[pipeline-pattern]]
- **Sources:** [[source-adk-skill-patterns]]
