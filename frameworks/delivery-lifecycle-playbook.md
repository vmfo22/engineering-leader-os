# Delivery Lifecycle Playbook — How We Work

**Created:** [DATE]
**Status:** Draft
**Companion to:** [[delivery-lifecycle-framework]] (phases, DoD, RACI)

---

## What This Document Is

The framework defines the phases. This playbook defines the behaviors.

If someone joins your team — a new PM, a new EM, a new Tech Lead — they should be able to read this and understand: how do we work here? What's expected of me? What decisions can I make? When do I ask for help?

This isn't about compliance. It's about empowerment. Clear expectations free people to move fast because they know the boundaries.

---

## Core Beliefs

These shape everything below. If you disagree with these, the playbook won't make sense.

1. **The people closest to the problem make the best decisions.** Our job as leaders is to give them context, set boundaries, and get out of the way.
2. **Context travels through people, not documents.** Documents decay. The person who shaped the problem should be in the room when the solution is designed. The person who designed it should be available when it's built.
3. **Finishing is more valuable than starting.** A feature in GA beats three features in Definition. We measure output, not activity.
4. **Speed comes from clarity, not from rushing.** Clear problem statements, clear contracts, clear scope boundaries — these eliminate rework, which is the real time thief.
5. **Every discipline adds value at every phase — but not equally.** PMs lead in Definition. Architects lead in Solution Design. EMs lead in Development. Leading means being accountable, not doing it alone. Everyone else contributes, challenges, and supports.

---

## Role Expectations by Phase

### Product Manager

**Your job across the lifecycle:** Own the "what" and "why." Make sure we're building the right thing for the right customer. Protect scope. Kill features that shouldn't exist.

#### In Definition — You Lead

**What great looks like:**
- You write the problem statement from the customer's perspective, not from the solution's perspective. "Customers can't X" beats "We need to build Y."
- You bring data or customer signal. Not always quantitative — a pattern from 3 support tickets is signal. "I think this would be cool" is not.
- You define what's OUT of scope before anyone asks. The boundaries matter more than the contents.
- You set the appetite: "This is worth 4 weeks of a team's time" — not "How long will this take?" You own the investment decision.
- For multi-team: you frame the problem for the Joint Ideation Session. You don't present a solution — you present a problem and let the room shape the constraints.

**Questions you should be asking:**
- Who has this problem? How many customers? How painful is it?
- What happens if we don't solve this?
- What's the smallest version of this that would matter?
- What are we explicitly NOT doing?

**Decisions you can make without escalation:**
- Scope boundaries (what's in, what's out)
- Priority within your feature set
- Whether to kill a feature in Definition that doesn't have a clear customer signal

**When to escalate:**
- The feature conflicts with another team's roadmap
- The appetite exceeds one quarter of a team's capacity
- You can't get a clear customer signal and you're unsure whether to proceed

#### In Solution Design — You Contribute

**What great looks like:**
- You stay in the room. Not to design the solution — to represent the customer when tradeoffs happen. "If we cut X, does the customer still get value?"
- You challenge complexity. If the Architect proposes a 3-month solution to a problem you scoped as 4 weeks, something is wrong — either the scope grew or the approach is over-engineered. Push back.
- You validate the UX direction against customer needs. The prototype should solve the problem you defined, not a different one.

**Questions you should be asking:**
- Does this solution actually solve the problem I defined, or has it drifted?
- What's the simplest version that delivers customer value?
- If we ship this and it works — how will we know?

**Decisions you can make:**
- Scope tradeoffs within the boundaries you set in Definition
- UX direction preferences (with Product Design)

**What you should NOT do:**
- Dictate technical approach. Trust the Architect and Tech Lead.
- Disappear. If you're not in the room, no one represents the customer.

#### In Development — You Protect

**What great looks like:**
- You protect scope. When someone says "while we're here, let's also add X" — you say no (or "that's a new feature, goes to Backlog").
- You're available for questions. Engineers will hit ambiguity — "the spec doesn't say what happens when Y." You answer quickly, within hours, not days.
- You start preparing release communication and success metric tracking.

