# Skill 2｜AI Discussion → Design Doc

## Purpose of This Skill

Take a "rough idea" or "sense of a problem" and, through dialogue with AI, deepen and refine it into a Design Doc that can be shared with stakeholders.

**Input**: Ideas, problem sense, improvement proposals (bullet points or conversational language are fine)  
**Output**: Design Doc (Markdown format)

---

## Steps

### Step 1｜Discussion with AI

When you receive an idea, don't jump straight into creating a Design Doc.
First, organize your thinking through discussion with AI. This determines the quality of the Design Doc.

The discussion proceeds in three major phases:

```
Phase 1｜Generate ideas (5–10 min)
  └ Dump everything in your head

Phase 2｜Deepen with questions (10–20 min)
  └ AI returns questions, clarifying ambiguities

Phase 3｜Consolidate into structure (5–10 min)
  └ Convert organized content into Design Doc form
```

**How to start Phase 1**

This single question is enough to begin:

> "Please tell me about the ideas or problems you're thinking about, in whatever order they come to mind. Bullet points or conversational language are both fine."

Don't ask for a perfect explanation here. Rough is fine. The goal is just to get everything out first.

For Phase 2, use the "Reference: Question Pattern Library" at the end to dig deeper.  
For how to communicate with AI, see "Reference: How to Talk to AI."

### Step 2｜Generate a Draft Design Doc

Based on information from the discussion, generate a Design Doc using the following template:

```markdown
# Design Doc｜[Feature / Initiative Name]

**Date**: YYYY-MM-DD  
**Author**: [Name]  
**Status**: Draft / Review / Approved

---

## Background
<!-- Why we're working on this now. Context, history, and assumptions -->

## Problem
<!-- Define the problem to solve. Describe from both qualitative and quantitative angles -->
<!-- Clearly state: "who" is "in what situation" experiencing "what difficulty" -->

## Goals
<!-- What this initiative aims to achieve, in bullet points -->
<!-- Include success metrics (KPIs/OKRs) -->

## Non-Goals
<!-- Explicitly state what is not in scope this time -->
<!-- Deciding "what not to do" is as important as the Goals -->

## User Story
<!-- Describe who needs what and why -->
<!-- Format: "[User] wants to [do something]. Because [reason]." -->

## UX Flow
<!-- Describe the user's action flow in order -->
<!-- Include branches, error states, and edge cases -->

## Technical Notes
<!-- Implementation constraints, considerations, and dependencies -->
<!-- Write what you know; mark unknowns as [TBD] -->

## Metrics
<!-- What to measure after release -->
<!-- Set metrics that enable before/after comparison -->

## Open Questions
<!-- Questions not yet answered; things that still need to be decided -->
```

### Step 3｜Review and Fill Gaps

After generating the draft, confirm the following and ask for feedback:

1. **List all blank / [TBD] sections** and communicate what's needed
2. **Check alignment between Problem and Goals**. "Does this Goal solve this Problem?"
3. **Check that Non-Goals are written**. If absent, ask: "What are you not doing this time?"
4. **Verify that Metrics are specific**. "What number measures success?"

### Step 4｜Output the Final Version

Incorporate feedback and output the final Design Doc in Markdown.  
If the next step (spec creation) is needed, hand off to Skill 3 (pdm-designdoc-to-spec).

---

## Notes

- A Design Doc is also a thinking organization tool. "Can't write it" = "haven't thought it through enough," so mark unresolved sections as [TBD] and keep moving.
- UX Flow doesn't need to be a flowchart. Writing the user's actions in order in prose is fine.
- Technical Notes will largely be deferred to engineers, but write any constraints you already know.

---

## Limits of AI Discussion and What Humans Must Supply

AI discussion is powerful for "organizing internal logic." However, there is information AI doesn't have. Humans must always bring this in.

**What AI doesn't know**

| Information AI Doesn't Have | How Humans Should Supply It |
|---|---|
| Current market and competitive landscape | Read competitive research and industry reports before discussion |
| Company strategy and OKRs | Review management direction and quarterly goals before entering discussion |
| Internal politics and stakeholder sentiment | Share the substance of pre-conversations with stakeholders |
| User field context | Convey specific episodes from observations and interviews |
| History of past decisions | Explain background like "we tried the same idea before and X happened" |

**The right mindset for using AI**

AI functions as a discussion partner, but the final responsibility for judgment always rests with humans. When AI says "this idea seems good," that means the internal logic holds together—it does not guarantee market success.

Don't interpret an AI's positive response as "validation complete." AI can only judge within the range of information it was given.

> 💡 When AI gives you a positive response, that is a signal that "your logic is internally consistent." It is not a signal that "it is correct in external reality."

---

## Reference: Question Pattern Library

Questions used in discussion have different types. Use them according to the situation.

