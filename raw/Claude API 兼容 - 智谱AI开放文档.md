---
title: "Claude API 兼容 - 智谱AI开放文档"
source: "https://docs.bigmodel.cn/cn/guide/develop/claude/introduction"
author:
published:
created: 2026-04-11
description:
tags:
  - "raw"
---
智谱提供与 Claude API 兼容的接口，这意味着您可以使用现有的 Anthropic SDK 代码，只需要简单修改 API 密钥和基础 URL，就能无缝切换到智谱的模型服务。

[GLM Coding Plan](https://bigmodel.cn/coding-plan/personal/overview) 编码套餐上线，支持含 Claude Code、Cline 等近10种全球主流编码工具，搭配智谱新旗舰 GLM-4.5，20元起包月畅享！

### 核心优势

## 零学习成本

如果您已经熟悉 Anthropic SDK，可以立即上手使用

## 快速迁移

现有 Claude 应用如 Claude Code 等可以快速迁移到智谱平台

## 极速访问

无障碍极速访问智谱模型的强大能力

## 持续更新

跟随 Anthropic SDK 更新，保持最新功能支持

某些场景下智谱与 Claude 接口仍存在差异，但不影响整体兼容性。

## 从 Claude 迁移至智谱

如果您已经在使用 Claude API，迁移到智谱非常简单。
- 替换您访问的 `base_url` 为 `https://open.bigmodel.cn/api/anthropic`
- 在 [智谱开放平台](https://bigmodel.cn/usercenter/proj-mgmt/apikeys) 申请您的 `api_key`
- 调用时使用智谱模型编码即可

```python
# 原来的 Claude 代码
import anthropic

client = anthropic.Anthropic(
    base_url="your-base-url",
    api_key="your-api-key",
)

# 迁移到智谱，只需要修改三个地方
client = anthropic.Anthropic(
    api_key="your-zhipuai-api-key",  # 替换为智谱 API Key
    base_url="https://open.bigmodel.cn/api/anthropic"  # 配置智谱 base_url
)

# 模型编码使用 智谱模型，其他代码保持不变
message = client.messages.create(
    model="glm-5",  # 使用智谱模型
    max_tokens=1024,
    messages=[{"role": "user", "content": "Hello!"}]
)
```

**推荐模型**

| 模型编码 | 定位 | 特点 | 上下文 | 最大输出 |
| --- | --- | --- | --- | --- |
| [glm-4.7](https://docs.bigmodel.cn/cn/guide/models/text/glm-4.7) | 高智能旗舰 | \- 旗舰性能   \- 强大的推理能力、代码生成能力以及工具调用能力 | 200K | 96K |
| [glm-4.5-air](https://docs.bigmodel.cn/cn/guide/models/text/glm-4.5) | 高性价比 | \- 在推理、编码和智能体任务上表现强劲 | 128K | 96K |
| [glm-4.5-flash](https://docs.bigmodel.cn/cn/guide/models/free/glm-4.5-flash) | 免费模型 | \- 基座模型的普惠版本 | 128K | 96K |

## 详细步骤

### 获取 API Key

1. 访问 [智谱开放平台](https://bigmodel.cn/)
2. 注册并登录您的账户
3. 在 [API Keys](https://bigmodel.cn/usercenter/proj-mgmt/apikeys) 管理页面创建 API Key
4. 复制您的 API Key 以供使用

建议将 API Key 设置为环境变量： `export ANTHROPIC_API_KEY=your-api-key` 替代硬编码到代码中，以提高安全性。

### 代码示例

```shellscript
curl https://open.bigmodel.cn/api/anthropic/v1/messages \
     --header "x-api-key: your-zhipuai-api-key" \
     --header "content-type: application/json" \
     --data \
'{
    "model": "glm-5",
    "max_tokens": 1024,
    "stream": true,
    "messages": [
        {"role": "user", "content": "Hello, ZHIPU"}
    ]
}'
```

## 更多资源

## [畅玩 Claude Code](https://docs.bigmodel.cn/cn/guide/develop/claude)

Claude Code 接入智谱随心畅玩

## [智谱 API 文档](https://docs.bigmodel.cn/cn/api/introduction)

查看智谱完整的 API 文档

## [Claude 官方文档](https://docs.anthropic.com/en/api/messages)

参考 Claude 官方文档了解更多

智谱致力于保持与 Claude API 的兼容性，如果您在迁移过程中遇到任何问题，请联系我们的 [技术支持团队](https://bigmodel.cn/online-book/customerService) 。