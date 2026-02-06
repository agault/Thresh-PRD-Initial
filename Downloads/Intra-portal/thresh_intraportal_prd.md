# Thresh IntraPortal - Product Requirements Document
#VERY BASIC FIRST DRAFT, MANY UPDATES NEED TO BE MADE || SCRAPPED

## 1. Executive Summary

### Product Vision
Thresh IntraPortal is a centralized internal web application that serves as the single source of truth for all Thresh Consulting operations, team resources, and product intelligence. It combines tool integration, onboarding automation, brand consistency, and industry intelligence to streamline operations and empower the team.

### Success Metrics
- Reduce tool access time by 70%
- Onboard new members in <2 days (vs current baseline)
- 90% team adoption within first month
- Daily active usage by 80% of team members

---

## 2. Problem Statement

**Current State:**
- Team members waste time navigating between disconnected tools
- No centralized onboarding system for new hires
- Limited visibility into product health and delivery metrics
- No systematic way to stay current with industry trends
- Brand assets and templates scattered across multiple locations
- Inconsistent access to documentation and learning resources

**Desired State:**
- Single portal for all team needs with SSO integration
- Automated onboarding workflow with role-based content
- Real-time product scorecard and operational dashboards
- AI-curated industry news and trend analysis
- Centralized brand asset library with version control
- Role-based access control (RBAC) with audit trails

---

## 3. Target Users & Personas

### Primary Users
1. **Core Product Team**
   - Product Managers
   - Product Designers
   - Product Strategists

2. **Development Team**
   - Frontend/Backend Engineers
   - DevOps Engineers
   - QA/Test Engineers

3. **Design Team**
   - UI/UX Designers
   - Brand Designers
   - Design Researchers

### Secondary Users
4. **Leadership**
   - CEO/Executive Team
   - Department Heads
   - Admin roles with CRUD permissions

5. **New Hires**
   - All roles during onboarding period

---

## 4. Core Features & Functionality

### 4.1 Dashboard & Home
**Priority: P0 (Launch Blocker)**

- **Product Scorecard Dashboard**
  - Real-time metrics: velocity, burn rate, delivery health
  - Project status overview (Active, At Risk, Completed)
  - Team capacity and allocation visualization
  - Sprint progress tracking
  
- **Personalized Home Feed**
  - Role-based content recommendations
  - Recent documents and updates
  - Upcoming deadlines and milestones
  - Quick access to frequently used tools

### 4.2 Tool Integration Hub
**Priority: P0 (Launch Blocker)**

**Integrated Applications:**
- **Google Workspace**
  - Drive: Document search and quick access
  - Calendar: Team availability and upcoming events
  - Gmail: Unread count and quick compose
  
- **Design Tools**
  - Figma: Recent files and shared libraries
  - Adobe Creative Suite: Asset library access
  
- **Development Tools**
  - Jira: Sprint board, ticket status, my assignments
  - GitHub: PR reviews, commit activity, repo health
  - Claude Code: Project snippets and automation scripts
  
- **Communication**
  - Slack: Channel quick links, notifications
  - Zoom: Instant meeting links

**Implementation:**
- OAuth 2.0 for secure authentication
- API integrations for data fetching
- Deep linking to specific documents/tickets
- Real-time sync with webhook support

### 4.3 AI-Powered Industry Intelligence
**Priority: P1 (High Priority)**

**Tech News Aggregator**
- **Sources:** TechCrunch, The Verge, Hacker News, Product Hunt, Benedict Evans newsletter, AI-focused publications
- **Topics:** AI/ML trends, digital transformation, product innovation, consulting industry news
- **Features:**
  - Daily curated digest (AI-summarized)
  - Topic categorization and filtering
  - Bookmarking and sharing with team
  - Trend analysis and pattern detection
  - Competitor intelligence tracking

**Recommended APIs:**
- News API or Google News API for aggregation
- OpenAI API or Claude API for summarization and analysis
- RSS feed parsers for niche sources
- Custom web scraping for specific sources (ethically)

**Benchmark Evolution Tracker**
- Industry benchmarks for product metrics
- Quarterly trend analysis
- Comparative analytics vs. competitors
- Visual trend graphs and insights

### 4.4 Onboarding & Learning Center
**Priority: P0 (Launch Blocker)**

**"What Does It Mean to Be Product at Thresh"**
- Interactive onboarding journey
- Role-specific learning paths
- Video tutorials and documentation
- Quiz-based knowledge checks
- Completion tracking and certifications

**Resources Library:**
- Thresh Stack documentation
- Best practices and playbooks
- Case studies and project retrospectives
- Training videos and workshops
- External learning resources (curated)

**Onboarding Workflow:**
- Day 1: Welcome package, system access, brand introduction
- Week 1: Tool training, team introductions, first assignment
- Month 1: Check-ins, feedback loops, certification completion
- Automated task assignment based on role
- Progress dashboard for managers

### 4.5 Brand & Asset Management
**Priority: P1 (High Priority)**

**Thresh Eminence Plan/Demo**
- Brand story and value proposition
- Client success stories
- Demo materials and pitch decks
- LinkedIn welcome graphics generator
- Custom branded templates

**Brand Guidelines & Style Guide**
- Logo usage and variations
- Color palette (with hex codes)
- Typography standards
- Voice and tone guidelines
- Design system documentation
- Downloadable asset packs

**Template Library:**
- Custom presentation decks (Google Slides/PowerPoint)
- Proposal templates
- Client deliverable templates
- Internal documentation templates
- Email signatures and letterheads

**Thresh AI Resume Evaluator**
- AI-powered resume screening for hiring
- Skill matching against job descriptions
- Automated candidate scoring
- Integration with ATS (if applicable)

### 4.6 User Management & Permissions
**Priority: P0 (Launch Blocker)**

**Role-Based Access Control (RBAC):**
- **Admin:** Full CRUD access to all features
- **Leadership:** Read-all, write-some (dashboards, reports)
- **Product Team:** Read-all, write-team resources
- **Development Team:** Read-most, write-dev resources
- **New Hires:** Read-only until onboarding complete

**User Features:**
- Profile management
- Notification preferences
- Activity logs
- Team directory with org chart

### 4.7 Knowledge Base & Documentation
**Priority: P1 (High Priority)**

- **Internal Wiki**
  - Process documentation
  - Technical specifications
  - FAQs and troubleshooting
  - Version-controlled documentation
  
- **Search Functionality**
  - Global search across all modules
  - AI-powered semantic search
  - Filter by content type, date, author
  - Search analytics for content gaps

----

## 5. Technical Architecture

### 5.1 Recommended Technology Stack

**Frontend:**
- **Framework:** Next.js 14+ (React) - with edge runtime support for Cloudflare
  - *Rationale:* SSR for performance, great developer experience, built-in API routes, Cloudflare Pages compatibility
  - *Alternative:* Remix (excellent Cloudflare support) or SvelteKit
- **UI Library:** shadcn/ui + Tailwind CSS or Material-UI
- **State Management:** Zustand or React Query for server state
- **Authentication:** NextAuth.js (with edge runtime adapters) or Clerk

**Backend:**
- **Primary Option:** Cloudflare Workers (serverless edge functions)
  - API routes deployed to Cloudflare's global network
  - Ultra-low latency worldwide
  - Automatic scaling
- **Alternative:** Next.js API Routes (compatible with Cloudflare Pages)
- **Database:** Cloudflare D1 (SQLite at edge) + Cloudflare KV (key-value) + Durable Objects
  - *Alternative:* PostgreSQL via Neon or Supabase (with edge functions)
