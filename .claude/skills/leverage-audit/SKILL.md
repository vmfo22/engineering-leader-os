# /leverage-audit

Use when user asks about time allocation, where their time goes, calendar health, delegation opportunities, energy drains, or says "my calendar is broken", "I'm in too many meetings", or wants a leverage/time audit.

---
allowed-tools: Read, Glob, Grep, AskUserQuestion
arguments: $ARGUMENTS
---

## Instructions

When the user invokes `/leverage-audit`, run a structured time allocation audit.

**Frequency:** Every 2-4 weeks, or when the calendar feels broken.

### Step 1: Load context

Read these files in parallel:
- `reviews/daily/` from the past 14 days (use Glob for the most recent daily files)
- `reviews/weekly/` from the past 2 weeks (most recent weekly reviews)
- `goals/90_day.md` — current quarter priorities
- `memory.md` — energy patterns, work patterns, warning signs
- `initiatives/_dashboard.md` or `initiatives/` folder — what should be getting time

### Step 2: Categorize time

Scan daily notes for how time was spent. Categorize every activity into one of these buckets:

| Category | Examples |
|----------|----------|
| **Meetings — 1:1s** | Direct report 1:1s, skip-levels, peer 1:1s |
| **Meetings — Group** | Staff meetings, all-hands, cross-team syncs, portfolio reviews |
| **Initiative Work** | Active work on key initiatives, framework rollout, strategic projects |
| **Reactive Work** | Escalations, firefighting, unplanned asks, Slack interrupts |
| **People Work** | Coaching, feedback, hiring, performance conversations, review cycle prep |
| **Administrative** | Expense reports, approvals, tooling, process overhead |
| **Strategic Thinking** | Planning, writing, framework development, reflection |
| **Personal Development** | Learning, blog, side projects, reading |

Count estimated hours per category across the 2-week window.

### Step 3: Present time allocation

Show the breakdown:

| Category | Est. Hours | % of Total | Ideal % | Gap |
|----------|-----------|------------|---------|-----|
| Meetings — 1:1s | | | 15-20% | |
| Meetings — Group | | | 10-15% | |
| Initiative Work | | | 15-20% | |
| Reactive Work | | | <10% | |
| People Work | | | 15-20% | |
| Administrative | | | <5% | |
| Strategic Thinking | | | 15-20% | |
| Personal Development | | | 5-10% | |

**Ideal %s are illustrative defaults** — adjust the targets to your role and context (a hands-on lead's mix differs from a director's). Set your own and keep them consistent run-to-run so the gaps mean something.

Flag:
- If reactive work exceeds 15% — that's a system problem, not a discipline problem
- If strategic thinking is under 10% — the calendar is crowding out direction-setting
- If administrative is over 10% — delegation or automation is overdue

### Step 4: Ask the user 4 questions

1. Does this breakdown feel accurate? What would you adjust?
2. Which of these activities can *only you* do? (Director-level, not delegatable)
3. What are the top 2-3 candidates for delegation this month?
4. What drained your energy most in the past 2 weeks?

### Step 5: High-leverage analysis

Based on the data and user answers, generate:

**High-Leverage Activities** (only you can do these — protect them):
- List the activities that are uniquely Director-level

**Delegation Candidates:**

| Activity | Current Owner | Suggested Owner | Why |
|----------|--------------|-----------------|-----|
| | You | [EM/team/peer] | |

**Automation Candidates:**
- Recurring tasks that could be templated, scripted, or eliminated

**Energy Drains:**
- Activities that cost disproportionate energy relative to impact
- Cross-reference with memory.md "What Drains Me" section

### Step 6: The "Run From Your Phone" test

For each recurring meeting or activity, ask: could you do this from your phone on a beach? If not, it requires deep attention — make sure it's scheduled in deep work blocks, not squeezed between meetings.

Categorize:
- **Phone-safe:** Status updates, approvals, quick Slack responses
- **Needs deep focus:** Strategy docs, framework work, difficult conversations, initiative planning
- **Should not exist:** Meetings where you're not needed, recurring meetings with no agenda

### Step 7: Recommendations

Provide the top 3 changes to make before the next audit:

| # | Change | Impact | Effort |
|---|--------|--------|--------|
| 1 | | H/M/L | H/M/L |
| 2 | | H/M/L | H/M/L |
| 3 | | H/M/L | H/M/L |

Set the next audit date (2-4 weeks out).

### Step 8: Check against patterns

Cross-reference findings with memory.md:
- Is the "procrastination -> overwhelm" cycle showing up? (delayed items piling up)
- Are warning signs present? (no thinking blocks, back-to-back meetings, evening catch-up)
- Connect to any relevant insights from the Insights Log

### Output

Display the full audit in chat. Then offer once: "Save this to `reviews/leverage-audits/YYYY-MM-DD.md`?" Write only if the user accepts — creating the directory if it does not exist. Never write without that yes.

If previous audits exist in `reviews/leverage-audits/`, add a **Trends** section comparing this audit to the most recent one. (Load it during Step 1 — see the file list there.)

---

## Adaptability

Adapt the sequence based on what you find. If the data clearly shows one dominant problem (e.g., reactive work at 40%), focus the analysis there rather than mechanically walking through every category. If the user just had a crisis week, acknowledge the anomaly rather than comparing rigidly to ideal allocations.

---

## General Rules

- **Be honest** — don't soften the findings. If the calendar is broken, say so.
- **Compare to last audit** — if a previous audit exists in `reviews/leverage-audits/`, compare progress.
- **Connect to goals** — time allocation should align with 90-day priorities. Flag disconnects.
- **Reactive work threshold** — if >15%, identify the source. Is it team maturity, missing processes, or organizational dysfunction?
- **No generic advice** — every recommendation should reference specific activities from the past 2 weeks.

## Gotchas

- **Time estimates from daily notes are approximations.** Present them as "~X hours" not "X.0 hours." They are derived from meeting counts and descriptions, not time tracking.
- **"Phone-safe" test categories need user validation.** Do not auto-classify meetings the user might disagree with. Present the classification and ask for corrections.
- **Don't compare to ideal allocations rigidly.** Context matters: a week with 3 performance conversations will naturally skew "People Work" higher. Flag deviations but interpret them.
- **If no previous audit exists** in `reviews/leverage-audits/`, say so and establish this as the baseline. Do not fabricate comparison data.
- **Ideal allocation percentages are guidelines, not targets.** A Director's split varies by quarter, team maturity, and crisis load.
