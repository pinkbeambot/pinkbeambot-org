---
date: 2026-02-05
type: roadmap
tags:
  - pinkbeambot
  - strategy
  - roadmap
  - architecture
  - engineering
  - business
moc: "[[[MoC] Pink Beam]]"
---
# 🗺 Master Roadmap: From Origin to Market Manifestation

*Last Updated: 2026-02-05*

---

## 🌑 Phase 1: The Agency Foundation (Infrastructure & Brand Zero)
*Objective: Build the primary PinkBeamBot.com site and establish the VALIS "Resident Intelligence" on the host machine.*

**Status: 75% Complete — Core infrastructure operational, pricing/contact live**

### 1.1 Technical Plumbing (The Engine)
- [x] **OpenClaw Resident Setup:**
    - [x] Configure `gateway.bind` to secure loopback (127.0.0.1:18789) ✅
    - [x] Set up `cron` jobs for PM/ENG/CEO agent orchestration ✅
    - [ ] Configure Tailscale for remote owner access ⚠️ *PENDING*
    - [ ] **CRITICAL:** Resolve Gateway RPC timeout instability (documented in [[CEO-Audit-2026-02-05|CEO Audit]])
- [x] **Security Hardening (The Fortress):**
    - [x] Config file permissions fixed (600) and directory permissions (700) ✅
    - [x] Removed unused anthropic auth profile from config ✅
    - [ ] Implement secrets management vault (Cloudflare Secrets) for production keys
- [x] **Cloudflare Provisioning:**
    - [x] **D1 Database:** `pbb_core_db` initialized with tables:
        - [x] `social_posts` — social media content
        - [x] `contact_submissions` — lead capture
        - [x] `rate_limits` — API protection
    - [x] **KV Namespace:** `LIVING_PULSE` active for agent telemetry ✅
    - [x] **Pages Setup:** Cloudflare Pages with SSR enabled and deployed ✅

### 1.2 Frontend Architecture (The Hull)
- [x] **Design System (Tailwind + CSS):**
    - [x] Implement `global.css` with custom keyframes ✅
    - [x] Configure `tailwind.config.mjs` with brand colors ✅
    - [x] "Vertical Beam Scan" and "Glow Drift" animations ✅
- [x] **Core Layout Components:**
    - [x] `MainLayout.astro`: Deep Space background ✅
    - [x] `BeamTransition.astro`: Page transition scanner ✅
    - [x] `PulseBorder.astro`: Fuchsia heartbeat for cards ✅
    - [x] `SubagentFeed.astro`: Real-time telemetry display ✅
    - [x] `EngineModal.astro`: Interactive engine details ✅
- [x] **The Agency Homepage (Index.astro):**
    - [x] **Hero Section:** "Living Intelligence" copy ✅
    - [x] **Telemetry Feed:** Terminal widget from `LIVING_PULSE` ✅
    - [x] **Engine Showcase:** Interactive breakdown of [[Intel Engines]] ✅
    - [x] **Navigation:** Full site navigation with BeamTransition ✅

### 1.3 Market Intelligence & Pricing ✅ COMPLETE
- [x] **Competitor Deep Dive:**
    - [x] Research traditional Web Design Agency pricing ($2k–$5k flat fee)
    - [x] Research AI Automation Agency (AAA) retainer models ($1k–$3k/mo)
- [x] **The "Living Retainer" Model:**
    - [x] Define 5-tier pricing (Signal $29 → Enterprise $2,499+)
    - [x] Annual discount structure (20% off)
    - [x] Add-on pricing (+$49 platform, +$99 boost/support)
    - [x] Create `Pricing-Strategy.md` in Obsidian vault ✅
    - [x] **DEPLOYED:** `/pricing` page with interactive toggle and feature matrix

### 1.4 Lead Capture & Conversion ✅ COMPLETE
- [x] **Professional Contact Form:**
    - [x] Form fields: Name, Email, Business, Tier dropdown, Message
    - [x] Client validation with real-time feedback
    - [x] Honeypot spam protection
    - [x] Character counter (0/5000)
    - [x] **DEPLOYED:** `/contact` page live
- [x] **Backend API:**
    - [x] `POST /api/contact` endpoint with D1 storage
    - [x] Input sanitization and parameterized queries
    - [x] CORS configuration
    - [x] **Rate limiting:** 100 req/hr per IP (added 2026-02-05)

### 1.5 VALIS Integration (The Intelligence)
- [x] **Gog/Gmail Synchronization:**
    - [x] **Owner Action:** Create Google Cloud Project, enable Gmail/Calendar APIs
    - [x] **VALIS Action:** Run `gog auth` via terminal
- [ ] **Background Triage Setup:**
    - [ ] Configure `heartbeat.md` for 15-min inbox triage
    - [ ] Set up proactive email monitoring (not just reactive)

### 1.6 Quality Assurance & Legal Baseline
- [ ] **Data Privacy Framework:**
    - [ ] Draft "Living Data Policy" (how we handle/delete client email context)
    - [ ] Implement automated PII scrubbing in agent memory logs
- [ ] **Fail-Safe Protocol:**
    - [ ] Create "Kill Switch" mechanism to revoke agent tool access
- [ ] **Telemetry Monitoring:**
    - [ ] Set up Sentry for frontend error tracking
    - [x] Gateway log alerts configured (manual monitoring)
    - [ ] Automated alerting for "Loop Detected" or "API Rate Limited"

---

## 🌒 Phase 2: Revenue & Checkout (Critical Path)
*Objective: Convert interested visitors into paying customers.*

**Status: 0% Complete — Next Priority Phase**

