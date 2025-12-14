# Product Requirements Document (PRD v2)

## Product Name

**TYMEDai1project**

## One-Line Description

A build-in-public founder network powered by LinkedIn data, AI-native agents, and ZeroDB's embedding, vector, and semantic search APIs to create intelligent introductions and autonomous growth.

---

## 1. Vision & Purpose

PublicFounders is a **semantic social network** designed for founders who build in public and grow through relationships, not reach.

Instead of a static social graph, the platform uses **intent embeddings** and **agent reasoning** to understand what founders are building, what they need, and who can help—then actively facilitates those connections.

The system is designed so AI agents are not assistants, but **participants** in the network.

---

## 2. Core Thesis

Traditional social networks rely on:

* Followers
* Connections
* Hard-coded graphs

PublicFounders relies on:

* Meaning
* Intent
* Outcomes

Relationships are **inferred dynamically** via embeddings and semantic similarity, continuously improving as founders interact and outcomes are observed.

---

## 3. Target Users

### Primary

* Early-stage founders (pre-seed → Series A)
* Solo and technical founders
* Founders building in public as a growth strategy

### Secondary

* Angels and early-stage investors
* Advisors and operators
* Recruiters hiring early teams

---

## 4. Core Use Cases

1. Founder documents progress, goals, and asks publicly
2. Platform embeds all activity into intent vectors
3. AI agents identify high-quality matches semantically
4. Agent facilitates warm introductions via LinkedIn or SMS
5. Outcomes feed back into the system to improve future matches

---

## 5. Product Principles

* **Intent over popularity**
* **Embeddings over graphs**
* **Agents over dashboards**
* **Trust through verified identity and outcomes**

---

## 6. Authentication & Data Ingestion

### LinkedIn Integration (Mandatory)

**OAuth-based sign-up**

**Permitted Data Ingestion:**

* Name, headline, profile photo
* Current and past roles
* Companies
* Education
* Skills
* Location
* Public activity signals

All ingested data is:

* User-consented
* Embedded (not mirrored)
* Used to seed semantic understanding

---

## 7. Founder Build-in-Public Profile

### Core Sections

* Auto-generated + editable bio
* Current startup(s)
* What I'm building now
* Current goals (fundraising, hiring, partnerships, growth)
* Open asks
* Public timeline / journal

### AI Enhancements

* Founder narrative summary
* Goal clarity suggestions
* Ask optimization prompts

---

## 8. Build-in-Public Feed

### Content Types

* Progress updates
* Learnings & failures
* Milestones
* Explicit asks

### Feed Logic

* Chronological by default
* Semantic relevance for discovery
* No ads
* No engagement-bait ranking

### AI Support

* Draft suggestions
* Cross-posting to LinkedIn
* Cadence recommendations

---

## 9. Virtual Advisor Agent

### Role

A persistent AI agent representing the founder's interests inside the network.

### Responsibilities

* Understand founder intent and goals
* Monitor semantic network activity
* Identify relevant people and opportunities
* Propose and execute introductions

### Autonomy Modes

* Suggest-only
* Approve-before-intro
* Autonomous (with guardrails)

---

## 10. Intelligent Introductions

### Intro Sources

* PublicFounders users
* LinkedIn 1st-degree connections
* Approved 2nd-degree LinkedIn discovery

### Channels

* LinkedIn DM
* SMS (phone-verified)
* Email (optional)

### Intro Flow

1. Semantic match detected via embeddings
2. Agent explains rationale to founder
3. Consent check (if required)
4. Personalized intro sent
5. Outcome tracked and embedded

---

## 11. Data & Intelligence Layer (ZeroDB)

### Stack

* ZeroDB Embedding API
* ZeroDB Vector Database
* ZeroDB Semantic Search APIs

### Embedded Objects

* Founders
* Companies
* Goals and asks
* Content and updates
* Introductions and outcomes
* Interaction summaries

### Semantic Relationships

Derived dynamically via similarity and clustering:

* Founder ↔ Founder (stage, goals, domain)
* Founder ↔ Investor (thesis alignment)
* Founder ↔ Advisor (experience overlap)

### Advantages

* No rigid schemas
* Strong cold-start performance
* Continuous learning from outcomes
* Agent-friendly reasoning layer

---

## 12. AI-Native Agents API Integration

### Agent Types

* Founder Advisor Agent
* Network Growth Agent
* Content Strategy Agent
* Intro Quality Guard Agent

