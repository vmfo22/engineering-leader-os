# Meeting playbooks — reference for `/prep-meeting`

Loaded on demand by `prep-meeting` for the matched meeting **type + role**. Use the relevant row(s); don't dump the whole file into the briefing. Distilled from Grove (*High Output Management*), Larson (lethain.com), Lopp (Rands in Repose), Hogan, Fournier (*The Manager's Path*), Amazon's WBR / Bezos shareholder letters, Google SRE, Cagan (SVPG), Mochary, Rubick, Lencioni, plus the empirical literature (Rogelberg, CIPD 2023 evidence review, MIT Sloan).

> **Read the evidence honestly.** Most meeting "science" is directional, not definitive — few controlled studies, many vendor surveys with a stake in the "too many meetings" story. What's robust: *goal clarity* and *facilitation* are the real levers; agenda-*presence* and head-count are near-noise. So center every prep on the **desired outcome**, not on ritual (having an agenda, hitting a size). Quote magnitudes with suspicion; trust the mechanisms.

---

## The universal spine — the 5-line pre-meeting card

Every briefing, both roles, rests on these five:

1. **What's actually on the table?** — decision / information / trust / teaching. If none, the meeting may not need to exist (or need you).
2. **My stance in one SCQA line** — Situation, Complication, Question, Answer — *with a proposal attached, never a bare problem.*
3. **Where it gets contested, and by whom** — pre-wire the top contester 1:1 before the room if stakes justify it (nemawashi).
4. **My 2–3 sharpest questions** — specific enough to force an answer ("what problems are you seeing with X", not "any thoughts on X").
5. **What I walk out with** — a decision recorded, an owner+date, a changed mind (maybe mine), or a relationship advanced.

---

## The fast filter — should this meeting exist / should I be in it?

