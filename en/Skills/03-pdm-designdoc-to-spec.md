# Skill 3｜Design Doc → Spec

## Purpose of This Skill

Convert the "What & Why" of a Design Doc into a "How" document that engineers can use directly for implementation.

**Input**: Design Doc (Markdown format)  
**Output**: Spec (Markdown format)

---

## Steps

### Step 1｜Read and Review the Design Doc

When you receive the Design Doc, check it against the following criteria before converting to a spec.

**Confirm before speccing out**

- Are Problem, Goals, and User Story all present? If not, don't begin the spec.
- Are Non-Goals explicitly stated? If absent, confirm them.
- Is UX Flow written? If absent, ask: "Please describe the user's action flow."

### Step 2｜Generate the Spec

Generate the spec using the following template. Transform and elaborate on the information from the Design Doc to fill it in.

```markdown
# Spec｜[Feature / Initiative Name]

**Date**: YYYY-MM-DD
**Corresponding Design Doc**: [Link or title]
**Status**: Draft / Review / Approved

---

## Overview
<!-- Compress the Design Doc's Problem + Goals into one paragraph. Aim for a reader to grasp "what, why, and for whom" within 3 seconds -->
<!-- Format: To solve [problem] for [users], we will implement [feature]. This will improve [outcome]. -->
<!-- Avoid turning this into a Background section — keep background in the Design Doc and lead with the conclusion here -->

## Target Users
<!-- "General users" is not a definition. This affects permission design, UI decisions, and error copy — so be specific -->
- Role / Permissions: <!-- e.g., Logged-in general users / Admin role only / Includes guest users -->
- Usage scenario: <!-- e.g., When creating a monthly report / Immediately after first login / When an error is detected -->
- Technical literacy: <!-- e.g., Non-engineers — avoid jargon / Internal engineers only — technical language is fine -->

## Functional Requirements
<!-- Break down the Design Doc's UX Flow into individual features. Aim for a level of detail where engineers don't need to make judgment calls on their own -->

### [Feature Name 1]

**Overview**
<!-- What this feature does, in one sentence. Make the subject explicit: "When the user does X, the system does Y" -->

**Happy Path**
<!-- Write the normal-case flow in order. Alternating between user actions and system responses makes it clearer for implementers -->
1. User does X
2. System does Y
3. ...

**Edge Cases / Exception Handling**
<!-- Think through "what happens in this case?" before engineers do. Unresolved edge cases discovered mid-implementation turn into spec changes -->
<!-- Minimum checklist: empty input / exceeds limit / user lacks permission / network failure -->
- If X → do Y
- If X is empty → display Y

**Validation**
<!-- Required whenever there is any input UI. "Handle validation properly" is not a spec -->
<!-- For each field, specify: required vs. optional · type · character limit · allowed characters · duplicate check -->

### [Feature Name 2]
(Repeat in the same structure)

---

## Non-Functional Requirements
<!-- These requirements tend to be deferred, but discovering them during implementation causes expensive rework. State them explicitly here; mark anything unknown as [TBD] and move on -->

### Performance
<!-- "Faster is better" is not a requirement. Write concrete numbers engineers can use when making architecture decisions. Start from the threshold at which users would perceive something as "slow" -->
- Response time target: <!-- e.g., Initial page load within 2s, API response within 500ms -->
- Expected peak load: <!-- e.g., 100 req/s normally, 5× during campaigns. Always include any events that could cause sudden spikes -->
- Notes: <!-- e.g., Bulk processing of large datasets → background job approach is acceptable -->

### Security
<!-- "Build it securely" is not a spec. Define exactly who can access what data and to what extent -->
- Authentication / Authorization: <!-- e.g., Logged-in users only / Admin role only / Users can only see their own data -->
- Data sensitivity: <!-- Explicitly state if PII, payment data, or confidential data is involved. If so, also specify masking rules and log exclusions -->
- Other: <!-- e.g., Communicates with external services → HTTPS required -->

### Accessibility
<!-- State "not required" explicitly too. Leaving it vague often turns into a last-minute requirement before release -->
- Compliance level: <!-- e.g., WCAG 2.1 AA / Screen reader support only / Not required (reason: internal admin tool) -->
- Keyboard navigation: <!-- Required / Not required (mouse-only assumed) -->
- Color contrast: <!-- e.g., Follow existing design system / Note any areas requiring individual attention -->

### Supported Environments
<!-- Also decide what happens in unsupported environments (show an error, degrade gracefully, etc.) -->
- Browsers: <!-- e.g., Chrome, Safari, Firefox — latest 2 versions. IE and legacy Edge are out of scope -->
- Devices: <!-- e.g., Desktop only / Mobile support (iOS & Android) / Responsive design -->
- OS: <!-- e.g., No restriction / iOS 16+ and Android 12+ -->
- Behavior in unsupported environments: <!-- e.g., Show a warning banner in unsupported browsers -->

### Availability / Reliability
<!-- This defines the user experience during failures. Errors need design decisions too -->
- Uptime target: <!-- e.g., 99.9% (max ~44 min downtime/month) / Align with existing SLA -->
- Behavior on failure: <!-- e.g., This feature going down must not affect other features / Show error screen with retry prompt -->
- Data loss tolerance: <!-- e.g., Zero (all input must be persisted) / Up to 1 hour acceptable (cache-layer feature) -->

## Out of Scope
<!-- Without explicit "not doing X," engineers make judgment calls and stakeholders form misaligned expectations -->
<!-- Pull from the Design Doc's Non-Goals and always include the reason. The reason makes it easier to push back on scope creep later -->
- X will not be handled (reason: Y)
- X will not be handled (reason: Y)

## UI/UX Spec

**Display State Definitions**
<!-- Define every state. Error state and empty state are the most commonly missed -->
- Default state: <!-- What the user sees on initial load -->
- Loading state: <!-- What to show while fetching data. e.g., spinner / skeleton / nothing -->
- Error state: <!-- Error message copy and whether a retry button is shown -->
- Empty state (no data): <!-- When there is nothing to display. e.g., "No X yet" message + CTA button -->
- Success state: <!-- How to notify the user on completion. e.g., toast for 3 seconds / close modal and return to list -->

**Navigation & Screen Transitions**
<!-- Define how users enter and exit this feature. Ambiguous transitions lead to inconsistency between screens -->
- Entry point: <!-- e.g., "Add" button on the X list screen -->
- Post-completion destination: <!-- e.g., Navigate to X detail screen / Stay on screen and show toast -->
- Cancel behavior: <!-- e.g., Return without confirmation / Show confirmation dialog if there are unsaved changes -->

## Data Spec
<!-- This feeds directly into DB schema and API response design. Write down the constraints you know so engineers aren't starting from scratch -->

**Data Fields**
<!-- List the key fields. You don't need to cover everything — focus on fields with business rules attached -->

| Field | Type | Constraints | Notes |
|---|---|---|---|
| e.g., Title | String | Required / Max 100 chars | Must be unique |
| e.g., Created at | Datetime | Auto-assigned | Not editable by users |

**Data Retention & Deletion**
<!-- Distinguish between data that can be lost and data that must never be lost -->
- Retention period: <!-- e.g., Indefinite / Auto-deleted after 90 days -->
- Deletion method: <!-- e.g., Hard delete / Soft delete (deletion flag) -->
- Deletion side effects: <!-- e.g., Related X records are also deleted / Referenced data is preserved to avoid broken links -->

## Measurement & Logging
**Measurement design must be finalized before release. It's too late to start thinking about it after launch.**

Select from the following four base metrics based on the nature of the feature:

| Metric | Question | Event Example |
|---|---|---|
| Adoption rate | Are users using the feature? | `feature_opened`, `first_use` |
| Retention rate | Are they continuing to use it? | Re-use at 7 and 28 days |
| Completion rate | Are they achieving their goal? | Reached final step of flow |
| Error rate | Where are they getting stuck? | `error_shown`, `retry_triggered` |

Success definition: [metric name] changes from [current value] to [target value]
<!-- If current value is unknown, mark as [TBD]. Pull target value from the Design Doc's Goals -->
Measurement start: within [N] days of release
Qualitative check: interview [N] users within [N] weeks of release

## Open Questions
<!-- Capture anything that couldn't be decided while writing this spec. Don't leave this empty -->
<!-- "Owner" should be the internal decision-maker or engineering lead. "Due" should be before implementation begins -->
| # | Question | Owner | Due |
|---|------|------|------|
| 1 |      |      |      |
```

### Step 3｜Detect Gaps and Request Feedback

After outputting the draft spec, always check the following:

**Checklist**

- [ ] Are edge cases covered?
- [ ] Are display states (loading, error, empty) defined?
- [ ] Are out-of-scope items explicitly stated?
- [ ] Are Open Questions populated with items that need confirmation?
- [ ] Is measurement design included?

**Common omissions**

- No UI definition for error states
- No consideration for permission/role-based visibility differences
- Mobile/desktop support scope undefined
- Impact on existing features unclear

### Step 4｜Output the Final Version

Incorporate feedback and output the final spec in Markdown.  
If the next step (implementation prompt generation) is needed, hand off to Skill 4 (pdm-spec-to-prompt).

---

## Notes

- The reader of the spec is an engineer. Write it as an implementation instruction, not a thinking exercise.
- Never use phrases like "in a good way" or "flexibly." Write in specific states and conditions.
- Mark unknown areas as [TBD] and move forward. Don't write with ambiguity.
