---
title: "Obsidian"
type: entity
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-karpathy-llm-wiki]]"
tags: [tool, knowledge-management, markdown]
---

# Obsidian

> A markdown-based knowledge management application with graph view, wikilinks, and a rich plugin ecosystem — the recommended frontend for the LLM Wiki pattern.

## Overview

[[obsidian]] is a note-taking and knowledge management application built on local markdown files. It has become the de facto standard for personal knowledge management due to several features that align perfectly with the [[llm-wiki-pattern]]:

- **Wikilinks** (`[[page-name]]`) — native support for interlinking notes, powering the cross-reference system.
- **Graph view** — visual representation of how pages connect, making the wiki's structure immediately visible.
- **Backlinks** — automatic detection of which pages link to the current page (cross-reference symmetry).
- **Local files** — the vault is just a directory of markdown files on disk, making it directly accessible to LLM agents.
- **Plugin ecosystem** — Dataview (frontmatter queries), Marp (slide decks), Web Clipper (article saving), and many more.

In the [[llm-wiki-pattern]], Karpathy describes the workflow: "I have the LLM agent open on one side and Obsidian open on the other. The LLM makes edits based on our conversation, and I browse the results in real time — following links, checking the graph view, reading the updated pages. Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase."

## Key Integrations for LLM Wiki

- **Obsidian Web Clipper** — browser extension that converts web articles to markdown for the `raw/` directory.
- **Dataview** — queries over YAML frontmatter for dynamic tables and lists.
- **Marp** — markdown-based slide decks generated from wiki content.
- **Attachment download** — hotkey to download all images in a note to `raw/assets/`.

## Connections

- **Related entities:** [[andrej-karpathy]] (recommender), [[google-adk]] (part of the same agent tool ecosystem), [[zhipuai]] (compatible API provider for agent tools)
- **Concepts:** [[llm-wiki-pattern]], [[knowledge-compilation]], [[claude-api-compatibility]]
- **Sources:** [[source-karpathy-llm-wiki]]

## References

- Website: https://obsidian.md
