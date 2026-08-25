# Hook: Launch Readiness Check
> Pre-launch checklist verification before a launch plan is finalized.

---

## Configuration

```yaml
trigger: pre-launch-finalization
enforcement: advisory  # Change to "blocking" to require all checks before launch approval
applies_to: Launch plans, GTM documents
```

### Claude Code (optional wiring)
To fire this check automatically in Claude Code, add a `PreToolUse` hook in `.claude/settings.json` that triggers on writes to launch-plan files:
```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "echo 'Launch readiness: review against hooks/launch-readiness.md before finalizing'"
          }
        ]
      }
    ]
  }
}
```

### GitHub Copilot
Copilot does not support repo-local hook configs. Invoke this check manually before finalizing a launch:
```
Run the launch readiness check (hooks/launch-readiness.md) on the current launch plan
```
Or enforce in CI via a GitHub Actions workflow gated on launch-plan file changes.

---

## Launch Readiness Categories

### 1. Product Readiness
- [ ] Feature is code-complete and passing all tests
- [ ] Edge cases and error states are handled
- [ ] Performance testing completed against defined SLAs
- [ ] Rollback plan is documented and tested
- [ ] Feature flags are configured for gradual rollout

### 2. Metrics & Instrumentation
- [ ] Success metrics from PRD are instrumented and validated
- [ ] Dashboard or monitoring is set up to track launch metrics
- [ ] Alerting is configured for critical thresholds
- [ ] Baseline metrics captured pre-launch for comparison
- [ ] Experiment framework ready (if A/B testing)

### 3. User Communication
- [ ] In-app messaging/announcements prepared
- [ ] Help documentation or changelog updated
- [ ] Support team briefed with FAQ and known issues
- [ ] Customer-facing comms drafted (email, blog, social)
- [ ] Internal stakeholders notified of launch timeline

### 4. Risk Mitigation
- [ ] All 🔴 assumptions from PRD are validated or accepted as known risks
- [ ] Dependencies confirmed (no external blockers)
- [ ] On-call or support escalation plan for launch window
- [ ] Kill switch or degradation plan if metrics go wrong
- [ ] Legal/compliance review completed (if applicable)

### 5. Go-to-Market
- [ ] Positioning statement finalized
- [ ] Sales enablement materials ready (if B2B)
- [ ] Marketing assets prepared and scheduled
- [ ] Launch timing confirmed (no conflicting releases)
- [ ] Success criteria for launch defined (when do we declare success/failure?)

---

## Output Format

```markdown
## Launch Readiness Check — [Feature/Initiative]

### Overall: ✅ Ready / ⚠️ Conditional / ❌ Not Ready

### Readiness Scorecard
| Category | Score | Blockers |
|----------|-------|----------|
| Product Readiness | [X/5] | |
| Metrics & Instrumentation | [X/5] | |
| User Communication | [X/5] | |
| Risk Mitigation | [X/5] | |
| Go-to-Market | [X/5] | |

### Blocking Issues (must resolve before launch)
1. [Issue]: [what's missing and who owns the fix]

### Advisory Issues (should resolve, launch can proceed)
1. [Issue]: [recommendation]

### Launch Confidence
- **Recommended launch date:** [date] or "not yet — resolve blockers first"
- **Risk level:** [low/medium/high]
- **Biggest remaining risk:** [specific risk]

### Sign-Off Checklist
| Stakeholder | Status | Date |
|------------|--------|------|
| PM | ☐ | |
| Engineering | ☐ | |
| Design | ☐ | |
| Marketing | ☐ | |
| Support | ☐ | |
```
