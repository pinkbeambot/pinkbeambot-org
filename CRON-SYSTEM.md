# CRON-SYSTEM.md — Pink Beam Agent Scheduling

**Last Updated:** 2026-02-07  
**Version:** 3.0 — Simplified Single-Cron Architecture

---

## 🎯 Overview

Pink Beam uses a **single-cron, multi-role dispatch system**. One cron job runs every 5 minutes, checks the work state, and dispatches the appropriate worker.

**Previous Architecture:** Multiple cron jobs (one per role) with complex handoff chains  
**Current Architecture:** One cron job that determines who should work

---

## 🏗️ Architecture

### Single Job: `pbb-shift`

```
┌─────────────────────────────────────────────────────────────┐
│  pbb-shift runs every 5 minutes (300,000 ms)                │
│  Session: isolated (runs in background)                     │
│  Delivery: announce to webchat                              │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
              ┌─────────────────────────────┐
              │   Read WORK-LOCK.md         │
              │   Determine work state      │
              └─────────────────────────────┘
                            │
            ┌───────────────┼───────────────┐
            ▼               ▼               ▼
      ┌─────────┐    ┌──────────┐   ┌──────────┐
      │ LOCKED  │    │ UNLOCKED │   │ UNLOCKED │
      │         │    │ no task  │   │ has task │
      └────┬────┘    └────┬─────┘   └────┬─────┘
           │              │              │
           ▼              ▼              ▼
      ┌─────────┐   ┌──────────┐  ┌──────────┐
      │  EXIT   │   │ Activate │  │ Dispatch │
      │ (wait)  │   │  Task    │  │  Worker  │
      └─────────┘   │  (CEO)   │  │          │
                    └──────────┘  └────┬─────┘
                                       │
                                       ▼
                         ┌─────────────────────────┐
                         │   Claim Lock            │
                         │   Load Identity         │
                         │   Execute Task          │
                         │   Document Progress     │
                         │   Release Lock          │
                         └─────────────────────────┘
```

---

## 📋 Job Configuration

### pbb-shift

| Property | Value |
|----------|-------|
| **ID** | `9f2e5825-e17c-427f-96e5-dfa0784f8edf` |
| **Schedule** | Every 5 minutes (300,000 ms) |
| **Session** | Isolated (background) |
| **Target** | `main` agent |
| **Delivery** | Announce to webchat |

### Schedule Logic

```json
{
  "kind": "every",
  "everyMs": 300000
}
```

**Why 5 minutes?**
- Frequent enough for responsive handoffs
- Not so frequent it wastes compute
- Allows ~12 attempts per hour for stuck locks

---

## 🔒 Work Lock System

### Lock File

**Location:** `~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md`

```yaml
---
status: unlocked|locked
employee: ""|"[[Org Chart/ROLE/IDENTITY]]"
active_task: ""|"[[Tasks/TASK-XXX]]"
started_at: ""|"2026-02-07T10:00:00Z"
---
```

### Lock States

| Status | Employee | Task | Meaning | Action |
|--------|----------|------|---------|--------|
| `locked` | Any | Any | Work in progress | Exit silently |
| `unlocked` | Empty | Empty | Idle, need task | CEO activates |
| `unlocked` | Empty | Exists | Ready for worker | Dispatch worker |

### Atomic Claim Protocol

1. Read lock
2. Verify still `unlocked`
3. Write `locked` + employee + timestamp
4. If write fails (race condition), exit

---

## 👷 Worker Dispatch Logic

### Determining Who Should Work

The agent reads the active task file and checks:

1. **Task Status = `review`** → Dispatch reviewer from `phase_reviews`
2. **`current_worker` set** → Dispatch that worker
3. **`next_worker` set** → Update `current_worker`, dispatch
4. **Phase reviews** → Find first `todo`/`in-progress` phase, dispatch worker
5. **Task complete** → Dispatch CEO for verification

### Worker Roles

| Role | Directory | Purpose |
|------|-----------|---------|
| CEO | `Org Chart/CEO/` | Strategy, activation, verification |
| CTO | `Org Chart/CTO/` | Technical architecture, code review |
| CMO | `Org Chart/CMO/` | Marketing, copy, brand |
| ENG-FE | `Org Chart/ENG-FE/` | Frontend development |
| ENG-BE | `Org Chart/ENG-BE/` | Backend development |

