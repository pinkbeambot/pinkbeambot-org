# 🗂️ Tasks — Pink Beam Task System

**The source of truth for all work at Pink Beam.**

Every piece of work is a task. Every task lives here. Everything is documented.

---

## 📋 Task Lifecycle

```
┌─────────┐    ┌─────────────┐    ┌──────────┐    ┌───────────┐    ┌──────────┐
│  todo   │───▶│ in-progress │───▶│  review  │───▶│ completed │───▶│ archived │
└─────────┘    └─────────────┘    └──────────┘    └───────────┘    └──────────┘
      │               │                 │
      │               │                 │
      ▼               ▼                 ▼
  ┌───────┐       ┌───────┐       ┌───────┐
  │blocked│       │blocked│       │blocked│
  └───────┘       └───────┘       └───────┘
```

---

## 🆕 Creating a Task

### Naming Convention

`TASK-{NNN}-{short-description}.md`

Examples:

- `TASK-001-stripe-integration.md`
- `TASK-042-gateway-timeout-fix.md`
- `TASK-156-onboarding-flow-redesign.md`

**Use sequential numbers starting from 001.**

### Task Activation Workflow

```
Creator makes task ──▶ Task in "todo" queue ──▶ CEO activates ──▶ Work begins
     (anyone)              (is_active: false)    (is_active: true)   (single-task mode)
```

**New tasks start with:**

- `status: todo`
- `is_active: false`
- `current_worker: ""`

**The CEO activates tasks by:**

1. Setting `WORK-LOCK.active_task: "[[Tasks/TASK-XXX]]"`
2. Setting `task.is_active: true`
3. Setting `task.status: in-progress`
4. Setting `task.current_worker: "[[Org Chart/ROLE/IDENTITY]]"`
5. Triggering that employee

### Task Template

