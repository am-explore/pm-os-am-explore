# Skill Eval: Intake & Triage
> Worked example. Method: `skills/automation/SKILL-skill-evals.md`. Template: `templates/skill-evals.md`.
> The product, personas and numbers below are **made up** for illustration.

**Skill file under test:** `skills/discovery/SKILL-intake-triage.md`
**Created:** 2026-10-01
**Noise floor:** dev **4.7 pts**, holdout **13.5 pts** (two unchanged runs, 2026-10-01; holdout has only 2 scenarios, so it can only detect large changes). An edit must beat these.

---

## Shared stub context (used by every scenario)

> A fictional product, "Pebble Planner", a weekly planning app. **This list is the complete context** — the producer and the grader must both get exactly this, and nothing else. (The first baseline run went wrong because the grader was given a shorter list than the producer; see Baseline notes.)
>
> - `company.md`: a small bootstrapped company serving solo freelancers.
> - `team.md`: team size 4; no dedicated designer.
> - `users.md`: **Solo freelancers** (primary; plan their own week, no team). **Small-team leads** (secondary; teams under 10, plan their own week in the app). There is **no** "enterprise admin" persona.
> - `product.md`: features that exist: weekly view, task list, calendar sync (Google only), reminders. Features that do **not** exist: export, teams/collaboration, dark mode, SSO, Outlook sync.
> - `metrics.md`: current bet: raise week-2 retention from 25% to 35%. Anti-bet: "We do not build team collaboration features this year."
> - `competitors.md`: no named competitors recorded.
> - `intake/register.md`: one row — 2026-09-10 "Freelancers using Outlook cannot sync their calendar (only Google supported)", routed Evaluate.

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
| 2026-10-01 | `8bb024d` | baseline (2 unchanged passes) | **85.1%** (97/114; passes 87.5 / 82.8) | **84.4%** (54/64; passes 90.9 / 77.4) | n/a | Baseline recorded | Criteria C2, C3, C5 (n/a rule) and C6 need revising before this eval can judge an edit; see Baseline notes. |

---

## Baseline notes (2026-10-01)

**How it was run.** Scratch copy of the repo (no `.git` history) with the stub context above written into `context-library/` and `intake/register.md`. Each scenario ran 3 times per pass, 2 passes, 36 runs, each as a fresh read-only `claude -p` session on Sonnet (`/intake <input>`, plus one line saying it is read-only so it should show the register row instead of writing it). Each output was graded in a separate session on a different model (Opus) that saw only: the input, the stub context, the output, the criteria. Not the skill file, not the "Expect" lines.

**The first grading was invalid and was thrown out.** The grader had been given a shorter context than the producer (it was missing team size, "bootstrapped" and "teams under 10"), so it marked correct statements like "a team of 4 with no designer" as invented. C3 failed 28 of 36. After giving the grader the identical context, C3 failures dropped to 14. Lesson, now written into the stub section above: build the grader's context from the same files the producer read.

**Per criterion (both passes, n/a excluded).** C1 100% (36/36) · C2 86% (31/36) · C3 61% (22/36) · C4 5/5 · C5 100% (29/29) · C6 78% (28/36).

**Human spot-check (done by the assistant, not by the PM — please re-check a few).** 12 of 36 outputs read next to the grader's verdicts (72 of ~216 verdicts, one third):
- C1, C4 and the C6 pass/fails on non-D4 scenarios held up.
- **C2 is unreliable.** The same flaw got different verdicts: "Pebble Planner has no SSO" as the obstacle failed in one SSO run and passed in another; "trying to see teammates' weekly plans" as the job failed in one D2 run and passed in another. I would flip at least two verdicts. Both restate the requested solution as the problem.
- **C3 is unreliable.** Its scope is ambiguous (the Evidence bullets, or every sentence in the output?). Note the repo's own `.claude/rules/output-standards.md` says *every substantive claim* carries a tag, so untagged claims in the rationale are real rule violations, not only a grader quirk; the criterion needs to say which reading it enforces and then be applied consistently. Untagged claims in "Why this route" or "Strongest counter-argument" failed some runs and passed others. It also never checks that a tag is *correct*: one run tagged "[Fact] a 500-person company is far outside both segments", which is an inference, and passed.
- **C5's "n/a" rule flipped** between near-identical D4 runs.
- **C6 conflicts with the negative control.** For "The app feels off", the right reply is clarifying questions, but C6 demands the reply state the understood problem and the route, so every D4 run fails it.
- Overall disagreement is about 7%, under the one-in-five rule, but concentrated: roughly one in five of the C2 and C3 verdicts I checked.

**What the baseline says about the skill itself** (real signals, not grader noise):
- Strong: always one route (36/36), never missed a duplicate or anti-bet that applied, never treated "enterprise admin" as a real persona, every Park had a concrete trigger (5/5), Decline for the anti-bet request 6/6, Duplicate for the Outlook request 6/6.
- Weak, **solution smuggle**: the problem statement's obstacle or job often just restates the requested solution ("no SSO", "see teammates' weekly plans", "can't get it out"). This is the skill's own headline failure mode, and it still happens.
- Weak, **tags stop at the Evidence list**: the rationale and counter-argument make untagged claims about users and counts, because the Output Format only requires tags in Evidence.
- Gap: no guidance on what the requester reply should look like for an under-specified request.

**Before judging any edit, revise the criteria and re-baseline:** sharpen C2 ("the obstacle must not be 'lacks [the requested solution]'"), fix C3's scope and add a correct-tag check, give C5 a deterministic n/a rule, and give C6 an under-specified-request carve-out. Then candidate first edits to the skill: a Step 2 rule against restating the solution as the obstacle, and tags required in the Why-this-route field.
