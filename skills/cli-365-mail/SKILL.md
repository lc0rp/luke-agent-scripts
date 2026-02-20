---
name: cli-365-mail
description: Check Outlook/OWA mail via cli-365. Use when asked to search, triage, or summarize mail, apply To/CC/since filters, or run urgent mail checks
---

# CLI‑365 Mail

## Overview
Use the `cli-365` tool at ~/.local/bin/cli-365 to run mail searches.

## Quick start
```bash
# Search (example)
cli-365 mail search --limit 50 --since 2026-01-26 --to "luke.kyohere@onafriq.com" --cc "luke.kyohere@onafriq.com"
```

## Required GUI prefix if not in env. 
If not set, prepend for any command that launches or connects to the browser:
```
DISPLAY=:1 XAUTHORITY=$HOME/.Xauthority
```

## Search patterns
- **To + CC (both):**
  ```bash
  --to "luke.kyohere@onafriq.com" --cc "luke.kyohere@onafriq.com"
  ```
- **To OR CC:**
  ```bash
  'to:"luke.kyohere@onafriq.com" OR cc:"luke.kyohere@onafriq.com"'
  ```
- **Date window:** `--since YYYY-MM-DD` (or `--after` / `--before`)

## Triage rules
Follow Obsidian mail rules:
`/data/projects/Obsidian-Notes/3-Resources/Obsidian/mail-rules.md`

## Troubleshooting
- **401 Unauthorized:** run `auth login` again; if still 401, delete tokens at
  `~/.local/state/cli-365/tokens.json` and re‑login.
- **Stale browser:** remove Singleton* files in
  `~/.config/cli-365/profile/` then `browser start`.
- **Binary lacks flags:** use `go run ./cmd/cli-365` (newer CLI flags).
