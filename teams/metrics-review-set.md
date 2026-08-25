# Metrics Review Set — what I review, when, and why

**Owner:** [[Me]]
**Sources:** [your engineering-metrics tool] · [your work-tracking system] · reliability/incident data

The principle: **cycle time over throughput, flow over count, and never trust a number before checking its config.** Metrics open conversations; they don't close them. Keep the set small — if a metric doesn't change a conversation or a decision at its cadence, drop it.

---

## 1. Weekly — flow pulse (solo, 5–10 min)

*A "shopkeeper walk" over the data. Skim for exceptions, not analysis.*

| Metric | What I'm looking for |
|--------|---------------------|
| PR cycle time (median, per team) | The systemic lever. Any team drifting up two weeks running → 1:1 topic. |
| PR throughput per eng/week (per team) | Directional only. **Never** a target (it's the classic vanity metric). |
| Time to first review | The queue half of cycle time; your review-latency signal. |
| Started vs finished (WIP) | Teams starting more than they finish = the carry-rate engine. |
| Exception flag | One team, one anomaly, one question written down for the EM. |

**Output:** nothing formal — at most one line in the daily note and one question routed to a 1:1.

## 2. Bi-weekly — execution review

*This is the metrics half of your `/execution-review` ritual.*

- Cycle time + PR size trend vs your norms (e.g. median PR < ~200 lines, first review < a few hours).
- Stage movement and **carry rate** per initiative (2+ weeks stuck = flag).
- Reliability pulse (incidents, breaches, aging issues) — the counterweight to velocity.

## 3. Monthly — EM working session

*Four leading indicators per team, reviewed **with** the EMs, not at them. EMs bring their read; you bring cross-team patterns.*

| Indicator | Why it leads |
|-----------|--------------|
| Throughput (per eng/week, 3-month avg) | Capacity signal — only meaningful against its own history |
| Cycle time (median) | Flow health; finds the high-variance outliers |
| Started-vs-finished ratio | Focus / WIP discipline |
| Carry rate (items slipping) | Planning realism + hidden drag |

**Output:** team-health tracker refresh + at most one intervention per team, EM-owned.

## 4. Quarterly — leadership review

- Trend vs targets (cycle time, share of teams above your bar, predictability).
- A business-outcome sentence per major initiative ("if this ships, X, measured by Y").
- Did the thing you fixed last quarter actually move the metric?

---

## Data-hygiene rules (each one is usually a scar)

1. **Check the contributor/config before reading any per-team number.** A team "dropping to zero" is often an untracked-contributor artifact, not a real change.
2. **Discount vanity spikes.** A number that jumps because of how work was categorized, not what was delivered, isn't a win.
3. **Don't cross-compare trailing averages with point-in-time pulls.** Directional only.
4. **Small denominators are noise.** Below a few tracked contributors, grey the number out — don't rank it.
5. **Watch recategorization drift.** Reclassifying work (bug→task, etc.) changes the metric without changing reality. Fine when justified — but note it.
6. **Reconcile team taxonomy before reporting up.** Make sure the team names in your rollup match the ones leadership uses.
7. **Count going up while value stays flat = gaming.** Cycle time and PR size are the honesty checks on throughput.

---

## Keeping the Monday pulse cheap

- Your work-tracking system likely already feeds `/execution-review` — started-vs-finished and carry rate can ride that.
- If your metrics tool has an API, a saved query for the weekly flow pulse turns the 10-minute skim into a 2-minute one.

## Open questions (tracked, not blocking)

- Is PR throughput still an adequate productivity proxy as AI-assisted coding grows? (Outcomes-delivered is the live alternative.)
- Individual-level coding data belongs in EM coaching, **not** your leader cadence — keep it out to avoid a surveillance smell.
- Keep the indicator set tool-agnostic: the metrics above should survive a change of measurement platform.

---

*The set is deliberately small. Add a metric only when it will change a decision.*
