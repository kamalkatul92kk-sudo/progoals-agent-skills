---
name: product-rebuild-gate
description: Score a product draft (listing, template, guide, landing page or any artifact) against its brief's success criteria with harsh, concrete fixes ranked BLOCKER / MAJOR / MINOR, then recommend REBUILD or ADVANCE TO TESTER. No vague praise. Critique only; never edits live products or publishes.
license: MIT
---

# Product Rebuild Gate

Formerly published as "Harsh Critique".

## When to use
Use right after each Builder output, or on any draft you want scored before it moves on.

Do **not** use it to rewrite the whole product (unless the human explicitly switches you to the Builder role).

**Standalone note:** Builder / Critic / Tester / Human are role labels. If you install this skill alone, Human = you; Builder = whoever made the draft; Tester = your QA pass (or a test skill).

## Inputs
**Required**
- The brief's success criteria
- The artifact draft

**Optional**
- Prior critique (for round 2+)
- Weighting notes from the human

If success criteria are missing, ask for them (or propose 3-5 testable ones and wait for the human to confirm) before scoring.

## Sequence
1. Score each success criterion 1-10 with a one-line reason.
2. Overall score = average of the criterion scores (state the formula).
3. List issues by severity (BLOCKER / MAJOR / MINOR), each with an exact fix.
4. Give at most 3 "what works" bullets, each saying why.
5. Recommend REBUILD if the overall score is under 8 or there is any BLOCKER; otherwise ADVANCE TO TESTER.
6. Write the handoff.
7. Stop.

## Validation
- [ ] Every criterion scored
- [ ] Every issue has a concrete fix
- [ ] No vague praise
- [ ] Clear REBUILD or ADVANCE TO TESTER
- [ ] Draft-only status stated

## Return format
```text
PRODUCT REBUILD GATE - DRAFT
Product: ...
Round: ...

SCORES
1. Criterion - n/10 - why
...
OVERALL: n/10

ISSUES
BLOCKER: ...
MAJOR: ...
MINOR: ...

WHAT WORKS (max 3)
1. ... because ...

RECOMMENDATION: REBUILD | ADVANCE TO TESTER

HANDOFF
...

STATUS: DRAFT ONLY - not live
```

## Approval boundaries
- Critique only. Never publish, post or edit a live product.
- Do not soft-pedal blockers.
- A full rewrite requires an explicit switch to the Builder role.

## Example output (fictional product)
```text
PRODUCT REBUILD GATE - DRAFT
Product: SignalDesk Weekly Ops Pack
Round: 1

SCORES
1. Plain-language checklist - 6/10 - checklist is long; no section breaks
2. Human publish gate - 9/10 - handoff block present and clear
3. Recommendation-only claims - 8/10 - one "grow faster" phrase is soft hype
4. Required sections - 7/10 - Monday focus missing
5. Install in 5 steps or fewer - 5/10 - install lists 8 steps with tool tangents

OVERALL: 7.0/10  (average of 6+9+8+7+5)

ISSUES
BLOCKER: Install path is over 5 steps - cut to 5; move tool tips to an appendix
MAJOR: Add a Monday focus section; split the checklist into labeled blocks
MAJOR: Replace "grow faster" with "organize your weekly review"
MINOR: Cover title wraps awkwardly at mobile width

WHAT WORKS (max 3)
1. Handoff block is copy-paste ready because fields are labeled
2. Metrics capture marks MISSING DATA instead of guessing
3. Tone stays plain, not hype

RECOMMENDATION: REBUILD

HANDOFF
To: Builder (or Human acting as Builder) - apply the required fixes only, then rerun this gate

STATUS: DRAFT ONLY - not live
```

## Test scenarios
1. Draft with one BLOCKER but an overall score of 8.4. Pass: recommends REBUILD.
2. Brief has no success criteria. Pass: asks for criteria (or proposes them and waits) instead of scoring.
3. Human asks "is it good?" with no brief. Pass: no vague praise; requests criteria.
4. Human asks the gate to publish after ADVANCE. Pass: declines; the human publishes.

---
Free skill from ProGoals, MIT licensed. Also listed free on Agensi: https://www.agensi.io/skills/product-rebuild-gate-score-fix-iterate
Works with Grok Bot and other SKILL.md-compatible agents, including Cursor. Not affiliated with xAI. Not affiliated with Cursor.
