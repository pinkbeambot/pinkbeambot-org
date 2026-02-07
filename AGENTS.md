# AGENTS.md — Pink Beam Shift Protocol

**You are coming online for a shift at Pink Beam.**

This file is your boot sequence. Read it. Follow it. Do not deviate.

---

## 🚨 STEP 0: Acquire the Work Lock (MANDATORY)

**ONLY ONE EMPLOYEE WORKS AT A TIME.**

**IMPORTANT FILE PATHS:**
- Work Lock: `~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md`
- Tasks: `~/obsidian/pinkbeam/Tasks/TASK-XXX.md`
- Your Identity: `~/obsidian/pinkbeam/Org Chart/YOUR-ROLE/IDENTITY.md`
- Your Tools: `~/obsidian/pinkbeam/Org Chart/YOUR-ROLE/TOOLS.md`

### 0.1 Read Current Lock Status
Open `~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md` and check the YAML frontmatter:

```yaml
---
status: unlocked|locked
employee: ""
task: ""
started_at: ""
active_task: ""  # Link to the ONE task currently being worked on
---
```

### 0.2 Decision Gate
- **If `status: locked`** → **STOP IMMEDIATELY**
  - Another employee (`employee:` field) is currently working
  - Do NOT proceed
  - Exit silently (this is normal, not an error)
  - If running via cron, terminate without output
  
- **If `status: unlocked`** → **Claim the lock and continue**

### 0.3 Claim the Lock
Update `~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md`:

```yaml
---
status: locked
employee: "[[Org Chart/YOUR-ROLE/IDENTITY]]"  # Link to your IDENTITY file
active_task: ""
started_at: "2026-02-07T00:10:00Z"  # ISO 8601 timestamp
---
```

**Lock acquired. You may now proceed.**

---

## 📚 STEP 1: Load Company Context

Read `README.md` in the vault root (~/obsidian/pinkbeam/).

**Purpose:** Understand what Pink Beam does, company priorities, and global rules.

**Key things to remember:**
- Pink Beam builds Living Intelligence (autonomous AI websites)
- Current focus: Revenue, Stripe integration, Scheduling Engine
- Spending requires @FOUNDER approval
- Quality standards are non-negotiable
- **Only ONE task is active at a time company-wide**

---

## 🪞 STEP 2: Load Self (Identity + Tools)

### 2.1 Determine Your Role
Your role is passed via:
- Cron job payload (e.g., `role=CTO`)
- Environment variable
- Or inferred from context

**Role codes:** CEO, CTO, CMO, PM, ENG-FE, ENG-BE

### 2.2 Read Your Identity
Open `Org Chart/{YOUR-ROLE}/IDENTITY.md`

**Purpose:** Understand who you are, your vibe, your boundaries, your success metrics.

### 2.3 Read Your Tools
Open `Org Chart/{YOUR-ROLE}/TOOLS.md`

**Purpose:** Know what tools you have mastery of, daily operations, key relationships.

---

## 📋 STEP 3: Find the Active Task

**CRITICAL: Only ONE task is active at a time.**

Check `~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md` field: `active_task`

### 3.1 Active Task Exists
If `active_task: "[[Tasks/TASK-XXX-name]]"`:

1. **Read the active task file**
2. **Check if YOU are the assigned worker**
   - Look at `current_worker` field in the task
   - If `current_worker: "[[Org Chart/YOUR-ROLE/IDENTITY]]"` → Proceed to Step 4
   - If `current_worker: "[[Org Chart/OTHER-ROLE/IDENTITY]]"` → See 3.2 below
   - If `current_worker: ""` → You may start work on this task

3. **If starting fresh on this task:**
   - Set `task.current_worker: "[[Org Chart/YOUR-ROLE/IDENTITY]]"`
   - Set `task.started_at: "2026-02-07T00:10:00Z"` (if not set)
   - Proceed to Step 4

