---
title: "5 Agent Skill Design Patterns for ADK"
type: source
created: 2026-04-11
updated: 2026-04-11
source_type: article
source_url: "https://x.com/GoogleCloudTech/status/2033953579824758855"
tags: [agent-skills, adk, design-patterns, llm-agents]
---

# 5 Agent Skill Design Patterns for ADK

> An article identifying five recurring design patterns for structuring agent skills, moving beyond SKILL.md format to content design.

## Bibliography

- **Author(s):** Shubham Saboo, Lavin Igam
- **Date:** 2026-03-18
- **URL:** https://x.com/GoogleCloudTech/status/2033953579824758855
- **Type:** Article (X/Twitter thread)

## Summary

With 30+ agent tools (Claude Code, Gemini CLI, Cursor) standardizing on the same SKILL.md layout, the formatting problem is obsolete. The real challenge is **content design** — how to structure the logic inside a skill. By studying skills across the ecosystem (Anthropic, Vercel, Google), the authors identify five recurring patterns:

1. **[[tool-wrapper-pattern|Tool Wrapper]]** — gives an agent on-demand context for a specific library. Loads conventions only when the agent works with that technology.
2. **[[generator-pattern|Generator]]** — enforces consistent output through a fill-in-the-blank process using templates and style guides.
3. **[[reviewer-pattern|Reviewer]]** — separates what to check from how to check it. Uses a modular rubric loaded from an external checklist file.
4. **[[inversion-pattern|Inversion]]** — flips the agent-user dynamic. The agent interviews the user before acting, refusing to generate until requirements are complete.
5. **[[pipeline-pattern|Pipeline]]** — enforces a strict sequential workflow with hard checkpoints and diamond gate conditions.

The key insight: these patterns **compose**. A Pipeline can include a Reviewer step. A Generator can use Inversion to gather variables first. ADK's `SkillToolset` and progressive disclosure ensure agents only spend context tokens on what they need.

## Key Claims

1. **Format is solved; content design is the new challenge.** 30+ tools share the same SKILL.md layout, so formatting expertise is no longer a differentiator.
2. **Skills should be structurally different, not just topically different.** A FastAPI wrapper and a documentation pipeline look identical on the outside but operate completely differently inside.
3. **Patterns compose.** They're not mutually exclusive — a Pipeline can include a Reviewer step, a Generator can start with Inversion.
4. **Stop cramming everything into a system prompt.** Break workflows down, apply the right structural pattern, build reliable agents.

## Notable Quotes

> "Stop trying to cram complex and fragile instructions into a single system prompt. Break your workflows down, apply the right structural pattern, and build reliable agents."

## Entities Mentioned

- [[google-adk]]
- [[obsidian]] (in the broader ecosystem context)

## Concepts Introduced

- [[tool-wrapper-pattern]]
- [[generator-pattern]]
- [[reviewer-pattern]]
- [[inversion-pattern]]
- [[pipeline-pattern]]

## Connections

- **Contradicts:** _(none yet)_
- **Extends:** relates to [[llm-wiki-pattern]] (skills are a form of schema/configuration for agents)
- **Related sources:** [[source-karpathy-llm-wiki]]
