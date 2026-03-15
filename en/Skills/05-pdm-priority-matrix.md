# Skill 5｜Priority Matrix

## Purpose of This Skill

Evaluate multiple feature and initiative candidates on three axes—**Impact × Effort × Strategic Fit**—and produce an actionable priority order that stakeholders can align on.

**Input**: List of features / initiatives (bullet points, backlog, idea notes—anything goes)  
**Output**: Priority matrix + recommended action order

---

## Steps

### Step 1｜Receive the List and Pre-process

Before beginning evaluation, confirm the following:

- Is each item an appropriate unit of "feature / initiative"? (Is the granularity consistent?)
- If granularity is inconsistent, propose decomposing or consolidating
- Align on the definition of evaluation axes (see below)

**Evaluation axis definitions**

```
Impact
  High: Solves a core user problem / directly tied to KPIs
  Low : Nice to have / limited reach

Effort
  Low : Expected to be done within 1–2 weeks
  High: Will take 1+ month, or has high technical uncertainty

Strategic Fit
  High: Directly aligned with this quarter's / this period's company or product strategy
  Low : Valuable, but outside the current strategic focus
```

Definitions can be adjusted to fit the situation. What matters is "everyone evaluating with the same criteria."

**Questions to assess Strategic Fit**

- "Does this feature tie into our OKRs / priority areas this period?"
- "Is there a reason to do this now? Would it have the same value in six months?"
- "What is the cost of this feature delaying other strategic efforts?"

If Strategic Fit is unknown, mark as `[TBD]` and create an action to confirm with leadership.

---

### Step 2｜Evaluate Each Item

Evaluate each item on Impact (High/Low) × Effort (High/Low) and assign a Strategic Fit score (High/Low).

**When unsure about Impact**
- "What is the user doing today without this feature?"
- "What number would move when this feature is complete?"

**When unsure about Effort**
- "Can I get a rough estimate from an engineer? If not, mark as [TBD]."
- "Have we built something similar before?"
- "Are there external service dependencies or impact on existing code?"

**When unsure about Strategic Fit**
- "If I summarize this period's strategy in one sentence, is this feature aligned with it?"
- "Could I answer 'why are we doing this now?' if asked by leadership?"

---

### Step 3｜Place in Matrix and Classify

Place items in the 4-quadrant Impact × Effort matrix, then overlay Strategic Fit for the final call.

```
                High Impact
                    │
  ┌─────────────────┼─────────────────┐
  │                 │                 │
  │     【Plan】    │  【Prioritize】  │
  │  High Effort    │   Low Effort    │
  │                 │                 │
Low Effort ─────────┼───────────────── High Effort
                    │
  │   【Won't Do】  │  【If Time】     │
  │  High Effort    │   Low Effort    │
  │                 │                 │
  └─────────────────┼─────────────────┘
                Low Impact
```

| Quadrant | Classification | Judgment |
|---|---|---|
| High Impact × Low Effort | **Prioritize** | Begin first |
| High Impact × High Effort | **Plan** | Decompose and design before beginning |
| Low Impact × Low Effort | **If Time Allows** | Fill sprint gaps |
| Low Impact × High Effort | **Won't Do** | Explicitly remove from scope |

**Strategic Fit adjustment rules**

After quadrant placement, adjust with Strategic Fit as follows:

- **"Prioritize" × Strategic Fit Low**: High in the quadrant but misaligned with this period's strategy. Consider downgrading to "Plan" or "If Time Allows." If not downgraded, document why.
- **"Plan" × Strategic Fit High**: Major investment but strategically important. Consider breaking it down for early start, or treat as top candidate for next period.
- **"If Time Allows" × Strategic Fit Low**: Fine to explicitly defer for this period.

Strategic Fit is used not as a final "do/don't" judgment, but as a "now vs. later" timeline judgment.

---

### Step 4｜Output the Priority Table

Output the priority table in the following format:

```markdown
# Priority Matrix

**Date**: YYYY-MM-DD  
**Scope**: [Product name / Feature area]  
**This period's strategic focus**: [State in one sentence. Shared with everyone before evaluation.]

---

## Prioritize (High Impact × Low Effort)
| # | Item | Impact Reason | Effort Estimate | Strategic Fit | Notes |
|---|---|---|---|---|---|
| 1 | | | | High / Low | |

## Plan (High Impact × High Effort)
| # | Item | Impact Reason | Effort Estimate | Strategic Fit | Decomposition Approach |
|---|---|---|---|---|---|
| 1 | | | | High / Low | |

## If Time Allows (Low Impact × Low Effort)
| # | Item | Strategic Fit | Notes |
|---|---|---|---|
| 1 | | High / Low | |

## Won't Do (Low Impact × High Effort)
| # | Item | Reason |
|---|---|---|
| 1 | | |

---

## Recommended Action Order
1. [Item name] — [One-line reason]
2. [Item name] — [One-line reason]

## Items Requiring Strategic Fit Confirmation
- [Item name]: [What needs to be confirmed] → Confirm with: [Owner / meeting]

## Pending / TBD
- [Item name]: [What needs to be confirmed to evaluate]
```

---

### Step 5｜Prepare for Sharing

After outputting the matrix, confirm the following:

- **Items in the "Won't Do" quadrant must be explicitly communicated**. Don't remove them silently—record "we decided not to do this."
- **Items with [TBD] Effort need an engineer confirmation action**.
- **Items in the "Plan" quadrant—consider if they can be decomposed**.
- **Items with [TBD] Strategic Fit need leadership confirmation first**. Aligning on strategic assumptions before seeking priority consensus prevents later reversals.

---

## Notes

- **Don't decide by numbers alone**. Impact × Effort × Strategic Fit is a decision support tool. Dependencies, timing, and organizational capacity need separate consideration.
- **Confirm Effort with engineers**. PdM-only estimates frequently diverge from reality.
- **Confirm Strategic Fit with leadership**. A PdM's judgment of "strategically important" may differ from leadership's priorities. Aligning on evaluation axis definitions with leadership upfront lowers the cost of later alignment.
- **Revisit regularly**. Priorities are not fixed. When strategy changes, so do Strategic Fit assessments.

---

## Reference: Common Failure Patterns

**Failure ① Everything ends up High Impact**  
Symptom: "Everything is important"—everything gets rated High.  
Fix: Force ordering with "If you had to choose just one of these, which would it be?" Use relative evaluation.

**Failure ② Effort is underestimated**  
Symptom: "Probably done in a week" turns into two months.  
Fix: Always get a rough estimate from an engineer. Default uncertain items to "High Effort."

**Failure ③ Not deciding "Won't Do"**  
Symptom: A matrix is created but everything is "doing."  
Fix: Explicitly stating "Won't Do" is one of the most important purposes of this matrix.

**Failure ④ Strategic Fit used retroactively**  
Symptom: Priorities are set with Impact × Effort, then leadership says "this doesn't align with this period's direction" and everything gets overturned.  
Fix: Define the Strategic Fit evaluation axis with all stakeholders at the start of matrix creation. Begin evaluation only after sharing "what is the focus this period?"

**Failure ⑤ Ignoring dependencies**  
Symptom: A and B are evaluated independently; A is rated High, but A actually can't be built until B is done.  
Fix: During list preparation, check "does this depend on anything else?" Reflect dependencies in the recommended action order.
