# Contributing to Core Skills

## Writing a New Skill

### 1. Pick your category

Skills live in `skills/<category>/`. Choose the category that best fits, or propose a new one.

### 2. Create the file

Use kebab-case for filenames: `skills/meta-cognitive/first-principles.md`

### 3. Follow the format

Every skill file needs YAML frontmatter and a clear structure:

```markdown
---
name: Skill Name
category: category-slug
description: One-line description of what this skill teaches.
---

# Skill Name

## Overview
What this skill is and why it matters. 2-3 sentences max.

## Core Principles
The fundamental ideas. Numbered list, each with a brief explanation.

## How to Apply
Step-by-step or framework for actually using this skill. This is the actionable part.

## Examples
Concrete examples showing the skill in action. Before/after, good/bad, or worked scenarios.

## Common Pitfalls
What goes wrong when this skill is applied poorly.

## When to Use
Triggers and situations where this skill is most valuable.
```

### 4. Update the README

Add your skill to the appropriate table in `README.md`.

## Quality Bar

A good skill file should:

- **Be self-contained** — an agent should be able to use it without any other context
- **Be actionable** — not just theory, but concrete steps and frameworks
- **Include examples** — show, don't just tell
- **Be concise** — aim for 500-1500 words; long enough to be useful, short enough to fit in context
- **Avoid fluff** — every sentence should earn its place

## Category Overview Files

Each category has a `_category.md` that describes the group. Update it if you add a skill that shifts the category's scope.
