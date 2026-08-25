# Delivery Lifecycle Framework

**Created:** [DATE]
**Status:** Draft
**Owner:** [YOUR_NAME]
**For:** [YOUR TEAM / VALUE STREAM]

---

## Purpose

Define what happens in each phase of our delivery lifecycle, who's accountable, what "done" means, and how we prevent the patterns that slow us down: context loss at handoffs, zombie features stuck in Definition, engineers excluded from shaping, and integration discovered too late.

This builds on your Jira Plan stages and incorporates the Joint Ideation + Embedded Trio model for multi-team initiatives.

---

## The Lifecycle

```
DEFINITION → SOLUTION DESIGN → DEVELOPMENT → RELEASE → GA → DONE
     ↕              ↕              ↕
  PAUSED          PAUSED         PAUSED        Any → CANCELLED
```

Detailed sub-stages (matching Jira Plan):

*Example stage set — replace with your own Jira workflow.*

```
Definition → Ready for Solution Design → Solution Design (parallel with Planning Preparation) → Ready for Planning → Development → Ready for Release → LA / GA → Done
```

**Key principle:** Phases can overlap for mature teams (dual-track). While the team develops Feature A, the trio can be in Solution Design for Feature B. Sequential is the default for Forming teams; parallel is earned.

---

## Phase 1: Definition

### What Happens Here

The problem gets validated and scoped. Not the solution — the problem. By the end of Definition, everyone involved should understand what we're solving, why it matters, and what's in/out of scope.

**Activities:**
- Problem statement written — what customer pain are we addressing?
- Business objective tied to [YOUR_PLANNING_FRAMEWORK]
- Success metrics defined — how will we know this worked?
- Four risks assessed (Cagan framework):
  - **Value:** Will customers want this?
  - **Usability:** Can they figure it out?
  - **Feasibility:** Can we build this? (initial signal, not full design)
  - **Viability:** Does it work for the business? (revenue, compliance, platform constraints)
- Scope boundaries set — what's IN and what's explicitly OUT
- Dependencies identified — which teams, APIs, platform capabilities
- Target timeline established (appetite, not estimate — "we're willing to invest X weeks," not "how long will this take?")

**For multi-team initiatives — Joint Ideation Session:**
All disciplines in one room before Solution Design starts. PM + Architect(s) + Product Design + EMs/Tech Leads from affected teams.
- Validate the problem together
- Surface constraints early from each team's domain
- Agree on scope boundaries
- Output: shared understanding, enough for PMs to build a credible roadmap, enough for engineers to flag risks
- This is NOT solution design. No architecture. No HLD. Just: is this the right problem, and do we understand the constraints?

### Accountability

| Role | Responsibility |
|------|---------------|
| **PM** | Accountable. Owns the problem statement, business case, success metrics, scope boundaries. |
| **EM** | Consulted. Validates feasibility signal, flags capacity constraints, identifies dependencies. |
| **Architect** | Consulted. Early technical risk assessment. Flags platform constraints or cross-team implications. |
| **Product Design** | Consulted. Early usability signal. Customer research input if available. |
| **Engineering Leader** | Informed. Reviews at gate. |

### Definition of Done — Exit Criteria

- [ ] Problem statement written and validated (customer signal, data, or strong strategic rationale)
- [ ] [YOUR_PLANNING_FRAMEWORK] objective identified (which objective does this serve?)
- [ ] Success metrics defined (measurable, not vague)
- [ ] Four risks assessed (value, usability, feasibility, viability) — each rated High/Medium/Low with mitigation if High
- [ ] Scope boundaries documented — what's IN and what's explicitly OUT
- [ ] Dependencies listed — teams, APIs, platform capabilities, external
- [ ] Owner pair assigned (PM + EM)
- [ ] Target timeline set (appetite — weeks, not story points)
- [ ] For multi-team: Joint Ideation Session completed, participants aligned

### Anti-Patterns

