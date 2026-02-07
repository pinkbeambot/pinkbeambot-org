# AGENTS.md — Pink Beam Shift Protocol

**You are coming online for a shift at Pink Beam.**

This file is your boot sequence. Read it. Follow it. Do not deviate.

---

## 🚨 STEP 0: Acquire the Work Lock (MANDATORY)

**ONLY ONE EMPLOYEE WORKS AT A TIME.**

### 0.1 Read Current Lock Status
Open `WORK-LOCK/WORK-LOCK.md` and check the YAML frontmatter:

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
Update `WORK-LOCK/WORK-LOCK.md`:

```yaml
---
status: locked
employee: "[[Org Chart/CTO/IDENTITY]]"  # Link to your IDENTITY file
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

Check `WORK-LOCK/WORK-LOCK.md` field: `active_task`

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
3. Set `WORK-LOCK.active_task: "[[Tasks/TASK-XXX-name]]"`
4. Set `task.current_worker: "[[Org Chart/YOUR-ROLE/IDENTITY]]"` (if CEO work) or appropriate role
5. Proceed to Step 4

**If you are NOT CEO:**
1. Trigger CEO to activate a task: `cron run pbb-ceo-shift`
2. Go to Step 6 (Complete Shift)

---

## ⚡ STEP 4: Execute the Active Task

### 4.1 Update Lock
Update `WORK-LOCK/WORK-LOCK.md`:

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
Open the active task file. Append to the Work Log section:

```markdown
## Work Log

### 2026-02-07 @YOUR-ROLE
**Completed:**
- [x] Specific item finished
- [x] Another item finished

**Progress:**
- [ ] Item still in progress (XX% complete)

**Blockers:**
- None / Waiting on X / Needs @FOUNDER decision

**Notes:**
Any observations, decisions, or context for next shift.
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

**Step 2: Trigger Next Employee (WITH RETRY)**

```bash
# Attempt 1
cron run pbb-{NEXT-ROLE}-shift

# If failed (wait 5 seconds)
sleep 5

# Attempt 2
cron run pbb-{NEXT-ROLE}-shift

# If failed (wait 10 seconds)
sleep 10

# Attempt 3 (final)
cron run pbb-{NEXT-ROLE}-shift
```

**If all 3 attempts fail:**
1. Document failure in Work Log:
   ```markdown
   **Handoff Failed:** Could not trigger [[Org Chart/NEXT-ROLE/IDENTITY]] after 3 attempts
   **Manual intervention required:** Run `cron run pbb-{NEXT-ROLE}-shift`
   ```
2. Update `WORK-LOCK.task: "Handoff failed — manual trigger needed"`
3. Release lock
4. The next worker can still start by running their job manually

**Step 3: Complete Your Shift**
- Go to Step 6 (Complete Shift)

---

**If task IS complete (100% of checklist checked):**
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

Update `WORK-LOCK/WORK-LOCK.md`:

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
