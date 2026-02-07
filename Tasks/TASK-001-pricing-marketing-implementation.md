---
id: TASK-001
title: Implement Pricing & Marketing Strategy Updates
status: in-progress
priority: P0
created_at: 2026-02-07T00:20:00Z
created_by: "[[Org Chart/CMO/IDENTITY]]"
started_at: "2026-02-07T08:47:00Z"
completed_at: ""
verified_at: ""
assigned_to: "[[Org Chart/CMO/IDENTITY]]"
collaborators:
  - "[[Org Chart/ENG-FE/IDENTITY]]"
  - "[[Org Chart/ENG-BE/IDENTITY]]"
current_worker: "[[Org Chart/ENG-BE/IDENTITY]]"
next_worker: ""
estimated_hours: 24
actual_hours: 0
dependencies: []
blocks: []
is_active: true
verified_by: ""

# Phase Reviews (gate between each phase)
phase_reviews:
  - phase: "Phase 1: Quick Wins — Copy Updates"
    worker: "[[Org Chart/ENG-FE/IDENTITY]]"
    reviewer: "[[Org Chart/CMO/IDENTITY]]"
    status: approved
    submitted_at: "2026-02-07T09:02:00Z"
    approved_at: "2026-02-07T09:20:00Z"
  - phase: "Phase 2: Content Expansion"
    worker: "[[Org Chart/ENG-FE/IDENTITY]]"
    reviewer: "[[Org Chart/CMO/IDENTITY]]"
    status: approved
    submitted_at: "2026-02-07T09:35:00Z"
    approved_at: "2026-02-07T09:55:00Z"
  - phase: "Phase 3: Pricing Structure Updates"
    worker: "[[Org Chart/ENG-BE/IDENTITY]] + [[Org Chart/ENG-FE/IDENTITY]]"
    reviewer: "[[Org Chart/CTO/IDENTITY]]"
    status: rejected
    submitted_at: "2026-02-07T09:56:00Z"
    approved_at: ""
  - phase: "Phase 4: VALIS Section Rewrite"
    worker: "[[Org Chart/ENG-FE/IDENTITY]]"
    reviewer: "[[Org Chart/CMO/IDENTITY]]"
    status: todo
    submitted_at: ""
    approved_at: ""
  - phase: "Phase 5: Final Polish"
    worker: "[[Org Chart/ENG-FE/IDENTITY]]"
    reviewer: "[[Org Chart/CTO/IDENTITY]]"
    status: todo
    submitted_at: ""
    approved_at: ""
  - phase: "Phase 6: Review & Launch"
    worker: "[[Org Chart/CMO/IDENTITY]] + [[Org Chart/CEO/IDENTITY]]"
    reviewer: "[[Org Chart/CEO/IDENTITY]]"
    status: todo
    submitted_at: ""
    approved_at: ""

tags:
  - frontend
  - marketing
  - pricing
  - revenue-critical
  - copy
---

# TASK-001: Implement Pricing & Marketing Strategy Updates

## 🎯 Objective
Implement the comprehensive pricing and marketing strategy updates from the CMO's analysis to improve conversion rates, clarify messaging, and increase revenue per customer.

**Source Strategy:** [[Notes/PRICING-MARKETING-STRATEGY-2026-02]]

---

## 📖 Context

The CMO completed a full audit of our pricing and marketing strategy. Key findings:
- Pricing tiers are well-positioned ($29-$2,499)
- Marketing messaging is too abstract/mystical
- Hero copy doesn't convert business buyers
- Setup fees should be added
- Add-ons need restructuring
- Website needs trust signals and clearer value props

This task implements all approved changes from that strategy.

---

## ✅ Definition of Done

### Phase 1: Quick Wins — Copy Updates (ENG-FE) ⏳ AWAITING REVIEW
**Worker:** [[Org Chart/ENG-FE/IDENTITY]]  
**Reviewer:** [[Org Chart/CMO/IDENTITY]]  
**Status:** Complete, pending CMO review

**Review Criteria:**
- Copy matches CMO strategy document
- Brand voice is consistent
- CTAs are clear and compelling
- Trust signals are visible

**Phase 1 Checklist:**
- [x] Update hero copy on home page
  - [x] Change from "The Web is Waking Up" to "Your Website Works While You Sleep"
  - [x] Add subhead: "AI-powered websites that answer customer questions, book appointments, and generate leads — automatically. No coding required."
  - [x] Update CTAs to "See What It Can Do" and "View Plans"