### Core APIs

* Embedding creation & updates
* Semantic search across entities
* Vector-based agent memory
* Action execution (intros, drafts)
* Feedback ingestion

### Learning Loop

* Outcome-weighted re-embedding
* Similarity threshold tuning
* Personalized trust calibration

---

## 13. Permissions & Privacy

### User Controls

* Public vs private data
* Intro autonomy level
* Allowed communication channels
* Do-not-intro lists

### Compliance

* LinkedIn API policies
* GDPR / CCPA
* Explicit agent consent model

---

## 14. Success Metrics (KPIs)

### Network Health

* Intro acceptance rate
* Response rate
* Successful outcome ratio

### User Value

* Time to first meaningful intro
* Weekly active founders
* Retention by cohort

### Growth

* Agent-initiated introductions
* Invite acceptance rate

---

## 15. MVP Scope

### Phase 1 – Semantic Foundation

* LinkedIn OAuth
* Founder profiles
* Build-in-public feed
* ZeroDB embeddings + vector search
* Human-in-the-loop AI suggestions

### Phase 2 – Agent Execution

* Persistent advisor agent
* Semantic intro matching
* LinkedIn + SMS execution

### Phase 3 – Network Effects

* Multi-agent collaboration
* Investor and advisor layers
* Monetization

---

## 16. Risks & Mitigations

| Risk                  | Mitigation                                  |
| --------------------- | ------------------------------------------- |
| Poor semantic matches | Human review + adaptive thresholds          |
| Agent overreach       | Autonomy controls + audit logs              |
| LinkedIn constraints  | Consent-driven ingestion + user context     |
| Vector drift          | Scheduled re-embedding + outcome correction |

---

## 17. Strategic Advantage

* Semantic network vs social graph
* AI agents as first-class users
* Faster iteration than graph-based systems
* Designed for autonomous growth

---

## 18. Data Model

### Relational Database (PostgreSQL)

#### Core Tables

**users**
```sql
id, email, linkedin_id, first_name, last_name, username,
bio, profile_photo_url, location, founder_type, startup_name,
startup_stage, funding_status, created_at, updated_at
```

**journey_updates**
```sql
id, user_id, content, update_type, mood, metrics_json,
visibility, embedding_id, created_at, reaction_count, comment_count
```

**ai_introductions**
```sql
id, from_user_id, to_user_id, reason, similarity_score,
delivery_method, status, sent_at, accepted_at, outcome_rating
```

**linkedin_connections**
```sql
id, user_id, linkedin_connection_id, first_name, last_name,
headline, matched_user_id, imported_at
```

### Vector Database (ZeroDB)

#### Embedded Entities

**Founder Embeddings**
* Profile bio + startup description + recent updates
* Metadata: stage, goals, needs, skills
* Updated: Weekly or on significant profile change

**Update Embeddings**
* Each journey update content
* Metadata: type, timestamp, visibility, mood
* Updated: On creation

**Introduction Outcomes**
* Intro context + outcome description
* Metadata: success rating, relationship type
* Updated: Post-intro feedback

### Semantic Search Indexes

* Founder intent similarity
* Goal-to-founder matching
* Ask-to-capability matching
* Update topic clustering

---

## 19. Technical Architecture

### Frontend

* Next.js 14 (App Router)
* TypeScript
* Tailwind CSS + shadcn/ui
* Real-time updates (WebSockets)

### Backend

* Next.js API Routes
* Prisma ORM
* PostgreSQL (Supabase)
* ZeroDB Cloud

### AI Layer

* OpenAI GPT-4 or Anthropic Claude
* ZeroDB Embedding API
* ZeroDB Semantic Search API
* Agent orchestration framework

### Integrations

* LinkedIn OAuth + APIs
* Twilio (SMS)
* Resend (Email)
* Stripe (Payments)

---

## 20. Agile Development Plan

### Sprint Structure

**2-Week Sprints, 12 Sprints Total (24 Weeks)**

### Epic Breakdown

**Epic 1: Authentication & LinkedIn Integration**
* OAuth implementation
* Profile data ingestion
* Connection import
* Story Points: 21

**Epic 2: Founder Profiles & Feed**
* Profile creation/editing
* Journey update posting
* Chronological feed
* Story Points: 34

**Epic 3: Embedding Pipeline**
* ZeroDB integration
* Embedding generation
* Vector storage
* Story Points: 34

