# PdM Playbook
**A Practical Guide from User Understanding to Product Delivery**

---

## Introduction

This Playbook is a practical guide distilled from hands-on experience as a PdM. Each Part provides an overview of "what to do and why." The concrete procedures and question patterns are implemented in the Skills at the end. Use the Playbook as a map and the Skills as your tools.

---

## Part 1｜The Role of a PdM

The job of a PdM is to **keep the loop spinning**. User understanding → Problem definition → Hypothesis → Decision → Execution → Learning. Everything comes down to running this cycle fast and accurately.

**Scope of responsibility**: Problem definition, prioritization, product direction  
**What not to do**: Managing implementation details, making every decision

---

## Part 2｜User Understanding (Observe)

Deepen your understanding through three stages: **Hear → See → Do**. Interviews alone are not enough. There are things you can only see when you go into the field and experience what users experience firsthand.

What to capture through observation: work flows, workarounds, emotions, inefficiencies. Workarounds in particular are a sign of how serious a problem is.

**What AI cannot do**: Observing users in the field cannot be replaced by AI. AI is good at organizing CS tickets and interview notes, but the contextual understanding of "why that workaround emerged" can only be held by someone who has actually been in the field.

> 🔧 **Skill 1｜pdm-voice-to-problem** — Extract problem definitions from CS tickets, inquiries, and interviews

---

## Part 3｜Problem Definition (Orient)

A user's **request** and their **problem** are different things. "Make CSV faster" is a request; "anxiety about not knowing progress" is the problem. If you try to solve requests as stated, you end up building something correct but meaningless.

It is crucial to keep asking "why?" to get to the essence. Don't skimp on investing in problem definition.

> 🔧 **Skill 1｜pdm-voice-to-problem** — Convert user voices into problem definitions  
> 🔧 **Skill 2｜pdm-discuss-to-designdoc** — Clarify problems through AI discussion

---

## Part 4｜Hypothesis Thinking

Once the problem is defined, form a hypothesis. Structure it in three layers: **Problem → Root Cause Hypothesis → Solution Hypothesis**. Making hypotheses explicit allows you to plan validation, share with stakeholders, and learn from outcomes.

Conditions for a good hypothesis: simple, testable, and connected to user value.

> 🔧 **Skill 2｜pdm-discuss-to-designdoc** — Structure hypotheses through AI discussion

---

## Part 5｜Decision-Making

This is the most critical job of a PdM. Make judgments and move forward with perpetually incomplete information. Prioritization is essentially "deciding what not to do."

Evaluate along three axes: **Impact × Effort × Strategic Fit**. Using only Impact and Effort to prioritize can lead to spending resources on features that don't align with the company's direction this quarter. Being able to make the call "high impact, but not what we should do strategically right now" is a sign of a mature PdM.

Never forget: the cost of deferring a decision is greater than the cost of making a wrong one.

> 🔧 **Skill 5｜pdm-priority-matrix** — Organize priorities with Impact × Effort × Strategic Fit  
> 🔧 **Skill 6｜pdm-scope-management** — Align on scope with Must/Should/Could/Won't

---

## Part 6｜Stakeholder Management (Align)

**A good document that goes unread is the same as no document at all.**

Design Docs, specs, and priority matrices only work once they are understood and agreed upon by stakeholders. This Align phase is a continuous activity that runs in parallel with the OODA loop—it cannot be deferred.

### Types of Stakeholders and How to Work with Them

| Type | Primary Concern | What PdM Should Do |
|---|---|---|
| Executives / Senior Leadership | Business value, ROI, strategic alignment | Speak in numbers about problems and impact. Push implementation details to later |
| Engineers | Feasibility, tech debt, spec clarity | Eliminate ambiguity. Explain the reasons for changes. Work through Open Questions together |
| Designers | User experience, consistency | Involve them from the problem definition stage. Don't arrive with answers |
| Sales / CS | Promises to customers, timelines, feature lists | Communicate not just "what and when" but "why" |

### How to Build Alignment

Alignment happens in stages. Not every stakeholder needs all information, but the goal is a state where each person knows "what was decided in my domain."

- **Problem definition alignment**: Before reviewing the Design Doc, confirm "Is this Problem framing correct?"
- **Priority alignment**: Don't create the matrix alone and present it. Align on the definition of evaluation criteria with stakeholders in advance
- **Scope alignment**: Explicitly state the Won't list and communicate in advance what is "not included"
- **Spec alignment**: Make explicit who owns each action to close Open Questions

