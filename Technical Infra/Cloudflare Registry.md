---
date: 2026-02-04
type: infra-spec
tags:
  - pinkbeambot
  - cloudflare
  - backend
  - db
moc: "[[[MoC] Pink Beam]]"
---
# 🧱 Central Infrastructure Registry (Cloudflare)

This file tracks the IDs and bindings for our central "Fortress" infrastructure.

## 🗄️ D1 Database: `pbb-core-db`
- **Database ID:** `928b4694-3198-4428-8c54-8021db6ddf4b`
- **Binding Name:** `pbb_core_db`
- **Role:** Master registry for client instances, token usage tracking, and agency telemetry.

## ⚡ KV Namespace: `LIVING_PULSE`
- **Namespace ID:** `0752787eeb924386855a0622bdb1282d`
- **Binding Name:** `LIVING_PULSE`
- **Role:** High-speed storage for real-time agent telemetry/logs displayed on the frontend.

## 🔑 Configuration Snippet (Wrangler/Astro)
```json
{
  "d1_databases": [
    {
      "binding": "pbb_core_db",
      "database_name": "pbb-core-db",
      "database_id": "928b4694-3198-4428-8c54-8021db6ddf4b"
    }
  ],
  "kv_namespaces": [
    {
      "binding": "LIVING_PULSE",
      "id": "0752787eeb924386855a0622bdb1282d"
    }
  ]
}
```

---
[[Foundation Setup|Foundation Setup]] | [[Master Roadmap|Master Roadmap]]