```markdown
---
id: "TASK-001"
title: "Implement Stripe Checkout"
status: "todo"  # todo | in-progress | blocked | review | completed
priority: "P0"  # P0 = critical, P1 = important, P2 = nice-to-have
created_at: "2026-02-07T00:00:00Z"
created_by: "@FOUNDER"
started_at: ""  # Set when task becomes active
completed_at: ""  # Set when work completes (before CEO verification)
verified_at: ""   # Set when CEO verifies and archives

# Assignment
assigned_to: "[[Org Chart/CTO/IDENTITY]]"  # Primary owner
collaborators:       # Others who need to contribute
  - "[[Org Chart/ENG-BE/IDENTITY]]"
  - "[[Org Chart/ENG-FE/IDENTITY]]"
current_worker: ""   # Who holds the lock right now
next_worker: ""      # Who should work next (safety flag for failed handoffs)

# Tracking
estimated_hours: 8
actual_hours: 0
dependencies:        # Blocked by these tasks
  - "TASK-000-setup-repo"
blocks:              # Blocks these tasks
  - "TASK-002-launch-page"

# Single-Task System
is_active: false     # Set to true when CEO activates this task
verified_by: ""      # CEO who verified completion

# Phase Reviews (for multi-phase tasks with gates)
phase_reviews:       # Gate between each phase
  - phase: "Phase 1: Name"
    worker: "[[Org Chart/ENG-FE/IDENTITY]]"
    reviewer: "[[Org Chart/CMO/IDENTITY]]"
    status: todo     # todo | pending_review | approved | rejected
    submitted_at: ""
    approved_at: ""

# Categorization
tags:
  - "backend"
  - "payments"
  - "revenue-critical"
---

# TASK-001: Implement Stripe Checkout

## 🎯 Objective
One-sentence description of what this task accomplishes.

## 📖 Context
Background information, why this matters, user story, constraints.

---

## ✅ Definition of Done (Checklist)

These items must ALL be checked for the task to be considered complete.

**ID Format:** `[PHASE-NUMBER]` — e.g., `[S1]`, `[BE2]`, `[FE3]`

### Phase 1: Setup ([[Org Chart/FOUNDER/IDENTITY]])
- [ ] `[S1]` Stripe account created
- [ ] `[S2]` API keys stored in environment
- [ ] `[S3]` Webhook endpoint designed

### Phase 2: Backend ([[Org Chart/ENG-BE/IDENTITY]])
- [ ] `[BE1]` Create checkout session endpoint
- [ ] `[BE2]` Webhook handler implemented
- [ ] `[BE3]` Idempotency keys handled
- [ ] `[BE4]` Error cases covered
- [ ] `[BE5]` Tests passing

### Phase 3: Frontend ([[Org Chart/ENG-FE/IDENTITY]])
- [ ] `[FE1]` Checkout button component
- [ ] `[FE2]` Success/cancel pages
- [ ] `[FE3]` Loading states
- [ ] `[FE4]` Error messages

### Phase 4: Integration ([[Org Chart/CTO/IDENTITY]])
- [ ] `[I1]` End-to-end test flow
- [ ] `[I2]` Test payment succeeds
- [ ] `[I3]` Error handling verified

### Phase 5: Deployment ([[Org Chart/CTO/IDENTITY]])
- [ ] `[D1]` Deployed to production
- [ ] Webhooks verified working
- [ ] Monitoring in place

---

## 📝 Work Log

Chronological log of all work performed on this task.

### 2026-02-07 [[Org Chart/CTO/IDENTITY]]
**Started work**
- Acquired lock
- Reviewing Stripe docs
- Initial architecture decisions

### 2026-02-07 [[Org Chart/ENG-BE/IDENTITY]]
**Backend implementation**
- Created `/api/checkout/session` endpoint
- Webhook handler at `/api/webhooks/stripe`
- Checked off: "Create checkout session endpoint"
- Checked off: "Webhook handler implemented"

### 2026-02-08 [[Org Chart/ENG-FE/IDENTITY]]
**Frontend work**
- Built CheckoutButton component
- Created success/cancel pages
- Checked off all frontend items

### 2026-02-08 [[Org Chart/CEO/IDENTITY]]
**Final review and deploy**
- All checklist items complete
- End-to-end tests passing
- Marking as completed

---

## 🚧 Blockers

**Current blockers:**
- None / Waiting for Stripe account approval from FOUNDER

**Previous blockers:**
- 2026-02-07: Blocked on API keys — resolved by FOUNDER

---

## 💬 Decisions

Record key decisions made during this task.

| Date | Decision | Made By | Rationale |
|------|----------|---------|-----------|
| 2026-02-07 | Use Stripe Elements | [[Org Chart/CTO/IDENTITY]] | Better UX, PCI compliance |
| 2026-02-07 | Webhook secret from env | [[Org Chart/ENG-BE/IDENTITY]] | Security best practice |

---

## 🔗 Related

- **Parent:** [[Master Roadmap]] — Q1 Revenue milestone
- **Depends on:** [[TASK-000-setup-repo]]
- **Blocks:** [[TASK-002-launch-page]]
- **Docs:** [[Stripe Integration Guide]]

---

## 🏁 Completion Notes

*Filled when status changes to completed*

**Summary:** Brief description of what was delivered.

**Metrics:**
- Actual hours: 12
- Estimated hours: 8
- Variance: +4 hours (stripe docs took longer)

**Lessons Learned:**
- Webhook testing requires ngrok in dev
- Stripe test cards behave differently than docs suggest

**Follow-up Items:**
- Monitor first 10 real transactions
- Consider Stripe Tax integration
```

---

## 📊 Task Status Definitions

| Status        | Meaning                                 | Can Work?                      | Next Step                       |
| ------------- | --------------------------------------- | ------------------------------ | ------------------------------- |
| `todo`        | Waiting in queue                        | ⛔ No                           | CEO activates it                |
| `in-progress` | Active task being worked                | ⛔ No (current_worker has lock) | Continue work or hand off       |
| `blocked`     | Waiting on dependency                   | ⛔ No                           | Resolve blocker or switch tasks |
| `review`      | Work complete, pending CEO verification | ⚠️ CEO only                    | CEO verifies or rejects         |
| `completed`   | Verified and archived                   | ⛔ No                           | None — task is done             |

### Single-Task Workflow

