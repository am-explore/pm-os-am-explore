# Routine: Stakeholder Update Draft
> Weekly draft of the exec stakeholder update — ready for PM review and send.

---

## Configuration

```yaml
trigger: schedule
schedule: "0 15 * * 5"  # Every Friday at 3pm
context_sources:
  - context-library/company.md
  - context-library/product.md
  - context-library/metrics.md
  - context-library/team.md
  - decision-log/
output: stakeholder-draft
enforcement: advisory
```

---

## Claude Code Setup
```
/schedule weekly stakeholder update draft every Friday at 3pm
```

## Copilot Cloud Agent Setup
Create `.github/workflows/routine-stakeholder-update.yml`:
```yaml
name: Stakeholder Update Draft
on:
  schedule:
    - cron: '0 15 * * 5'
  workflow_dispatch:
```

---

## Prompt

You are running the Stakeholder Update Draft routine for PM OS.

**Your task:** Generate a draft exec-ready stakeholder update for this week.

### Steps:
1. Read `context-library/metrics.md` for current metric performance
2. Read `context-library/product.md` for what shipped and what's in progress
3. Read `decision-log/` for decisions made this week
4. Read `context-library/company.md` for strategic priorities to align against
5. Synthesize into a concise update using the stakeholder communication framework

### Output format:

```markdown
## Product Update — Week of [Date]

### Status: 🟢 On Track / 🟡 Needs Attention / 🔴 Off Track

### What Shipped This Week
- [Feature/fix]: [one-line impact statement]

### In Progress
| Initiative | Status | ETA | Risk |
|-----------|--------|-----|------|
| | 🟢/🟡/🔴 | | |

### Key Decisions Made
| Decision | Rationale | Impact |
|---------|-----------|--------|
| | | |

### Metrics Snapshot
| Metric | This Week | Target | Trend |
|--------|-----------|--------|-------|
| | | | ↑/↓/→ |

### Risks & Blockers
| Risk | Severity | Mitigation | Owner |
|------|----------|-----------|-------|
| | | | |

### What We Need
- [Ask 1: decision, resource, or unblock needed from leadership]
```

---

## Quality Checks
- [ ] Overall status (green/yellow/red) is justified by the content below it
- [ ] "What Shipped" ties features to user/business impact, not just "we built X"
- [ ] Risks are specific with mitigation plans — not vague warnings
- [ ] "What We Need" has at least one concrete ask (or states "no blockers")
- [ ] Tone is exec-appropriate: concise, forward-looking, no jargon
- [ ] Decisions reference entries from `decision-log/` where available