- **ORM:** Drizzle ORM (optimized for edge) or Prisma with edge runtime
- **File Storage:** Cloudflare R2 (S3-compatible, zero egress fees)

**APIs & Integrations:**
- **AI/ML:** Claude API (Anthropic) or OpenAI API
- **News:** News API, RSS feeds, custom scrapers
- **Google Workspace:** Google APIs (Drive, Calendar, Gmail)
- **Jira:** Atlassian REST API
- **Figma:** Figma REST API
- **GitHub:** GitHub REST/GraphQL API
- **Slack:** Slack API with webhooks

**Infrastructure (Cloudflare-First):**
- **Hosting:** Cloudflare Pages (static + edge functions)
- **Serverless:** Cloudflare Workers for API routes
- **CDN:** Cloudflare CDN (included, global edge network)
- **Database:** Cloudflare D1 or Neon (serverless Postgres)
- **Storage:** Cloudflare R2 (object storage)
- **Caching:** Cloudflare KV + Cache API
- **CI/CD:** GitHub Actions → Cloudflare Pages
- **Monitoring:** Sentry (errors) + Cloudflare Analytics (included)
- **Authentication:** OAuth 2.0 with SSO via NextAuth.js or Clerk
- **DDoS Protection:** Included with Cloudflare

### 5.2 Data Models (High-Level)

**Core Entities:**
```
Users
- id, email, name, role, department, start_date
- permissions, preferences, avatar_url

Projects
- id, name, status, health_score, start_date, end_date
- assigned_team, jira_board_id, figma_file_id

Resources
- id, title, type, content, category, tags
- created_by, updated_at, access_level

News_Articles
- id, title, summary, source, url, published_date
- topics, ai_summary, bookmark_count

Templates
- id, name, type, category, file_url
- preview_image, description, usage_count

Activity_Logs
- id, user_id, action, resource_type, timestamp
```

### 5.3 Security & Compliance

- SSL/TLS encryption for all data in transit
- OAuth 2.0 for third-party integrations
- JWT tokens for session management
- Regular security audits and penetration testing
- GDPR-compliant data handling (if applicable)
- Audit logs for all CRUD operations
- Rate limiting on APIs
- Input validation and sanitization

---

## 6. Information Architecture & Site Map

### Navigation Structure

```
Thresh IntraPortal
│
├── 🏠 Dashboard (Home)
│   ├── Welcome / Quick Stats
│   ├── Tech News Feed (API-powered)
│   ├── Company Health Metrics
│   │   ├── Active Projects Count
│   │   ├── Team Velocity
│   │   ├── Recent Wins
│   │   └── Upcoming Milestones
│   ├── My Quick Actions
│   └── Recent Activity
│
├── 📋 SOPs (Standard Operating Procedures)
│   ├── SOP Library (categorized)
│   ├── Process Documentation
│   ├── Best Practices
│   ├── Templates & Checklists
│   └── Search SOPs
│
├── 📚 Resources
│   ├── Onboarding Journey
│   │   ├── Welcome Package
│   │   ├── Day 1 Checklist
│   │   ├── Week 1 Training
│   │   └── Month 1 Certification
│   ├── Brand Hub
│   │   ├── Brand Guidelines
│   │   ├── Logo Assets
│   │   ├── Templates Library
│   │   ├── Presentation Decks
│   │   └── LinkedIn Graphics Generator
│   ├── Learning Center
│   │   ├── What is Product at Thresh
│   │   ├── Thresh Stack Documentation
│   │   ├── Video Tutorials
│   │   └── Certifications
│   ├── Knowledge Base / Wiki
│   └── AI Resume Evaluator (Hiring Tool)
│
├── 🛠️ Tools & Apps
│   ├── Company Tech Stack Overview
│   ├── Tool Cards (with info)
│   │   ├── Figma
│   │   │   ├── What we use it for
│   │   │   ├── Why we chose it
│   │   │   ├── Quick access link
│   │   │   └── Getting started guide
│   │   ├── Slack
│   │   ├── GitHub
│   │   ├── Google Drive
│   │   ├── Claude
│   │   ├── Client Jira
│   │   └── [Other tools]
│   ├── Integration Dashboard
│   │   ├── Recent Figma files
│   │   ├── GitHub PRs
│   │   ├── Drive documents
│   │   └── Slack channels
│   └── Tool Request Form
│
├── 👥 Team
│   ├── Org Chart (Interactive)
│   ├── Team Directory
│   │   ├── Filter by: Department, Role, Location
│   │   ├── Profile Cards (with LinkedIn headshots)
│   │   └── Contact Info
│   ├── Departments
│   │   ├── Product Team
│   │   ├── Engineering Team
│   │   ├── Design Team
│   │   └── Leadership
│   └── My Profile
│
├── 📊 Projects
│   ├── Project Portfolio
│   │   ├── Active Projects
│   │   ├── Completed Projects (Archive)
│   │   ├── Upcoming Projects
│   │   └── On Hold
│   ├── Project Cards with:
│   │   ├── Status & Health Score
│   │   ├── Team Members
│   │   ├── Timeline
│   │   ├── Client Info
│   │   ├── Key Deliverables
│   │   └── Links (Jira, Figma, Drive)
│   ├── Project Templates
│   └── Success Stories / Case Studies
│
└── ⚙️ Settings (Admin Only)
    ├── User Management
    ├── Permissions & Roles
    ├── API Integrations
    └── Activity Logs
```

---

## 7. Detailed Page Specifications

### 7.1 Dashboard (Home) Page

**Purpose:** Central hub with real-time information and quick access

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  Header: Welcome back, [Name]! 👋                           │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ Active       │  │ Team         │  │ Projects     │      │
│  │ Projects: 12 │  │ Velocity: ↑  │  │ Completed: 8 │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│                                                              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  📰 Tech News & Industry Trends (AI-Curated)                │
│  ┌──────────────────────────────────────────────────────┐  │
│  │ [Article Card 1] - TechCrunch                         │  │
│  │ AI Summary: OpenAI releases...                        │  │
│  │ Tags: #AI #Product                                    │  │
│  ├──────────────────────────────────────────────────────┤  │
│  │ [Article Card 2] - The Verge                          │  │
│  │ AI Summary: New design trends...                      │  │
│  ├──────────────────────────────────────────────────────┤  │
│  │ [Article Card 3] - Hacker News                        │  │
│  └──────────────────────────────────────────────────────┘  │
│  [View All News →]                                          │
│                                                              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Quick Actions                    Recent Activity           │
│  • Create New Project             • John updated SOP...     │
│  • View My Tasks                  • New project added...    │
│  • Access Brand Assets            • Sarah joined team...    │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**Components:**

1. **Health Metrics Cards** (Top section)
   - Active Projects Count
   - Team Velocity (story points trend)
   - Projects Completed This Month
   - Team Capacity Utilization
   - Upcoming Deadlines (this week)
   - Recent Wins 🎉

2. **Tech News Feed** (Center, largest section)
   - AI-summarized articles (2-3 sentences each)
   - Filter by topic: All, AI/ML, Consulting, Design, Product
   - Source badges (TechCrunch, HN, The Verge)
   - Bookmark and share functionality
   - Refresh every 4 hours via cron
   - Link to full article
   - "Read More" → Full Industry Intelligence page

3. **Quick Actions** (Right sidebar)
   - Create new project
   - Submit SOP
   - Access templates
   - View my tasks (from Jira)
   - Schedule meeting