**Epic 4: Semantic Search**
* Search infrastructure
* Similarity matching
* Filtering & ranking
* Story Points: 21

**Epic 5: AI Advisor Agent**
* Agent architecture
* Intent understanding
* Match detection
* Story Points: 55

**Epic 6: Intelligent Introductions**
* Intro generation
* Multi-channel delivery
* Outcome tracking
* Story Points: 34

**Epic 7: Agent Autonomy**
* Consent management
* Automated execution
* Learning loop
* Story Points: 34

**Epic 8: Polish & Launch**
* UI/UX refinement
* Performance optimization
* Beta testing
* Story Points: 21

### Total Story Points: 254

---

## 21. User Stories (Sample)

### US-1.1: LinkedIn OAuth Sign-Up

**As a** founder  
**I want to** sign up with LinkedIn OAuth  
**So that** my profile is auto-populated and verified

**Acceptance Criteria:**
* LinkedIn consent screen shown with required permissions
* Profile data imported (name, photo, headline, work history)
* User can review and edit imported data
* Account created with linked LinkedIn ID
* Redirected to profile completion

**Priority:** P0  
**Story Points:** 8

---

### US-3.1: Embedding Generation

**As the** system  
**I want to** generate embeddings for founder profiles  
**So that** semantic matching can occur

**Acceptance Criteria:**
* Profile text combined (bio + startup + recent updates)
* Embedding generated via ZeroDB API
* Vector stored with metadata (stage, goals, location)
* Embedding ID linked to user record
* Re-embedding triggered on significant profile changes

**Priority:** P0  
**Story Points:** 13

---

### US-5.2: Semantic Match Detection

**As an** AI agent  
**I want to** detect high-quality founder matches  
**So that** I can suggest relevant introductions

**Acceptance Criteria:**
* Query user's embedding + metadata
* Semantic search returns top 10 similar founders
* Filter by: complementary needs, same stage, location
* Rank by similarity score + outcome history
* Present top 3-5 matches with rationale

**Priority:** P0  
**Story Points:** 21

---

## 22. Testing Strategy

### Methodology

* **TDD:** Write tests before implementation
* **BDD:** Gherkin scenarios for user flows
* **XP:** Pair programming for complex features

### Test Coverage

* Unit tests: 90%+ coverage
* Integration tests: All API endpoints
* E2E tests: Critical user flows
* AI tests: Embedding quality, match relevance

### Sample BDD Scenario

```gherkin
Feature: Intelligent Introduction

Scenario: AI suggests relevant founder match
  Given I am a founder building a SaaS product
  And I posted an update about needing design help
  When the AI advisor analyzes my profile
  Then it should find founders with design expertise
  And suggest introductions with rationale
  And allow me to approve before sending
```

---

## 23. AI Agent Seed Phrases

### Agent 1: Full-Stack Lead Developer

```
You are an expert full-stack developer specialized in:
- Next.js 14, React, TypeScript, Prisma, PostgreSQL
- Test-Driven Development (TDD)
- Behavior-Driven Development (BDD)
- Clean architecture and SOLID principles

When given a user story:
1. Write failing tests first
2. Implement minimum code to pass
3. Refactor for quality
4. Ensure 90%+ test coverage
5. Document edge cases

Focus on: Type safety, testability, performance, maintainability.
```

### Agent 2: AI/ML Integration Specialist

```
You are an AI/ML expert specialized in:
- ZeroDB Embedding & Vector APIs
- Semantic search and similarity matching
- GPT-4/Claude integration
- Agent orchestration and reasoning

When building AI features:
1. Design embedding strategy
2. Implement vector storage/retrieval
3. Build semantic search with filters
4. Create agent decision logic
5. Optimize for relevance and latency

Focus on: Accuracy, cost-efficiency, explainability.
```

### Agent 3: Database Architect

```
You are a database expert specialized in:
- PostgreSQL (indexes, JSONB, performance)
- Prisma ORM (schema, migrations, queries)
- Vector databases (ZeroDB)
- Data modeling for scale

When designing data:
1. Understand access patterns
2. Create normalized schema
3. Add strategic denormalization
4. Design proper indexes
5. Write efficient queries

Focus on: Data integrity, query performance, scalability.
```

### Agent 4: Agile Product Owner

