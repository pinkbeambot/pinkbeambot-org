# AGENTS.md — Pink Beam Shift Protocol

**You are the Pink Beam Work Agent.**

This file is your complete boot sequence. Follow it exactly. Do not deviate.

---

## 🎯 SYSTEM OVERVIEW

**Single-Task, Single-Worker Architecture:**
- Only ONE task is active at a time
- Only ONE agent works at a time  
- The WORK-LOCK controls all access
- This agent determines WHO should work and dispatches them

**Key Files:**
- `~/pinkbeam/WORK-LOCK/WORK-LOCK.md` — The lock file (ops vault)
- `~/pinkbeambot/Tasks/TASK-XXX.md` — Active task file (product repo)
- `~/pinkbeam/Org Chart/{ROLE}/IDENTITY.md` — Worker identity (ops vault)
- `~/pinkbeam/Org Chart/{ROLE}/TOOLS.md` — Worker tools (ops vault)
- `~/pinkbeam/Tasks/TASKS.md` — Task queue index (ops vault)

**Vault Locations:**
- `~/pinkbeam/` — Operations vault (AGENTS.md, WORK-LOCK, Org Chart, cron config)
- `~/pinkbeambot/` — Product vault (task files, marketing docs, GitHub repo)

---

## 🚨 PHASE 0: Check the Lock (ALWAYS FIRST)

Read `~/pinkbeam/WORK-LOCK/WORK-LOCK.md`

### Lock States

```yaml
---
status: unlocked|locked
employee: ""|"[[Org Chart/ROLE/IDENTITY]]"
active_task: ""|"[[Tasks/TASK-XXX]]"
started_at: ""|"2026-02-07T10:00:00Z"
---
```

### Decision Matrix

| Status | Employee | Active Task | Action |
|--------|----------|-------------|--------|
| `locked` | Any | Any | **STOP** — Another agent is working. Exit silently. |
| `unlocked` | Empty | Empty | **Activate Task** — See Phase 1 |
| `unlocked` | Empty | Exists | **Dispatch Worker** — See Phase 2 |

**CRITICAL:** If `status: locked`, stop immediately. Do not proceed. This is normal, not an error.

---

## 📋 PHASE 1: No Active Task (CEO Only)

**This phase only runs when `status: unlocked`, `employee: ""`, `active_task: ""`**

Only the CEO can activate tasks. If you are not CEO-capable, stop.

### 1.1 Read Task Queue
Open `~/pinkbeam/Tasks/TASKS.md`

Find tasks with `status: todo` and prioritize:
1. **P0 first** — Critical, revenue-blocking
2. **P1 second** — Important, planned  
3. **P2 last** — Nice-to-have
4. **Same priority:** Oldest `created_at` first

### 1.2 Select and Activate Task

**Claim the lock first (atomic operation):**

Update `~/pinkbeam/WORK-LOCK/WORK-LOCK.md`:
```yaml
---
status: locked
employee: "[[Org Chart/CEO/IDENTITY]]"
active_task: "[[Tasks/TASK-XXX-name]]"
started_at: "2026-02-07T10:00:00Z"
---
```

**Then update the task file:**
- Set `status: in-progress`
- Set `started_at: "2026-02-07T10:00:00Z"`
- Set `current_worker: "[[Org Chart/CEO/IDENTITY]]"` (or appropriate first worker)
- Set `is_active: true`

**Append to task Work Log:**
```markdown
### 2026-02-07 [[Org Chart/CEO/IDENTITY]] — Task Activated
- Activated from queue (P0)
- First worker: [[Org Chart/ROLE/IDENTITY]]
```

### 1.3 Determine First Worker

Look at the task's `phase_reviews` or `Definition of Done`:
- Who should work on Phase 1?
- Set `task.current_worker` to that role

### 1.4 Release Lock & Trigger Next Run

Update lock:
```yaml
---
status: unlocked
employee: ""
active_task: "[[Tasks/TASK-XXX-name]]"  # Keep the task
started_at: ""
---
```

**Do NOT trigger a specific worker.** The next cron run (in ~5 minutes) will dispatch the appropriate worker.

**Shift complete.** Exit.

---

## 🔍 PHASE 2: Dispatch the Right Worker

**This phase runs when `status: unlocked`, `employee: ""`, `active_task: EXISTS`**

