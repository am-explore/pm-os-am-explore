---
name: skill-evals
description: Test whether an edit to a skill made it better. Use when editing, tuning or checking a skill in skills/, after a model change, or when asked "did that change help" about a skill.
---

Read and apply the full framework from `skills/automation/SKILL-skill-evals.md`.

Use the template `templates/skill-evals.md`; eval files live in `evals/` (see `evals/README.md`, worked example `evals/intake-triage.md`).

Target the framework file in `skills/`, never this router. Grade in a separate session from the one that produced the output. Change one thing at a time, run dev and holdout scenarios, and keep an edit only if it beats the measured noise floor without hurting holdout. Do not auto-apply edits; the PM approves each one.
