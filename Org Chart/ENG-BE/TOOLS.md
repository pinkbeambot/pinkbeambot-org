# TOOLS.md - ENG-BE

Environment-specific notes and available tools for the Backend Engineer role.

---

## ☁️ Cloudflare Platform

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **Cloudflare Workers** | Edge compute, serverless | ⭐⭐⭐⭐⭐ |
| **Cloudflare D1** | SQLite edge database | ⭐⭐⭐⭐⭐ |
| **Cloudflare KV** | Key-value store | ⭐⭐⭐⭐⭐ |
| **Cloudflare R2** | Object storage | ⭐⭐⭐⭐⭐ |
| **Durable Objects** | Stateful edge compute | ⭐⭐⭐⭐⭐ |
| **Pages Functions** | Full-stack on Pages | ⭐⭐⭐⭐⭐ |

---

## 💻 Languages & Runtimes

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **TypeScript** | Primary language, strict mode | ⭐⭐⭐⭐⭐ |
| **Node.js** | Runtime, APIs | ⭐⭐⭐⭐⭐ |
| **Web Crypto API** | Native crypto in Workers | ⭐⭐⭐⭐⭐ |
| **SQL** | Database queries | ⭐⭐⭐⭐⭐ |

---

## 🗄️ Databases

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **D1 (SQLite)** | Primary database | ⭐⭐⭐⭐⭐ |
| **PostgreSQL** | Advanced relational | ⭐⭐⭐⭐⭐ |
| **SQLite** | Local dev, testing | ⭐⭐⭐⭐⭐ |
| **Redis** | Caching, sessions | ⭐⭐⭐⭐⭐ |

---

## 🔧 Frameworks & Libraries

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **Hono** | Web framework | ⭐⭐⭐⭐⭐ |
| **tRPC** | Type-safe APIs | ⭐⭐⭐⭐⭐ |
| **Zod** | Schema validation | ⭐⭐⭐⭐⭐ |
| **GraphQL** | API querying | ⭐⭐⭐⭐⭐ |

---

## 🔐 Security

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **JWT** | Authentication tokens | ⭐⭐⭐⭐⭐ |
| **HMAC** | Request signing | ⭐⭐⭐⭐⭐ |
| **bcrypt/Argon2** | Password hashing | ⭐⭐⭐⭐⭐ |
| **Web Crypto API** | Encryption, signing | ⭐⭐⭐⭐⭐ |
| **Row-Level Security** | Data isolation | ⭐⭐⭐⭐⭐ |

---

## 🧪 Testing

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **Vitest** | Unit testing | ⭐⭐⭐⭐⭐ |
| **Miniflare** | Local Workers runtime | ⭐⭐⭐⭐⭐ |
| **Integration Tests** | End-to-end API testing | ⭐⭐⭐⭐⭐ |
| **k6** | Load testing | ⭐⭐⭐⭐⭐ |

---

## 📊 Observability

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **Sentry** | Error tracking | ⭐⭐⭐⭐⭐ |
| **Wrangler Tail** | Log streaming | ⭐⭐⭐⭐⭐ |
| **Custom Metrics** | Business telemetry | ⭐⭐⭐⭐⭐ |
| **D1 Analytics** | Query performance | ⭐⭐⭐⭐⭐ |

---

## 🚀 DevOps

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **GitHub Actions** | CI/CD | ⭐⭐⭐⭐⭐ |
| **Wrangler CLI** | Deployment, secrets | ⭐⭐⭐⭐⭐ |
| **Terraform** | IaC (concepts) | ⭐⭐⭐⭐☆ |

---

## 💳 Payments & Integrations

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **Stripe API** | Payments, subscriptions | ⭐⭐⭐⭐☆ |
| **Webhooks** | Event handling | ⭐⭐⭐⭐⭐ |
| **Webhook Security** | Signature verification | ⭐⭐⭐⭐⭐ |
| **Idempotency** | Safe retries | ⭐⭐⭐⭐⭐ |

---

## 📁 Local Development

```bash
# Repository
cd ~/code/pinkbeambot-marketing

# Essential commands
npm run dev          # Start dev server
npm run build        # Verify build
npm run test         # Run tests
npx wrangler dev     # Local Workers
npx wrangler tail    # Stream production logs
npx wrangler d1 execute <db> --local --file=./schema.sql
```

---

## 🎯 Daily Operations

1. Check Work Lock status
2. Review shared tasks assigned to @ENG-BE
3. Verify builds pass, no uncommitted changes
4. Code review checklist:
   - Input validation on all APIs
   - Error handling (try/catch)
   - Proper HTTP status codes
   - No hardcoded secrets
   - TypeScript types defined
5. Optimize queries, review performance
6. Release Work Lock, trigger others if needed

---

## 🔗 Key Relationships

- **CTO:** Technical decisions, architecture approval
- **ENG-FE:** API contracts, data requirements
- **CEO:** Feature priority alignment

---

## 🚨 Code Quality Gates

**Required:**
- Input validation (Zod/schemas)
- Error handling with proper status codes
- TypeScript strict mode compliance
- Environment variables for secrets
- Tests for critical paths

**Red Flags (reject):**
- Hardcoded API keys
- Missing error handling
- `any` types without justification
- Console.log in production paths
- N+1 query patterns

---

*Bulletproof systems. Maximum uptime. Zero compromise.*
