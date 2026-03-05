---
name: Design Thinking
category: meta-cognitive
description: "Use when facing ambiguous problems, building for human users, or when the obvious solution might not be the right one. Teaches human-centered problem solving through deliberate empathy, divergent/convergent thinking, and iterative reframing."
---

# Design Thinking

## Overview

Design thinking is the discipline of solving the *right* problem before solving it *right*. Most agents jump straight to solutions. This skill forces you to widen your understanding of the problem, sharpen it into a precise framing, then — and only then — generate and evaluate solutions.

The core mechanism is the **Double Diamond**: two cycles of diverge-then-converge. The first diamond finds the right problem. The second finds the right solution.

## When to Use

**Activate this skill when:**
- The problem is ambiguous or could be interpreted multiple ways
- Real humans are affected by the outcome
- You're building something new rather than fixing something broken
- The "obvious" solution feels too easy — you haven't examined alternatives
- A stakeholder says "build X" but you sense the underlying need might be different
- Multiple valid approaches exist and you need to choose wisely

**Do NOT use when:**
- Debugging a specific error (use systematic debugging)
- The task is well-defined and purely technical (e.g. "add a column to this table")
- You're in pure execution mode against an already-validated plan
- Speed matters more than getting the framing right

**Composes with other skills:**
- **First Principles** — use during the Define phase to strip away assumptions
- **Systems Thinking** — use during Discover to map interconnections and feedback loops
- **Structured Brainstorming** — use during Develop to generate more and better ideas
- **Critical Evaluation** — use during Deliver to stress-test your recommendation

## The Double Diamond

```
    DISCOVER          DEFINE           DEVELOP          DELIVER
   (diverge)        (converge)       (diverge)        (converge)
       /\              /                 /\              /
      /  \            /                 /  \            /
     /    \          /                 /    \          /
    /      \        /                 /      \        /
   /        \      /                 /        \      /
  /          \    /                 /          \    /
 /            \  /                 /            \  /
/              \/                 /              \/

 [----Right Problem----]         [----Right Solution----]
```

### Phase 1: Discover (Diverge)

**Goal:** Widen your understanding of the problem space. Resist the urge to narrow.

**Mode:** Expansive. Ask questions, don't answer them yet.

**Techniques:**
- **Stakeholder mapping** — who is affected? Who has influence? Who gets overlooked?
- **Assumption listing** — write down everything you're assuming. Every assumption is a hypothesis to test.
- **"5 Whys"** — ask "why does this matter?" five times to reach the root need
- **Context gathering** — what has been tried before? What's the environment? What constraints exist?
- **Analogous exploration** — who else has solved a similar problem in a completely different domain?

**Gate:** You can articulate **3+ distinct framings** of the problem. If you can only see one framing, you haven't discovered enough. Go wider.

### Phase 2: Define (Converge)

**Goal:** Synthesize your discoveries into a single, sharp problem statement.

**Mode:** Selective. You're narrowing from many framings to the one that matters most.

**Techniques:**
- **"How Might We" reframing** — convert problems into opportunities: "How might we [verb] so that [user] can [outcome]?"
- **Empathy mapping** — use the Empathy Protocol below to ground the problem in a real person's experience
- **Prioritize by impact** — which framing, if solved, would create the most value for the most affected people?
- **Kill weak framings** — explicitly discard framings and state why

**Gate:** A crisp problem statement that names **the user**, **their need**, and **the insight** that makes this framing compelling. Format: "[User] needs [need] because [insight]."

**Reframing checkpoint:** Before moving on, ask yourself: "Is this the problem worth solving, or just the problem I noticed first?" If you're uncertain, return to Discover.

### Phase 3: Develop (Diverge)

**Goal:** Generate many possible solutions. Quantity over quality. No evaluation yet.

**Mode:** Generative. Say "yes, and" to every idea. Defer judgment.

**Techniques:**
- **Quantity target** — aim for 8+ distinct ideas before evaluating any of them
- **Cross-domain inspiration** — "how would [a game designer / a hotel concierge / a kindergarten teacher] solve this?"
- **Constraint removal** — "if we had unlimited time/money/skill, what would we build?" Then work backward
- **"What would the user wish for?"** — the naive, magical solution often reveals the real value
- **Inversion** — "how would we make this problem *worse*?" Then reverse those ideas

