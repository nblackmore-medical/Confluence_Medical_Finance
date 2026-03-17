# Finance Space Standards & Governance

> **Purpose**  
> This page defines the operating model for documentation, reporting, and stakeholder transparency in the Finance space.

---

## 1) Operating Model at a Glance

| Pillar | Why it matters | Primary owner | Key cadence |
|---|---|---|---|
| Documentation standards | Creates a single source of truth and reduces process variance | Finance Operations | Continuous |
| Reporting governance | Ensures decision-quality data and transparent rollups | FP&A / Controllership | Weekly & Monthly |
| Stakeholder transparency | Makes engagement with Finance predictable and trackable | Finance Leadership | Weekly |
| Change control | Preserves audit readiness and policy integrity | Controls & Compliance | Quarterly + ad hoc |

---

## 2) Content Types (What Goes Where)

Use the structure below to keep content discoverable and consistent.

### Operating Rhythm
- Weekly/monthly/quarterly cadence pages and runbooks
- Includes: weekly priorities, close calendars, review checkpoints

### Processes & SOPs
- Step-by-step execution documentation (**system of record**)
- Includes: SOPs, operational playbooks, role handoffs

### Policies & Controls
- Rules of the road + control and audit readiness evidence
- Includes: policy statements, approval authorities, control matrices

### Performance & Reporting
- KPI definitions, report schedules, and metric ownership
- Includes: glossary, dashboard definitions, forecast assumptions

### Initiatives & Projects
- Portfolio of change-the-business work
- Includes: initiative charters, status updates, milestone logs

### Stakeholder Engagement
- How cross-functional teams work with Finance
- Includes: intake processes, SLAs, communication channels

### Meetings & Decisions
- Meeting notes + decision register
- Includes: governance forums, action follow-ups, decision history

---

## 3) Naming Conventions (Recommended)

Use these patterns to improve searchability and sorting.

| Artifact type | Standard page title pattern | Example |
|---|---|---|
| SOP | `SOP — <Process Name>` | `SOP — Vendor Invoice Processing` |
| Policy | `Policy — <Policy Name>` | `Policy — Corporate Card Usage` |
| Initiative | `Initiative — <Initiative Name>` | `Initiative — AP Automation Rollout` |
| Decision | `Decision — <Decision Title>` | `Decision — Close Calendar Approval` |
| Weekly priorities | `Weekly Priorities — Week of <YYYY-MM-DD>` | `Weekly Priorities — Week of 2026-01-12` |
| Close runbook | `Monthly Close Runbook — <YYYY-MM>` | `Monthly Close Runbook — 2026-01` |

---

## 4) Label Taxonomy (Required)

> **Governance rule:** Labels are mandatory for all governed artifacts and are required for register/report rollups.

### 4.1 Artifact-Type Labels
- `fin-weekly`
- `fin-close`
- `fin-sop`
- `fin-policy`
- `fin-initiative`
- `fin-decision`
- `fin-meeting`
- `fin-request` *(optional, for stakeholder intake tracking)*

### 4.2 Domain Labels
- `fin-ap`
- `fin-ar`
- `fin-expense`
- `fin-r2r`
- `fin-fpa`
- `fin-treasury`
- `fin-controls`

### 4.3 Sensitivity Label (Optional)
- `fin-confidential` *(classification aid only; use page restrictions for actual security controls)*

---

## 5) Reporting Mechanics (How Rollups Work)

### Standard Pattern
1. Each object page (SOP / Policy / Initiative / Decision) includes a **Content properties** macro.
2. The page is labeled with the correct taxonomy label (for example, `fin-sop`).
3. Register pages use a **Content properties report** macro filtered by label.

### Recommended Register Pages
- SOP Register (`fin-sop`)
- Policy Register (`fin-policy`)
- Initiative Register (`fin-initiative`)
- Decision Register (`fin-decision`)

---

## 6) Content Properties Standard (Non-Negotiable)

To keep filters and sorting reliable across the space:

- Use a **2-column key/value** table
- Keep keys (left column) in **plain text**
- Apply **header column formatting** to the left column
- Use date format: **`YYYY-MM-DD`**

### Standard Fields by Artifact

| Artifact | Required fields |
|---|---|
| SOP | Owner, Last reviewed, Next review, Status |
| Policy | Owner, Approver, Last reviewed, Next review, Revision |
| Initiative | Sponsor, Owner, Status, Target date, Last updated |
| Decision | Decision date, Decision owner, Impacted area, Status |

---

## 7) Ownership Model

### Category-Level Accountability
Each top-level category page has a **Finance owner** responsible for:
- Information hygiene and page lifecycle
- Label and metadata compliance
- Quarterly review completion

### Artifact-Level Accountability
- **SOP / Policy pages must include:**
  - Process/Policy owner
  - Last reviewed
  - Next review
- **Initiative pages must include:**
  - Sponsor
  - Owner
  - Status
  - Target date
  - Last updated

---

## 8) Cadence Expectations

| Cadence | Required action | Expected output |
|---|---|---|
| Weekly | Refresh weekly priorities | Updated weekly priorities page |
| Monthly | Maintain close runbook + capture retro | Completed close runbook and lessons learned |
| Quarterly | Execute policy/SOP review schedule | Review records and updated metadata |

---

## 9) Change Control

Material policy changes require all of the following:
- Approver recorded in **Content properties**
- Revision history updated
- Effective date captured in `YYYY-MM-DD` format
- Impacted stakeholders notified and noted in the update summary

---

## 10) Confluence Page Design Standards (Professional UX)

To maintain a modern, user-friendly experience:

1. **Use a clear visual hierarchy**
   - H1 for page title, H2 for major sections, H3 for implementation details.
2. **Lead with scan-friendly blocks**
   - Start each section with a short descriptor line before bullets/tables.
3. **Prioritize decision-useful content**
   - Keep governance rules near the top and templates/examples near execution sections.
4. **Use panels intentionally**
   - Info panel for standards, warning panel for non-compliance risks.
5. **Keep tables compact and practical**
   - Avoid dense prose inside tables; prioritize fields, owners, and cadence.
6. **Design for mobile and quick reads**
   - Use concise bullets, limited nesting, and consistent naming patterns.

---

## 11) Implementation Checklist

- [ ] Create/register top-level pages for each content type
- [ ] Apply required label taxonomy to in-scope pages
- [ ] Add Content properties macros to all governed artifacts
- [ ] Build register pages with Content properties report filters
- [ ] Assign owners for each top-level category
- [ ] Schedule weekly/monthly/quarterly review cadence
- [ ] Validate policy change-control metadata for all material updates

---

### Versioning
- **Document owner:** Finance Operations
- **Version:** 1.0
- **Last updated:** 2026-01-15
- **Review cadence:** Quarterly
