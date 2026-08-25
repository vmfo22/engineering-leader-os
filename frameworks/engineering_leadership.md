# Engineering Leadership Frameworks

*Synthesized from Will Larson, Camille Fournier, and Andy Grove*

This document captures the key frameworks for engineering leadership—how to think about your role, your time, your teams, and your impact.

---

## The Job of an Engineering Director

### From The Manager's Path (Fournier)

As you move up, your job shifts:

| Level | Primary Focus |
|-------|---------------|
| Tech Lead | Technical decisions, small team delivery |
| Engineering Manager | Team health, individual growth, sprint delivery |
| Senior Manager | Multiple teams, managers, cross-team coordination |
| **Director** | **Org design, strategy, culture, leadership development** |
| VP | Business strategy, executive alignment, org-wide impact |

**At Director level, you're responsible for:**
- The health and output of multiple teams
- Developing other managers
- Strategy that connects business needs to engineering work
- Culture that enables your organization to succeed
- Representing engineering to the rest of the company
- Making decisions that set direction for quarters, not sprints

**You're NOT responsible for:**
- Every technical decision
- Being in every meeting
- Solving every problem yourself
- Having all the answers

---

### The Three Jobs (Larson)

Will Larson frames the director role as three distinct jobs:

**1. Systems Designer**
- Design the organization itself as a system
- Create processes that scale
- Build feedback loops that surface problems
- Optimize for organizational output, not individual heroics

**2. Sponsor**
- Sponsor people and initiatives
- Create opportunities for others to grow
- Clear paths for your people
- Make introductions, open doors, advocate

**3. Glue Worker**
- Fill gaps others don't see
- Connect people and teams
- Translate between technical and business
- Do the work that makes everything else work

**The balance shifts based on context:**
- Growing org → More Systems Designer
- Stable org → More Sponsor
- Crisis mode → More Glue Worker

---

## High Output Management (Grove)

### The Manager's Output

Andy Grove's core insight:

> A manager's output = The output of their organization + The output of neighboring organizations under their influence

**Implications:**
- Your individual work matters less than how you multiply others
- 1 hour with 10 people = 10 hours of impact
- Your leverage comes from what you enable, not what you do
- Spending time helping a neighboring team can be higher leverage than optimizing your own

### Leverage

**High-leverage activities:**
- Setting clear direction that guides hundreds of decisions
- Building processes that run without you
- Developing leaders who develop others
- Making decisions that unblock many people
- Removing ambiguity that's slowing everyone down

**Low-leverage activities:**
- Attending meetings where you add little value
- Making decisions others could make
- Doing work yourself instead of teaching
- Reviewing everything personally
- Being the bottleneck for information

**The leverage question:** For every hour I spend, how many person-hours of value does it create?

### Task-Relevant Maturity (TRM)

Don't manage everyone the same way. Adjust based on their maturity with the specific task:

| TRM Level | What They Need | Your Style |
|-----------|----------------|------------|
| Low | Clear direction, structure, frequent check-ins | Directive |
| Medium | Goals and guardrails, collaborative problem-solving | Coaching |
| High | Autonomy, big picture context, get out of the way | Delegating |

**Key insight:** The same person can be high TRM in one area and low TRM in another. Your style should vary by task, not by person.

### The Meeting Portfolio

Meetings are a manager's primary tool. Grove's categories:

**Process-oriented meetings** (regular, predictable)
- 1:1s → Maintain relationships, exchange information
- Staff meetings → Align leadership team
- Status meetings → Track progress, surface issues

**Mission-oriented meetings** (ad-hoc, purpose-specific)
- Decision meetings → Make specific decisions
- Problem-solving → Work through specific issues
- Planning → Design future work

**Meeting hygiene:**
- Every meeting should have a clear purpose
- Every meeting should have a clear owner
- Meetings without decisions are information exchanges (handle async?)
- Cancel meetings when the purpose is achieved

---

## Organizational Design

### Conway's Law

> Organizations design systems that mirror their communication structure.

**Implications:**
- If you want different architecture, you might need different org structure
- Cross-team dependencies create cross-team architecture
- Autonomous teams create autonomous services
- Your org chart is a prediction of your system design

