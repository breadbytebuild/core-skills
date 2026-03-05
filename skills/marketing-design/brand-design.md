---
name: Brand Design
category: marketing-design
description: "Use when creating a logo, building a brand identity, designing a brand mark, or evaluating whether an existing brand's visual identity is working. Covers strategy-before-style, logo anatomy, the professional design process adapted for AI agents working through image models, the AI Logo Slop Checklist, and brand system extension (color, typography, usage rules)."
---

# Brand Design

## Overview

A logo is a strategic tool, not a pretty picture. Your default is to generate a gradient icon with a geometric sans-serif wordmark and call it a brand. That's not a brand. That's clip art with a font attached.

Professional brand design encodes meaning into form. Stripe's S feels like code. Linear's mark feels like speed. Airbnb's Belo feels like belonging. Each logo communicates ONE idea in the simplest possible shape. That's the bar.

You work through image models, not Illustrator. This skill teaches both the design thinking (what makes a great brand mark) and the execution methodology (how to produce one through generation and iteration). Load Image Generation and Prompting Fundamentals alongside this skill for the technical craft.

## When to Use

- Creating a new brand identity or logo
- Redesigning or refreshing an existing brand mark
- Building a visual identity system (colors, typography, usage rules)
- Evaluating whether an existing brand mark is working

**Not for:** UI design (that's UI/UX Design Sense), product illustrations (that's Image Generation), marketing assets within an existing brand system (future skill).

## Strategy Before Style

The single biggest difference between professional brand work and amateur work. Before you generate a single image, answer these questions. Skip this and you'll produce something generic. Every time.

### The Brand Brief

Answer in writing before touching any visual tool:

1. **What does this brand need to communicate in one sentence?** Not what the product does. What feeling, quality, or idea should someone associate with the name? Stripe: "serious infrastructure." Linear: "speed and precision." Duolingo: "learning is fun."
2. **Who is the audience?** A developer tool, a consumer app, and a luxury product need completely different visual languages. Name the person, not the demographic.
3. **What's the competitive landscape?** List 5-10 competitors or adjacent brands. Screenshot their logos. Note the visual patterns: what colors dominate? What styles? What typography?
4. **What emotion should someone feel?** Trust? Excitement? Calm? Playfulness? Confidence? Pick one primary emotion, one secondary at most.
5. **What is the brand's personality in three words?** Not what it does. How it acts. "Precise, confident, approachable" is a personality. "Fast, modern, innovative" is a feature list.

### The Differentiation Test

From Neumeier's "Zag": look at what your competitors do visually, then don't do that.

If every competitor uses blue and geometric sans-serif, you use warm tones and a custom wordmark. If every competitor uses playful illustration, you use austere minimalism. If every competitor uses dark mode, you use light.

The point isn't to be contrarian. It's to be *recognizable*. In a lineup of 10 blue logos with similar shapes, you're invisible. The brand that looks different is the one people remember.

**Exercise:** Put your competitors' logos in a grid. Squint. If you can't tell them apart at a glance, that's the visual space you avoid.

### The SMART Check

Every logo concept must pass all five before you proceed:

- **S — Simple.** Can someone draw it from memory? If it takes more than 5 seconds to sketch, strip elements.
- **M — Memorable.** After seeing it once, would someone recognize it again? Distinctive shape or unexpected element.
- **A — Ageless.** Will this look dated in 5 years? If it relies on a current trend (gradient mesh, 3D chrome, neon outlines), it will.
- **R — Reliable.** Does it work at 16px (favicon), 64px (app icon), 200px (website), and 2000px (billboard)? Does it work in monochrome? On dark and light backgrounds?
- **T — Thoughtful.** Can you explain why every element exists? If any part is decorative rather than communicative, cut it.

## Logo Anatomy

Know what you're building before you build it. These are the four types of brand marks.

**Logomark** (symbol alone)
A standalone icon with no text. Apple's apple, Nike's swoosh, Target's target. Requires massive brand awareness to work alone. Most startups can't pull this off because nobody recognizes a standalone icon for a company they've never heard of.

**Logotype / Wordmark** (styled text)
The company name rendered in a distinctive typeface. Google, Stripe, Linear, Coca-Cola. The typography IS the brand. Works immediately because it literally says the name. Best starting point for most tech companies.

