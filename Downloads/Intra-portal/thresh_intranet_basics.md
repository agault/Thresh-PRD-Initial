## MVP:
* Landing page - Thresh metrics (tbd), News API- RSS FEED (Tech news [AI, digital products])
    + NewsAPI (has a free tier, easy integration) + Hacker News API (completely free). 
    + If no API Convert RSS feeds from TechCrunch, VentureBeat, MIT Technology Review, The Verge into JSON
* House all SOPs
    + Searchable knowledge base
    + Markdown files or simple CMS
    + Organized by category/tags
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

**Operational Optics:** High-level "Product Scorecard" (Health, Velocity, Success).
* KPI / OKR tracking
* Project Health (Green/Yellow/Red)
* Team Velocity (Sprint progress)
* Recent Wins
* (Placeholder metrics for MVP)

**Discovery Feed:** API-driven widget for Industry Tech News & Digital Consulting trends.
* NewsAPI + Hacker News API (cached daily)
* Filterable by topic: AI, Digital Products, Design, Development
* Click to read full article

**Quick Links:**
* Jump to: Tools & Apps, SOPs, Projects, Org Chart


____

### 2. SOPs (The Knowledge Base)
"The Thresh Way": Onboarding documentation on what it means to be "Product" at Thresh.

Resource Library: Templates, Brand Guidelines, and the Styleguide.

Brand Assets: Thresh-branded decks and the LinkedIn Welcome Graphic generator.

Training Vault: Standard Operating Procedures for internal workflows.

____

### 3. Tools & Apps (The Integration Hub)
**Centralized Access:** One-click login/entry to all external SaaS.

#### Page Layout:
* Grid of tool cards (like app icons)
* Each card shows:
    + Tool logo
    + Tool name
    + One-line description
    + **"Launch"** button (opens tool in new tab)
    + **"View Details"** button (expands full info)

#### Search & Filter:
* Search bar for finding tools
* Filter by category: Design, Development, Communication, AI, Security, Productivity
* Sort: Alphabetical, Most Used, Recently Added

____

#### Tool Card Details (Click to Expand):

**1. What It Is**
* Full description of the tool
* Key capabilities

**2. Why We Use It**
* Business justification
* Primary use cases at Thresh

**3. Who Has Access**
* Roles: All, Designers only, Devs only, etc.
* Admin/owner contact
* License count (X/10 used)

**4. How to Login** 🔐
* **For SSO tools:**
    + Badge: "Sign in with Google Workspace"
    + Instructions: "Click 'Sign in with Google' and use your @threshconsulting.com email"
* **For shared accounts:**
    + Username: team@threshconsulting.com
    + Password: **[Link to 1Password vault]** ← NEVER show password in plain text
* **For individual accounts:**
    + "Request access from [admin email]"

**5. Security Guardrails** ⚠️
* **✅ DO:**
    + Use for approved work purposes
    + Enable 2FA on your account
    + Keep credentials secure
    + Report suspicious activity
* **❌ DON'T:**
    + Share login credentials
    + Use for personal projects
    + Upload client confidential data (tool-specific)
    + Disable security features

**6. Tool Details**
* Cost: $X/month (admin view only)
* Integrations: Slack, Google Drive, etc.
* Resources: Official docs, internal training, usage guide

____

#### Tools to Include (MVP):

**Figma**
* **Category:** Design
* **Access:** Designers (edit), PMs/Devs (view/comment)
* **Login:** SSO via Google
* **✅ DO:**
    + Use for client projects and internal design work
    + Enable 2FA
    + Organize files in designated project folders
    + Use comments for feedback
* **❌ DON'T:**
    + Share login credentials
    + Download client files to personal devices without approval
    + Install unapproved plugins
    + Share client work publicly without approval

**Slack**
* **Category:** Communication
* **Access:** All team members
* **Login:** SSO via Google
* **✅ DO:**
    + Use threads to keep conversations organized
    + Set status when away or in meetings
    + Keep client work in private project channels
    + Use reactions for quick acknowledgments
* **❌ DON'T:**
    + Share client confidential info in public channels
    + Use @channel for non-urgent messages
    + Post passwords, API keys, or credentials
    + Respond to suspicious DMs

**Claude Pro (Team)**
* **Category:** AI
* **Access:** All team members
* **Login:** Team account (team@threshconsulting.com + individual SSO)
* **✅ DO:**
    + Use for drafting, editing, research
    + Anonymize/sanitize data before input
    + Review and fact-check all AI outputs
    + Use Projects feature to organize work
