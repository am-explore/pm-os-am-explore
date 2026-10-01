# Evals
> A written test for each skill, so a change to a skill has to prove it helped.

---

## What This Is

One file per skill you care about, holding a few realistic scenarios, a handful of yes/no criteria, and a log of every run. You run the skill against the scenarios before and after editing it, and keep the edit only if it beats the measured noise and does not hurt the holdout scenarios.

Method: `skills/automation/SKILL-skill-evals.md` (run with `/skill-evals`).
Template: `templates/skill-evals.md`.

---

## Structure

```
evals/
├── README.md              ← This file
└── <skill-name>.md        ← One eval per skill
```

### Naming Convention
Match the framework file: `skills/discovery/SKILL-intake-triage.md` → `evals/intake-triage.md`.

---

## Rules

- **Evals target the framework file** in `skills/`, never the router in `.claude/skills/`.
- **Keep real data out of eval files.** Scenarios use a made-up product and inline stub context. Real product context belongs in a private repo's `context-library/`, not in a file that may be shared.
- **One change per log row.** If two things changed, you cannot say which one helped.
- **Write the eval from what went wrong.** The best scenarios are real failures you saw, with the specifics removed.

---

## Current Evals

| Skill | Eval file | Baseline | Last run |
|-------|-----------|----------|----------|
| Intake & Triage | `intake-triage.md` | not yet run | — |
