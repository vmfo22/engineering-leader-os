# Jira Plan System Design

*How to structure Jira Plan (Advanced Roadmaps) so it gives you clean leadership reporting and initiative tracking. This is the Jira-side companion to the `/execution-review` skill, which syncs your initiative tracker against these items.*

*Last Updated: [DATE]*

---

## Goals

- **Leadership reporting:** Clear status and progress visibility
- **Capacity planning:** Team load and scheduling
- **Dependency tracking:** Cross-team visibility
- **Primary timeline driver:** Target end date
- **Accountability:** All items must have an assigned owner

---

## Hierarchy

A four-level hierarchy, grouped by **Portfolio** (your top-level grouping — use whatever your org calls it: portfolio, value stream, product area, or team group):

```
Initiative → Milestone → Epic → Story
```

- **Initiative** — a large body of work spanning teams/quarters.
- **Milestone** — a meaningful, shippable increment of an initiative (mark customer-facing ones with a GA Date).
- **Epic** — a team-sized chunk of a milestone.
- **Story** — a single sprint-sized unit of work.

*Adapt the level names to your Jira setup — the important part is the four altitudes and the fields at each.*

---

## 1. Required Fields by Hierarchy Level

| Level | Required Fields |
|-------|-----------------|
| **Initiative** | Owner, Status, Target start date, Target end date, Portfolio |
| **Milestone** | Owner, Status, Target start date, Target end date, GA Date (if customer-facing) |
| **Epic** | Owner, Status, Target start date, Target end date, Team |
| **Story** | Owner, Status, Sprint |

**Rules:**
- No item moves to DEVELOPMENT without all required fields filled
- GA Date only required for customer-facing releases (not internal milestones)
- Target end date = when dev work completes; GA Date = when customers get it

---

## 2. Status Definitions

| Status | Meaning | Entry Criteria |
|--------|---------|----------------|
| **BACKLOG** | Not yet prioritized | Exists in the system |
| **DEFINITION** | Being scoped/designed | Owner assigned, rough dates set |
| **SOLUTION DESIGN** | Technical design in progress | Requirements clear, design work active |
| **DEVELOPMENT** | Active implementation | Design complete, all required fields filled |
| **PAUSED** | On hold | Reason documented in comments |
| **GA** | Released to customers | Work complete, GA Date filled |

**Flow:** BACKLOG → DEFINITION → SOLUTION DESIGN → DEVELOPMENT → GA

---

## 3. Views/Filters Structure

### A. Portfolio-Level Views

#### 1. [Your Portfolio] Roadmap
**Purpose:** Main roadmap — what you own and are delivering
**Filter:**
- Portfolio = [your portfolio]
- Status ≠ BACKLOG

**Columns:** Item, Owner, Status, Progress, Target start, Target end, GA Date
**Audience:** Leadership reporting, quarterly planning

#### 2. [Your Portfolio] Consolidated
**Purpose:** Full picture including dependencies on other portfolios' work
**Filter:**
- Portfolio = [yours] OR has dependency from your teams
- Status ≠ BACKLOG

**Columns:** Item, Owner, Status, Portfolio, Target end, Dependencies
**Audience:** Director, cross-portfolio coordination

#### 3. Contributions to Other Portfolios
**Purpose:** Work your teams do for other portfolios
**Filter:**
- Team = [your teams] AND Portfolio ≠ [yours]
- OR linked as dependency to other portfolios' initiatives

**Columns:** Item, Owner, Status, Portfolio (requestor), Target end
**Audience:** Capacity planning, stakeholder alignment

### B. Team-Specific Views

Create one view per team:
- **[Team 1] View** — Filter: Team = [Team 1]
- **[Team 2] View** — Filter: Team = [Team 2]
- **[Team 3] View** — Filter: Team = [Team 3]
- *...add one per team*

**Standard columns for team views:** Item, Owner, Status, Progress, Target start, Target end, Sprint

### C. Operational Views

#### Data Quality Check
**Purpose:** Find items missing required fields
**Filter:**
- Owner = Unassigned OR Target end date = empty
- Status ≠ BACKLOG

**Use:** Weekly review by Director, EMs, PMs
**Columns:** Item, Owner, Status, Target start, Target end, Team

#### Dependencies View
**Purpose:** Cross-team/cross-portfolio dependencies
**Filter:** Has linked dependencies
**Columns:** Item, Owner, Status, Dependencies, Target end, Blocker status

---

## 4. Date Field Definitions

| Field | Definition | Required When |
|-------|------------|---------------|
| **Target start date** | When work begins | Status = DEFINITION or later |
| **Target end date** | When work completes (dev done) | Status = DEFINITION or later |
| **Due date** | Hard deadline (if different from target) | Only if external constraint |
| **GA Date** | When customers receive it | Customer-facing items only |

**Timeline bars should use:** Target start → Target end

---

## 5. Health Indicators

| Level | On Track | At Risk | Off Track |
|-------|----------|---------|-----------|
| **Initiative** | All child milestones on track | 1+ milestone at risk | 1+ milestone off track or dates slipped |
| **Milestone** | Progress ≥ expected for time elapsed | Progress 10-20% behind | Progress >20% behind or dates slipped |
| **Epic** | Stories completing per sprint plan | Sprint commitments missed | Blocked or no progress 2+ sprints |

---

## 6. Cadence

| Activity | Frequency | Who |
|----------|-----------|-----|
| Update epic status/progress | Weekly | Team Leads |
| Review milestone/initiative status | Bi-weekly | EMs + Director |
| Data quality check | Weekly | Director, EMs, PMs (shared) |
| Full roadmap review | Monthly | Leadership |

**Data quality ownership:**
- **Director:** Reviews consolidated view, escalates gaps
- **EMs:** Ensure their teams' items are complete
- **PMs:** Ensure initiative/milestone level data is accurate

---

## 7. Cleanup Checklist

Based on current state, fix these:

- [ ] Assign owners to all unassigned items (or move to BACKLOG if not prioritized)
- [ ] Fill Target start/end dates for all DEFINITION+ items
- [ ] Standardize status usage — remove any non-standard statuses
- [ ] Add GA Date to customer-facing milestones

---

## 8. Implementation Checklist

### Views to Create
- [ ] [Your Portfolio] Roadmap view
- [ ] [Your Portfolio] Consolidated view
- [ ] Contributions to Other Portfolios view
- [ ] Data Quality Check view
- [ ] Dependencies view
- [ ] [Team 1] team view
- [ ] [Team 2] team view
- [ ] [Team 3] team view
- *...add one per team*

### Rollout
- [ ] Create all portfolio-level views in Jira Plan
- [ ] Create team-specific views for each team
- [ ] Run initial data quality check — assign owners and fill dates for all DEFINITION+ items
- [ ] Communicate system to EMs and PMs (required fields, status definitions, cadence)
- [ ] Set up recurring calendar reminders for data quality reviews

---

## Related Documents

- [[90_day]] — quarterly priorities, initiatives, and milestones
- [[team_health]] — Team health tracking framework

---

*This is a living document. Update as the system evolves.*
