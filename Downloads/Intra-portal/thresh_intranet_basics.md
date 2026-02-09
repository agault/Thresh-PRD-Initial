## MVP:
* Landing page - Thresh metrics (tbd), News API- RSS FEED (Tech news [AI, digital products])
    + NewsAPI (has a free tier, easy integration) + Hacker News API (completely free). 
    + If no API Convert RSS feeds from TechCrunch, VentureBeat, MIT Technology Review, The Verge into JSON
* House all SOPs
* Info Tools & Apps 
* Onboarding 
    - General
    - Product Managers
    - Designers
    - Devs
* Org Chart || Teams & Members
* Thresh Standards
    - Brand Guidelines
        - Design Standards
        - Coding Standards
    - Templates
        + Slide Deck
        + Email Signature
        + PRD
    - Folder with standard assets (Imgs)

* Login with certain users having CRUD access




____


### *Flags*
* We are moving to **<u>Cloudflare</u>** keep that in mind when building
* we need to choose the best code stack that will mirror our branded eventually. Framer -> React || Vue ||  ?
* Tech APIs most are paid, may need to us RSS feeds to custom build the news carousel.

#### Critical Constraints

1. ✅ Moving to Cloudflare - entire stack must be Cloudflare-compatible

    + Cloudflare Pages for hosting
    + Cloudflare Workers for serverless functions
    + Cloudflare D1 or KV for data storage


2. 🤔 Code Stack Decision: Need to mirror eventual brand site migration

    + Current: Framer <- Branded site
    + Options: React || Vue || Next.js (React)
    + Recommendation: Next.js (React) for Cloudflare Pages compatibility + easier migration path


3. 💰 API Costs: Most tech news APIs are paid beyond free tiers

    + Use free tiers + caching strategy
    + Build custom RSS feed aggregator as fallback
    + Server-side API calls to hide keys
____
____

## Moonshot:
* Jira Ticket Scraper and Flagger
    + Auto-sync project health from Jira
    + Flag at-risk tickets/projects
    + Display sprint velocity
* Team member profiles (Pull from Linkedin API?)
    + Pull from LinkedIn API (with user consent)
    + Auto-populate bios, skills, work history
* Chat Bot
    + Internal AI assistant for answering SOP questions
    + Tool lookup ("Where's the Figma login?")
    + RAG on internal documentation
* KPI and OKR progress tracker
    + Visual dashboards for goals
    + Team-level and individual tracking
    + Quarterly OKR management



____
____

## Pages:
* Dashboard (The Home Base)
* SOPs (The Knowledge Base)
* Tools & Apps (What tools, why, and general info)
* Org Chart & Teams (The People)
* Projects (The Delivery)

____
____


### 1. Dashboard (The Home Base)
Operational Optics: High-level "Product Scorecard" (Health, Velocity, Success).

- Primary: NewsAPI (free tier: 100 req/day) + Hacker News API (unlimited free)
- Fallback: RSS to JSON conversion from TechCrunch, VentureBeat, MIT Tech Review, The Verge
- Display as carousel or card grid
- Cache results to minimize API calls
- Filter by: AI, Digital Products, Design, Development






____

### 2. SOPs (The Knowledge Base)
"The Thresh Way": Onboarding documentation on what it means to be "Product" at Thresh.

Resource Library: Templates, Brand Guidelines, and the Styleguide.

Brand Assets: Thresh-branded decks and the LinkedIn Welcome Graphic generator.

Training Vault: Standard Operating Procedures for internal workflows.

____

### 3. Tools & Apps (The Integration Hub)
Centralized Access: One-click login/entry to all external SaaS.

AI Resume Eval: A dedicated internal tool/module for scanning candidates.

Internal Automations: Area for future administrative task automation.

____

### 4. Org Chart & Teams (The People)
Core Product Team: Bio, roles, and contact info.

Engineering & Design: Breakdown of who is on which squad.

Eminence Plan: Tracking team demos and public-facing thought leadership.

____

### 5. Projects (The Delivery)
Project Health: Live status of current builds.

The "Stack" per Project: Which tech/tools are assigned to which initiative.

Archives: Record of past demos and project outcomes.

____

### Internal Tech Architecture (Mental Model)
#### Rough Data Logic
CRUD Rules: General users = Read Only. Leadership/Admin = Edit/Create.

Data Pulls: Needs to talk to Jira (for Project Health) and external News APIs (for Discovery).