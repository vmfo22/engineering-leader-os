---
name: weekly-review
description: End-of-week ritual - reads the week's daily notes, goals, team health, and initiatives, runs the 9-domain scan and connection check, forces at least two cuts for next week, and writes reviews/weekly/YYYY-Www.md. Run as /weekly-review on Friday. A time-allocation audit is leverage-audit; the monthly synthesis is monthly-review.
allowed-tools: Read, Glob, Grep, AskUserQuestion
---

# /weekly-review

User input: $ARGUMENTS

## Instructions

When the user invokes `/weekly-review`, follow these steps:

### Step 1: Read the template
Read the weekly review template from `reviews/weekly/_template.md`.

### Step 2: Find daily notes
Use Glob to find all daily check-in files from the past 7 days in `reviews/daily/`.
Read each file to extract:
- Wins and accomplishments
- Friction points and challenges
- Energy patterns
- Key meetings and outcomes
- Tasks completed vs pending

### Step 3: Reference goals
Read `goals/90_day.md` to check progress against quarterly priorities.

### Step 4: Check team health
Read `teams/health_tracker.md` for team pulse data.

### Step 5: Review initiatives
Check `initiatives/_dashboard.md` or `initiatives/` folder for progress on key initiatives.

### Step 6: Check decisions made
Use Glob to find any decision files from the past week in `decisions/` folder.

### Step 7: Review 1:1 quality
Look for mentions of 1:1 meetings in daily notes to assess quality and follow-ups.

### Step 8: Domain Scan
After gathering all data from previous steps, assess each of the 9 scanning domains using signal from the week's daily notes, 1:1s, team health, and initiative status:

| Domain | What to assess |
|--------|---------------|
| Individual Wellbeing | Anyone at risk? Energy/morale concerns from 1:1s or daily notes? |
| Team Health | Already gathered in Step 4 — confirm the overall signal. |
| Strategic Progress | Are quarterly goals advancing or stalling? |
| Leadership Relationships | Any tension or drift with your manager, skip-level, or upward? |
| Peer Relationships | Any cross-org connections made or missed this week? |
| Group Visibility | Did anything worth amplifying happen that didn't go upward? |
| Strategy / Direction | Is the roadmap still the right bet? Any shifts from meetings? |
| Operations / Process | Any process friction surfaced in daily notes or 1:1s? |
| Delivery / Execution | Anything stuck, slipping, or about to surprise? |

Mark each green/amber/red. Flag domains needing action next week.

### Step 9: Connection Moments
Review the week for low-stakes connection moments:
- Dropped into a team channel thread (not just work topics)
- Had an unstructured conversation with a report (not a 1:1 agenda item)
- Engaged with a peer outside of a formal meeting
- Was visible in a group setting (all-hands, demo, Slack)
- Reached out to someone not talked to in 2+ weeks

Score 0-5. Note who the user is losing touch with.

### Step 9.5: Required Subtraction (do NOT skip)

Before generating the review, force the subtraction the brain skips. Humans default to adding (only ~12% of people remove anything when improving a system — *Nature* 2021). Left unchecked, every week's plan grows and nothing gets cut — the documented root of plan slippage.

Ask the user directly and require an answer:

> **What gets cut or demoted next week?** Name at least 2 things you will stop, drop, defer, or hand off. Carrying everything forward is not an option here.

Pull candidates from the data to make it concrete:
- Carries that have aged 3+ weeks (likely never going to happen — kill or hand off)
- 🔴 items that slipped multiple days this week (the plan was over-stuffed)
- Recurring meetings flagged as noise in "What Was Noise"
- Anything in the inbox older than this week

If you keep a reading backlog (e.g. `read_later.md`), skim it too and name what to **archive** (already consumed) or **drop** (won't realistically read). A reading list that only grows is the Collector's Fallacy in miniature.

The review is not complete until this is answered. Record the cuts in the file.

### Step 10: Generate weekly review
**Check whether the target file already exists before writing.** If `reviews/weekly/YYYY-Www.md` is already there, stop and ask: "`reviews/weekly/YYYY-Www.md` already exists. Update it in place, append a new section, or overwrite it?" Never overwrite without an explicit answer.

Otherwise create a new file at `reviews/weekly/YYYY-Www.md` using the current ISO week number.

The file should synthesize:
- **What Moved the Needle:** 2-3 high-impact accomplishments from the week
- **What Was Noise:** Time spent that didn't create value
- **Time Leaks:** What took longer than expected
- **Strategic Insight:** Patterns or realizations from the week
- **90-Day Goals Status:** Quick progress check
- **Team Health Pulse:** Any concerns across teams
- **Domain Scan:** Traffic-light table across 9 domains + domains needing action next week
- **Connection Moments:** Score and "who am I losing touch with?"
- **Decisions Made:** Key decisions this week
- **Cut / Demoted:** What's being stopped, dropped, deferred, or handed off next week (from Step 9.5 — at least 2)
- **Next Week:** One big focus + top 3 priorities

### Output
After creating the file, summarize:
- The file path created
- Top 3 things that moved the needle
- Main focus for next week
- Any concerns flagged
- Domain scan: which domains are amber/red and why
- Connection score and any relationship gaps

## Gotchas

- **ISO week numbers can be wrong if computed.** Derive from the most recent weekly review file name. On the very first run (no prior weekly file), derive it from a recent daily note's date or just ask the user for the week number. Do not guess.
- **Read ALL daily files for the week.** Do not skip any day, even if it looks short. A one-line daily note might contain the week's biggest insight.
- **Do not soften bad news in the team health pulse.** If a team is struggling, say so directly. The user wants honest assessment, not reassurance.
- **If daily notes are missing for some days,** note which days had no check-in rather than silently ignoring the gap.
- **"What Was Noise" must be specific.** "Too many meetings" is not useful. "3h in cross-team syncs that produced no decisions" is.
- **Step 9.5 (Required Subtraction) is mandatory, not optional.** Do not generate the review without at least 2 named cuts. If the user resists or says "nothing to cut," push back once with a concrete aged-carry candidate from the data. The whole point is to counter the additive bias that inflates every plan.
