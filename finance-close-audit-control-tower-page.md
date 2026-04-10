h1. SECTION 1 — PAGE TITLE OPTIONS

# Finance Close & Audit Control Tower
# Finance Period-End Execution and Controls Dashboard
# Controller Close Command Center (Jira + Confluence)
# Finance Operations Control Tower — Monthly Close & Audit
# Finance Close Governance Hub — Execution, Review, and Evidence

----

h1. SECTION 2 — EXECUTIVE SUMMARY

{info:title=Executive Summary}
This page is the central management view for period-end close and audit control execution. It is designed for Controllers, process owners, reviewers, and Finance leadership who need a reliable, real-time view of work status, risks, and control evidence.

*Jira Data Center* is used as the system of execution (task ownership, due dates, workflow transitions, comments, and audit history). *Confluence Data Center* is used as the control tower and reporting layer (dashboarding, procedures, governance rules, and linked operational analytics through Jira macros).

This model replaces manually maintained task lists with automated Jira-driven reporting, improving accuracy, accountability, segregation of duties, and audit readiness.
{info}

----

h1. SECTION 3 — OPERATING MODEL OVERVIEW

h2. Beginner-Friendly Model: "Jira Executes, Confluence Governs"

* *Jira is where work happens.*
** Every close and audit task is created in Jira with an owner, due date, status, and reviewer.
** Team members update status directly in Jira as work progresses.
** Jira keeps the full audit trail (who changed what, and when).

* *Confluence is where management monitors and governs.*
** This page displays live Jira data using Jira macros.
** Leadership views KPIs, blocker queues, and review workload in one place.
** SOPs, policy guidance, escalation rules, and month-end setup instructions are documented here.

h2. Why This Is Better Than Confluence Tables for Task Maintenance

* Manual Confluence tables become outdated quickly.
* Manual updates do not enforce workflow controls.
* Manual records are weaker for audit evidence and user accountability.
* Jira workflow transitions enforce control points (for example, reviewer-only approval).
* Confluence macros display current Jira truth automatically, reducing reconciliation effort.

{note:title=Design Principle}
Confluence pages should *display and explain* close execution. Jira issues should *store and control* close execution.
{note}

----

h1. SECTION 4 — HOW JIRA SHOULD BE STRUCTURED

h2. Core Jira Concepts (for New Users)

* *Project*: A dedicated container for related work. For this solution, use one project for Finance Close and Audit Operations.
* *Board*: A visual view of issues in workflow stages (for example, Not Started, In Progress, In Review).
* *Epic*: A large parent work package (for example, one Epic per close cycle or functional close stream).
* *Task*: A standard execution item (for example, "Accrual Journal Preparation").
* *Sub-task*: A smaller component of a task (for example, "Extract SAP trial balance", "Upload support workbook").

h2. Recommended Hierarchy for Finance Close

# *Project*: FINCLOSE (Finance Close & Audit Operations)
# *Epic*: Monthly close cycle or major process stream
## Example: `FINCLOSE-EPIC-2026-03 Corporate Monthly Close`
# *Task*: Process steps owned by accountable individuals
## Example: `Prepare Revenue Accrual Journal — US01 — 2026-03`
# *Sub-task*: Optional detailed steps/checklist activities for complex tasks

h2. Recommended Project Strategy

* Use *one dedicated Jira project* for Finance Close / Audit Operations to standardize workflows, fields, permissions, and reporting.
* Optionally separate by issue security levels or components rather than creating many projects.

h2. Recommended Naming Conventions

* *Project Key*: `FINCLOSE`
* *Epic Name*: `<YYYY-MM> <Process/Entity> Close` (example: `2026-03 NA Controller Close`)
* *Task Summary*: `<Action Verb> <Deliverable> — <Entity/Site> — <YYYY-MM>`
* *Audit/PBC Task*: `PBC <Request ID> — <Artifact> — <Entity> — <Due Date>`

h2. Recommended Issue Types

