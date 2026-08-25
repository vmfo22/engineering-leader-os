# /prep-meeting

Use to prepare for a meeting — one you're **attending** or one you're **running**: staff, EM working sessions, reviews, decision forums, leadership/peer syncs, vision or vendor meetings. Digests any pre-reads (Google Docs/Slides, Confluence, Jira, PDFs, URLs, pasted text), pulls the **agenda + attendees** from the calendar invite, cross-references your known stance from the vault, and hands back a role- and type-aware briefing: what's on the table, your stance, where it'll get contested, your sharpest questions — and, if you're running it, the agenda, roster check, and a close plan. Display-only. **Not** for 1:1s (that's `/prep-1on1`) or post-meeting transcripts (that's `/process-meeting`).

---
allowed-tools: Read, Glob, Grep, AskUserQuestion, WebFetch, mcp__claude_ai_Google_Calendar__list_events, mcp__claude_ai_Google_Calendar__get_event, mcp__claude_ai_Google_Drive__search_files, mcp__claude_ai_Google_Drive__get_file_metadata, mcp__claude_ai_Google_Drive__read_file_content, mcp__claude_ai_Google_Drive__download_file_content, mcp__atlassian__getConfluencePage, mcp__atlassian__searchConfluenceUsingCql, mcp__atlassian__getJiraIssue
arguments: $ARGUMENTS
---

## What this is

A **subtractor**: it does the prep so you don't have to, and hands back a stance and a plan — never another document to file. You walk in two steps ahead, in two minutes instead of forty.

Governing principle: *every automation must remove work, not create another artifact to read.* So this skill is **display-only by default** — an ephemeral briefing in chat. It writes a file only if you explicitly ask.

It serves the **two roles you have with a meeting you don't handle elsewhere:**
- **Attend** — someone else owns it. The value is *where it'll get contested* and *your sharpest questions*, sharpened by your own known positions.
- **Run** — you own it. The value is a tight *desired outcome*, the *right room*, and a *close plan* (decisions, owners, dates) — because a meeting without a close was just a conversation.

(1:1s → `/prep-1on1`. Post-meeting capture → `/process-meeting`. The biweekly delivery review has its own skill → `/execution-review`; a recurring decision forum → `/decision-forum`. When the meeting is one of those, point there instead of duplicating it.)

---

## Instructions

When the user invokes `/prep-meeting`, follow these steps.

### Step 1: Intake — role, frame, type, material

Infer as much as possible; ask only what's genuinely unclear. Gather:

1. **Role — are you *attending* or *running* this?** Infer from the calendar organizer (Step 2) or the user's phrasing ("my staff meeting" / "I'm running…" = run; "I've been invited to…" = attend). If truly ambiguous, ask the one question.
2. **Frame (one line):** what's the meeting, when, and what are you trying to land, decide, or get out of it?
3. **Type** (infer; it drives the output — see the playbook): decision · review · generative/brainstorm · info/broadcast · vision/strategy · incident · vendor · peer/leadership sync · staff · EM working session.
4. **Material (optional):** links, pasted text, file paths. Docs are no longer required — plenty of prep-worthy meetings (a peer sync, a vision session) have none. If there are none, prep from the invite + the vault.

If you have neither a meeting name nor material, ask:
> "Name the meeting (I'll pull its invite) or paste any pre-reads — and one line on what you want out of it."

### Step 2: Pull the calendar invite (agenda + attendees + docs)

If a meeting is named, call `mcp__claude_ai_Google_Calendar__list_events` (time zone `[YOUR_TIMEZONE]`) for the window, find the event, then `get_event`. From the invite extract, best-effort:

- **Organizer** → confirms role (you organizing = *run*).
- **Agenda / desired outcome** from the description. **A missing or boilerplate agenda is a signal, not an error** — for *attend*, note "no agenda circulated"; for *run*, that's the gap this prep fills.
- **Attendee list** → who's in the room. This drives contest-mapping and roster checks (Step 4/6).
- **Attached doc links** → feed Step 3.

Degrade gracefully: if the invite is empty or the pull fails, say so and proceed from whatever else you have.

### Step 3: Fetch each pre-read source

Route each item by type; **never block on one failed source** — note it and move on.

- **Google Docs/Slides/Sheets/Drive:** extract the file ID (`/d/FILE_ID/`), `read_file_content` (use `download_file_content` for PDF/binary; `get_file_metadata` for title/owner only).
- **Confluence** (`*.atlassian.net/wiki/...`): `getConfluencePage` by page ID; pull comments to surface contested points cheaply. (Cloud ID, if needed, is in `execution-review/config.json` — reuse it.)
- **Jira** (`*.atlassian.net/browse/KEY-123`): `getJiraIssue`.
- **Public URL:** `WebFetch` for the argument, decisions, and any numbers/claims.
- **Local file** (PDF/`.md`): `Read`.
- **Pasted text:** use directly.

Graceful degradation: on a failed Google/Atlassian fetch, say plainly "couldn't open [doc] (likely not shared / token) — paste the text and I'll fold it in," and digest what you *could* reach.

### Step 4: Pull your stance + read the room (the differentiator)

- **Your stance:** `Glob`/`Grep` `initiatives/active/*/` for the topics in play; read the relevant `_initiative.md` / vision doc for your stated position. Read `principles.md` for the lens; check `memory.md` for relevant patterns. Scope it to what the meeting actually touches — don't read the whole vault.
- **The room:** for the invite's attendees (Step 2), glance at `people/@*.md` for the central ones — their known positions tell you *who* will push back and on what, and *who to pre-wire* before the room.
- **Recurring meeting?** If it's a standing meeting you run, `Glob meetings/*[keyword]*.md` for the last session and surface open carries / decisions to revisit (e.g. two-carry-kill items) so the prep continues the thread instead of restarting it.

### Step 5: Load the archetype playbook

Read `references/meeting-playbooks.md` and use the row for this meeting's **type + role**. It carries the per-archetype "what "prepared" means," the failure mode to avoid, and the frameworks (decision rights, door types, walk-the-board, the close discipline). Load it every run — it's the type-specific lens that keeps the output from being generic.

### Step 6: Build the briefing — role-aware, on the 5-line spine

Every briefing rests on the **pre-meeting card**: (1) what's actually on the table; (2) your stance in one line, *with a proposal attached, not just a problem*; (3) where it gets contested and by whom; (4) your 2–3 sharpest questions; (5) what you walk out with. Flex the sections by role:

**First, the fast filter (one line, only when it applies):** if you're attending and have no stance, no ask, and no unique information — *say so*: "you could decline this and read the notes" (Larson). If you're running it and it could be an async doc or a smaller room, name that.

**ATTEND — a scannable briefing (about a screen):**
- **Per doc:** one line — what it is + the decision/ask it drives.
- **TL;DR** (if there were docs) — 3–5 bullets, the packet in 30 seconds.
- **On the table** — what's being decided or asked, and of whom (including you).
- **Where it'll get contested** — the 2–3 points that'll get pushed on: the weak argument, the unstated assumption, where two docs disagree, the number that won't survive. *Highest-value section.* Name who's likely to push (from Step 4) and who to pre-wire.
- **Your angle** — given your known stance, where you likely land and where the pre-read supports or dents it. SCQA-tight.
- **Your sharpest questions** — 2–3 pointed, specific enough to require an answer. Not softballs.
- **Gaps / red flags** *(only if real)*.

**RUN — a facilitation plan:**
- **Purpose + desired outcome** — one sentence each. What must be true when people leave.
- **Agenda** — outcome-oriented items (not just topics), time-boxed. If the invite had none, this is draftable text to paste back.
- **Roster check** — right people present? For a decision, >8 in the room means it isn't a decision meeting (rule of eight) — name who could drop or move to "informed."
- **Pre-read plan** — what to circulate, or a silent-read block if it won't be read ahead.
- **Format + seed** — decision / working / review / generative, and the first question or pre-wire that gets it moving.
- **The 2–3 tensions to force** — the real disagreements to put on the table (from Step 4 + carries), so it isn't sanitized harmony.
- **Close plan** — how you'll capture decision / owner / date before anyone leaves. Hand off: "after it runs → `/process-meeting`."

### Step 7: Output — display only

Print the briefing in chat. **Do not create a file.** End with a light, opt-in offer (never auto-act):
> "Want me to draft the agenda/pre-read message, log a decision, or drop a follow-up in inbox off any of this? Or save this as a note?"

Act only on what the user explicitly picks.

---

## Gotchas

- **Display-only by default** — including the RUN branch. The agenda/close plan render in chat; write or send only if asked. (Governing principle.)
- **Docs are optional now.** Prep from the invite + vault when there are none. Don't refuse a doc-less meeting — that was the old limitation.
- **The invite agenda is best-effort.** Empty/boilerplate descriptions are common; a missing agenda is a *finding* (surface it), not a blocker.
- **This is not `/prep-1on1`, `/process-meeting`, `/execution-review`, or `/decision-forum`.** A 1:1 → `/prep-1on1`. A transcript after → `/process-meeting`. The biweekly delivery review and a standing decision forum have their own skills — point there rather than half-doing them here.
- **Never block on a failed fetch.** Note it, prep the rest, report what's missing.
- **Don't pad, don't invent.** Contested points and questions are the value; if there's no real friction, say "no obvious contested points" rather than manufacturing tension. A thin meeting gets a short briefing.
- **Sharp, not soft.** Cut any question that wouldn't move the room.
- **Respect confidential context.** Some vault material is Director-altitude; let it inform the read, but don't write questions that surface it into a room where it doesn't belong.
- **Don't compute day-of-week.** Trust calendar data or the user.
- **Keep the body lean.** Per-archetype depth lives in `references/meeting-playbooks.md`, loaded on demand — don't inline it here.
