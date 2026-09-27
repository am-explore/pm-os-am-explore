# Changelog
> Newest first. One entry per dated release tag (`vYYYY-MM-DD`; a second release the same day gets `.2`, `.3`).

## v2026-09-26 — Intake and Trade-off Evaluation
Adds the two stages the lifecycle was missing: a front door for incoming requests, and a single place to weigh options and state what a choice costs.

- **New: `/intake`** (`skills/discovery/SKILL-intake-triage.md`) — separates the problem from the proposed solution, grounds it against `context-library/`, sizes the signal, and routes it: Fast-track / Discover / Evaluate / Park (revisit trigger required) / Decline / Duplicate.
- **New: `/evaluate`** (`skills/strategy/SKILL-tradeoff-evaluation.md`) — options (always including "do nothing" and "smallest test"), criteria and weights set before scoring, a sensitivity check on [Assumption]-tagged inputs, an explicit trade-off statement, the bet, and a kill/revisit criterion.
- **New templates:** `templates/intake-request.md`, `templates/tradeoff-evaluation.md`.
- **New folder:** `intake/` (README, `register.md`, `requests/`) — same convention as `decision-log/`.
- **`hooks/prd-quality-gate.md`:** new Traceability check (PRD links to an intake record, a recorded trade-off, and a kill/revisit criterion).
- **Wiring:** `CLAUDE.md` routing/commands/templates, `.github/copilot-instructions.md`, README, `routines/backlog-grooming.md` (scope note: existing issues vs. new requests), `skills/execution/SKILL-roadmap.md` and `decision-log/README.md` cross-links.
- **Field map (`docs/index.html`):** two new stations — Intake (1) and Trade-off & Evaluate (3) — renumbered to 9 stations; loop-back now returns to Intake. Fixed the "Define & Strategize" label, which had its two lines in reverse order.