### 2.1 Checkout Flow Integration 🎯 CRITICAL
- [ ] **Stripe Integration:**
    - [ ] Set up Stripe account and webhook endpoint
    - [ ] Create checkout sessions for Signal/Satellite/Pink Beam tiers
    - [ ] Handle subscription lifecycle (upgrade/downgrade/cancel)
- [ ] **Pricing Page Updates:**
    - [ ] Replace "Get Started" buttons with Stripe checkout links
    - [ ] Add "Enterprise" tier contact flow (separate from general contact)
- [ ] **Post-Checkout Onboarding:**
    - [ ] Welcome email sequence
    - [ ] Owner dashboard access provisioning

### 2.2 Analytics & Conversion Tracking 🎯 HIGH PRIORITY
- [ ] **Event Instrumentation:**
    - [ ] Pricing tier card clicks
    - [ ] Annual/monthly toggle usage
    - [ ] Add-on selection tracking
    - [ ] Contact form submissions (with source attribution)
- [ ] **Dashboard:**
    - [ ] Google Analytics 4 or Plausible setup
    - [ ] Conversion funnel visualization

### 2.3 Admin & Lead Management 🎯 HIGH PRIORITY
- [ ] **Lead Dashboard:**
    - [ ] View contact submissions from D1
    - [ ] Status management (new → contacted → converted → archived)
    - [ ] Export functionality (CSV)
- [ ] **Email Notifications:**
    - [ ] New lead alert to owner
    - [ ] Auto-responder to prospect

---

## 🌓 Phase 3: The Living Engine Library (Development)
*Objective: Build the 5 core modules identified in the [[Intel Engines]] as reusable Astro/OpenClaw templates.*

**Status: 0% Complete — Begins after Phase 2**

### 3.1 Engine Template Development
- [ ] **Module 1: The Scheduling Engine (Time-Sync):**
    - [ ] `skill-scheduling`: Natural language calendar negotiation logic
    - [ ] `template-scheduling`: Astro frontend with interactive booking widget
- [ ] **Module 2: The Continuity Engine (Membership):**
    - [ ] `skill-membership`: Churn detection and automated re-engagement logic
    - [ ] `template-membership`: Dashboard for member-only content delivery
- [ ] **Module 3: The Logistics Engine (Inventory):**
    - [ ] `skill-logistics`: Webhook integration for Shopify/Order statuses
- [ ] **Module 4: The Nurture Engine (Lead Gen):**
    - [ ] `skill-sales-rep`: Qualification logic and CRM (D1) sync
- [ ] **Module 5: The Information Engine (Authority):**
    - [ ] `skill-semantic-search`: Vector-based search of site content

### 3.2 The Owner Portal (Prototype)
- [ ] **`portal.pinkbeambot.com`:**
    - [ ] **Activity Log:** Unified view of agent actions
    - [ ] **Memory Manager:** Interface to see what VALIS has learned about the business
    - [ ] **Control Panel:** Global toggle for "Autonomous Action" vs. "Draft Only" mode

---

## 🌔 Phase 4: The Scaling Protocol (Agency Launch)
*Objective: Build the automation to provision and manage fleet-wide isolated instances.*

**Status: 0% Complete — Post-Revenue Phase**

### 4.1 Provisioning Automation
- [ ] **Client Onboarding Flow:**
    - [ ] `pinkbeambot.com/onboard`: Collection of client business metadata
    - [ ] **Deployment Script:** VALIS-run script to:
        - [ ] Fork client-specific repo
        - [ ] Deploy Cloudflare Pages instance
        - [ ] Provision isolated OpenClaw Gateway
- [ ] **Billing & Subscription Engine:**
    - [ ] Integrate Stripe for agency retainers
    - [ ] Implement usage-based billing logic for token passthrough
- [ ] **Documentation Hub:**
    - [ ] Build `docs.pinkbeambot.com` with onboarding guides

### 4.2 The Fleet Dashboard
- [ ] Multi-tenant view for the agency owner
- [ ] Health monitoring for all client "Heartbeats"

---

## 🌕 Phase 5: Full Autonomy (Post-Launch Evolution)
*Objective: Transition from "Helpful Assistant" to "Strategic Partner."*

### 5.1 Proactive Business Optimization
- [ ] **The Insight Engine:** VALIS analyzes weekly trends and suggests business pivots
- [ ] **Inter-Agent Communication:** Client agents coordinate with each other
- [ ] **Recursive Self-Improvement (RSI):**
    - [ ] VALIS monitors its own success rate on tasks
    - [ ] Automated A/B testing of different agent "personalities"

---

## 📋 Next Immediate Actions (Priority Order)

### This Week (Revenue Critical)
1. [ ] **Stripe Integration** — Enable checkout for self-service tiers
2. [ ] **Analytics Instrumentation** — Track pricing page interactions
3. [ ] **Lead Admin Dashboard** — View/manage contact submissions

### Infrastructure (Stability)
4. [ ] **Gateway RPC Fix** — Resolve timeout instability
5. [ ] **Email Notifications** — New lead alerts to owner
6. [ ] **Sentry Error Tracking** — Frontend monitoring

### Content (Marketing)
7. [ ] **Case Studies** — Add to `/work` page
8. [ ] **Blog/Authority Content** — Launch content marketing
9. [ ] **Social Proof** — Testimonials, client logos

---

**Key Metrics to Track:**
- Conversion rate: Pricing page → Contact form
- Conversion rate: Contact form → Stripe checkout
- Lead response time (goal: < 2 hours)
- Site uptime (goal: 99.9%)

[[pinkbeambot/ARCHITECT_DIRECTIVE|Directive]] | [[Intel Engines|Taxonomy]] | [[CEO-Audit-2026-02-05|Latest Audit]]