**Questions you should be asking:**
- Are we still building what we defined, or has scope crept?
- Are the success metrics ready to measure on day one of release?

#### In Release — You Own the Story

**What great looks like:**
- You own the customer communication. Release notes, internal announcements, customer-facing docs.
- You track success metrics from day one. If the feature shipped but the metrics don't move, that's your signal — not the EM's.

---

### Engineering Manager

**Your job across the lifecycle:** Own the "how" and "when." Make sure your team can deliver what's been designed, on time, with quality. Protect your team's capacity and health.

#### In Definition — You Validate

**What great looks like:**
- You give an honest feasibility signal. Not a commitment — a gut check. "This feels like 2 sprints" or "This has hidden complexity in X area, we should flag that."
- You flag capacity constraints early. If your team is already at 100%, a new Definition doesn't magically create capacity.
- You identify dependencies your team has on other teams. Don't wait for Solution Design to discover these.
- For multi-team: you attend the Joint Ideation Session with your Tech Lead. You bring the team's perspective — what they're already working on, what capacity looks like, what they know about the problem space.

**Questions you should be asking:**
- Does my team have the skills and capacity for this?
- What would we need to stop doing to take this on?
- What are the dependencies that could block us?

**Decisions you can make without escalation:**
- Whether your team has capacity to take on a new feature (you can say no)
- Which Tech Lead or senior engineer participates in shaping

**When to escalate:**
- The PM's appetite doesn't match your feasibility assessment (they want 4 weeks, you see 8)
- Two features are competing for your team's capacity and you can't resolve the priority

#### In Solution Design — You Ensure Buildability

**What great looks like:**
- You confirm: "my team can build this." This is your sign-off. If the design is too complex, too risky, or doesn't account for your team's constraints — you push back before it exits Solution Design. Not during Development.
- You pair your Tech Lead with the Architect. They design together. You ensure your Tech Lead has the time and space to contribute meaningfully.
- You estimate at epic level. Not hours, not story points — "this is 2-3 sprints for my team." Honest, not optimistic.

**Questions you should be asking:**
- Can my team actually build this? Do they have the skills?
- Is the design complete enough to start, or are there gaps that will cause rework?
- What's the riskiest part? Do we need a spike first?

**The most important thing you do in this phase:** Sign off. "This design is ready for my team to build." If you sign off on something incomplete, your team pays the price in Development.

#### In Development — You Lead

**What great looks like:**
- You own the delivery commitment. Timeline, quality, team health — all yours.
- You run your team. Sprint planning, stand-ups, blockers — whatever cadence works for your team. The framework doesn't prescribe this.
- You flag problems early. Not at the end of the sprint — the moment you see risk. "We're behind on X because Y. I need Z to get back on track."
- You protect your team from scope creep. When the PM says "one more thing" — you check it against the Definition scope. If it's new, it's new.
- For multi-team: you attend the weekly integration checkpoint. You represent your team's progress and flag contract issues.

**Questions you should be asking:**
- Are we on track? If not, what's the gap and what do I need?
- Is anyone on my team struggling? Overloaded? Blocked?
- Are the cross-team contracts holding?

**Decisions you can make without escalation:**
- How to break epics into tasks
- Sprint-level prioritization within the feature
- Technical tradeoffs within the design boundaries (with your Tech Lead)
- Pulling in the Architect for guidance

**When to escalate:**
- You're going to miss the timeline by more than 1 sprint
- A cross-team contract is breaking and the other team disagrees on the fix
- Quality issues that require scope reduction to meet the deadline

#### In Release — You Own Operational Readiness

**What great looks like:**
- Monitoring is in place before rollout, not after
- Rollback plan exists and has been tested
- Your team is available during the rollout window for issues
- You don't "throw it over the wall" to ops — you own it until it's stable

---

### Architect

**Your job across the lifecycle:** Own the technical integrity. Make sure the solution is sound, scalable, and doesn't create problems for future work. Design with the team, not for the team.

