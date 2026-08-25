# Decision Log

Record of significant decisions — not every decision, just the ones worth remembering. Useful for accountability, pattern recognition, and onboarding.

---

## How to Use This Log

1. **Log decisions when they're made** — not after. Context fades fast.
2. **Include alternatives** — what else you considered and why you didn't choose it.
3. **Review quarterly** — look for patterns in your decision-making.
4. **For complex decisions**, create a full ADR using `decisions/adr_template.md`.

### What to Log

- Org structure changes
- Hiring / performance decisions
- Technical direction choices
- Process or tool changes
- Anything you might need to explain later

### What NOT to Log

- Day-to-day tactical choices
- Decisions that are easily reversible
- Things everyone already agreed on

---

## Decision Categories

Use these tags for filtering:

- `#strategy` - Strategic direction decisions
- `#people` - Hiring, firing, promotions, org changes
- `#technical` - Architecture, tech stack, technical direction
- `#process` - Process and workflow changes
- `#budget` - Financial and resource decisions
- `#priority` - Prioritization and tradeoff decisions

---

## Recent Decisions

*Newest first. Copy the entry template below for each significant decision.*

### [DECISION TITLE]

**Date:** [DATE]
**Category:** #strategy / #people / #technical / #process / #budget / #priority
**Type:** Type 1 (one-way door) / Type 2 (two-way door)

**Decision:**


**Context:**
*What situation led to this decision?*


**Options Considered:**

| Option | Pros | Cons |
|--------|------|------|
| Option A (chosen) | | |
| Option B | | |
| Option C | | |

**Rationale:**
*Why this option?*


**Decider (DACI Approver):**

**Key stakeholders consulted:**

**Risks:**


**Follow-up review date:** [DATE]

**Outcome (filled in later):**


---

## Decisions Pending Review

*Decisions that need follow-up evaluation:*

| Decision | Original Date | Review Date | Status |
|----------|---------------|-------------|--------|
| | | | Due / Overdue / Reviewed |
| | | | Due / Overdue / Reviewed |

---

## Decision Patterns

*What patterns do you notice in your decisions? Revisit quarterly.*

### Types of Decisions You Make Well


### Types of Decisions You Struggle With


### Biases to Watch For


---

## Decisions Reversed or Regretted

*Worth tracking what didn't work:*

| Decision | Date | Why It Didn't Work | Lesson |
|----------|------|-------------------|--------|
| | | | |
| | | | |

---

## Quick Reference: Decision Framework

### Type 1 vs Type 2

**Type 1 (One-way door):** Hard to reverse. Be deliberate.
- Major reorgs
- Key hires/fires
- Large investments
- Irreversible technical decisions

**Type 2 (Two-way door):** Easy to reverse. Decide fast.
- Most process changes
- Most feature decisions
- Experiments
- Reversible technical choices

### DACI Reminder

| Role | Definition |
|------|------------|
| **D**river | Owns the process |
| **A**pprover | Makes final call |
| **C**ontributors | Provide input |
| **I**nformed | Need to know |

### The 70% Rule

Decide at 70% confidence. Course-correct as you learn.

### Pre-Mortem Question

Before deciding: "If this fails in 6 months, what will be the reason?"

---

## Index by Category

*Link decisions to their detail entries or ADRs as the log grows.*

### Strategy Decisions
- [Decision 1](link)

### People Decisions
- [Decision 1](link)

### Technical Decisions
- [Decision 1](link)

### Process Decisions
- [Decision 1](link)

---

*Last updated: [DATE]*
