---
name: Image Generation
category: model-craft
description: "Use when generating illustrations, product visuals, infographics, or creative assets with image models. Covers Nano Bana Pro as the primary model, general image prompting principles, how major models differ, style consistency, and the iteration loop for visual output."
---

# Image Generation

## Overview

Image prompts are creative briefs, not descriptions. Your default is to write "a picture of a dashboard." That produces generic, forgettable output. This skill teaches you to write prompts that produce illustrations good enough to ship in a real product.

Nano Bana Pro is your primary image model. It excels at illustrations, text rendering, infographics, and design assets. This skill teaches its specific strengths and prompting patterns, plus when to reach for a different model.

The Prompting Fundamentals skill covers the universal iteration loop and debugging stack. This skill applies those principles specifically to visual output, where the craft is fundamentally different from text.

## When to Use Generated Images

Illustrations elevate a product when used strategically. They become noise when used everywhere.

**High-value placements:**
- **Empty states** -- guide the user, explain what's missing, make a blank page feel intentional
- **Onboarding screens** -- make setup friendlier, reduce anxiety, improve completion rates
- **Error pages** -- reduce frustration, add personality, make a bad moment slightly better
- **Landing pages** -- memorable first impression, communicate the product's personality
- **Abstract concepts** -- security, speed, AI, data privacy, scalability. Things you can't photograph.
- **Marketing assets** -- social cards, email headers, blog illustrations, ad creatives

**Don't use illustrations:**
- On every card in a grid (it becomes wallpaper)
- As decoration with no communicative purpose
- When a simple icon or UI element would work
- When a screenshot of the actual product is more convincing

**The test:** Does this illustration communicate something that text or UI alone can't? If yes, generate. If no, skip it.

## Writing Image Prompts

Image prompts are creative briefs with five dimensions. Cover each one intentionally.

### The Five Dimensions

**1. Subject** -- What is in the image? Be specific about the main element.
- Weak: "a person using a computer"
- Strong: "a focused designer working on a laptop, surrounded by sticky notes and sketches on a clean white desk"

**2. Scene/Setting** -- Where is the subject? Background, environment, context.
- "in a bright, modern co-working space with floor-to-ceiling windows"
- "on a clean white background with subtle geometric shapes"
- "floating in an abstract gradient space with soft particles"

**3. Style** -- What visual language?
- Flat illustration, isometric, watercolor, photorealistic, editorial, hand-drawn, line art, 3D render, paper cutout, minimal vector
- This is the most impactful dimension for the overall feel. Choose intentionally.

**4. Mood/Lighting** -- What feeling should the image evoke?
- Warm, minimal, energetic, dramatic, calm, playful, professional, futuristic
- Lighting is the single most impactful mood tool. "Soft diffused light" vs. "dramatic side lighting" vs. "golden hour warmth" completely changes the feeling.

**5. Composition** -- How is the image framed?
- Camera angle: top-down, isometric, eye-level, low angle
- Framing: wide shot, close-up, centered subject, rule of thirds, negative space on the left for text overlay
- Depth: shallow depth of field (blurred background), flat (everything in focus)

### Don't Over-Specify

Cover the dimensions you care about. Leave room for the model's interpretation on things you don't care about. Over-constrained prompts produce stiff, lifeless images. Under-constrained prompts produce generic ones. Hit the middle.

### Before/After

**Weak:** "A dashboard illustration"

**Strong:** "A clean, minimal flat illustration of a laptop showing an analytics dashboard with colorful bar charts and a line graph trending upward. Soft blue-to-white gradient background. Isometric perspective. Warm, friendly, professional mood. The style should feel like a premium SaaS marketing asset."

## Nano Bana Pro

Your primary image model. What makes it different and how to get the best results.

### Prompting Style: Brief an Artist

Write like you're talking to a human illustrator, not tagging a search engine. Full sentences, proper grammar, descriptive adjectives. Nano Bana Pro was trained on Gemini 3 Pro's language understanding, so it comprehends context and nuance better than keyword-driven models.

**Not this:** "dashboard, flat, minimal, blue, isometric, SaaS, clean, modern, illustration"

**This:** "Create a clean, minimal flat illustration of a SaaS analytics dashboard on a laptop screen. Use a soft blue gradient background with subtle geometric accents. The perspective should be slightly isometric. The mood is professional and approachable."

### Edit, Don't Re-Roll

When the output is 80% right, don't regenerate from scratch. Describe what to change specifically:
- "Make the background darker and more saturated"
- "Remove the person on the right side"
- "Change the text to say 'Get Started Free'"
- "Make the illustration style more minimal with fewer details"

This produces better results than re-rolling because you're refining, not gambling. The model adjusts from a good starting point instead of generating blind.

### Nano Bana Pro's Superpowers

**Text rendering.** This model can render actual legible, styled text. Use it for:
- Marketing posters with headlines
- Product mockups with realistic UI text
- Infographics with data labels
- Social cards with quotes or statistics
- Slides and presentation visuals

Other models hallucinate text. Nano Bana Pro gets it right. If your image needs words, this is the model.

