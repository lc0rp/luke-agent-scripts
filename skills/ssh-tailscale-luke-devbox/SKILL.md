---
name: ssh-tailscale-luke-devbox
description: How to connect to Luke's Devbox over Tailscale via SSH.
---

# SSH to Luke's Devbox via Tailscale

## When to use

Use this when you need terminal access to Luke's Devbox. If you are already on devbox, you don't need this.

## Connection details

- Host: 100.99.173.30 (Tailscale IP)
- User: ubuntu
- Key: ~/.ssh/acfs_ed25519
- Auth: publickey only; password auth is rejected
- Network: Tailscale only; do not use WAN port 22

## Connect

```bash
ssh dev
```

## Optional SSH config

Add to `~/.ssh/config` for a short alias:

```ssh-config
Host dev
  HostName 100.99.173.30
  User ubuntu
  IdentityFile ~/.ssh/acfs_ed25519
```

Then:

```bash
ssh dev
```

## Notes

- If SSH fails, confirm Tailscale is up on both ends.
- Sudo on the dev still requires ubuntu password; do not attempt sudo changes remotely.
- If the host key changes, remove/update the old entry in `~/.ssh/known_hosts`.
