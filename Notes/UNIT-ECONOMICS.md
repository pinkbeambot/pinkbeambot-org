# UNIT ECONOMICS

**Does this business actually work?**

---

## 💰 Revenue Model

### Pricing Tiers

| Tier | Employees Included | Price/Month | Target Customer |
|------|-------------------|-------------|-----------------|
| **Starter** | 1 employee | $500 | Solo founders, early testing |
| **Growth** | 3 employees | $1,500 | Seed-stage startups |
| **Scale** | 5 employees | $2,500 | Series A companies |
| **Enterprise** | 10+ employees | $5,000+ | Series B+ / Custom |

### Average Revenue Per User (ARPU)

**Conservative estimate:** $1,500/month ($18K ARR)  
**Optimistic estimate:** $2,000/month ($24K ARR)

**Blended ARPU (early):** $1,200/month  
**Blended ARPU (mature):** $1,800/month

---

## 📉 Cost of Goods Sold (COGS)

### Per-Employee Costs

| Cost Category | Monthly | Notes |
|---------------|---------|-------|
| **AI API (Claude/OpenAI)** | $80-150 | Depends on usage intensity |
| **OpenClaw/Orchestration** | $20-50 | Platform fees |
| **Compute/Hosting** | $30-60 | Workers, DB, queue processing |
| **Data Storage** | $10-20 | Vector DB, logs, memory |
| **Integrations** | $20-40 | API calls to Slack, HubSpot, etc. |
| **Monitoring/Observability** | $10-20 | Error tracking, analytics |
| **Total Per Employee** | **$170-340** | **Target: <$200 at scale** |

### Gross Margin by Package

| Package | Revenue | COGS (3x avg) | Gross Profit | Gross Margin |
|---------|---------|---------------|--------------|--------------|
| Starter (1 emp) | $500 | $200 | $300 | 60% |
| Growth (3 emp) | $1,500 | $600 | $900 | 60% |
| Scale (5 emp) | $2,500 | $1,000 | $1,500 | 60% |
| Enterprise (10 emp) | $5,000 | $2,000 | $3,000 | 60% |

**Target Gross Margin: 60-70%**

---

## 📊 Customer Economics

### Customer Acquisition Cost (CAC)

| Channel | Est. CAC | % of Customers |
|---------|----------|----------------|
| Organic/Twitter | $500 | 30% |
| Referrals | $1,000 | 25% |
| Product Hunt | $800 | 15% |
| Paid Ads (LinkedIn) | $2,500 | 20% |
| Events/Partnerships | $3,000 | 10% |

**Blended CAC (early):** $1,500  
**Blended CAC (mature):** $1,200

### Lifetime Value (LTV)

**Assumptions:**
- Average contract: $1,500/month
- Gross margin: 60%
- Monthly churn: 5% (early) → 3% (mature)
- Average lifetime: 20 months (early) → 33 months (mature)

**Calculation:**
```
LTV = (ARPU × Gross Margin) / Monthly Churn Rate

Early:  ($1,500 × 0.60) / 0.05 = $18,000
Mature: ($2,000 × 0.70) / 0.03 = $46,667
```

**Conservative LTV: $20,000**  
**Optimistic LTV: $40,000**

### LTV:CAC Ratio

| Scenario | LTV | CAC | LTV:CAC | Health |
|----------|-----|-----|---------|--------|
| Conservative | $18K | $1.5K | 12:1 | ✅ Excellent |
| Base Case | $25K | $1.2K | 21:1 | ✅ Excellent |
| Optimistic | $40K | $1K | 40:1 | ✅ Excellent |

