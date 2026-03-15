---
name: pre-build-research
description: "Mandatory research protocol before any significant build task. Ensures user needs are understood, best-in-class examples are studied, and tech decisions are justified BEFORE writing code. Use when: receiving a build request, starting a new feature, or choosing a tech stack."
---

# Pre-Build Research Protocol

## When to Use

Before ANY significant build task. "Significant" = more than a quick script or config change. If you're about to create a new file, deploy something, or build a feature, run this first.

## When NOT to Use

- Quick bug fixes where the solution is clear
- Config changes or minor edits
- Tasks where the user has already specified the exact implementation

## Why This Exists

The mistake ledger shows a pattern: jumping straight to code without understanding who the user is, what they need, or what "great" looks like. Results:
- Static HTML dashboard when the user needed real-time React
- Wrong tech stack choices that needed full rebuilds
- Features that solved the wrong problem

The code is the LAST thing, not the first.

## The Protocol (5 steps, ~10-15 minutes)

### Step 1: Understand the User (2 min)

Answer these before touching code:

- **Who is this for?** (A CEO checking on their phone? A team reviewing metrics? A customer onboarding?)
- **What problem are they solving?** (Not "what did they ask for" but "what do they NEED")
- **When/how will they use it?** (Mobile? Desktop? While doing other things? Once a day or real-time?)
- **What would make them say "wow"?** vs "yeah, that works"

Write answers in a scratch file or TASKS.md. If you can't answer confidently, ask.

### Step 2: Find Best-in-Class (5 min)

Before building, find the 3 best existing examples of what you're about to build:

1. Search for "best [thing you're building]" — real products, not tutorials
2. For each example, note: What makes it great? What's the core insight?
3. Screenshot or bookmark the best one as your north star

If you can't find 3 examples, you haven't searched hard enough. Everything has been built before in some form.

The bar: "Can I find a better example of this anywhere in the world? If yes, I'm not done."

### Step 3: Choose the Stack (3 min)

Decision framework:

1. **Check what's already in the repo.** Existing patterns > new experiments. If there's a Next.js project already, use Next.js.
2. **Default to the quality stack, not the fast stack:**
   - Web apps → React/Next.js (not static HTML)
   - APIs → whatever the team already uses
   - Dashboards → real-time by default (Supabase subscriptions, WebSocket, SSE)
   - Bots → Docker containers with health checks
3. **Speed is not the metric. Quality is.** A 2-hour build that makes the stakeholder say "wow" beats a 20-minute build that needs a redo.
4. **Document the decision:** Write a 1-2 sentence justification for your stack choice. "I chose X because Y." If you can't justify it, you haven't thought about it.

### Step 4: Define Success Criteria (2 min)

Before writing code, write down:

- **Must have:** What does "done" look like? (Specific, testable)
- **Wow factor:** What would elevate this from "works" to "best anyone has done"?
- **Anti-goals:** What are you explicitly NOT building? (Prevents scope creep AND gold-plating the wrong thing)

### Step 5: Brief Check (1 min)

Read back your notes from steps 1-4. Ask yourself:

- "If the best engineer in the world were building this, would they make the same choices?"
- "Am I building what the user needs, or what's fastest to ship?"
- "Is there anything I'm assuming that I should verify first?"

If any answer gives you pause, go back and fix it before writing code.

## Output Template

Save this to `TASKS.md` or a scratch file before building:

```markdown
## Pre-Build Brief: [Feature Name]

**User:** [who]
**Problem:** [what they need, not what they asked for]
**Context:** [when/how they'll use it]

**Best-in-class examples:**
1. [Example] — [why it's great]
2. [Example] — [why it's great]
3. [Example] — [why it's great]

**Stack:** [choice] — [1-2 sentence justification]

**Success criteria:**
- Must: [specific, testable]
- Wow: [what elevates it]
- Anti-goals: [what we're NOT building]
```

## Integration with Core Skills

This protocol fits between the routing step and the code-craft skill:

1. `core-skills/ROUTING.md` → identifies this is a build task
2. `skills/pre-build-research/SKILL.md` → THIS: research, understand, decide
3. `skills/code-craft/SKILL.md` → now build it

## Anti-Patterns

- **"I'll figure it out as I go"** — No. Understand first, then build.
- **"The user asked for X so I'll build X"** — Users describe problems. You propose solutions. Think beyond the literal request.
- **"Static HTML is faster"** — Faster to ship, slower to redo. Pick the right tool.
- **Skipping step 2 because "I know what good looks like"** — You probably don't. Find the examples. Humility prevents mediocrity.
