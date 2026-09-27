# Intake
> The front door. Every request gets an answer — even if the answer is "not now" or "no."

---

## What This Is

A register of incoming requests (ideas, customer asks, stakeholder asks, bugs, competitor moves) and where each one was routed. It exists so that:
- Nothing is lost in a Slack thread
- Nothing is decided by who shouted loudest
- "Parked" items resurface when their trigger fires
- Repeated declines become explicit **anti-bets**

Framework: `skills/discovery/SKILL-intake-triage.md` (run with `/intake`).
Template: `templates/intake-request.md`.

---

## Structure

```
intake/
├── README.md        ← This file
├── register.md      ← One-line index of every request (the thing you scan)
└── requests/        ← Full record per request
    └── YYYY-MM-DD-short-description.md
```

### Naming Convention
`YYYY-MM-DD-short-description.md` — same as `decision-log/`.

---

## Routes

| Route | Meaning | Next step |
|-------|---------|-----------|
| **Fast-track** | Small, reversible, in scope | Ticket |
| **Discover** | Real signal, problem not understood | `/discover` |
| **Evaluate** | Understood, competes for capacity | `/evaluate` |
| **Park** | Credible, not now — has a revisit trigger | Wait for trigger |
| **Decline** | Off-strategy or cost clearly exceeds value | Reply with reason |
| **Duplicate** | Already in the register | Link + merge evidence |

---

## Rhythm

- **Triage new requests within 2 business days.** Configurable, but pick a number and keep it.
- **Review Parked items on their triggers**, and at minimum monthly.
- **Quarterly:** scan Declines for patterns. Three declines for the same reason = write the anti-bet.

---

## How It Connects

- Upstream: any source of requests; signals looping back from **Iterate** (`/retro`, metrics anomalies, competitor moves).
- Downstream: `/discover`, `/evaluate`, tickets, `/strategy` (anti-bets).
- `routines/backlog-grooming.md` triages *existing issues*; intake is the front door for *new requests*.
- The `prd-quality-gate` hook checks that a PRD traces back to an intake record or an evaluation.