```
┌────────────────────────────────────────────────────────────────────┐
│                        SINGLE-TASK FLOW                            │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│   CEO picks from queue          Employee works              CEO    │
│   and activates task           on active task           verifies   │
│         │                            │                      │      │
│         ▼                            ▼                      ▼      │
│   ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐   │
│   │   todo   │───▶│ in-prog  │───▶│  review  │───▶│completed │   │
│   │ (queue)  │    │(employee │    │  (CEO    │    │(archived)│   │
│   │          │    │ works)   │    │verifies) │    │          │   │
│   └──────────┘    └──────────┘    └──────────┘    └──────────┘   │
│         ▲              │    │           │                        │
│         │              │    └───────────┘                        │
│         │              │         (if rejected, back to in-prog)  │
│         │              ▼                                         │
│         │         ┌──────────┐                                   │
│         └─────────│ blocked  │                                   │
│                   │ (wait or │                                   │
│                   │  switch) │                                   │
│                   └──────────┘                                   │
│                                                                    │
│   RULES:                                                           │
│   • Only ONE task in-progress at a time (tracked in WORK-LOCK)    │
│   • Work continues until 100% complete                            │
│   • CEO must verify before marking completed                      │
│   • Only then does next task activate                             │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

### Status Transitions

| From | To | Trigger | Who |
|------|-----|---------|-----|
| `todo` | `in-progress` | CEO sets `active_task` and `is_active: true` | CEO |
| `in-progress` | `review` | All checklist items completed | Current worker |
| `review` | `completed` | CEO verifies quality | CEO |
| `review` | `in-progress` | CEO rejects, sends back with feedback | CEO |
| `in-progress` | `blocked` | External dependency blocking work | Current worker |
| `blocked` | `in-progress` | Blocker resolved | Current worker or CEO |
| `completed` | (archive) | 30 days after completion | CEO |

---

## 🎯 How to Work on the Active Task

### Understanding the Single-Task System

**Only ONE task is active at a time across the entire company.**

This task is tracked in `WORK-LOCK.active_task`. When you acquire the lock:

1. **Check `WORK-LOCK.active_task`**
   - If empty → No active task (CEO needs to activate one)
   - If set → That is the ONLY task you should work on

2. **Read the active task file** completely

3. **Verify you are the `current_worker`**
   - If `"[[Org Chart/YOUR-ROLE/IDENTITY]]"` → Proceed with work
   - If another role → Wait or escalate to CEO
   - If empty → You may claim this task (set `current_worker: "[[Org Chart/YOUR-ROLE/IDENTITY]]"`)

### While Working on Active Task

1. **Update the Work Log** regularly:

   ```markdown
   ## Work Log
   
   ### 2026-02-07 [[Org Chart/YOUR-ROLE/IDENTITY]]
   **Completed:**
   - [x] Item you finished
   
   **Progress:**
   - [ ] Item in progress (70% complete)
   
   **Notes:** Context for next worker
   ```

2. **Check off completed items** in the Definition of Done checklist

3. **Update `actual_hours`** as you work

4. **If you encounter a blocker:**
   - Document in Work Log
   - If resolvable quickly: Resolve and continue
   - If requires FOUNDER: Create `FOUNDER/Todos/` item
   - If blocks entire task: Change `status: blocked`, hand off to CEO

### When Handing Off (Task NOT Complete)

1. **Update Work Log** with handoff notes:
   - What was done
   - What's next
   - Any blockers

2. **Determine next worker** from task phases/collaborators

3. **Update `task.current_worker: "[[Org Chart/NEXT-ROLE/IDENTITY]]"`**

4. **Trigger next employee:** `cron run pbb-{NEXT-ROLE}-shift`

5. **Release lock** (DO NOT clear `active_task`)

### When Task is 100% Complete

**IMPORTANT: Do NOT mark as `completed`. Mark as `review`.**

1. **Verify ALL checklist items are checked**

2. **Fill out Completion Notes section** with:
   - Summary of what was delivered
   - Actual hours vs estimated
   - Lessons learned
   - Follow-up items

3. **Update task fields:**

   ```yaml
   status: review
   completed_at: "2026-02-07T12:00:00Z"
   current_worker: @CEO
   ```

4. **Trigger CEO:** `cron run pbb-ceo-shift`

5. **Release lock** (CEO will clear `active_task` after verification)

---

## ✅ CEO Verification Protocol

**Only CEO performs these steps.**

### When Task Status is `review`

The CEO must verify before the task is truly done:

1. **Acquire lock** (via AGENTS.md)

2. **Review the completed task:**
   - Read entire task file
   - Verify ALL checklist items are checked
   - Review Completion Notes
   - Test/validate deliverables if needed

3. **Make decision:**

   **Option A: Approve and Archive**

   ```yaml
   status: completed
   verified_at: "2026-02-07T14:00:00Z"
   verified_by: "CEO"
   is_active: false
   ```

   - **KILL ALL CRON JOBS AND SUB-AGENTS** — Prevent zombie processes
   - Add CEO sign-off to Completion Notes
   - Update `TASKS.md` index — move to Completed section
   - Clear `WORK-LOCK.active_task: ""` (ready for next task)
   - Archive task file if >30 days old
   - Activate next task from queue
   - Trigger appropriate employee
   - Release lock

   **Option B: Reject and Return**

   ```yaml
   status: in-progress
   current_worker: "[[Org Chart/ROLE/IDENTITY]]"  # assign back with feedback
   ```

   - Document specific issues in Work Log
   - Trigger assigned employee
   - Release lock

### Clearing the Active Task

**Only the CEO clears `active_task`:**

```yaml
# WORK-LOCK/WORK-LOCK.md
---
status: unlocked
employee: ""
active_task: ""  # CLEARED — ready for next task
started_at: ""
---
```

After clearing, the CEO can immediately activate the next task:

```yaml
# WORK-LOCK/WORK-LOCK.md
---
status: unlocked
employee: ""
active_task: "[[Tasks/TASK-002-next-task]]"
started_at: ""
---
```

Then trigger the first worker on that task.

---

## 🧹 Process Cleanup (CRITICAL)

### When Task Completes — Kill All Background Processes

**Before marking a task `completed`, the CEO MUST clean up:**

#### 1. Kill All Cron Jobs

```bash
# List all cron jobs for this task
cron list | grep pbb-

