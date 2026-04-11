# Sync Schema

Push schema and template improvements from the mother vault to one or more child vaults.

## Arguments

- `$ARGUMENTS` — the target child vault path(s). Examples:
  - `/sync-schema ~/Vaults/llm-wiki-rust`
  - `/sync-schema ~/Vaults/llm-wiki-rust ~/Vaults/llm-wiki-health`
  - `/sync-schema ~/Vaults/*` (glob all child vaults)
  - If empty, list all directories that contain a `CLAUDE.md` and `wiki/templates/` and ask the user to choose.

## Instructions

1. Parse `$ARGUMENTS` as one or more target directory paths. If empty, search for candidate child vaults and ask the user.
2. Determine the mother vault root: walk up from the current working directory until you find a `CLAUDE.md` that contains the LLM Wiki schema (look for the `### Ingest Workflow` section).
3. For each target vault:
   a. Verify it is a valid child vault (contains `CLAUDE.md` and `wiki/templates/`).
   b. Compare the following files between mother and child:
      - `CLAUDE.md`
      - `wiki/templates/concept.md`
      - `wiki/templates/entity.md`
      - `wiki/templates/source.md`
      - `wiki/templates/synthesis.md`
      - `.claude/commands/*.md` (all skills)
   c. If the child vault has customized its `CLAUDE.md` (i.e., the diff shows meaningful additions beyond what the mother has), warn the user: "该子 vault 的 CLAUDE.md 有定制内容，同步可能覆盖。是否继续？" Ask for confirmation.
   d. Copy changed files from mother to child.
   e. In the child vault, stage and commit with message: "同步母 vault schema 更新"
4. Report results to the user in Chinese:
   - Which vaults were synced
   - Which files were updated in each
   - Which vaults were skipped (and why)

## Rules

- Do NOT overwrite a child vault's `raw/`, `wiki/concepts/`, `wiki/entities/`, `wiki/sources/`, `wiki/synthesis/`, `index.md`, or `log.md` — these belong to the child.
- Only sync structural files: `CLAUDE.md`, `wiki/templates/`, `.claude/commands/`.
- Always warn before overwriting a customized `CLAUDE.md`.
- Do NOT push to remote — only commit locally.