- **Async-first (Ringel/GitLab).** Default information-sharing, FYIs, and simple approvals to a doc, thread, or recorded video. Escalate to a live meeting only as the work turns *relationship-based* and *emotionally complex/interdependent*: incidents, live troubleshooting, creative ideation, first human connection, and — tellingly — "when people are talking past each other." If it's a status update, it isn't a meeting.
- **Cost is attendee-hours.** A 3-person half-hour is real money; a weekly exec meeting cascades into hundreds of prep-hours a year. Hold the cost in your head before you send the invite — visible cost changes behavior.
- **Grove's six questions** gate any *decision* meeting: What decision? By when? Who decides? Who's consulted? Who ratifies/vetoes? Who's informed? No answers → no meeting.
- **Larson:** large meetings are a *backup* channel — docs/dashboards are primary. And "don't assume attendance is valuable": no stance, no ask, no unique info → decline and read the notes. (Caveat mid-reorg: attendance is also signal — recalibrate *visibly*, don't quietly ghost.)
- **Fournier:** a meeting that doesn't need your presence is the urgent-not-important trap.
- **Rule of eight (Rubick/Bain).** >8 and it's no longer a decision meeting — split deciding from informing. (Size weakly predicts how people *feel* about a meeting but strongly affects *decision quality* — so size to purpose: tiny to decide, size-agnostic to broadcast.)

---

## PREPARED-TO-RUN (meetings you own)

| Type | Before | In the room | Walk out with | Failure mode to avoid |
|---|---|---|---|---|
| **Staff (your leads)** | Status pushed async; agenda from a running issues list; 1–2 written tensions queued | Lead/observe/question/decide — don't lecture; make peers debate each other | Decisions + owner/date; one first-team norm reinforced | Serialized status theater; sanitized harmony |
| **EM working session** | Pick a format — feedback roleplay / group coaching (questions only, then advice) / manager demos; case prepped; safety norms restated | Facilitate, don't chair; equal airtime | A skill *practiced*, not a status shared | Silently becomes a second staff meeting |
| **Execution / delivery review** | Tracker/Jira reconciled *first*; deck ordered inputs→outputs; variance annotated | Walk the board finish-first (blocked → almost-done → pull next); interrogate *variance only*; two-carry-kill on stalls | Stage/status deltas logged; 3–5 actions w/ owner+date | Status theater; blame session. *(Has its own skill → `/execution-review`.)* |
| **Ops / SLO review** | Know the budget burn + the signed error-budget policy | Enforce the pre-agreed consequence (freeze / shift effort); blameless on reds | Policy triggered or explicitly waived — on record | SLO becomes a vanity KPI nobody acts on |
| **Decision forum** | Grove's 6 Qs answered; written proposal with a *bold* recommendation; ≤8 people; door-type classified | ~5 min/proposal; RAPID if consensus stalls; disagree-and-commit to close | Decision logged w/ decider named; dissent recorded | Domineering / bottlenecked / status-oriented / inert. *(Standing one → `/decision-forum`.)* |
| **Your org's all-hands / Q&A** | Draft the 3 hardest questions *against yourself*; open anonymous pre-submission + voting | Short message, long Q&A; answer the hard ones straight | Trust; themes feed back into the staff agenda | Broadcast-only; dodged questions; blandness |

**Door types (Bezos) — the highest-leverage idea for an eng org.** One-way (irreversible: public API contracts, data-model migrations, org structure, security posture) → heavyweight, decide slowly. Two-way (reversible — *most technical decisions*) → **push down to the team and decide fast.** Applying one-way rigor to two-way doors is what makes an org slow and risk-averse. Decide at ~70% of the info you wish you had; being good at course-correcting makes being wrong cheap.

**Start on time.** The best-established finding in the literature: starting ~10 minutes late measurably lowers satisfaction, effectiveness, and idea quality (a 5-minute slip doesn't). Cheap discipline, real effect.

**The close (Grove):** decision / owner / deadline, said aloud in the last five minutes *and* written down, notes out in 24–48h. Treat the close-and-follow-through as *the* meeting — a structured debrief is the one intervention with a large measured effect (~20–25% performance lift). No meeting ends by scheduling another meeting.

---

## PREPARED-TO-ATTEND (meetings you don't own)

| Type | Before | In the room | Walk out with |
|---|---|---|---|
| **Peer / leadership sync** | Asks-of-peers + offers written; pre-wire the contested one 1:1 first | First-team posture — trade, don't broadcast | One dependency unblocked or escalated |
| **Strategy / vision** | Your written stance on the 2–3 *live* junctures; reread the current strategy | Extract perspective; SCQA when you speak; never fight feedback | Where exec priorities actually are |
| **Your manager's forums** | SCQA + proposal; problems surfaced never hidden; know your one ask | Engaged discussion > covering every topic | Perspective extracted; your risk register updated |
| **Sprint reviews** | Sprint goal + one strategic question per team | Be a *stakeholder*, not an inspector; react to outcomes | Roadmap adaptation signal; zero fear added |
| **Incident reviews** | Read the postmortem fully; systemic questions only | **Invert your stance to curiosity** — your visible reaction is the cultural artifact; reward candor publicly | Action items resourced; blameless culture reinforced |
| **Vendor / external** | Spec/criteria sheet written; buy-vs-build + exit options done; decision/owner/date known | Your spec referees the call; their agenda doesn't | Evaluation questions answered, or a clean walk-away |

---

## Frameworks quick-reference

- **Decision rights — DACI / RAPID:** name who Drives/Recommends, who's the single Approver/Decider, who's Consulted, who's Informed. Prevents decision-by-committee.
- **Disagree and commit (Bezos):** state your disagreement plainly, then commit sincerely to the decision. Ends deliberation honestly.
- **Amazon WBR discipline:** controllable *input* metrics first, their *output* metrics next; owners speak only to variance-against-expectation; swap an input metric out when it stops moving the output. "Argue with the dashboard, don't read it aloud."
- **Paired metrics (LeadDev):** never optimize one delivery metric without its counterweight; use metrics to find gaps across teams, not to rank them.
- **Pre-wire / nemawashi (Hogan, Larson):** build consensus 1:1 before the group meeting; seed the first question so nobody's surprised in the room.
- **Senior presence distorts the room:** speak last, state the *question* not your answer, let reports go first — write your own view down privately before the room does. Your title makes an early opinion contaminating (a single first "vote" measurably shifts the rest).
- **Premortem (Klein):** before committing to a plan, ask "assume this failed — why?" Prospective hindsight surfaces ~30% more failure modes; Kahneman's favorite debiasing move. Use it to prep your own proposal *and* to pressure-test a decision in the room.
- **Generative work: brainwrite, don't brainstorm.** Interacting groups produce roughly *half* the ideas of the same people generating independently (production-blocking — only one talks at once). Generate solo or silently in writing first, then convene to build and challenge. Dropping the "no criticism" rule *raises* output — debate is a feature.

---

## Source note

Primary practitioners: Andy Grove *High Output Management*; Will Larson (lethain.com — eng-org-meetings, present-to-executives, time-management, scaling-consistency); Michael Lopp / Rands ("How to Run a Meeting," "Agenda Detection"); Lara Hogan ("Better Meetings," "3 manager meetings"); Camille Fournier *The Manager's Path*; Amazon WBR (Commoncog) + Bezos 2016 shareholder letter (door types, disagree-and-commit); Google SRE (postmortem culture, error-budget policy); Marty Cagan / SVPG (design-by-committee, empowered teams); Matt Mochary *The Great CEO Within* (issues log, RAPID); Rubick (skip-levels, rule of eight); Lencioni *Death by Meeting* (cadence layers). **Two-carry-kill** is a house rule (the recurring `/decision-forum` skill applies it), with published analogues in Mochary's issues log and WIP-aging. No time-sensitive claims — safe to keep as a standing reference.