# Remove all Pink Beam cron jobs
cron remove pbb-ceo-shift
cron remove pbb-cto-shift
cron remove pbb-cmo-shift
cron remove pbb-eng-fe-shift
cron remove pbb-eng-be-shift
```

#### 2. Kill All Sub-Agents / Sessions

```bash
# List active sessions
sessions_list

# Kill any stuck agent sessions
sessions_send <sessionKey> "STOP — Task complete, session ending"

# Or use process management if applicable
process list
process kill <sessionId>
```

#### 3. Verify Cleanup

- [ ] No active cron jobs for completed task
- [ ] No hanging sub-agent sessions
- [ ] Work lock is released
- [ ] Only then: mark task `completed`

**Why this matters:**

- Prevents zombie processes consuming resources
- Avoids race conditions on next task activation
- Ensures clean slate for next work cycle
- Prevents duplicate/conflicting work

**If you don't clean up:**

- Multiple agents may try to work simultaneously
- Cron jobs trigger on old task context
- Resource leaks and system instability
- Confusing logs and state

---

## ✅ Checklist Best Practices

### Checklist Item Format

```markdown
- [ ] [ID] Clear, verifiable action (OWNER)
```

**ID Format:** Use short prefix + number

- `[S1]`, `[S2]` — Setup phase
- `[BE1]`, `[BE2]` — Backend phase  
- `[FE1]`, `[FE2]` — Frontend phase
- `[I1]`, `[I2]` — Integration phase
- `[D1]`, `[D2]` — Deployment phase

**Why IDs matter:**

- Reference specific items in Work Log ("Completed [BE3]")
- Track which items are done across shifts
- Easier to verify completion

**Good:**

- [ ] `[BE1]` Create checkout session endpoint
- [ ] `[BE2]` API returns 200 with session ID
- [ ] `[BE3]` Error case: invalid price ID returns 400

**Bad:**

- [ ] Do Stripe stuff
- [ ] Make it work
- [ ] Code

### Phasing Checklists

Break large tasks into phases. Each phase can have a primary owner.

```markdown
### Phase 1: Design ([[Org Chart/CTO/IDENTITY]])
- [ ] API contract defined
- [ ] Database schema designed
- [ ] Security review completed

### Phase 2: Backend ([[Org Chart/ENG-BE/IDENTITY]])
- [ ] Database migrations created
- [ ] API endpoints implemented
- [ ] Tests passing

