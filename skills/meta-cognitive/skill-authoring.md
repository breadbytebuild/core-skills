---
name: Skill Authoring
category: meta-cognitive
description: "Use when creating a new skill, updating an existing skill, or managing the soul file. Teaches how to write skills that actually trigger and work, manage the soul file for maximum impact, and diagnose when agent behavior needs a skill vs. a soul file change."
---

# Skill Authoring & Soul File Management

## Overview

This is the meta-skill: the skill for building skills and managing your own configuration. Every other skill makes you better at one thing. This one makes you better at making yourself better.

Most skill failures aren't instruction failures. They're description failures, specificity mismatches, or architecture mistakes (putting the wrong thing in the wrong place). This skill teaches you to avoid all three.

## When to Use

- Creating a new skill from scratch
- Updating a skill that isn't working as expected
- Deciding whether something belongs in the soul file or a loadable skill
- Diagnosing why a behavior change isn't sticking
- Monthly soul file review and iteration

## Writing a Skill: The Three Parts

### Part 1: The Description (Most Important)

The description determines whether the skill ever activates. Agents scan descriptions at startup to match tasks to skills. A bad description means your skill never loads, no matter how good the body is.

**A good description includes three things:**
1. **What** it does (the capability)
2. **When** to use it (specific trigger conditions)
3. **When NOT** to use it (prevents mis-activation)

Write in third person. Include specific words users would actually type.

**Bad:**
```yaml
description: "Helps with changelogs."
```

**Good:**
```yaml
description: "Generates changelog entries from git commit history using Keep a Changelog format. Use when the user asks to create release notes, update a CHANGELOG, or summarize recent changes. Do not use for commit message writing."
```

The bad version is 4 words and gives the agent nothing to match on. The good version names the format, the trigger actions, and the boundary. An agent reading 30 skill descriptions will reliably pick the good one.

### Part 2: The Body (Instructions)

The body guides execution once the skill is activated. Three rules:

**Only include what the model doesn't already know.** LLMs understand coding, file formats, common frameworks, and general knowledge. Don't explain what a PDF is before teaching PDF extraction. Don't describe what "concise" means. Only add your specific workflow, preferences, or domain knowledge.

**Bad (~150 tokens, teaches basics):**
> PDF files are a common document format. To extract text, you can use libraries like pdfplumber which is a Python package for extracting text and tables from PDF documents...

**Good (~50 tokens, assumes competence):**
> Use pdfplumber for extraction. Output as markdown tables. Skip pages with only images.

**Match specificity to risk level:**
- **Creative tasks** (code review, brainstorming, writing): Give direction and principles. "Analyze for bugs, performance issues, and readability."
- **Standard patterns** (API endpoints, component structure): Give templates with parameters. Show the pattern, let the agent adapt.
- **Fragile operations** (database migrations, deployments, auth changes): Give exact steps. "Run exactly this command. Do not modify or add flags."

**Build gates, not guidelines.** If you want behavior to stick under pressure, don't write "try to keep it concise." Write a checklist the agent runs before output. Principles get ignored when the context window is busy. Gates don't.

### Part 3: Structure (Progressive Disclosure)

```
skill-name/
  SKILL.md          # Required. Under 500 lines (under 200 is better).
  references/       # Optional. Loaded on demand, not on activation.
  scripts/          # Optional. Executable code.
  assets/           # Optional. Templates, schemas, data files.
```

The SKILL.md body loads entirely when activated. Everything in `references/` loads only when the agent explicitly reads it. This matters for token budget.

**If your skill is over 300 lines,** ask: what can move to a reference file? Detailed examples, edge case lists, and domain-specific reference tables are good candidates. The core process should stay in SKILL.md.

## Managing the Soul File

### What Belongs Where

**Soul file (always loaded, every message):**
- Identity and voice (who you are, how you sound)
- Always-on behavioral rules (NEVER lists, pre-send gates)
- Conversational awareness (when to reply, when to wait, style matching)

**Skills (loaded on demand, specific situations):**
- Situational processes (how to handle specific task types)
- Domain-specific knowledge (project context, API details)
- Frameworks with multiple steps (thinking processes, communication playbooks)

**The test:** Does this need to apply to every single message you send? Put it in the soul file. Does it only matter in specific situations? Make it a skill.

### When to Move Things Between Them

- A rule in a skill keeps getting violated because the skill isn't loaded when it matters. **Move it to the soul file.**
- The soul file is getting bloated with situational instructions. **Extract them into a skill.**
- A behavior works in some conversations but not others. **It's in a skill that isn't triggering consistently. Fix the description or move it to the soul file.**

### Monthly Soul File Review

Read your last 20 conversations. Note:
- Patterns you wish were different (add rules or gates)
- Rules you're violating repeatedly (enforcement gap, not knowledge gap)
- Rules that feel unnecessary or outdated (remove them, reduce bloat)
- Things in the soul file that only apply sometimes (extract to skill)

The soul file drives 80% of your behavior. Iterating on it monthly is the highest-ROI self-improvement you can do.

## Diagnosing Behavior Problems

When something isn't working, trace the failure:

| Symptom | Likely Cause | Fix |
|---------|-------------|-----|
| Skill never activates | Bad description, missing trigger words | Rewrite description with what/when/when-not |
| Skill activates but output is wrong | Instructions too vague or missing examples | Add specificity, add before/after examples, add a gate |
| Behavior is inconsistent across conversations | Rule is in a skill that doesn't always load | Move it to the soul file |
| Rule is ignored under pressure | It's a principle, not a gate | Convert guideline to a checklist or pre-send check |
| Soul file feels bloated and ineffective | Too many situational rules in always-on context | Extract situational rules into skills |
| Agent sounds generic despite having a soul file | Soul file is vague ("be helpful") instead of specific | Add concrete examples, NEVER lists, and specific voice rules |

## What Great Looks Like

**Great skills:**
- Target a specific weakness the model has by default (not general knowledge)
- Have a description that triggers reliably on matching tasks
- Are under 200 lines with concrete before/after examples
- Include enforcement mechanisms (gates, checklists), not just principles
- Assume the model is smart and only teach what it doesn't know

**Great soul files:**
- Are under 2,000 words total across all sections
- Put the most important rules first (models weight the beginning more heavily)
- Use NEVER/ALWAYS for hard rules, not "try to" or "consider"
- Include enforcement gates, not just principles
- Get iterated monthly based on real conversation patterns

## Anti-Patterns

| Pattern | Fix |
|---------|-----|
| 5-word description, 400-line body | Inverted priority. Spend more time on the description than anything else. |
| Explaining what the model already knows | Delete it. Only add your specific context, preferences, and workflows. |
| "Try to be concise" (guideline) | "Run the pre-send check before every message" (gate). Gates work. Guidelines don't. |
| Situational rules in the soul file | Extract to a skill. The soul file should be lean, always-relevant identity. |
| Always-on rules in a skill | Move to the soul file. Skills don't load reliably enough for rules you need every message. |
| Writing a skill and never updating it | Skills are living documents. Iterate based on what's working and what's not. |
| Testing the skill body without testing the description | The description is the entry point. If it doesn't trigger, the body doesn't matter. |

## Composability

This skill stands alone but informs how you build and maintain all other skills:

- When building new **meta-cognitive skills**, use the pattern established by Design Thinking, First Principles, etc.: Overview, Why This Works, When to Use, Core Framework, What Great Looks Like, Taste and Judgment, Anti-Patterns, Composability.
- When building new **communication skills**, remember: voice goes in the soul file, situation-specific playbooks go in skills.
- When something from **any skill** isn't working, load this skill to diagnose why and fix the root cause.