#### In Definition — You Assess

**What great looks like:**
- You give a quick technical risk assessment. Not a design — a signal. "This touches 3 teams and the data model" or "This is straightforward, single-team."
- You flag platform constraints that affect feasibility.
- You identify cross-team implications early.

**What you should NOT do:** Start designing. Definition is about the problem, not the solution. Save your design energy for Solution Design.

#### In Solution Design — You Lead (With the Team)

**What great looks like:**
- You design WITH the Tech Lead, not alone in a document. Co-create. The Tech Lead knows the codebase; you know the architecture. Together you produce something that's both sound and buildable.
- You consider at least 2 alternatives and document why you chose the one you did. This prevents confirmation bias and gives future readers the reasoning.
- You define integration contracts for cross-team boundaries. These are explicit: API shape, data model, ownership boundaries, error handling. Not "we'll figure it out."
- You make the design as simple as the problem allows. Over-engineering is a design failure, not a sign of thoroughness.

**Questions you should be asking:**
- What's the simplest design that solves this problem?
- Where are the integration points between teams? Are the contracts clear?
- What assumptions am I making? What breaks if they're wrong?
- Does this create technical debt we'll regret in 6 months?

**Decisions you can make without escalation:**
- Technical approach within the architecture guardrails
- API contract design
- Technology choices within the approved stack

**When to escalate:**
- The design requires a platform change outside your team
- Two architects disagree on the approach (someone needs to break the tie)
- The design is significantly more complex than the PM's appetite allows

**The trap to avoid:** Designing in isolation and presenting a finished HLD for the team to "review." By then it's too late for meaningful input — the team becomes an implementer, not a collaborator. Design in working sessions, not in documents.

#### In Development — You Support

**What great looks like:**
- You're available for questions. Not in every stand-up — but reachable. The team should be able to get an architecture question answered within hours, not days.
- You review integration points. The contracts you defined — are they holding? If not, you help adjust.
- You don't redesign during Development. If the design needs significant changes, that's a signal to pause and go back to Solution Design. Small adjustments are normal; fundamental rethinks are a process failure.

---

### Tech Lead / Senior Engineer

**Your job across the lifecycle:** Bridge between architecture and implementation. You know the codebase. You know what's possible. You make sure designs are grounded in reality.

#### In Definition — You Signal

**What great looks like:**
- You attend the Joint Ideation Session for multi-team features. You bring what you know about the codebase, existing technical debt, and hidden complexity.
- You give early feasibility signals: "This is harder than it looks because of X" or "We actually have a foundation for this already."

#### In Solution Design — You Co-Create

**What great looks like:**
- You sit next to the Architect and design together. You bring codebase knowledge; they bring architectural thinking. The output is better than either could produce alone.
- You prototype where possible. Code validates architecture faster than documents.
- You flag risks the Architect might miss because they're not in the code daily.
- You challenge over-engineering: "Do we really need this abstraction, or can we solve it simply?"

**Decisions you can make:**
- Implementation approach within the architecture boundaries
- Prototyping direction
- Flagging risks and proposing alternatives

#### In Development — You Execute and Elevate

**What great looks like:**
- You own the technical quality of the implementation.
- You mentor less experienced team members through the build.
- You're the first to flag when the design doesn't survive contact with reality.
- For multi-team: you represent your team in the weekly integration checkpoint.

---

## Collaboration Patterns

### How Disciplines Work Together (Not Just Side by Side)

**The default failure mode:** Each discipline works in their lane, hands off to the next, and wonders why context gets lost.

**What we do instead:**

| Phase | Collaboration Pattern |
|-------|----------------------|
| **Definition** | PM leads, but EM + Architect are in the room for feasibility and risk. Not reviewing a document — contributing in real-time. |
| **Joint Ideation** (multi-team) | All disciplines in one room. PM frames the problem. Architect flags technical constraints. EM flags capacity. Tech Lead flags codebase reality. Design flags usability risks. Output is shared — not PM's document that others "reviewed." |
| **Solution Design** | Architect + Tech Lead co-design. PM stays for tradeoffs. Design iterates on UX in parallel. EM validates buildability. Working sessions, not document reviews. |
| **Development** | EM leads. Architect available for questions. PM available for scope clarification. Weekly integration checkpoint for multi-team. |
| **Release** | EM owns operational readiness. PM owns customer communication. Architect reviews rollback plan. |

