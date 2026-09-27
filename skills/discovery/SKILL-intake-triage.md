# SKILL: Intake & Triage
> Skill type: Workflow + Decision Framework
> Auto-activates when: user mentions "intake", "new request", "someone asked for", "customer asked", "feature request", "idea", "triage this", "should we do this"
> Force load: /intake

---

## What This Skill Does
Gives every incoming request — an idea, a stakeholder ask, a customer complaint, a bug, a competitor move — one front door and one outcome: a **routing decision** with a reason, logged in `intake/register.md`.

Intake is not prioritization. It doesn't decide *how much* something matters relative to everything else (that's `/evaluate`). It decides **what kind of thing this is, and where it goes next.**

---

## Intake Philosophy

**A request is a symptom with a solution attached. Your job is to detach them.**

- "Add a dark mode toggle" is a solution. "I can't use the app at night without it hurting" is the problem. Route on the problem.
- The loudest request is not the most important one. Intake exists so volume of voice never substitutes for evidence.
- Every request gets an answer. "Parked" and "declined" are legitimate answers. **Silence is not.**
- Saying no is cheap when it's fast and explained. It's expensive when it's slow and implied.

---

## The Intake Process

### Step 1: Capture the raw request, verbatim
Record who asked, when, through what channel, and their exact words. Do not paraphrase yet — the paraphrase is where the solution gets smuggled in.

### Step 2: Extract the problem
Restate as: **"[Persona] is trying to [job] but [obstacle], which causes [consequence]."**
If you can't fill all four slots, that's information: the request is under-specified. Note what's missing rather than inventing it.

### Step 3: Ground it (closed-world check)
- **Persona:** does the person/segment exist in `context-library/users.md`? If not, tag **[Assumption]** — do not invent a segment (Operating Principle #6).
- **Product area:** does the affected feature exist in `context-library/product.md`?
- **Evidence:** tag every claim **[Fact]** / **[Inference]** / **[Assumption]** (convention in `templates/PRD-template.md`). "Three users mentioned it" is a Fact only if you can name the three.

### Step 4: Size the signal
| Question | Why it matters |
|----------|---------------|
| Is this an anecdote or a pattern? (Search `intake/register.md` and feedback for duplicates.) | One loud voice ≠ a segment |
| How often, and how severe, when it happens? | Frequency × severity, not volume |
| Is there a real deadline or cost of delay? | Separates urgent from merely loud |
| Is this the *requester's* need or *the target persona's* need? | Prevents building for the wrong user |

### Step 5: Check strategy fit
- Does it connect to a current OKR or bet in `context-library/metrics.md`?
- Does it collide with a stated **anti-bet**? (If yes, the default route is Decline.)

### Step 6: Route it

| Route | When | What happens next |
|-------|------|-------------------|
| **Fast-track** | Small, reversible (two-way door), clearly in scope, low risk. No real trade-off to weigh. | Straight to a ticket. Skip `/evaluate` and the PRD. |
| **Discover** | Real signal, but the problem is poorly understood or evidence is mostly [Assumption]. | `/discover` — run research before committing to anything. |
| **Evaluate** | Problem is well understood and credible, but it competes with other work for the same capacity. | `/evaluate` — weigh options and trade-offs. |
| **Park** | Credible but not now. **Must include a revisit trigger** (a date or a condition, e.g. "if 5+ more users report this"). | Stays in register with the trigger. Reviewed on schedule. |
| **Decline** | Off-strategy, collides with an anti-bet, or the cost clearly exceeds any plausible value. | Reason recorded. Recurring declines are candidates for a formal anti-bet in `/strategy`. |
| **Duplicate** | Already in the register. | Link to the original; add this requester and evidence to it. |

**A Park without a revisit trigger is a Decline in disguise. Write the trigger or call it a Decline.**

### Step 7: Close the loop with the requester
Every routed request gets a short reply: what you understood the problem to be, where it's going, and why. Draft it as part of the output. A decline with a clear reason builds more trust than a vague "we'll look into it."

### Step 8: Log it
Add a row to `intake/register.md` and save the full record to `intake/requests/YYYY-MM-DD-short-description.md` using `templates/intake-request.md`.

---

## Output Format

```markdown
## Intake: [Short title]
**Route:** Fast-track / Discover / Evaluate / Park / Decline / Duplicate
**Problem (one sentence):** [Persona] is trying to [job] but [obstacle], which causes [consequence].
**Evidence:** [tagged Fact / Inference / Assumption items]
**Strategy fit:** [OKR / bet it connects to, or anti-bet it collides with, or "none"]
**Why this route:** [2-3 sentences]
**Revisit trigger (if Park):** [date or condition]
**Reply to requester:** [draft, 2-4 sentences]
**Logged:** intake/register.md
```

---

## Batch Mode
When triaging many items at once (a backlog dump, a support export, a stakeholder wish list), run Steps 1-6 for each, then output one table sorted by route. Cap Discover + Evaluate at what the team can actually absorb; anything beyond that is Park by default, with a trigger.

---

## Common Intake Failure Modes

❌ **The solution smuggle:** Logging "build X" as the problem. Fix: force the four-slot problem statement.

❌ **The squeaky wheel:** Routing by who asked, not by evidence. Fix: Step 4 sizes the signal independent of the requester.

❌ **Everything becomes a PRD:** Small reversible things pushed through heavy process. Fix: use Fast-track honestly.

❌ **The graveyard:** Parking with no trigger, never revisiting. Fix: trigger required; review parked items on a cadence.

❌ **The black hole:** Requester never hears back. Fix: Step 7 is not optional.

✅ **The front door that works:** Fast for the easy calls, honest about the hard ones, and every answer explained.

---

## Where This Sits
- **Upstream:** any source of requests, plus signals looping back from Iterate (`/retro`, metrics anomalies, competitor moves).
- **Downstream:** `/discover` (route: Discover), `/evaluate` (route: Evaluate), a ticket (route: Fast-track), `/strategy` (recurring Declines → anti-bets).
- **Related:** `routines/backlog-grooming.md` triages *existing issues*; this skill is the front door for *new requests*.