**Combination Mark** (symbol + text)
A logomark paired with a wordmark. Airbnb, Notion, Slack, Spotify. The most versatile type: use together for full recognition, separate the icon for favicons and app icons, use the wordmark alone when the icon is too small. The sweet spot for most brands.

**Lettermark** (initials)
The company's initials styled distinctively. IBM, HBO, BBC, GE. Works for long company names or when initials are already how people refer to the brand. Requires careful typography because 2-3 letters carry the entire identity.

**Which type to choose:**

| Situation | Best Type | Why |
|-----------|-----------|-----|
| New startup, unknown name | Wordmark or combination | People need to read the name |
| Established brand with recognition | Any type works | People already know you |
| Long company name | Lettermark or combination | Full name doesn't fit in small spaces |
| Need a strong app icon | Combination (use icon separately) | App stores need a square icon |
| Want maximum flexibility | Combination | Works split apart or together |

## The Design Principles

What separates great logos from generic ones. These are drawn from studying Stripe, Linear, Airbnb, Apple, Notion, Figma, Vercel, and the work of Pentagram, Collins, and Koto.

### Radical Simplicity

The best logos can be drawn from memory. Apple: an apple with a bite. Nike: a swoosh. Linear: two angled lines. FedEx: the name (with a hidden arrow).

If you can't describe the logo in one sentence and have someone visualize it, the logo is too complex. Strip elements until removing one more would lose the meaning. That edge is where great logos live.

**The reduction test:** Take your concept and remove one element. Does it still communicate the idea? If yes, it was unnecessary. Keep removing until the answer is no. That's your logo.

### Monochrome First

Design in black and white. If the logo doesn't work without color, color won't save it. Color is applied after the form is right, not used to compensate for a weak shape.

This also guarantees it works in every context: black on white, white on black, stamped, engraved, faxed (yes, still), embroidered.

### Geometry With Intention

Great logos use geometric relationships (golden ratio, grid alignment, consistent stroke weights) but break them when optical correction demands it. A mathematically centered element doesn't always look centered to the human eye. Trust the eye over the grid when they disagree.

The grid is a tool for consistency, not a prison.

### Scalability Is Non-Negotiable

The logo must be recognizable at:
- **16px** (browser favicon)
- **64px** (app icon)
- **200px** (website header)
- **2000px+** (signage, print)

Details that disappear at small sizes are liabilities, not features. Fine lines, small text, intricate patterns, subtle gradients all fail at favicon scale. If a detail doesn't survive 16px, cut it from the mark entirely.

**Test this during design, not after.** Generate the concept, then immediately test it at favicon size. Most AI-generated logos fail this test because they have too much detail.

### Timeless Over Trendy

Trends in logo design have a 3-5 year shelf life. Gradient mesh, 3D chrome, neon glow, glassmorphism, outline-only marks, overlapping transparencies. They look contemporary now and dated soon.

The Apple logo has lasted since 1977. The Nike swoosh since 1971. The FedEx wordmark since 1994. They endure because they're built on form and meaning, not visual effects.

**The 10-year test:** Will this logo look as good in 2036 as it does today? If it relies on any current visual trend for its impact, the answer is no.

### Negative Space as a Weapon

The most clever logos use what's NOT there. FedEx's arrow between the E and x. The Spartan Golf Club's golfer in the negative space of a Spartan helmet. NBC's peacock formed by colored feathers.

Negative space logos are memorable because they reward attention. The viewer discovers something, and that discovery creates a bond with the brand. You don't force meaning. You hide it in plain sight.

Not every logo needs negative space. But when it's appropriate, it elevates a mark from good to iconic.

## The Execution Process

How to produce a quality logo when your tool is an image model. This is a five-phase process.

### Phase 1: Concept Exploration

Generate 10-15 rough concepts with broad style variation. The goal is divergence, not quality. You're exploring the space, not picking a winner.

**Prompt approach for concept phase:**

```
Create a minimal logomark for [brand name]. [One-sentence brand brief].
Style: [vary this across generations — try: geometric, organic, typographic,
abstract, letterform, negative space]. Black on white, clean vector style.
No gradients, no effects, no background texture.
```

