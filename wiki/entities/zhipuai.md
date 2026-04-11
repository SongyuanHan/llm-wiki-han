---
title: "ZhipuAI (智谱AI)"
type: entity
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[source-zhipuai-claude-api]]"
tags: [company, chinese-ai, llm-provider, zhipuai]
---

# ZhipuAI (智谱AI)

> Chinese AI company offering Claude API-compatible endpoints and the GLM family of language models.

## Overview

ZhipuAI (智谱AI) is a Chinese AI company that provides large language model services through their BigModel platform (bigmodel.cn). They offer a [[claude-api-compatibility|Claude API-compatible interface]] that allows developers to migrate from Anthropic's Claude to ZhipuAI's GLM models with minimal code changes.

Their model lineup includes:
- **GLM-5** — current flagship
- **GLM-4.7** — high-intelligence model (200K context, 96K output)
- **GLM-4.5-air** — cost-effective (128K context, 96K output)
- **GLM-4.5-flash** — free tier (128K context, 96K output)

ZhipuAI also offers a **GLM Coding Plan** — a subscription service starting at 20 RMB/month that supports Claude Code, Cline, and other coding tools, making it possible to run the [[llm-wiki-pattern]] on ZhipuAI's infrastructure.

## Key Contributions

- Claude API compatibility layer for the Chinese market
- GLM family of language models with large context windows
- GLM Coding Plan for agent-based development tools

## Connections

- **Related entities:** [[obsidian]] (tool ecosystem overlap), [[google-adk]] (both in the agent tool ecosystem)
- **Concepts:** [[claude-api-compatibility]], [[llm-wiki-pattern]]
- **Sources:** [[source-zhipuai-claude-api]]

## References

- Platform: https://bigmodel.cn
- API Docs: https://docs.bigmodel.cn/cn/guide/develop/claude/introduction
- API Keys: https://bigmodel.cn/usercenter/proj-mgmt/apikeys
