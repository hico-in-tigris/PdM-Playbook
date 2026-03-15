# Skill 4｜Spec → Implementation Prompt

## Purpose of This Skill

Convert the content of a spec into an AI implementation prompt. This is the final step to getting a working prototype without writing code.

**The implementation prompt is drafted by AI; the PdM reviews and refines it.** The PdM's role is to provide the spec as input — and to verify that the generated prompt accurately reflects the intent of the spec.

**Input**: Spec (Markdown format)
**Output**: AI implementation prompt (ready to paste directly into AI)

---

## Steps

### Step 1｜Read and Review the Spec

When you receive the spec, confirm that the information needed for prompt generation is present.

**Minimum required information**
- What to build (overview)
- Who it's for (target users)
- Happy path (normal operation flow)
- Technology stack (if unknown, ask)

**Optional but improves quality if present**
- Edge cases / exception handling
- Display state definitions (loading, error, empty state)
- UI/UX spec details

If the technology stack is unknown, always ask: "What technology stack will this be implemented with? (e.g., Next.js + TypeScript, React, Python, etc.)"

### Step 2｜Generate the Implementation Prompt

Generate the implementation prompt using the following template:

```
## Goal
<!-- Format: "Build a feature that allows [user] to [do X]" -->

## Tech Stack
- Language: 
- Framework: 
- Other libraries / tools: 

## Requirements

### Functional Requirements
1. [Feature Name]
   - [Specific requirement]
   
2. [Feature Name]
   - [Specific requirement]

### Edge Cases / Exception Handling
- If X → do Y
- If X errors → display Y

### UI State Definitions
- Default: 
- Loading: 
- Error: 
- Empty state: 
- Success: 

### Out of Scope
- Do not implement X
- Do not handle Y

## Output
Output format:
- File structure:
- Code format (should work as copy-paste):
- Comments: [English / not needed]

## Constraints
- Output code that has been verified to work
- If library installation is required, include the steps
- If anything is unclear, ask before implementing
```

### Step 3｜Quality Check the Prompt

Check the generated prompt against the following:

**Checklist**

- [ ] Does Goal include the user and purpose?
- [ ] Is Tech Stack written specifically?
- [ ] Are edge cases covered?
- [ ] Is Out of Scope explicitly stated?
- [ ] Is the Output format specified?

**Tips for improving prompt quality**

- **More specific is better**. Instead of "a nice UI," write "disable the button and show a loading spinner."
- **Write what not to do**. AI will try to add features if not instructed otherwise. Be explicit to keep scope.
- **Don't ask for everything at once**. For complex features, splitting into "first implement only the data fetching part" improves accuracy.

### Step 4｜Output the Final Version

Output the completed implementation prompt in a code block.

Where appropriate, recommend splitting the prompt:
- If there are many features: "Recommend passing to AI one feature at a time"
- If UI is complex: "Recommend implementing the logic first, then layering the UI on top"

---

## Notes

- A prompt is a spec for AI. Write it with the same care as a spec.
- An ambiguous prompt generates ambiguous code. Aim for "something verifiable" rather than "something that kind of works."
- The purpose of a prototype is to validate a hypothesis, not to build a finished product. Don't aim for perfection—instruct for the minimum implementation needed for validation.
