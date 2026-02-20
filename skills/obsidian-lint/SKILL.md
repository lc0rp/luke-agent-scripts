---
name: obsidian-lint
description: Lint Obsidian vault markdown with markdownlint-cli2 using an Obsidian-friendly .markdownlint-cli2.jsonc, and enforce lint-on-commit via a git pre-commit hook that blocks commits on failures (typically scoped to PARA folders).
---

# Obsidian Lint (markdownlint-cli2)

## Vault config (single file)

- Keep an Obsidian-friendly `.markdownlint-cli2.jsonc` in the vault root.
- Prefer scoping `globs` to PARA folders to reduce noise and runtime:
  - `0-Inbox/**/*.md`
  - `1-Projects/**/*.md`
  - `2-Areas/**/*.md`
  - `3-Resources/**/*.md`
  - `4-Archive/**/*.md`

## Enforce before each commit (blocking)

- Commit a repo-local hooks directory (recommended): `.githooks/pre-commit`.
- Enable it locally:
  - `git config core.hooksPath .githooks`

### Pre-commit behavior

- Lint only staged Markdown files within PARA folders.
- Fail the commit if markdownlint exits non-zero.
- Use `markdownlint-cli2` if installed; otherwise fall back to `npx markdownlint-cli2`.
