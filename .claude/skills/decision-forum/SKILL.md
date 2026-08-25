# /decision-forum

Use when the user mentions your recurring cross-functional decision forum (architecture review, design review, cross-team sync, etc.), references attendees by their configured roles, or says "post-meeting", "midcycle", "prep", or "agenda" in the context of the forum.

---
allowed-tools: Read, Write, Edit, Glob, Grep, AskUserQuestion
arguments: $ARGUMENTS
---

## Instructions

When the user invokes `/decision-forum`, determine the mode from $ARGUMENTS:

- **`post-meeting`** or **`post`** → Post-Meeting Wrap (run day of or day after meeting)
- **`midcycle`** or **`check`** → Mid-Cycle Check (run day 7, between meetings)
- **`prep`** → Meeting Prep (run Monday before meeting)
- **`agenda`** → Final Agenda (run 1h before meeting)
- **No arguments** → Show available modes and when to use each

Read `config.json` in this skill's directory at the start of every mode. Every tunable lives there — `forum_name`, `meeting_cadence_days` (drives due dates and the age thresholds), `meeting_file_path`, `slack_channel`, `max_agenda_items` (the agenda cap), `carry_threshold` (how many consecutive meetings before an item is forced to a decision), and `attendees`. Never hardcode any of these numbers in your output.

---

## Mode 0: No Arguments — Show Help

Display:

```
/decision-forum — [Forum Name] automation

Modes:
  /decision-forum post-meeting  — After the meeting: extract action items, update tracker, draft Slack post
  /decision-forum midcycle      — Day 7: check action item status, draft Slack ping for owners
  /decision-forum prep          — Monday before meeting: draft agenda from open items + pre-reads
  /decision-forum agenda        — 1h before meeting: generate final agenda of unresolved questions

Operating rhythm:
  Day 0:  Meeting happens → run /decision-forum post-meeting
  Day 7:  Mid-cycle       → run /decision-forum midcycle
  Day 10: Monday prep     → run /decision-forum prep
  Day 14: Meeting day     → run /decision-forum agenda 1h before
```

---

## Mode 1: Post-Meeting Wrap

Run this the day of or day after the forum meeting.

### Step 1: Find the latest session notes

Read the meeting file specified in `config.json` (`meeting_file_path`). Find the most recent session entry (latest date under `# Meeting Notes`). If today's date has no entry yet, ask the user: "I don't see notes for today's session. Want to paste the key points, or should I work from the template?"

### Step 2: Extract action items

From the latest session notes, extract:
- **Action items** — anything with `- [ ]` or discussed as a next step
- **Decisions made** — anything tagged with `**Decisions:**` or stated as agreed
- **Items carried forward** — anything explicitly noted as carry or not discussed

For each action item, determine:
- **Owner:** Who's responsible (from the notes or ask the user)
- **Due date:** From the notes, or default to "before next sync" (`meeting_cadence_days` from config.json)
- **Age:** If this item existed before, calculate days since first opened. If new, age = 0.

### Step 3: Update the Active Items table

Read the `## Open Action Items` / `### Active Items` table in the meeting file.

- Mark completed items as done and move to the session notes
- Add new items with owner, due date, opened date, age = 0d
- Update ages on existing items
- **Flag any item hitting the carry threshold** (`carry_threshold` from config.json — appeared in that many consecutive meetings without progress)

Present the updated table to the user for confirmation before writing.

### Step 4: Draft Slack message

Read `writing_style.md` — match Slack voice (lowercase opener, direct, no sign-off).

Draft a Slack message for the configured channel (`slack_channel` from config):

```
[forum name] — [date] recap

decisions:
• [decision 1]
• [decision 2]

action items:
• [item] — @owner, due [date]
• [item] — @owner, due [date]

[if any items hit the carry threshold:]
heads up — these items have been open 2+ syncs:
• [item] — @owner, [age] days. needs resolution by [date] or we drop/escalate.

next sync: [date]
```

