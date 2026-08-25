# /prep-1on1

Use when user wants to prepare for a 1:1, mentions an upcoming 1:1, says "prep for [name]", "meeting with [name]", or asks about open items for a direct report or skip-level.

---
allowed-tools: Read, Write, Glob, Grep, AskUserQuestion
arguments: $ARGUMENTS
---

## Instructions

When the user invokes `/prep-1on1 [Person Name]`, follow these steps:

### Step 1: Find the person file
Search for the person file in `people/` folder matching the name provided. The format is `@FirstName LastName.md`.

If no name is provided in $ARGUMENTS, ask the user which direct report they're meeting with.

### Step 2: Read person context
Read the person file to understand:
- Their role and team
- Development focus areas
- How they prefer feedback
- Current challenges or growth edges
- Recent notes from previous 1:1s

### Step 3: Find open action items
Use Grep to search across the vault for open action items mentioning this person:
- Search for `- [ ]` combined with their name
- Check `inbox.md` for any tasks related to them
- Check recent daily notes for mentions

### Step 4: Check recent wins
Search for wins tagged for this person:
- Look for `- [w]` or `[w]` patterns with their name
- Check their person file for recent accomplishments
- Review any feedback delivered `- [!]`

### Step 5: Check team health
Read `teams/health_tracker.md` to understand their team's current status.

### Step 6: Check recent meetings/decisions
Look in `meetings/` and `decisions/` folders for recent context relevant to this person or their team.

### Step 7: Generate prep document
Create a 1:1 prep document that includes:

**Quick Context:**
- Role, team, development focus
- How they prefer feedback

**Open Action Items:**
- From you to them
- From them to you

**Recent Wins to Acknowledge:**
- List specific accomplishments

**Topics to Discuss:**
- Career/Development items
- Feedback to deliver (if any)
- Projects/Work updates
- Team/Org context to share

**Suggested Questions:**
- Based on their current situation, suggest 2-3 specific questions

### Output
Display the prep document directly. Do NOT create a new file unless the user explicitly asks.

## Gotchas

- **Person file naming is @FirstName LastName.md** with a space. Some people have single-name files. Always use Glob to find the file, do not construct the path by guessing.
- **If the person file is not found,** ask the user: "I don't have a file for [name]. Want me to create one, or should I prep without historical context?"
- **Do not generate fake wins or feedback.** If there is nothing documented, say "No recent wins documented" rather than inventing something.
- **Check carries in the person file.** If action items have been carrying 3+ weeks, flag them prominently at the top of the prep. This is a common pattern worth surfacing.
- **For skip-levels:** the prep is different from direct report 1:1s. Focus more on "how is your manager doing" questions and team health signals rather than project updates.