* *Epic* — monthly close wave / audit wave
* *Task* — standard close and control activities
* *Sub-task* — optional detailed execution breakdown
* *(Optional)* Control Exception — dedicated type for repeat issues requiring remediation tracking

----

h1. SECTION 5 — RECOMMENDED JIRA FIELDS

|| Field Name || Purpose || Example Value || Required? ||
| Summary | Short, searchable work description | Prepare AP Accrual Journal — US01 — 2026-03 | Required |
| Description | Detailed instructions / definition of done | Reconcile AP aged balance, post accrual, attach support | Required |
| Assignee | Process owner responsible for execution | jsmith | Required |
| Reviewer | Control owner who reviews and approves | finance.reviewer1 | Required |
| Due Date | Completion target for execution/review | 2026-04-03 | Required |
| Status | Workflow state of the issue | In Progress | System/Required |
| Priority | Business criticality | High | Required |
| Close Period | Period tag for rollups and filtering | 2026-03 | Required |
| Entity | Legal entity / reporting unit | US01 | Required |
| Site | Site / cost center / location | Chicago Plant | Optional |
| Category | Process category for reporting | Journal Entry / Reconciliation / Variance Analysis / PBC | Required |
| Evidence Link | URL to source evidence in DMS/SharePoint/Confluence | https://... | Required before In Review |
| SAP Reference | ERP reference for traceability | SAP Doc 1900048127 | Optional (Required for JE category) |
| Recurring Task | Identifies repeat month-end activity | Yes | Required |
| Control Required | Indicates if reviewer approval gate is mandatory | Yes | Required |

{tip:title=Implementation Note}
Create *Close Period*, *Entity*, *Category*, *Recurring Task*, and *Control Required* as controlled-list custom fields to improve JQL consistency and dashboard reliability.
{tip}

----

h1. SECTION 6 — WORKFLOW DESIGN

h2. Status Set

* Not Started
* In Progress
* In Review
* Approved
* Rejected
* Blocked

h2. Execution Layer vs Control Layer

* *Execution Layer statuses*: Not Started, In Progress, Blocked
* *Control Layer statuses*: In Review, Approved, Rejected

h2. A) Simple Workflow Diagram (Text)

{code}
Not Started --> In Progress --> In Review --> Approved
                    |             |
                    v             v
                 Blocked <----- Rejected

Blocked --> In Progress
Rejected --> In Progress
{code}

h2. B) Role-Based Transition Matrix

|| From Status || To Status || Process Owner || Reviewer || Notes ||
| Not Started | In Progress | Yes | No | Execution begins |
| In Progress | Blocked | Yes | Yes | Use when dependency/risk prevents progress |
| Blocked | In Progress | Yes | Yes | Resume after blocker is resolved |
| In Progress | In Review | Yes | No | Evidence + comments required |
| In Review | Approved | No | Yes | Reviewer-only control gate |
| In Review | Rejected | No | Yes | Reviewer returns item with deficiencies |
| Rejected | In Progress | Yes | No | Owner remediates and resubmits |

h2. C) Plain-English Guidance for New Jira Users

* Process owners do the work and submit it for review.
* Reviewers do not execute the task; they verify completeness and control quality.
* Only reviewers can mark a task Approved.
* If work cannot proceed, mark Blocked immediately and add a blocker comment with owner + ETA.
* If review fails, reviewer sets Rejected and explains what must be corrected.

----

h1. SECTION 7 — ROLE PERSPECTIVE

h2. A. PROCESS OWNER PERSPECTIVE

h3. What the Process Owner Does

* Executes assigned close/audit tasks in Jira.
* Maintains accurate status and timing updates.
* Provides complete evidence before requesting review.

h3. Day-to-Day Jira Usage

# Open "My Open Close Tasks" filter.
# Start work by moving items from Not Started to In Progress.
# Update comments for key progress or delays.
# Move task to In Review only after completion criteria are met.

h3. Before Moving to *In Review*, the Owner Must

* Attach or link evidence (Evidence Link field complete).
* Add SAP Reference where applicable.
* Confirm Description checklist / definition of done is satisfied.
* Add a concise handoff comment: what was done, what evidence is attached, any assumptions.

