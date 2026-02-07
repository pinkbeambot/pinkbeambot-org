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
current_worker: "[[Org Chart/ENG-FE/IDENTITY]]"
next_worker: "[[Org Chart/ENG-FE/IDENTITY]]"
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
    status: todo
    submitted_at: ""
    approved_at: ""
  - phase: "Phase 3: Pricing Structure Updates"
    worker: "[[Org Chart/ENG-BE/IDENTITY]] + [[Org Chart/ENG-FE/IDENTITY]]"
    reviewer: "[[Org Chart/CTO/IDENTITY]]"
    status: todo
    submitted_at: ""
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

### Phase 2: Content Expansion (ENG-FE) 🔒 LOCKED
**Worker:** [[Org Chart/ENG-FE/IDENTITY]]  
**Reviewer:** [[Org Chart/CMO/IDENTITY]]  
**Status:** Locked — Phase 1 must be reviewed first

**Review Criteria:**
- FAQ answers are clear and helpful
- Testimonials section is well-designed
- Meta descriptions include target keywords
- Content aligns with brand voice

**Phase 2 Checklist:**
- [ ] Rewrite engines preview section on home page
  - [ ] Lead with problems solved, not engine names
  - [ ] Add icons for each capability
  - [ ] Use benefit-focused copy (see strategy doc for examples)
- [ ] Expand FAQ section
  - [ ] "How is this different from a chatbot?"
  - [ ] "What if the AI gets something wrong?"
  - [ ] "Can I change my tier later?"
  - [ ] "Do I need technical skills?"
  - [ ] "How long does setup take?"
- [ ] Add testimonials section to home page
  - [ ] Create placeholder section (content pending real testimonials)
  - [ ] Design quote card component
- [ ] Update all meta descriptions
  - [ ] Home page: "AI-powered websites that answer customer questions and book appointments automatically. Perfect for small businesses. See plans starting at $29/mo."
  - [ ] Pricing page: Lead with value + keyword
  - [ ] All engine pages: Update per strategy

### Phase 3: Pricing Structure Updates (ENG-BE + ENG-FE) 🔒 LOCKED
**Worker:** [[Org Chart/ENG-BE/IDENTITY]] + [[Org Chart/ENG-FE/IDENTITY]]  
**Reviewer:** [[Org Chart/CTO/IDENTITY]]  
**Status:** Locked — Phases 1-2 must be reviewed first

**Review Criteria:**
- Setup fees work correctly in Stripe
- Add-on pricing is clear to users
- No breaking changes to existing customers
- Code passes technical review

**Phase 3 Checklist:**
- [ ] Add setup fees to pricing configuration
  - [ ] Signal: $199
  - [ ] Satellite: $299
  - [ ] Pink Beam: $399
  - [ ] Full VALIS: $499
  - [ ] Enterprise: "Custom"
- [ ] Update pricing display to show setup fees
  - [ ] Show "+$XXX setup" next to monthly price
  - [ ] Add tooltip explaining one-time fee
- [ ] Restructure add-ons
  - [ ] Remove confusing add-ons (e.g., "Add Scheduling Engine" when Satellite includes it)
  - [ ] Add new add-on structure:
    - [ ] Engine Unlock: $49/mo
    - [ ] Interaction Boost: $79/mo
    - [ ] Extra Social Platform: $39/mo
    - [ ] Priority Support: $99/mo
    - [ ] Content Boost: $149/mo
  - [ ] Add one-time add-ons:
    - [ ] Migration Service: $299
    - [ ] Custom Domain Setup: $49
    - [ ] Content Import: $199
- [ ] Update Stripe products/prices to match new structure

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