| Pattern | Signal | Fix |
|---------|--------|-----|
| **PM-only definition** | Engineers see the feature for the first time at Solution Design | Include EM and Tech Lead in Definition — at minimum for feasibility signal |
| **Solution masquerading as definition** | "The problem is we need to build X" instead of "customers can't do Y" | Require problem-first framing. If the Definition starts with a solution, push back. |
| **Zombie in Definition** | Feature sits in Definition for 4+ weeks without movement | Time-box: 2-3 weeks. If not done, it goes back to Backlog or gets killed. Flag at 3 weeks. |
| **Scope without boundaries** | "We'll figure out what's out of scope later" | Require explicit OUT list. Shape Up: "what we're NOT doing is as important as what we are." |

### Cycle Time Target

**2-3 weeks.** Flag at 3 weeks. If Definition isn't done in 4 weeks, escalate — either the problem isn't clear enough, the initiative is too big (split it), or it should go back to Backlog.

---

## Phase 2: Solution Design

### What Happens Here

The solution gets designed. Architecture, UX, and technical approach — defined together, not sequentially. By the end of Solution Design, every team involved should know what they're building, how it connects to other teams' work, and what the integration contracts are.

**Activities:**
- Architecture defined at RFC/ADR level (not spec-level — teams own their detailed design)
- UX direction validated — prototype tested or design reviewed with stakeholders
- API contracts defined for cross-team boundaries
- Integration points explicit — who depends on whom, what's the interface
- Planning Preparation happens in parallel — effort estimated at epic level, capacity confirmed, sprint planning inputs ready
- At least 2 alternative approaches considered (prevents confirmation bias — "we already decided to do X")
- Open questions resolved — no blockers left that would stop Development from starting

**For multi-team initiatives — Trio Assigned:**
PM + Architect + senior engineer (or Tech Lead) from the lead team. The trio co-owns the initiative from here through delivery.
- The trio carries context from the Joint Ideation Session — they were in the room
- Architect designs WITH the engineer, not FOR the engineer. The engineer prototypes to validate the architecture.
- PM stays in the room for tradeoff decisions — not just at the start
- When the solution touches other teams, the trio pulls in those Tech Leads. The Tech Leads have context from the Ideation Session, so the conversation is grounded.

### Accountability

