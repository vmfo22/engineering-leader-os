# /daily-checkin

Use when user says good morning, starts their day, asks about today's priorities, mentions daily check-in, or wants to plan their day.

---
allowed-tools: Read, Write, Glob, Grep, AskUserQuestion, mcp__claude_ai_Google_Calendar__list_events, mcp__claude_ai_Google_Calendar__get_event, TaskCreate, TaskList, TaskUpdate
arguments: $ARGUMENTS
---

**Optional MCP:** the calendar pull uses the Google Calendar MCP (check with `/mcp`). Without it, everything else still works — just paste your agenda when asked. The session task list (Step 8) uses the TaskCreate/TaskList/TaskUpdate harness tools; if they're unavailable, skip Step 8 and note it.

## Instructions

When the user invokes `/daily-checkin` or says "good morning", determine the mode:

- **No arguments**, "good morning", or "morning" → **Mode 0: Morning Briefing** (display only, no file created)
- **"create"** or explicit `/daily-checkin create` → **Mode 1: Full Check-in** (creates file)
- **Morning Briefing followed by user saying "yes" or "create"** → Transition to Mode 1 with pre-populated data

---

## Mode 0: Morning Briefing

Display a concise morning briefing. Do NOT create a file.

### Step 0.1: Pull calendar

Pull today's events with the Google Calendar MCP — same logic as the `/calendar` skill. Call `mcp__claude_ai_Google_Calendar__list_events` in your time zone (from this skill's `config.json` `timezone`, default `[YOUR_TIMEZONE]`), with `eventTypeFilter: ["default"]`, `orderBy: "startTime"`, window today 00:00 → next day 00:00. Follow `nextPageToken` if present.

Parse events:
- Time range from start.dateTime / end.dateTime; name from summary.
- RSVP: the attendee with `self: true` → responseStatus. Organizer with no attendee record = accepted.
- SKIP lunch and focus blocks; track declined separately; detect overlapping time ranges.

**Graceful degradation:** If the Calendar MCP isn't connected or errors (auth/token):
- Note: "Calendar pull failed — paste your agenda, or run `/calendar` once it's connected."
- Continue with the remaining steps. Never block the briefing on calendar data.

### Step 0.2: Open action items

Use Grep to search for `- \[ \]` across:
- `people/` (action items from 1:1s)
- `inbox.md` (Quick Capture and Active sections)

Collect items with owners and due dates. Highlight anything due today or overdue.

### Step 0.3: Goal deadline alerts

Read `goals/90_day.md`. Flag any goals with deadlines within the next 7 days.

### Step 0.4: Yesterday's carries

Find yesterday's daily review (most recent file in `reviews/daily/` before today). Extract any uncompleted tasks (`- [ ]` items) and any items in the "Carry Forward" section.

### Step 0.5: Team health flags

Read `teams/health_tracker.md`. Surface any teams flagged red or with recent status changes.

### Step 0.6: Morning Scan prompts

After gathering all data, before presenting the briefing, do a quick domain scan based on the signals you've collected. Surface any domains that look amber or red:

- **People:** Anyone in the action items who's overdue, struggling, or gone quiet?
- **Teams:** Any team health flags from the tracker? Any team with stalled delivery?
- **Strategy:** Any 90-day goal deadlines approaching with no progress?
- **Delivery:** Any carries piling up? Anything stuck for 3+ days?
- **Operations:** Any process items in the inbox that keep recurring?
- **Relationships:** Any leadership 1:1 missed or overdue? Any peer connection gap?
- **Visibility:** Has anything worth amplifying happened that hasn't gone upward?

Include the top 2-3 domain signals in the briefing under "Morning Scan."

### Step 0.7: Present briefing

Display a concise morning briefing (NOT a file, keep to ~30 lines):

```
**Good morning. Here's your day.**

**Calendar**
| Time | Event | Status | Category |
|------|-------|--------|----------|
| ... | ... | ... | ... |

Conflicts: [list or "none"]
Meeting hours: X | Focus time: Y

**Due today / Overdue**
- [action items with owners]

**Carries from yesterday**
- [uncompleted items from yesterday's review]

**Deadline alerts**
- [90-day goal deadlines within 7 days]

**Team flags**
- [red-flagged teams or recent changes, or "all clear"]

**Morning Scan**
- [2-3 domain signals that need attention today, derived from the data above]
```

Then ask: "Want me to create today's daily check-in file?"

---

## Mode 1: Full Check-in

If running after a Morning Briefing, pre-populate the Calendar and Carry Forward sections with data already gathered. Do not re-ask for the calendar.

### Step 1: Read the template
Read the template from the path specified in this skill's `config.json` (default: `reviews/daily/_template.md`) to understand the structure.

### Step 2: Reference goals
Read `goals/90_day.md` to pull current quarter priorities and any deadline alerts.

### Step 3: Pull tasks from inbox
Read `inbox.md` to identify tasks that should be addressed today.

### Step 4: Ask for calendar agenda
If calendar data was already gathered in Mode 0, use it. Otherwise, use AskUserQuestion to ask:
> "What's on your calendar today? (paste your agenda or describe your meetings)"

This helps plan the day around meetings and commitments.

### Step 5: Consider principles
Read `principles.md` to keep leadership principles in mind when suggesting priorities.

