# VAULT-MAINTENANCE.md — Vault Cleanup Tracking

This file tracks vault maintenance decisions and history.

## Scope:
Files **outside** PARA folders (0-Inbox, 1-Projects, 2-Areas, 3-Resources, 4-Archive) that need attention:
- Empty .md files
- Potential duplicates (by title similarity or content)
- Orphaned attachments
- Files that should be filed into PARA

## Report Template:

# Vault Maintenance Report

- Run (UTC): 2026-01-15T14:06:13Z
- Markdown files: 8151
- Outside PARA: 6441
- Empty .md: 194
- Exact title duplicate groups: 900
- Fuzzy title pairs (>=0.92): 6463
- Near-duplicate content pairs (simhash<=3): 20043
- Attachments: 1248
- Orphaned attachments: 148

## Decision Log
Track decisions here so future runs know what was already reviewed.

### Ignored (intentional root-level files)
<!-- Files that should stay at root, e.g., README.md -->

### Filed
<!-- Date | File | Moved to | Reason -->

### Deleted
<!-- Date | File | Reason -->

### Merged (duplicates)
<!-- Date | Kept | Deleted | Reason -->

<!-- ### Other relevant sections as needed -->