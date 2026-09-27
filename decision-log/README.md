# Decision Log
> The institutional memory of your product team. Every significant decision, captured with full context.

---

## What This Is

The decision log is a centralized, timestamped record of product decisions. It ensures that future you — or a new team member — can understand not just *what* was decided, but *why*, what alternatives were considered, and what the strongest counter-argument was.

---

## How It Works

### Automatic Capture
The `decision-logger` agent (`.claude/agents/decision-logger.md`) monitors conversations for decisions and prompts you to log them. It captures:
- Context that prompted the decision
- Options considered with pros/cons
- The decision itself
- Rationale and counter-arguments
- Owner and review date

### Manual Capture
Log a decision manually:
```
Log a decision: We chose to delay the notification feature to Q4 because...
```

Or use the template directly: `templates/decision-template.md`

### Retrieval
Ask your AI partner:
```
Why did we decide to use webhooks instead of polling?
What decisions have we made about pricing this quarter?
Show me decisions that are due for review.
```

---

## Decision File Format

Each decision is a markdown file in `decision-log/decisions/`:
```
decision-log/
├── README.md           ← This file
├── decisions/          ← Individual decision files
│   ├── 2026-04-18-example-decision.md
│   └── ...
└── .gitkeep
```

### Naming Convention
`YYYY-MM-DD-short-description.md`

Example: `2026-04-18-delay-notifications-to-q4.md`

---

## Decision Types

| Type | When to Log |
|------|------------|
| **Strategic** | Changes to vision, positioning, target market, competitive response |
| **Tactical** | Feature prioritization, phasing, scope tradeoffs |
| **Technical** | Architecture choices, vendor selection, build vs. buy |
| **Organizational** | Team structure, process changes, ownership shifts |

---

## Best Practices

1. **Log decisions when they're made** — not a week later when context is fuzzy
2. **Always capture the counter-argument** — it's the most valuable part of the log
3. **Set review dates** — decisions should be revisited as context changes
4. **Link to artifacts** — reference PRDs, roadmap items, strategy docs
5. **Don't log trivial choices** — focus on decisions that affect direction, resources, or users

---

## Integration with Other Systems

- **Trade-off evaluations** (`templates/tradeoff-evaluation.md`) are the reasoning behind significant decisions — link the evaluation from the decision file
- **Intake** (`intake/`) records link forward to the decision that resolved them
- **PRDs** reference decisions in their Decision Log section
- **Stakeholder updates** surface recent decisions via the `stakeholder-update-draft` routine
- **Strategy reviews** use decision patterns to identify team tendencies
- **Context freshness audits** flag decisions that are past their review date