---

## 📁 Key Files

| File | Purpose |
|------|---------|
| `AGENTS.md` | Complete boot protocol for all agents |
| `WORK-LOCK/WORK-LOCK.md` | Mutex for work coordination |
| `Tasks/TASK-XXX.md` | Active task definition |
| `Tasks/TASKS.md` | Task queue index |
| `Org Chart/{ROLE}/IDENTITY.md` | Worker personality & authority |
| `Org Chart/{ROLE}/TOOLS.md` | Worker capabilities |

---

## 🔄 Task Lifecycle

```
todo → in-progress → review → completed
        ↓              ↓
     blocked       rejected
        ↓              ↓
     waiting      → in-progress
```

### State Transitions

| From | To | Triggered By |
|------|-----|--------------|
| `todo` | `in-progress` | CEO activation |
| `in-progress` | `review` | Worker submission |
| `review` | `in-progress` | Rejection + feedback |
| `review` | `completed` | CEO approval |
| `in-progress` | `blocked` | Blocker identified |
| `blocked` | `in-progress` | Blocker resolved |

---

## 🆘 Recovery Protocols

### Stuck Lock (> 2 hours)

If `status: locked` and `started_at` > 2 hours ago:

1. Check task Work Log for last activity
2. Document in `Notes/lock-recovery-YYYY-MM-DD.md`
3. Force release lock:
   ```yaml
   status: unlocked
   employee: ""
   started_at: ""
   ```
4. Next cron run dispatches appropriate worker

### Missing Task File

If `active_task` points to non-existent file:

1. Log to `Notes/agent-errors-YYYY-MM-DD.md`
2. Clear `active_task: ""`
3. Release lock
4. CEO activates new task on next run

### Missing Worker Profile

If `current_worker` references missing IDENTITY.md:

1. Log error
2. Default to CEO
3. Release lock
4. CEO handles on next run

---

## 🎛️ Management Commands

### Check Cron Status

```bash
cron status
cron list
```

### View Job Runs

```bash
cron runs pbb-shift
```

### Manual Trigger

```bash
cron run pbb-shift
```

⚠️ **Only run manually for debugging.** Normal operation is automatic.

### Pause System

To temporarily stop all automation:

```bash
cron update pbb-shift --enabled=false
```

### Resume System

```bash
cron update pbb-shift --enabled=true
```

---

## 📊 Monitoring

### Check Current State

```bash
# View lock
cat ~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md

# View active task
cat ~/obsidian/pinkbeam/Tasks/TASK-001-pricing-marketing-implementation.md

# View task queue
cat ~/obsidian/pinkbeam/Tasks/TASKS.md
```

### View Run History

```bash
ls -la ~/.openclaw/cron/runs/
cat ~/.openclaw/cron/runs/{job-id}.jsonl
```

### Log Files

```bash
tail -f /tmp/openclaw/openclaw-2026-02-07.log | grep -i "pbb-shift\|cron"
```

---

## 🔮 Future Enhancements

### Multi-Task Mode

**Current:** `active_task: string`  
**Future:** `active_tasks: string[]`

- Multiple concurrent tasks
- Worker pool per role
- Task-level locking

### Priority Preemption

- P0 tasks can bump P1/P2 tasks
- CEO force-switch capability
- Graceful task suspension/resume

### Worker Pools

- ENG-FE-1, ENG-FE-2, etc.
- Load balancing
- Work stealing

---

## ❓ Troubleshooting

### "No jobs running"

Check: `cron list`  
Fix: `cron run pbb-shift` (one-time) or check if job is enabled

### "Lock stuck for hours"

Check: `cat ~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md`  
Fix: Force release following recovery protocol

### "Task not progressing"

Check: Task file Work Log section  
Fix: May be blocked, waiting for review, or ambiguous next worker (defaults to CEO)

### "Wrong worker dispatched"

Check: Task file `current_worker`, `next_worker`, `phase_reviews`  
Fix: Update fields to correct role

---

## ✅ Success Metrics

| Metric | Target |
|--------|--------|
| Lock cycle time | < 2 hours max |
| Task handoff latency | < 10 minutes (next cron run) |
| Stuck lock rate | < 1% of shifts |
| Agent crash recovery | Automatic within 2 hours |

---

*Simple, robust, future-proof.*
