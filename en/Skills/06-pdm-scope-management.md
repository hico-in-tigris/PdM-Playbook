# Skill 6｜Scope Management

## Purpose of This Skill

Organize the scope of a release or development cycle using **Must / Should / Could / Won't** (the MoSCoW method), and create a state of clear, aligned agreement on "what we will do and what we won't."

**Input**: List of features / requirements, or a priority matrix (output from Skill 5)  
**Output**: Scope definition table + Won't list (explicit out-of-scope items)

---

## Steps

### Step 1｜Confirm Prerequisites Before Scoping

Before defining scope, confirm the following:

- **When is the target release?** (Deadline / sprint duration)
- **How much resource is available?** (Number of engineers / weeks of capacity)
- **Is there a result from Skill 5 (Priority Matrix)?** (Use it as the foundation if it exists)

If resources are unknown, confirm "how many weeks and people are working on this release?" before proceeding.

---

### Step 2｜Classify Each Item

Classify each item in the list into Must / Should / Could / Won't based on the following criteria:

```
Must (required)
  Must be delivered in this release.
  Without this, the release itself loses its meaning.
  → Target: within 50–60% of capacity.

Should (important)
  Would like to include, but not as absolute as Must.
  Will create significant value if in the release.
  → Target: Must + Should within 80% of capacity.

Could (nice to have)
  Include if there's room. Release works without it.
  → Fill in sprint slack.

Won't (not this time)
  Explicitly excluded from this scope.
  Includes "might do in the future, but not this release."
  → Stating this explicitly is the core of scope management.
```

**Questions when unsure how to classify**

- When considering placing something in Must: "Can we really not release without this? Are you sure?"
- When unsure between Should / Could: "Which of these would users ask about first after release?"
- When hesitant to put something in Won't: "What problem does deciding not to do this create? If nothing, Won't is fine."

---

### Step 3｜Load Check on Scope

After classification, verify that the Must volume is realistic given available resources:

```
Total Must effort ≦ Available capacity × 0.7
```

The 0.7 factor is for buffer. Unexpected problems, reviews, and revisions are guaranteed to occur.

If Must is too large, address in this order:

1. **Consider downgrading Must to Should** ("Is this really a Must?")
2. **Consider if anything in Must can be decomposed** ("Can we deliver minimum value with a smaller implementation?")
3. **Adjust the release date** (last resort)

---

### Step 4｜Output the Scope Definition Table

Output the scope definition table in the following format:

```markdown
# Scope Definition｜[Release Name / Sprint Name]

**Date**: YYYY-MM-DD  
**Target Release**: [Release name / version]  
**Planned Release Date**: YYYY-MM-DD  
**Estimated Capacity**: [N engineers × N weeks]

---

## Must (Required)
Deliver in this release without exception.

| # | Item | Reason | Effort Estimate |
|---|---|---|---|
| 1 | | | |

## Should (Important)
Include if possible. Prioritize if capacity allows.

| # | Item | Reason | Effort Estimate |
|---|---|---|---|
| 1 | | | |

## Could (Nice to Have)
Include if there's room. Release works without it.

| # | Item | Notes |
|---|---|---|
| 1 | | |

## Won't (Not This Time)
Not included in this scope. State the reason explicitly.

| # | Item | Reason | Future Consideration |
|---|---|---|---|
| 1 | | | |

---

## Scope Alignment Memo
- Alignment date:
- Agreed by:
- Next review scheduled:
```

---

### Step 5｜Make the Won't List Explicit

The Won't list is not just a "trash bin for things that didn't make it in." Always communicate the following:

- **Write the reason why it's not being done this time**. Without a reason, the debate "why isn't this in?" will resurface later.
- **Recommend sharing with stakeholders in advance**. "I thought this was included but it's not" expectation misalignment is most costly when discovered right before release.
- **Won't does not mean "never do"**. It means "out of scope for this release." Keep the door open for future consideration.

---

## Notes

- **Keep Must small**. The moment "everything is Must" happens, scope management loses its meaning. Restrict Must to genuinely essential items only.
- **Don't be afraid of Won't**. Protecting scope is protecting the project. Be prepared to clearly explain the reasoning behind Won't items.
- **Scope changes**. It's fine to revisit a scope that was once decided if new information comes in. However, make changes explicitly and communicate them to stakeholders.

---

## Reference: Common Failure Patterns

**Failure ① No distinction between Must and Should**  
Symptom: "Everything is Must" / "Everything is important."  
Fix: Use "Would we cancel the release without this?" as the Must standard. Only items you can say YES to are Must.

**Failure ② Not creating a Won't list**  
Symptom: Things that didn't make the scope silently disappear. Later: "whatever happened to that?"  
Fix: Always make Won't explicit. Writing "not doing this time" aligns stakeholder expectations.

**Failure ③ Continuously adding to scope after it's set (scope creep)**  
Symptom: "Can you add this too?" accumulates, Must keeps growing.  
Fix: When adding something, remove something as a pair. Keep total scope volume constant.
