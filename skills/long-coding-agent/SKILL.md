---
name: long-coding-agent
description: Long-running coding agent workflows (background + workdir), with tmux for interactive sessions.
metadata: {"clawdbot":{"emoji":"🧩","requires":{"anyBins":["claude","codex","opencode","pi"]}}}
---

# Long Coding Agent (background-first)

Use **bash background mode** for long-running, non-interactive work. For interactive sessions, use the **tmux** skill (preferred). If you must run an interactive CLI directly via bash, set **`pty:true`**.

## The Pattern: workdir + background

```bash
# Create temp space for chats/scratch work
SCRATCH=$(mktemp -d)

# Start agent in target directory (limits scope)
bash workdir:$SCRATCH background:true command:"<agent command>"
# Or for project work:
bash workdir:~/project/folder background:true command:"<agent command>"
# Returns sessionId for tracking

# Monitor progress
process action:log sessionId:XXX

# Check if done
process action:poll sessionId:XXX

# Send input (if agent asks a question)
process action:write sessionId:XXX data:"y"

# Kill if needed
process action:kill sessionId:XXX
```

**Why workdir matters:** keep the agent in a focused folder; avoid wandering into unrelated files.

---

## Interactive sessions

- **Preferred:** Use the **tmux** skill for interactive coding agents.
- **Fallback:** If running interactively via `bash`, always set `pty:true`.

---

## Codex CLI

**Model:** `gpt-5.2-codex` default (via `~/.codex/config.toml`)

### Building/Creating (use --full-auto or --yolo)
```bash
bash workdir:~/project background:true command:"codex exec --full-auto \"Build a snake game...\""
```

---

## Safety / hygiene

1. Prefer **workdir** scope; avoid `~` root.
2. Use **background** for long tasks; check logs via `process`.
3. Use **tmux** for interactive sessions; avoid half-attached CLI runs.
4. If a repo is sensitive/live, use a temp clone or worktree.

---

## PR Template (Razor Standard)

````markdown
## Original Prompt
[Exact request/problem statement]

## What this does
[High-level description]

**Features:**
- [Key feature 1]
- [Key feature 2]

**Example usage:**
```bash
# Example
command example
```

## Feature intent (maintainer-friendly)
[Why useful, how it fits, workflows it enables]

## Prompt history (timestamped)
- YYYY-MM-DD HH:MM UTC: [Step 1]
- YYYY-MM-DD HH:MM UTC: [Step 2]

## How I tested
**Manual verification:**
1. [Test step] - Output: `[result]`
2. [Test step] - Result: [result]

**Files tested:**
- [Detail]
- [Edge cases]

## Session logs (implementation)
- [What was researched]
- [What was discovered]
- [Time spent]

## Implementation details
**New files:**
- `path/file.ts` - [description]

**Modified files:**
- `path/file.ts` - [change]

**Technical notes:**
- [Detail 1]
- [Detail 2]

---
*Submitted by Razor 🥷 - Mariano's AI agent*
````
