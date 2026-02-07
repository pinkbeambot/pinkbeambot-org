# 📋 TASK SYSTEM — Complete Instructions

## Overview
Tasks are how work gets tracked and completed.

## ⚠️ RESTRICTED: Task Creation

**Only @FOUNDER can create tasks.**

Employees CANNOT create new tasks. If work is needed:
- Request @FOUNDER to create a task
- Or work within existing tasks assigned to you

---

## Where Tasks Live

**Location:** All tasks live in the shared `Tasks/` directory

```
pinkbeam/
├── Tasks/                       ← All tasks (shared)
│   ├── 🗂️ TASKS.md            ← Index of all tasks
│   ├── TASK-001-stripe-integration.md
│   ├── TASK-002-gateway-fix.md
│   └── ...
└── Org Chart/                   ← Employee directories
    ├── CEO/
    ├── CTO/
    └── ...
```

**Golden Rule:** Tasks are shared. Everyone works from the same task list.

---

## Where Tasks Live

**Location:** All tasks live in the shared `Tasks/` directory

```
pinkbeam/
├── Tasks/                       ← All tasks (shared)
│   ├── 🗂️ TASKS.md            ← Index of all tasks
│   ├── TASK-001-stripe-integration.md
│   ├── TASK-002-gateway-fix.md
│   └── ...
└── Org Chart/                   ← Employee directories
    ├── CEO/
    ├── CTO/
    └── ...
```

**Golden Rule:** Tasks are shared. Everyone works from the same task list.

---

## How to Work on Tasks

### Step 1: Check for Assigned Tasks

Look at `Tasks/🗂️ TASKS.md` for tasks assigned to you:

```markdown
## 📋 Active Tasks

| Task | Status | Priority | Assignee | Due |
|------|--------|----------|----------|-----|
| [[TASK-001-stripe-integration]] | in-progress | critical | @ENG-BE | 2026-02-13 |
```

### Step 2: Open Your Task

Open the task file and read:
- **Task Overview** — What needs to be done
- **Objectives** — Checklist of what to complete
- **Work Log** — Previous progress (append-only)

### Step 3: Update the Task

As you work, update the task file:

```yaml
---
status: in-progress    ← Change from "todo" to "in-progress"
---
```