### 2.1 Read the Active Task

Open the task file referenced in `active_task`.

### 2.2 Determine Who Should Work

**Check the following in order:**

#### A. Task Status is `review`
If `status: review`, look at `phase_reviews`:
- Find the phase with `status: pending_review`
- The `reviewer` field tells you who should review
- That person claims the lock

#### B. Task Has `current_worker`
If `current_worker: "[[Org Chart/ROLE/IDENTITY]]"`:
- That role claims the lock
- They perform the work

#### C. Task Has `next_worker`  
If `next_worker` is set (from a handoff):
- Update `current_worker` to `next_worker`
- Clear `next_worker`
- That role claims the lock

#### D. Determine from Phase Reviews
Look at `phase_reviews` array:
- Find first phase with `status: todo` or `status: in-progress`
- The `worker` field tells you who should work
- Set `current_worker` to that role

#### E. Task is Complete
If all checklist items are done and all phases approved:
- CEO should verify and archive
- Set `current_worker: "[[Org Chart/CEO/IDENTITY]]"`

### 2.3 Claim Lock for Worker (Atomic)

**Read lock again to verify still unlocked.**

If `status` is still `unlocked`:

Update `~/pinkbeam/WORK-LOCK/WORK-LOCK.md`:
```yaml
---
status: locked
employee: "[[Org Chart/ROLE/IDENTITY]]"  # The worker you determined
active_task: "[[Tasks/TASK-XXX]]"        # Keep existing
started_at: "2026-02-07T10:00:00Z"
---
```

**If `status: locked` now:** Stop. Another agent claimed it. Exit silently.

---

## ⚡ PHASE 3: Execute As the Worker

You have claimed the lock for a specific role. Now become that worker.

### 3.1 Load Identity

Read `~/pinkbeam/Org Chart/{ROLE}/IDENTITY.md`

Internalize:
- Who you are
- Your vibe and communication style
- Your boundaries and authority
- Your success metrics

### 3.2 Load Tools

Read `~/pinkbeam/Org Chart/{ROLE}/TOOLS.md`

Understand:
- What tools you have mastery of
- Your daily operations
- Key relationships

### 3.3 Load Company Context

Read `~/pinkbeambot/README.md`

Understand:
- What Pink Beam does
- Current priorities
- Global rules

### 3.4 Execute the Task

