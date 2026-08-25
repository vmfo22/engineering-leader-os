# [Forum Name] Decision Forum

*This meeting decides and unblocks. Status is async.*

---

## Meeting Identity

**Cadence:** [e.g. bi-weekly]
**Duration:** 30 min, hard stop
**Channel:** `#[your-channel]`

**Purpose:** [What decisions does this forum exist to make? What does it unblock? What is explicitly NOT its scope?]

**Success metric:** Every session produces at least one decision or unblocks at least one item. If it doesn't, cancel the next one and figure out why.

---

## Who's in the Room

| Person | Role in Meeting |
|--------|----------------|
| **[Your Name]** (Facilitator) | Facilitator. Probes, doesn't present. Enforces timeboxes. Talk-time target: <25%. |
| **[Role 1 — e.g. Architect]** | [What they own in the meeting. What they're responsible for presenting or deciding.] |
| **[Role 2 — e.g. Design Lead]** | [What they own in the meeting. What they're responsible for presenting or deciding.] |
| **[Role 3 — e.g. PM / Translator]** | [What they own. E.g.: reframes when discussion stalls in jargon — "What does this mean for the user?" Owns product context for prioritization.] |
| **[Additional role — as needed]** | [When they attend and why.] |

---

## Agenda — 30 Minutes, Hard Stops

| Segment | Time | What Happens |
|---------|------|--------------|
| **Action items** | 3 min | Every open item: done or not done. No explanations for done items. Brief reason for not-done. Two-carry kill applies. |
| **Primary items** | 12 min | 1-2 items requiring a decision. Pre-read required. Discuss only unresolved questions from async comments — not the whole document. |
| **Cross-discipline alignment** | 10 min | Items where two disciplines are misaligned or blocked on each other. **Constraint-first:** each side states their non-negotiable in one sentence before discussion starts. |
| **Decisions & next actions** | 5 min | Capture every decision made. Every action gets: owner + due date. One designated note-taker captures live. |

**Max 3 agenda items total** across segments 2 and 3. If it's not in the top 3, it waits for next sync or goes async.

### Standing Questions (when relevant)

- What is the riskiest item in this domain right now?
- Where do you need more clarity from me or other stakeholders?
- Is anything blocked that only this group can unblock?

---

## Pre-Work Protocol

The meeting is only as good as the preparation. No pre-work = wasted 30 minutes.

| When | Who | What |
|------|-----|------|
| **Day after meeting** | Facilitator | Post action items in channel with owners + due dates. |
| **Day 7** (mid-cycle) | Facilitator | Slack ping: "These items are due before next sync. Status?" Tag owners. |
| **Monday before meeting** | Agenda contributors | Share one-pager, proposal, or design spec with **specific questions** to resolve. Post in channel or shared doc. |
| **Mon–Wed** | All attendees | Comment async on shared docs. Flag disagreements, ask clarifying questions. |
| **Meeting day, 1h before** | Facilitator | Post final agenda: "These are the unresolved questions from async review. This is what we're deciding today." |

**The rule:** If it wasn't shared by Monday, it doesn't make the agenda. No exceptions. No "agenda ambush."

---

## Action Item Tracking

### Active Items

| # | Action | Owner | Due | Opened | Age | Status |
|---|--------|-------|-----|--------|-----|--------|
| | | | | | | |

*Update this table during every session. Items closed move to the session notes.*

### Two-Carry Kill Rule

If an action item appears in **2 consecutive meetings** without progress, it triggers one of three forced outcomes:

1. **Escalate:** Gets a DRI + hard 48h deadline, with the facilitator directly involved.
2. **Reassign:** Current owner can't do it — who can?
3. **Drop:** "We're choosing not to do this." Explicit, documented, no shame.

No fourth option. No "let's keep monitoring." No "TBD" in the Due column.

**Aging thresholds:**
- 0-14 days: normal
- 15-28 days: flag in meeting — why is this still open?
- 29+ days: two-carry kill triggers automatically

---

## Between-Meetings Operating Rhythm

```
Week A: Meeting happens
  └─ Day 0 (meeting day): Action items posted in channel with owners + due dates
  └─ Day 7 (mid-cycle): Slack ping — "Status on these items?" Tag owners.
  └─ Day 9: If anything is blocked, DM the owner — don't wait for the meeting

Week B: No meeting
  └─ Monday: Agenda items shared (one-pager or pre-read doc)
  └─ Mon-Wed: Async comments on shared docs
  └─ Meeting day: 1h before, post final agenda of unresolved questions

Week A: Meeting happens again
  └─ ...repeat...
```

### Slack Notifications — What Gets Posted

| When | What | Where |
|------|------|-------|
| After every meeting | Action items with owners + due dates | Channel |
| Day 7 (mid-cycle) | "Status on [items]?" — tag owners | Channel |
| Monday before meeting | Agenda items + docs for pre-read | Channel |
| 1h before meeting | Final agenda — unresolved questions only | Channel |
| When a decision is made | Brief decision record | Channel + `decisions/` folder if cross-team |

### Automation — `/decision-forum` Skill

Most of the operating rhythm is automated via the `/decision-forum` Claude Code skill. Each mode drafts content that you copy-paste to Slack (no Slack MCP available).

| When | Run | What It Does |
|------|-----|--------------|
| Day of or day after meeting | `/decision-forum post-meeting` | Extracts action items from session notes. Updates Active Items table (ages, new items, completed items). Drafts Slack recap with decisions + action items. Flags two-carry items. |
| Day 7 (mid-cycle) | `/decision-forum midcycle` | Reads Active Items table, calculates ages, checks for at-risk/overdue items. Drafts Slack ping tagging owners. Reminds you which items need pre-reads for next meeting. |
| Monday before meeting | `/decision-forum prep` | Reads action items, daily notes, active initiatives. Builds prioritized agenda (max 3 items). Checks if pre-reads were shared. Drafts Slack agenda announcement. |
| 1h before meeting | `/decision-forum agenda` | Generates final meeting agenda from unresolved async questions. Flags items with no pre-read. Drafts 1h-before Slack post. |

**Workflow:**
1. Run the skill at the right moment in the cycle.
2. Review the draft output.
3. Copy-paste the Slack message to the channel.
4. Confirm any file updates (action item table).

### Slack Reminders — Set Up Once

Set these once using Slack's built-in `/remind`. Adjust days and times to match your meeting schedule.

```
/remind me "Run /decision-forum post-meeting — extract action items and post recap to channel" [every other WEEKDAY at TIME]

/remind me "Run /decision-forum midcycle — check action item status and ping owners" [every other WEEKDAY at TIME]

/remind me "Run /decision-forum prep — build agenda for upcoming sync" [every other Monday at TIME]

/remind me "Run /decision-forum agenda — post final agenda to channel" [every other WEEKDAY at MEETING_TIME - 1h]
```

*Note: Slack `/remind` doesn't natively support "every other week." Use a specific start date and a 14-day interval: `/remind me "..." on [date] at [time] every 2 weeks`.*

---

## Decision Records

For decisions that affect multiple teams or have 6+ month impact, capture in `decisions/` using this format:

```markdown
## [Decision Title]
**Date:** YYYY-MM-DD
**Forum:** [Forum Name]
**DRI:** [who decides]
**Decision:** [1-3 sentences]
**Context:** [why this came up]
**Alternatives considered:** [what else was on the table]
**Consequences:** [what changes as a result]
```

For smaller decisions, capture in the session notes — one line per decision is enough.

---

## Facilitation Rules

1. **Constraint-first for cross-discipline items.** Before discussing any solution, each discipline states their non-negotiable in one sentence. Now the discussion is bounded.

2. **Pre-read, not present.** If a doc needs review, it goes out Monday. In the meeting, open with: "You've all read the doc. Here are the 2 unresolved questions." If someone hasn't read it, they listen — we don't re-present for them.

3. **DRI decides, group advises.** The person who owns the decision makes the call. The meeting gives input. If there's no DRI, assign one before discussing.

4. **Hard cut at timebox.** When the 12-min block ends, it ends. Unresolved → owner schedules focused follow-up with the 1-2 people who matter.

5. **Parking lot has a home.** Items that can't be resolved get an immediate owner and a resolution venue (async doc, 1:1, or next meeting). A parking lot without a path is a graveyard.

---

## Anti-Patterns to Watch

| Anti-Pattern | What It Looks Like | What to Do |
|-------------|-------------------|------------|
| **Design by committee** | Discussion loops, no one decides | "Who's the DRI? DRI, what's your call?" |
| **Scope creep** | Too many topics, important items skipped | Max 3 items. If not top 3, it waits. |
| **Review instead of decide** | Presenting docs from scratch in the meeting | "Was this shared Monday? No? Next meeting." |
| **Absent DRI** | Decision made without the person who implements | Reschedule the item — don't decide without them. |
| **Vocabulary paralysis** | Disciplines talking past each other | Reframe in user/delivery terms: "What does this mean for the user?" |
| **Carry culture** | Same items appearing meeting after meeting | Two-carry kill. No exceptions. |
| **Agenda ambush** | New topic raised in "open floor" that needs 15 min | "Post it in the channel. It's on the agenda for next time." |

---

# Meeting Notes

---

## YYYY-MM-DD

**Attendees:** [list]
**Timebox:** 30 min hard stop.

### Action Item Review (3 min)

| # | Action | Owner | Due | Age | Done? |
|---|--------|-------|-----|-----|-------|
| | | | | | |

*Items hitting 2-carry: force decision — escalate, reassign, or drop.*

### Primary Items (12 min) — pre-read required

**Item 1:** [title]
- Pre-read: [link to doc]
- Unresolved questions from async review:
  1.
  2.
- **Decision:**
- **Action:**

### Cross-Discipline Alignment (10 min)

**Item:** [title]
- Constraint (side A):
- Constraint (side B):
- **Decision:**
- **Action:**

### Decisions & Next Actions (5 min)

| Decision | DRI |
|----------|-----|
| | |

| Action | Owner | Due |
|--------|-------|-----|
| | | |

### Notes

[session notes here]

---

*Created: YYYY-MM-DD*