| Role | Responsibility |
|------|---------------|
| **Architect** | Responsible. Owns the technical design, architecture decisions, integration contracts. |
| **EM** | Accountable. Owns delivery feasibility — confirms the team can build this in the timeline. Signs off that design is complete enough to start Development. |
| **PM** | Consulted. Validates solution against customer value. Makes scope tradeoff decisions. |
| **Product Design** | Responsible (for UX). Owns the design direction and prototype validation. |
| **Tech Lead** | Responsible (for team's domain). Co-designs with Architect. Validates feasibility for their team. |
| **Engineering Leader** | Informed. Reviews at gate for multi-team initiatives. |

**Note:** EM is Accountable (not Architect) because the EM owns the delivery commitment. The Architect is Responsible for the design quality, but the EM must confirm: "yes, my team can build this, and the design is complete enough to start."

### Definition of Done — Exit Criteria

- [ ] Technical approach documented (RFC/ADR level)
- [ ] UX direction validated (prototype or design review completed)
- [ ] Architecture reviewed — cross-team implications identified and resolved
- [ ] API contracts defined (if cross-team)
- [ ] At least 2 alternative approaches considered and decision documented
- [ ] Risks from Definition phase mitigated or accepted with plan
- [ ] Effort estimated at epic level
- [ ] Team(s) confirmed and capacity allocated
- [ ] No open questions that would block starting Development
- [ ] EM sign-off: "this is ready for my team to build"
- [ ] For multi-team: trio assigned, integration contracts agreed, weekly checkpoint scheduled

### Anti-Patterns

| Pattern | Signal | Fix |
|---------|--------|-----|
| **Thrown over the wall** | Architect designs HLD, hands to team, team discovers problems during LLD/build | Architect designs WITH the team. Tech Lead co-owns the design. |
| **Design without engineering input** | Beautiful architecture that ignores team constraints, existing code, or capacity | Tech Lead must validate feasibility before exit. Prototype where possible. |
| **Endless design** | Feature in Solution Design for 4+ weeks, still iterating | Time-box: 2-4 weeks depending on complexity. If not done, the scope is too big — split it. |
| **Missing integration contracts** | "We'll figure out the API later" | For multi-team features, no exit from Solution Design without explicit contracts. |
| **Confirmation bias** | Team explores one approach and declares it done | Require at least 2 alternatives considered. Document why the chosen approach won. |

### Cycle Time Target

**2-4 weeks** depending on complexity. Flag at 3 weeks. Escalate at 5 weeks. If Solution Design runs longer than 4 weeks, either the initiative is too large (split it) or there's an unresolved disagreement (escalate it).

---

## Phase 3: Development

### What Happens Here

The team builds it. By this point, the design is done, the contracts are clear, and the team owns execution. The focus is on shipping working software, not on re-designing.

**Activities:**
- Sprint planning from epic-level estimates (team breaks into tasks)
- Build in vertical slices where possible — not "backend first, then frontend"
- Continuous integration — code merged frequently, not in a big bang at the end
- Cross-team integration validated early and often (weekly checkpoint for multi-team)
- Feature flag ready for controlled rollout
- Testing: unit + integration + performance benchmarks
- Documentation updated as you go (API docs, user-facing help)

**For multi-team initiatives:**
- Trio stays accountable. The architect reviews integration during build. PM validates against customer needs. The engineer escalates when contracts break.
- Weekly integration checkpoint (30 min) — Tech Leads from all teams + lead Architect. One question: "Are the contracts holding or do we need to adjust?"
- If contracts break, the trio decides: adjust the contract or adjust the implementation. Don't let it drift.

### Accountability

| Role | Responsibility |
|------|---------------|
| **EM** | Accountable. Owns delivery commitment — timeline, quality, team health. |
| **Engineering Team** | Responsible. Builds, tests, deploys. |
| **Architect** | Consulted. Design integrity — ensures the build matches the design intent. Available for questions, not blocking. |
| **PM** | Consulted. Scope questions, tradeoff decisions if scope pressure emerges. |
| **Engineering Leader** | Informed. Tracks via execution review, intervenes only on escalation. |

### Definition of Done — Exit Criteria

- [ ] Feature works end-to-end in staging/preview environment
- [ ] Unit + integration tests pass
- [ ] Performance benchmarks met (or deviations documented and accepted)
- [ ] Security review complete (if applicable)
- [ ] Cross-team integration validated
- [ ] Documentation updated (API docs, user-facing if applicable)
- [ ] Feature flag configured for controlled rollout
- [ ] Release notes drafted
- [ ] EM sign-off: "this is ready for release"

### Anti-Patterns

| Pattern | Signal | Fix |
|---------|--------|-----|
| **Scope creep** | New requirements appearing during Development | Refer to Definition scope boundaries. If it's new, it's a new feature — goes to Backlog. |
| **Big bang integration** | Teams build independently for weeks, integrate at the end | Weekly integration checkpoint. Build vertical slices. Integrate early. |
| **Hero mode** | One person working 12h days to hit deadline | EM intervenes. Redistribute work or adjust scope. Quality is speed — burnout creates bugs. |
| **Rework from bad design** | Team discovers the architecture doesn't work during build | If significant: PAUSE, go back to Solution Design. Don't build on a broken foundation. Flag early. |

### Cycle Time Target

**Depends on scope.** Track at sprint level. Flag if a feature hasn't shown visible progress in 2 consecutive sprints. For [MAJOR_MILESTONE] outcomes, the outer boundary is [TARGET_DATE] — work backwards.

---

## Phase 4: Release (Ready for Release → LA / GA)

### What Happens Here

The code is done. Now it gets into customers' hands safely. This is a separate phase from Development because "code complete" and "available to all users" are different things with different risks.

**Activities:**
- Controlled rollout — percentage-based, canary, or A/B as appropriate
- Monitoring and alerting confirmed — dashboards in place, on-call aware
- Rollback plan documented and tested
- Support team briefed (if customer-facing)
- Limited Availability (LA) if applicable — select customers, controlled environment, feedback loop active
- Measure success metrics from Definition — are they moving?

### Accountability

| Role | Responsibility |
|------|---------------|
| **EM** | Accountable. Owns release quality and rollout. |
| **QA** | Responsible. Validates release readiness. |
| **PM** | Consulted. Customer communication, success metrics tracking. |
| **Architect** | Consulted. Rollback plan review, system health. |
| **Engineering Leader** | Informed. |

### Definition of Done — Exit Criteria (for GA)

- [ ] Rolled out to 100% of users (or target audience)
- [ ] Monitoring and alerting in place and validated
- [ ] No P1/P2 issues open from rollout
- [ ] Success metrics baselined and tracking
- [ ] Rollback plan documented
- [ ] Feature flag cleaned up
- [ ] Support briefed and documentation live

### Cycle Time Target

**1-2 weeks** from code complete to GA for standard features. LA can run longer if customer validation is needed (up to 4 weeks). Flag if release is blocked for more than 1 week after code complete.

---

## Phase 5: Done

Feature is GA, metrics are tracking, and the team has moved on. The feature enters maintenance mode — owned by the team that built it.

**Exit action:** Retrospective on multi-team initiatives. What worked in the lifecycle? What would we change? Feed learnings back into this framework.

---

## The Trio Model — How It Maps to the Lifecycle

For **multi-team initiatives** (3+ teams involved):

| Phase | Trio Activity |
|-------|--------------|
| **Definition** | Joint Ideation Session — trio members participate with broader group. Problem validated together. |
| **Solution Design** | Trio forms and co-owns design. Architect + Tech Lead design together. PM stays for tradeoffs. Trio pulls in other teams' Tech Leads for contracts. |
| **Development** | Trio stays accountable. Weekly integration checkpoint. Architect reviews integration. PM validates scope. Engineer escalates contract breaks. |
| **Release** | Trio reviews rollout plan. PM owns customer communication. EM owns operational readiness. |
| **Done** | Trio runs retrospective. Learnings documented. |

For **single-team initiatives:** Standard RACI applies. No trio needed. The EM + PM pair owns it.

---

## Cycle Time Summary

| Phase | Target | Flag | Escalate |
|-------|--------|------|----------|
| Definition | 2-3 weeks | 3 weeks | 4 weeks — back to Backlog or split |
| Solution Design | 2-4 weeks | 3 weeks | 5 weeks — split or unblock |
| Development | Scope-dependent | No progress in 2 sprints | EM flags blockers in execution review |
| Release | 1-2 weeks | Blocked 1 week post code-complete | Investigate — deployment issue or quality gap? |

---

## How This Connects to Existing Frameworks

- **High-Performance Engineering (Section 9):** Finishing > Starting principle applies — don't start Solution Design for Feature B until Definition for Feature B is truly done. 3-Day Stall Rule applies within each phase.
- **Jira Plan System:** Stages map 1:1. Entry criteria in Jira should reflect the DoD from this framework.
- **Execution Review:** The `/execution-review` command uses these stages to assess progress. Cycle time targets give concrete thresholds for "stuck."
- **Ceremonies Review:** The execution review is exception-based — features that haven't moved stages in 2+ weeks get airtime.

---

## Rollout Plan

| Phase | When | What |
|-------|------|------|
| **Draft review** | [+1-2 weeks] | Share with [PM STAKEHOLDER] and 2-3 EMs for input |
| **Refine** | [+3 weeks] | Incorporate feedback, align with Architects |
| **Pilot** | [+4-6 weeks] | Apply to 2-3 new features entering Definition. Track cycle times. |
| **Calibrate** | [+7 weeks] | Retrospective on pilot. Adjust DoDs, cycle time targets. |
| **Team-wide** | [+8 weeks] | Standard for all new features. Existing in-flight features grandfathered. |

---

## Open Questions

1. **Architect accountability in Solution Design:** Current RACI has Architect as Accountable. This framework suggests EM (because EM owns delivery). Which fits your culture better? Discuss with [PM STAKEHOLDER] and Architects.
2. **Jira automation:** Can we enforce DoD checklists as transition conditions in Jira Plan? Would reduce manual tracking.
3. **Dual-track readiness:** Which teams are mature enough to run Definition/Solution Design for future features while developing current ones?
4. **Time-boxing enforcement:** How strict? Shape Up kills features that miss the timebox. You may want a softer approach — flag and discuss, not auto-kill.

---

*Draft v1 — [DATE]*
*References: Spotify (Think It/Build It), Shape Up (Basecamp), SVPG Empowered Teams (Cagan), Dual-Track Agile (Patton), Shopify GSD*