h3. Handling Blocked Items

* Move status to Blocked immediately.
* Add blocker reason, dependency owner, impact, and target resolution date.
* Notify reviewer/manager via @mention comment.
* Return to In Progress as soon as blocker clears.

h3. What the Process Owner Is *Not* Allowed To Do

* Must not set Approved status.
* Must not self-review tasks where they are the assignee.
* Must not move items to In Review without evidence.
* Must not close tasks outside defined workflow transitions.

h2. B. REVIEWER PERSPECTIVE

h3. What the Reviewer Does

* Monitors incoming In Review queue.
* Performs control validation for completeness, accuracy, and policy adherence.
* Approves compliant tasks or rejects with actionable feedback.

h3. How Reviewers Monitor Their Queue

* Use Confluence "Reviewer Queue" macro and Jira filter `reviewer = currentUser()`.
* Prioritize oldest and highest-risk items first.
* Review daily during close window; increase cadence near close deadline.

h3. What Reviewers Validate

* Right owner completed task.
* Required evidence exists and is readable.
* SAP / source-system references align to evidence.
* Output meets documented policy/SOP requirements.
* No unresolved exceptions remain.

h3. Approve vs Reject Rules

* *Approve* when all control requirements are satisfied and evidence is sufficient.
* *Reject* when evidence is missing/inadequate, calculation is incorrect, or policy steps are not followed.

h3. Reviewer Commenting Standard

* Approval comment should include: scope reviewed, evidence checked, date/time, conclusion.
* Rejection comment should include: specific deficiency, remediation required, and re-review expectation.

h3. Internal Control Rationale

This model enforces segregation of duties: the owner executes, the reviewer validates. Workflow permissions and reviewer-only approval preserve control integrity and improve external/internal audit confidence.

----

h1. SECTION 8 — MONTHLY TASK RECREATION WITH MINIMAL EFFORT

h2. Recommended First Implementation Approach

Start with a stable "model month" Epic and clone from it each period. Keep design simple before adding advanced automation.

h2. Using Prior Month Epic as the Model

# Select prior month Epic (for example, `2026-02 NA Controller Close`).
# Clone Epic and all child tasks.
# Update Close Period, due dates, and assignments for current month.
# Validate recurring flags and reviewer assignments.
# Publish period links on this Confluence page.

h2. Cloning / Templating / Automation Concepts

* *Cloning*: Fast start, good for early maturity.
* *Templating*: Standard task library by process/entity.
* *Automation*: Scheduled rules create monthly issues automatically with field defaults and due date offsets.

h2. Phased Maturity Model

# *Manual but Efficient*:
## Clone prior Epic; bulk-edit dates/period; quick validation checklist.
# *Semi-Automated*:
## Use saved filters + bulk actions + partial automation (auto-set reviewer, category, defaults).
# *Fully Automated*:
## Scheduled automation generates monthly Epic/tasks from template logic, assigns owners, and notifies stakeholders.

h2. Recommended Month-End Setup Procedure

# T-7 business days: Clone/create next-period Epic and tasks.
# T-6: Validate assignments, reviewers, due dates, and control flags.
# T-5: Run dashboard smoke test (Execution, Control, Blocked, Overdue).
# T-4: Publish kickoff note in Confluence and confirm ownership.
# T-0 to T+5: Daily monitoring and blocker escalation.

----

h1. SECTION 9 — CONFLUENCE PAGE LAYOUT

h2. 1) Page Header
* *Purpose*: Define period context and ownership.
* *Recommended macro(s)*: Info, Status, Page Properties.
* *Example body content*: "Finance Close Control Tower for period YYYY-MM; Controller: <Name>; Last refresh: auto via Jira macros."

h2. 2) Executive Summary
* *Purpose*: Explain what this page is and who should use it.
* *Recommended macro(s)*: Info macro.
* *Example body content*: 3–5 lines describing Jira execution + Confluence governance model.

