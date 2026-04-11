# New Vault

Create a new topic-specific LLM Wiki vault from the mother template.

## Arguments

- `$ARGUMENTS` — the target directory path and optional topic name. Examples:
  - `/new-vault ~/Vaults/llm-wiki-rust`
  - `/new-vault ~/Vaults/llm-wiki-health`
  - `/new-vault ./llm-wiki-ai-agents` (relative path)

## Instructions

1. Parse `$ARGUMENTS` as the target directory path. If the argument is empty, ask the user to provide a path.
2. If the target directory already exists and is non-empty, warn the user and ask for confirmation before proceeding.
3. Determine the mother vault root: walk up from the current working directory until you find a `CLAUDE.md` with `type: concept | entity | source | synthesis` in its templates section (i.e., the vault that contains `wiki/templates/`).
4. Create the target directory structure:
   ```
   <target>/
   ├── raw/
   ├── raw/assets/
   ├── wiki/
   ├── wiki/concepts/
   ├── wiki/entities/
   ├── wiki/sources/
   ├── wiki/synthesis/
   ├── wiki/templates/    (copied from mother)
   ├── .claude/
   ├── .claude/commands/  (copied from mother)
   ├── CLAUDE.md          (copied from mother)
   ├── index.md           (fresh empty template)
   ├── log.md             (fresh empty template)
   ```
5. Copy these files from the mother vault to the target:
   - `CLAUDE.md`
   - `wiki/templates/*.md` (all 4 templates)
   - `.claude/commands/*.md` (all skills)
6. Generate fresh `index.md` and `log.md` in the target (empty template, same format as mother).
7. Initialize a git repo in the target: `git init && git add -A && git commit`.
8. Report the result to the user in Chinese, including the full path and the initial commit hash.

## Rules

- Do NOT copy `raw/` content — child vaults start with empty raw sources.
- Do NOT copy `wiki/` content (concepts, entities, sources, synthesis) — only templates.
- Do NOT copy `.obsidian/` — Obsidian will regenerate its config when the vault is opened.
- Do NOT copy `.git/` — each child vault gets its own independent git history.
