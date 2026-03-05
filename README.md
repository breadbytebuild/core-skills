# Core Skills

A collection of skills you can give to an AI agent to make it world-class at specific capabilities. Each skill is a self-contained Markdown file designed to be loaded into an agent's context.

## Usage

Point your agent at any skill file and it becomes part of the agent's working knowledge. Each skill is standalone — no dependencies, no build step, just Markdown.

```
Load: skills/meta-cognitive/first-principles.md
```

Skills are additive — load multiple for richer thinking. The meta-cognitive skills are designed to compose together, each amplifying a different phase of reasoning.

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
Critical Evaluation →  stress-tests and selects the best one
Prioritization      →  ranks what matters most and kills the rest
```

Load all six for a full reasoning stack, or pick the ones that match your task.

## Skill Format

Each skill is a Markdown file with YAML frontmatter:

```markdown
---
name: Skill Name
category: category-slug
description: One-line description of what this skill teaches.
---

# Skill Name

(skill content)
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to write and add new skills.
