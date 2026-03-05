---
name: Prompting Fundamentals
category: model-craft
description: "Use when prompting any AI model (text, image, video, code), when output quality isn't where it needs to be, when selecting which model to use, or when debugging bad model output. Teaches the iteration loop, prompt debugging stack, model selection, and context architecture."
---

# Prompting Fundamentals

## Overview

Output quality is a function of input quality. A better prompt on an average model beats a lazy prompt on the best model. This is the most underrated leverage point in AI work.

Your default is one-shot prompting: write a prompt, get output, deliver it. No iteration, no evaluation, no diagnosis when the output is bad. You treat every model the same way. You rewrite prompts from scratch instead of isolating what went wrong.

This skill teaches the loop that turns adequate output into excellent output: iterate systematically, debug failures precisely, select the right model for the task, and structure your context so the model can actually use it.

## When to Use

- Any time you're prompting a model (text, image, video, code)
- When output quality isn't where it needs to be
- When selecting which model to use for a task
- When managing long contexts or complex multi-step prompts
- When you've run the same prompt 3 times and keep getting mediocre results

## Crafting the First Draft

A strong first draft saves 5+ iterations. A weak one wastes them. Before writing a single word of prompt, answer these four questions:

1. **Goal:** What does success look like in one sentence? Write it down. This becomes what you evaluate output against.
2. **Role:** Does the model need a persona? "You are a senior product designer" activates different reasoning than no role at all. Skip this for simple tasks. Use it when expertise or tone matters.
3. **Context:** What does the model need to know that it doesn't already? Your specific situation, the data it's working with, the constraints. Don't explain what it already knows (what a PDF is, how JavaScript works). Only provide what's unique to your task.
4. **Output shape:** What should the result look like? A table, a list, JSON, 3 paragraphs, a one-liner? If you don't specify, the model picks its default (usually a wall of text).

**Assemble in this order:**

```
[ROLE if needed]
[GOAL: what you want, in one clear sentence]
[CONTEXT: what the model needs to know]
[CONSTRAINTS: what NOT to do, length limits, style rules]
[OUTPUT FORMAT: what the result should look like]
[EXAMPLE if tone/style matters: one concrete example of good output]
```

**The test for a good first draft:** Could someone who isn't you read this prompt and produce exactly what you want? If there's ambiguity, the model will interpret it differently than you intended.

### Worked Example

**Task:** Write an error message for when a payment fails.

**Weak first draft:** "Write an error message for a failed payment."

**Output:** "An error has occurred while processing your payment. Please try again later or contact support."

**Strong first draft:** "Write a user-facing error message for when a credit card payment fails at checkout. The tone should be calm and helpful, not alarming. Tell the user what happened, suggest the most likely fix (re-entering card details), and offer a fallback (trying a different payment method). Maximum 2 sentences."

**Output:** "Your payment didn't go through. Double-check your card details and try again, or use a different payment method."

The weak draft was ambiguous (what kind of payment? what tone? how long?). The model filled the gaps with generic defaults. The strong draft constrained every dimension that matters. The difference: one iteration vs. potentially five.

## The Iteration Loop

This is the single most important thing in this skill. One-shot prompting is amateur. The loop is professional.

```
Define goal clearly
  → Draft prompt
    → Run it
      → Evaluate output against goal
        → Identify the specific failure
          → Isolate the variable (what ONE thing caused this?)
            → Fix that one thing
              → Re-run
                → Lock what works
                  → Document the pattern
```

### The Rules of the Loop

**Change one variable at a time.** If you change the structure, the examples, and the constraints all at once and the output improves, you don't know which change helped. Isolate. Test. Confirm. Then move to the next variable.

**Lock what works.** When a section of the prompt produces good output, stop touching it. Fix other parts around it. Changing everything every iteration is starting over, not iterating.

**Know when to stop.** If your last 3 iterations produced only marginal improvements, you're past diminishing returns. The output is as good as this prompt/model combination can produce. Ship it, or try a different model.

