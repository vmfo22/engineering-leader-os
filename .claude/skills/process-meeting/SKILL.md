---
name: process-meeting
description: Turn a meeting transcript into structured vault updates - action items, decisions, carries with week counts, person-file entries, inbox additions - confirming every write first. Use when the user pastes a transcript, says "process this meeting", mentions a Granola or Gemini transcript, or says "update [person]'s file" after a 1:1. Prep beforehand belongs to prep-meeting or prep-1on1.
allowed-tools: Read, Glob, Grep, AskUserQuestion
---

# /process-meeting

User input: $ARGUMENTS

## Instructions

When the user invokes `/process-meeting`, follow these steps.

If the user input above contains context (e.g., "1:1 with Alex"), use it. Otherwise, ask.

### Step 1: Get the transcript

If the user has already pasted text, use it. Otherwise, ask:
> "Paste the meeting transcript (from Granola, Gemini, or manual notes). I'll extract the key items."

### Step 2: Identify meeting context

Ask (skip any already answered via the user input above or inferrable from the transcript):
1. **Who was in the meeting?** (names — will match to `@Name.md` files in `people/`)
2. **What type?** (1:1 / group sync / staff / skip-level / external)
3. **Date?** (default to today if not specified)

### Step 3: Read relevant context

Read in parallel:
- `writing_style.md` — for any Slack drafts or summaries
- The person file(s) for attendees: Glob `people/@*.md` matching names from Step 2
- `inbox.md` — to check for existing related items
- `memory.md` — for known patterns about these people or meeting types

For 1:1s, pay attention to:
- Previous 1:1 entries in the person file (most recent 2-3)
- Open action items carrying from previous meetings
- Any enforcement/people items that were flagged but not yet addressed

### Step 4: Extract structured data

From the transcript, extract:

**Key Topics Discussed:**
- Summarize 3-5 main topics with 1-2 sentences each
- Use topic headings that match the person file's existing style

**Decisions Made:**
- Tag with #decision
- Note who made the decision and the reasoning if available

**Action Items:**
- Format as `- [ ] **Owner:** Description — due [date]`
- Separate into: (a) assigned to user, (b) assigned to others
- If no due date mentioned, flag it: "No deadline set — suggest one?"

**Carries / Deferred:**
- Items explicitly pushed to next meeting or "we'll come back to this"
- Note how many weeks carried if this is a recurring pattern (count from person file history)

**Granola/Source Link:**
- If a Granola or other transcript link is mentioned, capture it

### Step 5: Pattern detection

Check for known patterns:

- **Carries hitting 3+ weeks:** Search the person file for the same topic in previous entries. If found 3+ times without resolution, flag prominently:
  > "This item has been carrying N weeks. Escalate, delegate, or drop?"

- **Enforcement items displaced:** If this is a 1:1 and the transcript shows all technical/operational topics with no people/performance items, check the person file for open carries tagged as enforcement or people items. Flag:
  > "People items not covered again this week: [specific items from person file]. Consider opening with these next time or sending async."

- **Items without deadlines:** Flag any action item without a clear due date.

- **Async candidates:** Items that are status updates, FYIs, or simple approvals. Suggest:
  > "These items could go async instead of taking meeting time: [list]"

### Step 6: Route the output

**For 1:1s:**

1. Find the person file: Glob `people/@*.md` matching the person's name
2. If no file found, ask: "No file found for [name]. Create one, or add notes to `inbox.md` instead?"
3. Prepare a new dated entry matching the person file's existing format:

```markdown
### YYYY-MM-DD — [Brief Context Line]

**[Topic 1 heading]**
- Key points
- Key points

**[Topic 2 heading]**
- Key points

**Action Items:**
- [ ] **Owner:** description — due [date]
- [ ] **Owner:** description — due [date]

**Carries (not discussed):**

| Item | Weeks Carrying |
|------|---------------|
| [item] | **N weeks** |

**Granola:** [Link]
```

4. Show the proposed entry. Ask: "Add this to @Name.md?"

**For group meetings:**

1. Check if a meeting file already exists: Glob `meetings/*[keyword]*.md` using the meeting topic or attendee names
2. If found, propose appending a new dated session entry
3. If not found, propose creating `meetings/YYYY-MM-DD-[slug].md`
4. Show the proposed content. Ask: "Create/update this file?"

### Step 7: Update inbox

For any action items assigned to the user:
1. Read `inbox.md`
2. Prepare additions to the appropriate section (Quick Capture or Active)
3. Format: `- [ ] **[Due date]:** [Description] *(from [meeting type] with [person], [date])*`
4. Show proposed additions. Ask: "Add these to inbox.md?"

### Step 8: Summary

After all writes are confirmed, display:
- **Files updated:** [list with paths]
- **Action items created:** X total (Y assigned to you, Z assigned to others)
- **Decisions logged:** X
- **Patterns flagged:** [list]
- **Suggested async items:** [list, if any]

---

## Quick Mode

If the user provides enough context (e.g., `/process-meeting 1:1 with Alex` followed by pasted transcript), minimize questions. Extract what you can, ask only for genuinely ambiguous items. Show the proposed output and get confirmation before writing.

---

## Gotchas

- **Person file naming is @FirstName LastName.md.** Use Glob to find, do not guess paths. Some names are single-word (@Alex.md, @Sam.md).
- **Do not invent topics, decisions, or action items** not present in the transcript. If the transcript is sparse, say "Limited detail in transcript. Want to add anything?"
- **For 1:1s: check if the person file already has an entry for today's date.** If yes, warn before overwriting or suggest appending.
- **Carry-week counts must match person file history.** Count actual occurrences in previous entries, don't guess.
- **Granola links format:** `[Granola](https://notes.granola.ai/t/...)`. Preserve the full URL.
- **Slack messages referenced in transcripts are context, not action items.** Do not extract "mentioned in Slack" as an action item.
- **When flagging displaced enforcement items, be specific.** Name the items from the person file, don't say generically "you didn't cover people topics."
- **Match the existing entry format** in the person file. Read recent entries first. If the person has a distinctive notes style, follow it.
