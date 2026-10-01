# SKILL: Cross-Model Panel
> Skill type: Review Protocol
> Auto-activates when: user mentions "second opinion", "cross-check", "blind review", "panel review", "run this past other models", "check this with another assistant"
> Force load: /panel

---

## What This Skill Does
Runs a consequential document past **models from different vendors**, keeps them from seeing each other's answers, then (optionally) makes each one defend or drop its findings against the others', anonymously. You get a list of candidate problems, grouped by how contested they are, and you check each against the document.

It formalizes something PMs already do by hand — pasting a draft into more than one assistant and comparing — and fixes what usually goes wrong with it: the second assistant sees the first one's answer and anchors on it.

**It generates candidate defects. You still decide.** Agreement between models is a signal about where to look, not proof that something is right.

---

## How This Differs From `/review-prd`

| | `/review-prd` (7 personas) | `/panel` (cross-model) |
|---|---|---|
| Who reviews | One model playing 7 roles | 2-3 different vendors' models, same task |
| What it adds | **Breadth** — engineering, design, legal, competitor lenses | **Independence** — different training, different blind spots |
| Weakness it covers | A single perspective missing | A single model's blind spot or agreeableness |
| Cost | Cheap, in-session | Several model calls, plus copy-paste or API setup |

Use `/review-prd` for routine breadth. Use `/panel` when the artifact is hard to reverse, expensive to get wrong, or you have already seen one model be confidently wrong about this kind of thing.

---

## When to Use This

- A PRD about to go to engineering
- A `/evaluate` result with a kill criterion you are about to bet on
- A strategy or positioning doc going to leadership
- Any artifact where a missed flaw costs weeks

Do NOT use this for:
- Drafts, routine updates, anything easy to fix later
- **Anything you would not paste into a third-party service.** See Step 0.
- Settling a values or taste question — models will disagree and neither is right

---

## The Protocol

### Step 0: Privacy gate (do this first, every time)
You are sending the artifact to other companies' models.
- Do **not** run a panel on anything that contains confidential or sensitive product, user, financial, health or personal information. Real `context-library/` content, real user quotes and unreleased plans belong here.
- If the artifact is worth a panel but sensitive: **sanitize** (replace names, numbers and product specifics with neutral stand-ins) and confirm the sanitized version still raises the same questions — or skip the panel.
- If you cannot say yes to "I am comfortable with this text leaving my machine," stop.

### Step 1: Pick the panel
- **At least 2, ideally 3, models from different vendors.** Two models from the same vendor are not independent.
- Pick cheap/fast tiers for round 1; the point is independent eyes, not the strongest model.
- Fresh session for each. No shared history, no memory, no prior conversation about this artifact.

### Step 2: Round 1 — independent review
Send every model the **identical** prompt at the same time (use the Round 1 prompt in `templates/panel-review.md`). Rules:
- Same wording, same material, no model sees another's answer.
- Findings only — a numbered list, each with the section it refers to and one sentence on why it is wrong. "No comment" is a valid answer.
- Each finding is tagged **[Fact]** (checkable in the document), **[Inference]** or **[Assumption]**, per the convention in `templates/PRD-template.md`.
- Save each answer verbatim. Do not edit or merge them.

### Step 3: Round 2 — anonymous rebuttal (optional; use when round 1 disagrees or the stakes are high)
For each model, show it the **other** models' findings with names removed ("Reviewer A", "Reviewer B"). **Re-shuffle the letters per model** so position never reveals the vendor. Use the Round 2 prompt in `templates/panel-review.md`. Each model must open every point with one of:

- **UPHOLD** — my finding stands despite their objection; say what proves it
- **REJECT** — their finding is wrong or overstated; point to the text that makes it wrong
- **CONCEDE** — I was wrong; say exactly what changed my mind
- **MISSED** — they caught something real that I did not; confirm it against the document