- [x] Add "How It Works" section to home page (4-step process)
- [x] Update pricing tier descriptions in [[Intel Engines]]
  - [x] Signal: "For solo founders & side projects"
  - [x] Satellite: "For local businesses & creators"
  - [x] Pink Beam: "For scaling companies"
  - [x] Full VALIS: "For companies ready to automate"
  - [x] Enterprise: "For teams with custom needs"
- [x] Add trust signals to home page
  - [x] "99.9% Uptime SLA" badge
  - [x] "30-Day Money-Back Guarantee" badge
  - [x] "Human Support When You Need It" badge

### Phase 2: Content Expansion (ENG-FE) ⏳ AWAITING REVIEW
**Worker:** [[Org Chart/ENG-FE/IDENTITY]]  
**Reviewer:** [[Org Chart/CMO/IDENTITY]]  
**Status:** Complete, pending CMO review

**Review Criteria:**
- FAQ answers are clear and helpful
- Testimonials section is well-designed
- Meta descriptions include target keywords
- Content aligns with brand voice

**Phase 2 Checklist:**
- [x] Rewrite engines preview section on home page
  - [x] Lead with problems solved, not engine names — "What Can Your Website Do For You?"
  - [x] Icons already present for each capability (Search, Calendar, Users, Share2, ShoppingCart, TrendingUp)
  - [x] Benefit-focused copy already in place ("Stop answering the same emails", "No phone tag", etc.)
- [x] Expand FAQ section
  - [x] "How is this different from a chatbot?" — Added with comparison to receptionist analogy
  - [x] "What if the AI gets something wrong?" — Added with training & monitoring explanation
  - [x] "Can I change my tier later?" — Added with upgrade/downgrade details
  - [x] "Do I need technical skills?" — Added with "No coding required" message
  - [x] "How long does setup take?" — Already present
- [x] Add testimonials section to home page
  - [x] Testimonials section already exists with 3 quotes + metrics
  - [x] "REAL RESULTS" badge included
  - [x] Quote card component with hover effects implemented
- [x] Update all meta descriptions
  - [x] Home page: Already updated per strategy doc
  - [x] Pricing page: Already updated — "Simple pricing for serious results..."
  - [x] No separate engine pages to update

### Phase 3: Pricing Structure Updates (ENG-BE + ENG-FE) ❌ REJECTED
**Worker:** [[Org Chart/ENG-BE/IDENTITY]] + [[Org Chart/ENG-FE/IDENTITY]]  
**Reviewer:** [[Org Chart/CTO/IDENTITY]]  
**Status:** Rejected — Critical pricing mismatches found

**Review Criteria:**
- Setup fees work correctly in Stripe
- Add-on pricing is clear to users
- No breaking changes to existing customers
- Code passes technical review

**Phase 3 Checklist:**
- [x] Add setup fees to pricing configuration
  - [x] Signal: $199
  - [x] Satellite: $299
  - [x] Pink Beam: $399
  - [x] Full VALIS: $499
  - [x] Enterprise: "Custom"
- [x] Update pricing display to show setup fees
  - [x] Show "+$XXX setup" next to monthly price
  - [~] Add tooltip explaining one-time fee (low priority)
- [~] Restructure add-ons
  - [x] Remove confusing add-ons (e.g., "Add Scheduling Engine" when Satellite includes it)
  - [x] Add new add-on structure:
    - [x] Engine Unlock: $49/mo (pricing page)
    - [x] Interaction Boost: $79/mo ✓
    - [x] Extra Social Platform: $39/mo (pricing page)
    - [x] Priority Support: $99/mo ✓
    - [x] Content Boost: $149/mo (pricing page)
  - [ ] Add one-time add-ons:
    - [ ] Migration Service: $299
    - [ ] Custom Domain Setup: $49
    - [ ] Content Import: $199
- [~] Update Stripe products/prices to match new structure
  - [x] Setup fees in checkout API ✓
  - [ ] **CRITICAL:** Fix add-on prices in checkout API to match pricing page
  - [ ] **CRITICAL:** Fix add-on IDs in checkout API to match pricing page

### Phase 4: VALIS Section Rewrite (ENG-FE) 🔒 LOCKED
**Worker:** [[Org Chart/ENG-FE/IDENTITY]]  
**Reviewer:** [[Org Chart/CMO/IDENTITY]]  
**Status:** Locked — Phases 1-3 must be reviewed first

