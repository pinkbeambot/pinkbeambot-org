# 📝 NOTE SYSTEM — Complete Instructions

## Overview
Notes are for single-author content: research, observations, decisions, ideas, and documentation. They are NOT conversations (use Chats) and NOT work tracking (use Tasks).

---

## Where Notes Live

**Location:** All notes live in the shared `Notes/` directory

```
pinkbeam/
├── Notes/                       ← All notes (shared)
│   ├── 🗂️ NOTES.md            ← Index of all notes
│   ├── PRICING-STRATEGY-2026-02.md
│   ├── ADR-001-gateway-fix.md
│   └── ...
└── Org Chart/                   ← Employee directories
    ├── CEO/
    ├── CTO/
    └── ...
```

**Golden Rule:** Notes are shared. Everyone contributes to the same knowledge base.

---

## Before Creating a Note — CHECK FIRST

**Always check if a relevant note already exists.**

1. Check your Notes folder for similar topics
2. Search vault for keywords
3. If relevant note exists → **UPDATE it**, don't duplicate
4. If no relevant note exists → Create new

**Examples of when to update vs create new:**
- **Update:** Add new findings to existing research note
- **Update:** Update decision note with new information
- **Create New:** Completely different topic or time period

---

## How to Create a Note

### Step 1: Copy Template
Copy `_TEMPLATES/_NOTE.md` to **your** Notes folder.

### Step 2: Name the File

**Option A — Date-based (for time-sensitive):**
`YYYY-MM-DD-topic.md`
- `2026-02-06-weekly-strategy.md`
- `2026-02-10-user-research-synthesis.md`

**Option B — Descriptive (for evergreen):**
`TOPIC-description.md`
- `ARCHITECTURE-edge-computing-strategy.md`
- `DECISION-stripe-vs-paddle.md`
- `RESEARCH-competitor-analysis.md`

**Option C — Standard formats:**
- `ADR-XXX-decision-name.md` — Architecture Decision Records
- `RETRO-YYYY-MM-DD.md` — Retrospectives
- `SPEC-feature-name.md` — Feature specifications

### Step 3: Fill Frontmatter
```yaml
---
created: 2026-02-06T12:30
updated: 2026-02-06T12:30
type: note
author: @Your-Role        ← Your role code
category: research        ← idea | research | decision | reference | strategy | retrospective
tags: [stripe, pricing]   ← For discovery
status: draft             ← draft | review | final | archived
---
```

### Step 4: Write Content
Fill in the sections:
- **Note** — Main content
- **Context** — Why you created this
- **Key Points** — Bullet summary
- **Related** — Links to Tasks, Chats, other Notes
- **Attachments** — Files, screenshots

---

## Note Categories

Use the appropriate `category` in frontmatter:

| Category | Use For | Example |
|----------|---------|---------|
| `idea` | Concepts, possibilities | "Idea for new engine type" |
| `research` | Findings, analysis | "User research on scheduling pain points" |
| `decision` | Documented choices | "Decision: Use Stripe over Paddle" |
| `reference` | How-to guides, docs | "Cloudflare Workers best practices" |
| `strategy` | Long-term planning | "Q2 Growth Strategy" |
| `retrospective` | Post-mortems, reviews | "February Retrospective" |

---

## When to Use Note vs Chat vs Task

| Use Note For | Use Chat For | Use Task For |
|--------------|--------------|--------------|
| Research findings | Back-and-forth discussion | Work to be done |
| Decision documentation | Questions & answers | Has assignee & due date |
| Observations & insights | Coordination | Requires verification |
| Meeting summaries | Conflict resolution | Has work log |
| Ideas & concepts | Multiple perspectives | Trackable progress |
| Technical documentation | Building consensus | Completion criteria |

**Simple rule:**
- **One author** → Note
- **Multiple authors, conversation** → Chat
- **Work to complete** → Task

---

## How to Update a Note

Unlike Chats (append-only), Notes are **living documents** that get updated.

### Minor Updates
- Edit content directly
- Update `updated` timestamp in frontmatter
- Add to edit history if significant

### Major Updates
If adding substantial new information:
1. Update the content
2. Update `updated` timestamp
3. Consider adding a section: `## Update (YYYY-MM-DD)`
4. Update `status` if moving from draft → final

### Archiving
When note is no longer current:
- Change `status: archived`
- Add note at top: `**Archived: Superseded by [[new-note]]**`
- Don't delete — history matters

---

## Cross-Linking Notes

**Link to related tasks:**
```markdown
## 🔗 Related
- Implementation: [[TASK-001-stripe-integration]]
```

**Link to related chats:**
```markdown
## 🔗 Related
- Discussion: [[2026-02-06-CTO-architecture-chat]]
```

**Link to other notes:**
```markdown
## 🔗 Related
- Previous research: [[2026-01-15-payment-research]]
- Related decision: [[DECISION-pricing-strategy]]
```

