---
id: TASK-001
title: Implement Pricing & Marketing Strategy Updates
status: todo
priority: P0
created_at: 2026-02-07T00:20:00Z
created_by: "[[Org Chart/CMO/IDENTITY]]"
started_at: ""
completed_at: ""
verified_at: ""
assigned_to: "[[Org Chart/CMO/IDENTITY]]"
collaborators:
  - "[[Org Chart/ENG-FE/IDENTITY]]"
  - "[[Org Chart/ENG-BE/IDENTITY]]"
current_worker: ""
estimated_hours: 24
actual_hours: 0
dependencies: []
blocks: []
is_active: false
verified_by: ""
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

### Phase 1: Quick Wins — Copy Updates (ENG-FE)
- [ ] Update hero copy on home page
  - [ ] Change from "The Web is Waking Up" to "Your Website Works While You Sleep"
  - [ ] Add subhead: "AI-powered websites that answer customer questions, book appointments, and generate leads — automatically. No coding required."
  - [ ] Update CTAs to "See What It Can Do" and "View Plans"
- [ ] Add "How It Works" section to home page (4-step process)
- [ ] Update pricing tier descriptions in [[Intel Engines]]
  - [ ] Signal: "For solo founders & side projects"
  - [ ] Satellite: "For local businesses & creators"
  - [ ] Pink Beam: "For scaling companies"
  - [ ] Full VALIS: "For companies ready to automate"
  - [ ] Enterprise: "For teams with custom needs"
- [ ] Add trust signals to home page
  - [ ] "99.9% Uptime SLA" badge
  - [ ] "30-Day Money-Back Guarantee" badge
  - [ ] "Human Support When You Need It" badge

### Phase 2: Content Expansion (ENG-FE)
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

### Phase 3: Pricing Structure Updates (ENG-BE + ENG-FE)
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

### Phase 4: VALIS Section Rewrite (ENG-FE)
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

### Phase 5: Final Polish (ENG-FE)
- [ ] Update CTA buttons sitewide
  - [ ] "Explore Engines" → "See What It Can Do"
  - [ ] "See Pricing" → "View Plans"
  - [ ] Ensure consistent CTAs
- [ ] Add "Trusted By" section with customer count
- [ ] Ensure all changes are mobile-responsive
- [ ] Verify all links work
- [ ] Check page load performance after changes

### Phase 6: CEO Review & Launch
- [ ] CMO reviews all changes against strategy doc
- [ ] CEO reviews implementation
- [ ] @FOUNDER approval for launch
- [ ] Deploy to production
- [ ] Monitor conversion metrics

---

## 📝 Work Log

*Work sessions documented here*

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
