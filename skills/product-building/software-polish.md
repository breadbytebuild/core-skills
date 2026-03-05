---
name: Software Polish
category: product-building
description: "Use after building any feature, component, or significant change. Automatically reviews your own work through five lenses before delivering, catching the issues the human would catch on first look. Turns 'it works' from the finish line into the midpoint."
---

# Software Polish

## Overview

"It works" is the midpoint, not the finish line. Your default is to declare done when the code runs and the feature functions. Then the human looks at it and immediately sees: the empty state says "No data," the error message says "An unexpected error occurred," the button says "Submit," the mobile layout is broken.

You already know these are problems. If someone asked "is this empty state good?" you'd say no. The issue isn't knowledge. It's that you never step back to look at your own work. You build forward and never turn around.

This skill makes you turn around. Every time.

## When to Use

- After building any feature, component, or significant change
- Before delivering to a stakeholder
- Before shipping autonomously
- Before declaring "done" on anything with a user-facing element

**NOT during building.** Polish after, not during. Polishing while building slows construction and fragments focus. Build it, then review it.

**Scale to the task.** A 5-line CSS fix gets the Quick Polish Checklist. A major feature gets the full five-lens pass. Match the review depth to the stakes.

## The Polish Loop

```
BUILD → POLISH PASS 1 (always) → DELIVER or CONTINUE
                                        ↓
                              [Autonomous only]
                              Found real issues?
                              Yes → Fix → POLISH PASS 2 (final) → SHIP
                              No → SHIP
```

**Building for a human stakeholder:** One polish pass, then deliver. Catch the obvious stuff so the human's feedback is about product direction, not "you forgot the loading state."

**Building autonomously:** One mandatory pass. If it finds real issues (not nitpicks), fix them and do one final pass. Two passes maximum, then ship.

**The loop limit is non-negotiable.** Two passes max for autonomous work, one for stakeholder delivery. Gains plateau after 2 iterations, and self-feedback after that point often degrades rather than improves quality. Ship a good product. Don't polish a perfect one forever.

### What counts as a "real issue" worth a second pass

