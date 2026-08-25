# SKILL: User Interviews
> Skill type: Guided Workflow + Template Generator
> Auto-activates when: user mentions "interview", "user research", "talk to users", "customer calls"
> Force load: /user-interview

---

## What This Skill Does
Generates customized user interview guides, coaches on interview technique, and synthesizes raw interview notes into structured insights for the OST and PRD.

---

## Interview Design Principles

**The #1 rule:** You are there to understand their world, not to validate your ideas.

**The curiosity frame:** Approach every interview as if you've never seen this problem before.
What surprised you will be more valuable than what confirmed you.

**What interviews are for:**
- Understanding the user's current workflow and mental model
- Identifying the gap between what they say they want and what they actually do
- Discovering the emotional and social dimensions of the problem
- Finding the trigger moments that create demand

**What interviews are NOT for:**
- Validating your roadmap ("Would you use feature X?")
- Getting commitment ("Would you pay for this?")
- Gathering requirements lists

---

## Interview Types by Stage

| Stage | Interview Type | Goal |
|-------|---------------|------|
| Problem discovery | Exploratory | Understand the world as users experience it |
| Solution discovery | Solution interview | Test if your solution fits the problem |
| Post-launch | Usage interview | Understand how they're actually using it |
| Churn analysis | Exit interview | Understand why they stopped or didn't convert |

---

## The Exploratory Interview Guide

**Duration:** 45-60 minutes
**Setup:** Screen share off. Video on. Record with permission.
**Pre-interview brief:** "I'm here to learn about your experience, not pitch anything. There are no right or wrong answers. Please be brutally honest — that's the most helpful thing you can do."

### Opening (5 min)
1. "Tell me about your role and what a typical week looks like."
2. "What's the most frustrating part of your job right now?"

### Getting to the Job (15 min)
3. "Can you walk me through the last time you had to [relevant task]? Start from the beginning."
   - *[Listen for: triggers, steps, tools, emotions, people involved]*
4. "What made that harder than it needed to be?"
5. "What did you do when [friction point they mentioned]?"
   - *[Listen for: workarounds — these are gold]*

### Digging Deeper (15 min)
6. "How important is solving [problem] to you, on a scale of 1-10? Why not a [higher/lower] number?"
7. "How are you solving this today? Walk me through exactly what you do."
8. "What do you wish existed that doesn't?"
   - *[Caution: listen for the underlying need, not the literal feature request]*

### The Hidden Insight Questions (10 min)
9. "If you could wave a magic wand and have this problem completely solved, what would your life look like differently?"
10. "Who else on your team is affected by this? How do they handle it?"
11. "What have you tried before that didn't work? Why didn't it work?"

### Closing (5 min)
12. "Is there anything I didn't ask about that you think I should know?"
13. "Who else should I talk to about this?"

---

## Interview Synthesis Template

After each interview, fill this in within 24 hours while memory is fresh:

**Interviewee:** [ROLE, COMPANY TYPE, SEGMENT]
**Date:** [DATE]
**Interview type:** [Exploratory / Solution / Usage / Exit]

**Top 3 insights:**
1. [INSIGHT — specific, not generic]
2. [INSIGHT]
3. [INSIGHT]

**Surprising moments:** [What challenged your assumptions?]

**Exact quotes worth saving:**
- "[QUOTE]" — context: [WHEN THEY SAID IT]
- "[QUOTE]" — context: [WHEN THEY SAID IT]

**Workflow discovery:**
- Current trigger: [What makes them seek a solution]
- Current steps: [Their existing workflow]
- Biggest friction: [Where they struggle most]
- Current workaround: [What they do instead of an ideal solution]

**Jobs to Be Done identified:**
- Functional job: [JTBD]
- Emotional job: [JTBD]

**Assumptions this confirms:**
- [ASSUMPTION + HOW CONFIRMED]

**Assumptions this challenges:**
- [ASSUMPTION + HOW CHALLENGED]

**Follow-up actions:**
- [ACTION]

---

## Batch Synthesis (5+ Interviews)

When you have 5+ interviews, run the pattern analysis:

1. **Frequency count:** Which pain points appeared in 3+/5 interviews?
2. **Intensity rank:** Which pains got the most emotional language?
3. **Workflow divergence:** Where did users' workflows differ most? (signals opportunity)
4. **Quote convergence:** Which exact phrases did multiple users independently use? (signals real pain vs stated pain)
5. **Assumption audit:** Which of your pre-existing assumptions survived? Which were killed?

**Output:** Opportunity ranking for the OST.

---

## Anti-Patterns in User Interviews

❌ **Leading questions:** "Don't you think it would be easier if...?"
❌ **Pitching while interviewing:** "We actually built something for that..."
❌ **Skipping the workflow:** Only asking opinions, not observing behavior
❌ **Recency bias:** Treating the most recent interview as most important
❌ **Confirmation mining:** Only surfacing quotes that support your hypothesis
✅ **The mom test:** Would your most polite user say this even if it's wrong? Structure questions so even your most agreeable user would disagree if they needed to.
