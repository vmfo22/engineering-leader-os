# Engineering Leader Operating Model

**Owner:** [YOUR_NAME]
**Scope:** [YOUR_SCOPE] — [NUMBER_OF_TEAMS] teams, ~[NUMBER_OF_PEOPLE] people
**Last updated:** [DATE]

*The weekly/monthly rhythm below is an example — adapt the days, times, and blocks to your own calendar.*

---

## Weekly Rhythm

| Day | Morning | Afternoon | Purpose |
|-----|---------|-----------|---------|
| **Monday** | **Strategic Focus Block** (morning, ~2h). No meetings. Slack off. | Architect syncs, overflow | Start with proactive, not reactive |
| **Tuesday** | 1:1s ([NUMBER_OF_DIRECT_REPORTS] reports) | [Your cross-team sync] (bi-weekly), focus block | Alignment day |
| **Wednesday** | [Your Manager] 1:1 (bi-weekly), syncs | Sprint reviews, [your architecture/design forum] (bi-weekly) | Upward + execution visibility |
| **Thursday** | Staff Meeting (AM), 1:1s ([NUMBER_OF_DIRECT_REPORTS] reports) | **Strategic Focus Block** (afternoon, ~2h) | Team alignment + second strategic block |
| **Friday** | 1:1s (remaining), sprint syncs | **Weekly Review + Next Week Plan** (late afternoon) | Close the week |

### Structural Rules

1. **Monday morning is sacred** — no 1:1s, no syncs, no Slack. This is the only guaranteed deep work block.
2. **Thursday afternoon is the second strategic block** — protect it from recurring team standups/refinement. Use for framework drafts, initiative design, and strategic thinking.
3. **Friday wrap is non-negotiable** — weekly review + next week plan happens every week.

---

## Monthly Rhythm

| Week of Month | Activity | Time | Output |
|---------------|----------|------|--------|
| Week 1 | Roadmap Review (Jira Plan consolidated view) | 60 min (Mon strategic block) | Updated initiatives tracker, risks flagged |
| Week 2 | Team Health Assessment + Deep Domain Scan (update health_tracker.md) | 45 min (Fri during weekly review) | Health tracker current, monthly scan logged |
| Week 3 | Upward Summary for [Your Manager] (3 bullets) | 20 min (before manager 1:1) | Summary sent |
| Week 4 | Initiatives Dashboard + Inbox Processing to zero | 30 min (Fri during weekly review) | Dashboard and inbox current |

---

## Cadences by Scope

| Scope | Mechanism | Cadence | Owner |
|-------|-----------|---------|-------|
| Individual team | 1:1 with EM | Weekly | You |
| Individual team | EM updates epic status in Jira Plan | Weekly | EMs |
| Cross-team | [Your cross-team sync] + dependency check | Bi-weekly | You |
| Cross-team | [Your architecture/design forum] | Bi-weekly | Architects |
| Portfolio-level | Staff Meeting (with carry-forward check) | Weekly | You |
| Portfolio-level | Milestone/Initiative review in Jira Plan | Bi-weekly | Director + EMs |
| Portfolio-level | Full roadmap review | Monthly | Director + EMs + PMs |
| Upward | [Your Manager] 1:1 + async summary | Bi-weekly / Monthly | You |

---

## Information Flow

```
Teams → EMs update Jira Plan weekly
  → You review bi-weekly
    → You update Obsidian (initiatives tracker, health tracker)
      → Monthly summary to [Your Manager]
```

| Artifact | Location | Cadence | Owner |
|----------|----------|---------|-------|
| Operational status | Jira Plan | Weekly | EMs |
| Strategic status | Jira Plan + Obsidian initiatives tracker | Bi-weekly | You |
| Team health | Obsidian health_tracker.md | Monthly | You |
| Decisions | Obsidian decisions/ | As made | You |
| People context | Obsidian people/ | After each 1:1 | You |

---

## Personal Effectiveness Rules

### Rule 1: 3-Day Carry Rule

If a "Must Do" item appears for 3 consecutive days without progress, day 4 forces one of three actions:
1. **Do it** — block 2 hours and start
2. **Delegate it** — hand off with clear brief and deadline
3. **Drop it** — remove with explicit note why

No carrying. This is tracked in the daily check-in.

### Rule 2: Strategic Block Protection

- Monday AM and Thursday PM are strategic blocks in calendar
- Nothing gets added unless: people emergency or production incident
- Slack closed (not DND — closed)
- If consumed by reactive work 2 weeks in a row → weekly review must propose a structural fix

This is tracked in the daily evening check-in.

### Rule 3: Decision Forcing Functions

- Every decision in decisions/ has a "decide by" date
- If date passes without decision, the documented default option wins
- Weekly review checks: any decision pending 2+ weeks → resolve or escalate

This is tracked in the weekly review.

### Rule 4: Energy Threshold

- If average weekly energy < 5/10 for 2 consecutive weeks → calendar audit
- If a personal goal has zero progress for 3 consecutive weeks → schedule one action or remove the goal

### Rule 5: Inbox Decay

- Inbox processed to zero every Friday during weekly review
- If not at zero for 2 consecutive weeks → first 30 min of Monday strategic block goes to inbox

---

## Scanning Practice — The Shopkeeper Walk

*Adapted from "management by walking around" for remote/hybrid. A shopkeeper notices things by being present, not by reading reports. Your brain's task-focused network suppresses your awareness network — you can't scan while doing. It has to be scheduled.*

### Daily (~2 min, part of daily check-in)

Not a form — a mental sweep across domains. Notice what pulls your attention. Capture one thing if it matters. Most days this takes under a minute.

### Weekly (~5 min, during Friday review)

Traffic-light scan across 9 domains. Flag amber/red; green means move on. Track low-stakes connection moments.

### Monthly (~15 min, during monthly review, Week 2)

Full depth scan with reflection questions per domain. Prioritize top 3 concerns. Commit to specific actions.

### The 9 Domains

| Lens | Domain | Key Question |
|------|--------|-------------|
| People | Individual Wellbeing | Who needs attention? |
| People | Team Health | Any team feeling off? |
| People | Leadership Relationships | Any tension upward? |
| People | Peer Relationships | Connected or siloed? |
| Direction | Strategy / Direction | Still the right bet? |
| Direction | Group Visibility | Does the org know? |
| Direction | Strategic Progress | Activity or progress? |
| Execution | Operations / Process | Any process theater? |
| Execution | Delivery / Execution | Anything stuck? |

### Low-Stakes Connection Moments

The goal is presence, not monitoring:
- Drop into team channel threads (not just work topics)
- Have unstructured conversations (not just 1:1 agendas)
- Be visible in group settings (demos, all-hands, Slack)
- Reach out to people you haven't talked to in 2+ weeks

Tracked weekly as a simple 0-5 score in the weekly review. No rotation schedule — just notice who you're losing touch with.

---

## Staff Meeting Additions

Add to weekly staff meeting agenda:
- **Carry-forward check** (2 min): Any item carried from last week? Why? Action.
- **Cross-team dependency pulse** (3 min): Any blocker across teams? Escalate or assign.

---

## Quarterly Review Triggers

At the end of each quarter, evaluate:
1. Is the weekly rhythm still working? What needs adjustment?
2. Are strategic blocks actually being used for strategic work?
3. Is the Jira Plan → Obsidian → manager flow producing signal?
4. Are decisions getting made on time?
5. Is the 3-Day Carry Rule being followed?

---

*Created: 2026-02-09*
