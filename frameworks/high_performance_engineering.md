# High-Performance Engineering Framework

**Owner:** [YOUR_NAME], [YOUR_ROLE]
**Status:** Draft — for EM review and feedback

---

## Why This Framework Exists

We have [NUMBER_OF_TEAMS] teams and ~[NUMBER_OF_PEOPLE] people. Now we need to define what "good" looks like — not in theory, but in our context. What should a high-performing team in this organization actually do, measure, and deliver?

This framework answers three questions:
1. **What does high-performance look like here?** — the standards
2. **How do we know if we're achieving it?** — the metrics
3. **How do we stay on track?** — the operating rhythm

This isn't a mandate. It's a shared language. EMs should adapt it to their teams' maturity and context.

---

## 1. The Standards — What Good Looks Like

### Delivery

A high-performing team **ships reliably and predictably.**

| Dimension | What we expect |
|-----------|---------------|
| **Predictability** | Team delivers 80%+ of sprint commitments. Misses are communicated early, not discovered at review. |
| **Scope management** | Team pushes back on scope creep. Changes go through the EM, not directly to engineers. |
| **Quality at source** | All estimates include testing. No feature ships without unit tests. Bugs are caught in development, not production. |
| **Incremental delivery** | Work is broken into pieces that ship weekly or bi-weekly. No silent 4-week epics. |
| **Dependencies** | Cross-team dependencies identified at planning, not at delivery. Escalated early when blocked. |

### Engineering Quality

A high-performing team **builds things that last.**

| Dimension | What we expect |
|-----------|---------------|
| **Bug escape rate** | Trending down quarter over quarter. Team owns root cause analysis for escapes. |
| **Tech debt** | Actively managed — not zero, not ignored. 10-20% of capacity allocated per sprint. |
| **Code review** | PRs reviewed within 24h. Reviews are constructive, not gatekeeping. Feedback is standards-based, not preference-based. |
| **Documentation** | Runbooks exist for on-call scenarios. Release processes are documented. New team members can onboard from docs. |
| **Incidents** | Post-mortems happen within 5 business days. Action items are tracked and closed. Same class of incident doesn't repeat. |

### People and Team Health

A high-performing team **grows its people and takes care of itself.**

| Dimension | What we expect |
|-----------|---------------|
| **Psychological safety** | People raise concerns in the room, not in back-channels. Mistakes are learning opportunities. |
| **Growth** | Every engineer has a development focus. EMs have developmental (not just operational) 1:1s. |
| **Accountability** | The team holds each other accountable — not just the EM. Peer feedback is normalized. |
| **Sustainable pace** | No hero culture. Consistent 12h+ days are a systemic failure, not a badge of honor. If someone is burning out, the EM escalates. |
| **Retention** | Key people want to stay. If someone is at risk, the EM knows and has a plan. |

### Collaboration

A high-performing team **works well with others.**

| Dimension | What we expect |
|-----------|---------------|
| **Cross-team communication** | Dependencies are surfaced proactively. No team is surprised by another team's decisions. |
| **Stakeholder alignment** | PMs, architects, and EMs are aligned on priorities. Misalignment is escalated, not ignored. |
| **Knowledge sharing** | Teams share learnings (retro insights, patterns, tools) with the broader org. Not just internally. |
| **Support** | Support cases are triaged within SLA. Knowledge is documented so the same question doesn't come back. |

---

## 2. The Metrics — How We Measure It

### Team Scorecard

Each team is measured across four areas. Reviewed monthly by EM + Director.

| Area | Metric | Target | How we measure |
|------|--------|--------|----------------|
| **Delivery** | Sprint commitment hit rate | ≥80% | Jira: committed vs delivered per sprint |
| **Delivery** | Cycle time (story) | <5 business days (P3 stories) | Jira: in-progress to done |
| **Quality** | Bug escape rate | Trending down QoQ | Bugs found in production vs total stories shipped |
| **Quality** | Incident recurrence | 0 repeated incident classes | Post-mortem tracker |
| **People** | Team health score | ≥3.5/5 | Health tracker (monthly EM assessment) |
| **People** | eNPS or engagement signal | Stable or improving | Quarterly pulse or proxy |
| **Process** | Jira data quality | 100% required fields filled | Data quality view (weekly) |
| **Process** | Retro action completion rate | ≥70% | Retro tracker |