Two rules that matter more than agreeing:
1. **Do not concede merely because someone disagreed.** Concede only when you can point at what proves you wrong.
2. **Do not invent agreement.** If a finding cannot be verified from the material, say so.

### Step 4: Group by finding, not by reviewer
Rebuild the results as one table, one row per finding:

| Finding (reviewer + number) | Positions | Status |
|---|---|---|
| A3 — "Success metric has no baseline" | B: also raised it in round 1; C: MISSED (confirmed after reading A) | **Agreed** |
| B2 — "Rollout assumes one region" | A: REJECT; C: UPHOLD | **CONTESTED** |

- **Agreed:** raised or upheld by 2+ models independently. Verify, then likely fix.
- **CONTESTED:** at least one REJECT against at least one UPHOLD/MISSED. **Look here first** — the disagreement usually marks a real judgment call.
- **Single-source, no response:** one model only. Lowest priority, but do not discard — the lone dissenter is sometimes right.

### Step 5: You verify every finding against the document
For each finding, open the artifact and check it. Record: **Accept** (change the document), **Reject** (with reason), or **Decide** (a real trade-off — take it to `/evaluate`). A finding no one can point to a passage for is rejected.

### Step 6: Record it
Fill the record in `templates/panel-review.md`. If the panel changed a significant decision, log it with `/log-decision`.

---

## Output Format

```markdown
## Panel Review: [artifact]  —  [date]
**Privacy gate:** passed / sanitized / skipped — [what was removed, if anything]
**Panel:** [models/vendors used, versions pinned]
**Rounds:** 1 / 1+2
**Findings:** [n total] → [n agreed] · [n contested] · [n single-source]
**Accepted:** [list]   **Rejected:** [list with reasons]   **Escalated to /evaluate:** [list]
**Cost / effort:** [rough]
**Would I run it again on this kind of artifact?** yes / no — [why]
```

---

## Honest Limits

- **Anonymity is best-effort.** A model with a recognizable style, or one that names itself, is identifiable no matter what letter it gets.
- **Shared blind spots survive.** Vendors train on overlapping data. Unanimity is weaker evidence than it feels.
- **Small panels.** Two or three reviewers is a handful of opinions, not a statistic.
- **Round 2 is the expensive one.** Each rebuttal prompt carries the document again plus every review.
- **Models may not follow the format.** If a rebuttal ignores the four labels, read it by hand instead of forcing it into the table.
- **Pin versions to compare runs.** "Latest" aliases drift; record which model versions you actually used.

---

## Optional: automating the round trip

Doing this by copy-paste across three chat windows works and keeps you in control. If you want it scripted, the *LLM Panel Agent Team* example in [Shubhamsaboo/awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps) (`advanced_ai_agents/multi_agent_apps/agent_teams/llm_panel_agent_team`, Apache-2.0) implements the same two-round shape through one OpenRouter key. PM OS does **not** ship that script. Read it before running it, and note it sends your text to OpenRouter and to each vendor — Step 0 applies in full. Its prompt is written for code diffs; use the document prompts in `templates/panel-review.md` instead.

---

## Where This Sits
- **Upstream:** a finished draft from `/write-prd`, `/evaluate`, `/strategy`.
- **Alongside:** `/review-prd` (breadth), `sub-agents/debate-facilitator.md` (structures disagreement *between personas*).
- **Downstream:** edits to the artifact; `/evaluate` for contested trade-offs; `/log-decision` when the panel changed a decision.

---

## Credits
The two-round shape (independent first pass, then anonymous, per-reviewer-shuffled rebuttals with UPHOLD / REJECT / CONCEDE / MISSED and the two anti-sycophancy rules) comes from the *LLM Panel Agent Team* example by Jaret Arnold in [Shubhamsaboo/awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps) (Apache-2.0). This skill reuses the protocol idea, not the code. The privacy gate, document-review prompts, finding-level verification step and the comparison with persona review are additions.