Vary the style aggressively across generations. If your first 5 concepts are all geometric abstract marks, you haven't explored enough. Force yourself through:
- A pure wordmark (just the name, distinctive typography)
- A lettermark (initials only)
- An abstract geometric mark
- An organic/hand-drawn mark
- A negative space concept
- A pictorial mark (representing something specific, not literally)

**Model selection for concept phase:** Flux produces the cleanest vector-style output. Nano Bana Pro handles text-heavy concepts (wordmarks, lettermarks) better. Midjourney is useful for exploratory, aesthetic-forward concepts. Try multiple models.

### Phase 2: Direction Selection

Narrow from 10-15 concepts to 2-3 genuinely different directions. Not 3 variations of one idea. Three distinct approaches.

Evaluate each against:
- The brand brief (does it communicate the right idea and emotion?)
- The SMART check (simple, memorable, ageless, reliable, thoughtful?)
- The differentiation test (does it look different from competitors?)
- Gut reaction: does it FEEL right? Not just look right?

Present the 2-3 directions with a brief rationale for each. If building for a human stakeholder, share at this stage. If autonomous, pick the strongest and move to Phase 3.

### Phase 3: Refinement

Iterate on the selected direction. This is where the Image Generation skill's "edit, don't re-roll" principle matters most.

**Simplify aggressively.** Run the reduction test on every element. If you can remove it without losing meaning, remove it.

**Test in monochrome.** Generate the logo in pure black on white. Does the form hold?

**Test at small scale.** Generate at 32px. Is it still recognizable?

**Refine proportions.** Adjust the weight, spacing, angles. "Make the strokes thicker." "Increase the spacing between the letters." "Make the icon 20% smaller relative to the wordmark." Small adjustments, one at a time.

Aim for 5-8 refinement iterations, not 25. If you're past iteration 10 and it's still not working, the direction might be wrong. Go back to Phase 2.

### Phase 4: System Extension

Once the mark is locked, define the visual system around it.