### Org-Level Metrics

Aggregated across all teams. Reviewed monthly by Director.

| Metric | Target | How |
|--------|--------|-----|
| Initiative stage progression | No feature stuck in same stage for 3+ weeks without explanation | initiatives tracker |
| Cross-team dependency health | All dependencies identified and tracked | Jira dependencies view |
| EM development pulse | Every EM received developmental feedback this month | Director self-check |
| Framework adoption | All teams using scorecard by end of Q1 | Check-in |

### What We Don't Measure (On Purpose)

- Lines of code
- Hours worked
- Number of PRs
- Individual velocity
- Individual AI tool usage
- AI acceptance rate per person
- Lines of AI-generated code

These drive the wrong behavior. We measure outcomes and team health, not activity.

---

## 3. The Operating Rhythm — How We Stay On Track

### Daily

| Activity | Owner | Purpose |
|----------|-------|---------|
| Team standup | Team Lead / EM | Surface blockers, align on daily priorities |
| Async status updates (Slack) | Engineers | Visibility without meetings |

### Weekly

| Activity | Owner | Purpose |
|----------|-------|---------|
| Sprint ceremonies (planning, review, retro) | EM + Team | Delivery cadence |
| EM updates Jira Plan (epic status, progress) | EM | Data quality |
| Director data quality review | Director | Catch gaps, flag risks |
| 1:1s (EM ↔ Director) | Both | Operational + developmental |

### Bi-weekly

| Activity | Owner | Purpose |
|----------|-------|---------|
| Execution review (Director) | Director | Stage movement, risks, cross-team check, meeting prep |
| [Your cross-team sync] | Director + EMs | Cross-team alignment, dependency resolution |
| Sprint reviews (team demos) | EM + Team | Delivery visibility |

### Monthly

| Activity | Owner | Purpose |
|----------|-------|---------|
| Team scorecard review | EM + Director | Metrics review, trend analysis |
| Team health update | EM | Health tracker refresh |
| EM development check-in | Director | Growth edge review per EM |
| Full roadmap review | Director + Leadership | Initiative progress, roadmap adjustments |

### Quarterly

| Activity | Owner | Purpose |
|----------|-------|---------|
| Team health deep dive | EM + Director | Lencioni assessment (trust, conflict, commitment, accountability, results) |
| Metrics baseline reset | Director | Set new targets based on actuals |
| Framework retro | All EMs | What's working, what's not, what to change in the framework |
| Quarterly review | Director | Strategy, people, goals (see quarterly review template) |

---

## 4. Maturity Model — Where Teams Are and Where They're Going

Not all teams start at the same place. Use this to assess where each team is and set realistic expectations.

### Level 1: Forming (Survival)

**Focus:** Stability, basic processes, trust building.

- Team is new or recently restructured
- Sprint commitments are inconsistent
- Processes are being established
- People are learning to work together
- AI: Individual exploration is fine. No push for AI adoption — stability first.
- Execution: EM drives urgency and decisions. Focus on building the habit of finishing commitments, not speed.

**EM focus:** Build trust, establish ceremonies, create psychological safety. Don't optimize — stabilize.

**Current teams at this level:** [Assess your teams]

### Level 2: Norming (Consistency)

**Focus:** Predictable delivery, clear ownership, healthy team dynamics.

- Sprint commitment hit rate approaching 80%
- Processes are consistent and followed
- Team has healthy conflict — issues are raised
- Code review and quality practices in place
- Documentation exists for critical paths
- AI: Introduce AI tools for routine work (test generation, documentation). Identify 1 champion per team.
- Execution: Team begins owning sprint commitments. EMs push decisions down (L3-L4). Carry-forward items tracked explicitly.

**EM focus:** Raise the bar on quality and accountability. Start developmental 1:1s. Delegate more.

**Current teams at this level:** [Assess your teams]

### Level 3: Performing (Excellence)

**Focus:** High delivery with high quality, proactive improvement, cross-team impact.

