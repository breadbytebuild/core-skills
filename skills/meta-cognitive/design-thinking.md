---
name: Design Thinking
category: meta-cognitive
description: "Use when facing ambiguous problems, building for human users, or when the obvious solution might not be the right one. Teaches human-centered problem solving through deliberate empathy, divergent/convergent thinking, and iterative reframing."
---

# Design Thinking

## Overview

Design thinking is the discipline of solving the *right* problem before solving it *right*. Most agents jump straight to solutions. This skill forces you to widen your understanding of the problem, sharpen it into a precise framing, then — and only then — generate and evaluate solutions.

The core mechanism is the **Double Diamond**: two cycles of diverge-then-converge. The first diamond finds the right problem. The second finds the right solution.

## Why This Works

Design thinking isn't arbitrary. Each element exists because of how cognition actually works.

**Separating diverge from converge prevents premature convergence.** When you generate and evaluate simultaneously, your brain's critical faculty kills ideas before they develop. Research on brainstorming consistently shows that separating generation from judgment produces more and better ideas — the inner critic silences the inner inventor. By making diverge and converge explicit modes, you override the default tendency to collapse to the first plausible answer.

**Naming a specific person activates different reasoning than abstractions.** "Users" is an abstraction that lets you project your own preferences. "A sleep-deprived parent checking their phone at 2am while holding a baby" activates concrete, situational reasoning. You start thinking about screen brightness, one-handed interaction, cognitive load — things that never surface when thinking about "users."

**Multiple framings fight confirmation bias.** Once you frame a problem one way, everything you see confirms that frame. Requiring 3+ framings before committing forces you to see the problem from angles your first instinct would have missed. The most valuable framing is almost never the one you thought of first.

**Iteration prevents sunk-cost thinking.** Making it explicit that you can — and should — return to earlier phases means you don't cling to a framing or solution just because you spent time on it.

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

## What Great Looks Like

Following the process is necessary but not sufficient. Here's what separates mechanical design thinking from the real thing.

### The Reframe Is the Breakthrough

Every iconic design thinking outcome is a reframe — a moment where the problem itself changes.

**The slow elevator.** Tenants complained about slow elevators. The obvious solutions: faster motors, better algorithms, new elevators. The reframe: the problem isn't speed, it's boredom. The solution: install mirrors in the lobby. People check their appearance, lose track of time, complaints disappear. Cost: trivial. The problem was never about elevators.

**Airbnb's failing marketplace.** In 2009, Airbnb earned $200/week and was dying. The founders flew to New York and visited listings. The reframe: the problem wasn't the marketplace design, it was the photos — grainy, dark, unappealing amateur shots that made every apartment look terrible. They hired a photographer, replaced the images, and revenue doubled within a week. The problem was never about the platform.

**IDEO's children's toothbrush.** The brief: design a toothbrush for kids. The obvious approach: make an adult toothbrush smaller. Observation revealed the reframe: children have underdeveloped fine motor skills. They don't need *smaller* handles — they need *fatter* ones. The resulting thick-handled brush became the best-selling children's toothbrush in the US for 18 months.

**The pattern:** In each case, the initial problem statement was wrong. The breakthrough wasn't a better solution to the original problem — it was a *different problem entirely*. If your Define phase produces a problem statement that looks exactly like what you started with, you probably haven't reframed enough.

### What Mediocre Looks Like

Mediocre design thinking follows the steps and produces predictable output. You can spot it:

- The "empathy" section lists generic personas that could apply to any project
- The problem statement is a restatement of the original request, not a reframe
- All the solutions are variations on the same approach
- The recommendation feels safe and obvious — no one would argue with it, but no one would get excited either
- The process felt productive but produced no surprises

If nothing surprised you during the process, you didn't go wide enough.

## The Empathy Protocol

LLMs simulate empathy through pattern matching. This protocol turns simulated empathy into structured insight.

**Do this during the Define phase — don't skip it.**

1. **Name the person.** Not "users" — a specific type of person. Give them a role, a context, a day. "A sleep-deprived parent checking their phone at 2am while holding a baby" activates concrete, situational reasoning. "Mobile users" does not.

2. **Walk their journey.** Step by step, from the moment they encounter the problem to the moment it's resolved (or they give up). Don't skip steps. Don't idealize — describe what they *actually do*, not what you wish they'd do.

3. **Label emotions at each step.** Not generic emotions — specific ones grounded in the situation. "Anxious because they don't know if this is normal" is insight. "Frustrated" is a platitude. At each step, ask:
   - What are they **thinking**? (inner monologue, not your guess)
   - What are they **feeling**? (specific emotion + cause)
   - What are they **doing**? (actual behavior, including workarounds and hacks)
   - What are they **saying**? (or deliberately not saying — what are they hiding?)

4. **Find the highest-friction moment.** Where does the journey break down, slow down, or create the most anxiety? This is usually where the real opportunity lives. But don't assume — the moment that *looks* most painful might not be the one the person cares most about fixing.

5. **Find the person who breaks your framing.** This is the step most people skip. Identify someone whose experience *contradicts* your emerging understanding. The edge case. The person who hates what everyone else loves, or succeeds where everyone else fails. What do they know that you don't? If your empathy only covers the happy path, it's not empathy — it's confirmation bias.

6. **Ask the right question.** Not "what feature solves this?" but "what would make this person's day?" The answer is often simpler and more human than a feature. Sometimes it's not a product at all.

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

## Taste and Judgment

Process gives you structure. Taste tells you when the output is actually good. These heuristics help you evaluate your own work at each phase.

### The Inevitability Test

A great solution feels inevitable in hindsight. "Of course that's the answer — why didn't we see it immediately?" If your recommendation requires a lengthy justification to feel right, it probably isn't the best one. The best reframes make people say "oh, obviously" — not "hmm, I can see how that could work."

### Seek Disconfirmation

Average practitioners find evidence that supports their framing. Great ones hunt for evidence that *breaks* it. At every phase, actively ask:

- **During Discover:** "Who would disagree with how I'm framing this problem? What would they say?"
- **During Define:** "Who is this problem statement *not* true for? What's the edge case that breaks it?"
- **During Develop:** "What's the strongest argument against my favorite solution?"
- **During Deliver:** "If this fails in 6 months, what's the most likely reason?"

The framing that survives disconfirmation is the one worth pursuing.

### The "Would They..." Test

Test the strength of your solution against real human behavior:

- **Would someone pay for this?** Not "would they say they'd pay" — would they actually pull out their wallet?
- **Would someone tell a friend?** Not because you asked, but because the experience was remarkable enough to mention?
- **Would someone be upset if it disappeared?** If the answer is "they'd just find an alternative," you haven't reached the bar.
- **Would someone change their behavior for this?** The hardest bar — does this matter enough that people will do something differently?

### Know When Design Thinking Is the Wrong Tool

Design thinking can become a comfort blanket — a way to feel productive and rigorous without confronting hard truths. Watch for these signs:

- **You're using it to avoid a decision you already know the answer to.** Sometimes you don't need more empathy mapping. You need courage.
- **The problem is a constraint, not a design challenge.** "We don't have enough money" isn't reframeable. "How do we reach users with no marketing budget?" might be.
- **You're running the process to create buy-in, not insight.** If the goal is to make stakeholders feel heard rather than to discover something new, you're doing politics, not design thinking. That's fine — just be honest about which one you're doing.
- **The fifth iteration isn't producing new insight.** At some point, more process yields diminishing returns. Ship it and learn from real feedback.

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
