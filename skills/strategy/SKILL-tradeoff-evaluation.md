# SKILL: Trade-off Evaluation
> Skill type: Decision Framework
> Auto-activates when: user mentions "evaluate", "trade-off", "tradeoff", "compare options", "which should we do", "build vs", "go / no-go", "worth it", "should we prioritize"
> Force load: /evaluate

---

## What This Skill Does
Turns "several credible things compete for the same capacity" into a **defensible, recorded decision** — one that states what is being given up, what has to be true for the choice to pay off, and how it could be reversed.

It sits between Discover (we understand the problem) and Define (we're committing to a solution). Its output is a `templates/tradeoff-evaluation.md` document and, for anything significant, a `decision-log/` entry.

---

## Evaluation Philosophy

**Prioritization is resource allocation under uncertainty. The goal is not to optimize a framework — it's to make the bet you can explain.**

- A score is a **lens**, not an answer. RICE, ICE, Kano and Opportunity Scoring (see `skills/execution/SKILL-roadmap.md`) are inputs to judgment.
- Every "yes" is a hidden "no." A decision that doesn't name what it displaces isn't a decision.
- **Pick the criteria and weights *before* scoring.** Weights chosen after you see the scores are rationalization.
- Always include **"do nothing / defer"** and **"smallest test"** as options. If the real alternatives are all big builds, you haven't explored the space.
- If the evidence is mostly [Assumption], the answer is usually "run a cheaper test first," not "pick the highest score."

---

## When to Use This vs. Other Skills

| Situation | Use |
|-----------|-----|
| Small, reversible, no real competition for capacity | Skip — Fast-track from `/intake` |
| Don't understand the problem yet | `/discover` first |
| Two or more credible options compete for the same capacity | **`/evaluate`** |
| Deciding what goes on a quarterly roadmap | `/roadmap` (use `/evaluate` for the hard calls within it) |
| One large, hard-to-reverse commitment (one-way door) | **`/evaluate` full mode**, then `/review-strategy` for the multi-agent debate |
| Multi-stakeholder decision that needs clear roles | `/evaluate`, then `templates/daci-decision-doc.md` |

---

## Two Depths

**Quick (~15 min) — two-way door, low stakes.** Frame the decision → 2-3 options → one criteria table → trade-off statement → one-line bet. Log only if it changes direction.

**Full — one-way door, or large capacity commitment.** All steps below, plus the sensitivity check, the counter-argument, and (recommended) a `/review-strategy` debate.

---

## The Evaluation Process

### Step 1: Frame the decision
One sentence: **"We are deciding [what], by [when], owned by [who], given we can only [capacity constraint]."**
If you can't name the capacity constraint (people, weeks, budget, attention), there is nothing to trade off — it's a Fast-track.

### Step 2: Generate honest options (2-4)
Always include:
- **Do nothing / defer** — what actually happens if we don't act? (Often less bad than assumed; sometimes worse.)
- **Smallest test** — the cheapest way to learn whether the bet is right.
- At least one option the PM *doesn't* favor, written in its strongest form.

### Step 3: Choose criteria and weights (before scoring)
Pick 3-5 from strategy, not from convenience:

| Criterion | Grounded in | Question |
|-----------|-------------|----------|
| **User value** | `context-library/users.md` | Which persona, how much of their top pain does this remove? |
| **Strategic fit** | OKRs in `context-library/metrics.md`, anti-bets from `/strategy` | Does it move a North Star / OKR? |
| **Evidence strength** | Epistemic tags | How much of the case is [Fact] vs. [Assumption]? |
| **Cost & capacity** | `context-library/team.md` | Effort, and what it displaces |
| **Risk & reversibility** | `context-library/product.md`, compliance context | One-way or two-way door? What breaks if wrong? |

State weights up front (e.g., 30/25/20/15/10) and why.

### Step 4: Score, with the evidence visible
Score each option per criterion (1-5). Optionally compute RICE (features) or ICE (experiments) as a cross-check — see `skills/execution/SKILL-roadmap.md`.
Tag every input **[Fact] / [Inference] / [Assumption]**.

**Sensitivity check (full mode):** re-score with every [Assumption]-tagged input halved. If the ranking flips, the decision rests on an unvalidated bet — say so, and consider the "smallest test" option.

### Step 5: Write the trade-off statement
Not "Option A scored highest." Instead:

> **"Choosing [A] means we are NOT doing [B] and [C]. We give up [specific thing]. We accept [specific risk]."**

Include **cost of delay** for the options you're deferring: what does waiting a quarter actually cost?

### Step 6: State the bet
- **What has to be true for this to pay off:** [1-3 specific assumptions]
- **How we'll know early:** [leading indicator + threshold]
- **Kill / revisit criterion:** [what result makes us stop or change course, and when we check]
- **Reversibility:** one-way door / two-way door / costly-but-reversible

### Step 7: Steel-man the alternative
Write the strongest case for the option you rejected. If you can't, you haven't understood the trade-off. (Same bar as `templates/decision-template.md`.)

### Step 8: Sanity check the ranking
- Is anything at the top because of a squeaky stakeholder rather than evidence?
- Is anything at the bottom because we're avoiding it for emotional reasons?
- Would we choose the same if the requester were someone else?

### Step 9: Decide and record
- Recommendation + confidence (H/M/L) + what would change it.
- Log via `/log-decision` (significant decisions) — link the evaluation.
- **Rejected options:** if the same option keeps losing for the same reason, it's an anti-bet — propose it in `/strategy`.
- **Intake records:** update linked `intake/` entries with the outcome.

---

## Output Format
Use `templates/tradeoff-evaluation.md`. Minimum for Quick mode:

```markdown
## Evaluation: [decision in one line]
**Deciding:** [what / by when / owner / capacity constraint]
| Option | Value | Fit | Evidence | Cost | Risk | Weighted |
|--------|-------|-----|----------|------|------|----------|
**Trade-off:** Choosing [A] means NOT [B, C]. We give up [X].
**Bet:** true if [assumption]; know by [indicator]; revisit if [trigger].
**Reversibility:** [one-way / two-way]
**Recommendation:** [option] — confidence [H/M/L]
```

---

## Common Evaluation Failure Modes

❌ **Framework theater:** Precise-looking scores built on guessed inputs. Fix: tag the inputs; run the sensitivity check.

❌ **Weights after scores:** Picking criteria that make the favorite win. Fix: Step 3 comes before Step 4.

❌ **The false binary:** Two big builds and no cheap test. Fix: always include "smallest test" and "do nothing."

❌ **Unstated displacement:** "We'll do both." Fix: name the capacity constraint (Step 1) and what's displaced (Step 5).

❌ **Decision without a kill criterion:** No way to learn you were wrong. Fix: Step 6.

✅ **A good evaluation** lets someone who disagrees point to the exact assumption or weight they disagree with.

---

## Where This Sits
- **Upstream:** `/intake` (route: Evaluate), `/discover` (validated opportunities).
- **Downstream:** `/write-prd` (chosen option), `/roadmap` (sequencing), `decision-log/` (record), `/strategy` (recurring rejections → anti-bets).
- **Related:** `templates/roi-impact-estimation.md` (business case for the chosen option), `templates/daci-decision-doc.md` (roles), `sub-agents/debate-facilitator.md` and `sub-agents/synthesis-agent.md` (multi-agent trade-off debate).
