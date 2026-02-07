---
created: {{date:YYYY-MM-DD}}T{{time:HH:mm}}
updated: {{date:YYYY-MM-DD}}T{{time:HH:mm}}
type: employee
role: 
status: active
reports_to: 
---

# {{role}}

> **Role Code:** 
> **Status:** 🟢 Active
> **Reports To:** 

## 📁 Employee Files

| Document | Purpose |
|----------|---------|
| [[README]] | This dashboard — start here every shift |
| [[pinkbeam/Org Chart/PM/SHIFT-PROTOCOL]] | Step-by-step shift instructions |
| [[IDENTITY]] | Role definition and identity |
| [[SKILLS]] | Capabilities and expertise |

## 📂 Shared Directories

| Location | Purpose |
|----------|---------|
| [[Tasks/TASKS\|Tasks]] | All work (shared) — check for your assignments |
| [[Notes/🗂️ NOTES\|Notes]] | All notes (shared) — contribute knowledge |

## 🎯 Current Focus
<!-- Link to active tasks -->
- [ ] 

## 📊 Quick Stats
| Metric | Value |
|--------|-------|
| Tasks In Progress | 0 |
| Tasks Completed | 0 |
| Last Active | {{date:YYYY-MM-DD}} |

---

## 🏷️ Template Instructions

**How to use this template:**
1. Copy the entire `_EMPLOYEE` folder to `Org Chart/{ROLE}/`
2. Rename the folder to the role code (e.g., `CTO`, `PM`, `ENG-FE`)
3. Update frontmatter: `role`, `reports_to`, `status`
4. Fill out each linked document (IDENTITY, SKILLS, SHIFT-PROTOCOL)
5. This README serves as the employee's dashboard

**Role Naming Convention:**
- Use uppercase role codes: CEO, CTO, CMO, PM, ENG-FE, ENG-BE
- Keep it short and clear

**Important:**
- Tasks are in shared `Tasks/` folder — update `TASKS.md` index
- Notes are in shared `Notes/` folder — update `🗂️ NOTES.md` index
- **SHIFT-PROTOCOL.md lives at top level** (next to README)
- Cross-link everything using `[[filename]]`

---

## 🕐 Shift Start Instructions

**When you wake up:**

1. **Read this README** — This is your dashboard and identity
2. **Read your [[pinkbeam/Org Chart/PM/SHIFT-PROTOCOL|Shift Protocol]]** — Step-by-step shift instructions
3. **Check [[Tasks/TASKS|Tasks]]** — Look for tasks assigned to you
4. **Execute your shift** — Follow the protocol

**System Instructions:** [[_TEMPLATES/_INSTRUCTIONS/MASTER-GUIDE|MASTER-GUIDE]]

**You can trigger other employees:**
```bash
cron run pbb-ceo-shift
cron run pbb-cto-shift
cron run pbb-cmo-shift
cron run pbb-pm-shift
cron run pbb-eng-fe-shift
cron run pbb-eng-be-shift
```

Trigger someone when:
- You assigned them work and want them to start
- Their work is blocking your progress
- You want them to review your work
- You completed work and need their review/approval

---

**See full instructions:** [[_TEMPLATES/_INSTRUCTIONS/MASTER-GUIDE|Documentation System Guide]]