### Phase 3: Frontend ([[Org Chart/ENG-FE/IDENTITY]])
- [ ] Components built
- [ ] Integration tests passing
```

---

## 🔄 Task Index Maintenance

The `TASKS.md` file serves as the master index. Keep it updated.

### Single-Task Index Format

## 🔴 ACTIVE TASK (Current Focus)

**Only ONE task can be active at a time.**

| ID | Title | Status | Worker | Started |
|:---|:---|:---|:---|:---|
| TASK-001 | Implement Pricing & Marketing Strategy Updates | in-progress | ENG-FE | 2026-02-07 |

---

## 📋 QUEUE (Waiting for Activation)

Tasks ready to become active when current task completes.

| ID | Title | Priority | Owner | Est Hours |
|:---|:---|:---|:---|---:|
| — | *No tasks in queue* | — | — | — |

---

## 🚧 BLOCKED (On Hold)

| ID | Title | Blocked By | Since |
|:---|:---|:---|:---|
| — | *No blocked tasks* | — | — |

---

## ✅ COMPLETED (Last 30 Days)

| ID | Title | Completed | Verified By |
|:---|:---|:---|:---|
| — | *No completed tasks* | — | — |

---

## ❌ CANCELLED (Reference Only)

Cancelled tasks stay here for reference - not deleted.

| ID | Title | Cancelled | Reason |
|:---|:---|:---|:---|
| — | *No cancelled tasks* | — | — |

---

### Index Update Rules

**When CEO activates a task:**
1. Move from QUEUE to ACTIVE TASK
2. Set `is_active: true`
3. Update `started_at` timestamp

**When work hands off:**
1. Update ACTIVE TASK table with new `current_worker`
2. Update `last_updated` in task file

**When task enters review:**
1. Keep in ACTIVE TASK section
2. Change status to `review`
3. Update `current_worker: @CEO`

**When CEO verifies and completes:**
1. Move from ACTIVE TASK to COMPLETED section
2. Set `is_active: false`
3. Set `verified_by: CEO`
4. Update `verified_at` timestamp
5. **Clear ACTIVE TASK section** (until next activation)

**When task is archived (>30 days):**
1. Move task file to `Tasks/archive/`
2. Remove from COMPLETED section in index

---

## 🚨 Priority Levels

| Level | Criteria | Response Time |
|-------|----------|---------------|
| **P0** | Revenue-critical, blocking launch, security incident | Immediate |
| **P1** | Important feature, user-facing bug | Within 24h |
| **P2** | Nice-to-have, refactoring, docs | Within 1 week |

---

## 🔐 Assignment & Activation Rules

### Who Can Create Tasks
- **FOUNDER** — Any task
- **CEO** — Any task
- **Any employee** — Suggest tasks (create with `status: todo`, notify CEO)

**Created tasks start in QUEUE:**
- `status: todo`
- `is_active: false`
- `current_worker: ""`

### Who Can Activate Tasks
**Only CEO can activate tasks.**

The CEO:
1. Reviews QUEUE for highest priority task
2. Sets `WORK-LOCK.active_task: "[[Tasks/TASK-XXX]]"`
3. Updates task:
   - `is_active: true`
   - `status: in-progress`
   - `started_at: timestamp`
   - `current_worker: "[[Org Chart/ROLE/IDENTITY]]"` (first worker)
4. Triggers first worker: `cron run pbb-{ROLE}-shift`

### Who Can Modify Tasks

| Role | Can Modify |
|------|------------|
| **Creator** | Anything (before activation) |
| **Current Worker** | Work Log, checklists, actual_hours, blockers |
| **CEO** | Anything including status, activation, verification |
| **FOUNDER** | Anything |

### Status Change Permissions

| Status Change | Who Can Do It |
|---------------|---------------|
| `todo` → `in-progress` | CEO only (activation) |
| `in-progress` → `review` | Current worker (when 100% done) |
| `review` → `completed` | CEO only (verification) |
| `review` → `in-progress` | CEO only (rejection) |
| `in-progress` → `blocked` | Current worker |
| `blocked` → `in-progress` | Current worker or CEO |
| Any → `todo` | CEO only (reset)

---

## 📝 Work Log Format

Every work session adds an entry:

```markdown
### {YYYY-MM-DD} [[Org Chart/{ROLE}/IDENTITY]]

