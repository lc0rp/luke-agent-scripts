---
name: devbox-display1-screenshot
description: Capture screenshots from devbox GUI display :1, convert to PNG when possible, and provide fallback when only .xwd capture is available.
---

# Devbox Display :1 Screenshot

## When to use

Use when asked to capture what is visible in Kasm VNC session on devbox display `:1`.

## Health check

```bash
DISPLAY=:1 XAUTHORITY=$HOME/.Xauthority xset q >/dev/null && echo OK
```

If not `OK`, display/auth not ready.

## Capture screenshot (.xwd baseline)

```bash
TS=$(date +%Y%m%d-%H%M%S)
XWD="/tmp/display-1-${TS}.xwd"
DISPLAY=:1 XAUTHORITY=$HOME/.Xauthority \
  xwd -root -silent -display :1 -out "$XWD"
ls -lh "$XWD"
```

## Convert to PNG (preferred)

Try first available method:

### Method A: ImageMagick

```bash
convert "$XWD" "${XWD%.xwd}.png"
```

### Method B: Netpbm

```bash
xwdtopnm "$XWD" | pnmtopng > "${XWD%.xwd}.png"
```

### Method C: fallback

If converter tools unavailable, keep `.xwd` and send/share as-is.

## Verify output

```bash
PNG="${XWD%.xwd}.png"
[ -f "$PNG" ] && file "$PNG" && ls -lh "$PNG"
```

## Optional send via OpenClaw (Discord)

```bash
openclaw message send \
  --channel discord \
  --target 1464292705902395726 \
  --message "display :1 screenshot $(date -u +%Y-%m-%dT%H:%M:%SZ)" \
  --media "${XWD%.xwd}.png" \
  --json
```

If PNG conversion unavailable, use `--media "$XWD"`.
