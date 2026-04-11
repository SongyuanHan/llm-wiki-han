---
title: "Inversion Pattern"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-adk-skill-patterns]]"
tags: [agent-skills, design-patterns, inversion, requirements]
confidence: high
status: active
---

# Inversion Pattern

> Flips the agent-user dynamic — the agent interviews the user before acting, refusing to generate until requirements are complete.

## Summary

Agents inherently want to guess and generate immediately. The **Inversion** pattern flips this dynamic. Instead of the user driving the prompt and the agent executing, the agent acts as an interviewer.

The pattern relies on **explicit, non-negotiable gating instructions** (e.g., "DO NOT start building until all phases are complete") to force the agent to gather context first. It asks structured questions sequentially and waits for answers before moving to the next phase. The agent refuses to synthesize a final output until it has a complete picture of requirements and constraints.

Typical phases include:
1. **Problem Discovery** — what problem, who are users, expected scale
2. **Technical Constraints** — deployment environment, tech stack, non-negotiable requirements
3. **Synthesis** — only after all questions are answered

## When to Use

- Project planning and requirements gathering
- Any task where premature generation leads to wrong results
- Complex system design where context matters

## Connections

- **Related patterns:** [[generator-pattern]] (Inversion can precede generation), [[pipeline-pattern]]
- **Sources:** [[source-adk-skill-patterns]]
