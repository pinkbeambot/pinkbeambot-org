# RISK REGISTER

**What could kill us and how we prevent it**

---

## 🔴 CRITICAL RISKS (Kill the company)

### RISK-001: AI Quality Degrades
**Probability:** Medium  
**Impact:** Critical  
**Status:** 🟡 Monitoring

**Description:**
Claude/OpenAI model updates reduce quality, hallucinations increase, or costs spike. Our core product depends on AI quality.

**Early Warning Signs:**
- Customer complaints about brief quality
- Error rates increasing
- Model deprecation announcements

**Mitigation:**
- Multi-model strategy (Claude + GPT-4 + open source)
- Human-in-the-loop for edge cases
- A/B testing model versions
- Prompt versioning and rollback

**Contingency:**
- Switch to alternative models
- Increase human review layer
- Temporarily pause new signups while fixing

**Owner:** CTO  
**Review:** Weekly

---

### RISK-002: OpenClaw Platform Fails
**Probability:** Medium  
**Impact:** Critical  
**Status:** 🟡 Monitoring

**Description:**
OpenClaw (our orchestration layer) becomes unstable, changes API radically, or shuts down. We can't operate without it.

**Early Warning Signs:**
- OpenClaw downtime
- API breaking changes
- Funding/runway issues at OpenClaw

