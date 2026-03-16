# Confluence Space Blueprint: Meetings, Financial Close, Projects, Knowledge Base

## Space Vision
Create a **single Confluence command center** where teams can:
- Run recurring meetings with consistent notes and follow-through.
- Manage monthly/quarterly close activities with clear ownership and status.
- Execute projects with transparent milestones, risks, and decisions.
- Build a searchable, trusted knowledge base of SOPs and work instructions.

---

## Recommended Space Architecture (Hub-and-Spoke)

```text
Home (Command Center)
├── 1) Meetings Hub
│   ├── Team Meetings
│   │   ├── 2026
│   │   │   ├── 2026-01-08 Team Meeting
│   │   │   └── ...
│   ├── 1:1 Meetings
│   │   ├── Manager Name
│   │   │   ├── Employee Name
│   │   │   │   ├── 2026-01-09 1:1
│   │   │   │   └── ...
│   └── Meeting Action Register
├── 2) Financial Close Management Hub
│   ├── Close Calendar
│   ├── Monthly Close Runs
│   │   ├── FY26
│   │   │   ├── 2026-01 Close
│   │   │   └── ...
│   ├── Reconciliation Tracker
│   ├── Close Issues & Blockers
│   └── Sign-off & Audit Evidence
├── 3) Projects Hub
│   ├── Portfolio Dashboard
│   ├── Active Projects
│   │   ├── Project Name
│   │   │   ├── Charter
│   │   │   ├── Plan & Timeline
│   │   │   ├── RAID Log
│   │   │   └── Project Meetings
│   └── Completed Projects
├── 4) Knowledge Base Hub
│   ├── SOP Library
│   ├── Work Instructions
│   ├── Policies & Controls
│   ├── FAQ
│   └── Glossary
└── 5) Archive
    ├── Meetings Archive
    ├── Close Archive
    ├── Projects Archive
    └── Knowledge Archive
```

---

## Home Page (Command Center) Layout

Build the homepage in sections so users can scan and act in under 30 seconds.

### Section A: Hero + Quick Actions
Use:
- **Panel macro** (Info style) for purpose and ownership.
- **Create from Template buttons** for:
  - New Team Meeting Note
  - New 1:1 Note
  - New Close Run
  - New Project Workspace
  - New SOP

### Section B: Health Snapshot
Use:
- **Status macros** for:
  - Close status (Green/Amber/Red)
  - Portfolio health
  - Open blockers count
- **Page Properties Report macro** to roll up active close runs and active projects.

### Section C: What needs attention
Use:
- **Task Report macro** filtered by labels (`meeting-action`, `close-task`, `project-action`).
- **Recently Updated macro** for last 7 days across key hubs.
- **Content by Label macro** for urgent content (`blocker`, `needs-decision`).

### Section D: Navigation tiles
Use either table cards or panels to link to:
- Meetings Hub
- Financial Close Management Hub
- Projects Hub
- Knowledge Base Hub
- Archive

---

## Hub Design and Macro Standards

## 1) Meetings Hub

### Purpose
Centralize all recurring meeting cadences and ensure actions are not lost.

### Required macros
- **Children Display** for year/month note navigation.
- **Task Report** for all open meeting actions.
- **Page Properties Report** for meeting rollups by facilitator/date/status.
- **Decision macro** for key outcomes.

### Labels to enforce
- `meeting`
- `team-meeting` or `one-on-one`
- `meeting-action`

### Meeting note template (recommended)
Sections:
1. Objective
2. Attendees
3. Agenda
4. Notes
5. Action items (tasks with owners and due dates)
6. Decisions
7. Page Properties block:
   - Meeting Date
   - Meeting Type
   - Facilitator
   - Follow-up Status

---

## 2) Financial Close Management Hub

### Purpose
Provide structured oversight of close execution, dependencies, and sign-off.

### Required macros
- **Page Properties + Page Properties Report** to roll up each close run.
- **Status macro** for phase health (Pre-close, Day 1, Reconciliation, Review, Sign-off).
- **Date macro** for due dates and milestones.
- **Task Report** for overdue close tasks.
- **Attachments macro** in Sign-off pages for audit evidence packs.

