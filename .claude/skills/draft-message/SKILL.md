---
name: draft-message
description: Draft or review written communication in the user's own voice from writing_style.md. Use when the user wants to write, draft, compose, or edit an email, Slack message, document, or self-assessment, or says "help me write", "how should I say this", or "review this draft". Recap and agenda posts for the configured decision forum belong to decision-forum.
allowed-tools: Read, AskUserQuestion
---

# /draft-message

User input: $ARGUMENTS

## Instructions

When the user invokes `/draft-message`, follow these steps:

### Step 1: Read writing style (CRITICAL)
ALWAYS read `writing_style.md` first. This is non-negotiable. The goal is to produce writing indistinguishable from what the user would write themselves.

### Step 2: Gather context
If the user input above contains enough information, proceed. Otherwise, ask the user:
- **Who is the audience?** (team, executives, peers, external partners)
- **What is the channel?** (email, Slack, document)
- **What is the topic/purpose?**
- **Any specific points to include?**

### Step 3: Determine style based on context

**For Email to Team:**
- Match the user's team-email style from writing_style.md — tone, length, opener, and sign-off as documented there. Don't assume a tone; read it.

**For Email to Executives:**
- Match the user's executive email style from writing_style.md
- A common structure (use if it fits their style): strong opener → bullet summary → detailed findings → root cause → proposed strategy → clear ask

**For Slack (team channels):**
- Match the user's Slack style from writing_style.md
- Get to point quickly
- Use the user's typical openers and closers
- Sign-off per the user's Slack habit in writing_style.md (many people use none)

**For Slack (pushback/clarification):**
- Ask questions instead of making statements
- Match the pushback patterns from writing_style.md

**For Documents/Self-Assessments:**
- First person, active voice
- Honest about mistakes
- Balance achievements with self-criticism

### Step 4: Apply voice rules

Use the user's actual phrases from writing_style.md. NEVER use words from the avoid list.

### Step 5: Draft the message
Write the draft matching the user's voice exactly. Keep it shorter than you think it needs to be — they can always expand.

### Step 6: Quality check
Before presenting, verify:
- [ ] No words from the avoid list
- [ ] Tone matches the audience
- [ ] Uses the user's actual phrases
- [ ] Has direct questions where appropriate
- [ ] Opener and closer match the channel

### Output
Present the draft with a brief note on which style was applied. Ask if adjustments are needed.

## Gotchas

- **MUST read writing_style.md first,** even if you think you remember it. Voice drift happens across conversations. This is non-negotiable.
- **Never use words from the avoid list, even casually.** The avoid list in writing_style.md exists for a reason — those words are AI tells.
- **Follow the user's sign-off habits from writing_style.md.** Many people use no sign-off in Slack — but do what the user actually does; don't impose a rule that isn't theirs.
- **Em-dashes are a personal call.** Some writers avoid them as an AI tell; others use them naturally. Follow the user's writing_style.md — don't strip em-dashes unless their own samples avoid them.
- **"Review this draft" means match the user's existing voice.** Do not rewrite it in your style. Suggest targeted edits that preserve the author's voice.
- **Executive emails: always include data points,** specific names, and percentages. Generic claims without specifics are a red flag.
