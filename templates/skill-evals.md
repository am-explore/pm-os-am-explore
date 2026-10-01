# Skill Eval: [skill name]
> Copy to `evals/<skill-name>.md`. Method: `skills/automation/SKILL-skill-evals.md`.
> Target the framework file in `skills/`, never the router in `.claude/skills/`.

**Skill file under test:** `skills/[area]/SKILL-[name].md`
**Created:** [YYYY-MM-DD]
**Noise floor:** [x points — run the unchanged skill twice and score both; not measured yet]

---

## Scenarios

Realistic, messy inputs. Each carries its own stub context so the eval runs on placeholder `context-library/` files. Holdout scenarios are written once and not used to guide edits.

### Dev scenarios

**D1 — [short name]**
- Input: "[what a person would actually type]"
- Stub context: [personas, features, metrics, anti-bets the skill would normally read]

**D2 — [short name]**
- Input:
- Stub context:

**D3 — [short name]**
- Input:
- Stub context:

**D4 — Negative control — [short name]** *(the right behavior is to refuse, route away, or say there is not enough information)*
- Input:
- Stub context:

### Holdout scenarios

**H1 — [short name]**
- Input:
- Stub context:

**H2 — Negative control — [short name]**
- Input:
- Stub context:

---

## Criteria

Binary and observable. Each ties to a requirement the skill itself states. Two-graders test: could two reasonable graders disagree? If yes, rewrite.

| # | Question (yes/no) | Pass condition | Fail condition | Skill requirement it checks |
|---|-------------------|----------------|----------------|-----------------------------|
| C1 | | | | |
| C2 | | | | |
| C3 | | | | |
| C4 | | | | |
| C5 | | | | |

---

## Grader rules

- Grader sees only: scenario input, output, criteria. Not the skill file, not the edit history.
- Grader is a **separate session** from the producer; a different model, or you.
- Each verdict: pass/fail + one-line reason quoted from the output.
- Spot-check at least one third of verdicts. More than one in five disagreements → fix the criteria first.
- Runs per scenario: 3.

---

## Results log

Newest first. One row per run. One change per row.

| Date | Skill file @ commit | Change under test | Dev score | Holdout score | Beat noise floor? | Decision | Notes |
|------|--------------------|-------------------|-----------|---------------|-------------------|----------|-------|
| | | baseline | | | n/a | | |
