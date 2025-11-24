# Toloka App 
MVP Technical Specification
## Reviving Mutual Aid Through Technology

## 1. Project Overview

### Core Concept:
The Toloka application revives the traditional Central European concept of communal work parties ("toloka"), creating a digital platform that connects DIY project owners with skilled volunteers, learners, and mentors. It fosters mutual aid and skill-sharing within communities, ensuring that knowledge and resources circulate efficiently.

### Initial Target:
- **Location:** Marcinów, Zadzim, Poland
- **Ecosystem:** Connected to an existing makerspace and the 7-hectare Enklava protopia project, leveraging established networks and visitor experiences.

### Primary Use Cases:
| User Type | Purpose |
|-----------|---------|
| DIY Investors | Seeking skilled volunteers for hands-on projects |
| Learners | Gaining practical skills through real-world experience |
| Teachers/Mentors | Sharing expertise and building a reputation |
| Virtual Community Members | Connecting with purpose-driven projects |

## 2. Technical Architecture

### Platform Type:
Responsive web application (browser-based).

### Technical Stack:
- **Frontend/Backend:** Next.js framework
- **Authentication:** Phone number verification
- **Notifications:** In-app notification system
- **Hosting:** Beginner-friendly service (e.g., Vercel, Netlify)
- **Analytics:** Plausible Analytics
- **Payment Processing:** Integrated with Easy.Tools
- **Community Discussions:** Discourse integration

### Language Support:
- **MVP:** Polish only
- **Future:** Community-powered translations (similar to LocalFoodNodes)

## 3. User Roles & Registration

### Primary User Roles:
- DIY Investor
- Learner
- Teacher/Mentor
- Community Manager
- Hub Moderator (for local groups)

### User Registration Process:
Users will be required to provide basic information:

- First Name
- Surname
- Email
- Mobile
- Address (for community map display)

## 4. Core Features

### 4.1 Project Creation & Management

#### Initial Project Types:
- Yurt Design & Build
- Sauna Design & Build
- Natural Swimming Pool Design & Build

#### Project Creation Workflow:
**Initial Information:**
- Project Name
- Project Type/Category
- Brief Description
- Location Details (with map marking)
- Introductory Information

**Key Dates:**
- Start Date
- End Date
- Recruitment Deadline
- Results Announcement Date

**Accommodation Options:**
- Tent Field
- Indoor Accommodation
- None (with alternative information)

**Required Skills:**
- Minimum two skills required
- Initial skill types:
  - Power Tool Operation
  - Physical Fitness
  - AutoCAD Proficiency
  - SketchUp Proficiency
- Skill Level Importance Rating: 1-6 scale
- Option to add additional skills

**Additional Project Information:**
- Daily Schedule
- Supplementary Information
- Photo Uploads
- FAQ Section

**Project Structure:**
- Form Type: Volunteer / Paid Work
- Number of Candidates Needed

### 4.2 Skill Matching & Participation

**Skill Marketplace Features:**
- User skill profile creation
- Project skill requirement matching
- Experience-based skill validation

**Participation Workflow:**
- Application process for interested participants
- Host review and selection system
- Participation confirmation
- Post-project feedback and rating

### 4.3 Communication Features
- Direct messaging between users
- Discussion threads under project profiles
- Technical topic discussions via Discourse integration

### 4.4 Feedback & Reputation

**Rating System:**
- 5-star rating system for overall experience
- Optional short text feedback

**Experience Points (XP):**
- XP awarded for project completion
- Progressive levels (Beginner, Practitioner, Expert)
- Future gamification foundation (badges, leaderboards)

## 5. Administrative Features

### 5.1 User Management:
- User filtering and search
- Profile viewing/editing
- User suspension/ban functionality
- Role assignment management
- Bulk user operations

### 5.2 Project Management:
- Project approval workflow
- Project listing with filtering
- Project editing/moderation
- Project analytics
- Featured project designation

### 5.3 Content Management:
- Static page editing
- Resource library management
- Community announcements
- Comment/discussion moderation
- Content flagging review

## 6. Monetization Strategy

### Freemium Model:
- Free core skill-matching
- Paid premium features for project promotion

### Revenue Streams:
- Project listing fees for premium placement
- Affiliated book/resource sales
- Integration with Easy.Tools payment system

## 7. Assumptions & Validation Strategies

| Critical Assumption | Validation Strategy |
|---------------------|---------------------|
| Users will volunteer time/skills for mutual benefit | User surveys and pilot program engagement in Marcinów |
| Polish users will value the "toloka" heritage | Early adoption metrics and cultural relevance feedback |
| DIY investors will pay for premium features | A/B testing on premium feature demand with early users |
| Integration with publishing resources adds value | Analytics-driven content tracking of resource usage |
| The model can expand beyond initial pilot area | Targeted outreach to neighboring communities with metrics tracking |

## 8. Future Expansion Plans
- Advanced gamification (badges, leaderboards)
- Multilingual support via community translation
- Search & discovery features
- Enhanced analytics & reporting
- Mobile app development

## 9. Implementation Timeline

### MVP Development:
- Next.js platform development
- Integration with Discourse & payment system
- Testing with initial project types
- Launch in Marcinów, Zadzim

### Post-MVP Iteration:
- User feedback collection and implementation
- Feature prioritization based on usage data
- Expansion to additional regions

## 10. Opportunity-Solution Tree
(Adapted from Teresa Torres' Framework)

| Opportunity | Solution |
|-------------|----------|
| Limited access to skilled volunteers | Skill marketplace and project-matching system |
| Lack of hands-on learning opportunities | Structured DIY project-based education |
| Weak community engagement | Discourse forum & direct messaging |

## 11. Historical Context
Toloka – a fading Polish rural tradition of voluntary neighborly assistance during tasks like harvests. It begins with ceremonial invitations and ends with feasts, music, and dance. Beyond a mere custom, tłoka represents a ritual system rooted in mutual aid for the common good. While collaborative farming exists worldwide, tłoka holds unique spiritual significance in Central Europe, tied to ancestral traditions, as seen in Belarusian practices. Notably, the term tłoka appears in Belarusian, Lithuanian, Polish, Prussian, and Ukrainian cultures. Its influence on shaping the Rzeczpospolita – a historic multicultural and tolerant federation – is still debated. The geographic reach of this former state closely mirrors tłoka’s historical spread. The decline of both coincided with eroded solidarity. The word’s origin is disputed: some trace it to Prussian Talk (payment through hospitality), while Władysław Kopaliński links it to tłok (a crowd of helpers). Polish sociologist Florian Znaniecki saw tłoka as part of a broader solidarity uniting life against mortality. Though fading today, tłoka resurfaces unexpectedly – like during Belarus’s 1980s-90s revival, when the group Tałaká emerged. Reviving such traditions could help Central Europe balance modernity with heritage, resisting cultural homogenization. Toloka’s principles invite study not just as history, but as a framework for rebuilding post-communist identities through shared spiritual roots.

## 12. Conclusion
Toloka is a modern revival of traditional communal work practices, connecting project owners with skilled volunteers while preserving cultural heritage. Through continuous improvement and user-driven iteration, it has the potential to expand internationally, promoting decentralized collaboration worldwide.
