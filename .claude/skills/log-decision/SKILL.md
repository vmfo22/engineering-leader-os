# /log-decision

Use when user says they made a decision, wants to log/record/capture a decision, mentions "I decided", "we agreed", or wants to create an ADR. Also triggers on "should I document this decision."

---
allowed-tools: Read, Write, Edit, Glob, Grep, AskUserQuestion
arguments: $ARGUMENTS
---

## Instructions

When the user invokes `/log-decision`, follow these steps.

If $ARGUMENTS contains a brief description of the decision, use it as a starting point. Otherwise, ask.

### Step 1: Load context

Read these files in parallel:
- `decisions/decision_log.md` — existing log and format
- `goals/90_day.md` — current priorities (to check alignment)
- `memory.md` — decision patterns section (to cross-reference tendencies)

### Step 2: Gather the decision

Ask the user these 5 questions (adapt if $ARGUMENTS already answers some):

1. **What's the decision?** — One clear sentence.
2. **What options did you consider?** — At least 2 options, with brief pros/cons.
3. **Why this option?** — The reasoning, not just the choice.
4. **What are the risks or trade-offs?** — What could go wrong, what are you giving up.
5. **Reversibility** — Is this a Type 1 (one-way door, hard to reverse) or Type 2 (two-way door, easy to reverse)?

Also ask:
- **Category:** #strategy / #people / #technical / #process / #budget / #priority
- **Who was consulted?** (DACI Contributors)
- **Who needs to know?** (DACI Informed)
- **Follow-up review date?** (When should this decision be revisited?)

### Step 3: Cross-reference

Check against memory.md decision patterns:
- Does this decision type fall under "Decisions I Struggle With"? If yes, note it — not as a warning, but as awareness.
- Does the reasoning align with any known biases (conflict avoidance, analysis paralysis, holding on too long)?
- Connect to active initiatives if relevant — does this decision move an active initiative forward?

### Step 4: Write the decision log entry

Append a new entry to `decisions/decision_log.md` under "## Recent Decisions", using the existing format:

```markdown
### [DECISION TITLE]

**Date:** YYYY-MM-DD
**Category:** #category
**Type:** Type 1 (one-way door) / Type 2 (two-way door)

**Decision:**
[One sentence]

**Context:**
[What situation led to this]

**Options Considered:**

| Option | Pros | Cons |
|--------|------|------|
| Option A (chosen) | ... | ... |
| Option B | ... | ... |

**Rationale:**
[Why this option]

**Decider (DACI Approver):** [name]
**Key stakeholders consulted:** [names]
**Risks:** [brief]
**Follow-up review date:** YYYY-MM-DD
**Outcome (filled in later):**

---
```

Also update the "Decisions Pending Review" table if a follow-up date was set.

Also update the "Index by Category" section — add a link to the new entry under the right category.

### Step 5: ADR for significant decisions

If the decision is **Type 1** (one-way door) or affects multiple teams, offer to create a standalone ADR:

> "This looks like a significant decision. Want me to create a standalone ADR at `decisions/YYYY-MM-DD-[slug].md`?"

If yes, read `decisions/adr_template.md` and create the ADR with the information gathered, filling in as much as possible and leaving clear placeholders for what's missing.

If no, skip — the decision log entry is sufficient.

### Step 6: Confirm and summarize

After writing, confirm:
- Decision log entry added at `decisions/decision_log.md`
- ADR created at `decisions/YYYY-MM-DD-[slug].md` (if applicable)
- Follow-up review date: [date]
- Connection to initiatives: [if any]

If a decision pattern was flagged from memory.md, mention it:
> "Note: this falls in your 'decisions I struggle with' category (performance conversations). The fact that you're deciding now is good — check the outcome at the review date."

---

## Quick Mode

If the user provides enough context in $ARGUMENTS (e.g., `/log-decision promoted X to senior, chose over Y because Z`), skip the interactive questions. Extract what you can, ask only for what's missing (usually: options considered, risks, review date).

---

## General Rules

- **Don't over-engineer small decisions** — if it's clearly Type 2 and low-stakes, keep the entry short. Skip the options table if there were only 2 obvious choices.
- **Match existing log tone** — read the existing entries in decision_log.md and match the level of detail.
- **Always set a review date** — even for Type 2 decisions. Default: 30 days for Type 2, 90 days for Type 1.
- **Cross-reference, don't lecture** — flagging memory.md patterns is awareness, not judgment.
- **Connect to initiatives** — if the decision relates to an active initiative or 90-day goal, note the connection.

## Gotchas

- **Do not auto-categorize** (#strategy, #people, etc.) without user confirmation. Present your best guess and ask.
- **Type 1 vs Type 2 classification matters.** Type 1 (one-way door) triggers the ADR creation offer; Type 2 does not. Get this right by asking if unsure.
- **Cross-reference memory.md for bias patterns** (conflict avoidance, analysis paralysis, holding on too long). Flag gently as awareness, not as a lecture.
- **If the decision relates to a person,** check if there is a person file in `people/` and offer to add a note there too.
- **Read the last 2-3 entries in decision_log.md** before writing a new one, to match the current style — it may have evolved from the template format.