### Step 6: Check pending decisions
Use Glob to find files in `decisions/` folder. Read any recent decisions (last 7 days) to identify pending action items or follow-ups.

### Step 7: Create the daily file
Create a new file at `reviews/daily/YYYY-MM-DD.md` using today's date.

The file should include:
- **Today's Context:** Day type, week theme (from weekly review if exists), main priority
- **Deadline alerts:** Any goals or tasks with upcoming deadlines
- **Must Do Today (HARD CAP: max 3 🔴):** The single most important rule in this skill. A day plan may carry **no more than 3 🔴 must-lands**. If you find yourself about to write a 4th, STOP and make the user demote one to "Should Do" before continuing. Do not write the file with 4+ reds. State the cap out loud: "That's 4 must-lands. The cap is 3 — which one drops to Should Do?" The skill holds the line so willpower doesn't have to.
- **Should Do:** Tasks that would be good to complete if time allows
- **Meetings:** Key meetings from the calendar with prep notes if needed
- **Carry forward:** Items that need attention but weren't completed yesterday
- **Morning Scan:** Include the section from the template. If running after Mode 0, pre-populate "One thing I noticed" with the top domain signal from Step 0.6. Otherwise leave blank for the user.

Do NOT fill in the Energy Level or Evening Reflection sections — those are for the user to complete.

### Step 8: Seed the session task list
After the file is written, build a session task list that mirrors **today's** plan so the day is trackable in this session. **Propose it first — do NOT call `TaskCreate` until the user approves.** This step runs in **Mode 1 only** (Mode 0 writes no file and seeds no tasks).

**8a. Reconcile existing tasks.** Call `TaskList`. If it holds tasks from a previous day or session, include a proposal to clear the completed/stale ones (`TaskUpdate` → status `deleted`) so the list reflects today, not yesterday.

**8b. Select source items — TODAY-actionable only.** From the file you just wrote, turn these into candidate tasks:
- Each **🔴 Must Do Today** item → one task (Step 7 caps these at 3, so ≤3 here).
- Each **🟡 Should Do** item → one task.
- Each row in the **Meetings** table → one task (one per meeting; put the time in the subject).
- From **Carry Forward**, only the **🔴 must-fix-today** and **🆕 today** items → one task each.

**8c. EXCLUDE — today-only rule** (see Gotchas):
- Carry Forward **🟡 multi-week / parked** items.
- **Tomorrow's Priority** items.
- Anything deferred to a future day. These stay in the week plan, never the session task list.

**8d. Bake the outcome into each task.**
- `subject`: short imperative with a scannable marker — `🔴 …` (must-land), `🟡 …` (should-do), `📅 HH:MM …` (meeting).
- `description`: what to do **plus the intended result** — for meetings, pull the "Decision/Prep" content (the decision or outcome to land); for work, the deliverable / done-state.
- `metadata`: `{category: "work" | "meeting" | "outcome", priority: "🔴" | "🟡", time: "HH:MM"}` (omit keys that don't apply).
- `activeForm`: set where a spinner label helps (e.g. "Prepping the 1:1").

**8e. Propose, don't create.** Present the proposed list grouped as **Must-do / Should-do / Meetings**, plus any stale-task cleanup from 8a. Ask the user to approve or iterate.

**8f. On approval, create.** Apply any edits, then call `TaskCreate` once per task (and `TaskUpdate` for the agreed cleanup). All tasks land as `pending`; they move to `in_progress` / `completed` as the day runs.

### Output
After creating the file and seeding the task list, summarize:
- The file path created
- Today's main priority
- Any deadline alerts flagged
- The session task list: count created, grouped by category (must-do / should-do / meetings), plus any prior-day tasks cleared

## Gotchas

- **Do NOT compute day-of-week yourself.** Use file dates, calendar data, or ask the user. Day-of-week calculation is unreliable.
- **Do NOT fill in Energy Level or Evening Reflection sections.** Those are for the user to complete at the end of the day.
- **Always ask about the calendar** (Step 4 in Mode 1). Do not skip it even if you think you have enough context. The calendar question surfaces conflicts and meeting prep needs.
- **If today's file already exists,** warn before overwriting. Ask: "Today's file already exists. Want me to update it or start fresh?"
- **ISO week numbers:** do not compute manually. Read from the most recent weekly review file name if needed.
- **Template path is in config.json.** Read the template path from there.
- **Calendar pull (Google Calendar MCP):** if it's not connected or errors, degrade gracefully — ask the user to paste their agenda. Never block the morning briefing on calendar data.
- **Morning briefing is display-only.** Do not create a file unless the user explicitly confirms.
- **Keep the briefing concise** — no more than ~30 lines of output. The user wants a quick scan, not a document.
- **Enforce the 3-🔴 cap (Mode 1 Step 7).** This is not advisory. If the day would carry more than 3 must-lands, block and force a demotion in the moment. Do not relax it because the user insists everything is critical — that insistence is the pattern the cap exists to catch.
- **Task list is today-only (Step 8).** Never seed future-week carries or "Tomorrow's Priority" into the session task list — those stay in the week plan. The daily check-in is same-day, so the task list is too. Same discipline as the 3-🔴 cap.
- **Always propose the task list before creating it (Step 8e).** Do not call `TaskCreate` until the user has approved or edited the proposal — a validation gate, not silent creation.
