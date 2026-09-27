# Evaluation: [Decision in one line]
**Date:** [YYYY-MM-DD]
**Mode:** [Quick / Full]
**Owner:** [Who owns this decision]
**Decide by:** [YYYY-MM-DD]
**Status:** [draft / recommended / decided / superseded]
**Linked intake records:** [intake/requests/... or "none"]

---

## 1. The Decision

> We are deciding **[what]**, by **[when]**, owned by **[who]**, given we can only **[capacity constraint: people / weeks / budget / attention]**.

*If you can't name the capacity constraint, there's nothing to trade off — this is a Fast-track, not an evaluation.*

---

## 2. Options

| # | Option | What it is | Notes |
|---|--------|-----------|-------|
| A | [Option] | | |
| B | [Option] | | |
| C | **Smallest test** | [cheapest way to learn if the bet is right] | |
| D | **Do nothing / defer** | [what actually happens if we don't act] | |

*Include at least one option you don't favor, written in its strongest form.*

---

## 3. Criteria & Weights (set BEFORE scoring)

| Criterion | Weight | Grounded in | Why this weight |
|-----------|--------|-------------|-----------------|
| User value | [%] | `context-library/users.md` — [persona] | |
| Strategic fit | [%] | OKR: [which] / anti-bets: [which] | |
| Evidence strength | [%] | Epistemic tags below | |
| Cost & capacity | [%] | `context-library/team.md` | |
| Risk & reversibility | [%] | | |
| **Total** | 100% | | |

---

## 4. Scoring

Score 1-5 per criterion. Tag each score's basis: **[Fact] / [Inference] / [Assumption]**.

| Option | User value | Strategic fit | Evidence | Cost & capacity | Risk | **Weighted** |
|--------|-----------|---------------|----------|-----------------|------|--------------|
| A | | | | | | |
| B | | | | | | |
| C (test) | | | | | | |
| D (defer) | | | | | | |

**Optional cross-check (lens, not answer):** RICE for features / ICE for experiments — see `skills/execution/SKILL-roadmap.md`.

| Option | Score | Reach / Impact / Confidence / Effort |
|--------|-------|--------------------------------------|
| | | |

### Sensitivity check (Full mode)
Re-score with every **[Assumption]**-tagged input halved.
- **Does the ranking change?** [yes / no]
- **If yes, the decision rests on:** [the specific unvalidated assumption] → consider Option C (smallest test) first.

---

## 5. The Trade-off Statement

> **Choosing [A] means we are NOT doing [B] and [C]. We give up [specific thing]. We accept [specific risk].**

**Cost of delay for what we defer:**

| Deferred option | What waiting a quarter costs | Revisit when |
|-----------------|------------------------------|--------------|
| | | |

---

## 6. The Bet

- **What has to be true for this to pay off:**
  1. [Assumption]
  2. [Assumption]
- **How we'll know early:** [leading indicator + threshold]
- **Kill / revisit criterion:** [what result makes us stop or change course, and when we check]
- **Reversibility:** [one-way door / two-way door / costly-but-reversible]

---

## 7. Strongest Case for the Option We Rejected

*Steel-man it. If you can't, you haven't understood the trade-off.*

[FILL IN]

---

## 8. Sanity Check

- [ ] Nothing at the top is there because of a squeaky stakeholder rather than evidence
- [ ] Nothing at the bottom is there because we're avoiding it emotionally
- [ ] We'd choose the same if the requester were someone else
- [ ] Every persona / tier / competitor named exists in `context-library/` (closed-world check)
- [ ] Multi-agent debate run (`/review-strategy`) — required if one-way door: [ ] done / [ ] n/a

---

## 9. Recommendation

- **Recommended option:** [A / B / C / D]
- **Confidence:** [High / Medium / Low]
- **What would change this recommendation:** [specific evidence or event]

---

## 10. Follow-Through

| Action | Owner | Due |
|--------|-------|-----|
| Log decision via `/log-decision` → [link] | | |
| Update linked intake records with outcome | | |
| Next artifact: [`/write-prd` / `/roadmap` / experiment] | | |
| If a rejected option has now lost for the same reason more than once → propose as an **anti-bet** in `/strategy` | | |
