# Confluence Space Efficiency Blueprint

## Goal and Operating Principles
This blueprint is designed for a single team space that must support:
- Standard recurring team meetings
- Weekly 1:1s
- Monthly financial close status tracking
- SOPs and work instructions
- Project management and execution

Design principles:
1. **One-click entry points** from the homepage
2. **Structured content types** (templates + labels + page properties)
3. **Predictable archive strategy** for old meetings/projects
4. **Dashboard-driven status visibility** over manual browsing
5. **Minimal clicks to update recurring processes**

---

## Page Tree Option 1: Operating Rhythm First (Best for leadership visibility)
```
Home
├── 1) Team Rhythm
│   ├── Team Meetings
│   │   ├── 2026
│   │   │   ├── 2026-01-08 Team Meeting
│   │   │   └── ...
│   ├── 1:1 Meetings
│   │   ├── Manager A
│   │   │   ├── Employee A
│   │   │   │   ├── 2026-01-09 1:1
│   │   │   │   └── ...
│   └── Monthly Financial Close
│       ├── FY26
│       │   ├── 2026-01 Close
│       │   └── ...
├── 2) SOPs & Work Instructions
│   ├── Finance SOPs
│   ├── Operational SOPs
│   ├── Work Instructions by System
│   └── Policy and Controls
├── 3) Projects
│   ├── Active Projects
│   ├── Intake & Prioritization
│   └── Completed Projects
└── 4) Reporting & Dashboards
    ├── KPI Dashboard
    ├── Risks & Issues Register
    └── Decision Log
```

**How to use:**
- Best when your team cadence is the center of operations.
- Homepage highlights links to Team Rhythm + current month close + active projects.
- Monthly close pages include checklist, blockers, and sign-off.

**Best macros/tools:**
- `Page Properties` + `Page Properties Report` for meeting action tracking and close status rollups.
- `Task Report` for open action items from meeting pages.
- `Status` macro for Red/Amber/Green close and project states.
- `Children Display` for year/month navigation.
- `Roadmap Planner` (or Jira Roadmap integration) for projects.

---

## Page Tree Option 2: Process First (Best for SOP-heavy environments)
```
Home
├── 1) Core Processes
│   ├── Financial Close
│   │   ├── Process Overview
│   │   ├── Monthly Runs
│   │   └── Metrics & SLAs
│   ├── Team Meeting Process
│   └── 1:1 Process
├── 2) SOP Library
│   ├── By Function
│   ├── By System
│   ├── By Role
│   └── Retired SOPs (Archive)
├── 3) Work Execution
│   ├── Action Tracker
│   ├── Projects Portfolio
│   └── Risks, Dependencies, Decisions
└── 4) Governance
    ├── RACI
    ├── Audit Evidence
    └── Controls Testing
```

**How to use:**
- Each process owns its own SOPs, templates, metrics, and evidence pages.
- Team members start from process pages, not organization pages.
- Strong fit for controlled environments and audit readiness.

**Best macros/tools:**
- `Excerpt` + `Excerpt Include` to reuse standardized process snippets.
- `Expand` for long SOP sections (keep pages scannable).
- `Panel` for warnings, prerequisites, and control points.
- `Content by Label` for dynamic SOP indexes.
- `Attachments` + naming standards for audit evidence packs.

---

## Page Tree Option 3: Portfolio + Delivery First (Best for project-heavy teams)
```
Home
├── 1) Portfolio Overview
│   ├── Strategic Initiatives
│   ├── BAU Improvements
│   └── Intake Backlog
├── 2) Project Workspaces
│   ├── Project Alpha
│   │   ├── Charter
│   │   ├── Plan & Timeline
│   │   ├── RAID Log
│   │   └── Meeting Notes
│   └── Project Beta
├── 3) Team Operations
│   ├── Team Meetings
│   ├── 1:1s
│   └── Operating Metrics
└── 4) Knowledge Base
    ├── SOPs
    ├── Work Instructions
    └── Lessons Learned
```

**How to use:**
- Projects are first-class citizens with consistent project workspace templates.
- All recurring meetings still preserved in Team Operations.
- Lessons learned feed back into SOP improvements.

**Best macros/tools:**
- Jira Issue/Filter macros embedded in each project workspace.
- `Decision` macro for architectural and process decisions.
- `Page Tree` macro inside each project root page.
- `Status` and `Date` macros for milestone health.
- Whiteboards for planning and retrospectives.

---

## Page Tree Option 4: Role-Based Navigation (Best for cross-functional adoption)
```
Home
├── 1) For Managers
│   ├── Team Meeting Hub
│   ├── 1:1 Hub
│   └── People Action Tracker
├── 2) For Finance Team
│   ├── Monthly Close Hub
│   ├── Reconciliation SOPs
│   └── Reporting Calendar
├── 3) For Individual Contributors
│   ├── Work Instructions
│   ├── Daily/Weekly Checklists
│   └── Training & Onboarding
├── 4) For PM/Project Leads
│   ├── Portfolio Dashboard
│   ├── Project Templates
│   └── RAID & Decision Registers
└── 5) Shared Knowledge
    ├── Policies
    ├── Glossary
    └── FAQ
```

