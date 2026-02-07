---
date: 2026-02-05
type: strategy
tags:
  - pinkbeambot
  - architecture
  - business-logic
  - taxonomy
moc: "[[[MoC] Pink Beam]]"
---
# 🏗️ Living Website Business Taxonomy

## 🌌 Overview
To scale the **Pink Beam Bot** agency, we categorize businesses by their **operational engines** rather than their industries. This allows us to build reusable [[VALIS Protocol|VALIS Modules]] that can be deployed across various client instances.

## ⚙️ Core Operational Engines

### 1. The Scheduling Engine (Time-Sync)
*Focus: Managing the finite resource of the owner's time.*
- **VALIS Role:** Autonomous Booking Agent.
- **Key Actions:** 24/7 calendar negotiation via email/chat, rescheduling, intake triage.
- **Primary Verticals:** [[Verticals/Tax Professionals|Tax Pros]], Barbers, Lawyers, Therapists.

### 2. The Continuity Engine (Membership)
*Focus: Retention, content delivery, and community health.*
- **VALIS Role:** Digital Concierge.
- **Key Actions:** Password recovery, onboarding, churn detection, payment failure triage.
- **Primary Verticals:** Gyms, Online Courses, Paid Newsletters.

### 3. The Logistics Engine (Product/Inventory)
*Focus: Managing physical/digital assets and order flow.*
- **VALIS Role:** Virtual Warehouse Manager.
- **Key Actions:** Order status tracking, stock alerts, supplier coordination.
- **Primary Verticals:** Boutique E-commerce, Local Bakeries, Print Shops.

### 4. The Nurture Engine (Lead Gen)
*Focus: Qualifying cold leads for high-ticket sales.*
- **VALIS Role:** 24/7 Sales Development Rep (SDR).
- **Key Actions:** Qualification Q&A, CRM synchronization, long-term follow-up.
- **Primary Verticals:** Real Estate, Marketing Agencies, Custom Home Builders.

### 5. The Information Engine (Authority)
*Focus: Semantic search and knowledge management.*
- **VALIS Role:** Librarian & SEO Strategist.
- **Key Actions:** Semantic FAQ handling, automated SEO tagging, social media summarization.
- **Primary Verticals:** Bloggers, Portfolio Sites, Non-profits.

---

## 🆕 Extended Operational Engines (Phase 2)

### 6. The Social Sync Engine (Presence)
*Focus: Real-time social media mirroring and amplification.*
- **VALIS Role:** Social Media Synchronizer.
- **Key Actions:** 
  - Pull latest posts from X/Twitter, Instagram, LinkedIn
  - Display social feeds directly on the website
  - Cross-platform content distribution
  - Optimal posting time suggestions
- **Primary Verticals:** Personal Brands, Influencers, Marketing Agencies, Restaurants
- **Tech Spec:** [[Tech Spec - Social Sync Engine]]
- **Status:** 🚧 In Development - Phase 1.4

### 7. The Social Proof Engine (Community)
*Focus: Curating and displaying user-generated content and brand mentions.*
- **VALIS Role:** Community Curator.
- **Key Actions:**
  - Monitor brand mentions, hashtags, and reshares
  - Sentiment analysis on mentions
  - Display "Wall of Love" with authentic customer posts
  - Auto-respond to positive mentions
- **Primary Verticals:** E-commerce, SaaS, Local Businesses, Event Venues
- **Dependencies:** Social Sync Engine
- **Status:** 📋 Planned - Phase 2.1

### 8. The Autonomous Content Engine (Publication)
*Focus: Self-writing blog and content generation.*
- **VALIS Role:** Digital Journalist & Content Strategist.
- **Key Actions:**
  - Research trending topics in business niche
  - Draft SEO-optimized blog posts
  - Queue for human approval or auto-publish
  - Meta-blogging: "How I optimized your site today"
