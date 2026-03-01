# COMPILE.md

Instructions for the **weekly compilation job** — the mechanical organization pass that archives, promotes, prunes, and produces a weekly digest.

**Trigger:** Weekly cron (Sunday)  
**Model:** Haiku (rule-based, no judgment needed)  
**Runtime:** Isolated session, ~5-10 min

---

## Purpose

COMPILE is the **organizer** of the memory system. It handles mechanical tasks with clear rules:

- **Archive** old daily files
- **Promote** entities that exceed thresholds
- **Prune** obviously stale content
- **Digest** the week into a summary

No judgment calls — just "if X then Y" operations.

---

## Phase 1: File Organization

Keep the workspace tidy.

### 1.1 Archive Old Daily Files
Move daily files older than 30 days:
```bash
# Files older than 30 days → memory/archive/YYYY-MM/
mv memory/daily/2026-01-*.md memory/archive/2026-01/
```

### 1.2 Clean Up
- Remove empty files (0 bytes)
- Remove duplicate files (same content)
- Use `trash` instead of `rm` (recoverable)

### 1.3 Verify Structure
Ensure directories exist:
- `memory/daily/`
- `memory/archive/`
- `memory/by-contact/`
- `memory/by-channel/`
- `memory/by-topic/`
- `memory/ideas/`
- `knowledge/topics/`
- `knowledge/entities/`
- `knowledge/lessons/`
- `knowledge/reference/`

---

## Phase 2: Entity Promotion

Move overgrown content to dedicated files.

### 2.1 Check MEMORY.md
Scan for entities exceeding thresholds:
- **10+ lines** → promote to own file
- **5+ mentions** → promote to own file

### 2.2 Promotion Routing

| Entity Type | Destination |
|-------------|-------------|
| Person | `memory/by-contact/<channel>-<id>.md` |
| Group | `memory/by-channel/<channel>-g-<name>.md` |
| Named entity (company, place) | `knowledge/entities/<Name>.md` |
| Topic (factual) | `knowledge/topics/<topic>.md` |
| Topic (experiential) | `memory/by-topic/<topic>.md` |

### 2.3 Promotion Steps
1. Create new file from template (`_EXAMPLE-*.md`)
2. Copy content from MEMORY.md
3. Replace in MEMORY.md with one-liner pointer
4. Update Memory Structure Map in MEMORY.md

---

## Phase 3: Staleness Pruning

Remove clearly outdated content.

### 3.1 Prune Criteria (mechanical, no judgment)
Remove entries that are:
- **30+ days old** AND marked as temporary/transient
- **Completed reminders** (past due date, marked done)
- **Superseded** — explicitly replaced by newer entry
- **Orphaned references** — link to file that no longer exists

### 3.2 What NOT to Prune
Leave for DISTILL to evaluate:
- Old but potentially relevant content
- Entries requiring judgment about relevance
- Anything uncertain

### 3.3 Safety
- Use `trash` not `rm`
- Log what was pruned in the weekly digest

---

## Phase 4: Weekly Digest

Create a factual summary of the week.

### 4.1 Create File
```
memory/daily/YYYY-MM-DD-weekly-digest.md
```

### 4.2 Digest Structure
```markdown
# Weekly Digest — [Date Range]

## Activity Summary
- Daily files created: [count]
- Sessions recorded: [count]
- People interacted with: [list]

## File Operations
- Files archived: [count]
- Entities promoted: [list]
- Content pruned: [list]

## Structure Status
- MEMORY.md lines: [count] / 500
- memory/ files: [count]
- knowledge/ files: [count]

## Open for DISTILL
- [Items flagged for intelligent review]

---
*Compiled: [timestamp]*
```

### 4.3 Keep It Factual
COMPILE produces facts, not analysis:
- ✅ "5 daily files created"
- ❌ "It was a productive week"

---

## Phase 5: Structure Integrity Check

Verify the memory system is healthy.

### 5.1 Check References
- Do all files in MEMORY.md structure map exist?
- Are there orphaned files not referenced anywhere?

### 5.2 Check Sizes
```bash
wc -l MEMORY.md        # Should be < 500
du -sh memory/         # Monitor growth
du -sh knowledge/      # Monitor growth
```

### 5.3 Flag Issues
If problems found, note in weekly digest for DISTILL/AUDIT to address.

---

## Output Summary

At the end of compilation:

1. **Old files archived** → `memory/archive/YYYY-MM/`
2. **Entities promoted** → dedicated files
3. **Stale content pruned** → recoverable in trash
4. **Weekly digest created** → `memory/daily/YYYY-MM-DD-weekly-digest.md`
5. **Structure verified** → issues flagged if any

---

## Timing

| Phase | Expected Duration |
|-------|-------------------|
| File Organization | 1-2 min |
| Entity Promotion | 2-3 min |
| Staleness Pruning | 1-2 min |
| Weekly Digest | 1-2 min |
| Structure Check | 1 min |
| **Total** | **5-10 min** |

---

## Why Haiku?

COMPILE needs no judgment:
- Threshold exceeded? Promote. (rule)
- File older than 30 days? Archive. (rule)
- Entry marked done? Prune. (rule)

Save the smart model for DISTILL.

---

## Handoff to DISTILL

COMPILE runs first, then DISTILL runs on the organized workspace:

```
COMPILE (Haiku) → DISTILL (Sonnet)
     │                  │
     ▼                  ▼
  Organize          Extract
  Archive           Graduate  
  Promote           Learn
  Prune             Identify patterns
  Digest            Update digest
```

---

*Updated: 2026-03-01*
