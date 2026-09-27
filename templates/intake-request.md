# Intake: [Short title]
**ID:** [YYYY-MM-DD-short-description]
**Logged:** [YYYY-MM-DD]
**Status:** [open / routed / closed]
**Route:** [Fast-track / Discover / Evaluate / Park / Decline / Duplicate]

---

## 1. The Raw Request (verbatim)

- **Who asked:** [name / role / segment]
- **Channel:** [support ticket / sales call / Slack / interview / internal idea / metric anomaly / competitor move]
- **Date received:** [YYYY-MM-DD]
- **Exact words:**
  > [Paste verbatim. Do not paraphrase here — the paraphrase is where the solution gets smuggled in.]

---

## 2. The Problem (not the solution)

> **[Persona]** is trying to **[job]** but **[obstacle]**, which causes **[consequence]**.

- **Solution the requester proposed (kept separate on purpose):** [what they asked for]
- **What's missing to fill the sentence above:** [gaps — don't invent them]

---

## 3. Grounding (closed-world check)

| Check | Result |
|-------|--------|
| Persona exists in `context-library/users.md`? | [Yes: name / No → tag [Assumption]] |
| Affected feature exists in `context-library/product.md`? | [Yes / No] |
| Duplicate or related item in `intake/register.md`? | [None / link] |

**Evidence** (tag every line — see Epistemic Tagging in `templates/PRD-template.md`):
- [Fact] [what's verified, with source]
- [Inference] [what's reasonably projected]
- [Assumption] [what's unvalidated]

---

## 4. Signal Size

- **Anecdote or pattern?** [how many distinct sources, named]
- **Frequency × severity:** [how often, how bad when it happens]
- **Real deadline / cost of delay:** [none / describe]
- **Whose need is it — requester's or target persona's?** [answer]

---

## 5. Strategy Fit

- **Connects to OKR / bet:** [which, or "none"]
- **Collides with anti-bet:** [which, or "none"]

---

## 6. Routing Decision

**Route:** [Fast-track / Discover / Evaluate / Park / Decline / Duplicate]

**Why this route:** [2-3 sentences]

**Revisit trigger (required if Park):** [date, or condition, e.g. "if 5+ additional users report this"]

**Next action:** [owner + what + by when — e.g. "Run /evaluate against the two other onboarding requests, PM, by Fri"]

---

## 7. Reply to Requester

> [2-4 sentences: what we understood the problem to be, where it's going, and why. A clear decline beats a vague "we'll look into it."]

**Sent:** [ ] yes — [date]

---

## 8. Outcome (fill in when closed)

- **Resolved by:** [ticket / PRD / evaluation / decision-log entry link]
- **Final outcome:** [shipped / declined / merged into X / expired]
- **Was the routing right in hindsight?** [one line — this feeds better triage over time]