4. **Recent Activity Feed** (Bottom right)
   - Team updates
   - New SOPs added
   - Project status changes
   - New team members
   - Resource uploads

**Data Sources:**
- News: RSS feeds + Claude API summarization
- Metrics: D1 database + Jira API
- Activity: D1 activity_logs table

---

### 7.2 SOPs Page (Standard Operating Procedures)

**Purpose:** Centralized repository for all company processes and procedures

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  📋 Standard Operating Procedures                           │
│  [Search SOPs...] 🔍                                        │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Categories:                                                │
│  ├─ 📦 Product Management (8 SOPs)                          │
│  ├─ 💻 Engineering (12 SOPs)                                │
│  ├─ 🎨 Design (6 SOPs)                                      │
│  ├─ 👥 People & HR (4 SOPs)                                 │
│  ├─ 💼 Client Management (7 SOPs)                           │
│  └─ 🔐 Security & Compliance (5 SOPs)                       │
│                                                              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Recently Updated:                                          │
│  ┌──────────────────────────────────────────────────────┐  │
│  │ 📄 Client Kickoff Process                             │  │
│  │    Updated: 2 days ago by Sarah                       │  │
│  │    [View] [Download PDF]                              │  │
│  ├──────────────────────────────────────────────────────┤  │
│  │ 📄 Code Review Guidelines                             │  │
│  │    Updated: 1 week ago by Mike                        │  │
│  │    [View] [Download PDF]                              │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                              │
│  [+ Add New SOP] (Admin)                                    │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**Features:**

1. **SOP Library**
   - Hierarchical categories
   - Each SOP has:
     - Title
     - Description
     - Category/tags
     - Owner
     - Last updated date
     - Version history
     - PDF download option
     - Rich text editor view

2. **SOP Categories:**
   - **Product Management**
     - Product discovery process
     - User research guidelines
     - Roadmap planning
     - Feature prioritization
     - Sprint planning
   
   - **Engineering**
     - Code review process
     - Git workflow
     - Deployment procedures
     - Incident response
     - Testing standards
   
   - **Design**
     - Design handoff process
     - Figma organization
     - Accessibility guidelines
     - Design QA checklist
   
   - **Client Management**
     - Client kickoff process
     - Weekly status reports
     - Change request handling
     - Project closeout
   
   - **People & HR**
     - Onboarding checklist
     - Performance review process
     - Time off requests
     - Team meeting cadence

3. **Search & Filter**
   - Full-text search across all SOPs
   - Filter by category
   - Filter by recently updated
   - Filter by owner/department

4. **Templates & Checklists**
   - Downloadable templates for each SOP
   - Interactive checklists
   - Example deliverables

5. **Version Control**
   - Track changes over time
   - See who made updates
   - Compare versions
   - Restore previous versions

**Data Model:**
```sql
CREATE TABLE sops (
  id TEXT PRIMARY KEY,
  title TEXT NOT NULL,
  description TEXT,
  category TEXT NOT NULL,
  content TEXT, -- Rich text / Markdown
  owner_id TEXT,
  version INTEGER DEFAULT 1,
  status TEXT DEFAULT 'active', -- active, draft, archived
  file_url TEXT, -- PDF version
  tags TEXT, -- JSON array
  created_at DATETIME,
  updated_at DATETIME
);

CREATE TABLE sop_versions (
  id TEXT PRIMARY KEY,
  sop_id TEXT,
  version INTEGER,
  content TEXT,
  updated_by TEXT,
  updated_at DATETIME
);
```

---

### 7.3 Resources Page

**Purpose:** One-stop shop for all team learning materials, brand assets, and documentation

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  📚 Resources Hub                                            │
│  Everything you need to succeed at Thresh                   │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌─────────────────┐  ┌─────────────────┐                  │
│  │ 🎓 Onboarding   │  │ 🎨 Brand Hub    │                  │
│  │                 │  │                 │                  │
│  │ • Day 1         │  │ • Guidelines    │                  │
│  │ • Week 1        │  │ • Logo Assets   │                  │
│  │ • Month 1       │  │ • Templates     │                  │
│  │                 │  │ • Presentations │                  │
│  └─────────────────┘  └─────────────────┘                  │
│                                                              │
│  ┌─────────────────┐  ┌─────────────────┐                  │
│  │ 📖 Learning     │  │ 🤖 AI Tools     │                  │
│  │ Center          │  │                 │                  │
│  │                 │  │ • Resume Eval   │                  │
│  │ • What is PM    │  │ • Content Gen   │                  │
│  │ • Thresh Stack  │  │                 │                  │
│  │ • Certifications│  │                 │                  │
│  └─────────────────┘  └─────────────────┘                  │
│                                                              │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 📝 Knowledge Base & Wiki                            │   │
│  │ [Search documentation...]                           │   │
│  │                                                       │   │
│  │ Popular Articles:                                    │   │
│  │ • How to set up local development                   │   │
│  │ • Figma best practices                              │   │
│  │ • Client communication guidelines                   │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**Sections:**

1. **Onboarding Journey**
   - Interactive progress tracker
   - Day 1: Welcome video, profile setup, tool access
   - Week 1: Tool training, team intro, first assignment
   - Month 1: Certification, feedback, 1:1 with manager
   - Role-specific paths (PM, Engineer, Designer)
   - Completion badges

