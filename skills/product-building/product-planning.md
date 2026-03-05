---
name: Product Planning
category: product-building
description: "Use before building any new feature, product, or significant change. Produces a plan document through competitive research, first principles, user empathy, journey mapping, edge cases, and pre-mortems. The plan is the product. Load this before writing any code."
---

# Product Planning

## Overview

The plan is the product. A great plan prevents bad builds. A bad plan guarantees rework. The most expensive line of code is the one that solves the wrong problem.

Your default is to skip this. You read "build auth" and start coding because you feel like you understand the task. But understanding a task and specifying it are completely different. Understanding means you could describe it. Specifying means a different agent or developer could execute from your document with no additional questions. That's the bar.

This skill produces a plan document before any code is written. It forces the implicit decisions to the surface where they can be evaluated, challenged, and validated.

## When to Use

- Building a new feature or product
- Significantly changing an existing feature
- Any task that will take more than an hour to build
- When someone says "build X" and you haven't specified what X means in detail
- When you catch yourself about to start coding without a written plan

**Scale to the task.** A 30-minute bug fix doesn't need a 6-section plan document. A 1-paragraph scope statement might be enough. A major feature needs the full process. Match the depth of planning to the stakes of the work.

**Do NOT use when:**
- The task is purely technical with a clear, known solution (add a column, fix a typo, update a dependency)
- You already have a validated plan and the task is execution

## The Planning Process

Six steps. Each one surfaces decisions that would otherwise be made implicitly (and often wrong) during coding.

### Step 1: Competitive Research

Before designing anything, study what the best products in the world do for this problem.

- **Find 2-3 products that solve this problem well.** Name them specifically. Don't just say "competitor apps." Say "Linear does X, Notion does Y, Figma does Z."
- **What do they nail?** Study the specific interactions, flows, and design decisions that make their solution great.
- **Where do they fall short?** What do real users complain about? What's missing?
- **Search for real user voices.** Reddit threads, forum posts, Twitter complaints, support tickets, app reviews. What are actual people saying about this problem? This is free user research. Use it.
- **What can we borrow, improve, or do differently?** Synthesize: "We're borrowing X from Linear because it solves the core problem well. We're improving Y because their approach doesn't work for our use case. We're doing Z differently because our users need something they don't offer."

The goal: build on insight, not on your training data's most common pattern.

### Step 2: First Principles Check

Now set competitors aside. What are the fundamental truths about this problem?

- **What job is the user hiring this feature to do?** Use the JTBD format: "When [situation], they want to [motivation], so they can [outcome]." This strips away feature thinking and reveals the actual need.
- **Is this a painkiller or a vitamin?** Painkillers solve urgent problems people actively seek solutions for. Vitamins are nice-to-haves people can live without. Build painkillers first.
- **How do our specific constraints change the approach?** Team size, tech stack, timeline, existing architecture. The best-in-class approach might not be the right approach for us right now. What would we build if we could only spend 2 weeks on it?
- **What would we build from scratch?** If we ignored all existing solutions and only knew the problem, what would the ideal solution look like? This often reveals that the "obvious" approach is just the most common one, not the best one.

### Step 3: User Empathy and Journey Mapping

**Name a specific user.** Not "users." A person with a role, a context, a day. "A marketing manager who just launched their first email campaign and is checking results for the first time" activates concrete reasoning. "Users checking analytics" does not.

**Map their complete journey:**

1. **Trigger:** What makes them need this feature right now? What were they doing before?
2. **Entry:** How do they find/access this feature? What's their first impression?
3. **Core action:** What's the main thing they're trying to do? Walk each step.
4. **Magic moment:** What's the earliest point they get value? Can they reach it in under 60 seconds?
5. **Completion:** What does success look like? How do they know they're done?
6. **Return:** Why would they come back? What brings them to this feature again?

