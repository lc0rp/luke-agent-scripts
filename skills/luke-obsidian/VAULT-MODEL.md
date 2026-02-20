# MODEL.md - Obsidian Vault Mental Model (Agent vs User)

When working with this vault, the following **two distinct "profiles"** must not be conflated:

## 1) You, the agent - Whom the agent can refer to as "me"
- **Soul / mission / boundaries:** `SOUL.md`
- **Agent identity metadata:** `IDENTITY.md`
- **Agent voice (how the agent speaks):** defined by `SOUL.md` + the surrounding system/dev instructions, and also influenced by `USER.md` (to match Luke's preferences)

The agent's profile exists to keep the assistant consistent and safe.

## 2) Luke (the human user, whom the agent assists, and can refer to as "you" or "Luke")
- **Luke identity (who Luke is):** `USER.md`, and any files it links to, like `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Identity.md`
- **Luke voice (how Luke communicates / how to write "as Luke"):** `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Voice.md`, also linked from `USER.md`
- **Luke context (what Luke is working on):** see "Context layer" below

Luke's profile exists so the agent (you) can produce notes and drafted text that match Luke.

## Interaction Rules (must-follow)
- **Never treat Luke's identity/voice as the agent's identity/voice.**
- When chatting *as the agent*, use **agent voice**, but be compatible with Luke's preferences (casual tone, clarity).
- When drafting text *on Luke's behalf* (emails/messages/docs), use **Luke voice** from `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Voice.md`.
- When capturing notes about Luke's life/work, Luke's identity provides factual/background grounding, but it is not "agent identity".

## Mapping to the ["portable context" article](https://rundatarun.io/p/i-built-a-personal-memory-system)
The article's terms (Identity / Voice / Context / Memory) are primarily about the **human user's portable context**.

- **Article.Identity** → Luke.Identity (`/data/projects/Obsidian-Notes/3-Resources/People/Luke/Identity.md`)
- **Article.Voice** → Luke.Voice (`/data/projects/Obsidian-Notes/3-Resources/People/Luke/Voice.md`)
- **Article.Context** → Luke's current priorities/projects → now `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Context Protocol.md`
- **Article.Memory** → durable facts/preferences/decisions, captured in this workspace's `memory/YYYY-MM-DD.md` (raw) and curated `MEMORY.md` (long-term)

Separately, the agent has its own identity/voice (SOUL/IDENTITY), but that is **not** what the article means by "Identity/Voice".

## Context layer (implemented)
Luke's context is organized in layers. See `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Context Protocol.md` for the full spec.

**Layer 1 — Cold (rarely changes):**
- `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Identity.md`
- `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Voice.md`

**Layer 2 — Warm (updates periodically):**
- `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Priority system.md`
- `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Work context.md`
- `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Life context.md`

**Layer 3 — Hot (updates frequently):**
- Daily/weekly notes
- Project-specific notes

---

## Scribe Boot-Up Checklist
When starting a session, load context in this order:

1. **Agent self** (workspace files — loaded automatically via AGENTS.md):
   - `SOUL.md` — Agent identity/mission
   - `IDENTITY.md` — Agent metadata
   - `USER.md` — pointer to Luke
   - `MEMORY.md` — Agent long-term memory (main session only)
   - `memory/YYYY-MM-DD.md` — recent session logs

2. **Luke Layer 1** (always, for any substantive work):
   - `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Identity.md`
   - `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Voice.md`

3. **Luke Layer 2** (for prioritization/context):
   - `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Priority system.md`
   - `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Work context.md` and/or `/data/projects/Obsidian-Notes/3-Resources/People/Luke/Life context.md`

4. **Luke Layer 3** (as needed):
   - Relevant daily/weekly/project notes
