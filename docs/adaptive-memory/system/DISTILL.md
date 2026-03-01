# DISTILL.md

Instructions for the **weekly distillation job** — the intelligent extraction pass that identifies lessons, graduates content from memory to knowledge, and captures patterns.

**Trigger:** Weekly cron (Sunday, after COMPILE)  
**Model:** Sonnet (needs judgment and pattern recognition)  
**Runtime:** Isolated session, ~10-15 min

---

## Purpose

DISTILL is the **learner** of the memory system. While COMPILE handles mechanical organization, DISTILL does the intelligent work:

- **Extract** lessons from experiences
- **Graduate** mature content from memory → knowledge
- **Identify** patterns and contradictions
- **Capture** insights before they fade

This requires judgment — deciding what's worth keeping long-term and how to frame it.

---

## Phase 1: Lesson Extraction

Scan the week's daily files for implicit lessons.

### 1.1 Look For
- Mistakes and corrections ("turns out...", "actually...", "I was wrong about...")
- Friction and frustration ("this kept failing", "had to work around...")
- Successful patterns ("this worked well", "the trick is...")
- Surprises ("didn't expect...", "interesting that...")

### 1.2 Extract Format
For each lesson found:
```markdown
## Lesson Title
**Learned:** [date] (source reference)
**Context:** What happened
**Rule:** What to do / not do
```

### 1.3 Route to Domain
- Security issues → `knowledge/lessons/security.md`
- Communication patterns → `knowledge/lessons/communication.md`
- Technical gotchas → `knowledge/lessons/technical.md`
- Social/per-person → `knowledge/lessons/social.md`
- Skill/tool usage → `knowledge/lessons/skills.md`

### 1.4 Check for Duplicates
Before adding, scan the target file for similar lessons. Update existing entries rather than duplicating.

---

## Phase 2: Graduation Assessment

Identify content ready to move from memory → knowledge.

### 2.1 Graduation Criteria
Content is ready when:

| Criterion | Question |
|-----------|----------|
| **Factual** | Is it "how X works" rather than "what we did with X"? |
| **Stable** | Has it been unchanged for 2+ weeks? |
| **Substantial** | 5+ facts or 5+ references? |
| **Transferable** | Would it help someone with no relationship context? |

### 2.2 Scan Locations
Check these for graduation candidates:
- `MEMORY.md` — Technical sections, inline entities
- `memory/by-topic/` — Factual content mixed with experiential
- `memory/daily/` — Recurring factual information

### 2.3 Graduate Process
1. Extract factual content
2. Rewrite without temporal language ("we learned" → "X works by...")
3. Create/update file in `knowledge/topics/` or `knowledge/entities/`
4. Update source — leave pointer or remove graduated content
5. Update MEMORY.md structure map if new file created

### 2.4 What Stays in Memory
Never graduate:
- Relationship context → stays in `by-contact/`
- Group dynamics → stays in `by-channel/`
- Personal opinions and preferences
- Temporal context ("this month we're focused on...")
- Inside jokes and personality

---

## Phase 3: Contradiction Detection

Cross-reference for inconsistencies.

### 3.1 Check For
- MEMORY.md says X, but a topic file says Y
- Older daily file contradicts newer information
- Lessons that conflict with each other
- Outdated facts that have been corrected

### 3.2 Resolution
- **Fresher wins** — update the stale source
- **Specific wins** — topic file is more authoritative than MEMORY.md mention
- **When uncertain** — flag for human review in weekly digest

---

## Phase 4: Pattern Recognition

Look for emerging themes.

### 4.1 Recurring Topics
- Same subject mentioned 3+ times this week?
- Consider creating a dedicated topic file

### 4.2 Relationship Patterns
- Communication style insights for people
- Group dynamic shifts
- Update `by-contact/` or `by-channel/` files

### 4.3 Project Patterns
- Progress patterns (momentum, blockers)
- Decision patterns (what criteria get used)
- Update `knowledge/topics/projects.md` or relevant file

---

## Phase 5: Update Weekly Digest

Append distillation findings to the weekly digest created by COMPILE.

### 5.1 Add Section
```markdown
## Distillation

### Lessons Extracted
- [New lesson] → knowledge/lessons/[domain].md

### Content Graduated
- [Item] moved from [source] → [destination]

### Contradictions Resolved
- [What was inconsistent] → [resolution]

### Patterns Noted
- [Emerging pattern worth watching]
```

---

## Output Summary

At the end of distillation:

1. **New lessons** added to `knowledge/lessons/*.md`
2. **Graduated content** moved to `knowledge/topics/` or `knowledge/entities/`
3. **Sources updated** — pointers or content removed
4. **Contradictions resolved** — stale sources updated
5. **Weekly digest updated** — distillation section added
6. **Structure map current** — MEMORY.md reflects changes

---

## Timing

| Phase | Expected Duration |
|-------|-------------------|
| Lesson Extraction | 3-4 min |
| Graduation Assessment | 3-4 min |
| Contradiction Detection | 2-3 min |
| Pattern Recognition | 2-3 min |
| Update Digest | 1-2 min |
| **Total** | **10-15 min** |

---

## Why Sonnet?

DISTILL requires judgment:
- Is this a lesson or just a fact?
- Is this ready to graduate or still evolving?
- Is this a contradiction or a nuance?
- Is this a pattern or coincidence?

Haiku can follow rules. Sonnet can make judgment calls.

---

*Created: 2026-03-01*