Display the draft. Tell the user: "Copy this to Slack — I won't post it for you."

### Step 5: Update the meeting doc

After user confirms, write the updated Active Items table to the meeting doc.

---

## Mode 2: Mid-Cycle Check

Run this ~7 days after the meeting (between syncs).

### Step 1: Load action items

Read the meeting file from config. Find the Active Items table. Calculate current age for each item.

### Step 2: Assess status

For each open item:
- **On track:** Due date hasn't passed, age under one `meeting_cadence_days` cycle
- **At risk:** Due date within 3 days, or age between one and two `meeting_cadence_days` cycles
- **Overdue:** Past due date
- **Escalation trigger:** Item appeared in `carry_threshold`+ consecutive meetings without progress (age beyond two `meeting_cadence_days` cycles)

### Step 3: Draft Slack ping

Read `writing_style.md` for Slack voice.

Draft a mid-cycle Slack message:

```
mid-cycle check — [forum name] items due before [next meeting date]

@owner1 — [item]. status?
@owner2 — [item]. status?

[if any at risk or overdue:]
⚠️ overdue:
• [item] — @owner, was due [date]. what's blocking this?
```

Display the draft. Tell the user to copy to Slack.

### Step 4: Check for pre-reads

Look at the Active Items for any items that should produce a pre-read document (design specs, architecture decisions, proposals). Remind the user:

"These items should have pre-reads shared by Monday for the next meeting:
- [item] — has @owner shared the doc yet?
- [item] — pre-read doc needed before next sync"

---

## Mode 3: Meeting Prep

Run this Monday before the meeting (Day 10-11 of the cycle).

### Step 1: Load context

Read in parallel:
- The meeting file (from config) — Active Items table + last 2 session notes
- Glob `initiatives/active/*/` — scan for initiatives relevant to this forum's domain, checking for items that need architectural or design decisions
- Recent daily notes from past 7 days (Glob `reviews/daily/YYYY-MM-*.md`) — search for mentions of attendees (use names from config `attendees` list) and topics relevant to this forum
- `writing_style.md` — for Slack voice on the agenda post

### Step 2: Build agenda candidates

From the action items and context, identify:

1. **Action items to review** — list all open items with current age
2. **Domain items** — any pre-read docs or decisions that need discussion. Check: was a pre-read shared? If not, flag it.
3. **Cross-discipline alignment items** — any misalignments or blocks surfaced in daily notes or active initiatives
4. **Carried items** — anything hitting the carry threshold

### Step 3: Prioritize to the agenda cap

If there are more than `max_agenda_items` (from config.json) across segments 2 and 3, ask the user:

"I have [N] potential agenda items. The meeting only fits [max_agenda_items]. Here they are ranked by urgency:
1. [item] — [why urgent]
2. [item] — [why urgent]
3. [item] — [why urgent]
---
Below the cut:
4. [item] — could go async
5. [item] — can wait

Which 3 should we take?"

### Step 4: Draft the prep agenda

Generate a structured agenda following the meeting template:

```markdown
## [YYYY-MM-DD] — Prep Agenda

### Action Item Review (3 min)

| # | Action | Owner | Due | Age | Done? |
|---|--------|-------|-----|-----|-------|
| 1 | [item] | [owner] | [date] | [Xd] | ? |

*Carried items at threshold: [list any, or "none"]*

### Primary Items (12 min)

**Item: [title]**
- Pre-read: [link or "NOT SHARED — flag to @owner"]
- Unresolved questions:
  1. [from async comments, or "pending — no pre-read yet"]
- Decision needed: [what we need to decide]

### Cross-Discipline Alignment (10 min)

**Item: [title]**
- Constraint (side A): [if known]
- Constraint (side B): [if known]
- Decision needed: [what we need to resolve]

### Walk Away With
1. [specific outcome needed]
2. [specific outcome needed]
3. [specific outcome needed]
```

### Step 5: Draft Slack announcement

Draft the Monday agenda share for the channel:

```
[forum name] — [date] agenda

pre-reads due by Wednesday:
• [item] — @owner (share design spec / proposal doc)

agenda:
1. action items (3 min)
2. [primary item] (12 min)
3. [alignment item] (10 min)

if you have input on these items, comment on the docs before the meeting. we'll only discuss unresolved questions in the sync.
```

Display both the prep agenda and the Slack draft.

---

## Mode 4: Final Agenda

Run this 1h before the meeting.

### Step 1: Load latest state

Read the meeting file (from config) — Active Items table.
Check if a prep agenda was generated earlier this week (search for today's date or the meeting date in the session notes).

### Step 2: Check pre-read status

For each agenda item that needed a pre-read:
- Was the doc shared? (Ask user if unclear)
- Were there async comments with unresolved questions?

Items with no pre-read: "This item had no pre-read. Options: (a) discuss cold — limited to 5 min, (b) push to next meeting."

### Step 3: Generate final agenda

Build the meeting-ready agenda:

```markdown
## [YYYY-MM-DD] — Final Agenda (share in channel now)

### Action Items (3 min)
[table with current status]

### DISCUSS: [item 1] (12 min)
Unresolved questions:
1. [specific question from async comments]
2. [specific question]
Decision needed: [what we're deciding]

### DISCUSS: [item 2] (10 min)
[same format]

### Decisions & Actions (5 min)
[capture live]
```

### Step 4: Draft Slack post (1h before)

```
[forum name] starts in 1h

what we're deciding today:
1. [question 1 about item 1]
2. [question 2 about item 2]

pre-reads: [links]

if you haven't read the docs, please scan them before we start. we'll open with 3 min of silent reading.
```

Display the final agenda and Slack draft.

---

## General Rules

- **Always read `writing_style.md`** before drafting any Slack message
- **Slack voice:** lowercase opener, direct, parenthetical asides, no sign-off, end with question or statement
- **Never post to Slack directly** — always display the draft and tell the user to copy it. This is policy, not a capability limit: it holds even when a Slack MCP is connected.
- **Action item ages are calculated from the "Opened" date** in the Active Items table, not from when they were last discussed
- **Carry kill:** if an item has been in `carry_threshold`+ consecutive meeting action item reviews without progress, flag it prominently and force a decision: escalate, reassign, or drop
- **Cap the agenda at `max_agenda_items`** (config.json) for the primary items + alignment segments combined. Enforce this.
- **Pre-reads are non-negotiable.** If no pre-read was shared, the item either gets 5 min cold discussion or gets pushed. Don't let the meeting become a review session.
- After any write operation, confirm with the user before saving
- **Read config.json at the start of every mode** — all instance data (forum name, file path, channel, attendees) lives there

## Adaptability

Adapt based on what you find. If the mid-cycle check shows all items on track, shorten the output. If a post-meeting wrap surfaces a critical escalation, flag it immediately rather than waiting for the Slack draft step. If the meeting was cancelled or rescheduled, adjust the operating rhythm dates accordingly.

## Gotchas

- **Never post directly to Slack — by policy, not capability.** Even if a Slack MCP is connected, display the draft and let the user send it. A forum post carries names and stale action items; the user decides when it goes out.
- **The carry-kill rule flags items, but the USER makes the final call** on whether to drop, escalate, or reassign. Do not auto-drop.
- **Meeting dates must be validated** against the actual calendar or config, not assumed from "every 2 weeks." Holidays, PTO, and rescheduling happen.
- **Meeting file path, cadence, and attendees are in config.json.** Read from there — never hardcode.
- **Pre-read enforcement:** if no pre-read was shared, the item gets 5 min cold discussion max or gets pushed. Don't let the user silently waive this.
- **Slack voice:** lowercase opener, direct, no sign-off, parenthetical asides. Read `writing_style.md` even if you think you remember it.
- **Attendee names for searching daily notes** come from the `attendees` list in config.json — don't invent or assume names.