```
You are an Agile product expert specialized in:
- User story writing (INVEST criteria)
- Sprint planning and backlog management
- Acceptance criteria definition
- Prioritization (RICE, MoSCoW)

When given a feature:
1. Write clear user stories
2. Define testable acceptance criteria
3. Estimate story points
4. Prioritize by value
5. Identify dependencies

Focus on: User value, clarity, measurability.
```

### Agent 5: Testing & QA Engineer

```
You are a testing expert specialized in:
- TDD (Test-Driven Development)
- BDD (Behavior-Driven Development)
- Jest/Vitest, Playwright, React Testing Library
- Gherkin scenarios

When testing features:
1. Write BDD scenarios (Given/When/Then)
2. Create unit tests before implementation
3. Write integration tests for APIs
4. Write E2E tests for critical flows
5. Achieve 90%+ coverage

Focus on: Comprehensive coverage, realistic scenarios, maintainability.
```

---

## 24. Environment Configuration

```bash
# .env.local

# Database (Supabase)
DATABASE_URL="postgresql://postgres:[PASSWORD]@db.[PROJECT].supabase.co:5432/postgres"
DIRECT_URL="postgresql://postgres:[PASSWORD]@db.[PROJECT].supabase.co:5432/postgres"

# ZeroDB Configuration
ZERODB_API_KEY="your_zerodb_api_key_here"
ZERODB_PROJECT_ID="your_zerodb_project_id_here"
ZERODB_EMBEDDING_API_URL="https://api.zerodb.com/v1/embeddings"
ZERODB_VECTOR_API_URL="https://api.zerodb.com/v1/vectors"
ZERODB_SEARCH_API_URL="https://api.zerodb.com/v1/search"

# AI Services
OPENAI_API_KEY="sk-..."
# OR
ANTHROPIC_API_KEY="sk-ant-..."

# LinkedIn OAuth
LINKEDIN_CLIENT_ID="your_linkedin_client_id"
LINKEDIN_CLIENT_SECRET="your_linkedin_client_secret"
LINKEDIN_REDIRECT_URI="http://localhost:3000/api/auth/linkedin/callback"

# Authentication
NEXTAUTH_SECRET="generate_with_openssl_rand_base64_32"
NEXTAUTH_URL="http://localhost:3000"

# Communications
TWILIO_ACCOUNT_SID="AC..."
TWILIO_AUTH_TOKEN="..."
TWILIO_PHONE_NUMBER="+1..."
RESEND_API_KEY="re_..."

# Application
NEXT_PUBLIC_APP_URL="http://localhost:3000"
NODE_ENV="development"
```

---

## 25. Repository Structure

```
publicfounders/
├── app/                    # Next.js App Router
│   ├── (auth)/
│   ├── (dashboard)/
│   └── api/
├── components/
│   ├── ui/                # shadcn/ui
│   └── features/
├── lib/
│   ├── ai/               # Agent orchestration
│   ├── zerodb/           # ZeroDB client
│   ├── linkedin/         # LinkedIn API
│   └── prisma/
├── prisma/
│   ├── schema.prisma
│   └── migrations/
├── tests/
│   ├── unit/
│   ├── integration/
│   ├── e2e/
│   └── bdd/
├── docs/
│   ├── PRD.md
│   ├── ARCHITECTURE.md
│   └── API.md
└── .env.local
```

---

## 26. Getting Started

### Prerequisites

* Node.js 18+
* PostgreSQL or Supabase account
* ZeroDB account
* LinkedIn Developer app
* OpenAI or Anthropic API key

### Quick Start

```bash
# Clone repository
git clone https://github.com/yourusername/publicfounders.git
cd publicfounders

# Install dependencies
npm install

# Configure environment
cp .env.example .env.local
# Fill in API keys

# Setup database
npx prisma generate
npx prisma db push

# Run development server
npm run dev

# Run tests
npm test
```

---

## 27. Success Metrics

### Launch (Month 1)

* 100 registered founders
* 500 journey updates
* 50 AI-facilitated introductions
* 80% onboarding completion

### Growth (Month 3)

* 1,000 active founders
* 5,000 updates
* 500 successful connections
* 20% DAU/MAU ratio

### Product-Market Fit (Month 6)

* 40% 30-day retention
* NPS > 50
* 3+ updates per founder/month
* 10% conversion to paid tier

---

**Status:** Final Draft v2  
**Owner:** Product  
**Last Updated:** December 2024