**Focus:** What you worked on this session

**Completed:**
- [x] Item you finished
- [x] Another item

**Progress:**
- [ ] Item in progress (60% complete)

**Blockers:**
- None / Specific blocker with context

**Decisions:**
- Decision made and why

**Next Steps:**
- What should happen next
- Who should do it


---

## ♻️ Archiving Completed Tasks

Completed tasks older than 30 days should be archived.

1. **Create archive folder** if needed: `Tasks/archive/`
2. **Move task file:** `mv Tasks/TASK-XXX.md Tasks/archive/`
3. **Update index** — move to "Archived Tasks" section
4. **Keep completed index** for 90 days, then remove

---

## 🎯 Task Hygiene Checklist

When creating a task:

- [ ] Clear, specific title
- [ ] Detailed objective and context
- [ ] Checklist items are verifiable
- [ ] Dependencies identified
- [ ] Estimated hours provided
- [ ] Tags appropriate
- [ ] Set `status: todo`, `is_active: false`
- [ ] Added to QUEUE section in index
- [ ] CEO notified of new task

When CEO activates a task:

- [ ] Task moved from QUEUE to ACTIVE TASK in index
- [ ] `WORK-LOCK.active_task` set to task link
- [ ] Task `is_active: true`, `status: in-progress`
- [ ] `started_at` timestamp set
- [ ] `current_worker` assigned to first role
- [ ] First employee triggered

When working a task:

- [ ] Work Log updated every session
- [ ] Checklist items checked when done
- [ ] Hours tracked in `actual_hours`
- [ ] Blockers documented with context
- [ ] Decisions recorded in Decisions section
- [ ] Next worker identified for handoff

When completing a task (100% done):

- [ ] All checklist items checked
- [ ] Completion Notes filled with summary, metrics, lessons
- [ ] `status: review` (NOT completed)
- [ ] `completed_at` timestamp set
- [ ] `current_worker: "[[Org Chart/CEO/IDENTITY]]"` for verification
- [ ] CEO triggered for verification
- [ ] Index updated (status to review)

When CEO verifies a task:

- [ ] All checklist items reviewed
- [ ] Deliverables validated
- [ ] Completion Notes reviewed
- [ ] Decision: approve or reject
- [ ] **If approved: KILL ALL CRON JOBS and SUB-AGENTS**
- [ ] If approved: `status: completed`, `verified_by: CEO`, `verified_at` set
- [ ] If rejected: specific feedback in Work Log, returned to `in-progress`
- [ ] Index updated (move to COMPLETED or back to ACTIVE)
- [ ] `WORK-LOCK.active_task` cleared (if approved)
- [ ] Next task activated from QUEUE (if approved)

---

## 🔗 Quick Reference

| Action            | How To                                                                          |
| ----------------- | ------------------------------------------------------------------------------- |
| **Create task**   | Copy template, save as `TASK-{NNN}-{name}.md`, set `status: todo`, add to QUEUE |
| **Activate task** | CEO only: Set `WORK-LOCK.active_task`, `is_active: true`, trigger worker        |
| **Find work**     | Read `WORK-LOCK.active_task` — that's the ONE task to work on                   |
| **Start work**    | Follow AGENTS.md: acquire lock, verify you're `current_worker`, execute         |
| **Handoff**       | Update Work Log, set `current_worker` to next role, trigger them, release lock  |
| **Complete work** | Check all items, fill Completion Notes, set `status: review`, hand to CEO       |
| **Verify task**   | CEO only: Review, approve/reject, archive if approved, clear `active_task`      |
| **Activate next** | CEO only: Pick from QUEUE, set new `active_task`, trigger first worker          |

### Emergency Contacts

- **Task blocked on FOUNDER:** Create `FOUNDER/Todos/` item
- **Need to override current worker:** Escalate to CEO
- **Task stuck >24h:** CEO can reassign or activate different task
- **System issues:** Document in `Notes/system-issues-YYYY-MM-DD.md`

---

*Task System v2.0 — Single focus, verified completion, relentless progress.*
