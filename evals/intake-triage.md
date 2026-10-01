# Skill Eval: Intake & Triage
> Worked example. Method: `skills/automation/SKILL-skill-evals.md`. Template: `templates/skill-evals.md`.
> The product, personas and numbers below are **made up** for illustration.

**Skill file under test:** `skills/discovery/SKILL-intake-triage.md`
**Created:** 2026-10-01
**Noise floor:** not measured yet — run the unchanged skill twice and score both before trusting any comparison.

---

## Shared stub context (used by every scenario unless it says otherwise)

> A fictional product, "Pebble Planner", a weekly planning app.
> **Personas (`users.md`):** *Solo freelancers* (primary). *Small-team leads* (secondary). There is no "enterprise admin" persona.
> **Features (`product.md`):** weekly view, task list, calendar sync (Google only), reminders. There is no "export" feature and no "teams" feature.
> **Current bet (`metrics.md`):** raise week-2 retention from 25% to 35%.
> **Anti-bet:** "We do not build team collaboration features this year."
> **Register (`intake/register.md`):** contains one row — "Add Outlook calendar sync", routed Evaluate on 2026-09-10.

---

## Scenarios

### Dev scenarios

**D1 — Solution smuggle**
- Input: "Our biggest customer wants a dark mode toggle. Can we add it? They said it's urgent."
- Expect (for the grader's reference, not shown to the producer): the skill should restate the *problem*, not log "build dark mode"; the claim "biggest customer" and "urgent" need evidence tags.

**D2 — Anti-bet collision**
- Input: "Three people on Twitter asked for shared task lists so teammates can see each other's weeks."
- Expect: collides with the stated anti-bet; default route is Decline, with the reason recorded.

**D3 — Duplicate**
- Input: "A user emailed asking if we can sync with Outlook instead of just Google."
- Expect: recognized as already in the register; linked, requester added, no new work item.

**D4 — Negative control: too thin to route**
- Input: "The app feels off."
- Expect: the skill should not invent a persona, problem or route. It should say what is missing and ask, or record it as under-specified.

### Holdout scenarios

**H1 — Park needs a trigger**
- Input: "Could we add CSV export of the task list? Two freelancers asked last month."
- Expect: credible but not tied to the current bet; if routed Park, a revisit trigger is stated.

**H2 — Negative control: invented segment**
- Input: "An enterprise admin at a 500-person company wants SSO."
- Expect: "enterprise admin" does not exist in `users.md`; the skill must tag it [Assumption] and not treat it as a known segment.

---

## Criteria

| # | Question (yes/no) | Pass condition | Fail condition | Skill requirement it checks |
|---|-------------------|----------------|----------------|-----------------------------|
| C1 | Does the output end in exactly one named route? | One of Fast-track / Discover / Evaluate / Park / Decline / Duplicate is stated | No route, two routes, or an unlisted route ("revisit later") | "One front door and one outcome" |
| C2 | Is the problem stated as persona + job + obstacle + consequence, without the requested solution inside it? | All four slots present or the missing ones named; the solution (e.g. "dark mode toggle") is not the problem statement | Problem statement is the feature request restated, or missing slots are silently invented | Step 2 four-slot problem statement |
| C3 | Is every evidence claim tagged [Fact], [Inference] or [Assumption]? | Each claim about who/how many/how urgent carries a tag | Any untagged claim, or a persona not in the stub context treated as real without [Assumption] | Step 3 closed-world check, Operating Principle #6 |
| C4 | If the route is Park, is there a revisit trigger (a date or a condition)? | A concrete trigger is written | Park with no trigger, or a vague one ("later") | "A Park without a revisit trigger is a Decline in disguise" |
| C5 | Does it check the register and anti-bets before routing? | Mentions the existing register row or the anti-bet when relevant to the scenario | Ignores a duplicate or an anti-bet that the stub context contains | Steps 4-5 |
| C6 | Does it include a draft reply to the requester? | A 2-4 sentence reply stating understood problem, route and reason | Missing, or a vague "we'll look into it" | Step 7 |

*Not every criterion applies to every scenario (C4 only when the route is Park). The grader marks a criterion "n/a" only when its precondition is absent; n/a is excluded from the total.*

---

## Grader rules

- Grader sees only: scenario input (not the "Expect" lines), output, shared stub context, criteria.
- Grader is a **separate session** from the producer; a different model, or you.
- Each verdict: pass/fail + one-line reason quoted from the output.
- Spot-check at least one third of verdicts. More than one in five disagreements → fix the criteria first.
- Runs per scenario: 3.

---

## Results log

Newest first. One row per run. One change per row.

| Date | Skill file @ commit | Change under test | Dev score | Holdout score | Beat noise floor? | Decision | Notes |
|------|--------------------|-------------------|-----------|---------------|-------------------|----------|-------|
| — | — | baseline | not run | not run | n/a | — | Eval written 2026-10-01; no runs recorded yet. |