**How to use:**
- Homepage has role cards; users enter through “their lane.”
- Reduces confusion in large teams with mixed responsibilities.
- Governance pages under Shared Knowledge to maintain one source of truth.

**Best macros/tools:**
- `Livesearch` for role-specific findability.
- `Navitabs`-style app (if marketplace allowed) for hub pages.
- `Info`, `Note`, and `Warning` panels for role guidance.
- `Recently Updated` macro for role hubs.

---

## Page Tree Option 5: Hybrid Hub-and-Spoke (Best all-around recommendation)
```
Home (Command Center)
├── Hubs
│   ├── Meetings Hub
│   │   ├── Team Meetings
│   │   └── 1:1 Meetings
│   ├── Financial Close Hub
│   │   ├── Close Calendar
│   │   ├── Monthly Close Runs
│   │   └── Close Issues Log
│   ├── SOP & WI Hub
│   │   ├── SOP Index
│   │   ├── Work Instructions Index
│   │   └── Change Log
│   └── Projects Hub
│       ├── Portfolio Dashboard
│       ├── Active Projects
│       └── Project Archive
├── Shared Registers
│   ├── Action Register
│   ├── RAID Register
│   └── Decision Register
└── Archive
    ├── Meetings Archive
    ├── Close Archive
    ├── SOP Archive
    └── Project Archive
```

**How to use:**
- Home is a command center with KPIs, upcoming deadlines, and “create new” buttons.
- Hubs are functional entry points; registers provide cross-cutting visibility.
- Archive is explicit, preventing active areas from becoming cluttered.

**Best macros/tools:**
- `Page Properties Report` on each hub for standardized rollups.
- `Task Report` filtered by labels (e.g., `team-meeting`, `close`, `project`).
- `Content by Label` for dynamic indexes.
- `Create from Template` buttons on hub pages.
- Jira integration for portfolio/project status.

---

## Recommended Macro and Tool Stack (for visual clarity + usability)
Use these across all page tree options:

1. **Navigation and discovery**
   - `Children Display`, `Page Tree`, `Content by Label`, `Livesearch`
2. **Status and action tracking**
   - `Status`, `Task List`, `Task Report`, `Date`, `Decision`
3. **Structured reporting**
   - `Page Properties`, `Page Properties Report`
4. **Readable SOP formatting**
   - `Panel`, `Expand`, `Excerpt`, `Excerpt Include`, `Table of Contents`
5. **Project execution**
   - Jira Issue/Filter macros, Roadmap macro (native/app), Whiteboards
6. **Automation add-ons (if allowed)**
   - Comala Document Management (approvals)
   - Scroll Documents / Scroll PDF Exporter (publishing)
   - Automation for Confluence (auto-labeling, reminders)

---

## What content each major page should contain

### Home (Command Center)
- Space purpose + ownership
- Quick links: Meetings, 1:1s, Monthly Close, SOPs, Projects
- “Create New” buttons from templates
- KPI snapshot + current close status
- Overdue actions widget (Task Report)

### Team Meeting page template output
- Objective and attendees
- Agenda table
- Notes by agenda item
- Action items with owner and due date
- Decision log snippet
- Page Properties block (meeting date, facilitator, status)

### 1:1 page template output
- Private/shared expectations section
- Progress since last 1:1
- Current priorities and blockers
- Development/coaching notes
- Action commitments before next 1:1

### Monthly Financial Close page template output
- Month-end timeline and milestones
- Checklist by process stream
- Owner matrix (RACI-lite)
- Issue/blocker log with severity and aging
- Sign-off section and retrospective notes

### SOP/Work Instruction page template output
- Purpose, scope, owner
- Preconditions and inputs
- Step-by-step instructions (with screenshots)
- Exception handling
- Control/audit notes
- Revision history

### Project workspace root page output
- Project charter summary
- Scope / out-of-scope
- Milestone timeline + dependencies
- RAID section
- Linked Jira board/filter
- Weekly status summary and decisions

---

## Templates to create (high-value starter set)
1. Team Meeting Notes
2. Weekly 1:1 Notes
3. Monthly Close Runbook
4. Close Issue Log Entry
5. SOP Template
6. Work Instruction Template
7. Project Charter
8. Project Weekly Status Report
9. RAID Log Entry
10. Decision Record
11. Action Log Entry
12. Retrospective / Lessons Learned
13. Onboarding Checklist
14. Process Change Request
15. Audit Evidence Record

Template standards:
- Mandatory metadata block (Owner, Date, Status, Process, Labels)
- Consistent label taxonomy (e.g., `meeting-note`, `one-on-one`, `close-cycle`, `sop`, `project`)
- Pre-inserted Page Properties for rollups
- “Related links” section at bottom

---

## Implementation sequence (recommended 30-day rollout)
1. Build Home + Hub pages + template set
2. Configure labels and Page Properties standards
3. Migrate current SOPs and top 3 recurring meetings
4. Stand up Monthly Close hub + first close cycle page
5. Launch project workspace template and pilot on one project
6. Add archive rules and quarterly housekeeping routine

---

## Final recommendation
Choose **Option 5 (Hybrid Hub-and-Spoke)** for most teams because it balances recurring operations (meetings, 1:1s, close), structured knowledge (SOP/WI), and project execution while staying intuitive for new users.
