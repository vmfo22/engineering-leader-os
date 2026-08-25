---
name: execution-review
description: Delivery review against the execution tracker, with optional Jira sync - stage movement, at-risk features, risk register, cross-team dependencies, and 3-5 actions for the week. Run as /execution-review for the full portfolio, with a feature name or Jira ID for a deep-dive, or with a filter (at-risk, definition, a team name) for a slice. Meeting prep itself belongs to prep-meeting.
argument-hint: "[full | feature/ID | at-risk | definition | development | cross-team | team name]"
allowed-tools: Read, Glob, Grep, AskUserQuestion, mcp__atlassian__getJiraIssue, mcp__atlassian__searchJiraIssuesUsingJql
---

# /execution-review

User input: $ARGUMENTS

**Requires:** Atlassian MCP (Jira) for the sync steps — check with `/mcp`. Without it, the skill still runs on the tracker alone; it just skips the Jira comparison (say so rather than failing). Set your Jira cloud ID + project key in this skill's `config.json`, and point `tracker_path` at your delivery tracker (default: `initiatives/execution_tracker.md` — copy `initiatives/execution_tracker.md`'s structure to start).

## Instructions

When the user invokes `/execution-review`, determine the mode from the user input above:

- **No arguments** or `full` → Full Tracker Review (all features)
- **A feature name or number** (e.g., `[Feature Name]`, `#15`, `PROJ-123`) → Initiative Deep-Dive
- **A keyword** (e.g., `at-risk`, `definition`, `cross-team`) → Filtered Review

---

## Mode 1: Full Tracker Review

### Step 1: Load context
Read these files in parallel:
- This skill's `config.json` for Jira cloud ID and tracker file path
- The tracker file specified in config.json (default: `initiatives/execution_tracker.md`)
- The status log at the bottom — compare current state to last entry
- `reviews/daily/` from the past 7 days (use Glob for `reviews/daily/YYYY-MM-*.md`)
- `teams/health_tracker.md`
- `goals/90_day.md`
- This skill's `execution-review-history.log` for quick week-over-week comparison

### Step 2: Jira Sync
Read the Jira ID column from the tracker. For any feature missing a Jira ID, ask the user for it.

