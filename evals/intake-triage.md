# Skill Eval: Intake & Triage
> Worked example. Method: `skills/automation/SKILL-skill-evals.md`. Template: `templates/skill-evals.md`.
> The product, personas and numbers below are **made up** for illustration.

**Skill file under test:** `skills/discovery/SKILL-intake-triage.md`
**Created:** 2026-10-01
**Noise floor (criteria v2):** dev **5.6 pts**, holdout **9.6 pts** (two unchanged passes, 2026-10-01; grader agrees with itself on 96.3% of verdicts). An edit must beat these. Holdout has only 2 scenarios.

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

## Criteria (v2, revised 2026-10-01 after the first baseline's spot-check)

| # | Question (yes/no) | Pass condition | Fail condition | Skill requirement it checks |
|---|-------------------|----------------|----------------|-----------------------------|
| C1 | Does the output end in exactly one named route? | One of Fast-track / Discover / Evaluate / Park / Decline / Duplicate is stated as the route | No route, two routes, or an unlisted route (e.g. "revisit later") | "One front door and one outcome" |
| C2 | Is the problem statement free of the requested solution? | The job and obstacle describe what the person is trying to get done and what stops them **without** naming the requested feature as missing and without a synonym for it. Slots that are unknown are named unknown. | The obstacle is the absence of the requested feature ("has no X", "lacks X", "can't X" where X is what was asked for, or a paraphrase of it), or the job is "use the requested feature". *Test: delete the requested feature's name and its paraphrases from the sentence — is a real problem still left?* | Step 2 four-slot problem statement; "A request is a symptom with a solution attached. Detach them." |
| C3 | Are all claims about users, counts, demand, urgency or effects tagged, and tagged correctly? | Every such sentence **anywhere in the output** (including the rationale and any counter-argument) that is not stated in the stub context or the request wording carries [Fact], [Inference] or [Assumption]; and each [Fact] is directly supported by the stub context or the request. Restating stub context, reasoning, and recommendations need no tag. | Any untagged claim of that kind anywhere in the output, any tag other than the three, any [Fact] that is really an inference or guess, or a persona not in the stub context treated as real | Step 3 closed-world check; `.claude/rules/output-standards.md` (every substantive claim); Operating Principle #6 |
| C4 | If the route is Park, is there a revisit trigger (a date or a condition)? | A concrete trigger is written | Park with no trigger or a vague one ("later"). **n/a if the route is not Park.** | "A Park without a revisit trigger is a Decline in disguise" |
| C5 | Where it applies, does it use the register or the anti-bet? | **Applies only to a request that duplicates a register row, or that is about team collaboration/sharing** (the anti-bet). Pass: it names that register row or that anti-bet. | Applies but is not named. **n/a for every other request.** | Steps 4-5 |
| C6 | Is there an appropriate draft reply to the requester? | 2-5 sentences. If the output routed the request: it states the understood problem (not only the requested feature) and the reason. If the output itself says three or more problem slots are unknown: it asks specific clarifying questions instead. | No reply; a reply that only repeats the requested feature; or a vague "we'll look into it" with no reason and no question | Step 7 |

*Criteria v1 are preserved in this file's git history (`2514232`). Results logged before this revision were scored on v1.*

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
| 2026-10-01 | scratch (edit 1 + edit 2) | **Edit 2**: tags required across the whole output, not only Evidence (on top of edit 1) | 85.2% (46/54) | 79.2% (19/24) | **No** vs edit 1: dev +0.0; holdout +20.9 | **Revert** | The targeted criterion C3 barely moved (6/18 → 7/18). The holdout gain came from C6, which this edit does not touch, so it is treated as noise. Remaining C3 fails are mostly claims in the counter-argument / strategy-fit. |
| 2026-10-01 | scratch (edit 1) | **Edit 1**: Step 2 "detach the solution completely" rule + example not used in any scenario | 85.2% (46/54) | 58.3% (14/24) | **Yes**: dev +25.0 (floor 5.6); holdout +14.9 (floor 9.6) | **Keep** | C2 9/36 → 18/18. Side effect: CSV-export request moved from Park (5 of 6) to Discover (3 of 3) because an honestly "unknown" problem now reads as poorly understood. No criterion measures route appropriateness. 18 runs vs 36 for the baseline. |
| 2026-10-01 | `2514232` | baseline v2 (criteria revised; same 36 outputs regraded) | 60.2% (65/108; passes 57.4 / 63.0) | 43.4% (23/53; passes 48.1 / 38.5) | n/a | Baseline recorded | Stricter criteria expose the real weaknesses: C2 9/36, C3 4/36. |
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

---

## Round 2 notes (2026-10-01): criteria v2, then two edits

- **v2 criteria are consistent.** Grading pass A twice gave the same verdict on 104 of 108 (96.3%); the four flips were all C3 or C6.
- **Edit 1 kept.** It fixes the skill's headline failure (the problem statement restating the request) without touching anything else the criteria measure. Watch the side effect on routes: with the problem honestly "unknown", more requests go to Discover and fewer to Park. Whether that is right is a judgment call the eval does not make; consider adding a route-appropriateness scenario.
- **Edit 2 reverted.** Requiring tags across the whole output did not move C3. Remaining failures are mostly claims inside the counter-argument and strategy-fit, plus a few borderline grader calls. One failure is a harness limit: the producer reads the real repo (for example noticing `intake/requests/` is empty), and the stub context does not cover repo files. A better edit may need to restructure the output format (a dedicated tagged "counter-argument" field) rather than restate the rule.
- **Small samples.** Each edit was tested on one 18-run pass against a 36-run baseline. Treat the +25 as a clear win and the smaller differences as suggestive.
- **Not yet checked by the PM:** the spot-check from round 1 was by the assistant. Please read a few runs yourself.
