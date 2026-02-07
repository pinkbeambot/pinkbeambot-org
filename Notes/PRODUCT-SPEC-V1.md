# PRODUCT SPEC V1

**What we're building (technical requirements)**

---

## 🎯 Product Overview

**Product:** Pink Beam — AI Employee Platform  
**Version:** 1.0 (MVP)  
**Focus:** Researcher Employee only  
**Timeline:** 4 weeks to production

---

## 🏗️ System Architecture

### High-Level Flow

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Sources   │────▶│  Ingestion   │────▶│  Vector DB  │
│             │     │   Pipeline   │     │   (Memory)  │
└─────────────┘     └──────────────┘     └─────────────┘
                                                 │
                                                 ▼
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│  Customer   │◀────│   Delivery   │◀────│  Synthesis  │
│  (Slack/    │     │   Engine     │     │   Engine    │
│   Email)    │     │              │     │  (Claude)   │
└─────────────┘     └──────────────┘     └─────────────┘
       │
       ▼
┌─────────────┐
│  Feedback   │────▶ Improves future synthesis
│  (👍/👎)    │
└─────────────┘
```

### Components

#### 1. Source Connectors
**Purpose:** Pull data from external sources  
**Technology:** Python, RSS feeds, APIs, web scraping

**Supported Sources (V1):**
- RSS feeds (TechCrunch, VentureBeat, etc.)
- Twitter/X lists (via API)
- News APIs (NewsAPI, GDELT)
- Company websites (monitoring for changes)
- Subreddit monitoring

**Data Format:**
```json
{
  "source_id": "techcrunch_rss",
  "source_type": "rss",
  "content": "...",
  "title": "...",
  "url": "...",
  "published_at": "2026-02-07T10:00:00Z",
  "ingested_at": "2026-02-07T10:05:00Z"
}
```

#### 2. Ingestion Pipeline
**Purpose:** Normalize and store raw content  
**Technology:** OpenClaw cron jobs, PostgreSQL, Redis queue

**Pipeline Steps:**
1. **Fetch** — Pull from sources every 15 minutes
2. **Deduplicate** — Hash content, skip if seen
3. **Classify** — Tag by category (funding, product, hiring, etc.)
4. **Extract** — Pull key entities (companies, people, amounts)
5. **Store** — Save to vector DB with metadata

**Tech Stack:**
- Job queue: Redis + Bull
- Vector DB: Pinecone or Weaviate
- Metadata: PostgreSQL
- Embedding: OpenAI text-embedding-3-small

#### 3. Synthesis Engine
**Purpose:** Turn raw data into actionable intelligence  
**Technology:** Claude 3.5 Sonnet via API

**Process:**
1. Query vector DB for last 7 days of content
2. Cluster by topic/theme
3. Generate synthesis using Claude
4. Format as structured brief

**Prompt Template:**
```
You are a senior market intelligence analyst. Review the following 
articles from the past week and create an executive brief.

ARTICLES:
{articles}

CUSTOMER CONTEXT:
- Industry: {customer_industry}
- Competitors: {customer_competitors}
- Focus Areas: {customer_priorities}

OUTPUT FORMAT:
## Executive Summary
2-3 sentences on the most important development

## Competitor Moves
- Company: What they did, why it matters

## Industry Trends
- Trend name: Description and implications

## Opportunities
- 3 specific, actionable opportunities for the customer

## Key Readings
- 5 must-read articles with one-line summaries

STYLE:
- Professional but punchy
- Bullet points over paragraphs
- Specific examples, not generalities
- "So what" for every point
```

#### 4. Delivery Engine
**Purpose:** Send output to customer's preferred channels  
**Technology:** OpenClaw message tool, SendGrid, Slack API

**Supported Channels:**
- Slack (dm or channel)
- Email (HTML + plain text)
- Notion (page creation)
- Web dashboard

**Delivery Schedule:**
- Weekly: Every Monday 9am (customer timezone)
- Real-time: Breaking news alerts (configurable)

#### 5. Feedback Loop
**Purpose:** Learn from customer feedback to improve  
**Technology:** Simple 👍/👎 buttons, stored in DB

**Feedback Types:**
- Brief-level: Overall rating
- Item-level: Rate individual insights
- Correction: "This was wrong because..."

**Usage:**
- Adjust future synthesis prompts
- Re-rank sources by quality
- Improve relevance scoring

---

## 📊 Data Model

### Customer
```typescript
interface Customer {
  id: string;
  email: string;
  company_name: string;
  industry: string;
  stage: 'seed' | 'series_a' | 'series_b' | 'enterprise';
  created_at: Date;
  plan: 'starter' | 'growth' | 'scale';
  employees: Employee[];
  settings: CustomerSettings;
}
```

### Employee (Researcher)
```typescript
interface ResearcherEmployee {
  id: string;
  customer_id: string;
  name: string; // Customizable, default "Sarah"
  status: 'active' | 'paused' | 'error';
  
  // Configuration
  sources: SourceConfig[];
  competitors: string[];
  focus_areas: string[];
  delivery: DeliveryConfig;
  
  // State
  last_run_at: Date;
  next_run_at: Date;
  total_briefs: number;
  