For each Jira ID, fetch the initiative using `mcp__atlassian__getJiraIssue` (use the cloud ID from this skill's config.json). Pull status for each.

Compare Jira statuses against the Stage column in the tracker. Present a sync table:

| Feature | Tracker Stage | Jira Status | Match? | Notes |

Flag all mismatches. Use Jira as ground truth unless the user overrides.

### Step 3: Stage Movement
Compare current stages to the last Execution Review entry. For each feature:

| Feature | Previous Stage | Current Stage | Weeks in Stage |

Flag anything that hasn't moved stages in 2+ weeks.

### Step 4: Status Changes
Identify any features whose Status changed (On Track → At Risk, etc.). If yes, what triggered the change? Does the risk register need updating?

### Step 5: Risk Review
Read the risk register. For each open risk:
- Is the mitigation still valid?
- Has likelihood or impact changed?
- Any new risks to add from this week's context?

### Step 6: Stage Health
Show corrected stage summary counts. Compare to last review. Flag:
- Features in Definition that should be in Solution Design by now
- Features in Solution Design that should be in Development by now
- Definition count as % of portfolio (watch if >25%)

### Step 7: Cross-Team Check
Review cross-team dependencies. Any that need attention? Who does the user need to talk to this week?

### Step 8: Meeting Prep
Based on what surfaced:
- Topics for upcoming 1:1s (which EMs need a conversation about their features?)
- Talking points for leadership review (if this week)

### Step 9: Actions
List 3-5 specific actions for this week.

| Action | Who | By When |

### Step 10: Update Tracker
Propose updates:
- Stage changes to make (noting which came from Jira data)
- Status changes to make
- New Execution Review entry with date
- New status log entry

**Ask the user to confirm before writing any changes.**

Then update the tracker: the Features table, Stage Summary, Risk Register, Cross-Team Dependencies, and append a new dated entry to the Execution Review Log.

After all updates are written, append a one-line summary to this skill's `execution-review-history.log`:
`YYYY-MM-DD | [Review Type] | Def:X SD:Y Dev:Z | At Risk:N | [key flags]`

---

## Mode 2: Initiative Deep-Dive

For a single initiative, run a focused review.

### Step 1: Identify the initiative
Match the user input above against the tracker — by name, number, or Jira ID. If ambiguous, ask the user.

Read the initiative's row from the tracker (config.json `tracker_path`, default `initiatives/execution_tracker.md`).

### Step 2: Jira deep pull
Fetch the initiative from Jira using `mcp__atlassian__getJiraIssue`.

Then search for child issues (epics/stories) using JQL:
```
parent = [JIRA_ID] ORDER BY status ASC
```

Present:
- Initiative status
- Child epic/story breakdown: how many in each status (To Do, In Progress, Done)
- Any blocked items
- Recent updates or comments

### Step 3: Stage assessment
Based on Jira data, assess:
- **Current stage** — does Jira match the tracker?
- **Stage readiness** — is it ready to move to the next stage? What's missing?
- **Blockers** — anything preventing progress?

### Step 4: Design progress (if in Definition or Solution Design)
- Is there an HLD or design doc linked?
- Who owns the design work?
- What decisions are pending?

### Step 5: Development progress (if in Development)
- Epic/story completion rate
- Sprint velocity signals
- Any stories stuck or blocked?
- Cross-team dependencies resolved?

### Step 6: Risk assessment
- Check the risk register for risks related to this initiative
- Assess: is the current risk level accurate?
- Any new risks surfaced?

### Step 7: Recommendations
Provide 2-3 specific actions:
- What the DRI should focus on
- What the user (Director) should do (escalate, unblock, check in)
- Any conversations needed this week

### Output
Display the deep-dive directly. Do NOT create a file unless the user asks.

---

## Mode 3: Filtered Review

For keyword-based filters, run a subset of the full review.

| Keyword | Filter |
|---------|--------|
| `at-risk` | Only features with Status = At Risk |
| `definition` | Only features in Definition stage |
| `solution-design` | Only features in Solution Design stage |
| `development` | Only features in Development stage |
| `cross-team` | Only features with cross-team dependencies |
| `[team-name]` | Only features owned by that team |
| `[person-name]` | Only features where that person is DRI |

Apply the filter, then run Steps 2-10 from Mode 1 but only for the filtered set. Skip steps that don't apply to the filtered set.

---

## Adaptability

Adapt the sequence based on what you find. If something urgent surfaces early (a feature jumped to At Risk, a major Jira mismatch, a critical blocker), address it immediately rather than mechanically proceeding through the numbered steps. The steps are a guide, not a straitjacket.

---

## General Rules

- **Jira is ground truth** for stages unless the user explicitly overrides
- **Always compare to the last Execution Review** — this is how we detect movement
- **Be direct** — flag problems clearly, don't soften bad news
- **Ask before writing** — never update the tracker without user confirmation
- When adding an Execution Review entry, use this format:

```
### YYYY-MM-DD — [Review Type: Full / Deep-Dive / Filtered]

**Jira Sync:** [summary of mismatches]
**Stage Health:** [counts]
**Risk Changes:** [any changes]
**Flags:** [bullet list]
**Actions:** [table]
```

## Gotchas

- **Jira cloud ID is in config.json.** Never discover it dynamically via getAccessibleAtlassianResources — it wastes time and sometimes returns stale data.
- **Jira is ground truth** for stages unless the user explicitly says otherwise. If the user corrects a stage, note it was a manual override in the status log.
- **Always compare to the LAST execution review entry** in the status log (scroll to the bottom of the tracker), not an arbitrary past entry.
- **Ask before writing.** Never silently update the tracker. Always show proposed changes and get user confirmation.
- **Week-in-stage counts can drift** if the status log has gaps. When in doubt, count from the Jira transition date, not the log.
- **Tracker path comes from config.json.** If the tracker file moves, update config.json — don't hardcode paths in these instructions.
