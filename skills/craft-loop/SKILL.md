---
name: craft-loop
description: "Use before delivering ANY project or significant build. The full lifecycle: research the standard, build v1, iterate until excellent, verify end-to-end, ship with evidence."
---

# The Craft Loop — Iterative Excellence

## When to Use
- At the START of any significant build — load BEFORE writing code
- Any time you're building something that will be seen, used, or evaluated by a stakeholder

## When NOT to Use
- Slack messages, status updates, heartbeat checks
- One-line config changes
- Answering a question (this is for BUILDING)

## Quick Reference

Phase 0 (Brief) → Phase 1 (Build v1) → Phase 2 (Iterate) → Phase 3 (Verify) → Phase 4 (Ship)

v1 is never the answer. Keep iterating until it's genuinely great.

---

## Phase 0: Write the Brief

Before writing a single line of code, produce a written brief. No brief = no building.

1. **Name the audience.** "This is for [person/role] who will [action] and needs [outcome] within [context]." E.g., not "my boss" but "a CEO checking their phone between meetings, needing to know if the system is healthy in 5 seconds."

2. **Research what great looks like.** Find the best examples. Note what makes them great with specifics, not abstractions. "Clean UI" fails. "All key metrics visible without scrolling on mobile" passes.

3. **Write the brief:**

```
## Phase 0 Brief: [Project Name]
**Audience:** [one sentence from step 1]
**What great looks like:** [3-5 concrete, checkable bullets]
**Vocabulary check:** [my terms → audience terms for every label/concept]
**First-open test:** [what the audience sees in 5 seconds — if confusing, redesign]
```

The vocabulary check is the most important section. It forces translation from your mental model to the audience's language BEFORE building.

**Companion skills to load:** `skills/deep-research/SKILL.md` for research. `core-skills/skills/product-building/ui-ux-design.md` if it has a UI.

## Phase 1: Build v1

Get the shape right. Don't aim for perfect. v1 exists so you have an artifact to iterate on.

**Companion skills:** `skills/code-craft/SKILL.md` for engineering discipline. Code-craft owns testing — every new script needs a test.

## Phase 2: Iterate (up to 10 passes)

**First iteration — correctness sweep:** Run it. Does it actually work? Trace one happy path and one error path. Fix bugs before judging quality.

**Every iteration:**
1. Compare against the Phase 0 excellence bullets. What's the specific gap?
2. Ask: "What would the stakeholder flag in the first 10 seconds?"
3. Pick the SINGLE biggest improvement. Not a list — the ONE that matters most.
4. If the biggest improvement is genuinely minor → move to Phase 3.
5. If it's real → make it, re-evaluate. Go back to step 1.

**Systems check (after each iteration):** Does it work with related pieces? Is there overlap with existing tools? Would someone know which piece to reach for?

## Phase 3: Verify End-to-End

This is where last-mile failures get caught. Verification owns ONE concept: did you experience the deliverable the way the audience will?

**Walk the full path as the user:**
- URL → open it, look at every section, click every button
- Script → run with real inputs, read the output line by line
- API → make the real call, check the real response
- Cron → trigger once, verify output arrives where it should

**Check the connections:** Most failures happen at integration points. Does data flow end-to-end? Did you wire all the pieces together? (Built monitoring but never connected logging = classic.)

**Run tests:** Run your test suite — all tests must pass.

**Prove it:** Screenshot, curl response, output quote. Evidence, not claims.

**Complete the full task:** Re-read your task list. The PR without the notification is not done.

## Phase 4: Ship with Evidence

```
[Deliverable link/screenshot/output]

Iterations:
- v1: [what was built]
- v2: [what improved and why]
- vN: [final improvements]
Verified: [what was checked on the final version]
```

## Anti-Patterns

- Shipping v1 (iterate!)
- Perfunctory iterations (changing trivial things to satisfy the format)
- Skipping Phase 0 (no standard = "good enough" wins)
- Speed over quality (quality is the metric)
- Listing improvements but fixing none (do, don't analyze)
