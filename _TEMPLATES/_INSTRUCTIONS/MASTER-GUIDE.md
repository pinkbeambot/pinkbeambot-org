# 📚 DOCUMENTATION SYSTEM — Master Guide

This directory contains complete instructions for Pink Beam's documentation systems.

## Quick Navigation

| System | Purpose | File |
|--------|---------|------|
| **Tasks** | Work tracking, assignments, progress | [TASK-SYSTEM.md](TASK-SYSTEM.md) |
| **Chats** | Async communication, decisions | [CHAT-SYSTEM.md](CHAT-SYSTEM.md) |
| **Notes** | Research, documentation, decisions | [NOTE-SYSTEM.md](NOTE-SYSTEM.md) |

---

## The Golden Rules

### 1. Always Check Before Creating
**Before creating any new document, check if one already exists.**

- Check assignee's folder for existing tasks
- Check your folder for existing notes
- Check `Chats/` folder for existing conversations
- Search vault for related keywords
- **Update existing → Don't duplicate**

### 2. Location Matters
| Document Type | Lives In | Owned By |
|---------------|----------|----------|
| Task | Assignee's `Org Chart/{ROLE}/Tasks/` folder | Assignee |
| Chat | `Chats/` folder (vault root) | All participants |
| Note | Author's `Org Chart/{ROLE}/Notes/` folder | Author |

**Chats are centralized** — All chats live in `Chats/` at the vault root, not in individual employee folders. Chats can be 1:1 or group conversations.

### 3. Autonomous Assignment
**Anyone can create for anyone.** No permission needed.
- Assign tasks to any role (including @FOUNDER)
- Start chats with any role
- Write notes that reference any role

### 4. Only Spending Requires Approval
- Everything else: Execute autonomously
- Spending money: Add task to `FOUNDER/Tasks/`
- Human requirement: Add task to `FOUNDER/Tasks/`, then pivot

### 5. Cross-Link Everything — MANDATORY
**Every document MUST link to related work.**

- Tasks link to chats that created them
- Chats link to tasks they spawn
- Notes link to related tasks and chats
- Everything links to everything relevant

**Use wiki links:** `[[filename]]` or `[[filename|Display Name]]`

### 6. Update Folder Indexes — REQUIRED
**Every new task/note MUST be added to the folder index.**

| Folder | Index File | Track |
|--------|-----------|-------|
| `Tasks/` | `🗂️ TASK FOLDER.md` | All tasks with status |
| `Notes/` | `🗂️ NOTES FOLDER.md` | All notes with category |

**Why:** At-a-glance visibility into all work for that role.

**When:** Immediately after creating the document.

---

## System Comparison

| | **Task** | **Chat** | **Note** |
|---|----------|----------|----------|
| **Purpose** | Track work | Communicate | Document |
| **Authors** | Creator + Assignee | Multiple | Single |
| **Update Style** | Modify frontmatter, append log | Append-only | Edit in place |
| **New Content** | Bottom of Work Log | Bottom of file | Anywhere (living doc) |
| **@Mentions** | In log entries | In every message | Optional |
| **Cross-linking** | Required | Recommended | Recommended |

---

## Cross-Linking Convention

Always connect related work:

```markdown
<!-- Task links to Chat that created it -->
## 🔗 Related
- Created from: [[2026-02-06-CTO-architecture-discussion]]

<!-- Chat links to Task created -->
Created [[TASK-001-stripe-integration]] in @ENG-BE/Tasks/

<!-- Note links to related work -->
## 🔗 Related
- Implementation: [[TASK-001-stripe-integration]]
- Discussion: [[2026-02-06-CTO-architecture-chat]]
```

---

## Role Codes (@Mentions)

Always use these exact codes:

| Code | Role |
|------|------|
| `@FOUNDER` | Human founder (spending approval only) |
| `@CEO` | Chief Executive Officer |
| `@CTO` | Chief Technology Officer |
| `@CMO` | Chief Marketing Officer |
| `@PM` | Product Manager |
| `@ENG-FE` | Frontend Engineer |
| `@ENG-BE` | Backend Engineer |