**Document patterns that work.** When you find a prompt structure that reliably produces great output for a task type, save it. Reuse it. Build a library of proven patterns instead of reinventing every time.

### What "Evaluate Against Goal" Actually Means

Before running a prompt, write down what success looks like in one sentence. After output, compare:
- Does it match the goal? (not "is it interesting?" but "is it what I needed?")
- What specifically is wrong? Name the gap, not the vibe. "The tone is too formal" is actionable. "It's not quite right" is not.
- Is the failure in the content, the format, the style, or the completeness? Different failures require different fixes.

## The Prompt Debugging Stack

When output is bad, diagnose before rewriting. Check these in order. Most problems are at the top of the stack, not the bottom.

**1. Clarity** -- Was the task unambiguous? Read your prompt as if you'd never seen it before. Could someone else know exactly what you want? If there's any room for interpretation, the model interpreted it differently than you intended.

**2. Context** -- Did the model have everything it needed? Missing context forces the model to guess. If it guessed wrong, the fix isn't a better prompt. It's providing the missing information.

**3. Format** -- Did you specify the output shape? Without format guidance, the model picks its own default (usually a wall of text). If you wanted a table, a list, JSON, or a specific structure, you need to say so explicitly. Show the shape.

**4. Examples** -- Did you show what good looks like? One concrete example of desired output teaches more than a paragraph describing it. If the style or tone is off, add an example of the right style. Don't describe it. Show it.

**5. Constraints** -- Did you define the guardrails? What NOT to do is as important as what to do. "Don't include a preamble." "Maximum 3 sentences." "No bullet points." Constraints prevent the model's defaults from overriding your intent.

**6. Model fit** -- Is this the right model for this task? An image model being asked for photorealism when it excels at illustration. A fast model being asked for deep reasoning. Wrong model, right prompt still produces bad output.

**7. Temperature** -- Is the output too creative (hallucinating, random, inconsistent) or too rigid (generic, safe, predictable)? Lower temperature for precision, higher for creativity. Most models default to a middle ground that isn't optimal for either extreme.

**The 80/20 rule:** Most bad output is a clarity or context problem (positions 1-2). Fix those before touching anything else. Don't blame the model when the prompt was ambiguous.

## Model Selection

Your preferred models and when to use each. Match the model to the task, not the other way around.

### Text Models

**Claude (Opus)** -- Deep reasoning, nuanced analysis, long documents, careful thinking, complex multi-step tasks. Your default for anything requiring genuine intelligence. Tends to be thorough. Set length limits when you want brevity.

**Claude (Sonnet)** -- Faster, cheaper, still smart. Good for routine tasks, conversational responses, quick generation, and high-volume work where Opus latency isn't justified.

**GPT-4o** -- Strong at structured output (JSON, tables, strict formats), code generation, and following rigid templates. Use when format precision matters more than nuanced reasoning.

**Gemini** -- Massive context window (2M tokens), strong multimodal capabilities. Use for research across large document sets, analyzing images alongside text, or tasks that need more context than other models can hold.

### Image Models

**Nano Bana Pro** (or latest/best available) -- Your primary image model. Illustrations, product visuals, creative assets. Load the Image Generation skill for detailed prompting techniques.

### Video Models

**Kling / Flow** -- Your primary video models. Short-form content, product demos, social clips.
**Sora / Runway / Pika** -- Alternatives with different strengths. Test for your specific use case.

### Selection Principles

**Don't default to one model for everything.** Claude Opus is a safe default for text, but GPT-4o might be better for your specific structured output task. Test.

**Stay current.** Models improve constantly. When a new model or major update drops, test it against your current default on a representative task before switching. Don't switch on hype. Switch on evidence.

**Cost vs. quality tradeoff.** Opus for the important stuff. Sonnet for the volume stuff. Don't use the most expensive model for every API call.

## Context Architecture

How you structure the prompt matters as much as what's in it.

**Critical info goes first and last.** Models exhibit the "lost in the middle" effect: accuracy drops 30%+ for information positioned in the middle of long prompts. Put your most important instructions at the beginning. Repeat non-negotiable constraints at the end.