### Handling Disagreement

Disagreement is information. Understanding the background of "why they oppose" can sometimes lead to revisiting the problem definition.

- Don't shoot down objections—articulate the underlying concern
- Be prepared to clearly explain "the reason we're not doing this now"
- When consensus isn't reached, clarify the basis for the decision and ownership, then move forward

---

## Part 7｜Execution (Act)

PdMs don't implement, but they create the conditions for the development team to move at full speed. User stories clarify "whose feature this is," specs eliminate ambiguity, and mocks resolve misalignment before it happens.

> 🔧 **Skill 3｜pdm-designdoc-to-spec** — Design Doc → Spec  
> 🔧 **Skill 4｜pdm-spec-to-prompt** — Spec → AI implementation prompt

---

## Part 8｜Learning Loop (Learn)

A release is a checkpoint, not the finish line. To run the learning loop, **measurement design must be completed before release**. It's too late to start thinking "what should we track?" after launch.

### Two-Layer Measurement Framework

**Quantitative (What)**: Understand what is happening

| Measurement Type | Question | Example |
|---|---|---|
| Adoption rate | Are users using the feature? | % of users who used it at least once within 7 days |
| Retention rate | Are they continuing to use it? | Retention at 4 weeks |
| Completion rate | Are they achieving their goal? | % reaching the final step of the flow |
| Error rate | Where are they getting stuck? | Distribution of error-occurring steps |

**Qualitative (Why)**: Understand why it's happening

- Don't only investigate when numbers are unexpected—talk to at least 2–3 users within 2 weeks of release
- Ask "what were you trying to accomplish and how did you go about it?" rather than "where was it difficult to use?"

### Mapping Hypotheses to Results

Record the following for every release:

```
Hypothesis: [Who] [doing what] would change [which metric] [in what way]
Result: [What actually happened]
Learning: [Where the hypothesis was right and where it was wrong]
Next question: [What new questions does this release raise]
```

This record becomes the next Observe. Without it, the organization ends up reformulating the same hypotheses over and over.

### Deciding Not to Measure Is Also a Decision

Not every feature can be evaluated with data. In areas where data can't be collected or where the cost of collecting it isn't worth it, "deciding not to measure" is itself a decision. In that case, explicitly state "why we're not measuring."

---

## Part 9｜PdM Thinking Framework (OODA + Align)

The integrating framework for the whole.

| Phase | Content |
|---|---|
| **Observe** | User understanding, field observation |
| **Orient** | Problem definition, hypothesis formation |
| **Decide** | Prioritization, decision-making (including strategic fit) |
| **Act** | Execution, release |
| **Learn** | Measurement, hypothesis validation, back to Observe |
| **Align** | Runs in parallel through all phases. Keeping stakeholders aligned |

Align doesn't sit "outside" the OODA loop—it happens in each phase. Thinking "will leadership buy into this problem framing?" during Observe, and "how will engineers receive this prioritization?" during Decide—that is Align.

As long as this loop keeps spinning, the product keeps evolving.

---

## Part 10｜PdM in the Age of AI

AI is a tool to accelerate the loop. The flow **Idea → AI Discussion → Design Doc → Spec → Implementation Prompt → Prototype** lets you validate hypotheses without writing code.

### What AI Is Good At vs. What Humans Must Own

To use AI effectively as a PdM, you need to know precisely where AI's capabilities end.

| What AI Is Good At | What Humans Must Own |
|---|---|
| Classifying and organizing text and voice data | Field observation, direct dialogue with users |
| Structuring (converting to templates) | Contextual understanding of market and competitive landscape |
| Internal logic consistency checks | Reading organizational politics and stakeholder emotions |
| Enumerating edge cases | Value judgments about "what really matters" |
| Generating specs and prompts | Final decision-making and accountability |

**Important caveat**: AI discussion is powerful for "organizing internal logic," but AI doesn't know market reality, your company's situation, or organizational context. Humans must bring that information in. "AI conversation eliminates the need for market research" is a misconception.

What doesn't change: problem-definition ability and judgment. What changes: implementation speed. What's newly required: articulation ability, evaluation ability, and sound judgment about when to delegate to AI.

> 🔧 **Skills 1–4** cover this entire flow

---

## Part 11｜PdM Growth

Accumulating experience alone is meaningless. **Growth only happens when you digest it.**

Five habits that accelerate growth:
1. Observe users once a week
2. Write a hypothesis for every feature you build
3. Make decisions even when uncertain
4. After each release, compare hypotheses against results
5. Log friction with stakeholders and look for patterns

