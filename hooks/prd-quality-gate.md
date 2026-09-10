# Hook: PRD Quality Gate
> Validates that a PRD has all essential elements before it enters review.

---

## Configuration

```yaml
trigger: post-prd-creation
enforcement: advisory  # Change to "blocking" to require all checks before review
applies_to: PRD documents
```

### Claude Code (optional wiring)
To fire this gate automatically in Claude Code, add a `PostToolUse` hook in `.claude/settings.json` that triggers on `Write|Edit` of PRD files. Example:
```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "echo 'PRD quality gate: review output against hooks/prd-quality-gate.md'"
          }
        ]
      }
    ]
  }
}
```

### GitHub Copilot
Copilot does not support repo-local hook configs. Invoke this gate manually:
```
Run the PRD quality gate (hooks/prd-quality-gate.md) on the current PRD
```
Or enforce in CI via a GitHub Actions workflow that runs a checker on PRD file changes.

---

## Quality Checks

### Required Elements (must be present)
- [ ] **Problem Statement** — Clearly articulated user problem AND business problem
- [ ] **Why Now** — Explicit reasoning for timing
- [ ] **Target Users** — Specific personas from `context-library/users.md`, not generic descriptions
- [ ] **Success Metrics** — At least 2 measurable metrics with current baseline, target, and timeframe
- [ ] **Assumptions** — At least 3 assumptions listed with risk level and validation method
- [ ] **What We're NOT Building** — Explicit scope exclusions with rationale

### Quality Signals (should be present)
- [ ] **User Flows** — At least one key user flow described
- [ ] **Technical Considerations** — Dependencies and risks acknowledged
- [ ] **Phasing** — MVP scope defined with clear launch criteria
- [ ] **Open Questions** — At least one genuine open question with owner and due date
- [ ] **Decision Log** — Section present for tracking decisions during development

### Closed-World Constraint Check (entities must exist in context-library/)
- [ ] Every customer tier or pricing plan named exists in `context-library/company.md`
- [ ] Every persona named exists in `context-library/users.md` — not an invented segment
- [ ] Every competitor named exists in `context-library/competitors.md`
- [ ] Every API, integration, or technical capability claimed exists in `context-library/product.md`'s Technical Architecture section
- [ ] Nothing reads as invented — if it isn't in `context-library/`, it's not established; tag it **[Assumption]** (see Epistemic Tagging in `templates/PRD-template.md`) instead of stating it as given

### Anti-Patterns (should NOT be present)
- [ ] No vague success metrics ("improve engagement" without a number)
- [ ] No undefined personas ("users" without specifying which segment)
- [ ] No missing tradeoffs ("we'll do everything in Phase 1")
- [ ] No phantom certainty (stating assumptions as facts)
- [ ] No solution-first framing (jumping to features before establishing the problem)
- [ ] No invented entities (customer tiers, personas, APIs, competitors) absent from `context-library/`

---

## Output Format

```markdown
## PRD Quality Gate — [PRD Title]

### Status: ✅ Pass / ⚠️ Advisory / ❌ Blocking Issues

### Required Elements
| Element | Status | Notes |
|---------|--------|-------|
| Problem Statement | ✅/❌ | |
| Why Now | ✅/❌ | |
| Target Users | ✅/❌ | |
| Success Metrics | ✅/❌ | |
| Assumptions | ✅/❌ | |
| Scope Exclusions | ✅/❌ | |

### Quality Signals
| Signal | Status | Suggestion |
|--------|--------|-----------|
| User Flows | ✅/⚠️ | |
| Technical Considerations | ✅/⚠️ | |
| Phasing | ✅/⚠️ | |
| Open Questions | ✅/⚠️ | |

### Closed-World Constraint Check
| Entity Type | Status | Notes |
|-------------|--------|-------|
| Customer tiers / pricing | ✅/❌ | |
| Personas | ✅/❌ | |
| Competitors | ✅/❌ | |
| APIs / technical capabilities | ✅/❌ | |

### Anti-Patterns Detected
[List any anti-patterns found with specific examples from the PRD]

### Recommended Fixes
1. [Specific fix with example text]
2. [Specific fix with example text]
```