### The 30-Minute Rule

If a question blocks work and the right person isn't available, the decision maker has 30 minutes to respond (Slack, meeting, whatever) during working hours. If they don't, the team makes the best decision they can and moves forward. We optimize for flow, not for perfect consensus.

### Disagreements

When disciplines disagree on direction:

1. **PM vs Architect on scope:** PM wins on what to build (customer value). Architect wins on how to build it (technical integrity). If the "how" makes the "what" infeasible, they negotiate scope — not quality.
2. **EM vs PM on timeline:** EM provides honest assessment. PM adjusts scope to fit, or escalates for more resources. The EM never commits to a timeline they don't believe in.
3. **Architect vs Tech Lead on approach:** They resolve it together in a working session. If they can't, the Architect's decision stands — but they must explain the reasoning, not pull rank.
4. **Unresolvable:** Escalate to the engineering leader. Bring the options, the tradeoffs, and your recommendation. Don't bring "we can't agree" without doing the work first.

---

## Decision Rights

Clear decision rights prevent bottlenecks and empower people to move fast.

### Decisions Anyone on the Team Can Make

- Implementation details within the design boundaries
- Bug fixes and minor improvements in their area
- Refactoring that doesn't change behavior or interfaces
- Development tooling and local workflow choices

### Decisions the PM + EM Pair Makes

- Feature scope within the approved Definition
- Sprint-level prioritization
- Whether to accept a scope tradeoff during Development
- When a feature is ready for release

### Decisions That Need Architect Input

- Technical approach for new features
- API contract changes
- Cross-team integration design
- Technology choices outside the approved stack

### Decisions That Need Engineering Leader Input

- New features that weren't in the roadmap
- Resource allocation changes (moving people between teams)
- Killing a feature that's already in Development
- Timeline commitments to stakeholders outside the team

### The Default

**If in doubt, make the decision and communicate it.** A wrong decision made quickly and corrected is better than no decision waiting for approval. The only exceptions: decisions that are irreversible, affect other teams' commitments, or have customer-facing impact.

---

## What "Empowered" Looks Like in Practice

Empowerment isn't a feeling. It's a set of concrete conditions:

**You are empowered when:**
- You know what problem you're solving and why it matters
- You have the authority to decide how to solve it
- You have the information you need (context, constraints, dependencies)
- You know when to ask for help and when to move forward
- You are trusted to make mistakes and learn from them

**You are NOT empowered when:**
- You receive a solution to implement without understanding the problem
- Every decision needs approval from someone not in the room
- You don't know the business context behind what you're building
- You're afraid to raise risks because it might "look bad"

**Our commitment as leaders:** We will provide clear problem statements, share business context openly, define decision boundaries, and trust you within those boundaries. In return, we expect you to own outcomes, flag risks early, and collaborate across disciplines.

---

## How to Use This Playbook

**For onboarding:** New PMs, EMs, Architects, and Tech Leads read this in their first week. Their manager walks through it with them and answers questions.

**For calibration:** When something feels off — a feature is stuck, disciplines are clashing, decisions aren't being made — come back to this document. Which expectation is being violated? That's where the fix is.

**For retrospectives:** After a multi-team feature ships, review against this playbook. Where did we follow it and it helped? Where did we skip it and paid the price? Where did we follow it and it got in the way? (That last one means the playbook needs updating.)

**This is a living document.** It will change as we learn. If something here doesn't match reality or doesn't work, raise it — don't work around it.

---

---

## Rituals & Communication Patterns

The lifecycle defines the phases. The role expectations define the behaviors. This section defines the rituals — the concrete practices that create rhythm, keep context flowing, and prevent coordination theater.

