# Decision-Making Frameworks

A collection of frameworks for making better decisions faster—and knowing when to slow down.

---

## Type 1 vs Type 2 Decisions (Bezos)

Jeff Bezos's most useful insight for decision-making:

### Type 1: One-Way Doors
- Hard or impossible to reverse
- Consequences are significant and lasting
- Getting it wrong is very costly

**Examples:**
- Major acquisitions
- Shutting down a product
- Large-scale layoffs
- Architectural decisions that are expensive to change
- Key executive hires

**Process:** Be deliberate. Gather data. Consult widely. Take time.

### Type 2: Two-Way Doors
- Easy to reverse or adjust
- Consequences are limited
- Getting it wrong is recoverable

**Examples:**
- Most feature decisions
- Process changes
- Hiring most roles
- Team structure experiments
- Tool choices

**Process:** Decide fast. Act. Learn. Adjust.

### The Mistake

Most organizations treat Type 2 decisions like Type 1:
- Too many approvals
- Too much analysis
- Too slow
- Risk aversion that costs more than the risk itself

**The fix:** Ask: "What type of door is this?" Then apply the appropriate process.

---

## The 70% Rule

> Make decisions when you have ~70% of the information you wish you had.

**Why 70%:**
- At 50%, you're guessing
- At 90%, you've wasted time and the window may have closed
- At 70%, you have enough to make a reasonable call

**The tradeoff:**
- Speed of decision vs. quality of decision
- For most decisions, speed wins
- You learn more by doing than by analyzing

**When to use:**
- Most business decisions
- Most technical decisions
- Most people decisions

**When NOT to use (wait for more):**
- Type 1 decisions
- Decisions with severe downside risk
- Irreversible commitments

---

## DACI Framework

For any significant decision, clarify roles:

| Role | Definition | Quantity |
|------|------------|----------|
| **D**river | Owns the process, gathers input, makes recommendation | One person |
| **A**pprover | Makes the final call, has veto | One person |
| **C**ontributors | Provide input, expertise, perspective | Few people |
| **I**nformed | Need to know the outcome, not involved in making it | Many people |

### Using DACI

**Before the decision:**
1. Identify who fills each role
2. Communicate roles clearly
3. Driver gathers input from Contributors
4. Driver makes a recommendation

**Making the decision:**
5. Driver presents recommendation to Approver
6. Approver decides (may accept, modify, or reject)
7. Decision is final once Approver decides

**After the decision:**
8. Inform the Informed
9. Driver ensures execution
10. Everyone commits

### Common DACI Mistakes

- **Too many Approvers:** Decisions stall. One person approves.
- **Missing Driver:** No one owns the process. Assign someone.
- **Contributors treated as Approvers:** Input ≠ veto. Be clear.
- **Driver doesn't recommend:** They just present options. That's not driving.
- **Revisiting decisions:** Once Approver decides, it's done.

---

## Disagree and Commit

After a decision is made:
- You can disagree with the decision
- You must commit to its success
- You don't undermine, hedge, or say "I told you so"

**Why this matters:**
- Consensus is often impossible and always slow
- Organizations need to move
- Half-hearted execution is worse than a slightly suboptimal decision
- We succeed or fail as a team

**How to practice:**
1. Voice disagreement before the decision
2. Once decided, fully commit
3. If it fails, learn—don't blame
4. If you can't commit, escalate before the decision

---

## The Regret Minimization Framework (Bezos)

For big life and career decisions:

> Project yourself to age 80. Looking back, which choice would you regret more?

**The process:**
1. Imagine yourself old, looking back
2. Ask: "Will I regret not trying this?"
3. Minimize regret, not risk

**When to use:**
- Career changes
- Starting/leaving companies
- Big personal decisions
- Decisions where the "safe" choice feels wrong

**Example:**
- "Will I regret not taking this opportunity?"
- "Will I regret staying in this role another 5 years?"
- "Will I regret not spending more time with family?"

---

## SQCA Communication

For executive communication, structure your message:

| Element | Question It Answers |
|---------|---------------------|
| **S**ituation | What's the context? What's the background? |
| **C**omplication | What's the problem? What changed? |
| **Q**uestion | What's the decision we need to make? |
| **A**nswer | What do you recommend? |

### Example

**Situation:** We launched the new checkout flow 4 weeks ago.

**Complication:** Conversion dropped 8%, costing ~$200K/month.

**Question:** Should we roll back immediately or try to fix the current flow?

**Answer:** Roll back now. The current flow has fundamental UX issues that will take 6+ weeks to fix. We can relaunch after proper user research.

### Why SQCA Works

- Respects executives' time
- Provides context without rambling
- Makes the question clear
- Leads with a recommendation
- Enables fast decisions

---

## Working Backwards (Amazon)

For new initiatives, start with the customer outcome and work backward:

### The Process

1. **Write the press release first**
   - What will you announce when it's done?
   - What's the customer benefit?
   - What's the headline?

2. **Write the FAQ**
   - What questions will customers ask?
   - What questions will stakeholders ask?
   - What are the hard questions you need to answer?

3. **Design backward from there**
   - What do we need to build to deliver that press release?
   - What must be true for the FAQ answers to work?

### Why This Works

- Forces clarity on customer value
- Exposes fuzzy thinking early
- Creates alignment before building
- Documents the "why" alongside the "what"

### Press Release Template

**Headline:** [One sentence: what is it?]

**Subhead:** [One sentence: why should customers care?]

**Opening:** [Problem it solves, customer benefit]

**Solution:** [How it works at a high level]

**Quote from leader:** [Why this matters to us]

**Quote from customer:** [Why this matters to them]

**How to get started:** [Call to action]

---

## Decision Log Template

For important decisions, document:

| Field | Content |
|-------|---------|
| Decision | What did we decide? |
| Date | When? |
| Decider | Who made the call? (DACI Approver) |
| Context | Why did this decision come up? |
| Options Considered | What were the alternatives? |
| Rationale | Why this option? |
| Risks | What could go wrong? |
| Review Date | When should we revisit? |

See `decisions/decision_log.md` for tracking.

---

## Pre-Mortem

Before starting, imagine the project failed. Ask:

1. It's 6 months from now. The project failed. Why?
2. What warning signs did we ignore?
3. What risks are we underestimating?
4. What did we fail to plan for?

**Why this works:**
- Permission to voice concerns
- Surfaces risks before they materialize
- Prevents overconfidence
- Creates contingency plans

---

## Second-Order Thinking

Don't just consider immediate effects. Ask:

1. **First order:** What happens immediately?
2. **Second order:** Then what happens?
3. **Third order:** And then what?

**Example:**
- First order: We mandate return to office
- Second order: Some employees quit
- Third order: We lose senior talent who can afford to leave, increasing hiring costs and knowledge loss

**The discipline:** Never stop at first-order effects. The real consequences are often downstream.

---

## When NOT to Decide

Sometimes the right choice is to wait:

- When you're emotional (decide tomorrow)
- When new information is imminent (wait for it)
- When the decision can be deferred without cost
- When the situation might resolve itself
- When deciding would lock you in unnecessarily

**The test:** Will delaying this decision cost us anything? If not, and more information is coming, wait.

---

*Credits: Jeff Bezos (Type 1/2, Regret Minimization, Working Backwards), Amazon leadership principles, Barbara Minto (Pyramid Principle/SQCA)*