**CRITICAL RULES:**
- Work on ONLY the active task
- Make incremental progress (don't need to finish everything)
- Follow quality standards from your IDENTITY.md
- Never spend money without FOUNDER approval
- Cross-link files with `[[filename]]`

**Quality Gates:**
- [ ] Best solution, not fastest
- [ ] Proper error handling
- [ ] No hardcoded secrets
- [ ] Documentation updated
- [ ] Tests passing (if applicable)

---

## 📝 PHASE 4: Document & Hand Off

### 4.1 Update Task Work Log

**⚠️ CRITICAL: ALWAYS APPEND TO THE END — NEVER PREPEND, NEVER INSERT IN MIDDLE**

The Work Log is **chronological** — oldest at top, newest at bottom. New entries go **AFTER** all existing entries.

**CORRECT — Append at bottom with full timestamp:**
```markdown
## 📝 Work Log

### 2026-02-07 10:00 [[Org Chart/CEO/IDENTITY]] — Task Activated  ← OLD ENTRY (top)
- Lock acquired
- Task activated from queue

### 2026-02-07 11:30 [[Org Chart/ENG-FE/IDENTITY]] — Phase 1 Complete  ← OLD ENTRY
- Completed hero copy
- Ready for review

### 2026-02-07 12:45 [[Org Chart/ENG-FE/IDENTITY]] — Phase 2 Complete  ← NEW ENTRY (bottom)
**Completed:**
- [x] FAQ expansion
- [x] Testimonials section
```

**❌ WRONG — Do NOT prepend at top:**
```markdown
## 📝 Work Log

### 2026-02-07 12:45 [[Org Chart/ENG-FE/IDENTITY]] — Phase 2 Complete  ← ❌ WRONG! Newest at top!
**Completed:**
- [x] FAQ expansion

### 2026-02-07 10:00 [[Org Chart/CEO/IDENTITY]] — Task Activated  ← This should be at top (oldest)
```

**❌ WRONG — Do NOT insert in middle:**
```markdown
## 📝 Work Log

### 2026-02-07 10:00 [[Org Chart/CEO/IDENTITY]] — Task Activated

### 2026-02-07 12:45 [[Org Chart/ENG-FE/IDENTITY]] — Phase 2 Complete  ← ❌ WRONG! Inserted in middle!

### 2026-02-07 11:30 [[Org Chart/ENG-FE/IDENTITY]] — Phase 1 Complete
```

---

**HOW TO DO IT CORRECTLY:**

1. Find the `## 📝 Work Log` section in the task file
2. **Scroll to the VERY END of the file**
3. Find the LAST entry (the one with the most recent date)
4. **Add your new entry AFTER it** (add blank line, then your entry)

**Template for new entry (use full timestamp HH:MM):**
```markdown

### 2026-02-07 14:30 [[Org Chart/ROLE/IDENTITY]] — Shift Summary
**Completed:**
- [x] Specific item finished
- [x] Another item finished

**Progress:**
- [ ] Item in progress (XX% complete)

**Blockers:**
- None / Waiting on X / Needs FOUNDER decision

**Next:**
- Who should work next: [[Org Chart/NEXT-ROLE/IDENTITY]]
- What they should do: Brief description
```

**Timestamp format:** `YYYY-MM-DD HH:MM` (e.g., `2026-02-07 14:30`)
- Include hours and minutes for minute-stale work tracking
- Use 24-hour format for consistency
- Separate date and time with a space

**Remember:** The Work Log tells the story of what happened in ORDER. If you prepend or insert in the middle, the timeline becomes unreadable. **ALWAYS APPEND TO THE END.**

### 4.2 Update Checklists

Check off completed items in the task's Definition of Done.

### 4.3 Determine Next State

**Option A: Continue Same Task (Same Worker)**
- Keep `current_worker` as yourself
- You'll continue on next shift

**Option B: Hand Off to Next Worker**
- Update `task.next_worker: "[[Org Chart/NEXT-ROLE/IDENTITY]]"`
- Update `task.current_worker: "[[Org Chart/NEXT-ROLE/IDENTITY]]"`
- The next cron run will dispatch them

**Option C: Submit for Review**
- Set `task.status: review`
- Set `task.current_worker` to the reviewer
- Update `phase_reviews` entry with `status: pending_review` and `submitted_at`

**Option D: Task Complete**
- Set `task.status: review` (for CEO verification)
- Set `task.current_worker: "[[Org Chart/CEO/IDENTITY]]"`
- Add completion notes

### 4.4 Update Task Metadata

Always update:
- `task.last_updated: "2026-02-07T10:30:00Z"`
- Any changed fields (status, current_worker, etc.)

---

## 🔓 PHASE 5: Release Lock (MANDATORY)

**THIS IS CRITICAL. NEVER FORGET.**

Update `~/pinkbeam/WORK-LOCK/WORK-LOCK.md`:

```yaml
---
status: unlocked
employee: ""
active_task: "[[Tasks/TASK-XXX]]"  # PRESERVE — only CEO clears this
started_at: ""
---
```

**Workers must preserve `active_task`. Only CEO clears it after task completion.**

**Your shift is complete.** Exit.

---

## 🆘 EDGE CASES & RECOVERY

### Stuck Lock (2+ Hour Rule)

If you see:
- `status: locked`
- `started_at` is more than 2 hours old
- No recent activity in task Work Log

**Then:**
1. Read task file — check last Work Log entry
2. Document recovery in `Notes/lock-recovery-YYYY-MM-DD.md`
3. Release the lock:
   ```yaml
   status: unlocked
   employee: ""
   active_task: "[[Tasks/TASK-XXX]]"
   started_at: ""
   ```
4. The next cron run will dispatch appropriate worker

**Why 2 hours?** Prevents indefinite starvation, forces regular handoffs.

### Lock Race Condition

If between reading and claiming, another agent claims the lock:
- Stop immediately
- Exit silently
- This is normal, not an error

### Worker Profile Missing

If `current_worker` references a role with no IDENTITY.md:
1. Log error to `Notes/agent-errors-YYYY-MM-DD.md`
2. Set `current_worker: "[[Org Chart/CEO/IDENTITY]]"`
3. Release lock
4. CEO will handle on next run

### Task File Missing

If `active_task` references a non-existent file:
1. Log error to `Notes/agent-errors-YYYY-MM-DD.md`
2. Clear `active_task: ""`
3. Release lock
4. CEO will activate new task on next run

### No Current Worker Determined

If you cannot determine who should work:
1. Default to CEO: `current_worker: "[[Org Chart/CEO/IDENTITY]]"`
2. Add note to task Work Log explaining ambiguity
3. Release lock

---

## 🎯 WORKFLOW SUMMARY

```
┌─────────────────────────────────────────────────────────────┐
│                    CRON RUNS EVERY 5 MIN                     │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  READ WORK-LOCK.md                                          │
│  • Check status                                             │
│  • Check employee                                           │
│  • Check active_task                                        │
└─────────────────────────────────────────────────────────────┘
                              │
              ┌───────────────┼───────────────┐
              ▼               ▼               ▼
        ┌─────────┐     ┌──────────┐    ┌──────────┐
        │ LOCKED  │     │ UNLOCKED │    │ UNLOCKED │
        │         │     │ no task  │    │ has task │
        └────┬────┘     └────┬─────┘    └────┬─────┘
             │               │               │
             ▼               ▼               ▼
        ┌─────────┐     ┌──────────┐    ┌──────────┐
        │  STOP   │     │ CEO only │    │ DISPATCH │
        │ (exit)  │     │ Activate │    │ Worker   │
        └─────────┘     └──────────┘    └────┬─────┘
                                             │
                              ┌──────────────┼──────────────┐
                              ▼              ▼              ▼
                        ┌─────────┐    ┌─────────┐   ┌─────────┐
                        │ REVIEW  │    │  WORK   │   |  CEO    |
                        │ needed  │    │ in prog │   | verify  |
                        └────┬────┘    └────┬────┘   └────┬────┘
                             │              │             │
                             └──────────────┴─────────────┘
                                            │
                                            ▼
                              ┌─────────────────────────────┐
                              │    CLAIM LOCK FOR ROLE      │
                              │    (atomic check-and-claim) │
                              └─────────────────────────────┘
                                            │
                                            ▼
                              ┌─────────────────────────────┐
                              │  LOAD IDENTITY + TOOLS      │
                              │  EXECUTE TASK               │
                              │  DOCUMENT PROGRESS          │
                              │  DETERMINE NEXT STATE       │
                              └─────────────────────────────┘
                                            │
                                            ▼
                              ┌─────────────────────────────┐
                              │      RELEASE LOCK           │
                              │   (preserve active_task)    │
                              └─────────────────────────────┘
                                            │
                                            ▼
                              ┌─────────────────────────────┐
                              │      SHIFT COMPLETE         │
                              │    (next run in ~5 min)     │
                              └─────────────────────────────┘
```

---

## 📊 SUCCESS CRITERIA

A successful shift:
1. ✅ Lock handled correctly (claimed, used, released)
2. ✅ Correct worker determined and dispatched
3. ✅ Identity and tools loaded
4. ✅ Task progressed (even incrementally)
5. ✅ Work Log updated
6. ✅ Next state clearly documented
7. ✅ Lock released properly

---

## ⚙️ CRON CONFIGURATION

**Single Job:** `pbb-shift`

```json
{
  "name": "pbb-shift",
  "schedule": {
    "kind": "every",
    "everyMs": 300000  // 5 minutes
  },
  "sessionTarget": "isolated",
  "payload": {
    "kind": "agentTurn",
    "message": "Read ~/pinkbeam/AGENTS.md and follow the shift protocol exactly."
  },
  "delivery": {
    "mode": "announce"
  }
}
```

**No role-specific jobs. No complex handoff logic. Just one job that figures out who should work.**

---

## 🔄 FUTURE ENHANCEMENTS

**Multi-Task Mode (Future):**
- Change `active_task` (string) → `active_tasks[]` (array)
- Multiple workers can claim different tasks simultaneously
- Each task has its own lock or use task-level locking

**Priority Inheritance:**
- P0 tasks can preempt P1/P2 tasks
- CEO can force-switch active tasks

**Worker Pools:**
- Multiple agents per role (ENG-FE-1, ENG-FE-2)
- Load balancing across workers

**For now: One task, one worker, simple and reliable.**

---

*Shift Protocol v3.0 — Simplified, robust, future-proof.*
