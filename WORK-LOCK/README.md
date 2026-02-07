# WORK-LOCK — Single-Threaded Execution Control

This directory prevents race conditions by ensuring only one Pink Beam employee works at a time.

## Key Files

| File           | Purpose                                                     |
| -------------- | ----------------------------------------------------------- |
| `WORK-LOCK.md` | **Critical** — The lock itself. Check this before ANY work. |

## How the Lock Works

### For Employees Starting a Shift

**Step 1: Read the lock FIRST**
```bash
# Open WORK-LOCK.md
```

**Step 2: Check the YAML frontmatter:**
```yaml
---
status: locked | unlocked
shift: @employee-role
task: Brief description
---
```

**Step 3: Act based on status:**
- **`status: locked`** → **STOP IMMEDIATELY**
  - Another employee is working
  - Do nothing and exit
  - If running as cron, terminate silently
  
- **`status: unlocked`** → **Claim the lock and work**
  ```yaml
  ---
  status: locked
  shift: @YOUR-ROLE
  task: What you're working on
  ---
  ```

**Step 4: Do your work** (only one employee at a time)

**Step 5: Release the lock when done**
```yaml
---
status: unlocked
shift:
task:
---
```

## Critical Rules

1. **NEVER work without checking the lock first**
2. **If locked → stop immediately**, no exceptions
3. **If cron and locked → terminate silently** (no output)
4. **Always unlock when finished** — others are waiting
5. **The lock file stays minimal** — only YAML frontmatter changes

## Why This Matters

The Obsidian vault is a shared workspace. If two employees edit simultaneously:
- Files get corrupted
- Tasks get duplicated
- Work gets lost

**Single-threaded execution prevents chaos.**

---

*The lock is the gate. Check it, claim it, release it.*
