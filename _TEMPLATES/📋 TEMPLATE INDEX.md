# 📋 Template Library

Quick reference for creating tasks, notes, and employees.

## Document Templates

| Template | Purpose | Instructions |
|----------|---------|--------------|
| `_TASK.md` | Work tracking | See `_INSTRUCTIONS/TASK-SYSTEM.md` |
| `_NOTE.md` | Research & documentation | See `_INSTRUCTIONS/NOTE-SYSTEM.md` |

## Complete Documentation

See `_INSTRUCTIONS/MASTER-GUIDE.md` for full system documentation.

| Guide | Contents |
|--------|----------|
| `MASTER-GUIDE.md` | Overview, golden rules, workflows |
| `TASK-SYSTEM.md` | Complete task instructions |
| `NOTE-SYSTEM.md` | Complete note instructions |

## Key Principles

### 1. Check Before Creating
Always check if a document already exists before creating new.

### 2. Update Indexes
Every new task/note MUST be added to the folder index:
- Tasks: `Tasks/TASKS.md`
- Notes: `Notes/🗂️ NOTES.md`

### 3. Cross-Link Everything
Every document MUST link to related work using `[[filename]]`.

### 4. Location Matters
| Type | Location |
|------|----------|
| Tasks | `Tasks/` (shared) |
| Notes | `Notes/` (shared) |
| Employee Files | `Org Chart/{ROLE}/` |

## Employee Template

| Template | Purpose |
|----------|---------|
| `_EMPLOYEE/` | Creating new AI agent employees |

### Employee Structure (4 Files)
```
_EMPLOYEE/
├── README.md           # Employee dashboard
├── SHIFT-PROTOCOL.md   # Shift instructions
├── IDENTITY.md         # Role definition
└── SKILLS.md           # Capabilities matrix
```

**Note:** Tasks and Notes are now shared in top-level directories.

## File Naming Conventions

| Type | Format | Example |
|------|--------|---------|
| Task | `TASK-XXX-brief-description.md` | `TASK-001-stripe-integration.md` |
| Note | `TOPIC-description.md` | `PRICING-STRATEGY-2026-02.md` |
| MoC | `[MoC] Title.md` | `[MoC] Org Chart.md` |

## Role Codes for @Mentions

- `@FOUNDER` — Human founder (spending approval only)
- `@CEO` — Chief Executive Officer
- `@CTO` — Chief Technology Officer
- `@CMO` — Chief Marketing Officer
- `@PM` — Product Manager
- `@ENG-FE` — Frontend Engineer
- `@ENG-BE` — Backend Engineer

---

*Templates v2.0 — Simplified structure*