- Sprint commitment consistently ≥80%
- Bug escape rate is low and trending down
- Team proactively improves processes
- Engineers are growing and taking on stretch
- Cross-team collaboration is natural
- EM is strategic, not just operational
- AI: Active AI integration in workflows. Team-level AI metrics tracked. AI patterns shared across the org.
- Execution: Team self-manages urgency. Engineers own cross-team coordination. Decisions made at the lowest capable level.

**EM focus:** Stretch assignments, cross-team initiatives, innovation time. Prepare future leaders.

**Current teams at this level:** [Assess your teams]

### Level 4: Multiplying (Impact Beyond the Team)

**Focus:** Influence beyond team boundaries. Setting standards for others.

- Team exports best practices to the wider org
- Team members mentor across teams
- EM is developing future EMs
- Innovation and improvement are continuous
- Team is the reference for "how to do it well"
- AI: Defining AI best practices for the org. Exporting patterns. Innovation time includes AI R&D.
- Execution: Team exports execution norms to the wider org. EM drives improvements without Director involvement. Anti-patterns caught and corrected by the team.

**EM focus:** Scale impact. Lead cross-team initiatives. Build the next generation.

**Current teams at this level:** [Assess your teams]

---

## 5. How EMs Use This Framework

### Step 1: Assess (Week of Feb 24)

Rate your team honestly against the standards in Section 1. Use the maturity model to identify your level. Identify 2-3 areas where the gap is biggest.

### Step 2: Baseline (Week of Mar 2)

Capture current metrics for your team scorecard (Section 2). This is the starting point, not a judgment. Bad numbers are fine — they tell us where to focus.

### Step 3: Set Targets (Week of Mar 9)

Based on your maturity level and baseline, set realistic targets for Q2. Not everything needs to improve at once. Pick 2-3 metrics to move.

### Step 4: Operate (Ongoing)

Follow the operating rhythm in Section 3. Use the monthly scorecard review to track progress. Adjust as you learn.

### Step 5: Retro (End of Q1)

In the quarterly framework retro, share: what worked, what didn't, what we should change. This framework evolves based on real feedback.

---

## 6. What I Commit To as the Leader

This isn't just for EMs. Here's what I own:

- **Clarity:** Clear priorities, clear expectations, clear decisions. If something is ambiguous, that's on me.
- **Support:** Available for the hard stuff. Escalations, people problems, cross-team conflicts. Don't carry them alone.
- **Development:** Every EM gets developmental feedback, not just operational check-ins. At least one growth conversation per month.
- **Air cover:** When teams need space to improve, I protect that space from outside pressure.
- **Accountability:** I hold the framework accountable too. If it's not working, we change it. This is a tool, not bureaucracy.
- **Recognition:** Wins get acknowledged. Progress gets celebrated. Not just outcomes — improvement.

---

## 7. What This Framework Is Not

- **Not a performance management tool.** This doesn't replace individual performance reviews. It's about team performance and operating standards.
- **Not a one-size-fits-all mandate.** Teams at different maturity levels have different priorities. A forming team shouldn't be measured like a performing team.
- **Not static.** This evolves. The quarterly retro exists specifically to challenge and improve it.
- **Not about control.** The goal is shared language and shared expectations — not micromanagement. EMs own how they get there.
- **Not an AI mandate.** AI is a capability multiplier, not a requirement. Teams adopt at their maturity level.
- **Not about panic urgency.** Healthy speed means finishing what matters, not rushing everything. Bias for action is not an excuse for thoughtless execution.

---

## 8. AI-Augmented Engineering

AI is changing how engineering teams work. This section defines how we approach that change — not as a mandate, but as a structured evolution layer on top of the framework above.

### 8.1 Our AI Strategy: Structured Fast-Follower

We're not pioneers. We run a platform at significant scale — we can't afford to be the first to adopt every new pattern and absorb the cost of things breaking. We're also not lagging behind. The teams that ignore AI will fall behind in 12-18 months.

Our approach: adopt proven patterns quickly, with structure.

- **Wait for patterns to stabilize** (2-4 months after emergence). Let others find the sharp edges.
- **Adopt with clear evaluation criteria.** When a pattern is ready, we move fast. Each team has a champion who evaluates and rolls out.
- **Measure impact before scaling.** Prove it works on one team before pushing to all [NUMBER_OF_TEAMS].
- **Stay skeptical of hype.** 2025 saw a wave of AI-first mandates — Shopify's, requiring teams to justify new headcount against AI, was the most copied. Whatever those produce, a mandate is not a plan. We take a more structured path.