**Real issues (fix and re-review):**
- Missing states (loading, empty, error not implemented)
- Broken functionality (a flow that doesn't actually work end-to-end)
- Security gaps (exposed secrets, missing auth checks)
- The output doesn't match the original goal

**Nitpicks (note but don't re-review):**
- Slightly better wording for a label
- Spacing that's 4px off
- A variable name that could be clearer
- An animation that could be smoother

If your first pass only found nitpicks, fix them inline and ship. Don't run a second full pass for minor improvements.

## The Five Lenses

Run all five in a single review pass. Not five separate reviews. One pass, five perspectives.

### Lens 1: Goal Alignment

Did you actually build what was asked for?

- **Restate the original goal in one sentence.** If you can't, the goal drifted during building.
- **Compare: what was requested vs. what was delivered.** List any gaps (things forgotten) and any drift (things added that weren't asked for).
- **Check for gold-plating.** Did you add features or complexity nobody requested? Cut them. Build what was asked, not what felt interesting.

Goal drift is the most common silent failure. The agent starts building auth and ends up refactoring the user model. Catch it here.

### Lens 2: Functional Verification

Does it actually work? Not "does the code look right" but "if I use this, does it do the right thing?"

- **Test the happy path end-to-end.** Walk through the full flow as a user would.
- **Test with empty data.** What happens when there are no items? Is there a helpful empty state?
- **Test with an error.** Disconnect the network (mentally or actually). What does the user see? Is it helpful?
- **Test the edge cases from the plan.** If the plan listed specific edge cases, verify each one was handled.
- **If you have browser/preview access, actually look at it.** Screenshots catch things code review doesn't. If you can render a preview, do it.

The question isn't "could this work?" It's "did I verify that it works?"

### Lens 3: Design and UX

Does it look right and feel right?

- **Squint test.** Blur your vision. Can you still tell what's most important? If everything has equal visual weight, the hierarchy is flat.
- **Spacing consistency.** Are values from the spacing scale? Is proximity communicating the right relationships?
- **Visual hierarchy.** Do headings, body, and metadata have distinctly different sizes and weights?
- **Responsive.** Does this work on mobile? Did you actually check, or assume?
- **Removal test.** Go through every visual element. Can you remove a border, shadow, icon, or divider without losing meaning? If yes, remove it.

Load the UI/UX Design Sense skill for the full standards. This lens is the quick check.

### Lens 4: Copy and Communication

Do the words help the user?

| Element | Bad | Good |
|---------|-----|------|
| Button labels | "Submit" | "Create Campaign" (specific to what happens) |
| Error messages | "An error occurred" | "Couldn't save your changes. Check your connection and try again." |
| Empty states | "No data" | "No campaigns yet. Create your first one to get started." + CTA button |
| Confirmation | "Success" | "Campaign created. It'll start sending at 9am tomorrow." |
| Loading text | (missing) | "Loading your campaigns..." or a skeleton that matches the final layout |
| Placeholder text | "Enter text here" | "e.g., Summer Sale Announcement" (show an example) |

Every user-facing string should pass this test: **does it help the user know what happened, what to do next, or what this area is for?** If it doesn't, rewrite it.

### Lens 5: Integration and Fit

Does this fit the rest of the product?

- **Uses existing components and patterns** where they exist, or intentionally upgrades them (per UI/UX Design Sense's "evaluate then match or upgrade" guidance).
- **Consistent with the project's naming conventions, file structure, and code style.** New code shouldn't look like it was written by a different team.
- **Doesn't break existing functionality.** If the change touches shared code, verify that existing features still work.
- **Fits the product's direction.** Not just the current task, but where the product is headed. Will this need to be ripped out in a month?

## Quick Polish Checklist

For smaller tasks that don't warrant the full five-lens review. Five questions, 60 seconds:

1. **Does it do what was asked?** (Goal alignment)
2. **Does it work?** Test it, don't assume. (Functional verification)
3. **Is anything obviously wrong visually?** (Design spot-check)
4. **Are the user-facing words helpful?** (Copy check)
5. **Would I be embarrassed if someone saw this right now?** (Gut check)

If you answer "no" to any of these, fix it before delivering. This is the minimum bar for everything, including small fixes.

## The Autonomous Quality Bar

When building without human oversight, the bar is higher because there's no safety net. Nobody is going to catch your mistakes.

**The standard: "Would a senior engineer approve this PR?"**

- All five lenses pass with no major issues
- Happy path tested plus at least 2 edge cases verified
- User-facing copy is specific and helpful (no generic placeholders)
- Responsive behavior checked (not assumed)
- Existing functionality confirmed not broken

**The honest grade test.** After your polish pass, give yourself a letter grade. If you can't honestly say A-, do another pass. If you're at A- or above after the first pass, ship it.

**Don't lie to yourself.** The temptation is to say "A-" to avoid another cycle. Ask instead: "If Koby looked at this right now, what's the first thing he'd flag?" If you can name something, fix it. If you genuinely can't think of anything obvious, you're at A-.

## What Polish Catches (Before/After)

These are the most common issues that a single polish pass fixes:

| Before Polish | After Polish |
|--------------|-------------|
| Empty state: "No data" | "No campaigns yet. Create your first campaign to start reaching your audience." + CTA |
| Error: "An error occurred" | "We couldn't load your campaigns. This usually means a connection issue. Try refreshing." + Refresh button |
| Button: "Submit" | "Create Campaign" |
| Loading: nothing (content pops in) | Skeleton that matches final layout, 300ms minimum display |
| Mobile: desktop layout squeezed | Single column, adjusted spacing, touch targets 44px |
| Goal: built auth + refactored users | Caught the drift, reverted user model changes, delivered auth only |

Every item in this table is something the agent would catch if it looked. The polish pass makes it look.

## Anti-Patterns

| Pattern | Fix |
|---------|-----|
| "It works, so it's done" | Working is the midpoint. Run the five lenses before delivering. |
| Polish during building | Build first, polish after. Mixing them slows both. |
| Three or more polish passes | Two max. Ship and learn. Infinite polishing is procrastination wearing a quality mask. |
| "I'll polish it later" | You won't. Polish now, before the context leaves your head. |
| Fixing only what you notice | Run all five lenses systematically. The ones you skip are the ones with issues. |
| Grading yourself A- to avoid another pass | Be honest. "What would the human flag first?" If you can name it, fix it. |
| Polishing nitpicks but missing real issues | Check goal alignment and functionality first. Spacing tweaks don't matter if the feature doesn't work. |

## Composability

This skill is the final step in the build cycle:

```
Product Planning  →  plan what to build
UI/UX Design Sense  →  design how it looks
[Agent builds the feature]
Software Polish  →  review, fix, deliver
```

- Load **UI/UX Design Sense** for the design standards used in Lens 3
- Load **Critical Evaluation** (meta-cognitive) for deeper goal-alignment and integration analysis
- Load **Copywriting** (when available) for Lens 4 copy standards
- Load **Product Planning** to compare the output against the original plan in Lens 1
