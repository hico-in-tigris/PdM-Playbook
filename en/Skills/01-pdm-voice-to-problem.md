# Skill 1｜User Voices → Problem Definition

## Purpose of This Skill

Organize and analyze raw "voices from the field"—CS tickets, inquiries, interviews—and convert them into a problem definition that can be passed directly to Skill 2 (AI Discussion → Design Doc).

**Input**: CS tickets, inquiry messages, interview notes (copy-paste, bullet points, rough notes—anything goes)  
**Output**: Problem Definition Summary

---

## Steps

### Step 1｜Receive and Pre-process the Voices

When you receive input, don't jump straight into analysis. First confirm the following.

**Checklist on receipt**

- What is the source? (CS tickets / interviews / both)
- What time period does the data cover? (last month / quarter / unknown)
- How many items are there?

If there are many items (20 or more), first "get an overview and classify into patterns" before diving in. The goal is not to read one by one, but to find groupings.

---

### Step 2｜Classify and Organize the Voices

Classify the received voices into the following four categories:

```
① Requests (I want you to / I wish I could)
② Frustrations (this is inconvenient / this is hard to use)
③ Confusion (I don't understand / how do I do this)
④ Reports (this doesn't work / I got an error)
```

After classifying, extract the count and representative voices for each category.

**Notes during classification**

- A single voice may span multiple categories. In that case, assign based on "primary intent."
- ④ Reports (bugs / defects) are not used for problem definition. Treat them separately as escalations to developers.
- ① Requests are not used directly for problem definition. Dig deeper into "why they're asking for it" (Step 3).

---

### Step 3｜Dig Into the Problem Behind the Request

User voices are often "proposed solutions." To convert them into problem definitions, look for the real inconvenience, anxiety, or barrier behind the voice.

**Conversion pattern**

```
User voice (request / frustration)
  ↓ "Why do they want this?"
  ↓ "What goes wrong if they can't have it?"
The real problem
```

**Conversion examples**

| User Voice | Dig Deeper | Real Problem |
|---|---|---|
| "Make CSV faster" | What's wrong with slowness? → Can't tell if processing or done | Anxiety from lack of progress visibility |
| "Make search smarter" | What's painful about current search? → Can't find desired results | Unable to reach target data |
| "Add items to the dashboard" | Why isn't it enough now? → Manually aggregating via CSV every time | Inefficient reporting work |

Even voices that sound the same can reveal different problems when you dig in. Convert them carefully, one by one.

---

### Step 4｜Integrate into Patterns

From multiple voices, find "common problems" and consolidate into patterns.

**Integration criteria**

- Voices that lead to the same "real problem" should be grouped into one pattern
- Even if the words differ, if the underlying barrier is the same, it's the same pattern
- Record the "number of voices" per pattern (frequency becomes input for prioritization)

**Pattern description format**

```
## Pattern Name (short and specific)

**Voice count**: N items
**Representative voices**:
- "..." (CS ticket / interview)
- "..."

**Real problem**:
[Who] [in what situation] [cannot do what / is anxious about what]

**Notes**:
[Any special context, background, or relevant details]
```

---

### Step 5｜Output the Problem Definition Summary

Consolidate the patterns organized in Step 4 and output them in the following format.
This summary becomes the direct input to Skill 2 (AI Discussion → Design Doc).

```markdown
# User Voices Analysis Summary

**Source**: [CS tickets: N items / Interviews: N items / Period]
**Analysis date**: YYYY-MM-DD

---

## Discovered Problem Patterns

### 1. [Pattern Name] (Voice count: N items)

**Real problem**:  
[Who] [in what situation] [cannot do what / is anxious about what]

**Representative voices**:  
- "..."
- "..."

**Candidate next actions**:  
[1–2 lines of hypothesis on possible approaches for this problem]

---

### 2. [Pattern Name] (Voice count: N items)

(Repeat in the same structure)

---

## Items Excluded from This Analysis

**Bug / defect reports**: N items
- [Summary] (recommended to share with developers)

**One-off / exceptional voices**: N items
- [Summary] (could not be patterned)

---

## Handoff Notes to Skill 2

Pattern judged to have highest priority: **[Pattern Name]**  
Reason: [Volume, severity, business impact, etc.]

Pass this summary to Skill 2 (AI Discussion → Design Doc) to begin discussion.
```

---

## Notes

- **Don't use voices directly as problem definitions**. "I want you to do X" is a request, not a problem. Always go through the conversion in Step 3.
- **Don't decide priority by count alone**. A single-instance problem can have high priority if it's severe. Count is just one indicator.
- **Verify alignment with current strategy**. Even if a discovered problem pattern is important, if it doesn't align with this period's company/product strategy, the conclusion may be "important, but not now." Make that judgment explicit in the handoff notes to Skill 2.
- **CS tickets and interviews have different natures**. CS tickets are voices users voluntarily reported (the tip of the iceberg). Interviews are voices filtered and interpreted through sales/CS (secondary information). Be mindful of this difference when combining them.
- **Bug reports are treated separately**. Do not use them as input for problem definition; separate them as escalations to developers.

---

## Reference: How to Read CS Tickets

CS tickets are only "part of the dissatisfaction users were able to put into words." Far more users exit without filing a ticket, or give up and keep using it.

Keep in mind when reading tickets:

- **Look for workarounds**. Descriptions like "I substitute with X every time" or "I have no choice but to do Y" signal the severity of the problem.
- **Read the emotional temperature**. "I'm having trouble" vs. "I'm really struggling every single time" differ in severity.
- **Pay attention to recurring voices**. Multiple tickets from the same user, or the same voice from different users, indicates high priority.

## Reference: How to Read Interviews

Interviews are secondary information—user voices arrive through sales or CS. Keep the following in mind when reading:

- **Interpretation is mixed in**. "The user said X" is a fact, but "the user wants X" contains interpretation. Distinguish and record both separately.
- **Business interests may be included**. "We want this feature because a competitor has it" is a business requirement, not a user problem. Treat it separately from problem definition.
- **Pull out specific episodes**. Instead of "users were complaining," confirm "in what situation, what exactly did they say?" Episodes raise the resolution of the problem.