### Team Sizing

**Larson's team sizing guidance:**

- 6-8 engineers per team is optimal
- Below 4: team is fragile, hard to staff
- Above 10: coordination overhead explodes
- Managers should have 4-8 direct reports

**The Spotify Model warning:** Squads, tribes, chapters, guilds—the model is descriptive of Spotify, not prescriptive for everyone. Don't cargo-cult.

### The Pendulum

Organizations swing between:
- Centralization ↔ Decentralization
- Specialists ↔ Generalists
- Consistency ↔ Autonomy
- Process ↔ Judgment

**Your job:** Know where you are in the swing, what problems that creates, and when to start swinging back—before you hit the wall.

---

## Leading Leaders

### The Manager of Managers Shift

When you manage managers instead of ICs:

| Before | After |
|--------|-------|
| Give answers | Ask questions |
| Solve problems | Coach problem-solving |
| Direct work | Set context and goals |
| Review code | Review decisions |
| Build trust with ICs | Build trust through managers |
| Know all the details | Accept appropriate abstraction |

### Developing Managers

**What new managers need:**
1. Clear expectations for the role
2. Regular feedback on management (not just results)
3. Safe space to ask "dumb" questions
4. Help processing difficult situations
5. Permission to make mistakes
6. Your faith in their ability

**Warning signs in your managers:**
- They're doing IC work instead of managing
- Their team doesn't feel safe
- They avoid hard conversations
- They're becoming a bottleneck
- They're not developing anyone
- They're burning out

---

## Technical Strategy

### Architecture Decision Records (ADRs)

Document significant technical decisions:
- Context: What situation led to this decision?
- Decision: What did we decide?
- Consequences: What are the implications?

(See `decisions/adr_template.md` for full template)

### Tech Debt as a Management Problem

Tech debt isn't just technical—it's a management decision:
- How much debt is acceptable?
- When do we pay it down?
- Who owns the decision?
- How do we communicate tradeoffs to business?

**Cunningham's metaphor:** Tech debt is like financial debt. Some debt enables growth. Too much debt constrains everything. The question is always: what's the right amount?

---

## Staff+ Engineering Path

### The Two Ladders

IC and management are parallel paths, not a hierarchy:

```
                     VP Eng
                       ↑
          Principal ← → Director
               ↑        ↑
     Staff Eng  ←  →  Sr. Manager
          ↑            ↑
    Senior Eng  ←  →  Manager
          ↑            ↑
       Mid Eng  ←  →  Tech Lead
```

### Staff Engineer Archetypes (Larson)

**Tech Lead:** Deep partnership with a team, owns technical vision
**Architect:** Org-wide technical direction, defines patterns
**Solver:** Tackles the hardest problems that need senior attention
**Right Hand:** Executive's partner on whatever is most critical

**Your job with Staff+ engineers:**
- Clarify which archetype fits their situation
- Give them problems worthy of their level
- Shield them from process that doesn't serve them
- Create visibility for their work
- Help them find their own style of leadership

---

## Crisis Leadership

When things go wrong:

1. **Stabilize:** Stop the bleeding
2. **Communicate:** Over-communicate, especially upward
3. **Investigate:** Understand root cause (no blame)
4. **Fix:** Address immediate and systemic issues
5. **Learn:** Post-mortem without punishment
6. **Improve:** Change systems to prevent recurrence

**In crisis, your job is calm.** Your team will mirror your emotional state.

---

## Key Questions for Directors

### Weekly
- What decisions are blocked waiting for me?
- Who on my team needs attention?
- What's the biggest risk I'm not addressing?

### Monthly
- Is my organization healthy?
- Am I spending time on the right things?
- What's the capability I'm failing to build?

### Quarterly
- Is our strategy still right?
- Do we have the right people in the right seats?
- What should I start/stop/continue?

### Annually
- Am I still the right person for this role?
- What would I do differently if starting fresh?
- What's the long-term vision I'm building toward?

---

*Credits: Synthesized from Will Larson (Staff Engineer, An Elegant Puzzle), Camille Fournier (The Manager's Path), Andy Grove (High Output Management)*
