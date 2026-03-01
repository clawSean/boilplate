# AUDIT.md

Instructions for the **monthly audit job** — a deep review of the memory system, foundation files, skills, and overall health.

**Trigger:** Monthly cron (1st of each month)  
**Model:** Sonnet or higher (needs reasoning depth)  
**Runtime:** Isolated session, ~20-30 min

---

## Purpose

AUDIT is the **auditor** of the memory system. While COMPILE organizes and DISTILL extracts, AUDIT steps back to ask:

- **Is the system working?** — Are heartbeat, curation, compile, distill doing their jobs?
- **Am I who I should be?** — Have I drifted from my values or identity?
- **Are my skills sharp?** — What tools caused friction? What could improve?
- **Is anything at risk?** — Security issues, exposed data, trust violations?

This is the monthly reflection that keeps the agent aligned and improving.

---

## Phase 1: Foundation File Review

Check each foundational file for accuracy and drift.

### 1.1 SOUL.md
- Does this still reflect who I am?
- Have I developed traits not captured here?
- Any values I've drifted from that need reinforcement?
- Any boundaries I've violated that need strengthening?

### 1.2 IDENTITY.md
- Is the identity description still accurate?
- Has my "look" or "vibe" evolved?
- Any new defining characteristics?

### 1.3 USER.md
- Is the info about the human(s) still current?
- Anything learned that should be added?
- Any outdated context to remove?

### 1.4 AGENTS.md
- Are the operational rules working?
- Any guidelines I keep violating? (need adjustment)
- Any new patterns that should become guidelines?
- Are the session loading rules still correct?

### 1.5 TOOLS.md
- Are the documented paths still correct?
- Any new tools or credentials to add?
- Any stale entries to remove?

**Output:** Propose edits to any file that needs updating. For significant changes, flag for human review.

---

## Phase 2: Memory System Health

Audit the memory pipeline.

### 2.1 Heartbeat Review
- Check last 10 daily files — are they substantive or noise?
- Is heartbeat capturing the right things?
- Is anything important being missed?
- Is heartbeat too verbose? Too sparse?

### 2.2 Curation Review
- Are items routing to correct locations?
- Check for duplicates across files
- Are the routing rules in CURATION.md still accurate?
- Sample 5 recent routing decisions — were they correct?

### 2.3 COMPILE Review
- Is entity promotion working?
- Is archival happening correctly?
- Are weekly digests useful?

### 2.4 DISTILL Review
- Are lessons being extracted?
- Is graduation happening appropriately?
- Are contradictions being caught?

### 2.5 Structure Map Check
- Does MEMORY.md's structure map reflect reality?
- Any orphaned files that should be linked?
- Any folders that have grown unwieldy?

**Output:** Note any pipeline issues. Propose fixes or flag for human review.

---

## Phase 3: Skill Review

Evaluate tool and skill usage.

### 3.1 Identify Skills Used
Scan daily files from the past month for skill invocations:
- Explicit skill mentions
- Tool patterns that map to skills
- API calls, CLI commands

### 3.2 For Each Skill Used 3+ Times

**Check for friction:**
- Any failures or errors?
- Slow responses or timeouts?
- Unexpected behavior?
- Missing parameters I keep forgetting?

**Document findings:**
```markdown
# skills/<skill>/NOTES.md

## Usage Notes (YYYY-MM)

### Gotchas
- [date]: Issue description and workaround

### Best Practices
- [date]: Pattern that works well

### Quirks
- [date]: Unexpected behavior to remember
```

### 3.3 Cross-Skill Patterns
Look for lessons that apply across skills:
- Rate limiting patterns
- Error handling approaches
- Authentication patterns

**Add to:** `knowledge/lessons/skills.md`

### 3.4 Skill Improvement Proposals
For skills with significant friction, propose:
- Updates to the skill's SKILL.md
- New helper scripts or wrappers
- Alternative approaches

**Output:** Updated `skills/*/NOTES.md` files, lessons, and proposals.

---

## Phase 4: Lessons Validation

Audit the lessons system.

### 4.1 Review Existing Lessons
For each file in `knowledge/lessons/`:
- Is each lesson still valid?
- Have circumstances changed?
- Any lessons I keep forgetting? (need better placement)
- Any duplicate or conflicting lessons?

### 4.2 Lessons Freshness
- Are there lessons older than 6 months?
- Do they still apply?
- Mark outdated lessons for removal or update

### 4.3 Lessons Coverage
- Are there domains without lessons? (gap)
- Are there experiences without extracted lessons? (missed opportunity)

**Output:** Updated lessons files, removal of stale lessons.

---

## Phase 5: Security Audit

Check for vulnerabilities.

### 5.1 Credential Scan
```bash
grep -r "Bearer\|sk-\|password\|secret\|token\|api.key" memory/daily/
```
If anything found → flag for immediate attention.

### 5.2 File Permission Check
- Any files that shouldn't be readable?
- Any secrets stored in plain text?

### 5.3 Access Review
- Is trust tier documentation accurate?
- Any users who should have different access?
- Any concerning access patterns?

### 5.4 Sensitive Content
- Any medical, financial, or personal details that shouldn't be stored?
- Any content that could be embarrassing if leaked?

**Output:** Immediate flags for any security issues found.

---

## Phase 6: Meta-Review

Evaluate the evaluation.

### 6.1 Process Check
- Is this audit process working?
- Taking too long? Too shallow?
- Missing important areas?

### 6.2 Cadence Check
- Is monthly the right frequency?
- Should certain phases run more/less often?

### 6.3 Model Check
- Is the model tier appropriate for each job?
- Any jobs that could use a cheaper/better model?

### 6.4 System Evolution
- What would make the memory system better?
- Any architectural changes worth proposing?

**Output:** Propose updates to AUDIT.md, COMPILE.md, DISTILL.md, or system architecture.

---

## Output Summary

After completing all phases, write to `memory/daily/YYYY-MM-DD-audit.md`:

```markdown
# Monthly Audit — [Month Year]

## Foundation Files
- [ ] SOUL.md — [No changes / Proposed X]
- [ ] IDENTITY.md — [No changes / Proposed X]
- [ ] USER.md — [Updated X]
- [ ] AGENTS.md — [No changes / Proposed X]
- [ ] TOOLS.md — [Updated X]

## Memory System Health
- Heartbeat: [working/issues]
- Curation: [working/issues]
- Compile: [working/issues]
- Distill: [working/issues]
- Structure map: [accurate/updated]

## Skills Reviewed
- [skill]: [notes added/no issues]

## Lessons
- Validated: [count]
- Updated: [count]
- Retired: [count]

## Security
- Issues found: [none/list]

## Meta
- Process changes proposed: [none/list]

## Human Review Needed
- [ ] [Item requiring human decision]
```

---

## Timing

| Phase | Expected Duration |
|-------|-------------------|
| Foundation Review | 5-8 min |
| Memory System Health | 3-5 min |
| Skill Review | 5-8 min |
| Lessons Validation | 3-5 min |
| Security Audit | 2-3 min |
| Meta-Review | 2-3 min |
| **Total** | **20-30 min** |

---

## The Three-Job System

```
Weekly:  COMPILE (Haiku)  → DISTILL (Sonnet)
              ↓                   ↓
         Organize            Extract & Learn
         
Monthly: AUDIT (Sonnet+)
              ↓
         Reflect & Improve
```

---

*Updated: 2026-03-01*
