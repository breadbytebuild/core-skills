# Core Skills

A collection of skills you can give to an AI agent to make it world-class at specific capabilities. Each skill is a self-contained Markdown file designed to be loaded into an agent's context on demand.

## Installation

### Step 1: Clone the repo

```bash
git clone https://github.com/breadbytebuild/core-skills.git
```

### Step 2: Add the routing index to your agent's soul file

Add the following to your agent's soul file (SOUL.md, system prompt, or equivalent persistent configuration). This is the only thing that needs to be always-loaded — it's compact (~50 lines) and tells the agent when and how to load specific skills.

```markdown
## Core Skills — Meta-Cognitive Thinking

You have access to a set of meta-cognitive skills that make you better at
reasoning through complex problems. These skills are stored as files and
should be loaded on demand when a matching situation is detected.

**Routing index:** Read `core-skills/skills/meta-cognitive/ROUTING.md` at
the start of any task that involves problem-solving, decision-making,
creative work, or strategic thinking. It contains trigger conditions for
each skill and tells you which file to load.

**How to use skills:**
1. Read the ROUTING.md file to determine which skill(s) match your situation
2. Load the relevant skill file(s)
3. Follow the skill's process — it has phases, gates, and techniques
4. Skills compose together. For complex problems, load multiple skills and
   follow the composition flow in ROUTING.md

**Critical — do NOT narrate your process:** These skills are your internal
reasoning tools. Use them to think, but deliver clean, clear answers. Do NOT
say things like "Let me run the Empathy Protocol" or "Applying the Bedrock
Test" or walk the user through each phase step by step. Think through the
frameworks internally, then present your conclusion with the reasoning that
supports it — not the meta-process you used to get there. The user should
experience better answers, not see the scaffolding.

**Important:** These skills are additive — they enhance your base capabilities,
they don't replace them. Each one corrects a specific weakness in how LLMs
reason by default (premature convergence, analogy bias, linear thinking,
idea clustering, sycophancy, position bias).
```

Replace `core-skills/` with the actual path to wherever you cloned the repo.

### Step 3: That's it

The agent will read the routing index when it encounters a matching situation, load the relevant skill(s), and follow the process. No configuration, no API keys, no dependencies.

## How It Works

The system uses **progressive disclosure** — the agent doesn't load all skills into context at once (that would waste ~15K tokens per turn). Instead:

1. **Always loaded (~100 tokens):** The soul file snippet above tells the agent skills exist and where to find the routing index
2. **Loaded on trigger (~300 tokens):** The routing index maps situations to specific skill files
3. **Loaded on demand (~2-3K tokens each):** Individual skill files load only when the agent enters a matching situation

This means an agent can have access to all six skills while only consuming context for the ones it's actively using.

## Skills

### Meta-Cognitive & Thinking

The foundation layer. These skills change how an agent approaches *all* problems.

| Skill | What It Fixes | Core Tool |
|-------|--------------|-----------|
| [Design Thinking](skills/meta-cognitive/design-thinking.md) | Premature convergence, simulated empathy, single-framing | Double Diamond (Discover/Define/Develop/Deliver) |
| [First Principles](skills/meta-cognitive/first-principles.md) | Reasoning by analogy, treating convention as fact | The Assumption Stack + Bedrock Test |
| [Systems Thinking](skills/meta-cognitive/systems-thinking.md) | Linear cause-and-effect bias, ignoring feedback loops | Iceberg Model, Feedback Loops, Leverage Points |
| [Structured Brainstorming](skills/meta-cognitive/structured-brainstorming.md) | Artificial Hivemind — diverse ideas, not just more ideas | Lens Toolkit (SCAMPER, Constraint Injection, Inversion, etc.) |
| [Critical Evaluation](skills/meta-cognitive/critical-evaluation.md) | Sycophancy, confirmation bias, plausibility-over-truth | Adversarial Toolkit (Steel Man, Pre-Mortem, Evidence Audit) |
| [Prioritization Frameworks](skills/meta-cognitive/prioritization-frameworks.md) | Position bias, "everything is important" paralysis | Ruthless Cut, ICE Scoring, Eisenhower Matrix |

### How They Compose

```
First Principles    →  strips assumptions, finds bedrock truths
Design Thinking     →  frames the right problem for real humans
Systems Thinking    →  maps how everything connects
Brainstorming       →  generates diverse solution options
Critical Evaluation →  stress-tests each option for soundness
Prioritization      →  ranks what matters most and kills the rest
```

Load all six for a full reasoning stack, or pick the ones that match your task. See [ROUTING.md](skills/meta-cognitive/ROUTING.md) for the quick decision guide.

## Skill Format

Each skill is a Markdown file with YAML frontmatter:

```markdown
---
name: Skill Name
category: category-slug
description: One-line description and trigger conditions.
---

# Skill Name

(skill content — typically 140-250 lines)
```

Every skill follows the same structure: Overview → Why This Works → When to Use → Core Framework → What Great Looks Like → Taste and Judgment → Anti-Patterns → Process Integrity → Composability.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to write and add new skills.