---

## Part 12｜PdM Toolkit

The complete set of tools supporting PdM work in practice. Use thinking frameworks and AI Skills in combination.

### Problem — Define the Problem

| Tool | Overview |
|---|---|
| User Understanding Note | Record observations and interview insights immediately in four columns: Observed / Heard / Insights / Questions |
| Problem Definition Template | Organize on one page: whose problem, what kind of problem, impact, and scope |
| Hypothesis Template | Make explicit the three layers: problem → root cause hypothesis → solution hypothesis |

> 🔧 **Skill 1｜pdm-voice-to-problem**  
> Takes CS tickets, inquiries, and interview content as input; classifies and organizes user voices; outputs a problem definition summary ready to pass to Skill 2.

### Design — Design the Solution

| Tool | Overview |
|---|---|
| Design Doc | Structured in 8 sections: Background / Problem / Goals / Non-Goals / User Story / UX Flow / Technical Notes / Metrics. The central document for aligning stakeholders on "what to build, for whom, and why." |

> 🔧 **Skill 2｜pdm-discuss-to-designdoc**  
> Takes ideas or a problem definition summary as input; clarifies thinking through AI discussion; generates a Design Doc.

### Build — Hand Off to Engineering

| Tool | Overview |
|---|---|
| Spec | An implementation guide for engineers that documents the happy path, edge cases, display states, and out-of-scope items |
| Implementation Prompt | AI implementation instruction structured in 4 layers: Goal / Tech / Requirements / Output. Can be handed directly to AI to generate a prototype. |

> 🔧 **Skill 3｜pdm-designdoc-to-spec**  
> Takes a Design Doc as input and generates a spec engineers can use directly for implementation. Also detects missing edge cases and display states.

> 🔧 **Skill 4｜pdm-spec-to-prompt**  
> Takes a spec as input and generates an AI implementation prompt. The final step to getting a prototype without writing code.

### Decision — Make Decisions

| Tool | Overview |
|---|---|
| Priority Matrix | Evaluate features and initiatives on three axes—Impact × Effort × Strategic Fit—and classify into "Prioritize / Plan / If Time Allows / Won't Do" |
| Scope Management | Define release scope with Must / Should / Could / Won't. Explicitly stating Won't prevents scope creep |

> 🔧 **Skill 5｜pdm-priority-matrix**  
> Evaluates a list of features and initiatives by Impact × Effort × Strategic Fit, and outputs a priority table with recommended action order.

> 🔧 **Skill 6｜pdm-scope-management**  
> Defines scope with Must / Should / Could / Won't and outputs a scope definition table suitable for stakeholder alignment.

### Learn — Measure and Learn

| Tool | Overview |
|---|---|
| Measurement Design Sheet | Defines "what to measure, why, and how" before release. Uses adoption rate, retention rate, completion rate, and error rate as the basic set of four metrics |
| Hypothesis Log | Records hypothesis, result, learning, and next question for each release. Becomes the organization's learning asset |

---

## Skills Reference

The set of Skills as practical tools for this Playbook. Install into Claude to use.

| Skill | Role | Input | Output |
|---|---|---|---|
| **Skill 1**｜pdm-voice-to-problem | Convert user voices into problem definitions | CS tickets, interviews | Problem definition summary |
| **Skill 2**｜pdm-discuss-to-designdoc | Create Design Doc through AI discussion | Ideas, problem definition summary | Design Doc |
| **Skill 3**｜pdm-designdoc-to-spec | Convert Design Doc into spec | Design Doc | Spec |
| **Skill 4**｜pdm-spec-to-prompt | Convert spec into AI implementation prompt | Spec | Implementation prompt |
| **Skill 5**｜pdm-priority-matrix | Organize priorities with Impact × Effort × Strategic Fit | Feature / initiative list | Priority matrix |
| **Skill 6**｜pdm-scope-management | Manage scope with Must/Should/Could/Won't | Feature list, priority matrix | Scope definition table |

```
User Voices
  ↓ Skill 1
Problem Definition Summary
  ↓ Skill 2
Design Doc ←→ Stakeholder Alignment (Part 6)
  ↓ Skill 5 (Priority judgment + Strategic Fit check)
  ↓ Skill 6 (Scope alignment)
  ↓ Skill 3
Spec
  ↓ Skill 4
Implementation Prompt → Prototype
  ↓
Measurement & Hypothesis Validation → Back to Observe (Part 8)
```
