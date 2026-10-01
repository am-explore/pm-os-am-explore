# SKILL: Skill Evals
> Skill type: Quality Gate + Change Log
> Auto-activates when: user mentions "eval a skill", "test a skill", "did that edit make the skill better", "skill regression", "tune this skill"
> Force load: /skill-evals

---

## What This Skill Does
Gives every skill in `skills/` a small, written test: a few realistic scenarios and a handful of yes/no criteria. You run the skill against them **before and after** you edit it, and keep the edit only if the evidence says it helped.

PM OS has many skills and no way to tell whether a change made one better or worse. This is that way. It is deliberately **manual and human-approved**: it measures, it does not rewrite skills on its own.

---

## Why Not Automate the Whole Loop

The idea of letting a model rewrite its own skill against a score (try one change, keep it if the score rises, repeat) is sound. Naive versions fail in three predictable ways, and this skill is built around avoiding them:

| Failure in a naive auto-optimizer | What this skill does instead |
|---|---|
| **The same model writes the scenarios, runs the skill and grades the result.** It grades its own homework. | The grader is a **different session** from the producer — ideally a different model, or you. |
| **Few checks, so one flipped answer looks like progress.** 3 scenarios × 5 criteria is 15 checks; a single flip is ~7 points. | **Repeat runs and a measured noise floor** (below). An edit must beat the noise, not just the baseline. |
| **Edits are tuned to the same scenarios that judge them.** The skill learns the test. | **Holdout scenarios** the edit was never tuned against. A dev-score gain that costs holdout score is rejected. |

Also: auto-mutation edits whatever file it is pointed at. In PM OS the `.claude/skills/*/SKILL.md` files are thin routers; the framework lives in `skills/*/SKILL-*.md`. **Evals target the framework file, never the router.**

---

## When to Use This

- Before you edit a skill, to record a baseline
- After you edit a skill, to check the edit helped and broke nothing
- After a model change (new model, new version) — skills can regress silently
- Quarterly, on the skills you actually use (see "Active Now" in your `CLAUDE.md` if you have one)

Do NOT use this for:
- Judging a *product* decision (use `/evaluate`)
- Reviewing a document a skill produced (use `/review-prd` or `/panel`)
- Skills you have never run for real — first run them on real work, then write the eval from what went wrong

---

## The Framework

### Step 1: Write the eval file
Copy `templates/skill-evals.md` to `evals/<skill-name>.md`. It has four parts:

**Scenarios — 3 to 4 "dev" + 1 to 2 "holdout".**
- Realistic inputs, written the way a person would actually say them (messy, partial, with a solution smuggled in).
- Each carries its own stub context inline, so the eval works on a repo whose `context-library/` is placeholders.
- Include **one negative-control scenario** where the right behavior is to *refuse, route away, or say "not enough information"*. A skill that does something for every input is broken.
- Holdout scenarios are written once, then **not used to guide edits**.

**Criteria — 4 to 6 yes/no questions.**
- Each ties to a requirement stated in the skill itself ("every Park has a revisit trigger").
- Each has a written **pass condition** and **fail condition**.
- Binary and observable. "Is the output good?" is not a criterion. "Does every Park include a date or a condition?" is.
- Test: *could two reasonable graders disagree?* If yes, rewrite it.

**Grader rules** — who grades, and how (Step 3).

**Results log** — one row per run: date, skill file commit, the single change made, dev score, holdout score, decision.

### Step 2: Run the skill on every scenario, 3 times
Run each scenario in a fresh Claude Code session with the repo present (so the skill loads the way it does in real use, not as a bare prompt). Save each output. Three runs per scenario, because outputs vary run to run.

### Step 3: Grade in a separate session
Give the grader only: the scenario input, the output, and the criteria. **Not** the skill file, not the history of edits. For each criterion: pass or fail plus a one-line reason quoted from the output.

- Best: you grade a sample yourself.
- Good: a different model than the one that produced the output.
- Weakest, avoid for decisions: the same model in the same session.

Spot-check at least a third of the grader's verdicts yourself. If you disagree with more than one in five, the criteria are ambiguous — fix them before trusting any score.

### Step 4: Measure the noise floor (once per skill, redo after a model change)
Run the **unchanged** skill twice and score both. The gap between the two scores is your **noise floor**. An edit counts as an improvement only if it beats the baseline by **more than the noise floor** and the gain shows up in most runs, not just the average.

### Step 5: Make one change, re-run, decide
- Change **one** thing in the skill: add an example, add a constraint, restructure a step, or cover an edge case.
- Re-run Steps 2-3 on dev **and** holdout.
- **Keep** only if: dev score beats baseline by more than the noise floor **and** holdout did not drop by more than the noise floor.
- Otherwise **revert** (`git checkout` the file) and note why in the log.
- You approve each kept change. Nothing is auto-applied.

### Step 6: Log it
Add the row to the eval file's Results log. Mention the eval result in the commit message for the skill edit.

---

## Output Format

```markdown
## Skill Eval: [skill name]  —  [date]
**Skill file:** skills/<area>/SKILL-<name>.md @ [commit]
**Change under test:** [one sentence, or "baseline"]
**Noise floor:** [x points, from two unchanged runs]
**Dev score:** [passed / total] ([%])   **Holdout score:** [passed / total] ([%])
**Per-criterion:** [criterion → pass rate across runs]
**Grader:** [who/which model, separate from producer? yes/no]
**Decision:** Keep / Revert — [reason]
**Disagreements with grader (spot-check):** [n of m]
```

---

## Common Failure Modes

❌ **Grading with the producer.** Same session, same model: it agrees with itself. Fix: separate grader.
❌ **Tuning to the test.** Editing until the dev scenarios pass, never looking at holdout. Fix: holdout gates the keep decision.
❌ **Mistaking noise for progress.** A 7-point swing on 15 checks is one flipped answer. Fix: noise floor.
❌ **Vague criteria.** "Output is clear." Fix: the two-graders test.
❌ **Evaluating the router.** Editing `.claude/skills/*/SKILL.md`. Fix: eval the `skills/*/SKILL-*.md` framework file.
❌ **Only happy-path scenarios.** Fix: one negative control per eval.

---

## Honest Limits
- Small samples. This catches obvious regressions and clear wins, not subtle ones.
- A model-graded score is a proxy. The human spot-check is what keeps it honest.
- Criteria encode what the skill *claims* to do. They cannot tell you the skill claims the wrong thing — that is a `/review-strategy` question.

---

## Where This Sits
- **Downstream of:** any edit to a file in `skills/`.
- **Related:** `/panel` (vendor-independent review of a *document*); `hooks/` (checks at write time); `tools/custom-skill-template.md` (when you write a new skill, write its eval file at the same time).

---

## Credits
The keep-if-better, one-change-at-a-time loop follows the autoresearch idea from Andrej Karpathy ([karpathy/autoresearch](https://github.com/karpathy/autoresearch)). It was applied to agent skills in the *Self-Improving Agent Skills* example in [Shubhamsaboo/awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps) (Apache-2.0). This skill reuses only that concept; the holdout, separate-grader and noise-floor rules, and the human-approval gate, are additions.
