# Toloka Platform - System Architecture Documentation

**Version**: 2.1
**Last Updated**: 2025-11-24 14:31:47 UTC
**Based on**: Tloka_UX_UI_2025.pdf + Enklava.co Design System

> **Documentation Source of Truth**: [https://github.com/PawelSroczynski/toloka/](https://github.com/PawelSroczynski/toloka/platform-docs)  
> (Architecture PDFs, SOP templates, and quality mandates are mirrored there.)

---

## Table of Contents

1. [Platform Overview & Philosophy](#platform-overview--philosophy)
   - [Platform Purpose](#platform-purpose)
   - [Core Philosophy](#core-philosophy)
   - [Core Features](#core-features)
2. [Three-Role System](#three-role-system)
   - [Host/Project Owner (Gospodarz)](#1-hostproject-owner-gospodarz)
   - [Student/Volunteer (Tłoker)](#2-studentvolunteer-tłoker)
   - [Master/Expert/Mentor (Mistrz)](#3-masterexpertmentor-mistrz)
   - [Triadic Value Flow](#triadic-value-flow)
3. [Information Architecture](#information-architecture)
   - [Site Structure](#site-structure)
   - [Page Hierarchy](#page-hierarchy)
4. [User Flows](#user-flows)
   - [Flow 1: Student/Volunteer - Find and Apply](#flow-1-studentvolunteer-tłoker---find-and-apply-to-project)
   - [Flow 2: Host - Create Project](#flow-2-host-gospodarz---create-project-and-build-team)
   - [Flow 3: Master/Expert - Accept Invitation](#flow-3-masterexpert-mistrz---accept-invitation-and-provide-expertise)
   - [Flow 4-7: Additional Flows](#user-flows)
5. [Technical Architecture](#technical-architecture)
   - [System Architecture Overview](#system-architecture-overview-self-hosted)
   - [Technology Stack](#technology-stack)
   - [Folder Structure](#folder-structure)
6. [Data Models](#data-models)
   - [Core Entities](#core-entities)
   - [Entity Relationships](#entity-relationships)
7. [API Architecture](#api-architecture)
   - [RESTful API Endpoints](#restful-api-endpoints)
   - [API Response Formats](#api-response-formats)
   - [Authentication & Authorization](#authentication--authorization)
8. [Security & Performance](#security--performance)
   - [Security Measures](#security-measures)
   - [Performance Optimizations](#performance-optimizations)
   - [Scalability Considerations](#scalability-considerations)
9. [Senior Architect Code Quality Mandate](#senior-architect-code-quality-mandate)
   - [Purpose](#purpose)
   - [Core Requirements](#core-requirements)
10. [Design System](#design-system)
    - [Color Palette](#color-palette)
    - [Typography](#typography)
    - [Spacing System](#spacing-system)
    - [Component Library](#component-library)
11. [Implementation Guide for AI Agents](#implementation-guide-for-ai-agents)
    - [Prerequisites & Initial Setup](#prerequisites--initial-setup)
    - [Environment Configuration](#environment-configuration)
    - [Database Setup & Migrations](#database-setup--migrations)
    - [Supabase Self-Hosting Configuration](#supabase-self-hosting-configuration)
    - [Authentication & SSO Configuration](#authentication--sso-configuration)
    - [Discourse Integration Setup](#discourse-integration-setup)
    - [Testing & Quality Assurance](#testing--quality-assurance)
    - [Deployment Checklist](#deployment-checklist)
    - [Common Issues & Troubleshooting](#common-issues--troubleshooting)
    - [Monitoring & Maintenance](#monitoring--maintenance)

---

## Platform Overview & Philosophy

**Quick Links**: [Platform Purpose](#platform-purpose) | [Core Philosophy](#core-philosophy) | [Core Features](#core-features)

### Platform Purpose

Toloka digitizes the Slavic tradition of **communal swarm aid (gromadna pomoc)** into a transparent system where collective labor, know-how, and materials flow freely. It delivers four promises:

1. **Scout-inspired skill development** – Every project is a live training ground with mentors, badges, and progression paths.
2. **Living documentation** – SOPs, flowcharts, BOMs, and case studies archive each build so the next group starts smarter.
3. **Know-how exchange** – Hosts, volunteers, and masters trade expertise through structured forums, reviews, and curated libraries.
4. **Lower barriers to building** – Cooperative effort, shared assets, and communal financing make regenerative homes attainable without traditional capital.

By weaving these commitments into every Toloka, the platform keeps the ancestral social contract alive while accelerating modern, regenerative construction.

### Core Philosophy

- **Regenerative design** - Building practices that restore ecosystems
- **Community-driven learning** - Peer-to-peer knowledge exchange
- **Accessible education** - Democratizing natural building skills
- **Resource sharing** - Optimizing use of materials, space, and expertise

### Core Features

1. **Project Discovery & Creation** - Find and list natural building projects (Toloki/Tłoki)
2. **Application & Recruitment** - Match skills with needs, build teams
3. **Expert Integration** - Connect with mentors and masters (Mistrz)
4. **Knowledge Base** - SOP builder, flowcharts, BOM templates, case studies
5. **Project Planning** - BOM tracking, Gantt charts, logistics automation
6. **Skill Tree & Gamification** - Constellation-style progression map, attribute radar charts, verified badges
7. **Community & Resources** - Forum discussions, publications library

---

**Navigation**: [↑ Table of Contents](#table-of-contents) | [Next: Three-Role System →](#three-role-system)

---

## Three-Role System

**Quick Links**: [Host/Project Owner](#1-hostproject-owner-gospodarz) | [Student/Volunteer](#2-studentvolunteer-tłoker) | [Master/Expert](#3-masterexpertmentor-mistrz) | [Triadic Value Flow](#triadic-value-flow)

The platform operates on a **triadic value exchange model**, recognizing three distinct participant roles:

### 1. Host/Project Owner (Gospodarz)

**Profile**: Resource Provider

**Characteristics**:

- Possesses material resources (land, materials, infrastructure)
- Faces labor shortage for project completion
- Offers space for experimentation and learning
- Provides a "practical testing ground" (poligon doświadczalny)

**What They Offer**:

- Physical workspace and building site
- Construction materials
- Accommodation and food
- Real-world learning environment
- Project guidance

**What They Need**:

- Labor for project execution
- Skills and energy from participants
- Support in realizing their vision

**Platform Role**: Project creator and team manager

---

### 2. Student/Volunteer (Tłoker)

**Profile**: Skill Seeker

**Characteristics**:

- Has time and willingness to learn
- Lacks financial resources for expensive training
- Seeks practical, hands-on experience
- Cannot access traditional educational pathways

**What They Offer**:

- Physical labor and energy
- Time commitment
- Enthusiasm and dedication
- Fresh perspectives

**What They Need**:

- Practical skills development
- Hands-on learning opportunities
- Access to experts and materials
- Community and connection

**Value Exchange**: Labor for Skills

**Platform Role**: Project participant and learner

---

### 3. Master/Expert/Mentor (Mistrz)

**Profile**: Knowledge Provider

**Characteristics**:

- Possesses advanced expertise and know-how
- Wants to share knowledge (paid or exchange)
- Ensures professional quality in projects
- Elevates educational value of events

**What They Offer**:

- Expert guidance and mentorship
- Technical knowledge and best practices
- Quality control and professional standards
- Specialized skills training
- Problem-solving expertise

**What They Receive**:

- Financial compensation (optional)
- Other forms of value exchange
- Teaching satisfaction
- Network expansion
- Community contribution

**Platform Role**: Advisor, teacher, quality assurance

**Integration Model**:

- Can be hired by Gospodarz for specific projects
- May offer workshops or training sessions
- Provides consultation and technical oversight
- Certifies skills or validates work quality

---

### Triadic Value Flow

```text
                    ┌─────────────┐
                    │   Host      │
                    │ (Gospodarz) │
                    │             │
                    │ • Resources │
                    │ • Space     │
                    │ • Materials │
                    └──────┬──────┘
                           │
            ┌──────────────┴──────────────┐
            │                             │
      Provides:                      Provides:
   Site, Materials, Food          Payment/Value
            │                             │
            ▼                             ▼
    ┌─────────────┐              ┌─────────────┐
    │ Volunteer   │◄─────────────│   Expert    │
    │  (Tłoker)   │  Teaching    │  (Mistrz)   │
    │             │  Mentoring   │             │
    │ • Labor     │              │ • Knowledge │
    │ • Time      │              │ • Expertise │
    └─────────────┘              └─────────────┘
         Receives:                    Provides:
    Skills & Experience          Expert Guidance
```

**Key Relationships**:

- **Host (Gospodarz) ↔ Student/Volunteer (Tłoker)**: Resources/Space for Labor/Energy
- **Student/Volunteer (Tłoker) ↔ Master/Expert (Mistrz)**: Labor/Learning for Teaching/Mentoring
- **Host (Gospodarz) ↔ Master/Expert (Mistrz)**: Payment/Value for Expert Services
- **Triangle Effect**: All three roles benefit from each other's participation

---

**Navigation**: [← Previous: Platform Overview](#platform-overview--philosophy) | [↑ Table of Contents](#table-of-contents) | [Next: Information Architecture →](#information-architecture)

---

## Information Architecture

**Quick Links**: [Site Structure](#site-structure) | [Page Hierarchy](#page-hierarchy)

### Site Structure

```text
Toloka Platform (Tłoka)
│
├── Public Pages
│   ├── Homepage
│   │   ├── Hero (Two-path: Tłoker vs Gospodarz)
│   │   ├── Role Explanation (3 roles)
│   │   ├── Recent Projects
│   │   ├── Testimonials
│   │   ├── Forum Preview
│   │   └── Publications
│   │
│   ├── About / Czym jest tłoka (What is Toloka)
│   ├── Library / Biblioteka
│   └── Contact / Kontakt
│
├── Project Discovery
│   ├── Find Toloka / Znajdź tlokę (Find Toloka)
│   │   ├── Filters (category, date, location)
│   │   ├── List View
│   │   ├── Map View
│   │   └── Search
│   │
│   └── Project Detail
│       ├── Overview
│       ├── Required Skills
│       ├── Skill Yield (Zdobycze) - Shows XP and nodes unlockable by this project
│       ├── Host Profile
│       ├── Additional Info
│       ├── FAQ
│       └── Application CTA
│
├── User Dashboards
│   ├── My Toloki / Moje Tłoki (All roles)
│   │   ├── As Host (Gospodarz) - Hosting
│   │   ├── As Student/Volunteer (Tłoker) - Participating
│   │   └── As Master/Expert (Mistrz) - Mentoring
│   │
│   ├── Host Dashboard (Gospodarz)
│   │   ├── Create Project (7-step wizard)
│   │   ├── Manage Projects
│   │   ├── Recruitment Management
│   │   └── Expert Invitations
│   │
│   ├── Student/Volunteer Dashboard (Tłoker)
│   │   ├── Applied Projects
│   │   ├── Application Status
│   │   ├── Completed Projects
│   │   └── My Skill Tree (Moje Drzewo) - Constellation view, Radar stats, Badge inventory
│   │
│   └── Master/Expert Dashboard (Mistrz)
│       ├── Invitations
│       ├── Active Projects
│       ├── Project History
│       └── Profile Management
│
├── Application Process
│   ├── Application Form
│   ├── Skill Assessment
│   └── Status Tracking
│
├── Community
│   ├── Forum
│   │   ├── Topics
│   │   └── Discussions
│   │
│   ├── Knowledge Base / Dokumentacja
│   │   ├── SOP Library
│   │   ├── Flowcharts
│   │   ├── Bill of Materials
│   │   └── Case Studies
│   │
│   └── Publications
│       └── Resource Library
│
└── User Management
    ├── Authentication
    ├── Profile
    ├── Settings
    └── Notifications
```

---

### Page Hierarchy

#### 1. Homepage

- **Purpose**: Introduce platform, drive users to primary actions
- **Key Sections**: Dual hero (Tłoker/Gospodarz), role explanation, project showcase
- **CTAs**: "Find Toloka (Znajdź tlokę)", "Create Toloka (Zwołaj tlokę)"

#### 2. Find Toloka Page (Znajdź tlokę)

- **Purpose**: Browse and filter available projects
- **Features**: Multi-filter, list/map toggle, search
- **Flows To**: Project detail, application form

#### 3. Project Detail Page

- **Purpose**: Comprehensive project information
- **Sections**:
  - Project overview and images
  - Required skills with importance ratings
  - Accommodation, food, logistics
  - Host profile
  - Expert involvement (if any)
  - FAQ
  - Application count
- **CTAs**: Apply, save, share, contact host

#### 4. Application Form

- **Purpose**: Submit interest in project
- **Fields**:
  - Skill self-assessment
  - Motivation statement
  - Additional information
  - Contact details
- **Validations**: Required skills, minimum detail level

#### 5. Create Toloka Wizard (7 Steps) (Stwórz tlokę)

- **Purpose**: Guided project creation for Hosts (Gospodarz)
- **Steps**:
  1. Basic info (name, type, location)
  2. Dates (project timeline, deadlines)
  3. Accommodation (options and details)
  4. Skills (requirements with importance levels, optional expert request)
  5. Additional (schedule, photos, FAQ)
  6. Confirmation (review all info)
  7. Submit (publish project)
- **Features**: Save draft, preview at any step

#### 6. Recruitment Management

- **Purpose**: Review applicants and build team
- **Layout**: Two-column
  - Left: All applicants (filterable, expandable)
  - Right: Selected team
- **Features**: View full applications, add/remove from team, messaging

#### 7. Master/Expert Dashboard (Mistrz)

- **Purpose**: Manage expert engagements
- **Sections**:
  - Invitations (pending requests)
  - Active projects (current mentoring)
  - History (completed projects)
  - Profile (specializations, rates, portfolio)
- **Features**: Accept/reject invitations, communicate with hosts, track projects

#### 8. My Toloki Page (Moje Tłoki)

- **Purpose**: Central hub for user's project involvement
- **Organization**: Grouped by role
  - Host (Gospodarz): Projects I'm hosting
  - Student/Volunteer (Tłoker): Projects I've applied to / participating in
  - Master/Expert (Mistrz): Projects I'm mentoring
- **Status Indicators**: Draft, open, in recruitment, active, completed

#### 9. Knowledge Base Hub

- **Purpose**: Single entry point for documentation—SOPs, flowcharts, BOM templates, and case studies.
- **Features**: Category filters (technique, material, difficulty), search, "bookmark for later," usage analytics, Discourse topic link (via DiscourseLink), print/PDF export.
- **Integrations**: Pulls live data from completed Toloki (Tłoki), surfaces scout-style badges earned, and links back to project detail pages.

#### 10. SOP Builder

- **Purpose**: Guided authoring environment for masters and hosts to document repeatable steps.
- **Features**: Step ordering, media attachments, materials/tools lists, safety callouts, Discourse topic link per step (via DiscourseLink), version history with approvals.
- **Access**: Master/Expert (Mistrz) - full control, Host (Gospodarz) - draft + request review, Student/Volunteer (Tłoker) - suggest edits, comment.

#### 11. Flowchart & BOM Tools

- **Purpose**: Visualize decision trees and logistics while tracking quantities and costs.
- **Features**: Drag-and-drop flowchart nodes, BOM line items with supplier metadata, sync to project timeline, export to Gantt view.
- **Planning Hooks**: Each BOM item can spawn procurement tasks; each flowchart node can map to skill badges.

#### 12. Documentation Repository (GitHub Mirror)

- **Purpose**: Provide an auditable history of platform architecture, SOP templates, and quality mandates.
- **Features**: Markdown sources, Mermaid diagrams, contribution guide referencing `SENIOR_ARCHITECT_PROMPT.md`.
- **Workflow**: Docs PRs require technical review, auto-publish to in-app viewer, and create/update Discourse topics (via Discourse API) for community discussions and edits.

---

**Navigation**: [← Previous: Information Architecture](#information-architecture) | [↑ Table of Contents](#table-of-contents) | [Next: User Flows →](#user-flows)

---

## User Flows

**Quick Links**: [Flow 1: Student/Volunteer](#flow-1-studentvolunteer-tłoker---find-and-apply-to-project) | [Flow 2: Host](#flow-2-host-gospodarz---create-project-and-build-team) | [Flow 3: Master/Expert](#flow-3-masterexpert-mistrz---accept-invitation-and-provide-expertise) | [Flow 4-7: Additional Flows](#flow-4-expert-request-hostgospodarz-initiates)

### Flow 1: Student/Volunteer (Tłoker) - Find and Apply to Project

```text
START → Homepage
  ↓
  Click "Find Toloka (Znajdź tlokę)"
  ↓
Search/Filter Projects
  • Select categories
  • Set date range
  • Choose location
  • Toggle list/map view
  ↓
Browse Results
  ↓
Click Project Card
  ↓
View Project Detail
  • Read description
  • Check requirements
  • Review host profile
  • Assess feasibility
  ↓
Decision Point: Apply?
  │
  ├─ NO → Continue browsing or exit
  │
  └─ YES → Click "Zgłoś swój udział"
      ↓
  Fill Application Form
      • Self-assess skills
      • Write motivation
      • Add additional info
      ↓
  Preview Application
      ↓
  Submit Application
      ↓
  Confirmation
      ↓
  Track in "My Toloki (Moje Tłoki)"
      ↓
  Wait for Recruitment Results
      ↓
  ACCEPTED → Prepare for project
  REJECTED → Continue searching
```

---

### Flow 2: Host (Gospodarz) - Create Project and Build Team

```text
START → Homepage
  ↓
  Click "Create Toloka (Zwołaj tlokę)"
  ↓
7-Step Wizard:
  ↓
STEP 1: Info wstępne
  • Project name
  • Type
  • Location (with map picker)
  • Description
  • Format (volunteer/paid)
  • Number of participants
  ↓
STEP 2: Daty
  • Start/end dates
  • Application deadline
  • Results announcement date
  ↓
STEP 3: Nocleg
  • Accommodation type(s)
  • Details for each option
  ↓
STEP 4: Umiejętności
  • Add skills (min 2)
  • Set importance (1-6 scale)
  • Describe each skill
  • Optional: Request Master/Expert (Mistrz)
    - Specialization
    - Payment type
    - Description
  ↓
STEP 5: Dodatkowe
  • Daily schedule
  • Additional info
  • Upload photos
  • Add FAQ
  ↓
STEP 6: Potwierdzenie
  • Review all information
  • Make edits if needed
  ↓
STEP 7: Zgłoś
  • Final submission
  • Project goes live
  ↓
Project Published
  ↓
Applications Start Coming In
  ↓
Review Applications (Recruitment Phase)
  • View in "Zarządzaj rekrutacją"
  • Two-column layout:
    - Suggested applicants
    - Your team
  • Expand cards to see details
  • Evaluate skills, motivation
  • Add best matches to team
  ↓
Team Complete
  ↓
Announce Results
  ↓
Communicate with Accepted Students/Volunteers (Tłokers)
  ↓
Optional: Coordinate with Master/Expert (Mistrz) (if invited)
  ↓
Project Begins
  ↓
END (or → Project History)
```

---

### Flow 3: Master/Expert (Mistrz) - Accept Invitation and Provide Expertise

```text
START → Notification (Invitation Received)
  ↓
Log into Master/Expert Dashboard (Mistrz)
  ↓
Navigate to "Zaproszenia" tab
  ↓
View Invitation Card
  • Project title & description
  • Host information
  • Dates & duration
  • Payment/exchange terms
  • Required specialization
  ↓
Click "Zobacz szczegóły"
  ↓
Review Full Project Details
  • Scope of work
  • Expected deliverables
  • Student/Volunteer (Tłoker) count
  • Building type/technique
  ↓
Evaluation:
  • Does it match my expertise?
  • Am I available?
  • Is compensation fair?
  • Is it interesting?
  ↓
Decision Point:
  │
  ├─ REJECT
  │   → Click "Odrzuć"
  │   → Invitation removed
  │   → END
  │
  └─ ACCEPT
      → Click "Przyjmij zaproszenie"
      ↓
  Invitation → "Aktywne projekty"
      ↓
  Communicate with Host (Gospodarz)
      • Clarify expectations
      • Plan teaching schedule
      • Confirm logistics
      • Discuss payment
      ↓
  Prepare for Project
      • Develop lesson plans
      • Prepare materials
      • Review project specs
      ↓
  Participate in Project
      • Provide expert guidance
      • Conduct workshops
      • Mentor Students/Volunteers (Tłokers)
      • Ensure quality standards
      • Troubleshoot issues
      ↓
  Project Completion
      ↓
  Receive Compensation
      ↓
  Get Reviewed by Host (Gospodarz)
      ↓
  Project → "Historia"
      ↓
  Add to Portfolio
      ↓
  END
```

---

### Flow 4: Expert Request (Host/Gospodarz Initiates)

```text
START → Creating/Editing Project (Step 4)
  ↓
Check "I want to invite a Master/Expert (Chcę zaprosić Mistrza)"
  ↓
Expert Section Expands:
  • Select specialization
  • Describe needs
  • Choose payment type (paid/exchange)
  ↓
Complete Project Creation
  ↓
Project Published with Expert Flag
  ↓
System Actions:
  • Searches for matching Master/Expert (Mistrz) profiles
  • Sends notifications to qualified experts
  • Displays invitation in Master/Expert (Mistrz) dashboards
  ↓
Master/Expert (Mistrz) Responds (see Flow 3)
  ↓
If ACCEPTED:
  • Expert appears in project details
  • Host (Gospodarz) notified
  • Direct communication enabled
  ↓
If REJECTED or NO RESPONSE:
  • Host (Gospodarz) notified
  • Option to invite another expert
  • Option to proceed without expert
  ↓
END
```

### Flow 5: Knowledge Creation & Documentation

```text
START → Project completed or milestone reached
  ↓
Click "Document this Toloka (Tłoka)"
  ↓
Choose template:
  • SOP
  • Flowchart
  • Bill of Materials
  • Case Study
  ↓
SOP path:
  → Add ordered steps (title, description, media, safety, skills)
  → Attach materials & tools per step
  → Link to BOM lines and create Discourse topic (if not exists)
  → Submit for review → publish
Flowchart path:
  → Drag nodes (process/decision/start/end)
  → Connect dependencies, tag badges/skills
  → Embed in SOP + publish
BOM path:
  → Add line items (qty, unit, supplier, cost, status)
  → Link to procurement tasks + Gantt segments
  → Export for logistics team
  ↓
Artifact published to Knowledge Base + mirrored to GitHub
  ↓
Discourse topic created/updated for Q&A (via Discourse API)
  ↓
END
```

### Flow 6: Learning from Documentation

```text
START → Student/Volunteer (Tłoker) preparing to apply
  ↓
Open Knowledge Base hub
  ↓
Filter by technique, badge, or difficulty
  ↓
View SOP + flowchart + BOM bundle
  ↓
Study steps, required skills, materials
  ↓
Ask question (opens Discourse topic linked to step via DiscourseLink)
  ↓
Bookmark / download offline kit
  ↓
Return to project page → apply with referenced learnings
  ↓
After participation: submit feedback, mark mastered steps
  ↓
END
```

---

### Flow 7: Skill Acquisition & Verification

```text
START → Project Execution (On-site)
  ↓
Student/Volunteer (Tłoker) performs task (e.g., "Clay Plastering")
  ↓
Master/Expert (Mistrz) observes and approves quality
  ↓
Digital Action: Master/Expert scans User's QR Code or selects in App
  ↓
Master/Expert clicks "Grant Badge: Basic Plastering"
  ↓
System Update:
  • User gains XP
  • "Clay Plastering" Node turns Gold (Mastered) on Skill Tree
  • "Dexterity" stat increases
  ↓
Notification: "You unlocked the Earth Builder Badge!" → END
```

---

**Navigation**: [← Previous: Information Architecture](#information-architecture) | [↑ Table of Contents](#table-of-contents) | [Next: Technical Architecture →](#technical-architecture)

---

## Technical Architecture

**Quick Links**: [System Architecture Overview](#system-architecture-overview-self-hosted) | [Technology Stack](#technology-stack) | [Folder Structure](#folder-structure)

### System Architecture Overview (Self-Hosted)

```text
┌─────────────────────────────────────────────────────────┐
│                    Client Layer                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │   Web App    │  │  Mobile Web  │  │     PWA      │   │
│  │  (React/Next)│  │ (Responsive) │  │   (Future)   │   │
│  └──────────────┘  └──────────────┘  └──────────────┘   │
└─────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────┐
│              Traefik (Reverse Proxy/API Gateway)        │
│  • SSL/TLS Termination • Rate Limiting • Load Balancing │
└─────────────────────────────────────────────────────────┘
                            │
          ┌─────────────────┼─────────────────┐
          ▼                 ▼                 ▼
┌──────────────────┐  ┌──────────────┐  ┌──────────────┐
│  Supabase API    │  │  Custom API  │  │  File Storage│
│  (PostgREST +    │  │  (Express/   │  │  (Supabase   │
│   GoTrue +       │  │   Fastify)   │  │   Storage)   │
│   Realtime)      │  │              │  │              │
└──────────────────┘  └──────────────┘  └──────────────┘
          │                 │                 │
          └─────────────────┼─────────────────┘
                            ▼
┌─────────────────────────────────────────────────────────┐
│              Self-Hosted Supabase Core Services         │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │ PostgreSQL  │  │    Redis    │  │    Kong     │      │
│  │  (Database) │  │   (Cache)   │  │  (Gateway)  │      │
│  └─────────────┘  └─────────────┘  └─────────────┘      │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │  PostgREST  │  │   GoTrue    │  │  Realtime   │      │
│  │  (REST API) │  │    (Auth)   │  │ (WebSocket) │      │
│  └─────────────┘  └─────────────┘  └─────────────┘      │
│  ┌─────────────┐  ┌─────────────┐                       │ 
│  │   Storage   │  │   Functions │                       │
│  │   (S3-like) │  │  (Edge Fns) │                       │
│  └─────────────┘  └─────────────┘                       │
└─────────────────────────────────────────────────────────┘
```

---

### Technology Stack

#### Frontend

- **Framework**: React 18+ or Next.js 14+ with App Router
- **Language**: TypeScript
- **Styling**: Tailwind CSS with custom design tokens
- **State Management**: React Context + useReducer or Zustand
- **Forms**: React Hook Form + Zod validation
- **Maps**: Leaflet.js or Mapbox GL JS
- **Animations**: Framer Motion
- **Icons**: Lucide React or Heroicons
- **i18n**: next-intl or react-i18next (future)

#### Backend (Self-Hosted Supabase)

- **Backend Platform**: Self-hosted Supabase (Docker Compose / Kubernetes)
- **Database**: PostgreSQL 15+ (via Supabase)
- **ORM**: Prisma (for complex queries) + PostgREST (auto-generated REST)
- **Authentication**: Supabase Auth (GoTrue) - Email, OAuth, Magic Links
- **File Storage**: Supabase Storage (S3-compatible)
- **Cache**: Redis 7+ (via Supabase)
- **API Gateway**: Kong (via Supabase) + Traefik (reverse proxy)
- **Real-time**: Supabase Realtime (PostgreSQL changes via WebSocket)
- **Edge Functions**: Supabase Edge Functions (Deno runtime)
- **Job Queue**: BullMQ (Redis-based) for background tasks
- **Email**: Self-hosted Postfix or SMTP relay (SendGrid/SMTP)
- **Search**: PostgreSQL full-text search + pg_trgm extension
- **Payments**: Stripe (for paid Master/Expert (Mistrz) services)
- **Discussions & Forums**: Discourse (self-hosted or cloud) - All community discussions, Q&A, and forum functionality

#### Infrastructure (Self-Hosted)

- **Containerization**: Docker Compose (development) / Kubernetes (production)
- **Reverse Proxy**: Traefik (SSL, routing, load balancing)
- **Database Backups**: pg_dump + automated scripts or Barman
- **Monitoring**: Prometheus + Grafana
- **Logging**: Loki + Grafana or ELK Stack
- **CI/CD**: GitLab CI/CD or GitHub Actions (deploy to your servers)
- **Security**:
  - Fail2ban (intrusion prevention)
  - UFW/Firewall rules
  - SSL certificates (Let's Encrypt via Traefik)
  - Regular security updates

---

### Folder Structure

```text
tloka-platform/
├── src/
│   ├── app/                      # Next.js app router
│   │   ├── (auth)/               # Authentication group
│   │   ├── (main)/               # Main app group
│   │   ├── znajdz-tloke/         # Project search
│   │   ├── projekt/[id]/         # Project detail
│   │   ├── moje-tloki/           # My Toloki - User dashboard
│   │   ├── stworz-tloke/         # Create Toloka - Create project wizard
│   │   ├── rekrutacja/[id]/      # Recruitment management
│   │   ├── mistrz/               # Master/Expert dashboard
│   │   └── api/                  # API routes
│   │       ├── tloki/
│   │       ├── applications/
│   │       ├── experts/
│   │       └── users/
│   │
│   ├── components/
│   │   ├── ui/                   # Base components
│   │   ├── forms/                # Form components
│   │   ├── project/              # Project components
│   │   ├── recruitment/          # Recruitment components
│   │   └── layout/               # Layout components
│   │
│   ├── lib/
│   │   ├── api/                  # API client
│   │   ├── auth/                 # Auth utilities
│   │   ├── db/                   # Database utilities
│   │   ├── validations/          # Zod schemas
│   │   └── utils/                # Helpers
│   │
│   ├── hooks/                    # Custom React hooks
│   ├── contexts/                 # React contexts
│   ├── types/                    # TypeScript types
│   └── styles/
│       └── globals.css           # Global styles
│
├── prisma/
│   ├── schema.prisma             # Database schema
│   └── migrations/               # Database migrations
│
├── supabase/
│   ├── config.toml               # Supabase configuration
│   ├── migrations/               # Supabase SQL migrations
│   ├── functions/                # Edge Functions
│   └── seed.sql                  # Seed data
│
├── public/
│   ├── images/
│   ├── fonts/
│   └── icons/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── docs/
│   └── api/                      # API documentation
│
├── docker/
│   ├── docker-compose.yml         # Supabase local development
│   ├── docker-compose.prod.yml    # Production stack
│   └── Dockerfile                 # Application container
│
└── config files
    ├── package.json
    ├── tsconfig.json
    ├── tailwind.config.ts
    ├── next.config.js
    └── .env.example
```

---

### Discourse Integration Architecture

**Overview**: All community discussions, Q&A, forums, and user conversations are handled by Discourse. The Toloka platform does **not** implement its own discussion system. Instead, it stores references only (via `DiscourseLink` model), proxies to Discourse API, uses SSO for authentication, and embeds/links to Discourse topics.

**Key Integration Points**:

- **Data Model**: `DiscourseLink` stores metadata and references to Discourse topics (see [Data Models](#data-models))
- **API**: All discussion operations handled via Discourse REST API (see [API Architecture](#api-architecture))
- **Authentication**: SSO integration between Supabase Auth and Discourse
- **UI**: Topics displayed via embedded iframe or direct links

**For detailed setup instructions**, see [Discourse Integration Setup](#discourse-integration-setup) in the Implementation Guide.

---

## Data Models

**Quick Links**: [Core Entities](#core-entities) | [Entity Relationships](#entity-relationships)

### Core Entities

#### User

```typescript
User {
  id: UUID (PK)
  email: String (unique)
  name: String
  avatar: String (URL)
  bio: Text
  roles: Enum[] (STUDENT_VOLUNTEER/TLOKER, HOST/GOSPODARZ, MASTER_EXPERT/MISTRZ)

  // Master/Expert (Mistrz)-specific
  specializations: String[]
  yearsExperience: Integer
  rating: Decimal
  completedProjects: Integer
  hourlyRate: Decimal (optional)

  // Relationships
  hostedProjects: Tłoka[]
  applications: Application[]
  expertInvitations: ExpertInvitation[]

  // Metadata
  createdAt: DateTime
  updatedAt: DateTime
  lastLoginAt: DateTime
}
```

#### Toloka (Project) (Tłoka)

```typescript
Tłoka {
  id: UUID (PK)
  title: String
  slug: String (unique)
  type: String (e.g., "Budownictwo naturalne")
  description: Text

  // Location
  location: {
    street: String
    city: String
    postalCode: String
    coordinates: { lat: Float, lng: Float }
  }

  // Timeline
  dates: {
    start: Date
    end: Date
    applicationDeadline: Date
    resultsAnnouncement: Date
  }

  // Logistics
  accommodation: {
    tentField: Boolean
    underRoof: Boolean
    none: Boolean
    details: Text
  }
  spotsAvailable: Integer
  format: Enum (VOLUNTEER, PAID)
  food: Text
  insurance: Text
  schedule: Text
  additionalInfo: Text

  // Requirements
  requiredSkills: {
    name: String
    importance: Integer (1-6)
    description: Text
  }[]

  // Media
  images: String[] (URLs)
  faq: { question: String, answer: Text }[]

  // Expert Integration
  needsExpert: Boolean
  expertSpecialization: String
  expertPayment: Enum (PAID, EXCHANGE)
  expertDescription: Text

  // Relationships
  hostId: UUID (FK → User)
  host: User
  applications: Application[]
  selectedTeam: User[]
  invitedExperts: ExpertInvitation[]

  // State
  status: Enum (DRAFT, OPEN, IN_RECRUITMENT, CLOSED, COMPLETED)
  applicantsCount: Integer

  // Metadata
  createdAt: DateTime
  updatedAt: DateTime
  publishedAt: DateTime
}
```

#### Application

```typescript
Application {
  id: UUID (PK)

  // References
  tlokaId: UUID (FK → Tłoka)
  applicantId: UUID (FK → User)

  // Skills Assessment
  skills: {
    skillId: UUID
    skillName: String
    level: Enum (NONE, BASIC, INTERMEDIATE, ADVANCED)
    notes: Text
  }[]

  // Motivation
  motivation: Text
  additionalInfo: Text

  // Status
  status: Enum (PENDING, ACCEPTED, REJECTED, WITHDRAWN)

  // Metadata
  createdAt: DateTime
  updatedAt: DateTime
  reviewedAt: DateTime
}
```

#### ExpertInvitation

```typescript
ExpertInvitation {
  id: UUID (PK)

  // References
  tlokaId: UUID (FK → Tłoka)
  expertId: UUID (FK → User)

  // Details
  specialization: String
  description: Text
  payment: Enum (PAID, EXCHANGE)
  amount: Decimal (optional)

  // Status
  status: Enum (PENDING, ACCEPTED, REJECTED, COMPLETED)

  // Metadata
  createdAt: DateTime
  respondedAt: DateTime
  completedAt: DateTime
}
```

#### KnowledgeArtifact

```typescript
KnowledgeArtifact {
  id: UUID (PK)
  tlokaId: UUID (FK → Tłoka, optional)
  createdBy: UUID (FK → User)
  contributors: UUID[]

  title: String
  type: Enum('SOP','FLOWCHART','BOM','CASE_STUDY')
  description: Text
  difficulty: Enum('BEGINNER','INTERMEDIATE','ADVANCED')
  tags: String[]
  badgesAwarded: String[]

  steps: SOPStep[]
  flowchart: JSON | null      // Mermaid / React Flow payload
  billOfMaterials: BillOfMaterialItem[]
  attachments: String[]        // media URLs

  version: Integer
  status: Enum('DRAFT','IN_REVIEW','PUBLISHED','ARCHIVED')
  usageCount: Integer
  viewCount: Integer

  createdAt: DateTime
  updatedAt: DateTime
  publishedAt: DateTime | null
  archivedAt: DateTime | null
}
```

#### SOPStep

```typescript
SOPStep {
  id: UUID (PK)
  artifactId: UUID (FK → KnowledgeArtifact)
  order: Integer
  title: String
  description: Text
  durationMinutes: Integer | null
  skillsRequired: String[]
  badgesUnlocked: String[]
  materials: MaterialRef[]
  tools: ToolRef[]
  media: String[]
  safetyNotes: String[]
  discourseThreadId: UUID | null
}
```

#### BillOfMaterialItem

```typescript
BillOfMaterialItem {
  id: UUID (PK)
  artifactId: UUID (FK → KnowledgeArtifact)
  name: String
  category: String
  quantity: Decimal
  unit: String
  supplier: String | null
  costPerUnit: Decimal | null
  status: Enum('PLANNED','ORDERED','DELIVERED','USED')
}
```

#### MaterialRef / ToolRef

```typescript
MaterialRef {
  name: String
  quantity: Decimal
  unit: String
}

ToolRef {
  name: String
  required: Boolean
  notes: String | null
}
```

#### Discourse Link (Discussion Integration)

```typescript
DiscourseLink {
  id: UUID (PK)
  artifactId: UUID | null (FK → KnowledgeArtifact)
  stepId: UUID | null (FK → SOPStep)
  tlokaId: UUID | null (FK → Tłoka)
  
  // Discourse references
  discourseTopicId: Integer (Discourse topic ID)
  discoursePostId: Integer | null (Specific post ID if linking to a post)
  discourseCategoryId: Integer | null (Discourse category ID)
  
  // Metadata & sync
  lastSyncedAt: DateTime (Last sync with Discourse API)
  commentCount: Integer (Cached count from Discourse)
  isActive: Boolean (Whether the topic is still active)
  syncStatus: Enum('SYNCED','PENDING','ERROR')
  
  createdAt: DateTime
  updatedAt: DateTime
}
```

**Note**: All discussions, forums, and Q&A are managed through Discourse. This model only stores references and metadata for linking platform content to Discourse topics. The actual discussion content, replies, and moderation are handled entirely by Discourse.

#### SkillNode (The Tree Structure)

```typescript
SkillNode {
  id: UUID (PK)
  title: String (e.g., "Straw Bale Compression")
  category: Enum (EARTH, WOOD, STRAW, SYSTEMS, SOFT_SKILLS)
  tier: Integer (1-5)
  
  // Visuals
  icon: String (SVG path)
  coordinates: { x: Float, y: Float } // For canvas rendering
  
  // Logic
  parentId: UUID | null (Prerequisite skill)
  xpValue: Integer
  
  // Relationships
  requiredFor: SkillNode[]
  relatedSOPs: KnowledgeArtifact[]
}
```

#### UserProgression (The Save State)

```typescript
UserProgression {
  id: UUID (PK)
  userId: UUID (FK)
  nodeId: UUID (FK)
  status: Enum (LOCKED, UNLOCKED, IN_PROGRESS, MASTERED)
  currentXP: Integer
  
  // Verification
  verifiedBy: UUID (FK → Master/Expert/Mistrz or Host/Gospodarz)
  verifiedAt: DateTime
  evidence: String (Link to project photo or Host review)
}
```

#### AttributeStats (The Radar Chart)

```typescript
AttributeStats {
  userId: UUID (PK)
  strength: Integer     // Physical endurance
  dexterity: Integer    // Tool precision
  intelligence: Integer // Planning/Engineering
  charisma: Integer     // Leadership/Teaching
  wisdom: Integer       // Safety/Experience
}
```

---

### Entity Relationships

```text
User (Host/Gospodarz) ─────┬─── creates ──→ Toloka (Tłoka)
                          │
User (Student/Volunteer/Tłoker) ────────┼─── applies to ──→ Application ──→ Toloka (Tłoka)
                          │
User (Master/Expert/Mistrz) ────────┴─── receives ──→ ExpertInvitation ──→ Toloka (Tłoka)
                           │
                           └─── authors ──→ KnowledgeArtifact ──→ Toloka (Tłoka)

KnowledgeArtifact ─── contains ──→ SOPStep
KnowledgeArtifact ─── contains ──→ BillOfMaterialItem
KnowledgeArtifact ─── links to ──→ DiscourseLink ─── references ──→ Discourse (external)
SOPStep ─── links to ──→ DiscourseLink ─── references ──→ Discourse (external)
User ─── progresses through ──→ UserProgression ─── references ──→ SkillNode
SkillNode ─── relates to ──→ KnowledgeArtifact
User ─── has stats ──→ AttributeStats
```

**Cardinality**:

- User : Toloka (Tłoka) (as host) = 1 : Many
- User : Application = 1 : Many
- Toloka (Tłoka) : Application = 1 : Many
- User (Master/Expert/Mistrz) : ExpertInvitation = 1 : Many
- Toloka (Tłoka) : ExpertInvitation = 1 : Many
- Toloka (Tłoka) : User (selected team) = Many : Many
- KnowledgeArtifact : SOPStep = 1 : Many
- KnowledgeArtifact : BillOfMaterialItem = 1 : Many
- KnowledgeArtifact : DiscourseLink = 1 : Many (optional)
- SOPStep : DiscourseLink = 1 : 1 (optional)
- Tłoka : DiscourseLink = 1 : 1 (optional)
- User : UserProgression = 1 : Many
- SkillNode : UserProgression = 1 : Many
- User : AttributeStats = 1 : 1
- SkillNode : KnowledgeArtifact = Many : Many

---

**Navigation**: [← Previous: Technical Architecture](#technical-architecture) | [↑ Table of Contents](#table-of-contents) | [Next: API Architecture →](#api-architecture)

---

## API Architecture

**Quick Links**: [RESTful API Endpoints](#restful-api-endpoints) | [API Response Formats](#api-response-formats) | [Authentication & Authorization](#authentication--authorization)

### RESTful API Endpoints

#### Projects (Toloki/Tłoki)

```http
GET    /api/tloki
       • List all projects
       • Query params: ?type=, &location=, &startDate=, &page=, &limit=
       • Response: Paginated list of projects

POST   /api/tloki
       • Create new project (Host/Gospodarz only)
       • Body: Project data (all 7 wizard steps)
       • Response: Created project

GET    /api/tloki/:id
       • Get single project details
       • Response: Full project object with relations

PUT    /api/tloki/:id
       • Update project (Host/Gospodarz owner only)
       • Body: Partial project data
       • Response: Updated project

DELETE /api/tloki/:id
       • Delete project (Host/Gospodarz owner only, if no applications)
       • Response: 204 No Content

GET    /api/tloki/search
       • Full-text search
       • Query params: ?q=, &filters=
       • Response: Matching projects
```

#### Applications

```http
GET    /api/tloki/:id/applications
       • List all applications for a project (Host/Gospodarz only)
       • Response: Array of applications with applicant info

POST   /api/tloki/:id/applications
       • Submit application (Student/Volunteer/Tłoker)
       • Body: Skills, motivation, additional info
       • Response: Created application

GET    /api/applications/:id
       • Get application details
       • Access: Applicant or project host
       • Response: Full application

PUT    /api/applications/:id
       • Update application (before review)
       • Body: Partial application data
       • Response: Updated application

DELETE /api/applications/:id
       • Withdraw application
       • Response: 204 No Content
```

#### Recruitment

```http
GET    /api/tloki/:id/applicants
       • Get all applicants with details (Host/Gospodarz only)
       • Response: Suggested team + all applicants

POST   /api/tloki/:id/team
       • Add applicant to selected team
       • Body: { applicantId }
       • Response: Updated team

DELETE /api/tloki/:id/team/:userId
       • Remove from team
       • Response: Updated team

POST   /api/tloki/:id/announce-results
       • Finalize recruitment, notify applicants
       • Response: Confirmation
```

#### Expert System

```http
POST   /api/tloki/:id/invite-expert
       • Invite expert to project (Host/Gospodarz)
       • Body: { specialization, description, payment, amount }
       • Response: Created invitation

GET    /api/experts/invitations
       • List invitations for current Master/Expert (Mistrz)
       • Query params: ?status=PENDING
       • Response: Array of invitations

PUT    /api/experts/invitations/:id
       • Accept/reject invitation (Master/Expert/Mistrz)
       • Body: { status: 'ACCEPTED' | 'REJECTED' }
       • Response: Updated invitation

GET    /api/experts/projects
       • List active/completed projects (Master/Expert/Mistrz)
       • Query params: ?status=ACTIVE
       • Response: Projects with mentoring
```

#### Users

```http
GET    /api/users/me
       • Get current authenticated user
       • Response: User profile with roles

PUT    /api/users/me
       • Update user profile
       • Body: Partial user data
       • Response: Updated user

GET    /api/users/:id
       • Get public user profile
       • Response: Public user info (name, avatar, bio)
```

#### Gamification

```http
GET    /api/gamification/tree
       • Fetch static definition of skill tree (nodes & connections)
       • Response: Skill tree structure with all nodes and prerequisites

GET    /api/gamification/progress/:userId
       • Get user's unlocked nodes, XP, and radar stats
       • Response: User progression data with skill nodes, XP totals, and attribute stats

POST   /api/gamification/verify
       • (Master/Expert/Mistrz Only) Validate a skill
       • Body: { volunteerId, nodeId, rating, comment }
       • Response: Updated user progression with verification

GET    /api/leaderboards
       • Get top contributors by category (Global/Regional)
       • Query params: ?category=, &region=, &timeframe=
       • Response: Ranked list of users with stats
```

#### Discourse Integration

```http
GET    /api/discourse/topics/:topicId
       • Fetch Discourse topic metadata (proxies to Discourse API)
       • Response: { id, title, postsCount, lastActivity, url }

POST   /api/discourse/topics
       • Create new Discourse topic (for KnowledgeArtifact, SOPStep, or Tłoka)
       • Body: { title, raw (content), category, targetType, targetId }
       • Response: { discourseTopicId, discourseUrl, discourseLinkId }
       • Note: Creates topic in Discourse, stores reference in DiscourseLink table

GET    /api/discourse/sync/:linkId
       • Sync DiscourseLink metadata with Discourse API
       • Updates: commentCount, lastActivity, isActive
       • Response: Updated DiscourseLink

GET    /api/discourse/categories
       • List available Discourse categories
       • Response: Array of category objects
```

**Note**: For detailed Discourse setup and configuration, see [Discourse Integration Setup](#discourse-integration-setup) in the Implementation Guide.

#### Miscellaneous

```http
GET    /api/filters
       • Get available filter options
       • Response: { types, locations, skills }

GET    /api/publications
       • List resource library publications
```

#### Knowledge Base

```http
GET    /api/knowledge
       • List artifacts (supports filters: type, category, difficulty, badge, page, limit)

POST   /api/knowledge
       • Create artifact (Master/Expert/Mistrz or Host/Gospodarz)
       • Body: { title, type, description, difficulty, tags }

GET    /api/knowledge/:id
       • Fetch artifact with SOP steps, flowchart, BOM, related Toloki (Tłoki)

PUT    /api/knowledge/:id
       • Update metadata/status; trigger new version on publish

DELETE /api/knowledge/:id
       • Archive artifact (soft delete, retain history)

POST   /api/knowledge/:id/steps
       • Bulk add/update SOP steps (auto-order)

PUT    /api/steps/:stepId
       • Update single step (materials, safety, media)

DELETE /api/steps/:stepId
       • Remove step; reindex order values

POST   /api/knowledge/:id/bom
       • Upsert BOM line items with quantity, supplier, cost

POST   /api/knowledge/:id/flowchart
       • Persist flowchart JSON (Mermaid/React Flow)

GET    /api/knowledge/:id/discussions
       • Get Discourse topic link for this artifact
       • Response: { discourseTopicId, discourseUrl, commentCount, lastActivity }
       • Note: Proxies to Discourse API to fetch topic metadata

POST   /api/knowledge/:id/discussions
       • Create new Discourse topic for this artifact
       • Body: { title, initialPost, category }
       • Response: { discourseTopicId, discourseUrl, discourseLinkId }
       • Note: Creates topic in Discourse via API, stores reference in DiscourseLink

GET    /api/knowledge/search
       • Full-text search across SOP body, BOM, tags, titles
```

---

### API Response Formats

#### Success Response

```json
{
  "success": true,
  "data": { ... },
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 156,
    "pages": 8
  }
}
```

#### Error Response

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input data",
    "details": [
      {
        "field": "title",
        "message": "Title is required"
      }
    ]
  }
}
```

---

### Authentication & Authorization

#### Authentication Flow

1. User logs in via email/password or OAuth
2. Server generates JWT token
3. Token stored in HTTP-only cookie
4. Token included in subsequent requests
5. Server validates token on protected routes

#### Authorization Levels

- **Public**: Anyone (project listing, details)
- **Authenticated**: Logged-in users (apply, create profile)
- **Role-Based**: Specific actions per role
  - Host (Gospodarz): Create projects, manage recruitment
  - Student/Volunteer (Tłoker): Apply to projects, view applications
  - Master/Expert (Mistrz): Accept invitations, manage mentoring
- **Owner**: Resource owner (edit own projects/applications)

---

## Security & Performance

**Quick Links**: [Security Measures](#security-measures) | [Performance Optimizations](#performance-optimizations) | [Scalability Considerations](#scalability-considerations)

### Security Measures

#### Authentication Security

- **Password**: Hashed with bcrypt (10+ rounds)
- **JWT**: Signed with secure secret, short expiration (15min)
- **Refresh Tokens**: Long-lived, stored securely, rotated
- **HTTP-only Cookies**: Prevent XSS attacks
- **CSRF Protection**: Token validation on state-changing requests

#### API Security

- **Rate Limiting**:
  - 100 requests/15min per IP (general)
  - 10 requests/15min for login/signup
- **Input Validation**: Zod schemas on all endpoints
- **SQL Injection**: Prevented by Prisma ORM
- **XSS**: Sanitized user input, CSP headers
- **CORS**: Restricted to allowed origins

#### Data Security

- **Encryption at Rest**: Database encryption enabled
- **Encryption in Transit**: HTTPS only, TLS 1.3
- **Sensitive Data**: PII encrypted, audit logs
- **File Uploads**: Type/size restrictions, virus scanning
- **GDPR Compliance**:
  - User consent
  - Data export
  - Right to deletion
  - Privacy policy

---

### Performance Optimizations

#### Frontend Optimizations

- **Code Splitting**: Route-based, lazy loading
- **Image Optimization**:
  - Next.js Image component
  - WebP with fallbacks
  - Responsive images (srcset)
  - Lazy loading below fold
- **Caching**:
  - Static assets (CDN, long cache)
  - API responses (short cache for dynamic data)
  - Service worker (PWA, future)
- **Bundle Size**:
  - Tree shaking
  - Dynamic imports
  - Remove unused dependencies

#### Backend Optimizations

- **Database**:
  - Indexes on commonly queried fields
  - Connection pooling
  - Query optimization (select only needed fields)
  - Pagination on large datasets
- **Caching Layer** (Redis):
  - Frequently accessed data (user profiles, project lists)
  - Session storage
  - Rate limiting counters
- **CDN**: Static assets served from edge locations
- **Compression**: Gzip/Brotli for responses

#### Monitoring

- **Performance Metrics**:
  - Time to First Byte (TTFB)
  - Largest Contentful Paint (LCP)
  - First Input Delay (FID)
  - Cumulative Layout Shift (CLS)
- **Error Tracking**: Sentry for runtime errors
- **Logging**: Structured logs (JSON), log levels
- **Alerts**: Automated alerts for critical errors, downtime

---

### Scalability Considerations

#### Horizontal Scaling

- **Stateless API**: No server-side sessions (JWT-based)
- **Load Balancing**: Distribute requests across servers
- **Database Replicas**: Read replicas for heavy read operations
- **Microservices**: Potential split into smaller services
  - User service
  - Project service
  - Application service
  - Notification service

#### Vertical Scaling

- **Database**: Increase resources as needed
- **Server**: Upgrade compute resources

#### Future Enhancements

- **Queueing System**: Background jobs (emails, notifications)
- **Event-Driven**: Pub/sub for real-time updates
- **WebSockets**: Real-time chat, notifications
- **Mobile Apps**: React Native or Flutter
- **Internationalization**: Multi-language support

---

**Navigation**: [← Previous: API Architecture](#api-architecture) | [↑ Table of Contents](#table-of-contents) | [Next: Conclusion →](#conclusion)

---

## Conclusion

### System Highlights

1. **Three-Role Ecosystem**: Innovative triadic value exchange model
2. **Regenerative Design**: Aesthetics aligned with platform values
3. **Comprehensive Feature Set**: Discovery, application, recruitment, expert integration
4. **Scalable Architecture**: Modern stack with growth potential
5. **Security-First**: Multiple layers of protection
6. **Performance-Optimized**: Fast, responsive user experience

### Implementation Priorities

**Phase 1: MVP** (3-4 months)

- Core authentication
- Project CRUD (Host/Gospodarz)
- Project discovery & detail (Student/Volunteer/Tłoker)
- Application system
- Basic recruitment management

**Phase 2: Enhanced Features** (2-3 months)

- Master/Expert (Mistrz) integration (expert invitations)
- Advanced search & filters
- Map view
- Notifications
- User profiles

**Phase 3: Community** (2-3 months)

- Forum
- Publications library
- Reviews & ratings
- Messaging system

**Phase 4: Optimization** (Ongoing)

- Performance tuning
- Mobile app
- Internationalization
- Advanced analytics

## Senior Architect Code Quality Mandate

> Reference: `SENIOR_ARCHITECT_PROMPT.md` (maintained alongside this document)
> Location: `/docs/SENIOR_ARCHITECT_PROMPT.md` in the GitHub documentation repository

### Purpose

Guarantee that every code contribution meets senior-level production standards with an emphasis on maintainability, explicit architecture, and defensive programming.

### Core Requirements

1. **Technical Environment Definition**
   - Document the exact stack (framework versions, language level, testing tools, style guide).
   - Enforce consistent naming conventions for files, components, functions, and styles.

2. **Architecture & Layering**
   - Follow Clean/Hexagonal layering: Presentation → Application → Domain → Infrastructure.
   - Domain models never depend on UI or infrastructure concerns.
   - Each module has a single responsibility; no god objects or vague names.

3. **Type Safety & Validation**
   - Strict typing everywhere (no implicit `any`).
   - Validate all external data at boundaries (API, user input, integrations).
   - Separate DTOs, domain models, and view models; never reuse the same type across layers.

4. **Error Handling & Observability**
   - No silent failures: every catch must log, rethrow, or return a typed error.
   - Classify errors (domain, validation, infrastructure) and handle accordingly.
   - Structured logging with request IDs, user IDs, and sanitized payloads.

5. **Configuration & Constants**
   - Centralize configuration with environment-based overrides and validation at startup.
   - No hardcoded URLs, keys, colors, or timeouts—always reference config or design tokens.
   - All user-facing strings must go through the i18n system.

6. **Documentation & Comments**
   - Comment the “why” behind complex business rules, not the obvious “what.”
   - Public APIs require purpose, params, returns, errors, and usage examples.
   - TODO/FIXME/HACK markers must include date, author, context, and ticket reference.

7. **Quality Gate**
   - Code must pass lint, tests, and architecture checks before merging.
   - No duplicate logic; extract shared utilities.
   - Tests cover business logic, critical flows, edge cases, and error paths.

This mandate is the minimum bar for any feature or fix and should be referenced during code reviews, RFCs, and onboarding. Use the full `SENIOR_ARCHITECT_PROMPT.md` document for detailed checklists and rationale.

---

**Navigation**: [← Previous: Conclusion](#conclusion) | [↑ Table of Contents](#table-of-contents) | [Next: Design System →](#design-system)

---

## Design System

**Quick Links**: [Color Palette](#color-palette) | [Typography](#typography) | [Spacing System](#spacing-system) | [Component Library](#component-library)

### Color Palette

#### Dark Mode (Primary Theme)

Based on Enklava's earthy, regenerative aesthetic:

| Color | HSL Value | Hex Equivalent | Usage |
|-------|-----------|----------------|-------|
| Background | `hsl(160, 8%, 11%)` | #1A1F1D | Deep forest green-black - main background |
| Foreground | `hsl(50, 20%, 96%)` | #F8F6F0 | Warm off-white - main text |
| Card | `hsl(155, 10%, 15%)` | #222827 | Dark card backgrounds |
| Primary | `hsl(145, 35%, 52%)` | #57A876 | Sage green - brand, CTAs, active states |
| Secondary | `hsl(160, 6%, 24%)` | #393D3C | Muted gray-green - secondary UI |
| Accent | `hsl(38, 55%, 58%)` | #D5A55A | Warm ochre/clay - highlights, secondary CTAs |
| Muted | `hsl(160, 6%, 24%)` | #393D3C | Subtle backgrounds |
| Muted Foreground | `hsl(50, 10%, 65%)` | #A8A295 | Secondary text |
| Border | `hsl(160, 6%, 24%)` | #393D3C | Borders and dividers |
| Destructive | `hsl(0, 63%, 31%)` | #823232 | Error states, warnings |

#### Light Mode (Alternative)

| Color | HSL Value | Usage |
|-------|-----------|-------|
| Background | `hsl(42, 35%, 96%)` | Warm cream background |
| Foreground | `hsl(160, 30%, 12%)` | Dark green-black text |
| Primary | `hsl(145, 50%, 38%)` | Deeper sage green |
| Accent | `hsl(38, 65%, 52%)` | Richer ochre |

#### Color Usage Guidelines

- **Primary (Sage Green)**: Main CTAs, navigation, links, success states, Host (Gospodarz) role
- **Accent (Ochre)**: Secondary CTAs, highlights, featured content, Student/Volunteer (Tłoker) role
- **Secondary (Gray-green)**: Tertiary elements, Master/Expert (Mistrz) role, subtle backgrounds
- **Destructive (Deep Red)**: Errors, warnings, delete actions

---

### Typography

#### Font Families

- **Headings**: Cormorant Garamond (serif) - Weights: 300, 400, 500, 600
- **Display (Special)**: Cinzel (serif) - Weights: 400-900
- **Body**: Inter (sans-serif) - Weights: 300, 400, 500, 600

#### Type Scale

| Element | Size | Line Height | Weight | Usage |
|---------|------|-------------|--------|-------|
| Display | 56px (3.5rem) | 1.1 | 400-600 | Hero sections |
| H1 | 40px (2.5rem) | 1.2 | 400-600 | Page titles |
| H2 | 32px (2rem) | 1.3 | 400-500 | Section headers |
| H3 | 24px (1.5rem) | 1.4 | 500 | Subsection headers |
| H4 | 20px (1.25rem) | 1.5 | 500 | Card titles |
| Body Large | 18px (1.125rem) | 1.6 | 400 | Intro paragraphs |
| Body | 16px (1rem) | 1.6 | 400 | Default text |
| Body Small | 14px (0.875rem) | 1.5 | 400 | Helper text |
| Caption | 12px (0.75rem) | 1.4 | 400 | Metadata |

---

### Spacing System

Base unit: **4px (0.25rem)**

| Token | Value | Usage |
|-------|-------|-------|
| spacing-2 | 8px | Minimal spacing |
| spacing-3 | 12px | Small gaps |
| spacing-4 | 16px | Default component padding |
| spacing-6 | 24px | Card padding, medium gaps |
| spacing-8 | 32px | Large gaps |
| spacing-12 | 48px | Section spacing (small) |
| spacing-16 | 64px | Section spacing (medium) |
| spacing-24 | 96px | Section spacing (large) |

---

### Border Radius & Shadows

#### Border Radius

- **sm**: 8px - Input fields
- **md**: 10px - Buttons
- **lg**: 12px - Cards, images
- **2xl**: 16px - Modals
- **full**: 9999px - Pills, avatars

#### Shadows

- **sm**: Subtle elevation (1-2px)
- **default**: Card elevation (3px)
- **md**: Raised elements (4-6px)
- **lg**: Modals, dropdowns (10-15px)
- **xl**: Prominent overlays (20-25px)

---

### Component Library

#### Gamification Components

##### SkillConstellation

- Pan-and-zoom canvas component for interactive skill tree visualization
- Dark mode background with constellation-style node layout
- Nodes act as "stars" that pulse when available for unlocking
- Visual states: Locked (gray), Unlocked (dim), In Progress (pulsing), Mastered (gold)
- Supports touch gestures and mouse interactions for navigation

##### StatRadar

- Pentagon chart overlay component for User Profiles
- Displays five attributes: Strength, Dexterity, Intelligence, Charisma, Wisdom
- Scales from 0-100 with visual fill and numeric labels
- Updates dynamically based on verified skill completions
- Color-coded by attribute category

##### BadgeCard

- Hexagonal "patch" design component with fabric texture overlay
- Displays earned badges with scout-inspired aesthetic
- Shows badge icon, title, unlock date, and verification evidence
- Hover states reveal detailed achievement information
- Supports collection view and individual badge detail modals

---

**Navigation**: [← Previous: Senior Architect Code Quality Mandate](#senior-architect-code-quality-mandate) | [↑ Table of Contents](#table-of-contents) | [Next: Implementation Guide for AI Agents →](#implementation-guide-for-ai-agents)

---

## Implementation Guide for AI Agents

**Quick Links**: [Prerequisites](#prerequisites--initial-setup) | [Environment Config](#environment-configuration) | [Database Setup](#database-setup--migrations) | [Supabase Config](#supabase-self-hosting-configuration) | [Auth Setup](#authentication--sso-configuration) | [Discourse Setup](#discourse-integration-setup) | [Testing](#testing--quality-assurance) | [Deployment](#deployment-checklist) | [Troubleshooting](#common-issues--troubleshooting) | [Monitoring](#monitoring--maintenance)

This section provides step-by-step guidance for AI agents and developers implementing the Toloka platform. Follow these sections in order for a successful deployment.

### Prerequisites & Initial Setup

**System Requirements**:

- **Server**: Ubuntu 22.04 LTS or Debian 12+ (recommended)
- **Resources**: Minimum 4 CPU cores, 8GB RAM, 100GB SSD (production)
- **Docker**: Docker 24+ and Docker Compose 2.20+
- **Domain**: Registered domain with DNS access
- **SSL**: Let's Encrypt support (via Traefik)

**Initial Server Setup**:

1. **Update system packages**

   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install Docker and Docker Compose**

   ```bash
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker $USER
   ```

3. **Install required tools**

   ```bash
   sudo apt install -y git curl wget ufw fail2ban
   ```

4. **Configure firewall**

   ```bash
   sudo ufw allow 22/tcp    # SSH
   sudo ufw allow 80/tcp    # HTTP (for Let's Encrypt)
   sudo ufw allow 443/tcp   # HTTPS
   sudo ufw enable
   ```

5. **Clone repository**

   ```bash
   git clone https://github.com/PawelSroczynski/toloka.git
   cd toloka
   ```

### Environment Configuration

**Required Environment Variables**:

Create `.env` files for each environment (`.env.development`, `.env.production`):

```env
# Application
NODE_ENV=production
APP_URL=https://yourdomain.com
API_URL=https://api.yourdomain.com

# Supabase (Self-Hosted)
SUPABASE_URL=http://supabase:8000
SUPABASE_ANON_KEY=your_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
SUPABASE_DB_URL=postgresql://postgres:password@postgres:5432/postgres

# Database
DATABASE_URL=postgresql://postgres:password@postgres:5432/postgres
DIRECT_URL=postgresql://postgres:password@postgres:5432/postgres

# Authentication
JWT_SECRET=your_jwt_secret_min_32_chars
JWT_EXPIRY=3600

# Discourse Integration
DISCOURSE_API_KEY=your_discourse_api_key
DISCOURSE_BASE_URL=https://discourse.yourdomain.com
DISCOURSE_API_USERNAME=system
DISCOURSE_SSO_SECRET=your_sso_secret

# File Storage
STORAGE_BUCKET=toloka-uploads
STORAGE_URL=https://storage.yourdomain.com

# Email
SMTP_HOST=smtp.yourdomain.com
SMTP_PORT=587
SMTP_USER=your_smtp_user
SMTP_PASS=your_smtp_password
SMTP_FROM=noreply@yourdomain.com

# Payments (Stripe)
STRIPE_SECRET_KEY=sk_live_...
STRIPE_PUBLISHABLE_KEY=pk_live_...
STRIPE_WEBHOOK_SECRET=whsec_...

# Redis
REDIS_URL=redis://redis:6379

# Monitoring
SENTRY_DSN=your_sentry_dsn
LOG_LEVEL=info
```

**Validation**:

- All required variables must be set before deployment
- Use strong, unique secrets (generate with `openssl rand -hex 32`)
- Never commit `.env` files to version control
- Use secrets management in production (HashiCorp Vault, AWS Secrets Manager)

### Database Setup & Migrations

**Initial Database Setup**:

1. **Start PostgreSQL** (via Supabase Docker Compose)

   ```bash
   cd supabase
   docker-compose up -d postgres
   ```

2. **Run Prisma migrations**

   ```bash
   cd ..
   npx prisma migrate deploy
   ```

3. **Generate Prisma Client**

   ```bash
   npx prisma generate
   ```

4. **Seed initial data** (optional)

   ```bash
   npx prisma db seed
   ```

**Migration Workflow**:

- **Development**: Use `prisma migrate dev` (creates migration files)
- **Production**: Use `prisma migrate deploy` (applies existing migrations)
- **Rollback**: Use `prisma migrate resolve --rolled-back <migration_name>`

**Important Notes**:

- Always backup database before migrations in production
- Test migrations in staging environment first
- Supabase migrations go in `supabase/migrations/` directory
- Run Supabase migrations: `supabase db reset` (dev) or `supabase migration up` (prod)

### Supabase Self-Hosting Configuration

**Docker Compose Setup**:

1. **Navigate to Supabase directory**

   ```bash
   cd supabase
   ```

2. **Copy environment template**

   ```bash
   cp .env.example .env
   ```

3. **Configure `config.toml`**
   - Set `API_EXTERNAL_URL` to your domain
   - Configure `DB_POOL` for connection pooling
   - Set `JWT_SECRET` (must match application JWT_SECRET)
   - Configure email settings

4. **Start Supabase services**

   ```bash
   docker-compose up -d
   ```

5. **Verify services are running**

   ```bash
   docker-compose ps
   ```

**Service Dependencies**:

Services must start in this order:

1. PostgreSQL
2. Redis
3. Kong
4. PostgREST
5. GoTrue (Auth)
6. Realtime
7. Storage
8. Edge Functions

**Common Configuration Issues**:

- **Port conflicts**: Ensure ports 5432, 6379, 8000, 54321 are available
- **Memory limits**: Increase Docker memory allocation if services fail to start
- **Network issues**: Ensure all services are on the same Docker network
- **JWT mismatch**: Verify JWT_SECRET matches between Supabase and application

### Authentication & SSO Configuration

**Supabase Auth Setup**:

1. **Configure OAuth providers** (in Supabase Dashboard or `config.toml`)

   ```toml
   [auth.external.google]
   enabled = true
   client_id = "your_google_client_id"
   client_secret = "your_google_client_secret"
   ```

2. **Set up email templates**
   - Customize email templates in Supabase Dashboard
   - Configure SMTP settings (see Environment Configuration)

3. **Configure password policies**
   - Set minimum password length
   - Enable password complexity requirements

**Discourse SSO Integration**:

1. **Enable SSO in Discourse**
   - Admin → Settings → Login → Enable SSO provider

2. **Configure SSO endpoint in Toloka API**
   - Implement `/api/auth/discourse-sso` endpoint
   - Validate user session from Supabase
   - Generate SSO payload with Discourse secret
   - Redirect to Discourse with SSO token

3. **Test SSO flow**
   - Login to Toloka platform
   - Click "View Discussion" on any content
   - Should automatically authenticate in Discourse

### Discourse Integration Setup

**Discourse Deployment**:

1. **Deploy Discourse** (Docker recommended)

   ```bash
   git clone https://github.com/discourse/discourse_docker.git
   cd discourse_docker
   ./discourse-setup
   ```

2. **Configure Discourse**
   - Set domain name
   - Configure email service
   - Set up SSL certificates

3. **Generate API key**
   - Admin → API → Generate new key
   - Store in `DISCOURSE_API_KEY` environment variable (see [Environment Configuration](#environment-configuration))

4. **Configure SSO** (see [Discourse SSO Integration](#authentication--sso-configuration) section below)

**API Integration**:

- Test API connection: `curl -X GET "https://discourse.yourdomain.com/admin/api/keys.json" -H "Api-Key: YOUR_KEY" -H "Api-Username: system"`
- Create test topic via API to verify integration
- Set up webhook handlers for Discourse events (optional)

### Testing & Quality Assurance

**Unit Testing**:

```bash
# Run unit tests
npm run test

# Run with coverage
npm run test:coverage
```

**Integration Testing**:

```bash
# Start test database
docker-compose -f docker-compose.test.yml up -d

# Run integration tests
npm run test:integration
```

**E2E Testing**:

```bash
# Start full stack for testing
docker-compose up -d

# Run E2E tests
npm run test:e2e
```

**Test Data Management**:

- Use Prisma seed scripts for test data
- Reset test database between test runs
- Use factories for generating test entities

**Quality Gates**:

- All tests must pass before deployment
- Code coverage must be >80% for new code
- Linting must pass (`npm run lint`)
- Type checking must pass (`npm run type-check`)

### Deployment Checklist

**Pre-Deployment**:

- [ ] All environment variables configured
- [ ] Database migrations tested and ready
- [ ] Supabase services running and healthy
- [ ] Discourse instance deployed and accessible
- [ ] SSL certificates configured
- [ ] DNS records pointing to server
- [ ] Firewall rules configured
- [ ] Backups configured
- [ ] Monitoring tools installed

**Deployment Steps**:

1. **Build application**

   ```bash
   npm run build
   ```

2. **Start services**

   ```bash
   docker-compose -f docker-compose.prod.yml up -d
   ```

3. **Run database migrations**

   ```bash
   npx prisma migrate deploy
   ```

4. **Verify health endpoints**

   ```bash
   curl https://api.yourdomain.com/health
   ```

5. **Test critical user flows**
   - User registration
   - Project creation
   - Application submission
   - Discourse topic creation

**Post-Deployment**:

- [ ] Monitor error logs
- [ ] Verify all services are running
- [ ] Test authentication flows
- [ ] Verify Discourse integration
- [ ] Check database connections
- [ ] Verify file uploads work
- [ ] Test email delivery

### Common Issues & Troubleshooting

**Database Connection Issues**:

- **Symptom**: "Connection refused" or timeout errors
- **Solution**:

  - Verify PostgreSQL is running: `docker-compose ps`
  - Check connection string in `.env`
  - Verify network connectivity between services
  - Check firewall rules

**Supabase Services Not Starting**:

- **Symptom**: Services crash or fail to start
- **Solution**:
  - Check Docker logs: `docker-compose logs [service-name]`
  - Verify environment variables in `config.toml`
  - Check available disk space
  - Verify port availability

**Discourse API Errors**:

- **Symptom**: 401 Unauthorized or 403 Forbidden
- **Solution**:
  - Verify API key is correct
  - Check API username matches configured user
  - Verify Discourse instance is accessible
  - Check API rate limits

**Authentication Failures**:

- **Symptom**: Users cannot login or SSO fails
- **Solution**:
  - Verify JWT_SECRET matches between services
  - Check Supabase Auth configuration
  - Verify OAuth provider credentials
  - Check session cookie settings

**Performance Issues**:

- **Symptom**: Slow API responses or timeouts
- **Solution**:

  - Check database query performance (use EXPLAIN ANALYZE)
  - Verify Redis caching is working
  - Check server resource usage
  - Review database indexes
  - Enable query logging

### Monitoring & Maintenance

**Health Monitoring**:

Implement health check endpoints:

- `/health` - Basic application health
- `/health/db` - Database connectivity
- `/health/redis` - Redis connectivity
- `/health/discourse` - Discourse API connectivity

**Logging Setup**:

- **Application Logs**: Use structured logging (Winston, Pino)
- **Access Logs**: Configure Traefik access logs
- **Error Tracking**: Integrate Sentry for error monitoring
- **Log Aggregation**: Use Loki + Grafana for centralized logging

**Metrics to Monitor**:

- API response times
- Database query performance
- Error rates
- Active user sessions
- Disk space usage
- Memory usage
- CPU utilization

**Backup Strategy**:

- **Database**: Daily automated backups (pg_dump)
- **File Storage**: Regular S3/Supabase Storage backups
- **Configuration**: Version control all config files
- **Retention**: Keep 30 days of backups, weekly archives

**Maintenance Tasks**:

- **Weekly**: Review error logs, check disk space
- **Monthly**: Review and optimize database queries
- **Quarterly**: Security audit, dependency updates
- **As needed**: Apply security patches, update dependencies

**Alerting**:

Configure alerts for:

- Service downtime
- High error rates (>1% of requests)
- Database connection failures
- Disk space <20% remaining
- Memory usage >90%

---

**Navigation**: [← Previous: Design System](#design-system) | [↑ Back to Top](#table-of-contents)

---