**Guiding principles for rituals:**
- Async by default, sync when it matters (decisions, disagreements, ideation)
- Every ritual has an owner, an output, and a reason to exist. If it stops producing value, kill it.
- Communication travels through people first, documents second. Documents are records, not substitutes for conversation.
- No ritual should exist to make leadership feel informed. If leadership needs information, automate it or read the channel.

---

### Per-Initiative Communication Infrastructure

When a feature moves from Backlog to Definition, the PM creates:

1. **Slack channel:** `#init-[short-name]` (e.g., `#init-[short-name]`, `#init-[short-name]`)
   - Owner: PM (keeps it on-topic, archives when feature hits Done)
   - Who joins: everyone involved — PM, EM, Architect, Tech Lead, Designer, and any cross-team contributors
   - What goes in: day-to-day decisions, blockers, async updates, links to PRs and docs, quick questions
   - What stays out: general chatter, unrelated threads
   - Archive when the feature reaches Done. Dead channels create confusion.

2. **Initiative doc:** A single living document (Confluence or equivalent) that is the source of truth — problem statement, scope, design decisions, status. Not a spec — a context hub.
   - Updated by whoever made the last meaningful decision
   - Linked from the Slack channel topic

**For single-team features:** The team's existing channel is enough. No dedicated channel unless the feature is complex enough to warrant its own conversation space.

**For multi-team features:** The dedicated channel is mandatory. This is where cross-team coordination happens async. Tech Leads from all involved teams join.

---

### Rituals by Phase

#### Definition Phase

**Joint Ideation Session** (multi-team only)

| | |
|---|---|
| **When** | Within the first week of a feature entering Definition. Triggered by PM. |
| **Who** | PM + Architect(s) + Product Design + EMs + Tech Leads from all affected teams. Keep it under 12 people. |
| **Duration** | 90 min max. One session. If you need a second, the problem isn't clear enough — go back and sharpen. |
| **Format** | PM presents the problem (10 min, no solution). Each discipline shares what they know: constraints, risks, dependencies, past attempts (30 min round). Group identifies scope boundaries and open questions (30 min). Last 20 min: agree on what's in, what's out, who owns what next. |
| **Output** | Updated initiative doc with: validated problem statement, constraints from each discipline, scope boundaries, open questions assigned to owners, and trio nomination (if multi-team). |
| **Anti-pattern** | PM presents a solution, not a problem. The Architect starts designing in the room. The session runs 3 hours because scope keeps expanding. |

**PM-EM Alignment Check** (all features)

| | |
|---|---|
| **When** | Before Definition exits. Quick sync — 15-30 min. |
| **Who** | PM + EM (the owner pair). |
| **Purpose** | Confirm: is the problem clear? Is the scope bounded? Does the EM's feasibility signal match the PM's appetite? Are we ready for Solution Design? |
| **Output** | Go / no-go for Solution Design. If no-go, what's missing. |

#### Solution Design Phase

**Kick-Off** (all features entering Solution Design)

| | |
|---|---|
| **When** | First day of Solution Design. Triggered by PM + EM after Definition exit. |
| **Who** | The trio (PM + Architect + Tech Lead) + EM + Designer. For multi-team: Tech Leads from other involved teams. |
| **Duration** | 60 min. |
| **Format** | PM recaps the problem and scope (5 min — context setting, not re-debating). Architect shares initial thinking on approach (15 min). Tech Lead shares codebase context — what exists, what's hard, what's easy (15 min). Group identifies the 2-3 biggest open questions and assigns them (15 min). Agree on working cadence for the design phase (10 min). |
| **Output** | Shared understanding of starting point. Open questions assigned. Working schedule for the design sessions. |
| **Anti-pattern** | The kick-off becomes the entire design process — 4 hours of whiteboarding that tries to solve everything in one session. The kick-off aligns and assigns. The design work happens in focused working sessions after. |

**Design Working Sessions** (Architect + Tech Lead)

