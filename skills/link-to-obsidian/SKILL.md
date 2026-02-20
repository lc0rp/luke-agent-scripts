---
name: link-to-obsidian
description: Generate shareable http(s) links that redirect into Obsidian via the link-to-obsidian service. Use when sending Obsidian note links in chat apps (Discord/WhatsApp) that can’t open obsidian:// URLs, or when converting obsidian://open links to http(s) format.
---

# Link-to-Obsidian (usage)

## Overview

Generate HTTP links that redirect to `obsidian://open` so they’re clickable in apps that only allow http(s) links.

## Quick start

Format:

```
http://<ip>:<port>/?[v=<VaultName>&]f=<Path/Note.md>
```

v= (optional) name of the vault (if not default)
default vault name = `Obsidian-Notes`

Example:

```
http://100.99.173.30:7777/?f=0-Inbox/Tasks.md

http://100.99.173.30:7777/?v=Obsidian-Notes&f=Projects/ProjectA/MeetingNotes.md
```

Notes:
- Keep the **file** query string; scheme/host/port change from `obsidian://open`.
- Percent-encode the `f=` path the same way Obsidian expects.
- Use the **Tailscale IP** (e.g., `100.99.173.30`) for shareable links.
- **Do not** use `127.0.0.1` or `localhost` in shared links.
- Default port is `7777` (unless overridden by config).

## Convert from obsidian://open

Given:

```
obsidian://open?vault=Vault&file=Inbox/Note.md
```

Convert to:

```
http://<host>:<port>/?f=Inbox/Note.md
```

## Troubleshooting link format

- If the link doesn’t open, check for bad encoding in `f=` or a wrong `v=`.
- If unsure of host/port, check `/etc/link-to-obsidian/link-to-obsidian.env` (read-only) for `LTO_TAILSCALE_DNS`, `LTO_TAILSCALE_IP`, and `PORT`.
