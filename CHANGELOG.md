# Changelog
> Newest first. One entry per dated release tag (`vYYYY-MM-DD`; a second release the same day gets `.2`, `.3`).
>
> **Maintenance:** `docs/index.html` shows a condensed "Version History" widget (in the masthead) mirroring the 3 most recent entries here. When you tag a new release, update both together — add a `.version-entry` block there (newest first, `open` on the first one) and drop the oldest once there are already 3. This file stays the full, un-condensed record either way.

## v2026-10-01.3 — Intake: detach the solution from the problem
First skill edit judged by `/skill-evals`, and the first one it rejected.

- **`skills/discovery/SKILL-intake-triage.md` (Step 2):** new "detach the solution completely" rule. The obstacle must never be "the product has no X" where X is what was asked for; if deleting the requested feature leaves no real problem, that slot is written as unknown. Includes a worked example that is not one of the eval's scenarios.
- **Measured:** dev 60.2% → 85.2% (+25.0, noise floor 5.6); holdout 43.4% → 58.3% (+14.9, noise floor 9.6); the targeted criterion went from 9/36 to 18/18. One 18-run pass per edit against a 36-run baseline, so treat the size as indicative.
- **Side effect to know about:** with the problem honestly "unknown", more requests route to Discover and fewer to Park (CSV-export request: Park 5 of 6 → Discover 3 of 3). The eval does not judge whether that is better.
- **Rejected by the eval:** a second edit (require tags across the whole output) did not move its target criterion and was reverted; logged in `evals/intake-triage.md`.
- **Eval revised:** criteria C2, C3, C5, C6 rewritten to be unambiguous (grader self-agreement 96.3%); results log and round-2 notes added.

## v2026-10-01.2 — First eval baseline (intake triage)
First real run of `/skill-evals` on a skill, plus what it taught us about the eval itself.

- **`evals/intake-triage.md`:** baseline recorded — dev 85.1%, holdout 84.4%, measured noise floor 4.7 / 13.5 pts (36 runs, graded in separate sessions on a different model).
- **Eval fix:** the shared stub context is now the complete list the producer and grader must both receive. The first grading was discarded because the grader had a shorter context than the producer.
- **Found:** the criteria for solution-smuggle (C2), tag scope (C3), the n/a rule (C5) and the under-specified-request reply (C6) are ambiguous and must be revised before the eval can judge an edit; a human spot-check of one third of verdicts is written up in the file.
- **Found in the skill itself:** problem statements often restate the requested solution as the obstacle, and evidence tags stop at the Evidence list.

## v2026-10-01 — Skill Evals and Cross-Model Panel
Two quality tools: one to tell whether an edit to a skill actually helped, and one to get a review of a high-stakes document from models that cannot see each other's answers.

- **New: `/skill-evals`** (`skills/automation/SKILL-skill-evals.md`) — a written test per skill: dev and holdout scenarios (including a negative control), 4-6 yes/no criteria, repeat runs, a measured noise floor, a grader separate from the producer, one change at a time, human approval of every kept edit. Deliberately does **not** auto-rewrite skills.
- **New: `/panel`** (`skills/execution/SKILL-cross-model-panel.md`) — independent first-round review by 2-3 different vendors' models, optional anonymous rebuttal round (UPHOLD / REJECT / CONCEDE / MISSED), results grouped by finding with contested ones flagged, every finding verified against the document by a person. Starts with a **privacy gate**: nothing sensitive leaves the machine. No script shipped.
- **New templates:** `templates/skill-evals.md`, `templates/panel-review.md` (round prompts + findings record).
- **New folder:** `evals/` (README + a worked example, `intake-triage.md`, on a fictional product).
- **Wiring:** `CLAUDE.md` (skill routing, commands, templates, Skill Evals section, persona-vs-cross-model note), `.github/copilot-instructions.md`, README, two new routers under `.claude/skills/`.
- **Credits:** the keep-if-better loop follows Karpathy's autoresearch idea as applied in *Self-Improving Agent Skills*, and the panel protocol follows *LLM Panel Agent Team* by Jaret Arnold, both in Shubhamsaboo/awesome-llm-apps (Apache-2.0). Concepts only, no code copied; the holdout / noise-floor / separate-grader rules and the privacy gate are additions.

## v2026-09-26 — Intake and Trade-off Evaluation
Adds the two stages the lifecycle was missing: a front door for incoming requests, and a single place to weigh options and state what a choice costs.

- **New: `/intake`** (`skills/discovery/SKILL-intake-triage.md`) — separates the problem from the proposed solution, grounds it against `context-library/`, sizes the signal, and routes it: Fast-track / Discover / Evaluate / Park (revisit trigger required) / Decline / Duplicate.
- **New: `/evaluate`** (`skills/strategy/SKILL-tradeoff-evaluation.md`) — options (always including "do nothing" and "smallest test"), criteria and weights set before scoring, a sensitivity check on [Assumption]-tagged inputs, an explicit trade-off statement, the bet, and a kill/revisit criterion.
- **New templates:** `templates/intake-request.md`, `templates/tradeoff-evaluation.md`.
- **New folder:** `intake/` (README, `register.md`, `requests/`) — same convention as `decision-log/`.
- **`hooks/prd-quality-gate.md`:** new Traceability check (PRD links to an intake record, a recorded trade-off, and a kill/revisit criterion).
- **Wiring:** `CLAUDE.md` routing/commands/templates, `.github/copilot-instructions.md`, README, `routines/backlog-grooming.md` (scope note: existing issues vs. new requests), `skills/execution/SKILL-roadmap.md` and `decision-log/README.md` cross-links.
- **Field map (`docs/index.html`):** two new stations — Intake (1) and Trade-off & Evaluate (3) — renumbered to 9 stations; loop-back now returns to Intake. Fixed the "Define & Strategize" label, which had its two lines in reverse order.
