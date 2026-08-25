# SKILL: Product Design Review
> Skill type: Review Framework + Critique Workflow
> Auto-activates when: user mentions "design review", "UX", "user flow", "mockup", "prototype", "usability", "onboarding design"
> Force load: /design-review

---

## What This Skill Does
Runs structured critique of product designs using UX heuristics, PLG design principles, and behavioral design frameworks. Surfaces both usability issues and strategic design opportunities.

---

## The PM's Role in Design
You are not the designer. You are the user advocate and strategic stakeholder.

**Your critique should focus on:**
1. Does this design serve the user's job-to-be-done?
2. Does it move toward or away from the activation event?
3. Does it make the core value obvious before requiring effort?
4. Does it create the emotional response we intend?
5. Are we asking the user to do too much work?

**Your critique should NOT be:**
- Personal aesthetic preferences
- "Can we make it look more like [competitor]?"
- Detailed layout decisions that are the designer's domain
- Changes that don't connect to user outcomes

---

## Nielsen's 10 Usability Heuristics (Applied to Product)

| # | Heuristic | PM Evaluation Questions |
|---|-----------|------------------------|
| 1 | Visibility of system status | Does the user always know what's happening? Where they are? What happened? |
| 2 | Match between system and real world | Does the language match how users actually talk about this problem? |
| 3 | User control and freedom | Can users undo mistakes easily? Is there a clear exit? |
| 4 | Consistency and standards | Do interactions work the same way across the product? |
| 5 | Error prevention | Does the design prevent common mistakes before they happen? |
| 6 | Recognition over recall | Are options visible rather than requiring memory? |
| 7 | Flexibility and efficiency | Can power users take shortcuts while novices still succeed? |
| 8 | Aesthetic and minimalist design | Is every element on screen earning its place? |
| 9 | Recognizable error messages | Are errors explained in plain language with recovery steps? |
| 10 | Help and documentation | Is help available in context, not just in a separate docs site? |

---

## PLG Design Principles

### 1. Time-to-Value Design
Every design decision should be evaluated against: does this get the user to their first value moment faster or slower?

**Anti-patterns:**
- Required profile completion before first use
- Multi-step wizards before showing the core product
- Onboarding that teaches features rather than delivering value
- Blank empty states that leave users stranded

**Patterns that work:**
- "What are you trying to do?" → personalized path to value
- Pre-populated sample data so users can experience the product immediately
- Progressive onboarding — get to value, then build the context
- Contextual tooltips that appear when relevant, not upfront

### 2. Activation Funnel Design
Map every screen between signup and activation. For each screen:
- What must the user understand here?
- What action must they take?
- What's stopping them?
- How do we reduce that friction?

**Friction inventory:**
- Required fields (each field = drop-off)
- Confirmation emails (async delays kill momentum)
- Permissions requests (ask only when needed, explain why)
- Tutorial videos (most users skip them — embed value instead)
- Choice overload (too many options = paralysis = abandon)

### 3. Empty State Design
Empty states are the highest-leverage design surface in PLG products.

**The empty state opportunity:** When a user has no data yet, you have their full attention and maximum motivation. Design this moment deliberately.

**Empty state checklist:**
- [ ] Is the value prop visible (not just "No items yet")?
- [ ] Is there ONE clear call-to-action?
- [ ] Is there a way to see what "done" looks like (sample data, demo, video)?
- [ ] Is the first step so small it feels effortless?

### 4. Feature Discovery Design
Users should discover features at the moment they need them, not before.

**Patterns:**
- Contextual feature announcements triggered by behavior
- Feature gates that show what's available before blocking access
- "Try this" suggestions based on what similar users do next
- Progressive complexity: simple view → advanced view toggle

### 5. Viral Loop Design
If your growth strategy includes virality, the sharing/invitation moment must be designed with the same rigor as activation.

**Sharing design checklist:**
- [ ] Is the sharing action obvious and low-friction?
- [ ] Does shared content carry context that makes it valuable to the recipient?
- [ ] Is the invitation personalized enough to have a high open rate?
- [ ] Does the new user arrival experience connect to why they were invited?

---

## Design Review Criteria Matrix

Rate each area 1-5 when reviewing designs:

| Area | Score (1-5) | Key Issue | Recommendation |
|------|------------|----------|---------------|
| Clarity — is the value obvious? | | | |
| Friction — is the task easy? | | | |
| Hierarchy — is the most important thing most prominent? | | | |
| Consistency — does it match the rest of the product? | | | |
| Mobile experience | | | |
| Accessibility | | | |
| Empty state quality | | | |
| Error handling | | | |
| Time-to-value impact | | | |

**Design review output format:**
- **Critical issues:** [Must fix before shipping — user can't complete task / serious confusion]
- **Important improvements:** [Should fix — measurable UX degradation]
- **Nice-to-haves:** [Consider if time allows]
- **Strengths:** [What's working well — don't only critique]

---

## The 5-Second Test (Use for Any New Design)
Show the design to someone unfamiliar with it for 5 seconds. Then ask:
1. "What is this product?"
2. "What are you supposed to do here?"
3. "Who is this for?"

If they can't answer 1 and 2 accurately, the design needs revision before it's ready for user testing.