**At each step, name the emotional state.** Not "frustrated" (that's a platitude). "Anxious because they don't know if the campaign actually sent" or "Relieved because the open rate is above their benchmark." Specific emotions grounded in the situation.

**Find the highest friction point.** Where does the journey break down, slow down, or create confusion? This is usually where the real opportunity is.

**Use the Mom Test lens.** Don't plan based on what users would say they want ("I'd love a dashboard with..."). Plan based on what they actually do. Past behavior over future predictions. "When did you last check campaign analytics? What did you do? What was confusing?" This produces real signal.

### Step 4: Define Scope and Edge Cases

**What's in scope for v1?** List the specific features and behaviors. Be explicit.

**What's explicitly out of scope and why?** This is as important as what's in. "We're not building bulk import in v1 because it affects <5% of users and adds 2 weeks. We'll revisit if users request it." Naming what you're cutting and why prevents scope creep and shows intentional trade-offs.

**Edge cases to specify:**

| Category | Examples |
|----------|---------|
| Data states | Empty, sparse (1-2 items), dense (1000+ items), missing fields, malformed data |
| User states | First-time user, returning user, power user, admin, unauthenticated, expired session |
| Error states | Network failure, timeout, server error, validation failure, rate limit |
| Interruptions | User navigates away mid-process, browser refresh, concurrent editing, duplicate submission |
| Boundaries | Maximum file size, maximum items, character limits, permission boundaries |

**For each edge case, specify the expected behavior.** Not "handle gracefully." What actually happens? "If the network fails during save, show a toast with 'Changes couldn't be saved. They're stored locally and will sync when you reconnect.' Auto-retry every 30 seconds."

### Step 5: Pre-Mortem

"It's 3 months later and this feature failed. Nobody uses it. Write the post-mortem."

This reframing activates more honest thinking than "what could go wrong?" People are better at explaining past failures than predicting future ones.

**What's the most likely reason it failed?** This is the #1 risk to mitigate right now. If you can only address one risk, address this one.

**What's the second most likely reason?** Often a completely different category of failure (technical vs. product vs. adoption).

**For each failure mode:** What would we do now, before building, to prevent it? If we can't prevent it, how do we detect it early?

Common failure categories to consider:
- **Wrong problem:** We built the feature nobody needed. (Research gap.)
- **Right problem, wrong solution:** We understood the need but the implementation didn't serve it. (Journey mapping gap.)
- **Adoption:** We built it but nobody found it or understood it. (Discovery/onboarding gap.)
- **Technical:** It's too slow, unreliable, or breaks at scale. (Edge case gap.)
- **Scope:** We tried to build too much and shipped nothing well. (Prioritization gap.)

### Step 6: Write the Plan Document

Everything above feeds into a single document. This is the output of the planning process. Scale the depth to the task size.

**The plan document template:**

```
## Problem Statement
[JTBD format] When [situation], [user] wants to [motivation], 
so they can [outcome].

[1-2 sentences on why this matters now and what happens if we 
don't solve it.]

## Research
Best in class: [product A] does [X], [product B] does [Y].
Real user signal: [what people actually say about this problem].
Our approach: borrowing [X], improving [Y], doing [Z] differently 
because [reason].

## User Journey
[Step-by-step journey with emotional states at each step.]
Magic moment: [earliest value point].
Highest friction: [where it breaks down].

## Scope
**In v1:** [explicit list]
**Out of v1:** [explicit list with reasons]

## Edge Cases
[Table of edge cases with expected behavior for each]

## Technical Approach
[High-level architecture and key decisions. Answer "what and why,"
leave "how" to implementation. Name the 2-3 biggest technical 
decisions and the reasoning behind each.]

## Pre-Mortem
1. [Most likely failure mode] → [mitigation]
2. [Second most likely] → [mitigation]

## Success Criteria
[Specific, measurable outcomes. Not "users like it" but "40% of 
new users complete onboarding in the first session."]
```

Not every section needs equal depth. A small feature might have a 2-line problem statement and a 5-row edge case table. A major feature might have a full user journey with 10 steps and emotional states. Scale to the stakes.

## What Great Planning Looks Like

**Amazon's press release for Kindle** started with: "Readers deserve access to any book, in any language, in 60 seconds." Every feature decision traced back to this single statement. The press release format forced customer obsession before a single line of technical planning.

**Shape Up's appetite framing:** "This is worth 2 weeks of effort" is a better starting point than "how long will this take?" It forces scope discipline. If the plan can't fit in the appetite, cut scope, don't extend time. The best plans have a clear appetite: how much is this problem worth solving right now?

**The Mom Test in practice:** "Would you use a feature that does X?" is worthless data (everyone says yes to be polite). "Tell me about the last time you dealt with this problem. What did you do? What was annoying about it?" is gold. Great plans reference real user behavior, not hypothetical preferences.

**The pattern:** Great plans start with the customer, not the technology. They specify the problem before the solution. They name what they're cutting, not just what they're building. They predict how they'll fail and plan to prevent it.

## AI Planning Traps

These thoughts mean you're about to plan badly. Catch them.

| Thought | Reality |
|---------|---------|
| "I understand the task, I'll start building" | Understanding is not specifying. Can another agent execute from your plan alone? If not, write more. |
| Listing features without mapping the journey | Features without user context are guesses. How does the user get here? What are they feeling? Map the journey first. |
| "Handle errors gracefully" | What does that mean specifically? Name the error. Name the behavior. Name the message the user sees. |
| Skipping competitive research | "I know how to build this" is not the same as "I know what the best version of this looks like." Research first. |
| Happy-path-only planning | If your plan doesn't address empty states, errors, edge cases, and failure modes, it's a wishlist, not a plan. |
| No pre-mortem | You're optimistic by default. Force the pessimism. "This failed. Why?" catches risks that confidence misses. |
| Overplanning a small task | A 30-minute fix needs a 1-paragraph scope, not a 6-section document. Scale the planning to the stakes. |
| Planning without real user signal | If you haven't searched for what real users say about this problem, your plan is based on assumptions, not evidence. |

## Composability

This skill defines what to build and why. It pairs with other skills:

- Load **UI/UX Design Sense** after planning to define how it should look and feel. The plan defines the what. UI/UX defines the how-it-looks.
- Load **Critical Evaluation** (meta-cognitive) to stress-test your plan before building. Pre-mortem the plan itself. Steel-man the alternative approaches you rejected.
- Load **First Principles** (meta-cognitive) during step 2 to strip assumptions from your problem framing.
- Load **Design Thinking** (meta-cognitive) to enrich step 3 with deeper empathy protocols and the Double Diamond diverge-converge process.
- Load **Systems Thinking** (meta-cognitive) when the feature touches multiple interconnected parts of the product. Map the feedback loops before building.