### Labels to enforce
- `financial-close`
- `close-run`
- `close-task`
- `reconciliation`
- `close-blocker`

### Monthly close run template
Sections:
1. Period and owner
2. Close checklist by phase
3. Critical dependencies
4. Blockers and escalations
5. Reconciliation status
6. Sign-off checklist
7. Evidence links
8. Page Properties block:
   - Close Period
   - Close Manager
   - Current Phase
   - RAG Status
   - Target Sign-off Date

---

## 3) Projects Hub

### Purpose
Run projects consistently while keeping portfolio visibility for leadership.

### Required macros
- **Page Tree macro** inside each project root page.
- **Status macro** for schedule/scope/budget health.
- **Decision macro** for governance decisions.
- **Jira Issue/Filter macros** for sprint and delivery tracking (if Jira is used).
- **Roadmap macro** (native/app) for milestone timeline.

### Labels to enforce
- `project`
- `active-project`
- `raid`
- `project-decision`

### Project workspace template
Pages:
- Charter
- Plan & Timeline
- RAID Log
- Stakeholder Communications
- Project Meetings
- Lessons Learned

Each root project page includes **Page Properties**:
- Project Owner
- Stage
- RAG Status
- Target End Date
- Strategic Priority

---

## 4) Knowledge Base Hub

### Purpose
Create a trusted source of SOPs, work instructions, and operational knowledge.

### Required macros
- **Table of Contents** for long SOP pages.
- **Expand** for detailed steps and edge-case handling.
- **Excerpt + Excerpt Include** for reusable standard text.
- **Content by Label** for dynamic indexes (SOPs by function/system).
- **Livesearch** for quick retrieval.

### Labels to enforce
- `sop`
- `work-instruction`
- `policy`
- `control`
- `kb`

### SOP template
Sections:
1. Purpose
2. Scope
3. Prerequisites
4. Procedure steps
5. Controls and exceptions
6. Related links
7. Change history
8. Page Properties block:
   - Document Owner
   - Effective Date
   - Review Date
   - Version
   - Approval Status

---

## Space-Wide Governance Rules

### Naming conventions
- Meeting page: `YYYY-MM-DD Team Meeting`
- 1:1 page: `YYYY-MM-DD Manager-Employee 1:1`
- Close page: `YYYY-MM Close`
- Project root: `Project - <Name>`
- SOP page: `SOP - <Process Name>`

### Archiving policy
- Meetings: move notes older than 12 months to Meetings Archive.
- Close runs: archive by fiscal year after annual audit completion.
- Projects: move completed projects 60 days after close-out.
- SOPs: move retired docs to Knowledge Archive with `retired` label.

### Access model
- Open read access for most team members.
- Restricted edit rights for controlled content (policies/sign-off pages).
- Use page restrictions only where compliance requires it.

---

## High-Productivity Macro Pack (install/use first)

1. **Page Properties** + **Page Properties Report** (structured rollups)
2. **Task Report** (global follow-up visibility)
3. **Status** + **Date** (health and timelines)
4. **Children Display** + **Page Tree** (clean navigation)
5. **Content by Label** + **Livesearch** (findability)
6. **Decision** (traceable governance)
7. **Panel**, **Expand**, **Table of Contents** (readability)
8. **Create from Template** (fast, standardized page creation)

---

## Implementation Plan (first 2 weeks)

### Week 1
- Create page tree skeleton and hub pages.
- Build and publish 5 templates:
  - Team Meeting
  - 1:1
  - Monthly Close Run
  - Project Workspace
  - SOP
- Add required labels and sample pages in each hub.

### Week 2
- Configure Page Properties Reports on Home + all hubs.
- Migrate existing key content into correct hubs.
- Add archive pages and update ownership metadata.
- Run team onboarding session (30 minutes) and publish usage guide.

---

## Definition of Done for Space Launch

The space is considered production-ready when:
- Home page shows real-time status rollups for meetings, close, and projects.
- All four hubs have templates, labels, and dashboard macros active.
- Task Report exposes open actions across all operational areas.
- Knowledge Base content is searchable by label and Livesearch.
- Archive strategy is documented and implemented.