* **❌ DON'T:**
    + ⚠️ **CRITICAL:** NEVER input client confidential data, PII, proprietary info, unreleased products
    + Never paste API keys, passwords, credentials
    + Never input code with sensitive business logic
    + Don't present AI work as original research without verification

**GitHub**
* **Category:** Development
* **Access:** Devs (full), Designers/PMs (read)
* **Login:** Individual GitHub + SSO
* **✅ DO:**
    + Enable 2FA (required)
    + Use SSH keys or Personal Access Tokens
    + Code review via Pull Requests
    + Commit frequently with clear messages
    + Document code with README
* **❌ DON'T:**
    + ⚠️ **CRITICAL:** NEVER commit API keys, passwords, or secrets
    + Never force push to main/production branches
    + Never commit client proprietary code without rights
    + Never share SSH keys or tokens

**Google Workspace**
* **Category:** Productivity
* **Access:** All team members
* **Login:** Individual Google account (@threshconsulting.com)
* **✅ DO:**
    + Enable 2FA (required)
    + Organize files in shared team/client folders
    + Use "Internal sharing" for company docs
    + Use professional email signatures
* **❌ DON'T:**
    + Use "Anyone with link" for sensitive documents
    + Forward company emails to personal email
    + Store personal files on company Drive
    + Click suspicious links (report phishing)

**1Password**
* **Category:** Security
* **Access:** All team members (required)
* **Login:** Individual account + team vault
* **✅ DO:**
    + Store ALL work passwords in 1Password
    + Use 1Password to generate strong passwords (20+ chars)
    + Enable biometric unlock (Face ID, fingerprint)
    + Keep master password secure and unique
* **❌ DON'T:**
    + Share your master password with anyone (even IT)
    + Write down master password
    + Reuse passwords across services
    + Store passwords in browsers or plain text
____

### 4. Org Chart & Teams (The People)
Engineering, Design & Product Team: Bio, roles, and contact info.

Eminence Plan: Tracking team demos and public-facing thought leadership.

____

### 5. Projects (The Delivery)
**Project Health:** Live status of current builds.
* Green/Yellow/Red health indicators
* Recent updates
* Team assigned

**The "Stack" per Project:** Which tech/tools are assigned to which initiative.
* Tech stack used
* Team members
* Links: Figma files, GitHub repos, Jira board, Slack channel

**Archives:** Record of past demos and project outcomes.
* Completed projects
* Lessons learned
* Reusable components 

**Features:**
* Filter by: Status, Client, Team
* Project detail pages (click to expand)
* Jira integration (post-MVP)

____
____

## Internal Tech Architecture (Mental Model)

#### Rough Data Logic
**CRUD Rules:** General users = Read Only. Leadership/Admin = Edit/Create.

**Data Pulls:** Needs to talk to Jira (for Project Health) and external News APIs (for Discovery).

#### Authentication & Permissions
* Google Workspace SSO (@threshconsulting.com)
* General Users: Read-only access to all pages
* Leadership/Admin: Full CRUD (Create, Read, Update, Delete)

#### Data Storage
* Cloudflare D1 (SQLite) for structured data (tools, users, projects)
* Cloudflare KV for caching (news feed, frequently accessed)
* Markdown files for SOPs (in repo, version controlled)

#### External Integrations
* NewsAPI + Hacker News API (server-side calls via Cloudflare Workers)
* RSS to JSON fallback (TechCrunch, VentureBeat, MIT Tech Review, The Verge)
* Jira API (post-MVP for project health)
* LinkedIn API (post-MVP for team profiles)

#### Deployment
* Cloudflare Pages for hosting
* GitHub for version control
* CI/CD: Auto-deploy on push to main

____
____

## Tech Stack Recommendation

____
____

## Key Takeaways

### For Tools & Apps Page:
1. **One-click launch** to every tool
2. **Login info accessible** but secure (link to 1Password, never plain text)
3. **Guardrails front and center** (DO's and DON'Ts for every tool)
4. **Admin can edit** everything via CRUD panel
5. **Search and filter** for easy discovery

### For Overall Portal:
1. Keep it **simple and fast** (POC that can be iterated)
2. **Cloudflare-first** architecture
3. **Google SSO** for authentication
4. **Role-based access** (read-only vs. CRUD)
5. **Mobile-friendly** from day one

____
____

## Next Steps

1. ✅ Finalize tech stack (Next.js + Cloudflare)
2. ✅ Create GitHub repo
3. ✅ Set up Cloudflare Pages project
4. ✅ Design mockups in Figma (Tools & Apps page priority)
5. ✅ Start with Tools & Apps page (highest value, easiest to demo)
6. ✅ Iterate based on team feedback

____
____