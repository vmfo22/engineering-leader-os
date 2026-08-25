# CLAUDE.md — Engineering Leader OS

*This file tells Claude Code how to work with your Obsidian vault and personal productivity system.*

---

## About This System

This is a personal operating system for an engineering leader based on Rohun Jauhar's CEO Personal OS framework, adapted for engineering leadership.

**Owner:** [YOUR_NAME]
**Role:** [YOUR_ROLE]
**Company:** [YOUR_COMPANY]
**Teams:** [NUMBER_OF_TEAMS] teams, ~[NUMBER_OF_PEOPLE] people ([NUMBER_OF_DIRECT_REPORTS] direct reports)

---

## Vault Structure

```
engineering-leader-os/
├── README.md                    # How to use this system
├── principles.md                # My leadership principles
├── north_star.md                # Long-term direction
├── memory.md                    # Accumulated patterns and insights (CRITICAL)
├── frameworks/                  # Mental models and frameworks
├── interviews/                  # Self-reflection scripts
├── reviews/
│   ├── daily/                   # Daily check-ins (YYYY-MM-DD.md)
│   ├── weekly/                  # Weekly reviews (YYYY-Www.md)
│   ├── monthly/                 # Monthly summaries (YYYY-MM.md)
│   ├── quarterly/               # Quarterly reviews (YYYY-Qn.md)
│   └── annual/                  # Annual reviews (YYYY.md)
├── goals/
│   ├── 90_day.md               # Current quarter priorities
│   ├── 1_year.md               # This year's goals
│   ├── 3_year.md               # Medium-term vision
│   └── 10_year.md              # Long-term vision
├── teams/                       # Team health and context
├── people/                      # Person notes (@Name.md format)
├── initiatives/                 # Active projects and initiatives
├── decisions/                   # Decision log and ADRs
├── meetings/                    # Meeting templates
└── uploads/                     # Past reviews, notes to process
```

---

## Key Files to Always Reference

When helping me, always read these files first:

1. **memory.md** — My patterns, strengths, growth edges, and accumulated insights
2. **writing_style.md** — How I write (CRITICAL for any drafting tasks)
3. **goals/90_day.md** — Current quarter priorities
4. **teams/health_tracker.md** — Team health overview
5. **initiatives/_dashboard.md** — What I'm working on
6. **inbox.md** — Quick capture for tasks and ideas

---

## Common Commands

### Daily Operations

**Create today's daily check-in:**
```
Read the daily check-in template.
Create a new file at reviews/daily/YYYY-MM-DD.md with today's date.
Reference my 90-day goals for context.
Ask me to paste today's schedule (or fill in manually).
```

**Prep for a 1:1:**
```
Read the 1:1 template and the person note for [[@Person Name]].
Find all open action items tagged with their name.
Find any recent wins or feedback I've documented.
Generate a prep document.
```

### Calendar — `/calendar`

Use `/calendar` (or `/calendar today` / `/calendar week`) to pull and format your agenda — conflicts, meeting hours, and estimated focus time. The full procedure lives in the `/calendar` skill (`.claude/skills/calendar/`). Requires the Google Calendar MCP; without it, paste your agenda and Claude will format it. `/daily-checkin` uses the same calendar pull.

### Weekly Operations

**Generate weekly review:**
```
Read all daily check-ins from the past 7 days in reviews/daily/.
Read my 90-day goals and team health tracker.
Create a new weekly review at reviews/weekly/YYYY-Www.md.
Include: what moved the needle, noise, time leaks, strategic insight, team health pulse.
```

### Monthly Operations

**Generate monthly review — `/monthly-review`:**
```
Read all weekly reviews and daily notes from the past month in reviews/.
Read goals, team health, and the initiatives dashboard.
Create a monthly summary at reviews/monthly/YYYY-MM.md — synthesize the weeklies,
run the deep domain scan (People / Direction / Execution), and name the month's top 3 concerns.
```

### Quarterly Operations

**Generate quarterly review:**
```
Read all weekly reviews from the past quarter in reviews/weekly/.
Read all monthly summaries in reviews/monthly/.
Read my memory.md for patterns.
Read my goals/90_day.md and goals/1_year.md.
Create a comprehensive quarterly review at reviews/quarterly/YYYY-Qn.md.
At the end, suggest updates to memory.md.
```

### Writing Tasks

**Draft any message/document:**
```
Read writing_style.md first.
Draft a [email/slack message/document] to [audience] about [topic].
Match my voice exactly. No AI smell.
```

**Review something I wrote:**
```
Read writing_style.md.
Review this draft and flag anything that doesn't sound like me.
Suggest edits that match my voice.
```

### Task Capture

**Add to inbox:**
```
Add to inbox.md: [task description]
```

**Process inbox:**
```
Read inbox.md.
For each item, suggest where it should go based on the processing guide.
Help me move items to their proper locations.
```

### Meeting Prep

**Prep for staff meeting:**
```
Read team health tracker.
Read initiatives/_dashboard.md.
Read this week's daily notes.
Generate talking points for staff meeting.
```

**Prep for skip-level:**
```
Read the skip-level template.
Find context about [[@Person]] from people/ folder.
Generate prep with suggested questions.
```

