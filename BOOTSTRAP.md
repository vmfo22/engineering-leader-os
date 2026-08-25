# Bootstrap Your Engineering Leader OS

Two phases. Phase 1 gets the system running (~15 minutes). Phase 2 builds the deep foundation through guided interviews (~45-60 minutes). You can do Phase 2 the same day or spread it across a week.

---

## Phase 1: Get Running

Copy this prompt into Claude Code:

```
I just set up the Engineering Leader OS template. Walk me through the initial configuration.

Read CLAUDE.md and README.md first to understand the system, then guide me through these steps interactively — ask me questions, fill in the files based on my answers. Don't dump everything at once. One section at a time.

**Step 1 — Identity (CLAUDE.md)**
Ask me: my name, role, company, how many teams I manage, how many people, how many direct reports. Update CLAUDE.md with my answers.

**Step 2 — Writing Voice (writing_style.md)**
Ask me to paste 3-5 real messages I've written (Slack, email, documents — the more natural the better). Analyze them for patterns: sentence length, punctuation habits, how I open/close, words I overuse, level of formality. Update the writing style guide with what you find. Ask me to confirm.

**Step 3 — Current Goals (goals/90_day.md)**
Ask me: "What are your top 3 priorities this quarter? For each one, what does done look like?" Write them into the 90-day goals file.

**Step 4 — Your Teams (teams/health_tracker.md)**
Ask me to list my teams with: team name, EM name, rough team size, and a gut-feel health rating (Green/Yellow/Red). Fill in the health tracker. (The tracker also has per-dimension 1–5 scores — leave those for later; the overall gut-feel rating is enough to start.)

**Step 5 — Your People (people/direct_reports.md)**
For each direct report from step 4, ask me: their strengths, their growth edge, and one thing I should remember for our next 1:1. Fill in the direct reports file and create individual person files in people/.

**Step 6 — Upload Processing (optional)**
If I've dropped any files into uploads/, read them and extract relevant information into the right places (memory.md, people/ files, goals, etc.).

**Step 7 — First Check-in**
Run /daily-checkin to create my first daily note. The system is live.

After each step, confirm what you wrote and ask if I want to adjust anything before moving on.
```

At the end of Phase 1, you have a working system. Daily check-ins, weekly reviews, and 1:1 prep will all work. But the deep files — principles, north star, memory — are still empty. That's what Phase 2 is for.

---

## Phase 2: Go Deep (Interviews)

The `interviews/` folder contains 4 guided conversations. These aren't busywork — they're the foundation that makes the entire system personal. Each one feeds directly into your core files.

Run them in this order:

### Interview 1: Identity & Values
```
Read interviews/identity_and_values.md and walk me through it as a conversation. Ask one question at a time. Give me space to think. Don't rush.

When we're done, use my answers to:
- Update memory.md — Core Identity section (who I am, top values, who I'm becoming)
- Update principles.md — extract the principles that came through in my answers
```
*~15 minutes. Feeds: memory.md, principles.md*

### Interview 2: Leadership Philosophy
```
Read interviews/leadership_philosophy.md and walk me through it conversationally.

When we're done, use my answers to:
- Update principles.md — refine or add principles based on how I actually lead
- Update memory.md — Strengths, Growth Edges, and Patterns sections
```
*~15 minutes. Feeds: principles.md, memory.md*

### Interview 3: Future Self
```
Read interviews/future_self_interview.md and walk me through it.

When we're done, use my answers to:
- Update north_star.md — fill in the three questions and career direction
- Update goals/1_year.md and goals/3_year.md with anything concrete that emerged
```
*~15 minutes. Feeds: north_star.md, goals/*

### Interview 4: Past Year Reflection
```
Read interviews/past_year_reflection.md and walk me through it.

When we're done, use my answers to:
- Update memory.md — Accomplishments, Failures, and Patterns sections
- Flag anything that should become a 90-day goal or development focus
```
*~15 minutes. Feeds: memory.md, goals/90_day.md*

---

## Tips

- **Be honest.** The system gets more useful the more specific and truthful you are — especially memory.md and the interviews.
- **Don't overthink it.** First answers are usually right. You can refine everything later.
- **Paste real writing samples.** Pick messages that sound most like you — not your best writing, your most natural writing.
- **You can stop and resume.** Files save as you go. Come back and pick up where you left off.
- **Interviews are reusable.** Run Identity & Values annually. Run Past Year Reflection every December. They get richer over time.

---

## After Bootstrap

Once the system is configured:

- Run `/daily-checkin` every morning (5 min)
- Run `/weekly-review` every Friday (15 min)
- Update `memory.md` whenever you notice a new pattern
- Process `inbox.md` weekly
- Review frameworks in `frameworks/` when you face a specific challenge

The system compounds. Week 1 feels mechanical. By week 4, Claude knows your patterns, your voice, and your priorities. By quarter 2, it catches things you miss.
