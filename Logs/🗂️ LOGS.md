# 🗂️ Logs

Execution logs for cron jobs and agent shifts.

---

## Directory Structure

```
Logs/
├── cron-ceo-2026-02-06.log
├── cron-cto-2026-02-06.log
├── cron-cmo-2026-02-06.log
├── cron-eng-fe-2026-02-06.log
├── cron-eng-be-2026-02-06.log
└── 🗂️ LOGS.md (this file)
```

---

## Log Format

Each log file follows this format:

```
[2026-02-06T23:45:00Z] SHIFT START — Role: CTO
[2026-02-06T23:45:01Z] Lock acquired successfully
[2026-02-06T23:45:02Z] Loaded company context (README.md)
[2026-02-06T23:45:03Z] Loaded self (CTO/IDENTITY.md, CTO/TOOLS.md)
[2026-02-06T23:45:05Z] Found 2 active tasks
[2026-02-06T23:45:30Z] Working on TASK-001: Fix Gateway timeout
[2026-02-06T23:47:00Z] Progress: Implemented retry logic
[2026-02-06T23:50:00Z] Task updated with work log
[2026-02-06T23:50:05Z] Lock released
[2026-02-06T23:50:06Z] SHIFT COMPLETE — Duration: 5m 6s
```

---

## Retention Policy

- Keep 30 days of logs
- Archive monthly to `Logs/archive/YYYY-MM/`
- Delete logs older than 90 days

---

## Viewing Logs

To check recent activity:
```bash
ls -lt Logs/*.log | head -10
tail -50 Logs/cron-cto-2026-02-06.log
```

---

*Logs provide accountability and debugging context for agent operations.*
