# CRON-SYSTEM — Pink Beam Agent Cron Jobs

**Cron jobs for triggering employee shifts at Pink Beam.**

---

## 🕐 Available Cron Jobs

| Job Name | Role | Purpose | Status |
|----------|------|---------|--------|
| `pbb-ceo-shift` | CEO | Strategic execution, task activation, verification | Ready |
| `pbb-cto-shift` | CTO | Technical architecture, code review, mentorship | Ready |
| `pbb-cmo-shift` | CMO | Marketing, growth, brand, copy | Ready |
| `pbb-eng-fe-shift` | ENG-FE | Frontend, UI/UX, design system | Ready |
| `pbb-eng-be-shift` | ENG-BE | Backend, APIs, infrastructure | Ready |

---

## 🚀 How to Trigger a Shift Manually

These jobs are set to run in the far future (2036) so they don't auto-trigger. You run them manually when needed.

### Command

```bash
cron run pbb-{ROLE}-shift
```

### Examples

```bash
# Trigger CEO to activate a task from the queue
cron run pbb-ceo-shift

# Trigger CTO to work on technical implementation
cron run pbb-cto-shift

# Trigger CMO for marketing copy or strategy
cron run pbb-cmo-shift

# Trigger Frontend Engineer for UI implementation
cron run pbb-eng-fe-shift

# Trigger Backend Engineer for API/infrastructure work
cron run pbb-eng-be-shift
```

---

## 📋 What Each Job Does

When triggered, each job:

1. **Spawns an isolated agent session** (no memory from other sessions)
2. **Tells the agent their role** (CEO, CTO, CMO, ENG-FE, ENG-BE)
3. **Points them to AGENTS.md** as their boot sequence
4. **The agent then:**
   - Reads AGENTS.md (shift protocol)
   - Acquires the work lock
   - Loads company context (README.md)
   - Loads their identity (Org Chart/{ROLE}/IDENTITY.md)
   - Loads their tools (Org Chart/{ROLE}/TOOLS.md)
   - Checks for the active task
   - Executes work on that task
   - Reports back when complete

---

## 🔄 Typical Workflow

### Starting Work on a New Task

```bash
# 1. CEO activates task from queue
cron run pbb-ceo-shift

# 2. CEO sets active_task and triggers first worker
# (e.g., if task needs ENG-FE first)

# 3. First worker runs
cron run pbb-eng-fe-shift

# 4. When ENG-FE hands off to ENG-BE, they trigger:
cron run pbb-eng-be-shift

# 5. When task is complete, worker triggers CEO for verification:
cron run pbb-ceo-shift

# 6. CEO verifies, archives task, clears active_task, triggers next:
cron run pbb-cto-shift  # (or whoever works next task)
```

---

## 🧹 Cleaning Up Zombie Jobs

When a task completes, the CEO should kill all cron jobs before archiving:

```bash
# List all cron jobs
cron list

# Remove all Pink Beam shift jobs
cron remove pbb-ceo-shift
cron remove pbb-cto-shift
cron remove pbb-cmo-shift
cron remove pbb-eng-fe-shift
cron remove pbb-eng-be-shift

# Recreate them fresh for next task (if needed)
# (See vault documentation for recreation)
```

---

## ⚙️ Job Configuration Details

Each job is configured with:

```yaml
name: pbb-{ROLE}-shift
schedule:
  kind: at
  at: "2036-02-07T00:00:00Z"  # Far future — manual trigger only
sessionTarget: isolated        # Clean session, no memory
enabled: true
deleteAfterRun: true           # Clean up after execution
payload:
  kind: agentTurn
  message: "You are the {ROLE}... Read ~/obsidian/pinkbeam/AGENTS.md..."
```

### Key Settings

- **`sessionTarget: isolated`** — Each shift runs in a fresh session with no memory of previous shifts
- **`deleteAfterRun: true`** — Jobs clean up after running (but we keep them for reuse)
- **`enabled: true`** — Jobs are ready to run
- **Manual trigger via `cron run`** — No auto-execution

---

## 📝 Job Payload (What the Agent Receives)

Each job sends this message to the agent:

```
You are the {ROLE} of Pink Beam. Your role is {ROLE}.
Read ~/obsidian/pinkbeam/AGENTS.md and follow the shift protocol exactly.
Start by acquiring the work lock, then execute the active task.
Report back when your shift is complete or if you need to hand off to another employee.
```

The agent then follows the AGENTS.md protocol:
1. Check WORK-LOCK
2. Load context
3. Work on active task
4. Document progress
5. Release lock

---

## 🎯 Best Practices

### When to Trigger

**Trigger an employee when:**
- You're handing off the active task to them
- They need to review your work
- Their work blocks your progress
- CEO activates a new task and needs to trigger the first worker

**Don't trigger randomly** — Only when there's actual work to do.

### Single-Task Rule

Only ONE employee should be working at a time (enforced by WORK-LOCK). If you trigger an employee while another holds the lock, they'll see the lock is taken and exit silently.

### After Task Completion

When CEO verifies and completes a task:
1. Kill all cron jobs (see cleanup section above)
2. Clear WORK-LOCK.active_task
3. Recreate cron jobs if needed (for next task cycle)

---

## 🔧 Troubleshooting

### Job Not Found

If a job was accidentally deleted:

```bash
# Recreate it (adjust role name)
cron add --name pbb-{ROLE}-shift --at "2036-02-07T00:00:00Z" \
  --message "You are the {ROLE} of Pink Beam..."
```

### Agent Not Responding

If an agent session hangs:

```bash
# List active sessions
sessions_list

# Check session history
sessions_history --sessionKey <key>

# Send stop message if needed
sessions_send <key> "STOP — session ended by admin"
```

### Lock Stuck

If WORK-LOCK shows `status: locked` with old timestamp:

1. Check if work was abandoned
2. Document state in Notes
3. Manually release lock:
   ```yaml
   ---
   status: unlocked
   employee: ""
   active_task: ""
   started_at: ""
   ---
   ```

---

## 📁 Related Files

- **Shift Protocol:** `~/obsidian/pinkbeam/AGENTS.md`
- **Work Lock:** `~/obsidian/pinkbeam/WORK-LOCK/WORK-LOCK.md`
- **Active Task:** Tracked in `WORK-LOCK.active_task`
- **Task Queue:** `~/obsidian/pinkbeam/Tasks/TASKS.md`
- **Employee Directories:** `~/obsidian/pinkbeam/Org Chart/{ROLE}/`

---

*Cron System v1.0 — Manual triggering, isolated sessions, clean execution.*
