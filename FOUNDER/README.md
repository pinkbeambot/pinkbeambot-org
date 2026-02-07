# FOUNDER — Human Intervention Directory

**This directory is for FOUNDER (human) only.**

AI agents should NOT read or write here without explicit permission, except when creating escalation todos.

---

## Directory Structure

```
FOUNDER/
├── README.md          # This file
├── IDENTITY.md        # Founder identity and boundaries
├── TOOLS.md           # Founder-specific tools and notes
└── Todos/             # Escalation items requiring human action
    └── TODO-XXX.md    # Individual todo files
```

---

## Todos/ — Escalation Queue

When AI agents need human intervention, they create files here.

### Creating a Todo

**Naming:** `TODO-{NNN}-{brief-description}.md`

**Template:**
```markdown
---
id: "TODO-001"
assigned_to: "[[Org Chart/FOUNDER/IDENTITY]]"
priority: P0  # P0 = urgent, P1 = important, P2 = when convenient
status: todo  # todo | in-progress | completed
created_at: "2026-02-07T00:00:00Z"
created_by: "[[Org Chart/CEO/IDENTITY]]"  # Who escalated
---

# TODO-001: Brief Description

**Escalated from:** [[Org Chart/CEO/IDENTITY]]
**Related Task:** [[Tasks/TASK-004]]  # If applicable
**Reason:** Why human intervention is needed

## Context

Full description of the situation, what was tried, why it failed.

## Options

1. Option A — with pros/cons
2. Option B — with pros/cons

## Recommendation

What the agent thinks should happen.

## Required Action

What specifically needs the FOUNDER to do.
```

---

## Privacy

- **Notes/ and Chats/ subdirectories** (if created) are PRIVATE
- AI agents do NOT read these without explicit permission
- AI agents do NOT write to these directories
- Personal information stays in this directory only

---

## When to Escalate to FOUNDER

Agents should create todos here when:

- **Spending approval needed** — Paid services, tools, infrastructure costs
- **Legal decisions** — Contracts, terms changes, liability issues
- **Account setup requiring human identity** — Stripe, banking, etc.
- **Strategic pivots** — Major direction changes affecting company
- **Team deadlock** — AI agents cannot agree or are stuck
- **Ethical concerns** — Something feels wrong or risky
- **External communications** — Emails, public posts, customer calls

---

## When NOT to Escalate

Agents should NOT escalate when:

- They can make the decision autonomously (per their IDENTITY.md)
- There's a free alternative to a paid solution
- It's a technical implementation detail
- It's a routine task within their authority

---

*This directory is the bridge between AI autonomy and human judgment.*
