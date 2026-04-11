---
title: "ZhipuAI Claude API 兼容文档"
type: source
created: 2026-04-11
updated: 2026-04-11
source_type: article
source_url: "https://docs.bigmodel.cn/cn/guide/develop/claude/introduction"
tags: [zhipuai, claude-api, compatibility, chinese-ai]
---

# ZhipuAI Claude API 兼容文档

> 智谱AI提供的Claude API兼容接口 — 无需修改代码，仅需替换API密钥和基础URL即可迁移到智谱的GLM模型。

## Bibliography

- **Author(s):** ZhipuAI (智谱AI)
- **Date:** _(not specified)_
- **URL:** https://docs.bigmodel.cn/cn/guide/develop/claude/introduction
- **Type:** Documentation

## Summary

智谱AI提供与Claude API完全兼容的接口，支持用户使用现有Anthropic SDK代码，仅需修改API密钥和基础URL即可无缝切换到智谱的模型服务。迁移只需三步：

1. 替换 `base_url` 为 `https://open.bigmodel.cn/api/anthropic`
2. 在智谱开放平台申请 `api_key`
3. 调用时使用智谱模型编码（如 `glm-5`）

该文档列出了推荐模型：

| 模型 | 定位 | 上下文 | 最大输出 |
|------|------|--------|----------|
| glm-4.7 | 高智能旗舰 | 200K | 96K |
| glm-4.5-air | 高性价比 | 128K | 96K |
| glm-4.5-flash | 免费 | 128K | 96K |

文档还提到GLM Coding Plan编码套餐，支持Claude Code、Cline等近10种编码工具，搭配GLM-4.5旗舰模型，20元起包月。

## Key Claims

1. **零学习成本迁移。** 已有Anthropic SDK代码可直接使用，仅需改两个配置参数。 — _core value proposition_
2. **支持Claude Code等工具。** 通过GLM Coding Plan，可直接在Claude Code等工具中使用智谱模型。 — _ecosystem integration_
3. **持续跟踪Anthropic SDK更新。** 保持最新功能支持。 — _maintenance promise_

## Notable Quotes

> "智谱提供与 Claude API 兼容的接口，这意味着您可以使用现有的 Anthropic SDK 代码，只需要简单修改 API 密钥和基础 URL，就能无缝切换到智谱的模型服务。"

## Entities Mentioned

- [[zhipuai]]

## Concepts Introduced

- [[claude-api-compatibility]]

## Connections

- **Contradicts:** _(none yet)_
- **Extends:** related to [[llm-wiki-pattern]] (Claude Code is the tool that runs the wiki)
- **Related sources:** [[source-karpathy-llm-wiki]]
