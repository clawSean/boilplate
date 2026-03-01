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
- **Automated curation** — Cron jobs that route content to the right places
- **Weekly maintenance** — Pruning, graduation, and digests
- **Monthly self-review** — System audits and skill feedback loops

---

## Contents

### [HOW-IT-WORKS.md](./HOW-IT-WORKS.md)
The complete architecture documentation. Start here.

### System Files (`system/`)
These control how memory flows and gets processed:

| File | Purpose |
|------|---------|
| `MEMORY.md` | Working memory + index to everything (~500 line cap) |
| `HEARTBEAT.md` | Instructions for the 30-min heartbeat job |
| `CURATION.md` | Routing decision tree for the 5-hour curation job |
| `COMPILE.md` | Weekly pruning and graduation instructions |
| `REEVALUATE.md` | Monthly system audit and skill review |

### Templates (`templates/`)
Example files for per-entity storage:

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
├── CURATION.md                   # Curation instructions
├── COMPILE.md                    # Weekly compile instructions
├── REEVALUATE.md                 # Monthly review instructions
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
