---
name: openclaw-message-luke
description: Message Luke via OpenClaw (Discord/WhatsApp), including media/file attachments, target resolution, and send-result verification.
---

# OpenClaw Message Luke

## When to use

Use when asked to message Luke (status update, screenshot, artifact, alert) via OpenClaw.

## Defaults

- Prefer Discord channel `1464292705902395726` (`cli-365`) unless user specifies another target.
- Always use `--json` and report `messageId` + `channelId` from output.
- Include UTC timestamp in message body.

## Resolve target first (if unsure)

```bash
openclaw channels resolve --channel discord --json "<id-or-name>"
```

Known good Discord channels on this devbox:

- `1464292705902395726` -> `cli-365`
- `1126043332171284480` -> `tmux`
- `1103206451478016032` -> `general`

## Send text

```bash
openclaw message send \
  --channel discord \
  --target 1464292705902395726 \
  --message "update $(date -u +%Y-%m-%dT%H:%M:%SZ)" \
  --json
```

## Send media/file

```bash
openclaw message send \
  --channel discord \
  --target 1464292705902395726 \
  --message "artifact $(date -u +%Y-%m-%dT%H:%M:%SZ)" \
  --media /tmp/file.png \
  --json
```

## Common failures

- `Unknown Channel`: target is invalid or bot lacks access. Re-resolve target, then retry with a known-good channel id.
- OpenClaw doctor migration notes in output: informational; send can still succeed. Trust JSON payload `ok/result`.

## Success criteria

- JSON includes:
  - `"ok": true`
  - `"result.messageId"`
  - `"result.channelId"`