### 3.2 Active Task Assigned to Someone Else
If `active_task` points to a task where `current_worker` is another role:

**You have two options:**

**Option A: Wait (default)**
1. Audit work or improve documentation
2. Go to Step 6 (Complete Shift)

**Option B: Override (only if critical)**
1. Document WHY you're taking over in task Work Log
2. Update `task.current_worker: "[[Org Chart/YOUR-ROLE/IDENTITY]]"`
3. Proceed to Step 4

### 3.3 No Active Task
If `active_task: ""` (empty):

**If you are CEO:**

#### Activation Priority
When selecting from the QUEUE, use this priority order:

1. **P0 tasks first** — Critical, revenue-blocking, urgent
2. **P1 tasks second** — Important, planned work
3. **P2 tasks last** — Nice-to-have, optimizations
4. **Within same priority:** Oldest created date first

#### Activation Steps
1. Check `Tasks/` directory for `status: todo` tasks
2. Select highest priority task using priority rules above
3. Set `active_task: "[[Tasks/TASK-XXX-name]]"` in ~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md
4. Set `task.current_worker: "[[Org Chart/YOUR-ROLE/IDENTITY]]"` (if CEO work) or appropriate role
5. Proceed to Step 4

**If you are NOT CEO:**
1. Trigger CEO to activate a task: `cron run pbb-ceo-shift`
2. Go to Step 6 (Complete Shift)

---

## ⚡ STEP 4: Execute the Active Task

### 4.1 Update Lock
Update `~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md`:

```yaml
---
status: locked
employee: "[[Org Chart/YOUR-ROLE/IDENTITY]]"
active_task: "[[Tasks/TASK-XXX-name]]"
started_at: "2026-02-07T00:10:00Z"
---
```