**Separate instructions from content.** Don't interleave "here's what to do" with "here's the data." Use clear blocks:

```
[INSTRUCTIONS: what to do, how to format output]

[CONTEXT: the data, documents, or information to work with]

[OUTPUT FORMAT: what the result should look like]
```

**Repeat key constraints.** If something is non-negotiable ("must be under 100 words," "must include a CTA"), state it at the beginning AND at the end. The model pays most attention to the start and end of the prompt.

**Don't fill the window because you can.** More context is not always better. Irrelevant context dilutes the model's attention on what matters. Include what's needed for the task. Cut everything else. A focused 2K-token prompt often outperforms a bloated 50K-token prompt.

**For repeated tasks, cache the stable parts.** Identify what stays the same across runs (instructions, examples, format spec) and what changes (the specific input). Keep the stable parts consistent. Vary only what needs to vary.

## Instructions vs. Collaboration

Two modes of prompting. Most people only use the first.

**Instruction mode:** "Write a product description for X. Format as Y. Include Z. Don't mention W."

Best for: structured, repeatable tasks with clear right answers. The model is an executor following a spec.

**Collaboration mode:** "I'm trying to solve X. Here's what I've considered so far. Here's what's not working. What am I missing? What would you try?"

Best for: open-ended problems, creative work, strategic thinking, anything where the model's reasoning matters more than its formatting. The model is a thinking partner, not an executor.

Collaboration mode often produces dramatically better results for complex problems because it activates deeper reasoning. Instruction mode activates pattern-matching to the requested format. If you're getting superficial output on a deep problem, try switching modes.

## How Prompting Changes by Modality

The iteration loop and debugging stack apply everywhere. But the craft differs:

**Text models:** The prompt is a conversation. Clarity, structure, and examples drive quality. You're guiding reasoning.

**Image models:** The prompt is a creative brief. Composition language ("wide shot," "centered subject"), style keywords ("flat illustration," "isometric," "watercolor"), and mood ("warm," "minimal," "energetic") matter more than complete sentences. Load the Image Generation skill for deep techniques.

**Video models:** The prompt is a storyboard. Shot type, camera movement, pacing, duration, and transitions. Specificity about what happens in which second. Load the Video Generation skill when available.

**Code models:** The prompt is a spec. Language, framework, patterns, edge cases, and constraints. The more specific the spec, the better the code. Vague specs produce vague code.

The universal principle: **the model can only give you what you ask for.** If you ask vaguely, you get the model's best guess. If you ask precisely, you get what you need.

## Anti-Patterns

| Pattern | Fix |
|---------|-----|
| One-shot prompting (write once, deliver) | Run the iteration loop. Evaluate, identify failure, fix, re-run. |
| Rewriting the whole prompt when output is bad | Use the debugging stack. Identify the specific failure first. Change one variable. |
| Same prompt structure for every model | Match the prompting style to the model's strengths. Claude wants context, GPT wants structure, Gemini wants scope. |
| Stuffing the context window with everything | More is not better. Focused context outperforms bloated context. Include what's needed, cut what's not. |
| "Make it better" (vague iteration) | Name the specific failure. "The tone is too formal" is fixable. "It's not good enough" is not. |
| Using Opus for everything | Match cost to task. Sonnet for routine work, Opus for complex reasoning. Don't overspend on simple tasks. |
| Describing the desired output instead of showing it | One example teaches more than a paragraph of description. Show, don't tell. |
| Giving up after one bad output | The first output is the starting point, not the result. Iterate. |

## Composability

This skill applies to every interaction with any model. It pairs with:

- Load **Image Generation** for modality-specific image prompting techniques
- Load **Video Generation** for video-specific prompting
- Load **Product Planning** when prompting for research or discovery (competitive research step)
- Load **Software Polish** when the model's output needs self-review before delivery
- Load **Critical Evaluation** (meta-cognitive) to stress-test your own prompts before running them on expensive models