**Infographic compression.** Feed it dense content (articles, data tables, earnings reports) and ask for a visual summary. It can create detailed infographics from raw information, which no other image model does reliably.

**Character consistency.** For a series of illustrations with the same character or mascot, provide reference images. The model maintains facial features, clothing, and style across generations (up to 5 reference images, 14 total reference objects).

**Purpose-aware generation.** Tell the model what the image is for: "This is for an empty state in a SaaS email marketing product" gives it context to make better artistic decisions than just describing the scene.

### Prompt Template

```
Create a [style] illustration for [purpose/context].
The image shows [subject] in [setting/environment].
The mood is [mood adjectives]. Use [color palette/scheme].
[Any text to render, if applicable.]
[Composition notes if needed: perspective, framing, where to leave space.]
```

## Other Models: When to Reach for Something Else

Nano Bana Pro is your default. But it isn't the best at everything.

| Need | Model | Why |
|------|-------|-----|
| Photorealism (product photos, headshots, environments) | **Flux** | 92% prompt adherence, best hands/anatomy, photographic quality |
| Magazine-quality artistic aesthetics | **Midjourney** | Cinematic lighting by default, style references (--sref), polished output |
| Quick iterative editing via chat | **DALL-E** | Conversational interface, natural inpainting, fastest iteration |
| Specific fine-tuned style (anime, pixel art, brand-specific) | **SDXL + LoRA** | Massive ecosystem of custom models, cheapest per image |
| Text rendering, infographics, design assets | **Nano Bana Pro** | Stay here. Best in class for these. |

When choosing: try your primary model first. Only switch when you hit a limitation that a different model specifically solves. Don't model-hop based on vibes.

## Style Consistency Across a Project

The hardest part of using generated images in a product. Every illustration must look like it belongs in the same family.

**Lock a style description.** Write one paragraph defining the project's visual style. Reuse it as a prefix on every prompt:

> "Flat vector illustration style with soft rounded shapes and minimal detail. Muted pastel color palette with one bold accent color (#4F46E5). Clean white or light gray backgrounds. Warm, approachable, professional mood. No heavy shadows or gradients."

Every image prompt starts with this paragraph, then adds the specific subject and scene.

**Save working prompts.** When you generate an image that nails the style, save the exact prompt. Use it as the template for all future images in the series, changing only the subject and scene.

**Use reference images.** On Nano Bana Pro, feed previously generated illustrations as reference images. The model will match the style, color palette, and level of detail.

**Define a color palette.** Include specific hex colors or named colors in every prompt. "Use #4F46E5 as the primary accent, #F3F4F6 as the background, and #1F2937 for dark elements." This prevents color drift across illustrations.

**The consistency test:** Put all your generated images side by side. Do they look like they were made by the same artist for the same project? If one looks different, regenerate it using the locked style description and reference images.

## The Image Iteration Loop

The Prompting Fundamentals iteration loop applied to visual output.

1. **Define what you need.** Subject, style, purpose, mood, and where it goes in the product.
2. **Draft the prompt** using the five dimensions and the template.
3. **Generate.**
4. **Evaluate.** Is the composition right? Style on brand? Mood correct? Text accurate? Colors matching the palette?
5. **If 80%+ correct:** Edit specifically. "Darken the background." "Remove the extra element on the right." "Make the text larger." Don't re-roll.
6. **If fundamentally wrong:** Revise the prompt. Change one dimension at a time (style OR composition OR subject, not all three).
7. **Lock the prompt** when it works. Save it as the template for the series.

**Know when to stop.** If iteration 4 and iteration 5 look equally good but different, you're past diminishing returns. Pick the better one and move on.

## Anti-Patterns

| Pattern | Fix |
|---------|-----|
| "A picture of X" (description, not a brief) | Use the five dimensions: subject, scene, style, mood, composition. |
| Keyword soup ("dashboard, minimal, blue, SaaS, clean, modern") | Write natural language for Nano Bana Pro. Brief an artist, not a search engine. |
| Re-rolling until you get lucky | Edit the 80% correct image. Describe what to change specifically. |
| Different style on every illustration | Lock a style description. Use it as a prefix on every prompt. |
| Using one model for everything | Nano Bana Pro is the default, but Flux does photorealism better. Midjourney does aesthetics better. Match the model to the need. |
| Illustrations everywhere | Use strategically. Empty states, onboarding, errors, landing pages. Not every card and section. |
| Ignoring the purpose | Tell the model what it's for. "For an empty state in a SaaS product" produces better results than just describing the scene. |
| No color palette consistency | Define hex colors and include them in every prompt. Color drift kills visual cohesion. |

## Composability

This skill handles the image-specific craft. It pairs with:

- Load **Prompting Fundamentals** for the universal iteration loop, debugging stack, and model selection principles
- Load **UI/UX Design Sense** when deciding where illustrations go in the product and how they fit the design system
- Load **Software Polish** to evaluate whether the generated images meet the quality bar before shipping
- Load **Product Planning** when illustrations are part of a larger feature plan (onboarding redesign, landing page, marketing campaign)
