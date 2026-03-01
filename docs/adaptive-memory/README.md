# Adaptive Memory System

**A cognitive architecture for persistent AI agents**

This folder extends OpenClaw's default agent setup with a complete memory system based on the four memory systems from cognitive psychology: Working, Episodic, Semantic, and Procedural memory.

---

## Quick Start

1. Read `HOW-IT-WORKS.md` for the full architecture
2. Copy the `system/` files to your agent's workspace
3. Copy the `templates/` to your `memory/` folder
4. Update your `AGENTS.md` with the session loading rules from HOW-IT-WORKS.md
5. Set up cron jobs for automated memory maintenance

---

## What This Adds to OpenClaw

OpenClaw provides the foundation files (`SOUL.md`, `IDENTITY.md`, `USER.md`, `AGENTS.md`, `TOOLS.md`). This system adds:

- **Structured memory storage** — `memory/` and `knowledge/` directories
- **Automated curation** — Routes content to the right places every 5 hours
- **Weekly maintenance** — Organize (COMPILE) then extract learnings (DISTILL)
- **Monthly self-review** — System health and skill feedback (AUDIT)

---

## The Five Jobs

| Job | Frequency | Model | Purpose |
|-----|-----------|-------|---------|
| **HEARTBEAT** | 30 min | Main | Capture notable content → daily files |
| **CURATION** | 5 hours | Haiku | Route content → memory/knowledge |
| **COMPILE** | Weekly | Haiku | Organize, archive, promote, prune |
| **DISTILL** | Weekly | Sonnet | Extract lessons, graduate content |
| **AUDIT** | Monthly | Sonnet+ | System health, skill review, security |

### Intelligence Separation

```
CONTINUOUS:  Heartbeat → Curation
             (capture)   (route)

WEEKLY:      COMPILE  →  DISTILL
             (Haiku)     (Sonnet)
             organize    extract & learn

MONTHLY:     AUDIT
             (Sonnet+)
             reflect & improve
```

---

## Contents

### [HOW-IT-WORKS.md](./HOW-IT-WORKS.md)
The complete architecture documentation. Start here.

### System Files (`system/`)

| File | Model | Purpose |
|------|-------|---------|
| `MEMORY.md` | — | Working memory template (~500 line cap) |
| `HEARTBEAT.md` | Main | 30-min capture instructions |
| `CURATION.md` | Haiku | 5-hour routing decision tree |
| `COMPILE.md` | Haiku | Weekly organization (mechanical) |
| `DISTILL.md` | Sonnet | Weekly extraction (intelligent) |
| `AUDIT.md` | Sonnet+ | Monthly review (reflective) |

### Templates (`templates/`)

| File | Purpose |
|------|---------|
| `_EXAMPLE-contact.md` | Template for per-person memory |
| `_EXAMPLE-channel.md` | Template for per-group memory |
| `_EXAMPLE-topic.md` | Template for topic/knowledge files |

---

## Directory Structure

After setup, your workspace adds these directories:

```
workspace/
├── [OpenClaw defaults]           # SOUL.md, IDENTITY.md, etc.
├── MEMORY.md                     # Working memory + index
├── HEARTBEAT.md                  # Heartbeat instructions  
├── CURATION.md                   # Curation routing
├── COMPILE.md                    # Weekly organization
├── DISTILL.md                    # Weekly extraction
├── AUDIT.md                      # Monthly review
│
├── memory/                       # EPISODIC — what happened
│   ├── daily/                    # Raw daily logs
│   ├── by-contact/               # Per-person memory
│   ├── by-channel/               # Per-group memory
│   ├── by-topic/                 # Experiential topics
│   └── ideas/                    # Raw brainstorms
│
└── knowledge/                    # SEMANTIC — what's true
    ├── topics/                   # Factual reference
    ├── entities/                 # Named things
    ├── lessons/                  # Learned rules
    └── reference/                # Stable docs
```

---

## Configuration

See `HOW-IT-WORKS.md` for detailed guidance on:

- **Premier models** for structural work
- **`dmScope: per-channel-peer`** for per-contact memory isolation
- **Isolated sessions** for cron jobs

---

## Academic Foundation

This architecture implements the four memory systems from cognitive psychology:

- **Tulving (1972)** — Episodic vs semantic memory
- **Baddeley & Hitch (1974)** — Working memory model
- **Squire (2004)** — Long-term memory taxonomy

Reference implementation: [ALucek/agentic-memory](https://github.com/ALucek/agentic-memory)

---

*Part of the [Lobster Boilerplate](https://github.com/clawSean/lobster-boilerplate) project*