| | |
|---|---|
| **When** | 2-3 sessions per week during Solution Design. Time-boxed to 60-90 min each. |
| **Who** | Architect + Tech Lead (core). PM joins for tradeoff decisions when needed. Designer joins for UX-adjacent decisions. |
| **Format** | Collaborative. Whiteboard, prototype, discuss. Not "Architect presents, Tech Lead reviews." Co-create. |
| **Output** | Architecture evolving in the initiative doc. Decisions recorded as they happen — not in a separate meeting. |

**Cross-Team Contract Session** (multi-team only)

| | |
|---|---|
| **When** | After 1 week of design work. One session. |
| **Who** | Trio + Tech Leads from all involved teams. |
| **Duration** | 60 min. |
| **Purpose** | Align on integration contracts: API shapes, data models, ownership boundaries, error handling. Each team has had time to explore their domain — now they connect the dots. |
| **Output** | Written contracts in the initiative doc. Each team knows their scope and how it connects to others. |
| **Anti-pattern** | Contracts are "agreed in principle" but not written down. Three weeks later, teams discover they built incompatible interfaces. If it's not written, it doesn't exist. |

#### Development Phase

**Sprint Kick-Off** (standard — team-level)

No change from existing team cadence. EM owns this. The lifecycle doesn't prescribe how teams run sprints — that's the team's working agreement.

**Weekly Integration Checkpoint** (multi-team only)

| | |
|---|---|
| **When** | Weekly, 30 min. Same day/time every week. |
| **Who** | Tech Leads from all involved teams + Architect. EM attends if there's a blocker. PM attends if there's a scope question. |
| **Format** | One question per team: "Are the contracts holding, or do we need to adjust?" If contracts are holding, team says "green" and doesn't present. If not, focus the time on the break. |
| **Output** | Contract adjustments documented. Blockers assigned. |
| **Kill condition** | If 3 consecutive weeks are "all green," switch to async check-in (Slack post) and cancel the meeting. Reinstate if something breaks. |
| **Anti-pattern** | This becomes a status meeting. It's not. It's a contract validation meeting. If people are giving updates instead of checking contracts, the facilitator cuts it. |

**Async Monday Status** (all teams)

| | |
|---|---|
| **When** | Every Monday morning, posted in [TEAM CHANNEL]. |
| **Who** | Each EM (or delegate). |
| **Format** | 4 lines: Shipping this sprint / Blocked on / Cross-team need / Flag for [ENGINEERING LEADER]. |
| **Purpose** | Replaces status portions of multiple meetings. Engineering leader reads every update Monday. Silence = acknowledged. |

#### Release Phase

**Release Readiness Check** (before rollout)

| | |
|---|---|
| **When** | Before flipping the switch. Triggered by EM. |
| **Who** | EM + Tech Lead + QA. PM for customer comms. Architect if there's rollback complexity. |
| **Duration** | 15-30 min. Can be async if the checklist is clean. |
| **Format** | Walk through the Release DoD checklist from the framework. Is monitoring in place? Rollback tested? Support briefed? Success metrics ready? |
| **Output** | Go / no-go for rollout. |

#### Done Phase

**Initiative Retrospective** (multi-team only, recommended for complex single-team)

| | |
|---|---|
| **When** | Within 1 week of reaching Done. |
| **Who** | The trio + EMs + anyone who wants to join. |
| **Duration** | 45-60 min. |
| **Format** | Three questions: What worked in our lifecycle process? What didn't? What would we change for next time? |
| **Output** | 3-5 concrete improvements. Fed back into this playbook if they're systemic. |

---

### When to Reach Other Teams

Clear triggers, not vague "coordinate early."

