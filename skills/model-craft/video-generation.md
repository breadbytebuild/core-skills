---
name: Video Generation
category: model-craft
description: "Use when generating video content with Kling, Sora, Runway, Pika, or similar models. Covers the director mindset (shots, not scenes), the image-to-video workflow, camera movement, shot planning, pacing, model comparison, and the video iteration loop."
---

# Video Generation

## Overview

Video generation is directing, not describing. Your default is to write image prompts with the word "video" attached: "A video of a dashboard with data flowing." That produces generic, incoherent output with random camera movement and no sense of purpose.

This skill teaches you to think like a director. You write shot directions with intentional camera movement, subject action, pacing, and temporal structure. Every second of video should have a reason to exist.

The Prompting Fundamentals skill covers the universal iteration loop and debugging stack. The Image Generation skill teaches visual prompting. This skill builds on both, adding the dimensions that only exist in motion: time, camera, pacing, and the critical image-to-video workflow.

## When to Use Generated Video

Video adds value when motion communicates something stills can't.

**High-value placements:**
- **Product demos** -- show the product in action without recording real UI (useful pre-build or for concept validation)
- **Social content** -- TikTok, Reels, Shorts. Motion stops the scroll better than stills.
- **Hero section backgrounds** -- subtle ambient motion (floating particles, slow camera drift) adds premium feel
- **Ad creatives** -- short-form video ads consistently outperform static across platforms
- **Concept visualization** -- pitch videos, investor decks, "imagine this" moments before the product exists
- **Animated illustrations** -- bringing static product assets to life (an illustration that breathes, a mascot that waves)

**Don't use generated video:**
- When a screen recording of the actual product is more convincing
- When the product UI speaks for itself and adding motion would be decoration
- When you need pixel-perfect UI interactions (screen record instead)
- When a GIF or animated SVG would accomplish the same thing with less weight

**The test:** Does motion add emotion, clarity, or attention that a still image can't? If yes, generate. If the still version communicates the same thing, skip video.

## The Video Prompt Structure

Video prompts have five dimensions. These replace the image dimensions (subject, scene, style, mood, composition) with motion-native equivalents.

### 1. Shot Type and Framing

How the camera frames the subject. This sets the emotional distance.

| Shot | What It Shows | Emotion |
|------|--------------|---------|
| **Wide / establishing** | Full environment, subject small | Context, scale, setting the scene |
| **Medium** | Subject from waist up, some environment | Neutral, conversational, balanced |
| **Close-up** | Face or object fills frame | Intimacy, detail, importance |
| **Extreme close-up** | Eyes, hands, a single UI element | Tension, focus, revealing detail |
| **POV** | Camera is the subject's eyes | Immersion, "you are here" |
| **Over-the-shoulder** | Looking past one subject at another | Relationship, dialogue, context |

### 2. Camera Movement

The most impactful dimension in video. Camera movement IS emotion.

| Movement | What It Does | Feeling |
|----------|-------------|---------|
| **Static** | Camera doesn't move | Stability, observation, letting the subject breathe |
| **Slow dolly in** | Camera glides toward subject | Building intimacy, drawing focus, revelation |
| **Dolly out / pull back** | Camera moves away from subject | Revealing context, ending, pulling away |
| **Pan** (left/right) | Camera rotates on axis | Scanning, following, showing breadth |
| **Tracking** | Camera follows subject movement | Energy, pursuit, journey |
| **Crane / aerial** | Camera moves up or down vertically | Drama, establishing, grandeur |
| **Handheld** | Slight shake, organic movement | Raw, documentary, authentic |

Don't combine multiple movements in one shot. "Dolly in while panning left and craning up" confuses the model. One primary movement per shot.

### 3. Subject Action

What moves within the frame. Describe the start state and end state explicitly.

- Weak: "A person working on a laptop"
- Strong: "A designer leans forward, clicks something on screen, then leans back with a satisfied expression. Her coffee cup sends up a thin trail of steam."

Describe what CHANGES. If the subject is static, say so. Unspecified action produces random, incoherent motion.

### 4. Environment and Lighting

Same principles as image generation, but add temporal awareness. Lighting can shift during a shot (sunrise, passing clouds, a screen illuminating a dark room). Specify if the environment should be static or alive.

### 5. Pacing and Duration

How long the shot lasts and what happens when. This is the dimension image prompting doesn't have.

- Specify duration: "5-second clip" or "10-second shot"
- Specify timing within the shot: "The camera holds for 2 seconds, then slowly dollies in over the remaining 3 seconds"
- Shorter is almost always better. Two crisp 4-second clips stitched together beat one muddy 8-second generation.

### Before/After

**Weak:** "A video of someone using a modern app on their phone"

