# /monthly-review

Use when user asks for a monthly review, monthly summary, end-of-month reflection, "how did this month go", or mentions monthly wrap-up.

---
allowed-tools: Read, Write, Glob, Grep, AskUserQuestion
---

## Instructions

When the user invokes `/monthly-review`, follow these steps:

### Step 1: Read the template
Read the monthly review template from `reviews/monthly/_template.md`.

### Step 2: Find weekly reviews
Use Glob to find all weekly review files from the past 4-5 weeks in `reviews/weekly/`.
Read each file to extract:
- What moved the needle each week
- Strategic insights
- Team health pulse trends
- Domain scan signals (green/amber/red per domain)
- Connection moment scores
- Decisions made
- Recurring friction points

### Step 3: Find daily notes
Use Glob to find all daily check-in files from the past month in `reviews/daily/`.
Scan for:
- Energy patterns (averages, low points)
- Wins and friction points
- Morning scan signals that recurred
- Carry-forward patterns (anything carried 3+ days)

### Step 4: Reference goals
Read `goals/90_day.md` to assess progress against quarterly priorities.
Read `goals/1_year.md` if it exists for longer-term context.

### Step 5: Check team health
Read `teams/health_tracker.md` for current team health data.
Compare against any weekly pulse data to identify trends.

### Step 6: Review initiatives
Glob `initiatives/active/` for active trackers or dashboards; read the most recently modified one for progress context.

### Step 7: Check decisions made
Use Glob to find decision files from the past month in `decisions/` folder.
Note any decisions that are overdue or pending.

### Step 8: Review people context
Use Grep to search for recent updates in `people/` files.
Note any development highlights, concerns, or feedback gaps.

### Step 9: Deep Domain Scan
This is the core monthly addition. Assess each of the 9 domains at depth using all data gathered:

**People Lens:**
- **Individual Wellbeing:** Who is thriving? Who is struggling? Anyone I've been avoiding a hard conversation with? Anyone who deserves recognition I haven't given?
- **Team Health:** What do the numbers not capture? Any team dynamics shifting?
- **Leadership Relationships:** How is the relationship with my manager? Any unspoken tension? Any senior leaders to invest in?
- **Peer Relationships:** Which peer relationships are strong vs transactional? Am I seen as a partner or a silo?

**Direction Lens:**
- **Strategy / Direction:** Is the current strategy still right? What has changed? Biggest strategic risk? Any strategic conversation being avoided?
- **Group Visibility:** Does the broader org understand what my group does and why? When was the last proactive upward communication?
- **Strategic Progress:** Am I confusing activity with progress? Where?

**Execution Lens:**
- **Operations / Process:** Which ceremony or process has become theater? What operational friction are engineering managers complaining about? Where is toil accumulating?
- **Delivery / Execution:** Which deliverables am I most worried about? Any team consistently underdelivering? Am I close enough to execution?

Synthesize into: top 3 concerns + committed actions with deadlines.

### Step 10: Generate monthly review
**Check whether the target file already exists before writing.** If `reviews/monthly/YYYY-MM.md` is already there, stop and ask: "`reviews/monthly/YYYY-MM.md` already exists. Update it in place, append a new section, or overwrite it?" Never overwrite without an explicit answer.

Otherwise create a new file at `reviews/monthly/YYYY-MM.md` using the current month.

The file should synthesize all sections from the template:
- **Month Overview:** Theme + one sentence summary
- **Progress Toward Quarterly Goals:** Status table + what moved, stalled, needs attention
- **Key Accomplishments:** Top 5
- **Team Health Trends:** Per-team start/end comparison with trends
- **Key Decisions Made:** Table with impact assessment
- **Initiatives Status:** Progress table
- **Deep Domain Scan:** Full 9-domain assessment with top 3 concerns and action commitments
- **People:** Development highlights, concerns, feedback delivered + feedback owed
- **Time & Energy:** Where time went, energy assessment, burnout check
- **Sustainability Reflection:** Was it sustainable? Boundaries maintained/violated?
- **Patterns and Insights:** From weekly reviews
- **Looking Ahead:** Next month's focus, key dates, risks, commitments
- **Life Map Quick Check:** 6 dimensions scored

### Output
After creating the file, summarize:
- The file path created
- Month theme and one-sentence summary
- Top 3 accomplishments
- Domain scan: which domains are amber/red and the top 3 concerns
- Goal progress (on track / behind / at risk per goal)
- Key focus for next month
- Any hard conversations or actions being avoided

## Gotchas

- **Read ALL weekly reviews for the month.** Do not skip any. A week that looks quiet might contain the month's biggest signal.
- **The Deep Domain Scan is the most important section.** Do not rush it or make it generic. Use specific names, teams, and situations from the data gathered.
- **Do not soften the assessment.** The user wants honest, direct evaluation. If a domain is red, say why with specifics.
- **Compare against last month's review** if it exists. Read it to identify trends and check whether last month's committed actions were completed.
- **Flag avoidance patterns.** If the same concern appears in weekly reviews but no action was taken, call it out explicitly. Push on this — it's one of the most common avoidance patterns for engineering leaders.
- **The "Feedback You Should Have Given But Didn't" section must be honest.** Push on this — it's one of the most common avoidance patterns for engineering leaders.
- **Month file naming:** Use YYYY-MM.md format (e.g., 2026-04.md).
