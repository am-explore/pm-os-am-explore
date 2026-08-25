---
name: review-prd
description: Trigger all 7 specialist reviewers to critique a PRD.
disable-model-invocation: true
---

Read each sub-agent persona file and produce a review from that perspective:

1. Read `sub-agents/engineer-reviewer.md` → produce the Engineer review
2. Read `sub-agents/designer-reviewer.md` → produce the Designer review
3. Read `sub-agents/exec-reviewer.md` → produce the Executive review
4. Read `sub-agents/user-researcher.md` → produce the User Researcher review
5. Read `sub-agents/data-analyst.md` → produce the Data Analyst review
6. Read `sub-agents/legal-reviewer.md` → produce the Legal/Privacy review
7. Read `sub-agents/competitor-watcher.md` → produce the Competitor Watcher review
8. Read `sub-agents/debate-facilitator.md` → run a debate pass across the 7 reviews, surfacing the sharpest tensions and agreements between reviewers
9. Read `sub-agents/synthesis-agent.md` → produce the final weighted recommendation with explicit must-fix / should-fix / consider buckets

Each reviewer should follow their own output format as defined in their file.