h2. 3) Operating Model
* *Purpose*: Clarify system-of-execution vs reporting layer.
* *Recommended macro(s)*: Expand, Panel.
* *Example body content*: Beginner explanation and roles.

h2. 4) Status Legend
* *Purpose*: Ensure consistent interpretation of workflow states.
* *Recommended macro(s)*: Table, Status lozenges.
* *Example body content*: Status definitions and ownership.

h2. 5) KPI Dashboard
* *Purpose*: Management summary of close health.
* *Recommended macro(s)*: Jira Chart, Jira Issues (count mode), Roadmap/Chart app if available.
* *Example body content*: % complete, blocked, overdue, in review.

h2. 6) Execution Layer Tasks
* *Purpose*: Show active execution work.
* *Recommended macro(s)*: Jira Issues macro (table).
* *Example body content*: Tasks in Not Started / In Progress / Blocked.

h2. 7) Control Layer Tasks
* *Purpose*: Show review-stage and outcome-state tasks.
* *Recommended macro(s)*: Jira Issues macro.
* *Example body content*: In Review / Approved / Rejected.

h2. 8) Reviewer Queue
* *Purpose*: Personal and team review workload.
* *Recommended macro(s)*: Jira Issues macro filtered by reviewer.
* *Example body content*: Items requiring reviewer action.

h2. 9) Blocked / Escalations
* *Purpose*: Highlight operational risk and required intervention.
* *Recommended macro(s)*: Jira Issues macro + Task Report or excerpt panel.
* *Example body content*: Blocked items with blocker owner and ETA.

h2. 10) Monthly Cycle Instructions
* *Purpose*: Standard work for monthly setup and monitoring.
* *Recommended macro(s)*: Expand, Numbered list, Decision/Task macros.
* *Example body content*: T-7 to T+5 runbook.

h2. 11) Governance Rules
* *Purpose*: Enforce controls and role boundaries.
* *Recommended macro(s)*: Warning, Info, Table.
* *Example body content*: Approval rights, evidence standards, escalation timelines.

h2. 12) Admin Notes / Future Enhancements
* *Purpose*: Track technical debt and maturity backlog.
* *Recommended macro(s)*: Expand, Task list.
* *Example body content*: planned automation phases and dashboard enhancements.

----

h1. SECTION 10 — JIRA MACRO / JQL DESIGN

{info:title=Usage Note}
Replace `YYYY-MM` with selected period. If possible, create a Confluence page variable for period and re-use it in macro filters.
{info}

h2. Execution Layer Macro (Tasks)
{code}
project = FINCLOSE
AND "Close Period" = "YYYY-MM"
AND status in ("Not Started", "In Progress", "Blocked")
ORDER BY due date ASC, priority DESC
{code}

h2. Control Layer Macro (Tasks)
{code}
project = FINCLOSE
AND "Close Period" = "YYYY-MM"
AND status in ("In Review", "Approved", "Rejected")
ORDER BY status ASC, updated DESC
{code}

h2. Reviewer Queue Macro
{code}
project = FINCLOSE
AND "Close Period" = "YYYY-MM"
AND status = "In Review"
AND reviewer = currentUser()
ORDER BY due date ASC
{code}

h2. Blocked Items Macro
{code}
project = FINCLOSE
AND "Close Period" = "YYYY-MM"
AND status = "Blocked"
ORDER BY priority DESC, updated ASC
{code}

h2. Overdue Items Macro
{code}
project = FINCLOSE
AND "Close Period" = "YYYY-MM"
AND status not in ("Approved")
AND due <= now()
ORDER BY due ASC
{code}

h2. Approved Items Macro
{code}
project = FINCLOSE
AND "Close Period" = "YYYY-MM"
AND status = "Approved"
ORDER BY updated DESC
{code}

h2. Additional Personal Queue (Owner View)
{code}
project = FINCLOSE
AND "Close Period" = "YYYY-MM"
AND assignee = currentUser()
AND status in ("Not Started", "In Progress", "Blocked", "Rejected")
ORDER BY due date ASC
{code}

----