**Mitigation:**
- Build abstraction layer (don't hardcode OpenClaw)
- Keep alternative orchestrators evaluated (AutoGPT, LangChain)
- Maintain fallback manual processes

**Contingency:**
- 2-week sprint to migrate to alternative
- Hybrid approach (OpenClaw + custom workers)
- Long-term: Build own orchestration

**Owner:** CTO  
**Review:** Monthly

---

### RISK-003: Unit Economics Don't Work
**Probability:** Medium  
**Impact:** Critical  
**Status:** 🟢 Monitoring

**Description:**
Cost per customer exceeds revenue. AI API costs, compute, or integration fees make us unprofitable.

**Early Warning Signs:**
- Gross margin < 50%
- COGS growing faster than revenue
- Customer usage 10x higher than expected

**Mitigation:**
- Aggressive caching
- Usage limits and fair use policies
- Price optimization testing
- Efficiency improvements (cheaper models where possible)

**Contingency:**
- Increase prices (existing customers grandfathered)
- Usage-based pricing tiers
- Reduce service levels
- Pivot to higher-price market segment

**Owner:** CEO  
**Review:** Weekly

---

### RISK-004: Customers Don't Want "Employees"
**Probability:** Medium  
**Impact:** Critical  
**Status:** 🟡 Monitoring

**Description:**
Mental model of "AI employees" doesn't resonate. Customers prefer "automation" or "workflows" or just don't get it.

**Early Warning Signs:**
- High churn in first month
- "This isn't what I expected" feedback
- Low engagement with product
- Difficulty explaining to prospects

**Mitigation:**
- Customer interviews (validate positioning NOW)
- A/B test messaging
- Pivot to "automation" if needed
- Focus on outcomes, not metaphor

**Contingency:**
- Rebrand as "AI Automation Platform"
- Emphasize workflows/triggers
- Deprecate "employee" language
- Maintain tech, change positioning

**Owner:** CEO  
**Review:** After 10 customer interviews

---

## 🟠 HIGH RISKS (Major setback)

### RISK-005: Big Tech Builds This
**Probability:** High  **Impact:** High  
**Status:** 🟢 Accepting

**Description:**
Microsoft (Copilot), Google (Duet), or Salesforce builds native AI employees. They have distribution, trust, and resources.

**Timeline:** 12-24 months

**Mitigation:**
- Move fast (12-month head start)
- Specialize deeply (specific roles, not general)
- Build brand in niche
- Cross-platform (work with any tool, not just Microsoft)
- Integrate with them (be complementary, not competitive)

**Contingency:**
- Acquisition target (sell to them)
- Niche down further (only serve specific industry)
- Pivot to infrastructure layer (power their employees)

**Owner:** CEO  
**Review:** Quarterly

---

### RISK-006: Customer Acquisition Fails
**Probability:** Medium  
**Impact:** High  
**Status:** 🟢 Monitoring

**Description:**
Can't acquire customers at viable CAC. Channels don't work, product-market fit unclear, or competition too intense.

**Early Warning Signs:**
- CAC > $3,000
- Conversion rate < 1%
- No organic growth
- High churn (> 10% monthly)

**Mitigation:**
- Test 5+ acquisition channels
- Optimize funnel ruthlessly
- Lower price to improve conversion
- Focus on referrals/virality

**Contingency:**
- Pivot use case (different employee type)
- Pivot market segment (enterprise vs. SMB)
- Pivot to partnership/channel model
- Wind down if unsalvageable

**Owner:** CMO  
**Review:** Weekly

---

### RISK-007: AI Makes Serious Mistake
**Probability:** Medium  
**Impact:** High  
**Status:** 🟡 Monitoring

**Description:**
AI employee causes real harm: wrong financial advice, misspoken on behalf of customer, data breach, etc.

**Examples:**
- Researcher includes false info in brief, customer acts on it
- SDR sends offensive email to prospect
- Support agent gives dangerous advice

**Mitigation:**
- Confidence thresholds (don't act if <80% sure)
- Human approval for external-facing actions
- Error handling and escalation
- Insurance (E&O, cyber liability)
- Clear disclaimers

**Contingency:**
- Immediate incident response
- Customer communication plan
- Legal review
- Improve safeguards
- Possible feature removal

**Owner:** CEO/CTO  
**Review:** As needed

---

### RISK-008: Churn is Too High
**Probability:** Medium  
**Impact:** High  
**Status:** 🟢 Monitoring

**Description:**
Customers churn faster than we can acquire. LTV:CAC ratio drops below 3:1.

**Early Warning Signs:**
- Monthly churn > 8%
- "Didn't see value" exit interviews
- Low weekly active usage
- No expansion revenue

**Mitigation:**
- Customer success from Day 1
- Usage-based triggers (intervene if inactive)
- Expansion features (add more employees)
- Annual contracts (improve retention)

**Contingency:**
- Focus on narrower ICP (only customers who love us)
- Increase prices (filter for serious customers)
- Add mandatory onboarding
- Pivot product if fundamental issue

**Owner:** CEO  
**Review:** Weekly

---

## 🟡 MEDIUM RISKS (Manageable issues)

### RISK-009: Integration Partners Change APIs
**Probability:** Medium  
**Impact:** Medium  
**Status:** 🟢 Monitoring

**Description:**
Slack, HubSpot, etc. change APIs, breaking our integrations.

**Mitigation:**
- API versioning abstraction
- Monitoring for deprecation notices
- Multiple integration options (don't rely on one)

**Owner:** CTO  
**Review:** Monthly

---

### RISK-010: Key Person Dependency
**Probability:** Low  
**Impact:** Medium  
**Status:** 🟢 Monitoring

**Description:**
Solo founder gets sick, burned out, or leaves. Company stalls.

**Mitigation:**
- Document everything (runbooks, decisions)
- Build AI team to offload work
- Advisory board for guidance
- Maintain health/sanity

**Owner:** FOUNDER  
**Review:** Quarterly

---

### RISK-011: Data Privacy Incident
**Probability:** Low  
**Impact:** Medium  
**Status:** 🟢 Monitoring

**Description:**
Customer data leaked, exposed, or misused.

**Mitigation:**
- Encryption at rest and in transit
- Access controls
- Regular security audits
- SOC 2 compliance (Month 6)

**Owner:** CTO  
**Review:** Quarterly

---

### RISK-012: Funding Runs Out (if raising)
**Probability:** Low  
**Impact:** Medium  
**Status:** 🟢 N/A (bootstrapped)

**Description:**
If we raise, runway runs out before profitability.

**Mitigation:**
- 18-month runway minimum
- Monthly burn tracking
- Clear path to profitability
- Revenue milestones before spending

**Owner:** CEO  
**Review:** Monthly

---

## 📊 Risk Matrix Summary

| Risk | Probability | Impact | Priority | Status |
|------|-------------|--------|----------|--------|
| AI Quality Degrades | Medium | Critical | 🔴 P0 | Monitoring |
| OpenClaw Fails | Medium | Critical | 🔴 P0 | Monitoring |
| Unit Economics Fail | Medium | Critical | 🔴 P0 | Monitoring |
| Positioning Rejected | Medium | Critical | 🔴 P0 | Monitoring |
| Big Tech Competition | High | High | 🟠 P1 | Accepting |
| Customer Acquisition Fails | Medium | High | 🟠 P1 | Monitoring |
| AI Serious Mistake | Medium | High | 🟠 P1 | Monitoring |
| High Churn | Medium | High | 🟠 P1 | Monitoring |
| API Changes | Medium | Medium | 🟡 P2 | Monitoring |
| Key Person Risk | Low | Medium | 🟡 P2 | Monitoring |
| Privacy Incident | Low | Medium | 🟡 P2 | Monitoring |
| Funding Runs Out | Low | Medium | 🟡 P2 | N/A |

---

## 🛡️ Risk Mitigation Budget

**Time allocation:**
- 40% — Build core product
- 30% — Customer acquisition
- 20% — Risk mitigation (abstraction, monitoring, insurance)
- 10% — Buffer

**Financial reserves:**
- 6-month emergency fund
- Insurance (E&O, cyber liability)
- Legal retainer

---

## 📅 Review Schedule

**Weekly:**
- Unit economics (COGS, margins)
- Customer feedback (quality complaints)
- System health (errors, uptime)

**Monthly:**
- Competitive landscape
- Technology dependencies
- Churn analysis

**Quarterly:**
- Strategic risks (big tech, market shifts)
- Insurance and legal
- Long-term positioning

---

*Last Updated: 2026-02-07*  
*Next Review: Weekly for P0 risks, Monthly for all*
