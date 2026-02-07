# TOOLS.md - CTO

Environment-specific notes and available tools for the CTO role.

---

## 🔧 Core Platform

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **Cloudflare Workers** | Edge compute, serverless functions | ⭐⭐⭐⭐⭐ |
| **Cloudflare D1** | SQLite edge database | ⭐⭐⭐⭐⭐ |
| **Cloudflare KV** | Key-value store, edge caching | ⭐⭐⭐⭐⭐ |
| **Cloudflare R2** | Object storage (S3-compatible) | ⭐⭐⭐⭐⭐ |
| **Cloudflare Pages** | Static site hosting, CI/CD | ⭐⭐⭐⭐⭐ |
| **Durable Objects** | Stateful edge compute | ⭐⭐⭐⭐⭐ |

---

## 💻 Languages & Frameworks

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **TypeScript** | Primary language, strict mode | ⭐⭐⭐⭐⭐ |
| **Rust** | Systems programming, performance | ⭐⭐⭐⭐☆ |
| **Go** | Backend services, concurrency | ⭐⭐⭐⭐☆ |
| **Hono** | Lightweight web framework | ⭐⭐⭐⭐⭐ |
| **tRPC** | Type-safe APIs | ⭐⭐⭐⭐⭐ |
| **GraphQL** | API querying, schemas | ⭐⭐⭐⭐⭐ |

---

## 🗄️ Data & Storage

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **D1 (SQLite)** | Primary database | ⭐⭐⭐⭐⭐ |
| **PostgreSQL** | Advanced relational patterns | ⭐⭐⭐⭐⭐ |
| **Redis** | Caching, sessions, queues | ⭐⭐⭐⭐⭐ |
| **Vector DBs** | pgvector, Pinecone, embeddings | ⭐⭐⭐⭐⭐ |
| **R2** | File/object storage | ⭐⭐⭐⭐⭐ |

---

## 🧪 Testing & Quality

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **Vitest** | Unit testing | ⭐⭐⭐⭐⭐ |
| **Playwright** | E2E testing | ⭐⭐⭐⭐⭐ |
| **k6** | Load testing | ⭐⭐⭐⭐⭐ |
| **TypeScript Strict** | Compile-time safety | ⭐⭐⭐⭐⭐ |

---

## 📊 Observability

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **Sentry** | Error tracking | ⭐⭐⭐⭐⭐ |
| **Grafana** | Metrics visualization | ⭐⭐⭐⭐⭐ |
| **Custom Telemetry** | Business metrics | ⭐⭐⭐⭐⭐ |
| **Wrangler CLI** | CF deployment, logs | ⭐⭐⭐⭐⭐ |

---

## 🔐 Security

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **JWT/OAuth 2.0/OIDC** | Authentication | ⭐⭐⭐⭐⭐ |
| **Row-Level Security** | Data isolation | ⭐⭐⭐⭐⭐ |
| **HMAC/Web Crypto** | Signatures, encryption | ⭐⭐⭐⭐⭐ |
| **Threat Modeling** | Security design | ⭐⭐⭐⭐⭐ |

---

## 🚀 DevOps

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **GitHub Actions** | CI/CD pipelines | ⭐⭐⭐⭐⭐ |
| **Wrangler** | Cloudflare deployment | ⭐⭐⭐⭐⭐ |
| **Terraform** | Infrastructure as code | ⭐⭐⭐⭐☆ |

---

## 🤖 AI/ML Integration

| Tool | Purpose | Expertise |
|------|---------|-----------|
| **OpenAI API** | LLM integration | ⭐⭐⭐⭐⭐ |
| **Embeddings** | Vector search, semantic retrieval | ⭐⭐⭐⭐⭐ |
| **OpenClaw** | Agent orchestration | ⭐⭐⭐⭐⭐ |

---

## 📁 Local Development

```bash
# Repository location
cd ~/code/pinkbeambot-marketing

# Key commands
npm run build      # Verify build passes
npm run test       # Run test suite
npm run deploy     # Deploy to production
npx wrangler dev   # Local dev server
npx wrangler tail  # Stream logs
```

---

## 🔗 Quick References

- **Architecture Decisions:** Document in `Org Chart/CTO/Notes/`
- **Code Review Checklist:** Security, performance, maintainability
- **Escalation Path:** CEO for spending, FOUNDER for legal
- **Direct Reports:** ENG-FE, ENG-BE

---

## 🎯 Daily Operations

1. Check Work Lock status
2. Review shared tasks assigned to @CTO
3. Audit engineering work (builds, quality)
4. Code review and mentorship
5. Architecture documentation
6. Release Work Lock, trigger others if needed

---

*Tools mastered, standards enforced, excellence delivered.*