**Review Criteria:**
- Messaging is compelling
- VALIS concept is clear but not overwhelming
- Business value is front and center

**Phase 4 Checklist:**
- [ ] Rewrite "Meet Your Digital Employee" section
- [ ] Lead with business transformation angle
- [ ] Keep VALIS as underlying tech story
- [ ] Use bullet list of capabilities:
  - [ ] Answers customer questions 24/7
  - [ ] Books appointments while you sleep
  - [ ] Follows up with leads automatically
  - [ ] Keeps your content fresh
  - [ ] Never takes a day off
- [ ] Add closing line: "Think of it as hiring a digital employee for the price of software."

### Phase 5: Final Polish (ENG-FE) 🔒 LOCKED
**Worker:** [[Org Chart/ENG-FE/IDENTITY]]  
**Reviewer:** [[Org Chart/CTO/IDENTITY]]  
**Status:** Locked — Phases 1-4 must be reviewed first

**Review Criteria:**
- Code quality meets standards
- All CTAs are consistent
- Mobile responsive
- Performance acceptable
- No broken links

**Phase 5 Checklist:**
- [ ] Update CTA buttons sitewide
  - [ ] "Explore Engines" → "See What It Can Do"
  - [ ] "See Pricing" → "View Plans"
  - [ ] Ensure consistent CTAs
- [ ] Add "Trusted By" section with customer count
- [ ] Ensure all changes are mobile-responsive
- [ ] Verify all links work
- [ ] Check page load performance after changes

### Phase 6: CEO Review & Launch 🔒 LOCKED
**Worker:** [[Org Chart/CMO/IDENTITY]] + [[Org Chart/CEO/IDENTITY]]  
**Reviewer:** [[Org Chart/CEO/IDENTITY]]  
**Status:** Locked — All previous phases must be reviewed first

**Review Criteria:**
- All phases completed and approved
- CMO verifies strategy implementation
- CEO verifies business goals met
- FOUNDER approves launch

**Phase 6 Checklist:**
- [ ] CMO reviews all changes against strategy doc
- [ ] CEO reviews implementation
- [ ] @FOUNDER approval for launch
- [ ] Deploy to production
- [ ] Monitor conversion metrics
## 📝 Work Log

### 2026-02-07 [[Org Chart/CTO/IDENTITY]] — PHASE 3 REJECTED
**Lock acquired:** 2026-02-07T09:56:00Z  
**Reviewed:** Phase 3: Pricing Structure Updates  
**Status:** ❌ REJECTED — Critical pricing mismatches

**Issues Found:**

| Issue | Severity | Details |
|-------|----------|---------|
| Add-on ID Mismatch | 🔴 Critical | Pricing page uses `engine-unlock`, checkout uses `scheduling`/`continuity` |
| Wrong Pricing — Social | 🔴 Critical | Pricing page: $39/mo, Checkout: $49/mo |
| Wrong Pricing — Content | 🔴 Critical | Pricing page: $149/mo, Checkout: $99/mo |
| Phantom Add-ons | 🟡 High | Checkout has `scheduling` ($39) and `continuity` ($59) not on pricing page |
| Missing Add-on | 🟡 High | `engine-unlock` ($49) missing from checkout API |

**Impact:**
- Customers charged incorrect amounts
- Selected add-ons won't match purchase
- Revenue loss / customer disputes likely

**Required Changes in `src/pages/api/checkout/session.ts`:**

```typescript
// REPLACE ADDON_PRICES with:
const ADDON_PRICES: Record<string, { monthly: number; name: string }> = {
  'engine-unlock': { monthly: 4900, name: 'Engine Unlock' },
  'interactions': { monthly: 7900, name: 'Interaction Boost' },
  'social': { monthly: 3900, name: 'Extra Social Platform' },
  'content': { monthly: 14900, name: 'Content Boost' },
  'support': { monthly: 9900, name: 'Priority Support' },
};
```

**Setup fees verified ✅:**
- Signal: $199, Satellite: $299, Pink Beam: $399, Full VALIS: $499
- Properly implemented as one-time payment + recurring subscription

**Phase Review Updated:**
- Status: `rejected`
- Submitted: 2026-02-07T09:56:00Z

**Lock released:** 2026-02-07T09:58:00Z  
**Return to:** [[Org Chart/ENG-BE/IDENTITY]] for fixes