- **Primary Verticals:** News Sites, Thought Leaders, Niche Blogs, Agency Sites
- **Status:** 📋 Planned - Phase 2.2

### 9. The Trend Pulse Engine (Intelligence)
*Focus: Industry trend monitoring and competitive intelligence.*
- **VALIS Role:** Market Intelligence Analyst.
- **Key Actions:**
  - Monitor competitor blogs and industry news
  - Track Google Trends for relevant keywords
  - Alert on emerging topics before they peak
  - Feed insights to Autonomous Content Engine
- **Primary Verticals:** Competitive Industries, Fast-Moving Markets, Tech Companies
- **Status:** 📋 Planned - Phase 2.3

---

## 🎯 Engine Pricing Tiers (NEW - 5 Tier Structure)

*Based on [[Pricing Strategy Analysis]] - Proposed restructure to capture full market spectrum*

### Proposed New Pricing (2026-02-05)

| Tier | Monthly | Annual | Included Engines | Target Client |
|------|---------|--------|------------------|---------------|
| **Signal** | $29/mo | $290/yr | Information Engine only | Side hustlers, landing pages |
| **Satellite** | $79/mo | $790/yr | Information + Basic Scheduling | Small businesses, creators |
| **Pink Beam** | $299/mo | $2,990/yr | 4 Core Engines | Growing businesses, agencies |
| **Full VALIS** | $999/mo | $9,990/yr | All 9 Engines + Autonomous Content | Established businesses |
| **Enterprise** | $2,499+/mo | Custom | Everything + Custom Development | Large orgs, franchises |

### Legacy Pricing (Current - For Reference)
| Tier | Monthly | Included Engines |
|------|---------|------------------|
| **Satellite** | $50/mo | Information Engine only |
| **Pink Beam** | $500/mo | Scheduling + Continuity + Social Sync + Information |
| **Full VALIS** | $2000/mo | All 9 Engines |

**Key Changes:**
- Added **Signal** tier ($29) for entry-level market
- Added **Enterprise** tier ($2,499+) for whales
- **Satellite** increased from $50 → $79 (better value alignment)
- **Pink Beam** reduced from $500 → $299 (fills massive gap)
- **Full VALIS** reduced from $2000 → $999 (psychological threshold)

### Add-Ons (Increase ARPU)
| Add-On | Monthly | Description |
|--------|---------|-------------|
| Extra Social Account | $49/account | Beyond tier limit |
| Content Boost Pack | $99 | 10 additional AI-generated posts |
| Priority Support | $99 | 4hr response time |
| Custom Domain Setup | $49 one-time | White-glove DNS config |
| Migration Service | $299 one-time | From WordPress/Squarespace |

### Discounts
- **Annual:** 2 months free (17% discount)
- **Non-profits:** 30% off all tiers
- **Startups:** 50% off first 6 months
- **Open Source:** Free Signal tier

---

## 🛠️ Implementation Strategy: Modular Skills
Instead of building monolithic sites, we develop **OpenClaw Skills** that map to these engines.
- `skill-scheduling`: Connects to Google/Outlook Calendar.
- `skill-continuity`: Connects to Stripe/MemberStack.
- `skill-logistics`: Connects to Shopify/Inventory APIs.
- `skill-social-sync`: Connects to X/Twitter, Instagram, LinkedIn APIs. 🆕
- `skill-content-autonomy`: Web research + content generation pipeline. 🆕

---
**Next Actions:**
- [ ] Define the technical spec for `skill-social-sync`. → [[Tech Spec - Social Sync Engine]]
- [ ] Implement Social Sync Engine in `pinkbeambot-engines` repo.
- [ ] Create "Owner Portal" mockup that displays Engine-specific logs.
- [ ] Update marketing site with new engine grid.

[[[MoC] Pink Beam|Back to MoC]] | [[High Level Vision|Vision]] | [[pinkbeambot/dev/Tech Spec - Social Sync Engine|Social Sync Spec]]