**① Questions to make the user concrete**
When the idea is stuck at the word "user":

- "What specific job title or role is that user?"
- "In what kind of situation does that user encounter this problem?"
- "How is that user currently working around this problem? (Workaround)"
- "How often per week do you think that user experiences this problem?"

> 💡 Asking about workarounds is especially important. When a workaround becomes visible—"manually copying to Excel" or "taking screenshots to share every time"—the severity of the problem becomes real.

**② Questions to dig deeper into the problem**
When the explanation is surface-level: "X is inconvenient" or "I want to improve X":

- "Because of that inconvenience, what is the user unable to do?"
- "What happens if this problem is left unsolved?"
- "'X is inconvenient'—is that a speed problem or a usability problem?"
- "Is a similar problem occurring in other situations?"

> 💡 "Inconvenient" or "hard to use" are not yet problem definitions. Digging down to "what the user cannot do" reveals the real problem.

**③ Questions to separate solution from problem**
When the input comes as "I want to build X feature":

- "What is the user trying to achieve with that feature?"
- "Is there another way to achieve the same goal without that feature?"
- "Why did you think of this form of solution? Did you consider other approaches?"

> 💡 A feature idea is a "solution hypothesis," not a "problem." Defining the problem first often leads to a better solution. Common example: "I want faster search" → the real problem was "anxiety about not being able to find results."

**④ Questions to clarify goals**
When there's a directional sense of "improve" or "fix," but no specific picture of success:

- "When this initiative succeeds, what will have changed?"
- "Looking back in 3 months, what number or state will you look at and say 'it worked'?"
- "In terms of user behavior, what should increase and what should decrease for this to be a success?"

> 💡 "It got better" can't be measured. Converting to a measurable goal makes later Metrics design smooth.

**⑤ Questions to narrow the scope**
When ideas are multiplying and there's too much to do:

- "What absolutely must be solved in this release?"
- "What would be nice to have, but would be fine without?"
- "If you had to remove one thing this time, what would you cut?"

> 💡 Deciding "what not to do" is an important PdM job. Writing a Design Doc with an unclear scope leads to divergent stakeholder understanding later.

---

## Reference: How to Talk to AI

The key mindset for AI discussion is "using it to organize your own thinking," not "getting AI to produce the answer."

**Basic pattern**

```
Put your hypothesis out first → let AI poke holes in it
```

❌ Common mistake
> "What do you think about this idea?"

→ AI gives a safe, non-committal answer. Doesn't help organize your thinking.

✅ Correct approach
> "I think [X user] is struggling with [Y]. I'm planning to build [Z] as the solution. Are there gaps in this problem definition, or other perspectives I should consider?"

→ AI will respond: "Have you considered this case?" "Is this assumption actually correct?" and so on.

**Discussion prompt template**

```
## Background
[One paragraph on why you're thinking about this initiative]

## Current Problem Recognition
[Your definition of the problem]

## Proposed Solution
[Image of the feature idea or initiative]

## Areas Where I Lack Confidence
[Specifically what you want challenged]

## Request
Please identify: gaps in the problem definition, incorrect assumptions, and other perspectives I should consider.
Prioritize pushback, questions, and blind spots over agreement.
```

> 💡 Explicitly stating "prioritize pushback over agreement" is the key. AI tends to give affirmative responses by default. Actively requesting a critical perspective is how you find holes in your thinking.

---

## Reference: Common Failure Patterns and Fixes

**Failure ① The discussion immediately turns to solutions**

Symptom: Starting with "I want to build this screen" or "I want to add this button."  
Problem: Implementation talk starts before the problem is defined; later you ask "wait, who was this for again?"  
Fix: Ask "What is the user trying to achieve with that screen?" and steer back to the problem.

**Failure ② The problem is too broad**

Symptom: "I want to improve the overall user experience," "I want to fix onboarding somehow," etc.  
Problem: Too broad to decide anything. Design Doc stays abstract.  
Fix: Ask "Of all of that, which single moment is the user struggling with most?"

**Failure ③ The goal is "releasing the feature"**

Symptom: Writing "release X feature" as a Goal.  
Problem: Release is a means, not an end. You won't notice if things didn't change after releasing.  
Fix: Reframe: "What will have changed as a result of the release for it to be a success?"

**Failure ④ Not writing Non-Goals**

Symptom: Only writing what to do; not writing what not to do.  
Problem: As implementation progresses, "let's add this too" and "this seems necessary too" cause scope creep.  
Fix: Always ask "please explicitly state what you're not doing this time" during discussion.

**Failure ⑤ Metrics are "users will be satisfied"**

Symptom: Success metrics are qualitative and unmeasurable.  
Problem: Can't judge success or failure after release.  
Fix: Ask "What would you measure to confirm that?" and convert to a number or state change.