---

### 2026-02-07 [[Org Chart/ENG-FE/IDENTITY]] — PHASE 2 COMPLETE
**Lock acquired:** 2026-02-07T09:31:00Z  
**Task:** [[Tasks/TASK-001-pricing-marketing-implementation]]  
**Intent:** Complete Phase 2 Content Expansion

**Completed:**
- [x] FAQ Section expanded with 4 new questions:
  - "How is this different from a chatbot?" — Receptionist analogy explaining action vs just answers
  - "What if the AI gets something wrong?" — Training process + monitoring explanation
  - "Can I change my tier later?" — Upgrade/downgrade flexibility with no penalties
  - "Do I need technical skills?" — Emphasizes no-code, hands-off approach
- [x] Added FAQSection to home page (index.astro) — now displays after Testimonials
- [x] Verified EnginesPreview already has benefit-focused copy with icons
- [x] Verified Testimonials section already exists with "REAL RESULTS" badge
- [x] Verified meta descriptions already updated on home and pricing pages
- [x] Build verified — npm run build successful

**Progress:**
- [ ] Phase 2 awaiting CMO review
- [ ] Phase 3: Pricing Structure Updates (requires ENG-BE for Stripe integration)
- [ ] Phase 4: VALIS Section (already appears complete from prior work)
- [ ] Phase 5: Final Polish
- [ ] Phase 6: CEO Review & Launch

**Blockers:**
- None

**Notes:**
Most Phase 2 items were already in place from previous work. Primary contribution was adding the 4 missing FAQ items and ensuring FAQSection renders on the home page. FAQ now has 10 total questions covering all major customer concerns.

**Files Modified:**
- `~/code/pinkbeambot-marketing/src/components/FAQSection.astro` — Added 4 new FAQ items
- `~/code/pinkbeambot-marketing/src/pages/index.astro` — Added FAQSection import and component

**Ready for review by:** [[Org Chart/CMO/IDENTITY]]

**Handoff:**
- Lock released: 2026-02-07T09:38:00Z
- Cron trigger: Timeout (job still ran in background)
- Manual trigger available: `cron run pbb-cmo-shift`

---

### 2026-02-07 [[Org Chart/CMO/IDENTITY]] — PHASE 1 APPROVED
**Lock acquired:** 2026-02-07T09:17:00Z  
**Reviewed:** Phase 1: Quick Wins — Copy Updates  
**Status:** ✅ APPROVED  
**Quality:** Meets all standards from PRICING-MARKETING-STRATEGY-2026-02

**Verified:**
- Hero copy: "Your Website Works While You Sleep" headline ✅
- Subhead: Clear value prop with "No coding required" ✅
- CTAs: "See What It Can Do" + "View Plans" ✅
- How It Works: 4 steps including new 4th step ✅
- Pricing descriptions: All 5 tiers match strategy doc ✅
- Trust signals: All 3 badges present in hero ✅
- Meta description: Keywords and value prop included ✅

**Notes:**
- Brand voice is consistent (direct, benefit-focused)
- Visual design matches existing system
- Ready for Phase 2: Content Expansion

**Lock released:** 2026-02-07T09:22:00Z  
**Next:** [[Org Chart/ENG-FE/IDENTITY]] to begin Phase 2

**⚠️ Handoff Failed:** Could not trigger [[Org Chart/ENG-FE/IDENTITY]] after 3 attempts  
**Manual intervention required:** Run `cron run pbb-eng-fe-shift`

---

### 2026-02-07 [[Org Chart/CEO/IDENTITY]]
**Task Activated by CEO**
- Lock acquired and task activated
- Status: todo → in-progress
- is_active: true
- current_worker: [[Org Chart/ENG-FE/IDENTITY]]
- Starting at: 2026-02-07T08:47:00Z
- **Phase 1 assigned:** Quick Wins — Copy Updates
- Triggering ENG-FE to begin work

### 2026-02-07 [[Org Chart/ENG-FE/IDENTITY]]
**Lock acquired:** 2026-02-07T09:02:00Z
**Task:** [[Tasks/TASK-001-pricing-marketing-implementation]]
**Intent:** Complete Phase 1 Quick Wins — Copy Updates

