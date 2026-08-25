---
name: calendar
description: Show today's or this week's calendar as a clean agenda - conflicts, meeting hours, estimated focus time. Use when the user asks what's on their calendar or schedule, "what does my day look like", or about free/focus time. Display-only; pulls events via the Google Calendar MCP, or formats a pasted agenda without it. For the full morning briefing with tasks and flags, use daily-checkin instead.
argument-hint: "[today | week]"
allowed-tools: Read, mcp__claude_ai_Google_Calendar__list_events, mcp__claude_ai_Google_Calendar__get_event
---

# /calendar

User input: $ARGUMENTS

**Requires:** Google Calendar MCP (connected + authenticated). Check with `/mcp`. If it's not connected, this skill can't pull events — paste your agenda and Claude will format it instead.

## Usage
- `/calendar` or `/calendar today` → today's events
- `/calendar week` → the full current week

## Instructions

### Step 1: Pull events
Call `mcp__claude_ai_Google_Calendar__list_events` in your time zone (`[YOUR_TIMEZONE]`, e.g. "Europe/Lisbon"), with `eventTypeFilter: ["default"]` (drops focus time, working-location, OOO), `orderBy: "startTime"`, `pageSize: 50`. Window:
- today: startTime = today 00:00 → endTime = next day 00:00
- week: startTime = Monday 00:00 → endTime = following Monday 00:00 (current ISO week)
- Follow `nextPageToken` if present.

If the call fails (auth/token/not connected), say so plainly and ask the user to paste their agenda. Do **not** fall back to a browser scrape.

### Step 2: Parse
- Time range from start.dateTime / end.dateTime; event name from summary.
- RSVP: the attendee with `self: true` → responseStatus (accepted / declined / tentative / needsAction). Organizer with no attendee record = accepted.

### Step 3: Filter and flag
- SKIP lunch and focus blocks.
- Track declined events separately.
- Detect conflicts (overlapping time ranges).

### Step 4: Output — markdown table, one section per day

### Friday, February 20, 2026

| Time | Event | Status | Category |
|------|-------|--------|----------|
| 11:00–11:30 | Person / You | Accepted | 1:1 |
| 11:30–12:00 | Team Standup | Accepted | Team |

Conflicts: (list overlapping events, or "none")
Declined: (list declined events separately)

### Step 5: Summary line
- Total active events (excluding declined/focus/lunch)
- Meeting hours
- Estimated focus time (gaps between meetings, minimum 30-min blocks)

## Gotchas
- **Display only** — never creates a file.
- **Don't compute day-of-week** — trust the calendar data.
- If several calendars exist, default to the user's primary unless they name another.