This is a core tenet for me: we adopt because we've evaluated, not because we're afraid of missing out.

### 8.2 AI-Era Metrics

These are **optional/experimental** additions to the Team Scorecard (Section 2) for Q2-Q3. We track them to learn, not to judge.

| Metric | What it measures | Why it matters | Anti-pattern to avoid |
|--------|-----------------|----------------|----------------------|
| AI Acceptance Rate (team-level only) | % of AI suggestions accepted by the team | Adoption signal | Don't measure per person — creates gaming |
| AI Rework Rate | % of AI-generated code changed within 7 days | Quality of AI output | Low rework ≠ good code if nobody reviews |
| Review Bottleneck Ratio | Time waiting for review vs time coding | Flow efficiency as AI increases PR volume | Don't speed up reviews at the expense of quality |
| Code Duplication Trend | Are AI tools introducing copy-paste patterns? | Architectural health signal | Zero duplication isn't the goal — the trend matters |

Key principle: **Never measure individual AI usage.** Team-level only. The goal is to understand impact, not to surveil.

### 8.3 The Productivity Paradox

Individual output rises with AI tooling. Organizational delivery often doesn't move with it. That disconnect is the thing to manage — and it is measurable.

Why it happens:
- More code generated = more code to review, test, and maintain
- Review becomes the bottleneck: teams with high AI adoption merge **98% more PRs** while PR review time rises **91%** ([Faros AI, *The AI Productivity Paradox*](https://www.faros.ai/blog/ai-software-engineering) — telemetry from 10,000+ developers across 1,255 teams)
- Teams ship faster individually but system complexity grows

What this means for us:
- Don't chase individual productivity metrics. They will look great and mean nothing.
- Focus on cycle time and quality metrics — these are already in our scorecard and they capture what actually matters.
- Watch for review bottleneck as a leading indicator. If AI increases output but reviews pile up, we haven't gained anything.
- Quality at source becomes MORE important with AI, not less. The cost of shipping bad code faster is worse than shipping less code.

### 8.4 Role Expectations in the AI Era

How each level evolves. This ties to the maturity model in Section 4.

**Engineers (all levels):**
- AI is a tool, not a replacement. Learn to use it. Judge its output critically.
- Junior: AI accelerates learning but doesn't replace understanding fundamentals. If you can't explain what AI generated, you don't understand it yet.
- Senior: Shift from writing more code to reviewing and judging more output. Your value is in knowing what's right, not in typing speed.
- Staff+: Lead AI adoption patterns. Define quality standards for AI-generated code. Architect systems where AI and humans complement each other.

**Engineering Managers:**
- New skill: evaluating team productivity when individual output metrics are unreliable.
- Coach engineers on effective AI usage, not just tool adoption.
- Watch for: false velocity (shipping more but quality dropping), review bottleneck, junior engineers skipping fundamentals.
- Growing need for product thinking as AI handles more implementation work.

**Engineering Leader (you):**
- Set AI strategy for the org (this section).
- Create psychological safety for experimentation AND structured skepticism.
- Ensure AI adoption doesn't create new inequality (access, training, tooling).
- Track organizational metrics (cycle time, quality) not just individual output.

### 8.5 AI Culture Principles

Five principles for the culture we're building:

1. **Experiment openly, evaluate honestly.** Try AI tools. Share what works AND what doesn't. No pressure to adopt everything.
2. **Quality over speed.** AI lets you go faster. That doesn't mean you should. The bar for shipping stays the same.
3. **Understand what you ship.** No black-box code in production. If you can't explain what AI generated, don't merge it.
4. **Share patterns, not just tools.** When you find an effective AI workflow, document and share it. Champions emerge from practice, not mandates.
5. **Protect the fundamentals.** Code review, testing, documentation, architecture — these matter MORE with AI, not less. AI makes it easier to create; humans ensure what's created is right.

### 8.6 AI Adoption by Maturity Level

Maps to Section 4. Teams adopt AI based on their stability, not on a universal timeline.

| Team Maturity | AI Adoption Focus |
|---------------|-------------------|
| Level 1: Forming | Not ready for an AI adoption push. Stabilize first. Individual exploration is fine. |
| Level 2: Norming | Introduce AI tools for routine work (test generation, documentation). Identify 1 champion per team. |
| Level 3: Performing | Active AI integration in workflows. Team-level metrics tracked. AI patterns shared across the org. |
| Level 4: Multiplying | Defining AI best practices for the org. Exporting patterns. Innovation time includes AI R&D. |

Current state: Assess your teams against the maturity model. Focus AI adoption on Performing teams first — they have the stability to absorb change.

### 8.7 AI Rollout (addition to Rollout Plan below)

| When | What | Who |
|------|------|-----|
| [Week 1] | Share AI section with EMs, gather feedback | You + EMs |
| [Week 2] | Identify 1 AI champion per Level 3 team | EMs |
| Q2 | Start tracking experimental AI metrics (team-level) | EMs + Director |
| Q2 end | First AI metrics review — decide what to keep | All EMs |

---

## 9. Execution Culture — How We Work

Sections 1-3 define what we do and when. This section defines how execution should feel. Standards and cadences work only if the culture underneath supports them.

### 9.1 Principles

Four axioms that shape how we execute:

1. **Finishing > Starting.** WIP kills throughput. A finished feature beats three started ones. When in doubt, close something before opening something new.
2. **Bias for action on reversible decisions.** Reserve deliberation for irreversible decisions. Everything else: decide with 80% confidence, course-correct if wrong. Grounded in Principle #3 (Speed Where It Matters) and #10 (Progress Over Perfection).
3. **Ownership at the lowest capable level.** The person closest to the problem who can make the decision should make the decision. See the Delegation Ladder (L1-L5) in [[developing_engineering_managers]].
4. **Quality is speed.** Cutting corners creates rework. Rework is slower than doing it right. This is not a contradiction to bias for action — ship it, but ship it right.

### 9.2 Urgency: Healthy Speed

Urgency is not panic. This table draws the line.

| Healthy Urgency | Panic |
|-----------------|-------|
| Making decisions when you have enough information | Rushing without thinking because something feels urgent |
| Raising blockers immediately, not at the next standup | Escalating everything as P0 |
| Finishing what's in progress before starting something new | Starting things to show activity |
| Communicating a slip the day you see it | Hoping the schedule problem resolves itself |
| Cutting scope to hit a date with rationale | Cutting quality to hit a date |
| Saying "we don't know yet, here's when we will" | Making up an answer to avoid looking uncertain |

**Forcing functions for teams:**

- **3-Day Stall Rule.** Adapted from the Director's 3-Day Carry Rule ([[engineering-leader-operating-model]], Rule 1). If a task hasn't moved in 3 days, the EM asks why. If the answer is a dependency, it gets an owner and a 48-hour resolution deadline per [[escalation-criteria]].
- **Decision deadlines.** Adapted from Decision Forcing Functions ([[engineering-leader-operating-model]], Rule 3). Every significant decision gets a decide-by date. Default option wins if the date passes. EMs apply this within their teams, not just Director-level decisions.
- **Dates as commitments.** When dates slide without accountability, it's a culture problem, not a scheduling problem. Slips happen — but silent slips compound.

### 9.3 Empowerment: Autonomy with Accountability

What "empowerment" means changes as the team matures. This maps to the Maturity Model in Section 4.

| Maturity Level | Empowerment Expectation |
|----------------|-------------------------|
| **Level 1: Forming** | EM makes most decisions. Team follows established process. Engineers flag issues, EM resolves. |
| **Level 2: Norming** | EM pushes decisions to L3-L4 ([[developing_engineering_managers]], Delegation Ladder). Team owns sprint commitments. Engineers propose solutions, not just problems. |
| **Level 3: Performing** | Engineers own cross-team coordination directly. EM is strategic, not operational. Director is consulted, not deciding. |
| **Level 4: Multiplying** | EM owns team strategy end-to-end. Director consulted on direction, not involved in execution. Team self-corrects without escalation. |

**Decision-making at the right level.** Use RAPID ([[developing_engineering_managers]]) to clarify who decides. One rule: if you're always the D in RAPID, you're not developing your team.

**What "ownership" means concretely:**
- You know the status without being asked.
- You raise problems before they're discovered.
- You propose solutions, not just flag issues.
- You follow through without being reminded.

**Anti-patterns:**

| Anti-Pattern | What It Looks Like | The Fix |
|---|---|---|
| Permission-seeking | EM asks Director before every decision, even at L4 | Explicitly set delegation level. Push back: "What would you do?" |
| Empowerment theater | Delegate then override the decision | If you're going to override, don't delegate. Own that it's L1. |
| Abdication | Hand off with no context, check-in, or support | Delegation needs a clear brief, timeline, and support level |

### 9.4 Collaboration: One Team

When several teams share a platform, disagreement about priorities and technical approach is normal. The question is whether we resolve it or avoid it.

**Trust before coordination.** Coordination is tracking dependencies in Jira. Collaboration is proactively reaching out before you're blocked. The Lencioni model ([[team_health]]) shows why: without trust, you can't have honest conflict. Without conflict, you can't get real commitment. Without commitment, coordination is theater.

**Cross-team norms:**
- Dependencies identified at planning, not at delivery.
- Blockers get an owner within 48 hours ([[escalation-criteria]]).
- EMs resolve disagreements between themselves first. Escalate to Director only if stuck after one attempt.
- Sprint reviews are open — anyone from the wider org can attend.

**The one-team test:** "That's not my team's problem" = cultural failure. "Let me check with that team" = collaboration.

### 9.5 Anti-Patterns — What Bad Execution Looks Like

These patterns are organizational, not individual. If you see them, name them.

| Anti-Pattern | What It Looks Like | Why It's Dangerous | The Fix |
|---|---|---|---|
| Analysis paralysis | Decisions carried 3+ weeks, "need more data" as default response | Cost of delay exceeds cost of being slightly wrong | Set decide-by date. 80% confidence is enough for reversible decisions. |
| WIP explosion | 8 things in progress, 0 finished this sprint | Throughput drops, context-switching burns energy, nothing ships | WIP limits per team. Finish before starting. |
| Hero culture | One person saves the day, 12h+ days normalized, "only they can do it" | Hero burns out. Team never builds capability. Single point of failure. | Distribute knowledge, rotate ownership, celebrate team delivery not individual rescues. |
| Coordination theater | Status meetings with 12 people, no decisions made, everyone "aligned" | Consumes time, produces nothing, creates illusion of progress | Every meeting has a purpose, an owner, and expected decisions. No purpose — cancel. |
| False velocity | More stories shipped but quality declining, bugs increasing | Looks like progress, product gets worse, rework eats future capacity | Track quality alongside delivery. Scorecard (Section 2) already does this — use it. |
| Drift | 1:1 topics never get discussed, priorities shift weekly without explanation, important items carried indefinitely | Small delays compound into missed quarters. Problems grow in silence. | Written agendas, open with key items, track carry-forwards. Apply the 3-Day Stall Rule. |

---

## Rollout Plan

| When | What | Who |
|------|------|-----|
| Week 1 | Draft v1 (this document) | You |
| Week 2-3 | Share with EMs for feedback in 1:1s | You + EMs |
| Week 2-3 | Discuss execution culture norms in 1:1s — ask EMs which anti-patterns they see | You + EMs |
| Week 4 | Incorporate feedback, publish v1.0 | You |
| Week 5-6 | Baseline metrics captured per team | EMs |
| Week 7-8 | Targets set per team | EMs + You |
| End of quarter | First quarterly retro on the framework | All EMs |

---

## Related Documents

- [[team_health]] — Team health assessment framework (Lencioni, Hogan)
- [[developing_engineering_managers]] — EM development framework
- [[engineering_leadership]] — Engineering leadership frameworks (Grove, Larson, Fournier)
- [[jira_plan_system]] — Jira Plan system design and cadences
- [[engineering-leader-operating-model]] — 3-Day Carry Rule, Decision Forcing Functions, carry-forward check
- [[escalation-criteria]] — When and how to escalate blockers and risks

---

*This is a living document. Version history tracked in git.*