**Completed:**
- [x] Hero copy already updated (confirmed "Your Website Works While You Sleep" headline, new subhead, CTAs: "See What It Can Do" and "View Plans")
- [x] Updated How It Works section — added 4th step "It Keeeps Getting Smarter" with Sparkles icon
- [x] Updated pricing tier descriptions in PricingSection:
  - Signal: "For solo founders & side projects"
  - Satellite: "For local businesses & creators"
  - Pink Beam: "For scaling companies"
  - Full VALIS: "For companies ready to automate"
  - Enterprise: "For teams with custom needs"
- [x] Added trust signals to home page (HeroSection):
  - 99.9% Uptime SLA (was already present)
  - 30-Day Money-Back Guarantee (new)
  - Human Support When You Need It (new)

**Verified Existing:**
- Meta description already updated in index.astro
- VALIS section already has updated copy with bullet list and closing line
- EnginesPreview already uses benefit-focused copy

**Progress:**
- [ ] Phase 2: Content Expansion (FAQ expansion, testimonials section)
- [ ] Phase 3: Pricing Structure Updates (setup fees, add-ons — requires ENG-BE)
- [ ] Phase 4: VALIS Section already complete
- [ ] Phase 5: Final Polish sitewide CTAs

**Blockers:**
- None

**Notes:**
Phase 1 is functionally complete. Several items were already implemented in previous commits. Next phase (Phase 2: Content Expansion) involves FAQ additions and testimonials section — recommended to hand off to next ENG-FE shift or continue with Phase 2.

**Lock released:** 2026-02-07T09:04:00Z
**Duration:** ~2 minutes
**Next:** Phase 2 (Content Expansion) or hand off to ENG-BE for Phase 3 (pricing structure)

---

### 2026-02-07 [[Org Chart/CMO/IDENTITY]] — PHASE 2 APPROVED
**Lock acquired:** 2026-02-07T09:50:00Z  
**Reviewed:** Phase 2: Content Expansion  
**Status:** ✅ APPROVED  
**Quality:** Meets all standards from PRICING-MARKETING-STRATEGY-2026-02

**Verified:**
- Engines Preview: "What Can Your Website Do For You?" headline ✅
- 6 capability cards with benefit-focused copy and icons ✅
- FAQ expanded to 10 questions (4 new: chatbot diff, AI accuracy, tier changes, technical skills) ✅
- Testimonials section: 3 quotes + metrics, "REAL RESULTS" badge ✅
- Meta descriptions: Keywords + value prop + pricing anchor ✅

**Quality Notes:**
- Brand voice consistent (direct, no mystical fluff)
- Copy addresses real customer objections
- Design matches glassmorphism system
- All checklist items complete

**Phase 3 Unlocked:**
- Phase 3 status: `in_progress`
- Workers: [[Org Chart/ENG-BE/IDENTITY]] + [[Org Chart/ENG-FE/IDENTITY]]
- Reviewer: [[Org Chart/CTO/IDENTITY]]
- Focus: Setup fees ($199-$499), add-on restructuring, Stripe integration

**Handoff:**
- Triggering ENG-BE for backend Stripe work: `cron run pbb-eng-be-shift` — ⏱️ Gateway timeout (job still ran)
- Triggering ENG-FE for frontend pricing display: `cron run pbb-eng-fe-shift` — ⏱️ Gateway timeout (job still ran)
- Lock released: 2026-02-07T09:58:00Z
- **Manual trigger available if needed:** Run `cron run pbb-eng-be-shift` and `cron run pbb-eng-fe-shift`

---

## 🚧 Blockers

**Current blockers:**
- None

**Potential blockers:**
- Requires FOUNDER approval for setup fees (business decision)
- Need real testimonials for final section (can use placeholders initially)

---

## 💬 Decisions

| Date | Decision | Made By | Rationale |
|------|----------|---------|-----------|
| 2026-02-07 | Task created from strategy doc | CMO | Strategy approved, ready for implementation |

---

## 🔗 Related

- **Strategy Source:** [[Notes/PRICING-MARKETING-STRATEGY-2026-02]]
- **Current Pricing:** [[Intel Engines]]
- **Code Location:** `~/code/pinkbeambot-marketing`
- **Target Metrics:** See strategy doc for KPIs

---

## 🏁 Completion Notes

*To be filled when task enters review*

**Summary:**

**Metrics:**
- Actual hours:
- Estimated hours: 24

**Results:**
- Home page conversion:
- Pricing page conversion:

**Lessons Learned:**

**Follow-up Items:**
- Monitor metrics for 30 days
- A/B test hero variants
- Gather real testimonials
