---
title: "Reviewer Pattern"
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-adk-skill-patterns]]"
tags: [agent-skills, design-patterns, reviewer, code-review]
confidence: high
status: active
---

# Reviewer Pattern

> Separates what to check from how to check it — using a modular rubric loaded from an external checklist file.

## Summary

The **Reviewer** pattern stores review criteria in a modular `references/review-checklist.md` file. When code is submitted, the agent loads the checklist and methodically scores the submission, grouping findings by severity.

The key insight is **separation of concerns**: the SKILL.md instructions remain static (the "how"), while the checklist content is swappable (the "what"). Swap a Python style checklist for an OWASP security checklist, and you get a completely different specialized audit using the exact same skill infrastructure.

Severity levels typically include: **error** (must fix), **warning** (should fix), **info** (consider). Output is structured with summary, findings grouped by severity, an overall score, and top recommendations.

## When to Use

- Automated PR reviews
- Security audits (swap in OWASP checklist)
- Style enforcement (swap in language-specific checklist)
- Any systematic evaluation against a rubric

## Connections

- **Related patterns:** [[tool-wrapper-pattern]] (similar separation of instructions from content), [[pipeline-pattern]] (Reviewers often appear as a Pipeline step)
- **Sources:** [[source-adk-skill-patterns]]
- **Related concepts:** [[llm-wiki-pattern]] (lint operation is similar to a Reviewer)
