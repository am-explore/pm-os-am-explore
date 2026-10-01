# Panel Review: [artifact name]
> Method: `skills/execution/SKILL-cross-model-panel.md` (run with `/panel`).
> Run Step 0 (privacy gate) before pasting anything below into a third-party model.

**Date:** [YYYY-MM-DD]
**Artifact:** [path or title, and version/commit]
**Privacy gate:** passed / sanitized / skipped — [what was removed or replaced]
**Panel:** [vendor + exact model/version for each; at least 2 vendors]
**Rounds:** 1 / 1+2

---

## Round 1 prompt (send identical text to every model, fresh session each)

```
Review the document below. Report defects only, as a numbered list. For each one give:
- the section or line it refers to,
- one sentence on why it is a problem,
- a tag: [Fact] if it can be checked directly in the document, [Inference] if it follows
  from the document, [Assumption] if you are guessing at something not stated.

Do not praise. Do not rewrite the document. If the document needs no comment, say so.

--- DOCUMENT START ---
[paste artifact]
--- DOCUMENT END ---
```

Optional line to add for a PRD: `Pay particular attention to: unmeasurable success criteria, unstated assumptions about users, and scope that does not match the stated problem.`

## Round 2 prompt (per model; show only the OTHER models' findings, anonymised, letters re-shuffled for each model)

```
You already reviewed this document independently. Below are the findings of the OTHER
reviewers. They did not see your review, and their identities are withheld on purpose.

Refer to a finding as <Letter><number>: B3 is Reviewer B's finding 3. Start each point with
exactly one of these labels, then the reference, then your argument:

  UPHOLD:  B3 -- you stand by your own claim despite theirs; say what proves it.
  REJECT:  B3 -- theirs is wrong or overstated; point to the text that makes it wrong.
  CONCEDE: B3 -- you were wrong; say exactly what changed your mind.
  MISSED:  B3 -- they caught something real you did not; confirm it against the document
           rather than taking their word.

Two rules that matter more than agreeing:
1. Do NOT concede merely because someone disagreed. Concede only if you can point at
   what proves you wrong.
2. Do NOT invent agreement. If a finding cannot be verified from the document, say so.

Your own review was:
[paste this model's round-1 answer]

The other reviewers' findings:
### Reviewer A
[paste, names removed]
### Reviewer B
[paste, names removed]
```

---

## Findings, grouped by finding

| # | Finding (source reviewer + number) | Tag | Positions after round 2 | Status | My verdict | Reason / action |
|---|-----------------------------------|-----|-------------------------|--------|------------|-----------------|
| 1 | | [Fact/Inference/Assumption] | | Agreed / CONTESTED / Single-source | Accept / Reject / Decide | |

Status key — **Agreed:** raised or upheld by 2+ models independently. **CONTESTED:** at least one REJECT against at least one UPHOLD/MISSED; look here first. **Single-source:** one model only; lowest priority, not discarded.

Verdicts: **Accept** = change the document. **Reject** = no passage supports it (say why). **Decide** = a genuine trade-off; take it to `/evaluate`.

---

## Outcome

- **Findings:** [n total] → [n agreed] · [n contested] · [n single-source]
- **Accepted:** [list]
- **Rejected:** [list with reasons]
- **Escalated to /evaluate:** [list]
- **Roughly what it cost (time/money):**
- **Round 2 used?** yes / no — [why]
- **Would I run it again on this kind of artifact?** yes / no — [why]
- **Decision logged?** [link to `decision-log/` entry, or "no decision changed"]

> Findings are candidates. Agreement between models is a pointer to where to look, not evidence the point is correct. Every accepted finding was checked against the document by a person.