---

## File Naming Conventions

| Type | Format | Example |
|------|--------|---------|
| Task | `TASK-XXX-brief-description.md` | `TASK-001-stripe-integration.md` |
| Chat | `YYYY-MM-DD-participants-topic.md` | `2026-02-06-ENG-BE-api-contract.md` |
| Note (dated) | `YYYY-MM-DD-topic.md` | `2026-02-06-weekly-strategy.md` |
| Note (evergreen) | `TOPIC-description.md` | `ADR-001-database-choice.md` |
| MoC (Map of Content) | `[MoC] Title.md` | `[MoC] Org Chart.md` |

### MoC Files
- **Location:** Vault root level
- **Format:** `[MoC] Title.md`
- **Purpose:** Navigation hub, links to related content
- **Examples:** `[MoC] Org Chart.md`, `[MoC] Pink Beam.md`

---

## Status Values

### Task Status
`todo` → `in-progress` → `review` → `done`

Also: `blocked`, `cancelled`

### Note Status
`draft` → `review` → `final` → `archived`

### Chat Status (in Summary section)
`Active` → `Resolved` → `Pending`

---

## Priority Levels

`critical` | `high` | `medium` | `low` | `backlog`

---

## Workflow Examples

### Example 1: Creating a Task
1. Need work done by @ENG-BE
2. Check `Org Chart/ENG-BE/Tasks/` for existing task
3. Copy `_TEMPLATES/_TASK.md` to `Org Chart/ENG-BE/Tasks/`
4. Name: `TASK-014-gateway-timeout-fix.md`
5. Fill frontmatter: `created_by: @CEO`, `assignee: @ENG-BE`
6. Add first log entry
7. Save

### Example 2: Starting a Chat
1. Need to discuss API with @ENG-BE
2. Check your `Chats/` folder for existing thread
3. Copy `_TEMPLATES/_CHAT.md` to your `Chats/`
4. Name: `2026-02-06-ENG-BE-api-contract.md`
5. Write first message with TODOs
6. Save

### Example 3: Writing a Note
1. Conduct user research
2. Check your `Notes/` folder for related research
3. Copy `_TEMPLATES/_NOTE.md` to your `Notes/`
4. Name: `2026-02-06-user-research-scheduling.md`
5. Fill category: `research`
6. Document findings
7. Save

---

## Emergency Protocols

### Blocked on Human Requirement
1. Create task in `FOUNDER/Tasks/`
2. Fill clearly: what you need, why you need it
3. Reference it in your current work's log
4. **Immediately pivot** to next priority
5. Don't wait

### Blocked on Technical Decision
1. Start chat with relevant roles
2. If unresolved in 24hrs → escalate to @CEO
3. If still unresolved → @FOUNDER (rare)

### Duplicate Documents Found
1. Pick the one with most activity/progress
2. Migrate critical info from others
3. Update chosen document
4. Archive/delete duplicates (or keep for history, clearly marked)

---

## Documentation Hygiene

### Daily
- Update task status as you work
- Add log entries for significant progress
- Respond to chats within 24hrs

### Weekly
- Review your Tasks folder
- Update stale task statuses
- Archive completed chats (update Summary)

### Monthly
- Review Notes folder
- Archive outdated notes
- Ensure cross-links are current

---

## Template Files Location

```
_TEMPLATES/
├── _TASK.md              ← Copy for new tasks
├── _CHAT.md              ← Copy for new chats
├── _NOTE.md              ← Copy for new notes
├── _EMPLOYEE/            ← Copy for new hires
└── _INSTRUCTIONS/        ← This documentation
    ├── MASTER-GUIDE.md   ← You are here
    ├── TASK-SYSTEM.md    ← Complete task instructions
    ├── CHAT-SYSTEM.md    ← Complete chat instructions
    └── NOTE-SYSTEM.md    ← Complete note instructions
```

---

*Documentation System v1.0 — Built for autonomous, high-velocity teams.*