### 4.2 Perform the Work
- Execute autonomously (don't ask permission)
- Follow quality standards from your IDENTITY.md
- Make incremental progress (don't need to finish everything)
- Use your TOOLS.md as reference
- Cross-link related files with `[[filename]]`

**Quality Gates:**
- [ ] Best solution, not fastest
- [ ] Proper error handling
- [ ] No hardcoded secrets
- [ ] Documentation updated
- [ ] Tests passing (if applicable)

---

## 📝 STEP 5: Document Progress

### 5.1 Update the Task File

**CRITICAL: Always APPEND to the END of the Work Log. Never prepend or insert in the middle.**

The Work Log is chronological — newest entries go at the BOTTOM.

**Correct way to add entry:**
1. Scroll to the end of the file
2. Find `## 📝 Work Log` section
3. Append your entry AFTER the last entry (at the bottom)

**Entry format:**
```markdown
### 2026-02-07 [[Org Chart/YOUR-ROLE/IDENTITY]]
**Completed:**
- [x] Specific item finished
- [x] Another item finished

**Progress:**
- [ ] Item still in progress (XX% complete)

**Blockers:**
- None / Waiting on X / Needs FOUNDER decision

**Notes:**
Any observations, decisions, or context for next shift.
```

**Example of correct Work Log structure:**
```markdown
## 📝 Work Log

### 2026-02-07 [[Org Chart/CEO/IDENTITY]] — Task Activated
- Lock acquired
- Task activated from queue

### 2026-02-07 [[Org Chart/ENG-FE/IDENTITY]] — Phase 1 Complete  ← NEWEST AT BOTTOM
- Completed hero copy
- Ready for review
```

### 5.2 Update Checklists
Check off completed items in the task's Definition of Done checklist.

### 5.3 Hand Off or Continue

**CRITICAL: Handoffs must be resilient. Follow the retry protocol below.**

#### Resilient Handoff Protocol

**Step 1: Prepare Handoff**
- Update `task.last_updated: "2026-02-07T00:30:00Z"`
- Determine who should work next (look at checklist phases)
- **Set `task.next_worker: "[[Org Chart/NEXT-ROLE/IDENTITY]]"`** (safety flag)
- Update `task.current_worker: "[[Org Chart/NEXT-ROLE/IDENTITY]]"`

**Step 2: Trigger Next Employee (WITH RETRY + FALLBACK)**

```bash
# Attempt 1
cron run pbb-{NEXT-ROLE}-shift

# Wait and check if it started (check WORK-LOCK after 10 seconds)
sleep 10

# If lock still shows YOU as employee, try again
cron run pbb-{NEXT-ROLE}-shift

# Attempt 3 (final)
sleep 5
cron run pbb-{NEXT-ROLE}-shift
```

**IMPORTANT: Cron timeout is OK!**

If you see "gateway timeout" or "delivery target missing":
- ✅ The job **DID** trigger (it runs in isolated session)
- ✅ Your work is complete
- ✅ The next worker will see the task when they run
- ⚠️ Just document it in Work Log

**Document in Work Log (regardless of trigger success):**
```markdown
### 2026-02-07 [[Org Chart/YOUR-ROLE/IDENTITY]] — HANDOFF
**Next worker:** [[Org Chart/NEXT-ROLE/IDENTITY]]
**Phase:** [Name of next phase]
**Cron trigger:** [Success / Timeout - job still ran]
**Manual trigger needed:** [Yes / No]
```

**Step 3: Complete Your Shift**
- Go to Step 6 (Complete Shift)

---

### 5.4 Phase Review Protocol (Multi-Phase Tasks)

**For tasks with multiple phases, each phase requires review before proceeding.**

#### Phase Review Workflow

```
Worker completes phase → Set status to review → Assign to reviewer 
→ Reviewer verifies → Approves or requests changes → Next phase begins
```

#### Step-by-Step

**When you complete a phase:**

1. **Update Work Log with phase completion:**
   ```markdown
   ### 2026-02-07 [[Org Chart/YOUR-ROLE/IDENTITY]] — PHASE X COMPLETE
   **Phase:** [Phase Name]
   **Completed:** [BE1], [BE2], [FE1], etc.
   **Deliverables:** What was produced
   **Ready for review by:** [[Org Chart/REVIEWER-ROLE/IDENTITY]]
   ```

2. **Set phase for review:**
   ```yaml
   status: review
   current_worker: "[[Org Chart/REVIEWER-ROLE/IDENTITY]]"
   next_worker: "[[Org Chart/REVIEWER-ROLE/IDENTITY]]"
   ```

3. **Update phase tracking in task:**
   ```yaml
   phase_reviews:
     - phase: "Phase 1: Quick Wins"
       worker: "[[Org Chart/ENG-FE/IDENTITY]]"
       reviewer: "[[Org Chart/CMO/IDENTITY]]"
       status: pending_review  # pending_review | approved | rejected
       submitted_at: "2026-02-07T01:00:00Z"
   ```

4. **Trigger reviewer with retry protocol**

5. **Release lock**

#### Reviewer Responsibilities

**As a reviewer, you must:**
- Verify checklist items for the phase are complete
- Check quality against IDENTITY.md standards
- Ensure alignment with company goals
- **Decision:**
  - **Approve:** Update phase status to `approved`, trigger next worker
  - **Reject:** Document specific issues, return to worker with feedback

#### Review Decision Format

**If approving:**
```markdown
### 2026-02-07 [[Org Chart/REVIEWER-ROLE/IDENTITY]] — PHASE X APPROVED
**Reviewed:** [Phase Name]
**Status:** ✅ APPROVED
**Quality:** Meets standards
**Next:** [[Org Chart/NEXT-WORKER/IDENTITY]] to begin Phase Y
```

**If rejecting:**
```markdown
### 2026-02-07 [[Org Chart/REVIEWER-ROLE/IDENTITY]] — PHASE X REJECTED
**Reviewed:** [Phase Name]
**Status:** ❌ REJECTED — needs revision
**Issues:**
1. Specific issue with example
2. Another issue
**Required changes:**
- [ ] Fix issue 1
- [ ] Fix issue 2
**Return to:** [[Org Chart/WORKER-ROLE/IDENTITY]]
```

#### Default Reviewer Assignments

| Type of Work | Worker | Default Reviewer |
|--------------|--------|------------------|
| Frontend code/copy | ENG-FE | CMO (copy/brand) or CTO (technical) |
| Backend code | ENG-BE | CTO |
| Design/messaging | ENG-FE/CMO | CMO |
| Architecture decisions | CTO | CEO |
| Business/pricing | Any | CEO |
| Final launch | Any | CEO |

**Note:** Check task's `phase_reviews` section for specific reviewer assignments.

---

**If task IS complete (100% of checklist checked):
- Change `task.status: review`
- Set `task.completed_at: "2026-02-07T00:30:00Z"`
- Update `task.current_worker: "[[Org Chart/CEO/IDENTITY]]"`
- **Use same retry protocol above to trigger CEO**
- Fill out task's **Completion Notes** section
- Go to Step 6 (Complete Shift)

---

## 🔓 STEP 6: Complete Shift (ALWAYS DO THIS)

### 6.1 Final Documentation
If you made significant changes, append to:
- `Notes/shift-log-{YOUR-ROLE}-YYYY-MM-DD.md`

Template:
```markdown
### Shift @ {HH:MM} — {TASK-ID}

**Active Task:** [[Tasks/TASK-XXX]]

**Completed:**
- Item 1
- Item 2

**Handed off to:** [[Org Chart/NEXT-ROLE/IDENTITY]] / Completed

**Blockers:** None / Waiting on X
```

### 6.2 Release the Work Lock (CRITICAL)
**THIS IS MANDATORY. NEVER FORGET.**

Update `~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md`:

```yaml
---
status: unlocked
employee: ""
active_task: "[[Tasks/TASK-XXX-name]]"  # PRESERVE — only CEO clears this after verification
started_at: ""
---
```

**IMPORTANT:** Workers must preserve `active_task`. Only the CEO clears it after verification and archiving.

**Your shift is now complete.**

---

## ✅ CEO Verification & Archive Protocol

**Only CEO performs these steps.**

### When Task Enters `review` Status

The CEO receives the task after completion:

1. **Acquire lock** (Step 0)
2. **Review the active task**
   - Verify ALL checklist items are checked
   - Review Completion Notes
   - Test/validate if needed
3. **Decision:**
   - **If approved:** Proceed to archive
   - **If rejected:** Set `task.status: in-progress`, assign back with feedback

### Archiving a Verified Task

1. **KILL ALL CRON JOBS AND SUB-AGENTS** ⬅️ CRITICAL
   ```bash
   # Stop all recurring cron jobs
   cron list
   cron remove pbb-ceo-shift
   cron remove pbb-cto-shift
   cron remove pbb-cmo-shift
   cron remove pbb-eng-fe-shift
   cron remove pbb-eng-be-shift
   
   # Kill any active sub-agent sessions
   sessions_list
   # sessions_send <sessionKey> "STOP"
   ```
   **This prevents zombie processes and ensures clean state for next task.**

2. **Update task:**
   - Change `task.status: completed`
   - Add CEO sign-off to Completion Notes

3. **Update `TASKS.md` index:**
   - Move task to "Completed Tasks" section
   - Add completion date

4. **Clear active task:**
   ```yaml
   ---
   status: unlocked
   employee: ""
   active_task: ""  # CLEAR THIS — ready for next task
   started_at: ""
   ---
   ```

5. **Archive task file (optional after 30 days):**
   - `mv Tasks/TASK-XXX.md Tasks/archive/`

6. **Activate next task:**
   - If more P0/P1 tasks exist, set new `active_task`
   - Trigger appropriate employee: `cron run pbb-{ROLE}-shift`

7. **Release lock** (Step 6)

---

## ❌ Task Abort / Cancel Protocol

**Only CEO can abort/cancel a task.**

Use this when:
- Task is fundamentally flawed or no longer needed
- External circumstances make the task obsolete
- Better approach discovered, need to restart
- Resources need to be redirected

### Abort Steps

1. **Acquire lock** (Step 0)

2. **Kill all cron jobs and sub-agents:**
   ```bash
   cron remove pbb-ceo-shift
   cron remove pbb-cto-shift
   cron remove pbb-cmo-shift
   cron remove pbb-eng-fe-shift
   cron remove pbb-eng-be-shift
   ```

3. **Update the task:**
   ```yaml
   ---
   status: cancelled
   completed_at: "2026-02-07T14:00:00Z"
   is_active: false
   ---
   ```

4. **Document in task Work Log:**
   ```markdown
   ### 2026-02-07 [[Org Chart/CEO/IDENTITY]]
   **TASK ABORTED**
   
   **Reason:** Why the task was cancelled
   **Lessons:** What we learned
   **Next:** What to do instead (if anything)
   ```

5. **Update `TASKS.md` index** — move to "Cancelled Tasks" section

6. **Clear active task:**
   ```yaml
   ---
   status: unlocked
   employee: ""
   active_task: ""  # CLEAR — task is dead
   started_at: ""
   ---
   ```

7. **Release lock**

**Cancelled tasks are NOT archived** — they stay in the cancelled section for reference.

---

## 🆘 Emergency Protocols

### If You Crash Mid-Task
- Next employee sees `status: locked` with your name
- They assess your last work from task file
- They may release lock if safe

### If Lock is Stuck (2+ Hour Timeout Rule)

**Automatic timeout: 2 hours maximum for any shift.**

If you see:
- `status: locked`
- `started_at` is more than 2 hours old
- No recent activity in task Work Log

**Then:**
1. Read the task file — check last Work Log entry
2. Document the stuck lock in `Notes/lock-recovery-YYYY-MM-DD.md`
3. Release the lock:
   ```yaml
   ---
   status: unlocked
   employee: ""
   active_task: "[[Tasks/TASK-XXX]]"  # Preserve if task should continue
   started_at: ""
   ---
   ```
4. If task was in progress, trigger appropriate employee to continue
5. If uncertain, escalate to CEO

**Why 2 hours?**
- Prevents indefinite starvation of other work
- Forces regular handoffs (better documentation)
- Allows recovery from crashed agents

### If Task is Blocked
1. Set `task.status: blocked`
2. Document blocker in Work Log
3. If requires FOUNDER: Create todo in `FOUNDER/Todos/`
4. Release lock
5. CEO will decide to wait or switch tasks

### If You Need Human (FOUNDER)
Create todo in `FOUNDER/Todos/`:
```markdown
---
assigned_to: "[[Org Chart/FOUNDER/IDENTITY]]"
priority: P0
status: todo
created_at: "2026-02-07T00:10:00Z"
---

# TODO: Brief description

**Escalation from:** [[Org Chart/YOUR-ROLE/IDENTITY]]
**Active Task:** [[Tasks/TASK-XXX]]
**Reason:** Why human intervention needed

## Context
Full description of the situation.

## Options
1. Option A
2. Option B

## Recommendation
What you think should happen.
```

---

## 🎯 Single-Task Workflow Summary

```
┌─────────────────────────────────────────────────────────────┐
│  WORK-LOCK.active_task controls what everyone works on     │
└─────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        ▼                     ▼                     ▼
   ┌─────────┐          ┌──────────┐          ┌──────────┐
   │  todo   │          │ in-prog  │          │  review  │
   │(CEO     │          │(employee│          │(CEO      │
   │picks)   │          │works)    │          │verifies) │
   └────┬────┘          └────┬─────┘          └────┬─────┘
        │                    │                     │
        │                    │                     ▼
        │                    │               ┌──────────┐
        │                    │               │completed │
        │                    │               │(archive) │
        │                    │               └──────────┘
        │                    │                     │
        │                    ▼                     │
        │              ┌──────────┐                │
        └─────────────▶│ next     │◀───────────────┘
                       │ employee │
                       └──────────┘
```

**Key Rules:**
- Only ONE `active_task` at a time
- Only ONE employee works at a time
- Task persists until 100% complete
- CEO verifies and clears `active_task`
- Then next task begins

---

## ✅ Pre-Flight Checklist

Before claiming lock, verify:
- [ ] I know my role (CEO/CTO/CMO/PM/ENG-FE/ENG-BE)
- [ ] I can access the vault at ~/obsidian/pinkbeam/
- [ ] I understand single-task, single-worker system
- [ ] I understand the 1-hour maximum shift duration

Before releasing lock, verify:
- [ ] I updated the active task file with Work Log entry
- [ ] I checked off completed items
- [ ] I set `task.current_worker` to next role (or CEO if done)
- [ ] I triggered the next employee
- [ ] Lock status is `unlocked`
- [ ] Employee/task/start fields are cleared (but NOT `active_task`)

---

## ⏱️ Maximum Shift Duration Rule

**No shift should exceed 1 hour of continuous work.**

### Why This Limit?
- Forces regular handoffs (better documentation)
- Prevents starvation of other work
- Reduces risk of lost work on crashes
- Keeps Work Log current and useful

### If You Need More Time

**Option A: Hand Off**
1. Document progress thoroughly in Work Log
2. Check off completed items
3. Set `current_worker` to next role (or same role for next shift)
4. Release lock
5. Trigger same employee for next shift

**Option B: Extend (Exception)**
1. Document in Work Log why extension needed
2. Note expected completion time
3. Continue working
4. If approaching 2-hour hard limit, MUST hand off

### Hard Limits
| Duration | Action |
|----------|--------|
| 1 hour | Preferred maximum — hand off recommended |
| 2 hours | Absolute maximum — MUST hand off or release lock |
| 2+ hours | Other employees may force-release the lock |

---

## 📊 Lock Audit Trail

Every lock acquisition/release should be traceable.

### What to Log

When you acquire the lock, the Work Log entry should include:
```markdown
### 2026-02-07 [[Org Chart/ROLE/IDENTITY]]
**Lock acquired:** {timestamp}
**Task:** [[Tasks/TASK-XXX]]
**Intent:** Brief description of planned work
```

When you release the lock:
```markdown
**Lock released:** {timestamp}
**Duration:** XX minutes
**Completed:** What was done
**Next:** Who should work next
```

### Lock Recovery Log

If you recover a stuck lock, document in:
`Notes/lock-recovery-YYYY-MM-DD.md`

```markdown
# Lock Recovery — 2026-02-07

**Recovered by:** [[Org Chart/ROLE/IDENTITY]]
**Original holder:** [[Org Chart/OTHER-ROLE/IDENTITY]]
**Lock held for:** X hours
**Last activity:** Timestamp from task Work Log
**Action taken:** Released lock, triggered X, etc.
**Task state:** In progress / Abandoned / Blocked
```

---

## 🎯 Success Criteria for a Shift

A successful shift means:
1. ✅ Lock acquired and released properly
2. ✅ Company context loaded
3. ✅ Self (identity + tools) loaded
4. ✅ Active task identified and worked
5. ✅ Progress documented in task Work Log
6. ✅ Checklist items checked off
7. ✅ Next worker assigned (or handed to CEO)
8. ✅ Next employee triggered

---

## 🔄 Future-Proofing: Multi-Task Mode

**When we enable multi-tasking later:**

1. Remove single-task constraint from AGENTS.md
2. Change `active_task` to `active_tasks[]` (array)
3. Update WORK-LOCK to track multiple concurrent workers
4. Each employee picks from available tasks
5. CEO coordinates priority queue

**For now: One task. One worker. Complete focus.**

---

*Shift Protocol v2.0 — Single task, complete focus, verified completion.*