h1. SECTION 11 — DASHBOARD KPI DESIGN

|| KPI || Formula / Logic || What It Means || Why It Matters || Leadership Action if Unfavorable ||
| % Complete | Approved tasks / Total tasks for Close Period | Overall close completion health | Core close readiness indicator | Trigger daily stand-up and focus on remaining high-risk items |
| Open Tasks | Count of status in (Not Started, In Progress, In Review, Rejected, Blocked) | Remaining workload | Shows volume still requiring action | Rebalance workload across teams; add surge support |
| In Review Count | Count status = In Review | Review queue size | Signals potential control bottleneck | Assign backup reviewers or prioritize critical-path reviews |
| Blocked Count | Count status = Blocked | Dependency/risk concentration | Early warning for slippage and unresolved dependencies | Escalate blockers >24h to Controller and dependency owners |
| Rejected Count | Count status = Rejected | Quality/control defects in first submission | Indicates execution quality and rework burden | Launch targeted coaching and root-cause review |
| Overdue Count | Count due <= now() and status != Approved | Missed commitments | Direct risk to close timeline and reporting quality | Enforce recovery plan, daily escalation, leadership intervention |

{warning:title=Controller Signal Thresholds (Example)}
* Blocked Count > 5 or any critical-path blocked item > 24h
* Overdue Count > 0 after day T+2
* Rejected Count trending upward for same process over two cycles

When thresholds are breached, require same-day corrective action plan and owner accountability.
{warning}

----

h1. SECTION 12 — GOVERNANCE RULES

h2. Status Ownership

* Process Owner: Not Started -> In Progress -> In Review; manages Blocked and remediation after Rejected.
* Reviewer: In Review -> Approved or Rejected.
* Admins may perform exception transitions only under documented governance approval.

h2. Evidence Requirements

* Evidence Link must be populated before In Review.
* Evidence must be complete, traceable, and readable by reviewer.
* JE-related tasks should include SAP reference and tie-out details.

h2. Reviewer Requirements

* Reviewer cannot be same user as assignee for controlled tasks.
* Review comments must clearly document rationale.
* Reviewer must validate policy/SOP adherence, not only task completion.

h2. Commenting Standards

* Use structured comments: *Context / Action / Result / Next Step*.
* Rejections require explicit remediation instructions.
* Blocked comments require dependency owner + ETA.

h2. Escalation Rules (Blocked and Overdue)

* Blocked > 24 hours: escalate to process manager.
* Blocked > 48 hours or critical-path dependency: escalate to Controller.
* Overdue tasks: immediate escalation at daily close meeting.

h2. Why Only Reviewer Sets *Approved*

This preserves segregation of duties, prevents self-certification, and ensures control effectiveness is independently validated.

h2. Why Confluence Is Not the Source of Truth for Task Maintenance

Confluence dashboards are views of Jira data. Maintaining tasks in Confluence duplicates records, increases errors, and weakens audit defensibility. All task changes must occur in Jira.

----

h1. SECTION 13 — IMPLEMENTATION ROADMAP

h2. Phase 1: Foundational Setup (Weeks 1–2)

* Create FINCLOSE Jira project.
* Configure issue types and custom fields.
* Build baseline workflow and permissions.
* Publish first Confluence control tower page with core Jira macros.

h2. Phase 2: Workflow and Notifications (Weeks 3–4)

* Add notification rules for due-date risk, blocked transitions, and review queue alerts.
* Train process owners and reviewers on role-specific behavior.
* Stabilize month-end operating cadence.

h2. Phase 3: Automation and Recurring Task Setup (Weeks 5–8)

* Implement cloning/templates for monthly cycle generation.
* Add automation for field defaults, assignment rules, and scheduled task creation.
* Improve data quality controls (required fields on transition).

h2. Phase 4: Executive Reporting Maturity (Weeks 9+)

* Add KPI trend views by period/entity/category.
* Add SLA-style performance views (review turnaround, blocker aging).
* Integrate leadership scorecards and audit-ready evidence drill-downs.

----