**Strong:** "Medium shot, static camera. A person sits at a cafe table, phone in hand. They tap the screen, smile slightly, then look up at someone off-camera. Warm natural lighting from a window to the left, shallow depth of field blurring the cafe background. 5 seconds."

## The Image-to-Video Workflow

This is the single most important technique in this skill. Text-to-video is a lottery. Image-to-video is directed filmmaking.

**Why it works:** When you provide a start frame, you control the visual foundation: composition, color, style, subject appearance, lighting. The video model only needs to figure out motion, not everything at once. This dramatically improves consistency and quality.

**The workflow:**

1. **Generate the start frame** using the Image Generation skill. Apply the five image dimensions. Get the frame looking exactly right before adding motion.
2. **Write the motion prompt.** Describe ONLY what changes from the start frame: camera movement, subject action, environmental shifts. Do NOT re-describe what's already visible in the image.
3. **Generate the video** using the start frame as input.
4. **Evaluate** motion coherence, not just visual quality.

**What to describe in the motion prompt:**
- Camera movement (dolly, pan, track, static)
- Subject action (what the person/object does)
- Environmental changes (wind, lighting shift, particles)
- Duration

**What NOT to describe (it's already in the frame):**
- The subject's appearance
- The color palette
- The environment layout
- The style

**First frame + last frame:** Some models (Runway, Seedance) accept both a start and end frame. This gives you precise control over transitions. Generate both frames as images first, then let the model interpolate the motion between them.

**Start frame quality rules:**
- High resolution (the model downscales, it can't upscale)
- Clean composition (complex, cluttered frames produce incoherent motion)
- Leave room for the action (if the subject will move right, don't frame them at the right edge)

## Models: When to Use What

The video model landscape is more fragmented than images. Each model has a distinct personality.

| Model | Best For | Strength | Limitation |
|-------|----------|----------|------------|
| **Kling 3.0** | Multi-shot narratives, storyboards | Native multi-shot (up to 6), audio/dialogue, 4K@60fps, best value | Shorter max per shot (10-15s) |
| **Sora 2** | Cinematic single shots, physics-heavy scenes | Best physics simulation, most photorealistic motion | Inconsistent (~30% excellent rate), expensive, max 25s |
| **Runway Gen-4.5** | Precise creative control, professional editing | Motion Brush for pixel-level control, 4K upscale, longest output | Requires more manual direction |
| **Pika 2.0** | Quick social content, fun effects | Fastest generation (10-30s), intuitive, creative effects | Max 10s, less cinematic |
| **Seedance 2.0** | Multi-modal projects, high first-try quality | Accepts 12+ reference inputs (images, video, audio), 90%+ first-try quality | Newer, less community knowledge |
| **Veo 3.1** | Long-form, high-res, audio-native | 4K, native spatial audio, 60s+ chained output | Premium pricing |

### Selection Edge Cases

**When someone asks for a specific model:** Use it, but flag if another model would produce meaningfully better results. "I'll use Pika for this. Worth noting Kling would handle the multi-shot storyboard better if we want to try that."

**When you don't have access to the ideal model:** Be transparent about the tradeoff. Use what you have. Adjust expectations around what's achievable.

**Platform-specific optimization:** Match aspect ratio and duration to the target platform. 9:16 for TikTok/Reels/Shorts (max 60s, hook in first 2s). 16:9 for YouTube (any length). 1:1 for feed posts. 4:5 for Instagram feed video. Generate in the target ratio from the start. Cropping after generation wastes composition.

**Default behavior:** Start with Kling for most tasks. It offers the best balance of quality, multi-shot capability, and cost. Switch when you hit a specific limitation.

## Shot Planning and Pacing

The part AI agents completely miss. Video is not one long generation. It's a sequence of intentional shots.

**Think in shots, not clips.** Before generating anything, plan the shot list:

```
Shot 1 (3s): Wide establishing shot, slow dolly in. Empty dashboard, cursor blinking.
Shot 2 (2s): Close-up on the "Import Data" button. Finger clicks it.
Shot 3 (3s): Medium shot, data populates the dashboard. Charts animate in from left.
Shot 4 (2s): Close-up on user's face. Slight smile, nod.
```

**Duration guidelines:**
- Social content: 2-4 seconds per shot. Total 10-30 seconds.
- Product demos: 3-5 seconds per shot. Total 15-60 seconds.
- Cinematic/brand: 4-8 seconds per shot. Total 30-120 seconds.

**The shorter-is-better rule:** Models produce more coherent output in shorter durations. Two sharp 4-second clips stitched in post produce better results than one 8-second generation that degrades halfway through. Generate short, stitch together.

**Transition planning:** Decide how shots connect BEFORE generating. Match the ending composition of shot 1 to the starting composition of shot 2. Use the last frame of one generation as the start frame reference for the next.

## Video Types: How Prompting Changes

**Product demos:** Shot-list approach. Wide establishing shot of the product, then close-ups of key interactions. Keep camera movement minimal. Let the product be the star. Use screen recordings where possible and generated video only for concept/pre-build visualization.

**Social media clips (TikTok, Reels, Shorts):** Hook in the first frame. Fast pacing (2-3s per shot). Bold, attention-grabbing composition. Vertical 9:16 aspect ratio. The first frame becomes the thumbnail on most platforms, so make it visually compelling.

**Hero section backgrounds:** Subtle is everything. Slow, ambient motion: floating particles, gentle camera drift, soft light shifts. No subject action. No dramatic camera moves. The video should feel like a living photograph, not a movie scene. Loop-friendly endings (last frame matches first frame).

**Ad creatives:** Structure as: hook (1-2s), value (3-5s), CTA (2-3s). The hook shot is the most important. Bold composition, unexpected motion, or a visually arresting moment. The value shots show the product or benefit. The CTA shot should be clean with clear text (use Nano Bana Pro to generate the CTA frame, then animate subtly).

**Animated illustrations:** Start with a strong illustration (Image Generation skill), then add minimal, purposeful motion. A character blinking, particles floating, a subtle parallax shift. Less is more. Over-animating a beautiful illustration makes it feel cheap.

## The Video Iteration Loop

Adapted from the image iteration loop, but with video-specific evaluation criteria.

1. **Plan the shot list.** Define each shot: framing, camera movement, subject action, duration.
2. **Generate start frames** for each shot using Image Generation. Get the visual foundation right.
3. **Generate the video** shot by shot, using image-to-video when possible.
4. **Evaluate each shot against these criteria:**
   - Motion coherence: does movement feel natural and intentional?
   - Subject consistency: does the subject look the same throughout?
   - Camera smoothness: is the camera movement fluid or jittery?
   - Pacing: does the shot feel the right length?
   - Physics: do objects interact realistically (gravity, fabric, water)?
5. **If 60%+ correct:** Try editing (describe what to change) or extending rather than full re-generation. Video generation is expensive in time and credits.
6. **If fundamentally wrong:** Check whether the issue is the start frame or the motion prompt. Fix one at a time.
7. **Stitch approved shots** in your video editor or platform.

**Know when to stop.** Video iteration burns more time and credits than image iteration. If the shot communicates what it needs to, ship it. Perfect is the enemy of shipped.

## What Makes Video Striking

**Camera movement as emotion.** A slow dolly-in creates intimacy. A fast tracking shot creates energy. A static shot creates calm observation. The camera's relationship to the subject IS the storytelling. Don't default to "slow pan" on everything.

**The first frame is the thumbnail.** On every platform, the first frame (or a selected frame) is the preview image. Compose the first frame of every shot as if it were a standalone image. If the thumbnail isn't compelling, nobody presses play.

**Unexpected pacing.** Fast content with one slow-motion moment creates contrast that grabs attention. A speed ramp (normal speed to slow to normal) at the climax adds drama. Monotonous pacing, even at a fast tempo, becomes wallpaper.

**Purposeful stillness.** The most striking moment in a video is sometimes when everything stops. A held frame after action, a static shot after a sequence of movement. Stillness creates weight. Don't fill every second with motion.

**Sound design cues.** For models that support audio (Kling 3.0, Seedance 2.0, Veo 3.1), specify ambient sound, effects, and music mood. "Soft ambient electronic music, the click of a keyboard, a notification chime" turns a visual into an experience. Audio-native models produce dramatically more immersive output when given sound direction.

## Anti-Patterns

| Pattern | Fix |
|---------|-----|
| "A video of X" (image prompt with "video" added) | Write shot directions: framing, camera movement, subject action, duration. |
| One long generation hoping for the best | Plan a shot list. Generate short clips. Stitch together. |
| Text-to-video for everything | Use image-to-video. Generate the start frame first, then animate. |
| Random camera movement (no direction specified) | Specify exactly one camera movement per shot. Static is a valid choice. |
| Over-animating illustrations | Subtle motion (blink, float, parallax) keeps the illustration's quality. Too much makes it cheap. |
| Same pacing throughout | Vary shot duration. Use stillness for contrast. Fast-slow-fast is more engaging than fast-fast-fast. |
| Generating in wrong aspect ratio then cropping | Generate in the target platform's aspect ratio from the start. |
| Ignoring the first frame | Compose it like a standalone image. It's the thumbnail. |

## Composability

This skill handles video-specific craft. It pairs with:

- Load **Image Generation** to create start frames for the image-to-video workflow
- Load **Prompting Fundamentals** for the universal iteration loop, debugging stack, and model selection principles
- Load **UI/UX Design Sense** when video is part of a product interface (hero sections, onboarding, empty states)
- Load **Software Polish** to evaluate whether generated video meets the quality bar before shipping