**Digest pre-reads before a meeting — `/prep-meeting`:**
```
/prep-meeting [paste links/text, or name the meeting]
```
Reads the pre-read docs (Google Docs/Slides, Confluence, Jira, PDFs, public URLs, or pasted text — fetched via the Drive/Atlassian MCP), cross-references your known stance from the vault, and hands back a digest: TL;DR, decisions on the table, where it'll get contested, your angle, and your 2-3 sharpest questions. Display-only — writes no file unless you ask. Distinct from `/prep-1on1` (1:1s, no docs) and `/process-meeting` (post-meeting transcripts).

**Run a recurring decision forum — `/decision-forum`:**
```
/decision-forum [mode]
```
Manages a recurring architecture/decision meeting across its lifecycle: post-meeting wrap, mid-cycle check, prep, and a final agenda before it starts. Tracks how long action items have been open, caps the agenda, and enforces a carry-limit so stale items get killed rather than rolled forever. Set the meeting name, channel, and notes file in `.claude/skills/decision-forum/config.json`.

---

## File Naming Conventions

| Type | Format | Example |
|------|--------|---------|
| Daily notes | YYYY-MM-DD.md | 2026-01-11.md |
| Weekly reviews | YYYY-Www.md | 2026-W02.md |
| Monthly summaries | YYYY-MM.md | 2026-01.md |
| Quarterly reviews | YYYY-Qn.md | 2026-Q1.md |
| Person notes | @FirstName LastName.md | @Sarah Chen.md |

---

## Tagging Conventions

| Tag | Use |
|-----|-----|
| `- [ ]` | Task / action item |
| `- [x]` | Completed task |
| `- [w]` | Win to remember |
| `- [!]` | Feedback delivered |
| `#decision` | Decision made |
| `#insight` | Strategic insight |
| `#pattern` | Pattern noticed |

---

## When Helping Me...

**DO:**
- Reference memory.md for my patterns and context
- **Read writing_style.md BEFORE any drafting task** — match my voice exactly
- Be direct and concise — I prefer clarity over softness
- Call out when I'm repeating past mistakes (check memory.md)
- Suggest connections between current situation and past insights
- Use executive-level language, not therapy-speak
- When drafting: shorter is better, avoid AI-sounding phrases

**DON'T:**
- Add productivity theater or unnecessary structure
- Be overly positive — I want honest assessment
- Forget to reference my 90-day goals for context
- Create new files without checking if similar exists
- Use words from my "avoid" list in writing_style.md
- Sound like ChatGPT default output (too polished, too many transitions)
- Add pleasantries or filler phrases I wouldn't use

---

## My Preferences

- **Tone:** Calm, direct, executive-level
- **Format:** Minimal formatting, no excessive headers or bullets
- **Reviews:** I do daily (5min), weekly (15min), quarterly (60min)
- **1:1s:** I meet weekly with [NUMBER_OF_DIRECT_REPORTS] team leads
- **Energy:** Track patterns to optimize my schedule

---

## Integration Notes

This system lives in Obsidian and is accessed by Claude Code.

### Setting Up MCP Servers (Optional)

MCP (Model Context Protocol) servers extend Claude Code with access to external services. Install the ones this vault uses from the official plugin marketplace:

```bash
claude plugin install atlassian@claude-plugins-official
claude plugin install slack@claude-plugins-official
claude plugin install playwright@claude-plugins-official
```

**Google Calendar / Drive** — Powers `/calendar` and `/daily-checkin` (reads your agenda via the Calendar API), and lets `/prep-meeting` fetch Google Docs/Slides linked from initiatives. Not a plugin: connect it through your Claude Code MCP integrations and run its one-time authentication before first use.

**Atlassian** — Jira and Confluence access. Powers `/execution-review` (Jira sync) and `/prep-meeting` (Confluence/Jira pre-reads).

**Slack** *(optional)* — Enables reading and searching channels. Note that `/decision-forum` never posts to Slack even when this is connected — it drafts in chat and you send it.

**Playwright** *(optional)* — Ad-hoc browser automation. No longer used by `/calendar` (the Google Calendar MCP replaced it), but handy for other web tasks. **Fallback rule:** prefer MCP → CLI → Playwright. When a service has no MCP server and no CLI, Playwright can drive its web UI directly (log in, navigate, read, submit) to get the job done rather than giving up.

Check what's connected with `/mcp`. Tool name prefixes follow the server name — the skills here reference `mcp__atlassian__*` and `mcp__claude_ai_Google_Calendar__*`; if your setup differs, run `/mcp` and adjust `allowed-tools` in the skills that list them.

See the [Claude Code MCP docs](https://code.claude.com/docs/en/mcp) for more server options.

### Obsidian Plugins

These plugins enhance the vault:

- **Dataview** — Query your vault like a database (list recent dailies, filter tasks, etc.)
- **Templater** — Dynamic templates with date variables, cursor placement
- **Periodic Notes** — Auto-create daily, weekly, monthly notes from templates
- **Tasks** — Track tasks across files with statuses, dates, and queries

**Example Dataview query:**
```dataview
LIST
FROM "reviews/daily"
WHERE file.cday >= date(today) - dur(7 days)
SORT file.cday DESC
```

---

*Last updated: {{date}}*