h1. SECTION 14 — ADMIN BUILD CHECKLIST

h2. Jira / Confluence Admin Checklist

* [ ] Create Jira project `FINCLOSE` with controlled permission scheme.
* [ ] Configure issue types: Epic, Task, Sub-task (and optional Control Exception).
* [ ] Create custom fields: Close Period, Entity, Site, Category, Reviewer, Evidence Link, SAP Reference, Recurring Task, Control Required.
* [ ] Build workflow statuses and transitions with reviewer-only approval.
* [ ] Configure board columns aligned to workflow.
* [ ] Add automation rules (notifications, defaults, recurring setup).
* [ ] Build Confluence page skeleton using this template.
* [ ] Insert and validate Jira macros and period filters.
* [ ] Validate security/permissions for assignees, reviewers, and leadership viewers.
* [ ] Deliver onboarding training and publish SOP quick guides.
* [ ] Run one pilot close cycle and capture lessons learned.

----

h1. SECTION 15 — APPENDICES

h2. A) Sample Task Examples for Monthly Close

|| Task Summary || Category || Owner || Reviewer || Due Date || Evidence Expected ||
| Prepare Revenue Accrual Journal — US01 — 2026-03 | Journal Entry | GL Accountant | Revenue Controller | 2026-04-02 | Journal support workbook + SAP document reference |
| Reconcile AP Clearing Accounts — US01 — 2026-03 | Reconciliation | AP Lead | Accounting Manager | 2026-04-03 | Reconciliation file + aging tie-out |
| Analyze Gross Margin Variance — NA — 2026-03 | Variance Analysis | FP&A Analyst | FP&A Manager | 2026-04-04 | Variance bridge + commentary pack |

h2. B) Sample Task Examples for Audit / PBC Requests

|| Task Summary || Category || Owner || Reviewer || Due Date || Evidence Expected ||
| PBC-014 — Fixed Asset Rollforward Support — US01 | PBC | Fixed Assets Accountant | External Audit Coordinator | 2026-04-06 | Rollforward workbook + GL tie-out |
| PBC-022 — Revenue Cutoff Sample Population — NA | PBC | Revenue Accounting Lead | Audit Manager | 2026-04-07 | Source report + sampling logic note |

h2. C) Sample Naming Conventions

* Epic: `2026-03 Corporate Monthly Close`
* Task: `Prepare Payroll Accrual JE — US01 — 2026-03`
* PBC Task: `PBC-031 — Lease Contract Listing — EMEA — 2026-03`
* Blocker comment tag: `[BLOCKER] <dependency> | owner: <name> | ETA: <date>`

h2. D) Sample Reviewer Comments

* *Approval Example*:
"Reviewed JE support and SAP Doc 1900048127; tie-out agrees to GL and period policy checklist is complete. Approved on 2026-04-03 14:20 UTC."

* *Rejection Example*:
"Rejected: Evidence file does not reconcile to final GL balance (difference: 12,450). Please update reconciliation tab, reload evidence, and re-submit by 2026-04-04 12:00 UTC."

h2. E) Sample Blocked-Item Escalation Notes

* "[BLOCKER] Awaiting payroll file from HRIS team; owner: A. Lee; ETA: 2026-04-02 10:00 UTC; impact: payroll accrual JE cannot be posted. Escalated to Controller after 24h threshold."
* "[BLOCKER] SAP role access failure for entity DE02; owner: IT Security Queue; ETA pending; impact: reconciliation cannot start; escalated to Finance Systems Manager."

----

h1. IMPLEMENTATION NOTES (FOR ADMIN ADAPTATION)

* Replace sample role names with actual Jira groups (for example, `fin-process-owners`, `fin-reviewers`, `fin-leadership`).
* Enforce transition validators so *In Progress -> In Review* requires Evidence Link and Reviewer.
* Use board quick filters for `Entity`, `Category`, and `Control Required`.
* Consider one "Current Close Period" Confluence excerpt/include pattern to reduce monthly page edits.
* Keep this page as a reusable template for each close period copy.