**Target: >3:1 (we're well above)**

---

## ⏱️ Payback Period

**CAC:** $1,500  
**Monthly gross profit per customer:** $900  
**Payback period:** $1,500 ÷ $900 = **1.7 months**

**This is exceptional.** Healthy SaaS is 12-18 months. We're <2 months.

---

## 📈 Operating Expenses (OpEx)

### Fixed Costs (Monthly)

| Category | Early (1-10 customers) | Growth (50 customers) | Scale (200 customers) |
|----------|------------------------|----------------------|----------------------|
| **Founder salary** | $0 (bootstrapped) | $8,000 | $15,000 |
| **Contractors** | $3,000 | $10,000 | $25,000 |
| **Software/tools** | $500 | $2,000 | $5,000 |
| **Office/infra** | $0 (remote) | $1,000 | $3,000 |
| **Legal/accounting** | $500 | $2,000 | $5,000 |
| **Marketing** | $1,000 | $5,000 | $15,000 |
| **Total Fixed** | **$5,000** | **$28,000** | **$68,000** |

### Break-Even Analysis

**At $1,500 ARPU and 60% gross margin:**
- Contribution margin per customer: $900/month

**Break-even customers:**
- Early: $5,000 ÷ $900 = **6 customers**
- Growth: $28,000 ÷ $900 = **32 customers**
- Scale: $68,000 ÷ $900 = **76 customers**

---

## 🎯 Path to Profitability

### Scenario 1: Bootstrapped (No Funding)

| Milestone | Customers | MRR | Monthly Profit | Timeline |
|-----------|-----------|-----|----------------|----------|
| Ramen profitable | 6 | $9,000 | $400 | Month 4 |
| Founder salary | 15 | $22,500 | $8,500 | Month 8 |
| Hire #1 | 35 | $52,500 | $23,500 | Month 12 |
| Comfortable | 50 | $75,000 | $37,000 | Month 18 |

### Scenario 2: Seed Funded ($1M)

| Milestone | Customers | MRR | Burn Rate | Runway |
|-----------|-----------|-----|-----------|--------|
| Start | 0 | $0 | $15K/mo | 66 mo |
| Product-market fit | 20 | $30K | $20K/mo | 50 mo |
| Growth mode | 50 | $75K | $35K/mo | 28 mo |
| Break-even | 80 | $120K | $40K/mo | Profitable |

---

## 📊 Key Metrics Dashboard

### Track Weekly
- **New customers** (this week)
- **Churned customers** (this week)
- **Net revenue retention** (expansion - contraction)
- **Gross margin %** (actual, not target)

### Track Monthly
- **CAC** (by channel)
- **LTV** (rolling 12-month)
- **LTV:CAC ratio**
- **Payback period**
- **COGS per employee** (are we getting more efficient?)

### Track Quarterly
- **Logo churn %**
- **Revenue churn %**
- **Expansion revenue %**
- **Gross margin trend**
- **Operating leverage** (revenue growth % vs. cost growth %)

---

## ⚠️ Risks to Unit Economics

### Risk 1: AI API Costs Increase
**Impact:** COGS could double if OpenAI/Anthropic raise prices  
**Mitigation:** 
- Multi-model strategy (use cheaper models where possible)
- Caching layer (don't re-process same data)
- Pass-through pricing for heavy users

### Risk 2: Customers Want Unlimited Usage
**Impact:** COGS becomes unpredictable  
**Mitigation:**
- Usage tiers ("up to 1,000 tasks/month")
- Overage pricing
- "Fair use" policies

### Risk 3: Churn Higher Than Expected
**Impact:** LTV collapses, unit economics break  
**Mitigation:**
- Annual contracts (improve retention)
- Usage-based pricing (harder to cancel if integrated)
- Customer success investment

### Risk 4: Pricing Pressure from Competitors
**Impact:** ARPU declines  
**Mitigation:**
- Differentiation on quality (not just price)
- Enterprise features (less price-sensitive)
- Outcome-based pricing ("pay per meeting booked")

---

## 🎯 Targets

| Metric | Month 6 | Month 12 | Month 18 |
|--------|---------|----------|----------|
| **Customers** | 20 | 50 | 100 |
| **MRR** | $30K | $75K | $150K |
| **ARPU** | $1,500 | $1,500 | $1,500 |
| **Gross Margin** | 55% | 60% | 65% |
| **Churn (monthly)** | 8% | 5% | 3% |
| **CAC** | $2,000 | $1,500 | $1,200 |
| **LTV** | $15K | $25K | $40K |
| **LTV:CAC** | 7.5:1 | 16:1 | 33:1 |
| **Payback** | 2.5 mo | 1.7 mo | 1.3 mo |

---

## 💡 Key Insights

1. **Unit economics are strong.** LTV:CAC of 10+:1 is excellent. Payback of <2 months is exceptional.

2. **The leverage is in automation.** We're not hiring humans to serve customers. We're building software that serves them. Margins improve with scale.

3. **Churn is the killer metric.** If monthly churn is >10%, LTV:CAC drops below 5:1. Focus on retention.

4. **Expansion revenue is free money.** If customers add employees over time, LTV doubles without CAC increasing.

5. **Enterprise is the margin story.** At $5K/month with 70% margins, one enterprise customer = 3 growth customers.

---

*Last Updated: 2026-02-07*  
*Next Review: Monthly (with actuals)*