**Link from task/chat to note:**
```markdown
See [[2026-02-06-architecture-decision]] for technical context.
```

---

## Note Best Practices

### Start with Context
Always explain WHY this note exists:
```markdown
## 💭 Context
Conducted 5 user interviews to understand scheduling pain points.
```

### Use Structure
- Headers for organization
- Bullet points for readability
- Bold for emphasis
- Code blocks for technical content

### Summarize at the Top
Key Points section lets readers get the gist quickly:
```markdown
## 🔑 Key Points
- 80% of users struggle with calendar coordination
- Current solutions require 3+ back-and-forth emails
- Users would pay premium for automated booking
```

### Link Generously
Notes are most valuable when connected to other work.

### Keep Updated
Stale notes are misleading. Update or archive.

---

## Special Note Types

### Architecture Decision Records (ADRs)

Name: `ADR-XXX-short-description.md`

Template:
```markdown
---
created: 2026-02-06T12:30
type: note
author: @CTO
category: decision
tags: [architecture]
status: final
---

# ADR-001: Use Cloudflare D1 for Primary Database

## Status
Accepted

## Context
What is the issue that we're seeing that is motivating this decision...

## Decision
We will use Cloudflare D1 for our primary database...

## Consequences
### Positive
- Edge deployment
- No cold start latency for DB

### Negative  
- SQLite limitations
- Migration complexity

## Alternatives Considered
- PostgreSQL on Supabase
- PlanetScale MySQL
```

### Retrospectives

Name: `RETRO-YYYY-MM-DD.md`

Sections:
- What went well
- What didn't go well
- What we learned
- Action items (link to Tasks)

---

## Note Hygiene

### Regular Review
Monthly review of your Notes folder:
- Update outdated information
- Archive superseded notes
- Link orphaned notes to active work

### Naming Consistency
Pick a convention and stick to it:
- Date-first for time-bound content
- Descriptive for evergreen content
- Prefixes for special types (ADR-, RETRO-, SPEC-)

### Don't Duplicate
If information exists elsewhere, link to it rather than copy.

---

## Folder Index Tracking — REQUIRED

**Every note SHOULD be tracked in the author's folder index file.**

### What is the Folder Index?
Each Notes folder contains an index file: `🗂️ NOTES FOLDER.md`

This file provides an at-a-glance view of all notes for that role.

### When Creating a Note — UPDATE THE INDEX

**Step 1:** Create the note file in your Notes folder
**Step 2:** Update `🗂️ NOTES FOLDER.md` in your Notes folder

### Index File Format

```markdown
## 📝 Recent Notes

| Note | Date | Category |
|------|------|----------|
| [[2026-02-06-weekly-strategy]] | 2026-02-06 | strategy |
| [[ADR-001-database-choice]] | 2026-02-05 | decision |
| [[Research-user-interviews]] | 2026-02-04 | research |

## 🏷️ Tags Used
- #architecture
- #strategy
- #research
```

### Index Maintenance Rules

1. **Add immediately** when creating a note
2. **Update** when note status changes significantly
3. **Organize by category** for easy browsing
4. **Never delete** — notes are knowledge history

---

## Cross-Linking — MANDATORY

**Every note MUST link to related work.**

### Link to Related Tasks
```markdown
## 🔗 Related
- Implementation: [[TASK-001-stripe-integration]]
- Depends on: [[TASK-003-gateway-fix]]
```

### Link to Related Chats
```markdown
## 🔗 Related
- Discussion: [[2026-02-06-CTO-architecture-chat]]
- Decision context: [[2026-02-05-CEO-priority-alignment]]
```

### Link to Other Notes
```markdown
## 🔗 Related
- Previous research: [[2026-01-15-payment-research]]
- Related decision: [[ADR-001-database-choice]]
- Strategic context: [[2026-02-01-q2-strategy]]
```

### Link from Task to Note
```markdown
See [[2026-02-06-architecture-decision]] for technical context.
```

### Link from Chat to Note
```markdown
Decision documented in [[ADR-001-database-choice]]
```

---

## Why Cross-Linking Matters

Without cross-linking:
- Knowledge is scattered and hard to find
- Decisions lack context
- Tasks lack background
- Duplication happens

With cross-linking:
- Everything is connected
- Context is one click away
- Knowledge graph emerges
- Future you (and others) can navigate effortlessly

**Rule: If it relates, link it.**

---

## Quick Reference

| Action | Where | How |
|--------|-------|-----|
| Create note | Your Notes folder | Copy `_NOTE.md`, fill frontmatter |
| Check existing | Your Notes folder | Look before creating |
| Update note | Same file | Edit content, update `updated` timestamp |
| Update index | `🗂️ NOTES FOLDER.md` | Add to table |
| Archive note | Same file | Change `status: archived` |
| Link related | `## 🔗 Related` section | Use `[[filename]]` wiki links |

---

*Note System v1.0 — Knowledge capture, single-author documentation, fully cross-linked.*