2. **Brand Hub**
   - **Brand Guidelines**
     - Mission, vision, values
     - Voice and tone guide
     - Visual identity (colors, typography)
     - Logo usage rules (with dos/don'ts)
     - Downloadable brand book PDF
   
   - **Logo & Assets**
     - Logo variations (full, icon, wordmark)
     - Multiple formats (PNG, SVG, EPS)
     - Color and B&W versions
     - Minimum size guidelines
     - Download all assets (ZIP)
   
   - **Templates Library**
     - Presentation decks (Google Slides, PowerPoint)
     - Proposal templates
     - Case study templates
     - One-pagers
     - Email signatures
     - Social media templates
   
   - **LinkedIn Graphics Generator**
     - Upload photo → generates branded welcome graphic
     - Input: Name, title, headshot
     - Output: LinkedIn-ready image
     - Multiple design variants

3. **Learning Center**
   - **"What Does It Mean to Be Product at Thresh"**
     - Video course
     - Interactive modules
     - Quiz at end
     - Certificate upon completion
   
   - **Thresh Stack Documentation**
     - Why we use each tool
     - Setup guides
     - Best practices
     - Tips and tricks
   
   - **Video Tutorials**
     - Figma workflows
     - Jira setup
     - GitHub basics
     - Claude Code usage
   
   - **External Resources**
     - Recommended books
     - Online courses
     - Podcasts
     - Industry blogs

4. **AI Tools**
   - **Thresh AI Resume Evaluator**
     - Upload resume (PDF/DOCX)
     - Select job role
     - AI analyzes fit (Claude API)
     - Generates score and feedback
     - Downloadable report
   
   - **Content Generator** (future)
   - **Meeting Summarizer** (future)

5. **Knowledge Base / Wiki**
   - Full-text search
   - Categories: Technical, Process, Client, General
   - Community contributions
   - Upvote helpful articles
   - Recently updated
   - Most viewed

---

### 7.4 Tools & Apps Page

**Purpose:** Document all company tools with reasoning, access info, and quick links

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  🛠️ Our Tech Stack                                          │
│  Tools that power Thresh                                    │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌────────────────────────────────────────────────────┐    │
│  │ 🎨 Figma                                            │    │
│  │ Design & Prototyping                               │    │
│  │                                                      │    │
│  │ What: Collaborative design tool                     │    │
│  │ Why: Best-in-class for UI/UX, real-time collab     │    │
│  │ Used by: Design, Product teams                      │    │
│  │                                                      │    │
│  │ Quick Links:                                        │    │
│  │ • [Recent Files] • [Team Library] • [Tutorials]    │    │
│  │                                                      │    │
│  │ Getting Started: [Setup Guide] [Best Practices]    │    │
│  └────────────────────────────────────────────────────┘    │
│                                                              │
│  ┌────────────────────────────────────────────────────┐    │
│  │ 💬 Slack                                            │    │
│  │ Team Communication                                  │    │
│  │                                                      │    │
│  │ What: Real-time messaging and collaboration        │    │
│  │ Why: Keeps team connected, integrates with tools   │    │
│  │ Used by: Everyone                                   │    │
│  │                                                      │    │
│  │ Key Channels:                                       │    │
│  │ • #general • #engineering • #design • #wins        │    │
│  │                                                      │    │
│  │ [Open Slack] [Channel Guide] [Best Practices]     │    │
│  └────────────────────────────────────────────────────┘    │
│                                                              │
│  [More tools below: GitHub, Drive, Claude, Jira...]        │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**Tool Cards Format:**

Each tool gets a detailed card:

1. **Figma**
   - **Icon/Logo:** Official Figma logo
   - **Category:** Design & Prototyping
   - **What it is:** Collaborative interface design tool
   - **Why we use it:**
     - Industry-leading design tool
     - Real-time collaboration
     - Component libraries and design systems
     - Developer handoff features
     - Integrates with our workflow
   - **Who uses it:** Design team, Product team
   - **Cost:** Professional plan, ~$15/user/month
   - **Quick links:**
     - Open Figma
     - Recent files (API integration)
     - Team libraries
     - Plugin recommendations
   - **Getting started:**
     - Setup guide
     - Best practices doc
     - Video tutorials
     - Keyboard shortcuts
   - **Support:** help@thresh.com

2. **Slack**
   - **Category:** Communication
   - **What + Why + Who**
   - **Key channels:**
     - #general - announcements
     - #engineering - dev discussions
     - #design - design critiques
     - #random - watercooler
     - #wins - celebrate successes
   - **Integrations:** GitHub, Jira, Google Drive
   - **Etiquette guide:**
     - Use threads
     - @channel sparingly
     - Status updates
   - **Links:** [Open Slack] [Channel Guide]

3. **GitHub**
   - **Category:** Version Control & Code Hosting
   - **What + Why + Who**
   - **Repos:**
     - Active repos list (API)
     - Open PRs needing review
     - Recent commits
   - **Workflow:**
     - Branch strategy
     - PR template
     - Review process
   - **Links:** [GitHub] [Repos] [PR Queue]

4. **Google Drive**
   - **Category:** File Storage & Collaboration
   - **Folder structure:**
     - /Clients
     - /Internal
     - /Brand Assets
     - /Templates
   - **Organization tips**
   - **Permissions guide**
   - **Links:** [Open Drive] [Recent Docs]

5. **Claude (Anthropic)**
   - **Category:** AI Assistant
   - **What + Why + Who**
   - **Use cases:**
     - Code generation
     - Documentation
     - Research
     - Content creation
   - **Best practices**
   - **Links:** [Claude] [API Docs]

6. **Client Jira**
   - **Category:** Project Management (Client-facing)
   - **What + Why + Who**
   - **Multi-tenant:** Different board per client
   - **Workflow**
   - **Links:** [Client 1 Jira] [Client 2 Jira]

**Additional Features:**

- **Integration Dashboard** (bottom section)
  - Live data from each tool
  - Recent Figma files (API)
  - GitHub PR queue (API)
  - Drive recent docs (API)
  - Slack unread counts

- **Tool Request Form**
  - Suggest new tools
  - Submit for leadership review
  - Track requests

- **Tech Stack Diagram**
  - Visual representation
  - How tools connect
  - Data flow

---

### 7.5 Team Page

**Purpose:** Team directory with org chart and profiles (LinkedIn headshots)

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  👥 Our Team                                                 │
│  [Search team...] 🔍   Filter: [All] [Product] [Eng] [Design│
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  📊 Org Chart (Interactive)                                 │
│  ┌──────────────────────────────────────────────────────┐  │
│  │                    [CEO]                              │  │
│  │                      │                                │  │
│  │       ┌──────────────┼──────────────┐                │  │
│  │       │              │              │                │  │
│  │   [Product]      [Engineering]  [Design]            │  │
│  │     │  │           │  │  │        │  │              │  │
│  │    [PMs...]      [Devs...]     [Designers...]       │  │
│  └──────────────────────────────────────────────────────┘  │
│  [Expand Org Chart]                                         │
│                                                              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Team Directory                                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │ [Headshot]   │  │ [Headshot]   │  │ [Headshot]   │     │
│  │ John Doe     │  │ Jane Smith   │  │ Mike Chen    │     │
│  │ Product Lead │  │ Sr. Engineer │  │ Lead Designer│     │
│  │ Product Team │  │ Engineering  │  │ Design Team  │     │
│  │              │  │              │  │              │     │
│  │ 📧 john@..   │  │ 📧 jane@..   │  │ 📧 mike@..   │     │
│  │ 🔗 LinkedIn  │  │ 🔗 LinkedIn  │  │ 🔗 LinkedIn  │     │
│  │ [View Profile│  │ [View Profile│  │ [View Profile│     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**Features:**

1. **Interactive Org Chart**
   - Click to expand/collapse departments
   - Hover to see quick info
   - Click person → go to profile
   - Export as PNG
   - Mobile-friendly tree view

2. **Team Directory Cards**
   - **Profile Photo:** Pulled from LinkedIn API or uploaded
   - **Name**
   - **Title/Role**
   - **Department**
   - **Contact:**
     - Email
     - Slack handle
     - LinkedIn profile link
   - **Bio:** Short description (optional)
   - **Skills/Expertise:** Tags
   - **Start date**
   - **Fun fact** (optional)

3. **Filters:**
   - By department (Product, Engineering, Design, Leadership)
   - By role (PM, Engineer, Designer, etc.)
   - By location (if distributed team)
   - By start date (veterans vs new hires)

4. **Search:**
   - Search by name
   - Search by skills
   - Search by department

5. **LinkedIn Integration Options:**
   
   **Option A: Manual Upload (Simplest)**
   - Team members upload their own headshot
   - Admin uploads during onboarding
   
   **Option B: LinkedIn Profile Scraping (Medium)**
   - Use LinkedIn public profile URLs
   - Scrape headshot from public profiles
   - Requires profile URLs in database
   - Note: LinkedIn may block automated scraping
   
   **Option C: LinkedIn API (Official, Requires Approval)**
   - Apply for LinkedIn API access
   - Requires each user to OAuth authorize
   - Can pull: headshot, title, headline
   - Best for long-term solution
   
   **Recommended:** Start with Option A (manual), move to C if LinkedIn approves API access

6. **Profile Page (click through from directory)**
   ```
   ┌─────────────────────────────────────────────┐
   │  [Large Headshot]                           │
   │                                             │
   │  John Doe                                   │
   │  Senior Product Manager                     │
   │  Product Team                               │
   │                                             │
   │  📧 john@thresh.com                         │
   │  💬 @john.doe (Slack)                       │
   │  🔗 linkedin.com/in/johndoe                 │
   │  📅 Joined: Jan 2024                        │
   │                                             │
   │  About:                                     │
   │  Passionate about building products that... │
   │                                             │
   │  Skills: Product Strategy, User Research,   │
   │  Roadmapping, Stakeholder Management        │
   │                                             │
   │  Projects:                                  │
   │  • Project Alpha (Lead PM)                  │
   │  • Project Beta (Contributing PM)           │
   │                                             │
   │  Fun Fact: 🎸 Plays guitar in a band        │
   └─────────────────────────────────────────────┘
   ```

**Data Model:**
```sql
CREATE TABLE team_members (
  id TEXT PRIMARY KEY,
  email TEXT UNIQUE NOT NULL,
  name TEXT NOT NULL,
  title TEXT NOT NULL,
  department TEXT NOT NULL,
  role TEXT,
  bio TEXT,
  skills TEXT, -- JSON array
  linkedin_url TEXT,
  slack_handle TEXT,
  headshot_url TEXT, -- R2 storage or LinkedIn
  start_date DATE,
  fun_fact TEXT,
  manager_id TEXT, -- For org chart
  status TEXT DEFAULT 'active', -- active, offboarded
  created_at DATETIME
);
```

---

### 7.6 Projects Page

**Purpose:** Portfolio of all projects (active, completed, upcoming)

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  📊 Projects                                                 │
│  [Search projects...] 🔍   Filter: [All] [Active] [Complete]│
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Stats: 12 Active | 8 Completed | 3 Upcoming                │
│                                                              │
│  Active Projects                                            │
│  ┌────────────────────────────────────────────────────┐    │
│  │ 🟢 Project Alpha                                    │    │
│  │ Client: Acme Corp                                   │    │
│  │ Status: On Track | Health: 🟢 Green                │    │
│  │ Timeline: Jan 2026 - Apr 2026                       │    │
│  │                                                      │    │
│  │ Team: [John] [Sarah] [Mike] +2                      │    │
│  │                                                      │    │
│  │ Progress: ▓▓▓▓▓▓▓▓░░░░ 60%                          │    │
│  │                                                      │    │
│  │ Quick Links:                                        │    │
│  │ [Jira Board] [Figma File] [Drive Folder]           │    │
│  │                                                      │    │
│  │ [View Details →]                                     │    │
│  └────────────────────────────────────────────────────┘    │
│                                                              │
│  ┌────────────────────────────────────────────────────┐    │
│  │ 🟡 Project Beta                                     │    │
│  │ Status: At Risk | Health: 🟡 Yellow                │    │
│  │ Timeline: Dec 2025 - Mar 2026                       │    │
│  │ [View Details →]                                     │    │
│  └────────────────────────────────────────────────────┘    │
│                                                              │
│  Completed Projects (Archive)                               │
│  [View Completed Projects →]                                 │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

**Features:**

1. **Project Cards**
   - **Status indicator:** 🟢 Active, 🟡 At Risk, 🔴 Blocked, ✅ Complete
   - **Project name**
   - **Client name**
   - **Health score:** Green/Yellow/Red
   - **Timeline:** Start - End dates
   - **Team members:** Avatar stack with "+X more"
   - **Progress bar:** % complete
   - **Quick links:** Jira, Figma, Drive, GitHub
   - **Key deliverables:** Upcoming milestones
   - **Last updated:** Timestamp

2. **Filters & Views**
   - Filter by status: All, Active, Completed, On Hold, At Risk
   - Filter by client
   - Filter by team member
   - Sort by: Start date, End date, Health, Alphabetical
   - View as: Cards (default), List, Timeline/Gantt

3. **Project Detail Page (click "View Details")**
   ```
   ┌─────────────────────────────────────────────────────┐
   │  Project Alpha                                      │
   │  Client: Acme Corp                                  │
   │  Status: Active | Health: 🟢 Green                  │
   ├─────────────────────────────────────────────────────┤
   │                                                      │
   │  Overview:                                          │
   │  Building a customer portal for Acme Corp...        │
   │                                                      │
   │  Timeline:                                          │
   │  Start: Jan 15, 2026                                │
   │  End: Apr 30, 2026                                  │
   │  Duration: 15 weeks                                 │
   │                                                      │
   │  Team (5 members):                                  │
   │  • John Doe - Lead PM                               │
   │  • Sarah Lee - Senior Engineer                      │
   │  • Mike Chen - Lead Designer                        │
   │  • [+2 more]                                        │
   │                                                      │
   │  Key Deliverables:                                  │
   │  ✅ Discovery & Research (Done)                     │
   │  ✅ Design System (Done)                            │
   │  🔄 Development Sprint 1-3 (In Progress)            │
   │  ⏳ QA & Testing (Upcoming)                         │
   │  ⏳ Launch (Apr 2026)                               │
   │                                                      │
   │  Metrics:                                           │
   │  Velocity: 45 pts/sprint                            │
   │  Sprint progress: 60% complete                      │
   │  Bugs: 3 open, 12 resolved                          │
   │                                                      │
   │  Tools & Links:                                     │
   │  [Jira Board →] [Figma Design →]                    │
   │  [GitHub Repo →] [Drive Folder →]                   │
   │  [Client Slack Channel →]                           │
   │                                                      │
   │  Recent Updates:                                    │
   │  • Feb 3: Completed Sprint 2 planning               │
   │  • Feb 1: Design review with client                 │
   │  • Jan 28: Dev environment setup                    │
   │                                                      │
   └─────────────────────────────────────────────────────┘
   ```

4. **Completed Projects Archive**
   - All completed projects
   - Success metrics
   - Client testimonials
   - Case study links
   - Retrospective notes
   - Export as portfolio piece

5. **Success Stories / Case Studies**
   - Showcase best completed projects
   - Problem → Solution → Results format
   - Client quotes
   - Screenshots/demos
   - Team reflections
   - Lessons learned

6. **Project Templates**
   - New project kickoff template
   - Project charter template
   - Retrospective template
   - Client handoff checklist

**Data Model:**
```sql
CREATE TABLE projects (
  id TEXT PRIMARY KEY,
  name TEXT NOT NULL,
  client_name TEXT NOT NULL,
  description TEXT,
  status TEXT NOT NULL, -- active, at-risk, completed, on-hold
  health_score TEXT, -- green, yellow, red
  start_date DATE,
  end_date DATE,
  progress_percent INTEGER DEFAULT 0,
  
  -- Tool integrations
  jira_board_id TEXT,
  jira_url TEXT,
  figma_file_id TEXT,
  figma_url TEXT,
  github_repo TEXT,
  drive_folder_url TEXT,
  
  -- Metadata
  tags TEXT, -- JSON array
  created_by TEXT,
  created_at DATETIME,
  updated_at DATETIME
);

CREATE TABLE project_team_members (
  project_id TEXT,
  user_id TEXT,
  role TEXT, -- lead, member, contributor
  PRIMARY KEY (project_id, user_id)
);

CREATE TABLE project_updates (
  id TEXT PRIMARY KEY,
  project_id TEXT,
  update_text TEXT,
  updated_by TEXT,
  created_at DATETIME
);
```

---

## 8. API Integrations - Detailed Specifications

### THRESH CONFIRMED TECH STACK
The following APIs will be integrated based on Thresh's existing accounts:
- ✅ Figma
- ✅ Slack  
- ✅ Claude (Anthropic)
- ✅ GitHub
- ✅ Google Drive (Thresh Email)
- ✅ Client Jira (access through client accounts)

---

### 8.1 Google Workspace APIs (CONFIRMED - Thresh Email)

**Setup Required:**
- Google Cloud Console project creation
- Enable Drive API and Gmail API
- OAuth 2.0 consent screen configuration
- Service account creation for backend access

**Google Drive API:**
- **Endpoint:** `https://www.googleapis.com/drive/v3/files`
- **Scope:** `https://www.googleapis.com/auth/drive.readonly`
- **Use Cases:**
  - List recent files
  - Search across team documents
  - Get file metadata (name, modified date, owner)
  - Generate preview links
  - Quick access to shared folders
- **Rate Limit:** 1,000 requests per 100 seconds per user
- **Cost:** FREE

**Gmail API (Optional):**
- **Endpoint:** `https://gmail.googleapis.com/gmail/v1/users/me/messages`
- **Use Cases:**
  - Unread count in dashboard
  - Quick compose from portal
- **Rate Limit:** 250 quota units per user per second
- **Cost:** FREE

**Google Calendar API (Optional):**
- **Endpoint:** `https://www.googleapis.com/calendar/v3/calendars`
- **Use Cases:**
  - Team availability view
  - Upcoming meetings widget
- **Cost:** FREE

### 8.2 Figma API (CONFIRMED)

**Setup Required:**
- Generate Personal Access Token in Figma account settings
- Store token securely in environment variables
- Identify team ID and project IDs

**API Details:**
- **Base URL:** `https://api.figma.com/v1/`
- **Authentication:** Personal Access Token (Header: `X-Figma-Token`)
- **Key Endpoints:**
  - `GET /teams/{team_id}/projects` - List all team projects
  - `GET /projects/{project_id}/files` - Files in a project
  - `GET /files/{file_key}` - File metadata and version history
  - `GET /files/{file_key}/images` - Render nodes as images
  - `GET /files/{file_key}/comments` - File comments
- **Use Cases:**
  - Recent design files dashboard
  - Project thumbnails and previews
  - Design system component library access
  - Quick links to active files
  - Team activity feed
- **Rate Limit:** 400 requests per minute (shared across all tokens from your team)
- **Cost:** FREE (included with Figma account)

**Implementation Tips:**
- Cache file thumbnails to reduce API calls
- Use webhooks for real-time updates (if available in your Figma plan)
- Store file metadata locally to improve performance

### 8.3 Slack API (CONFIRMED)

**Setup Required:**
- Create Slack App in workspace
- Configure OAuth scopes and permissions
- Install app to workspace
- Generate OAuth tokens

**API Details:**
- **Base URL:** `https://slack.com/api/`
- **Authentication:** OAuth 2.0 (Bot Token and User Token)
- **Required Scopes:**
  - `channels:read` - List public channels
  - `groups:read` - List private channels
  - `users:read` - Access user info
  - `chat:write` - Send messages (for notifications)
  
- **Key Endpoints:**
  - `GET /conversations.list` - All channels user has access to
  - `GET /conversations.history` - Recent messages in channel
  - `GET /users.list` - Team member directory
  - `POST /chat.postMessage` - Send portal notifications to Slack
  - `GET /users.info` - User profile details
  
- **Use Cases:**
  - Channel quick links widget
  - Unread message count (if using User Token)
  - Team directory sync
  - Send portal notifications to Slack
  - Display recent announcements from #general
  
- **Rate Limit:** Tier 3 (50+ requests per minute for most methods)
- **Cost:** FREE (included with Slack workspace)
- **Webhooks:** Set up incoming webhooks for portal → Slack notifications

### 8.4 GitHub API (CONFIRMED)

**Setup Required:**
- Create GitHub OAuth App or GitHub App
- Configure callback URLs
- Generate Personal Access Tokens for service accounts

**API Details:**
- **Base URL:** `https://api.github.com/`
- **Authentication:** OAuth 2.0 or Personal Access Token
- **Required Scopes:**
  - `repo` - Repository access
  - `read:org` - Organization data
  - `user` - User profile data
  
- **Key Endpoints:**
  - `GET /user/repos` - User's repositories
  - `GET /orgs/{org}/repos` - Organization repositories
  - `GET /repos/{owner}/{repo}/pulls` - Pull requests
  - `GET /repos/{owner}/{repo}/commits` - Recent commits
  - `GET /repos/{owner}/{repo}/branches` - Branch list
  - `GET /search/issues` - Search issues and PRs
  
- **Use Cases:**
  - Active repositories dashboard
  - Open PR review queue
  - Recent commit activity
  - Repository health metrics
  - Code review assignments
  - Branch status indicators
  
- **Rate Limit:** 5,000 requests per hour (authenticated)
- **Cost:** FREE (included with GitHub account)
- **Webhooks:** Set up webhooks for real-time PR/commit notifications

### 8.5 Claude API (CONFIRMED - Anthropic)

**Setup Required:**
- Anthropic API Console account
- Generate API key
- Set up billing (pay-as-you-go)

**API Details:**
- **Base URL:** `https://api.anthropic.com/v1/messages`
- **Authentication:** API Key (Header: `x-api-key`)
- **Model:** `claude-sonnet-4-5-20250929` (recommended for cost/performance)
- **Alternative Models:**
  - `claude-opus-4-5-20251101` (highest quality, more expensive)
  - `claude-haiku-4-5-20251001` (fastest, cheapest)

**Use Cases:**
1. **AI Resume Evaluator**
   - Parse resume content
   - Compare against job descriptions
   - Generate scoring and recommendations
   
2. **Industry News Summarization**
   - Summarize articles into 2-3 sentences
   - Extract key topics and tags
   - Generate weekly digest compilations
   
3. **Benchmark Analysis**
   - Analyze trend data
   - Generate insights and predictions
   - Comparative analysis reports
   
4. **Smart Search**
   - Semantic search across knowledge base
   - Query understanding and reformulation
   
5. **Onboarding Assistant**
   - Answer new hire questions
   - Personalized learning recommendations

**Pricing (Claude Sonnet 4.5):**
- Input: $3.00 per million tokens
- Output: $15.00 per million tokens
- **Estimated Monthly Cost:** $50-150 depending on usage

**Rate Limits:**
- 50 requests per minute (tier 1)
- 100,000 tokens per minute
- Can request tier increases

**Best Practices:**
- Cache common responses to reduce API calls
- Use batch processing for news summarization
- Implement request queuing for rate limit management
- Monitor token usage to control costs

### 8.6 Client Jira Access (CONFIRMED)

**Setup Required:**
- Obtain OAuth credentials from client Jira instances
- Configure per-client authentication
- Map users to client accounts

**API Details:**
- **Base URL:** `https://[client-domain].atlassian.net/rest/api/3/`
- **Authentication:** OAuth 2.0 or API token (per client)
- **Key Endpoints:**
  - `GET /search` - JQL queries for issues
  - `GET /board/{boardId}/sprint` - Sprint information
  - `GET /issue/{issueKey}` - Issue details
  - `GET /project/{projectKey}` - Project metadata
  - `GET /dashboard` - Dashboard data
  
- **Use Cases:**
  - Client project dashboard in portal
  - My assigned tickets across all clients
  - Sprint burndown and velocity charts
  - Project health metrics per client
  - Multi-client workload view
  
- **Rate Limit:** 10,000 requests per hour per client instance
- **Cost:** FREE (using client Jira instances)

**Implementation Considerations:**
- Multi-tenancy: Support multiple client Jira instances
- Per-user OAuth: Each team member authorizes their client Jira access
- Data segregation: Ensure client data remains separated
- Caching: Cache project/board metadata to reduce API calls

### 8.7 News & Industry Intelligence APIs (RECOMMENDED)

Since you don't have these set up yet, here are the best options:

**RECOMMENDED: RSS Feed Aggregation (FREE)**
This is the most cost-effective approach for starting:

**Target Sources:**
1. **Hacker News RSS**
   - URL: `https://news.ycombinator.com/rss`
   - Focus: Tech, startups, AI/ML
   - Cost: FREE
   
2. **TechCrunch RSS**
   - URL: `https://techcrunch.com/feed/`
   - Focus: Tech industry news
   - Cost: FREE
   
3. **The Verge RSS**
   - URL: `https://www.theverge.com/rss/index.xml`
   - Focus: Tech, product, design
   - Cost: FREE
   
4. **Product Hunt Daily Digest**
   - URL: `https://www.producthunt.com/feed`
   - Focus: New products, tools
   - Cost: FREE
   
5. **Stratechery (Ben Thompson)**
   - URL: `https://stratechery.com/feed/`
   - Focus: Tech strategy, business
   - Cost: FREE (public posts)
   
6. **Google News (Custom Topic)**
   - URL: `https://news.google.com/rss/search?q=artificial+intelligence+consulting&hl=en-US`
   - Focus: Customizable by topic
   - Cost: FREE

**Implementation:**
- Use RSS parser library (Node: `rss-parser`, Python: `feedparser`)
- Fetch feeds every 1-4 hours
- Store articles in database
- Use Claude API to summarize and tag articles
- Filter by keywords: AI, ML, consulting, digital transformation, product

**ALTERNATIVE: News API (PAID but comprehensive)**
- **URL:** `https://newsapi.org/v2/`
- **Pricing:** 
  - Free tier: 100 requests/day (good for testing)
  - Developer: $449/month (unlimited)
- **Coverage:** 80,000+ sources globally
- **Endpoints:**
  - `/everything` - Search all articles
  - `/top-headlines` - Breaking news by category/source
  - `/sources` - Available news sources

**RECOMMENDATION:** Start with FREE RSS feeds + Claude API for summarization, then upgrade to News API if you need broader coverage.

### 8.8 Additional Free APIs to Consider

**Hacker News API (FREE)**
- **URL:** `https://hacker-news.firebaseio.com/v0/`
- **Endpoints:**
  - `/topstories.json` - Top stories IDs
  - `/item/{id}.json` - Story details
- **Use Case:** Tech community trending topics
- **Cost:** FREE

**Product Hunt API (FREE with limitations)**
- **URL:** `https://api.producthunt.com/v2/api/graphql`
- **Authentication:** OAuth 2.0
- **Use Case:** Daily new product launches
- **Cost:** FREE (500 requests/hour)

**Reddit API (FREE)**
- **Subreddits:** r/technology, r/artificial, r/consulting, r/ProductManagement
- **URL:** `https://www.reddit.com/r/artificial/hot.json`
- **Cost:** FREE
- **Use Case:** Community discussions and trends

---

## 9. AI-Powered Features (Detailed)

### 9.1 Thresh AI Resume Evaluator

**Functionality:**
- Upload resume (PDF, DOCX)
- Parse and extract: Skills, experience, education
- Compare against job description
- Generate scoring: Technical fit, cultural fit, experience level
- Provide hiring recommendation with reasoning
- Flag red flags or gaps

**Technical Implementation:**
- Document parsing: pdf-parse or docx library
- AI analysis: Claude API or OpenAI
- Scoring algorithm: Weighted criteria matching
- Storage: Candidate database with evaluations

**Prompt Engineering:**
```
Analyze this resume against our job description for [Role].
Evaluate on: Technical skills, Relevant experience, Culture fit, Communication.
Provide: Score (1-10), Strengths, Concerns, Recommendation.
```

### 9.2 Industry News Summarization

**Process:**
1. Fetch articles from News API / RSS feeds
2. Filter by relevance (AI/ML, consulting, product)
3. For each article:
   - Generate 2-3 sentence summary
   - Extract key topics/tags
   - Determine relevance score
4. Rank and display top articles
5. Weekly digest compilation

**Prompt for Summarization:**
```
Summarize this article in 2-3 sentences for a product team at a consulting firm.
Focus on: Key insights, Business implications, Actionable takeaways.
```

### 9.3 Benchmark Evolution Tracker

**Metrics to Track:**
- Product velocity (story points/sprint)
- Customer satisfaction (NPS, CSAT)
- Time to market
- Feature adoption rates
- Technical debt ratio

**AI Analysis:**
- Trend detection (improving/declining)
- Anomaly identification
- Predictive forecasting
- Comparative analysis vs. industry benchmarks

---

## 10. Development Phases & Roadmap

### Phase 1: Foundation (Weeks 1-4)
**Goal:** Core infrastructure and authentication

**Deliverables:**
- [ ] Set up Next.js project with TypeScript
- [ ] Implement authentication (NextAuth.js with SSO)
- [ ] Database schema design and setup (PostgreSQL + Prisma)
- [ ] Basic UI components library (shadcn/ui)
- [ ] User roles and permissions framework
- [ ] Home/Dashboard skeleton

### Phase 2: Tool Integration (Weeks 5-8)
**Goal:** Connect external tools

**Deliverables:**
- [ ] Google Workspace integration (Drive, Calendar)
- [ ] Jira API integration
- [ ] Figma API integration
- [ ] GitHub API integration
- [ ] Slack webhooks and notifications
- [ ] Tools Hub page with live data

### Phase 3: Core Features (Weeks 9-12)
**Goal:** Product Scorecard and Knowledge Base

**Deliverables:**
- [ ] Product Scorecard dashboard with metrics
- [ ] Knowledge Base with Wiki functionality
- [ ] Global search implementation
- [ ] Activity feed and notifications
- [ ] File upload and storage (S3)

### Phase 4: Onboarding & Brand (Weeks 13-16)
**Goal:** Onboarding automation and brand assets

**Deliverables:**
- [ ] Onboarding journey builder
- [ ] Role-based learning paths
- [ ] Brand Hub with asset library
- [ ] Template management system
- [ ] LinkedIn graphics generator
- [ ] Brand guidelines documentation

### Phase 5: AI Features (Weeks 17-20)
**Goal:** Industry intelligence and AI tools

**Deliverables:**
- [ ] News API integration
- [ ] AI-powered summarization (Claude/OpenAI)
- [ ] Industry Intelligence page
- [ ] Trend analysis dashboard
- [ ] AI Resume Evaluator
- [ ] Bookmark and sharing features

### Phase 6: Polish & Launch (Weeks 21-24)
**Goal:** Testing, optimization, and deployment

**Deliverables:**
- [ ] User acceptance testing (UAT)
- [ ] Performance optimization
- [ ] Mobile responsiveness
- [ ] Security audit
- [ ] Documentation and training materials
- [ ] Soft launch to core team
- [ ] Full production deployment
- [ ] Post-launch monitoring and iteration

---

## 11. Success Metrics & KPIs

### Adoption Metrics
- Daily Active Users (DAU) / Weekly Active Users (WAU)
- Feature adoption rate (% of users using each module)
- Time spent in portal (daily average)
- Login frequency

### Efficiency Metrics
- Average time to access a tool (baseline vs. post-launch)
- Onboarding completion time (days)
- Documentation search effectiveness (time to find answer)
- Reduction in duplicate work / questions

### Engagement Metrics
- News articles read per user
- Templates downloaded
- Knowledge base contributions
- Team directory usage

### Business Impact
- Onboarding cost reduction
- Tool switching time saved (hours/week)
- Employee satisfaction (NPS for portal)
- Knowledge retention (quiz scores)

---

## 12. Risks & Mitigation

### Technical Risks

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| API rate limits exceeded | High | Medium | Implement caching, request queuing, upgrade API tiers |
| Third-party API downtime | Medium | Low | Graceful degradation, cache data, show stale data with indicator |
| Security breach | Critical | Low | Regular audits, penetration testing, least-privilege access |
| Poor performance with scale | High | Medium | Load testing, CDN for assets, database optimization |
| Integration breaking changes | Medium | Medium | Version pinning, automated testing, fallback mechanisms |

### Product Risks

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| Low user adoption | High | Medium | User research, training sessions, gradual rollout |
| Feature bloat | Medium | High | Prioritization framework, MVP mindset, user feedback loops |
| Maintenance burden | Medium | Medium | Modular architecture, documentation, automated testing |
| Competing with existing tools | Low | Low | Focus on integration vs. replacement, unique value props |

---

## 13. Open Questions & Decisions Needed

### Technical Decisions
- [ ] **Frontend Framework:** Next.js vs. Nuxt.js vs. SvelteKit?
- [ ] **Database:** PostgreSQL vs. MySQL vs. MongoDB (for certain data)?
- [ ] **Hosting:** Vercel vs. AWS vs. self-hosted?
- [ ] **AI Provider:** Claude API vs. OpenAI vs. both?
- [ ] **Authentication:** NextAuth.js vs. Auth0 vs. Clerk?

### Product Decisions
- [ ] **Launch Scope:** Which features are P0 vs. P1 vs. P2?
- [ ] **User Roles:** What specific permissions for each role?
- [ ] **News Sources:** Which publications to prioritize?
- [ ] **Branding:** Custom theme or use company brand colors?
- [ ] **Mobile Strategy:** Responsive web app vs. native mobile app?

### Business Decisions
- [ ] **Budget:** What's allocated for third-party APIs and hosting?
- [ ] **Timeline:** Is 24-week timeline realistic or should we phase more aggressively?
- [ ] **Team:** Who's building this (internal team vs. contractors)?
- [ ] **Training:** How will we train users on the new portal?

---

## 14. Appendix

### A. Recommended Third-Party Services & Costs

**REVISED: Cloudflare-First Architecture (Per CEO Request)**

**Estimated Monthly Costs (10 users):**

| Service | Purpose | Cost |
|---------|---------|------|
| **Cloudflare Pages** | Hosting (Next.js/static) | FREE (unlimited requests on Free plan) |
| **Cloudflare Workers** | Serverless API functions | FREE (100k requests/day) or $5/month (10M requests) |
| **Cloudflare D1** | Edge database (SQLite) | FREE (5M reads, 100k writes/day) or $5/month |
| **Cloudflare R2** | Object storage (files/assets) | FREE (10GB storage) or ~$0.015/GB/month |
| **Cloudflare KV** | Key-value cache | FREE (100k reads, 1k writes/day) or $5/month |
| **Claude API** | AI features (summarization, resume eval) | ~$75-150/month |
| **Sentry** | Error monitoring | FREE (up to 5K events/month) |
| **Google Workspace APIs** | Already included with Thresh Email | FREE |
| **Figma API** | Already included with Figma account | FREE |
| **Slack API** | Already included with Slack workspace | FREE |
| **GitHub API** | Already included with GitHub | FREE |
| **RSS Feeds** | News aggregation | FREE |
| **Cloudflare Pro** (Optional) | Advanced features, better analytics | $20/month |
| **Total (Minimal)** | Using all free tiers | **~$75-150/month** (just Claude API!) |
| **Total (Recommended)** | With paid Workers/D1 for production | **~$90-170/month** |

**🎉 INCREDIBLE COST SAVINGS WITH CLOUDFLARE:**
- **Original estimate:** ~$650/month
- **Cloudflare architecture:** ~$75-170/month
- **Savings:** $480-575/month (73-88% reduction!)
- **Bonus:** Global edge network, DDoS protection, analytics all included

**Cloudflare Free Tier Limits (Generous!):**
- **Pages:** Unlimited requests, 500 builds/month
- **Workers:** 100,000 requests/day
- **D1:** 5M row reads/day, 100k row writes/day, 5GB storage
- **R2:** 10GB storage, 1M Class A operations/month
- **KV:** 100k reads/day, 1k writes/day
- **CDN:** Unlimited bandwidth (yes, really!)

**When to Upgrade:**
- Workers Paid ($5/mo): >100k requests/day or need longer CPU time
- D1 Paid ($5/mo): >5M reads or 100k writes per day
- R2 Paid: >10GB file storage
- Cloudflare Pro ($20/mo): Advanced analytics, image optimization, better support

**Alternative Database Options (if D1 limitations are hit):**
- **Neon (Serverless Postgres):** FREE tier (512MB, 3GB storage)
- **Supabase:** FREE tier (500MB, 2GB storage, 2GB bandwidth)
- **PlanetScale:** FREE tier (5GB storage, 1B row reads/month)

**News API Decision:**
- **Start with:** FREE RSS feeds + Claude summarization
- **Upgrade to News API ($449/month) if:** Need broader coverage or real-time breaking news alerts
- **Current recommendation:** RSS feeds are sufficient for your use case

### B. Example User Stories

**As a Product Manager:**
- I want to see all my active projects' health status at a glance so I can prioritize my focus.
- I want to quickly access the latest product templates so I can create deliverables faster.
- I want to stay updated on AI trends so I can advise clients effectively.

**As a New Hire:**
- I want a clear onboarding path so I know what's expected in my first month.
- I want easy access to all team tools so I don't waste time asking for links.
- I want to understand Thresh's brand guidelines so I can create on-brand work.

**As a Designer:**
- I want to access brand assets quickly so I can maintain consistency.
- I want to see recent Figma files so I can continue where I left off.
- I want to share my work with the team easily.

**As Leadership:**
- I want to see team productivity metrics so I can make informed decisions.
- I want to track onboarding completion so I can ensure new hires are set up for success.
- I want to manage user permissions so I can control access to sensitive data.

### C. Glossary

- **RBAC:** Role-Based Access Control
- **SSO:** Single Sign-On
- **CRUD:** Create, Read, Update, Delete
- **API:** Application Programming Interface
- **OAuth:** Open Authorization
- **JWT:** JSON Web Token
- **REST:** Representational State Transfer
- **ORM:** Object-Relational Mapping
- **CI/CD:** Continuous Integration/Continuous Deployment

---

## Next Steps

1. **Review & Refine:** Share this PRD with stakeholders for feedback
2. **Prioritization Workshop:** Determine P0/P1/P2 features for launch
3. **Technical Spike:** Evaluate framework options with small POC
4. **Design Kickoff:** Create wireframes and mockups for key pages
5. **Development Sprint Planning:** Break down Phase 1 into 2-week sprints
6. **API Account Setup:** Register for required third-party services
7. **Security Review:** Engage security team for architecture review

---

**Document Version:** 1.0  
**Last Updated:** February 6, 2026  
**Owner:** Product Team, Thresh Consulting  
**Next Review:** March 6, 2026