  // Feedback
  avg_rating: number; // 1-5
  feedback_count: number;
}
```

### Source Config
```typescript
interface SourceConfig {
  id: string;
  type: 'rss' | 'twitter_list' | 'news_api' | 'website';
  name: string;
  url: string;
  frequency: 'realtime' | 'hourly' | 'daily';
  priority: 'high' | 'medium' | 'low';
  is_active: boolean;
}
```

### Brief
```typescript
interface Brief {
  id: string;
  employee_id: string;
  customer_id: string;
  created_at: Date;
  period_start: Date;
  period_end: Date;
  
  // Content
  summary: string;
  competitor_moves: CompetitorMove[];
  trends: Trend[];
  opportunities: Opportunity[];
  key_readings: Reading[];
  
  // Metadata
  sources_count: number;
  articles_analyzed: number;
  
  // Feedback
  rating?: number;
  feedback?: string;
}
```

---

## 🔌 Integrations

### V1 Integrations (Must-Have)

#### 1. Slack
**Scope:** Send briefs to channel or DM  
**Auth:** OAuth 2.0  
**Permissions:** chat:write, channels:read  
**Features:**
- Rich formatting with blocks
- Thread for detailed items
- 👍/👎 reaction buttons

#### 2. Email (SendGrid)
**Scope:** HTML email delivery  
**Auth:** API key  
**Features:**
- Responsive HTML template
- Plain text fallback
- Open/click tracking

#### 3. Notion (Optional V1)
**Scope:** Create database entries  
**Auth:** OAuth 2.0  
**Features:**
- Create weekly brief page
- Add to customer database

### V2 Integrations (Post-Launch)
- HubSpot (CRM sync)
- Salesforce
- Zendesk/Intercom
- Linear/Jira
- GitHub

---

## 🎨 User Experience

### Onboarding Flow (Target: 10 minutes)

**Step 1: Sign Up (1 min)**
- Email, password, company name
- Verify email

**Step 2: Configure Researcher (5 min)**
- Name your researcher (default: Sarah)
- Add competitors (autocomplete from Crunchbase)
- Select focus areas (checkboxes)
- Add RSS feeds (or pick from curated list)

**Step 3: Connect Channels (3 min)**
- Connect Slack (OAuth) OR
- Verify email delivery
- Choose delivery time (default: Monday 9am)

**Step 4: First Brief Preview (1 min)**
- Show sample brief based on their inputs
- "Your first real brief arrives Monday!"
- CTA: Invite team, upgrade plan

### Dashboard (Simple V1)

**Main View:**
- Employee status (active/paused)
- Next brief countdown
- Last brief preview
- Quick stats (briefs delivered, avg rating)

**Settings:**
- Sources management
- Competitors list
- Delivery preferences
- Billing

**Feedback:**
- List of past briefs
- Rating history
- Suggested improvements

---

## 🔒 Security & Privacy

### Data Handling
- Customer data isolated (no cross-contamination)
- Raw content stored 30 days max
- Vector embeddings anonymized
- No training on customer data

### Compliance
- SOC 2 Type II (target: Month 6)
- GDPR compliant (data deletion on request)
- CCPA compliant

### Access Control
- Customer sees only their data
- Employee config isolated per customer
- Admin access for debugging only

---

## 📈 Scalability

### Current Limits (V1)
- 1 brief per customer per week
- Up to 50 sources per researcher
- Up to 20 competitors tracked
- 100 articles analyzed per brief

### Scaling Plan
**10 customers:** Single server, monolith  
**100 customers:** Containerized, load balancer  
**1,000 customers:** Microservices, separate ingestion/synthesis/delivery  
**10,000 customers:** Multi-region, edge computing

### Cost Optimization
- Caching layer for common queries
- Batch API calls to Claude
- Smart source prioritization (don't check low-value sources as often)
- Efficient embedding storage

---

## 🧪 Testing Strategy

### Unit Tests
- Source connectors (mock HTTP responses)
- Data transformation pipelines
- Prompt engineering (output format validation)

### Integration Tests
- End-to-end brief generation
- Integration health checks (Slack, email)
- Data flow validation

### Manual QA
- Sample 10 briefs, verify quality
- Test edge cases (no news week, breaking news)
- Customer feedback loop validation

---

## 🚀 Release Criteria

### Must-Have (V1.0)
- [ ] Researcher generates coherent briefs
- [ ] Slack integration works
- [ ] Email delivery works
- [ ] Onboarding < 10 minutes
- [ ] 90%+ uptime
- [ ] Cost per brief < $5

### Nice-to-Have (V1.1)
- [ ] Real-time alerts
- [ ] Notion integration
- [ ] Feedback loop impacts synthesis
- [ ] Mobile-responsive dashboard

### Future (V2.0)
- [ ] SDR Employee
- [ ] Support Employee
- [ ] Multi-employee coordination
- [ ] Custom employee builder

---

## 📊 Success Metrics

### Product Metrics
- Brief generation time < 2 minutes
- Brief quality rating > 4.0/5.0
- Source freshness (avg age < 24 hours)
- Error rate < 1%

### Business Metrics
- Time to first brief < 10 minutes (onboarding)
- Weekly active users > 80%
- Feature adoption (connecting 3+ sources) > 70%

---

*Next: Update as we build*