**Append to Work Log:**
```markdown
### [2026-02-06 14:30] @ENG-BE
**Progress:** Implemented API endpoint
**Completed:**
- [x] Database schema
- [x] Basic endpoint
**Todos:**
- [ ] Input validation
- [ ] Error handling
**Blockers:** None
```
```

---

## Task Assignment Rules

### Only @FOUNDER Can Assign Tasks

**Employees cannot assign tasks to each other.**

If you need a task:
- Request @FOUNDER to create one
- Or work within your existing assigned tasks

### @FOUNDER Assigns Work
- @FOUNDER decides who works on what
- Tasks are created in `Tasks/` with specific assignees
- Employees work on tasks assigned to them
- Account setup (API keys, Stripe, etc.)
- Legal decisions
- Strategic pivots requiring human judgment
- When absolutely stuck and no alternative exists

**Format for FOUNDER tasks:** Be extremely clear about what you need.

---

## How to Update a Task

### Update Frontmatter
- Change `status` as work progresses
- Update `updated` timestamp
- Add/remove `contributors` as needed

### Append to Work Log
**Work Log is append-only. Add new entries at the BOTTOM.**

Format for each log entry:
```markdown
### [YYYY-MM-DD HH:mm] @YourRole
**Progress:** What you did
**Completed:** What got finished (checkboxes)
**Todos:** What's next
**Blockers:** 
- If human requirement → Add task to FOUNDER/Tasks/ and link here
- If technical blocker → Tag relevant person with @mention
**Notes:** Additional context
```

### Use @Mentions in Logs
```markdown
**Blockers:** 
- Need API contract from @ENG-BE
- @CTO decision required on approach
- Spending approval needed — created TASK-XXX in FOUNDER/Tasks/
```

---

## Task Status Values

| Status | Use When | Next Action |
|--------|----------|-------------|
| `todo` | Task created, not started | Assignee reviews and begins |
| `in-progress` | Work has started | Continue execution |
| `blocked` | Cannot proceed | Document blocker, pivot to other work |
| `review` | Work complete, needs review | Request review from creator/contributors |
| `done` | Verified complete | Archive, celebrate |
| `cancelled` | No longer needed | Document why, close out |

---

## Cross-Linking Tasks

Always link related work:

**Link to Chat that created the task:**
```markdown
## 🔗 Related
- Created from: [[2026-02-06-CTO-architecture-discussion]]
```

**Link to related tasks:**
```markdown
## 🔗 Related
- Depends on: [[TASK-001-database-schema]]
- Blocks: [[TASK-003-frontend-integration]]
```

**Link from Chat to Task:**
```markdown
Created [[TASK-014-gateway-fix]] in @ENG-BE/Tasks/
```

---

## Task Hygiene

### Keep Updated
- Update status within 24 hours of progress
- Add log entry for any significant work
- If blocked > 24 hours → escalate or pivot

### Close Completed Tasks
When `status: done`:
1. Final log entry: "Task completed, verified"
2. Update Verification Criteria checkboxes
3. Update Status History table
4. No further edits needed

### Don't Delete Tasks
Even cancelled tasks stay. History matters.

---

## Task Index Tracking — REQUIRED

**Every task MUST be tracked in the shared index file.**

### What is the Index?
The `Tasks/🗂️ TASKS.md` file provides an at-a-glance view of all tasks.

### When Creating a Task — UPDATE THE INDEX

**Step 1:** Create the task file in `Tasks/`
**Step 2:** Immediately update `Tasks/🗂️ TASKS.md`

### Index File Format

```markdown
## 📋 Active Tasks

| Task | Status | Priority | Assignee | Due |
|------|--------|----------|----------|-----|
| [[TASK-001-stripe-integration]] | in-progress | critical | @ENG-BE | 2026-02-13 |
| [[TASK-003-gateway-fix]] | todo | high | @ENG-BE | 2026-02-10 |

## ✅ Recently Completed

| Task | Completed |
|------|-----------|
| [[TASK-000-setup]] | 2026-02-06 |
```

### Index Maintenance Rules

1. **Add immediately** when creating a task
2. **Update status** when task status changes
3. **Move to completed** when task is done
4. **Never delete** — move to completed section

---

## Cross-Linking — MANDATORY

**Every task MUST link to related work.**

### Link to Chat that Created It
```markdown
## 🔗 Related
- Created from: [[2026-02-06-CTO-architecture-discussion]]
```

### Link to Related Tasks
```markdown
## 🔗 Related
- Depends on: [[TASK-001-database-schema]]
- Blocks: [[TASK-003-frontend-integration]]
- Related: [[TASK-005-stripe-webhooks]]
```

### Link from Chat to Task
```markdown
### [2026-02-06 14:00] @CTO → @ENG-BE
Based on this discussion, created [[TASK-014-gateway-fix]] in @ENG-BE/Tasks/
```

### Link from Note to Task
```markdown
See [[TASK-003-gateway-fix]] for implementation status.
```

---

## Quick Reference

| Action | Where | How |
|--------|-------|-----|
| Create task | Assignee's Tasks folder | Copy `_TASK.md`, fill frontmatter |
| Check existing | Assignee's Tasks folder | Look before creating |
| Update task | Same file | Edit frontmatter, append to Work Log |
| Update index | `🗂️ TASK FOLDER.md` | Add to table, update status |
| Assign to FOUNDER | FOUNDER/Tasks/ | Only for spending/human-required |
| Link related work | `## 🔗 Related` section | Use `[[filename]]` wiki links |

---

*Task System v1.0 — Single source of truth for all work.*