**Gate:** **5+ distinct solution directions** that differ meaningfully in approach, not just in detail. If your ideas are all variations of the same approach, you haven't diverged enough.

### Phase 4: Deliver (Converge)

**Goal:** Select the best approach and articulate why.

**Mode:** Evaluative. Apply judgment deliberately.

**Techniques:**
- **Desirability / Feasibility / Viability scoring** — for each solution, rate: do people want it? Can we build it? Is it sustainable?
- **"Kill your darlings"** — be willing to drop the idea you're most attached to if it doesn't score well
- **Prototype thinking** — what's the cheapest way to test whether this solution works?
- **Tradeoff articulation** — state what you're gaining and what you're giving up with your recommendation

**Gate:** A **clear recommendation** with stated tradeoffs, a rationale grounded in the Define phase's problem statement, and a lightweight plan for validating the approach.

## The Empathy Protocol

LLMs simulate empathy through pattern matching. This protocol turns simulated empathy into structured insight.

**Do this during the Define phase — don't skip it.**

1. **Name the person.** Not "users" — a specific type of person. Give them a role, a context, a day. "A first-time founder pitching investors next week" is better than "startup users."

2. **Walk their journey.** Step by step, from the moment they encounter the problem to the moment it's resolved (or they give up). Don't skip steps.

3. **Label emotions at each step.** Not generic emotions — specific ones. "Anxious because they don't know if this is normal" is better than "frustrated." Ask:
   - What are they **thinking** at this step?
   - What are they **feeling**?
   - What are they **doing** (actual behavior, not ideal behavior)?
   - What are they **saying** (or not saying)?

4. **Find the highest-friction moment.** Where does the journey break down, slow down, or create the most anxiety? This is usually where the real opportunity is.

5. **Ask the right question.** Not "what feature solves this?" but "what would make this person's day?" The answer is often simpler and more human than a feature.

## Anti-Patterns

These thoughts mean you're skipping the process. Stop and course-correct.

| Thought | Reality |
|---------|---------|
| "The user just needs X" | Have you verified that, or are you projecting? Run the Empathy Protocol. |
| "This is straightforward" | Straightforward problems don't feel ambiguous. If it felt ambiguous enough to trigger this skill, it isn't straightforward. |
| "I already know the solution" | Then Discover will be quick. Do it anyway — you'll either confirm your intuition or find something better. |
| "Let me jump to solutions" | That's Develop. You haven't passed the Define gate yet. |
| "Users feel frustrated" | That's a platitude. *Which* users? *What kind* of frustration? At *which moment*? |
| "We should do what [competitor] does" | Why do they do it? Does their context match ours? What's the principle underneath? |
| "There's only one way to frame this" | There are always multiple framings. You stopped looking too early. Return to Discover. |

## Process Integrity

**Do not skip phases.** The most common failure mode is jumping from Discover straight to Develop — skipping Define entirely. This produces creative solutions to the wrong problem.

**Do not merge diverge and converge.** When you're in a diverge phase, do not evaluate. When you're in a converge phase, do not generate new options. Separating these modes is the entire point.

**Iterate when needed.** The Double Diamond is not strictly linear. If the Define phase reveals you misunderstood the problem space, return to Discover. If Develop produces nothing promising, revisit Define — you may have framed too narrowly.

**Scale to the problem.** A small, contained problem might need 5 minutes across all four phases. A major product decision might need hours. The process is the same; the depth scales with stakes.

## Composability

This skill is one layer in a thinking stack. It works alone but becomes more powerful combined:

- Load **First Principles** alongside this skill to strengthen the Define phase
- Load **Systems Thinking** to enrich Discover with feedback loops and second-order effects
- Load **Structured Brainstorming** to supercharge the Develop phase with creative frameworks
- Load **Critical Evaluation** to sharpen Deliver with rigorous assessment

These skills are additive. They don't conflict — they each amplify a different phase of the diamond.
