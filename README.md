# Engineering Leader OS

A personal operating system for engineering leaders. Plain text files + AI.

---

## What This Is

This is a system for managing the cognitive load of engineering leadership — the kind of role where you're responsible for multiple teams, dozens of people, and more context than any human can hold in their head.

It's not a productivity app. It's a set of plain text files in [Obsidian](https://obsidian.md) structured so an AI assistant ([Claude Code](https://code.claude.com/docs), in the terminal or the desktop app) can help you think, write, review, and stay on top of what matters.

The system handles:
- **Daily check-ins** — 5 minutes to orient your day
- **Weekly reviews** — 15 minutes to find patterns and plan the week ahead
- **1:1 prep** — context on every person, pulled together before each meeting
- **Writing** — messages, documents, and reviews drafted in your actual voice
- **Initiative tracking** — what's moving, what's stuck, what needs your attention
- **Pattern recognition** — connecting today's situation to past insights

What it doesn't do: add process for the sake of process. Every file exists because it solves a real problem.

---

## Why

Three problems this solves:

**1. Context overload.** You have several teams, dozens of people, and more initiatives than any one person can hold in their head. No one can keep all that context. The system holds it for you and surfaces what's relevant.

**2. Invisible patterns.** You make the same mistakes, have the same blind spots, and repeat the same goals year after year — but without a system to catch it, you don't notice. The memory file and review cadences make patterns visible.

**3. Writing overhead.** Half the job is communication — emails, Slack messages, documents, performance reviews. The writing style guide means the AI drafts in your voice, not generic AI-speak.

---

## Requirements

### Required

| What | Why | Cost |
|------|-----|------|
| A **Claude paid plan** — Pro, Max, Team, or Enterprise | Claude Code needs one. The free tier can't run it. | Paid |
| **[Claude Code](https://code.claude.com/docs)** | Reads your vault, runs the commands, drafts content. Two ways to get it — see below. | Included with the plan |
| **[Obsidian](https://obsidian.md)** | Reads and edits the vault. Any markdown editor works; Obsidian's plugins make the system better. | Free |
| **Time** | 5 minutes/day, 15 minutes/week, 2 hours/quarter. The system compounds — it gets more useful the longer you run it. | — |

### Two Ways to Run Claude Code

Both run the same engine and share the same configuration, so the vault and its skills work identically in either. Pick whichever you'd rather look at.

**Desktop app** — a graphical interface. No terminal, and you don't install Node.js or the CLI.

- Download it from the [desktop quickstart](https://code.claude.com/docs/en/desktop-quickstart) — macOS and Windows have direct installers; Linux is in beta
- On Windows, you must also install [Git for Windows](https://git-scm.com/downloads/win) — the Code tab won't start local sessions without it. Most Macs include Git already.

**Terminal (CLI)** — `claude` in your shell. Needs Node.js.

```bash
npm install -g @anthropic-ai/claude-code
```

### Required Only For The Version-Controlled Setup

Skip these if you use the [setup without Git](SETUP-WITHOUT-GIT.md).

- **A [GitHub account](https://github.com/signup)** (free) — to create your own private copy of this template
- **Git** — to clone that copy to your machine. Bundled with Xcode Command Line Tools on macOS; [download for Windows](https://git-scm.com/downloads/win)

### Optional

MCP servers connect Claude to your calendar, Jira, and Slack. Everything works without them — they just make some steps automatic instead of manual. See [MCP Servers](#mcp-servers-optional).

---

## Choose Your Setup Path

**[Version-controlled setup](#quick-start)** — the default, below. Your vault becomes a private Git repository, so you get history: every daily note, every revision of `memory.md`, diffable. Requires a GitHub account and basic Git.

**[Setup without Git](SETUP-WITHOUT-GIT.md)** — download the template as a ZIP, keep it in a synced cloud folder, and use the Claude desktop app. No GitHub account, no Git commands, no terminal. You trade version history for cloud backup.

---

## Quick Start

Steps 1-3 get you running in about 10 minutes. Step 4 adds around 30, whether you run the bootstrap or fill the core files in by hand.

### 1. Get your own copy

Click **Use this template → Create a new repository** at the top of this page, and **set it to Private**.

> [!WARNING]
> **Your vault will hold personnel data.** 1:1 notes, performance ratings, flight-risk assessments, feedback you haven't delivered yet, succession plans about people who don't know. Keep your copy private. Don't push it to a public repo, and don't push it back to this one.

Then clone your new repo:
```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git engineering-leader-os
```

Check `.gitignore` before your first commit — it has one decision in it about whether `uploads/` (performance reviews, HR documents) gets versioned.

### 2. Open in Obsidian

Open Obsidian → "Open folder as vault" → select the `engineering-leader-os` directory.

### 3. Set up Claude Code

**Desktop app:** open the **Code** tab, click **Select folder**, and choose your vault directory. Skip the rest of this step.

**Terminal:** install the CLI if you haven't:
```bash
npm install -g @anthropic-ai/claude-code
```

Navigate to your vault and start Claude Code:
```bash
cd path/to/engineering-leader-os
claude
```

Claude Code will automatically read the `CLAUDE.md` file and understand how your system works.

### 4. Run the bootstrap prompt

Open `BOOTSTRAP.md` and copy the prompt into Claude Code. It walks you through a ~30-minute interactive setup: identity, principles, writing voice, goals, teams, people, and self-awareness. Claude asks questions, you answer, it fills in the files.

If you prefer to do it manually, here are the core files:

#### Manual alternative — personalize core files by hand

These are the files that make the system yours — about half an hour end to end:

| File | What to do | Time |
|------|-----------|------|
| `CLAUDE.md` | Replace `[YOUR_NAME]`, `[YOUR_COMPANY]`, `[YOUR_ROLE]`, team counts | 2 min |
| `north_star.md` | Answer the three questions: who you want to become, what life you want, what impact you want | 5 min |
| `writing_style.md` | Fill in your tone profile, add your actual phrases, paste 2-3 writing samples | 10 min |
| `goals/90_day.md` | Set your top 3 priorities for this quarter | 5 min |
| `teams/health_tracker.md` | Add your teams with current health ratings | 5 min |

> [!NOTE]
> If you'll use the calendar features, also replace `[YOUR_TIMEZONE]` (e.g. `Europe/Lisbon`) in the `calendar`, `daily-checkin`, and `prep-meeting` skills — a single find-and-replace.

### 5. Upload your history (optional but powerful)

Drop existing documents into `uploads/`:
- Past annual reviews → `uploads/past_annual_reviews/`
- Performance reviews you've written → `uploads/performance_reviews/`
- Notes, docs, anything relevant → `uploads/notes/`

Then ask Claude Code to process them:
```
Read the files in uploads/ and help me extract relevant information
into the appropriate system files (memory.md, people/ files, etc.)
```

### 6. Run your first daily check-in

In Claude Code:
```
/daily-checkin
```

Claude will read your goals, check your inbox, ask about your calendar, and create a structured daily note. You're up and running.

---

## The Cadences

The system runs on nested review loops. Each one builds on the one below.

### Daily (5 minutes)

**When:** Morning, before your first meeting.

**What:** Run `/daily-checkin`. Claude creates a daily note with your top priorities, deadline alerts, and meeting prep. At the end of the day, fill in the energy check (30 seconds).

**Why:** Orients your day around what actually matters vs. what's loudest.

### Weekly (15-20 minutes)

**When:** Friday afternoon or Sunday evening.

**What:** Run `/weekly-review`. Claude reads all your daily notes, goals, and team health data, then synthesizes what moved the needle, what was noise, and what to focus on next week.

**Why:** Catches patterns you miss in the daily grind. Prevents drift.

### Monthly (30 minutes)

**When:** Last week of the month.

**What:** Run `/monthly-review`. It rolls up the past 4 weekly reviews, runs a deep domain scan (People / Direction / Execution), refreshes the team health tracker, checks initiative progress, and names the month's top 3 concerns.

**Why:** Monthly is where strategic patterns become visible. Are you spending time on the right things?

### Quarterly (2 hours)

**When:** End of quarter. Block real time for this.

**What:** Full review — read all weeklies, update 90-day goals, refresh memory.md with new patterns, set next quarter's priorities.

**Why:** This is where compounding happens. Your memory.md gets richer, your pattern recognition gets sharper, your goals get more honest.

### Annual (half day)

**When:** December or January.

**What:** Run the annual review framework (`frameworks/annual_review.md`). Review all quarterly summaries. Update north star. Run the self-reflection interviews (`interviews/`).

**Why:** Are you building the life and career you actually want? Or just the one that happened?

---

## Working with Initiatives

Initiatives are the projects and bets you're driving or sponsoring. The `initiatives/` folder uses one folder per initiative:

- **Start one:** create a folder under `initiatives/active/`, copy `_project_template.md` (personal/small work) or `_org_initiative_template.md` (org-wide, with DACI and formal tracking) into it as `_initiative.md`, and add a row to `_dashboard.md`.
- **Track them:** `initiatives/_dashboard.md` is your operating view — by priority, by your role (driving / sponsoring / informed), upcoming milestones, and decisions needed. Walk it in your weekly review.
- **Finish one:** fill in the retrospective, move the folder to `initiatives/completed/`, and log it under Recently Completed on the dashboard.

Full convention in `initiatives/README.md`. Longer research tracks get the same folder-per-topic treatment under `research/` (see `research/_index_template.md`).

---

## Claude Code Integration

### How It Works

Claude Code reads the `CLAUDE.md` file at the root of your vault. This file teaches it:
- Your vault structure and where things live
- Your preferences (tone, format, directness)
- Common commands and how to execute them
- What files to reference for context

### Skills (Slash Commands)

Skills are predefined workflows in `.claude/skills/`. They tell Claude exactly how to handle common tasks:

| Command                    | What it does                                                               |
| -------------------------- | -------------------------------------------------------------------------- |
| `/daily-checkin`           | Creates today's daily note with goals, inbox items, and calendar context   |
| `/weekly-review`           | Synthesizes the past week from daily notes into a structured review        |
| `/monthly-review`          | Rolls the month's weeklies into a monthly summary with a deep domain scan  |
| `/prep-1on1 [Name]`        | Pulls context on a person and generates 1:1 prep with topics and questions |
| `/prep-meeting [links]`    | Digests pre-read docs into your stance, contested points, and sharp questions |
| `/draft-message [context]` | Drafts a message in your voice for any channel (email, Slack, doc)         |
| `/execution-review`        | Runs a full delivery-tracker review with Jira sync                         |
| `/decision-forum`          | Runs a recurring architecture/decision forum — agenda, wrap-up, carry limits |
| `/calendar`                | Shows today's or the week's events (Google Calendar MCP), with conflicts and focus-time |
| `/process-meeting`         | Turns a meeting transcript into notes, decisions, and action items, filed to the right places |
| `/log-decision`            | Records a decision (ADR-style) in the decision log                         |
| `/leverage-audit`          | Audits where your time actually goes vs. where it should, from your daily notes |

### What Claude Code Does Well

- **Reads across files** — pulls context from goals, team health, person notes, and recent dailies to give you relevant information
- **Remembers patterns** — references your memory.md to connect current situations to past insights
- **Writes in your voice** — uses your writing_style.md to draft messages that sound like you
- **Tracks over time** — weekly and quarterly reviews surface trends you'd otherwise miss

### What It Doesn't Do

- It doesn't replace your judgment. It surfaces information and drafts content. You decide.
- It doesn't have real-time access to your calendar, email, or Slack unless you set up MCP servers.
- It doesn't automatically create files or update trackers without your approval.

---

## MCP Servers (Optional)

MCP (Model Context Protocol) servers give Claude Code access to external services. The easiest way to add the ones this vault uses is the official plugin marketplace:

```bash
claude plugin install atlassian@claude-plugins-official
claude plugin install slack@claude-plugins-official
claude plugin install playwright@claude-plugins-official
```

Google Calendar and Drive aren't plugins — connect those through your Claude Code MCP integrations (claude.ai connectors) and run the one-time authentication.

**Which skills use which tools** — everything works without MCP; these just make it automatic instead of manual:

| Skill | Uses | Without it |
|-------|------|------------|
| `/calendar`, `/daily-checkin` | Google Calendar | Paste your agenda when asked |
| `/prep-meeting` | Google Calendar + Drive, Atlassian | Paste the docs/links to digest |
| `/execution-review` | Atlassian (Jira) | Runs on the tracker alone; skips the Jira sync |
| `/decision-forum` | Slack (optional) | Drafts posts in chat for you to send |
| all other skills | none | — |

Check what's connected with **`/mcp`** in Claude Code.

> [!NOTE]
> **Tool name prefixes follow the server name.** The skills in this vault reference tools like `mcp__atlassian__getJiraIssue` and `mcp__claude_ai_Google_Calendar__list_events`. If your setup registers a different server name, run `/mcp` to see the real names and adjust `allowed-tools` in the skills that list them.

### Google Calendar & Drive

Used by `/calendar` and `/daily-checkin` to read your agenda through the Calendar API, and by `/prep-meeting` to fetch Google Docs/Slides linked from initiatives. Connect it through your Claude Code MCP integrations and run its one-time authentication. This replaced the old Playwright-based calendar scrape — the API path is more robust and works even if your org blocks browser access to Calendar.

### Playwright — Browser Automation (optional)

Ad-hoc browser automation. No longer used by `/calendar` (the Google Calendar MCP replaced it), but useful for any other web interaction.

**Tip — Playwright is your universal fallback.** Prefer a dedicated MCP server or a CLI for a service. When neither exists, Playwright can drive the web app directly — log in, navigate, read a dashboard, submit a form — to reach data or actions Claude otherwise couldn't. So the order of preference is **MCP → CLI → Playwright**: if a skill needs a service you have no MCP or CLI for, reach for Playwright before giving up.

```bash
claude plugin install playwright@claude-plugins-official
```

**Use case:** Reach a web app that has no MCP server — log in, navigate, and pull data Claude couldn't otherwise access.

### Atlassian — Jira & Confluence

Used by `/execution-review` to sync initiative status with Jira.

```bash
claude plugin install atlassian@claude-plugins-official
```

**Use case:** During execution reviews, Claude pulls live Jira status for each initiative and flags mismatches between your tracker and Jira.

### Adding Your Own

Any MCP-compatible server works. Check the marketplace first (`claude plugin marketplace list`); for anything not there, add it directly:

```bash
claude mcp add <name> <command-or-url>
```

Common additions:
- **GitHub** — for PR reviews, issue tracking
- **Linear** — alternative to Jira

See the [Claude Code MCP docs](https://code.claude.com/docs/en/mcp) for the full list.

---

## Obsidian Plugins

These plugins enhance the system. Install them from Obsidian → Settings → Community Plugins.

| Plugin | What it does | Why you need it |
|--------|-------------|-----------------|
| **Dataview** | Query your vault like a database | List recent dailies, filter tasks, count initiatives by status |
| **Templater** | Dynamic templates with variables | Auto-fill dates, cursor placement in templates |
| **Periodic Notes** | Auto-create daily/weekly/monthly notes | One click to create today's note from the template |
| **Tasks** | Track tasks across files | Query open tasks, filter by person or date |

### Dataview Examples

**Recent daily check-ins:**
```dataview
LIST
FROM "reviews/daily"
WHERE file.cday >= date(today) - dur(7 days)
SORT file.cday DESC
```

**Open tasks across all files:**
```dataview
TASK
WHERE !completed
SORT file.cday DESC
LIMIT 20
```

---

## The Frameworks

The `frameworks/` directory contains mental models and structured thinking tools. They're reference material — read them when relevant, not all at once.

### Leadership & Management
| Framework | What it is |
|-----------|-----------|
| `engineering_leadership.md` | Core frameworks from Fournier and Grove on what an Engineering Director actually does |
| `engineering-leader-operating-model.md` | Weekly rhythm, meeting cadence, and how to structure your time |
| `engineering-leader-development.md` | Personal growth plan across 8 key leadership competencies |
| `developing_engineering_managers.md` | How to grow EMs using capability matrices, delegation ladders, and feedback patterns |
| `leadership_frameworks.md` | Supplementary models — sponsorship, autonomy delegation, influence |

### Decision-Making & Execution
| Framework | What it is |
|-----------|-----------|
| `decision_making.md` | When to move fast vs. slow — Type 1/Type 2 decisions, reversibility, speed/quality |
| `escalation-criteria.md` | When EMs should escalate and how fast |
| `high_performance_engineering.md` | What "good" looks like for engineering teams — maturity, execution culture, anti-patterns |
| `leverage_analysis.md` | Andy Grove's framework for finding where your time creates the most value |
| `jira_plan_system.md` | How to use Jira for leadership reporting and initiative tracking |
| `delivery-lifecycle-framework.md` | Phase-gate model for delivery — definition-of-done, RACI, and anti-patterns per phase |
| `delivery-lifecycle-playbook.md` | Companion playbook — role expectations, decision rights, and rituals for empowered teams |

### Team Health
| Framework | What it is |
|-----------|-----------|
| `team_health.md` | Lencioni's Five Dysfunctions + Lara Hogan's tools for diagnosing team health |

### Personal
| Framework | What it is |
|-----------|-----------|
| `annual_review.md` | Structured 3-4 hour annual reflection |
| `vivid_vision.md` | Present-tense description of your ideal future 3 years out |
| `life_map.md` | Six-dimension life review (Career, Health, Relationships, Finance, Growth, Fun) |
| `ideal_life_costing.md` | What your ideal life actually costs — work backward from a number |

---

## Making It Yours

This is a template, not a prescription. Adapt it to how you actually work.

### If you manage fewer teams
Remove team rows you don't need. Simplify the health tracker. The structure scales down easily.

### If you're not a Director
The frameworks and cadences work for any engineering leader — Senior EM, VP, Staff+. Adjust the scope (fewer teams, different meetings) but keep the review loops.

### If you use Linear instead of Jira
Swap the Jira MCP server for Linear. Update the execution-review skill to use Linear's API. The review process stays the same.

### If you want different cadences
Maybe daily is too much. Start with weekly reviews and 1:1 prep. Add daily check-ins when you're ready. The minimum viable system is: weekly review + memory.md + writing_style.md.

### If the frameworks don't fit your style
Delete the ones you don't use. Add your own. The `frameworks/` directory is a library, not a curriculum.

### What to customize first

1. **writing_style.md** — This makes the biggest difference. The more specific your writing samples and phrase patterns, the better Claude sounds like you.
2. **CLAUDE.md** — Add commands specific to your workflow. If you run a specific meeting or have a recurring task, teach Claude how to help.
3. **memory.md** — Start filling this in honestly. The more you put in, the more Claude can connect patterns and give relevant advice.

---

## Contributing

This repo is the shared template, not anyone's live vault. Your own copy (with your real people, goals, and reviews) stays private on your machine. What flows back here is the reusable machinery: skills, frameworks, review templates, and fixes that any engineering leader can use.

**What's worth contributing**
- New skills (`.claude/skills/<name>/`): a recurring workflow worth running again
- New frameworks (`frameworks/`): a mental model or playbook that isn't tied to one org
- Improvements to review templates, cadences, or the bootstrap flow
- Bug fixes, doc fixes, and new MCP integrations

**One hard rule: keep it generic.** Nothing personal or company-specific goes into what you contribute.
- No real names, teams, customers, or person files
- No company or product jargon, no internal codenames (use neutral terms)
- No confidential data (metrics, revenue, HR or performance)
- No hardcoded personal paths, tokens, IDs, channels, or timezones. Use placeholders like `[YOUR_NAME]`, `[YOUR_JIRA_CLOUD_ID]`, `[YOUR_TIMEZONE]`, and put anything user-specific in a skill's `config.json`.

**Skill checklist** (skills are the most common contribution)
- [ ] Matches the existing `SKILL.md` shape: usage, steps, gotchas (copy an existing skill as a model)
- [ ] User-specific settings live in `config.json`, not in the instructions
- [ ] Works without MCP where it can. If it needs one, add a `Requires:` note and a graceful fallback (the order is MCP, then CLI, then Playwright)
- [ ] You tried it against a fresh copy of the vault and it works
- [ ] Listed in the README skills table, and in `CLAUDE.md` if it's a common command
- [ ] No personal or company data (see the hard rule)

**How to submit**
1. Fork the repo and branch off `main`.
2. Keep the PR focused. One skill or framework per PR.
3. Open a PR against `main` and say what it adds and why.

Not sure if something fits? Open an issue and ask first. Contributions ship under the same MIT license as the rest of the repo.

---

## Credits

This system synthesizes ideas from:

- **[Rohun Jauhar](https://x.com/rohunjauhar)** — CEO Personal OS (the original framework this is built on)
- **[Matt Mochary](https://docs.google.com/document/d/18FiJbYn53fTtPmphfdCKT2TMWH-8Y2L-MLqDk-MFV4s)** — The Great CEO Within
- **[Andy Grove](https://www.amazon.com/High-Output-Management-Andrew-Grove/dp/0679762884)** — High Output Management (leverage, OKRs, one-on-ones)
- **[Camille Fournier](https://www.amazon.com/Managers-Path-Leaders-Navigating-Growth/dp/1491973897)** — The Manager's Path
- **[Will Larson](https://www.amazon.com/Elegant-Puzzle-Systems-Engineering-Management/dp/1732265186)** — An Elegant Puzzle, Staff Engineer
- **[Lara Hogan](https://larahogan.me/)** — Resilient Management
- **[Patrick Lencioni](https://www.amazon.com/Five-Dysfunctions-Team-Leadership-Fable/dp/0787960756)** — The Five Dysfunctions of a Team
- **[Tim Ferriss](https://tim.blog/2018/12/28/past-year-review/)** — Past Year Review, Fear Setting
- **[Tony Robbins](https://www.tonyrobbins.com/)** — RPM, identity work
- **[Cameron Herold](https://www.amazon.com/Vivid-Vision-Remarkable-Aligning-Business/dp/1619617722)** — Vivid Vision
- **[David Allen](https://gettingthingsdone.com/)** — Getting Things Done (inbox processing, capture)
- **[James Clear](https://jamesclear.com/)** — Atomic Habits (identity-based change, systems over goals)

---

## License

MIT. Use it, adapt it, share it.

---

*Built with Obsidian + Claude Code.*
