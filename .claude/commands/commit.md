# Commit Wiki Changes

Commit all changes in the current working directory with a descriptive message.

## Instructions

1. Run `git status` to see all changes (staged and unstaged, untracked files).
2. Run `git diff` and `git diff --cached` to understand what changed.
3. Analyze the changes and draft a commit message that:
   - Starts with a verb in imperative form (e.g., "Add", "Update", "Fix", "Ingest")
   - Summarizes the **why**, not just the **what**
   - Is in **Chinese** (matching this wiki's primary interaction language)
   - Keeps the subject line under 72 characters
   - Adds a blank line and a bullet-point body if multiple logical changes are present
4. Stage all relevant files with `git add` (be specific — avoid `git add -A` if `.env` or credentials might be present).
5. Commit with the message, appending the co-author trailer.
6. Run `git status` after commit to verify clean state.

## Commit message format

```
<中文动词><简要描述>

- 变更1
- 变更2

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>
```

## Examples

- `新增来源：智谱AI Claude API兼容文档`
- `Lint：修复5处交叉引用不对称`
- `更新CLAUDE.md：增加check-ingest动作和防编造约束`
- `Ingest：添加ADK技能设计模式文章，创建7个wiki页面`

## Rules

- Do NOT push to remote unless the user explicitly asks.
- Do NOT amend existing commits — always create a new commit.
- If there are no changes, tell the user "没有需要提交的变更" and stop.