**Color palette:**
- **Primary:** The logo's main color. One color. Define the hex value.
- **Secondary:** 1-2 supporting colors that complement the primary. Used for backgrounds, accents, illustrations.
- **Neutral:** Background and text colors. Usually a warm or cool gray scale, not pure black (#000) and white (#FFF).
- **Accent:** A single high-contrast color for CTAs, alerts, highlights. Used sparingly.

Generate the logo in its final colors. Then generate it on dark background, light background, and each secondary color as background.

**Typography pairing:**
- **Display font:** For headlines, brand moments, marketing. Should feel like it belongs to the same family as the logo. If the logo is geometric, the display font should be too.
- **Body font:** For readable text, UI, documentation. Functional and clean. Doesn't need to be distinctive, just legible and compatible.

**Usage rules** (define explicitly):
- Minimum size (usually 24-32px wide for combination marks)
- Clear space around the mark (usually the height of one element, like the icon)
- Approved color combinations (logo on white, logo on dark, logo on primary color)
- Forbidden treatments: don't stretch, don't rotate, don't add shadows, don't place on busy backgrounds, don't change the colors

### Phase 5: Stress Test

Before declaring the brand done, test it in context:

1. **Favicon test:** Generate at 16px. Recognizable?
2. **App icon test:** Generate at 64px in a rounded square. Does it fill the space well?
3. **Header test:** Place next to navigation text at website header scale.
4. **Dark/light test:** Generate on both backgrounds.
5. **Competitor lineup:** Place your logo next to 5 competitor logos. Does it stand out? Does it hold its own? Or does it blend in?
6. **Monochrome test:** Black version, white version. Both work?

If any test fails, go back to Phase 3 and address the specific failure. Don't re-roll the entire concept. Fix the specific problem.

## What World-Class Looks Like

Each of these logos encodes ONE idea in the simplest possible form. Study the pattern, not the style.

**Stripe's S.** A simple letterform, but the gradient treatment turns typography into something that feels alive and technical simultaneously. The brand feels like code. The gradient is earned because it's the identity, not decoration. Without it, the S still works (monochrome test passed).

**Linear's mark.** Speed made visual. The angled lines suggest forward motion. Radical simplicity: two lines. Works at any size because there's nothing to lose. The dark-mode-first approach made the brand feel technical and fast before you ever used the product.

**Airbnb's Belo.** One continuous line that encodes "belonging" as a concept. A heart, a location pin, and the letter A in a single stroke. Simple enough to draw from memory, meaningful enough to remember. The form is the story.

**Vercel's triangle.** A play button, a forward arrow, a delta (change). The simplest possible geometric shape, loaded with meaning about deployment and speed. Black on white. No effects. The confidence of simplicity.

**Apple's apple.** The bite prevents it from being mistaken for a cherry or any other round fruit. One detail, one purpose. Everything else stripped away. Unchanged for nearly 50 years.

**The pattern:** none of these logos describe what the company does. They encode how the company *feels*. Stripe doesn't show a payment. Linear doesn't show a task list. Airbnb doesn't show a house. The meaning is abstract, emotional, and embedded in form.

## The AI Logo Slop Checklist

Specific patterns to catch and reject. If your generated logo has any of these, it needs work.

| Slop Pattern | Why It Fails | Fix |
|-------------|-------------|-----|
| Gradient mesh background | Trend from 2020-2023, already dated | Solid colors or no background. Gradients only if they ARE the identity (like Stripe). |
| Literal representation (brain for AI, lock for security, rocket for speed) | Stock icon, not a brand. Could belong to any company in the category. | Abstract the concept. Encode the feeling, not the object. |
| Too many colors (4+) | Visual noise. Reduces to mud at small sizes. | 1-2 colors maximum in the mark itself. 3 if one is the neutral. |
| Too much detail | Disappears at favicon size. Looks busy at any size. | Run the reduction test. If you can remove it, do. |
| 3D effects, chrome, glow, drop shadows | Effects applied to compensate for a weak form. Dates immediately. | Remove all effects. Does the mark still work? If not, the form is the problem. |
| Circular badge/emblem | Overused, reads as "local brewery" or "vintage brand," not modern tech. | Open forms. Let the mark breathe without a container. |
| Generic geometric shapes | Random hexagons, abstract swooshes, overlapping circles with no meaning. | Every geometric choice must have a reason tied to the brand brief. |
| Illegible text at small sizes | Decorative typography that sacrifices readability for style. | If you can't read it at 32px, simplify the letterforms. |
| Interchangeable identity | The mark could belong to any company in any industry. | The differentiation test: place it next to competitors. If it blends in, start over. |

**The phone test:** Could you describe this logo to someone on the phone and they'd recognize the brand? "It's a blue hexagon with a gradient" fails. "It's two angled lines that look like they're moving forward" (Linear) passes. If the description is generic, the logo is generic.

## Anti-Patterns

| Pattern | Fix |
|---------|-----|
| Generating visuals before writing the brand brief | Strategy before style. Always. The brief takes 10 minutes and saves hours of generic iteration. |
| Converging on the first decent concept | Generate 10-15 concepts across different types before picking a direction. Your first idea is the statistical average. |
| "Make me a logo" (no strategic input) | Write the brand brief. One sentence of positioning, audience, emotion, and competitive context changes everything. |
| Designing in color first | Monochrome first. Color is applied after the form works. |
| Never testing at small scale | Generate at favicon size during Phase 3, not after Phase 5. Catch scalability issues early. |
| Adding elements to make it "more interesting" | Logos fail by addition, not subtraction. The urge to add more is almost always wrong. Remove. |
| Copying a brand you admire | Study why it works, then apply the principle to your unique brief. Stripe's gradient works for Stripe. It won't work for you. |
| Declaring done without the stress test | Phase 5 exists because logos that look great as hero images regularly fail in real-world contexts. Test every context. |

## Composability

This skill handles brand identity craft. It pairs with:

- Load **Image Generation** for the actual generation process, model selection, and style consistency
- Load **Prompting Fundamentals** for the iteration loop and debugging stack when refining concepts
- Load **UI/UX Design Sense** when applying the brand identity to a product interface
- Load **Critical Evaluation** (meta-cognitive) to stress-test brand directions: steel-man the alternatives, pre-mortem the chosen direction
- Load **Structured Brainstorming** (meta-cognitive) during Phase 1 to force diverse concept exploration across different logo types