| Trigger | Action | When |
|---------|--------|------|
| Feature touches another team's codebase | Invite their Tech Lead to the Joint Ideation Session | At Definition start |
| Feature depends on another team's API or component | Define the contract in a Cross-Team Contract Session | During Solution Design (week 1-2) |
| Feature requires another team to build something | PM-to-PM conversation first: is this on their roadmap? Can they prioritize it? | Before Definition exits — don't design against a dependency you haven't confirmed |
| Cross-team PR needed during Development | Discuss in the initiative Slack channel. If the PR is non-trivial, Tech Lead-to-Tech Lead conversation before submitting. | During Development, as early as possible |
| Integration breaks during Development | Raise in weekly integration checkpoint. If urgent, Slack the other Tech Lead directly (30-minute rule). | Immediately |

### When to Reach Other PMs

| Trigger | Action |
|---------|--------|
| Your feature affects another PM's feature (shared dependency, competing for same team, scope overlap) | DM or Slack thread. Frame it: "I think my feature X affects your feature Y because Z. Can we align?" |
| You need another team to build something for your feature | Talk to their PM first, not their EM. PMs own prioritization. If they can't prioritize it, escalate through the leadership sync. |
| Scope conflict between two features | PMs resolve it together. If they can't, bring both perspectives to the engineering leader with a recommendation, not just "we disagree." |
| Joint Ideation Session involves features from multiple PMs | All relevant PMs attend. One PM leads (the one whose feature has the most scope). |

---

### Communication Cadence Summary

| Practice | Cadence | Sync/Async | Owner |
|----------|---------|-----------|-------|
| Initiative Slack channel | Continuous | Async | PM |
| Joint Ideation Session | Once (at Definition start) | Sync | PM facilitates |
| PM-EM Alignment Check | Once (at Definition exit) | Sync | PM + EM |
| Solution Design Kick-Off | Once (at SD start) | Sync | Architect |
| Design Working Sessions | 2-3x/week during SD | Sync | Architect + Tech Lead |
| Cross-Team Contract Session | Once (SD week 1-2) | Sync | Architect |
| Weekly Integration Checkpoint | Weekly during Development | Sync (kill if 3x green) | Tech Lead (lead team) |
| Async Monday Status | Weekly | Async | EM |
| Release Readiness Check | Once (before rollout) | Sync or async | EM |
| Initiative Retrospective | Once (at Done) | Sync | EM |

**Total sync rituals for a multi-team feature across the full lifecycle:** ~10-12 sessions. Not 10 per week — 10 total across 2-4 months. The rest is async.

---

### Working Agreements

Each team maintains a short working agreement (1 page max, co-created by the team, not imposed). Covers:

1. **Communication norms:** Which channel for what. Expected response time (Slack: same day. Blocked question: 30 min. PR review: 24h).
2. **Decision-making:** How the team makes decisions. Default: Tech Lead decides implementation, EM decides process, PM decides scope. Team discusses, decision maker decides.
3. **Code review norms:** Turnaround time (24h for same-team, 48h for cross-team). Required approvals. What "approved" means (I've read it and it's good, not "I glanced at it").
4. **Meeting norms:** What's required, what's optional. How to decline without guilt.
5. **Deep work protection:** Core focus hours (if any). How to signal "do not disturb."

**How to create:** EM facilitates a 60-min session with the team. Team co-creates the agreement. Revisit quarterly or when someone joins/leaves.

**The point:** When everyone knows the norms, they don't need to ask permission to act. That's empowerment.

---

### Decision Documentation — Lightweight

**For significant design decisions:** Write a short ADR (Architecture Decision Record). 5 fields: Title, Context, Decision, Alternatives Considered, Consequences. Half a page. Stored in the initiative doc.

**For scope or priority decisions:** Record in the Slack channel. Pin the message. That's enough — it's searchable and timestamped.

**For cross-team contract decisions:** Written in the initiative doc under a "Contracts" section. This is the source of truth for integration boundaries.

**Rule:** If you made a decision that someone who wasn't in the room would need to know about — write it down somewhere findable. If it only matters to the people who were there, don't create paperwork.

---

## Appendix: Worked Example

*Stress-test this playbook against a real initiative of your own: pick one initiative currently in flight and walk it through every phase, checking that the role expectations and rituals above actually hold. Where they don't, that's where your delivery model needs attention.*
