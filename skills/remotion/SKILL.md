---
name: remotion
description: "Remotion video production system. Use when creating programmatic video, building video templates, rendering social content (TikTok/Reels/ads), or working with audio/captions/animations in Remotion. NOT for non-Remotion editing (ffmpeg), live streaming, or AI video generation (Veo)."
---

# Remotion Mastery — Complete Video Production System

## Architecture Overview

Remotion = React components that render to video frames. Every frame is a screenshot of your React app at a specific point in time. This mental model is everything.

```
Project Structure (canonical):
├── src/
│   ├── Root.tsx              # Composition registry (all videos defined here)
│   ├── compositions/         # One folder per video type
│   │   ├── QuoteVideo/
│   │   │   ├── index.tsx     # Main composition component
│   │   │   ├── Scene1.tsx    # Individual scenes
│   │   │   ├── Scene2.tsx
│   │   │   └── schema.ts     # Zod props schema
│   │   └── MotionAd/
│   │       ├── index.tsx
│   │       └── schema.ts
│   ├── components/           # Reusable across compositions
│   │   ├── AnimatedText.tsx
│   │   ├── CaptionOverlay.tsx
│   │   ├── Background.tsx
│   │   └── Counter.tsx
│   ├── hooks/                # Custom hooks
│   │   ├── useStagger.ts
│   │   └── useCaptions.ts
│   └── lib/                  # Utilities
│       ├── colors.ts
│       └── timing.ts
├── public/                   # Static assets (audio, video, images, fonts)
│   ├── audio/
│   ├── video/
│   └── fonts/
├── scripts/                  # Generation scripts (voiceover, captions, pipeline)
│   ├── generate-voiceover.ts
│   └── transcribe.ts
├── remotion.config.ts
├── package.json
└── .env                      # API keys (ELEVENLABS_API_KEY, etc.)
```

## The Five Commandments

1. **ALL animation driven by `useCurrentFrame()`** — CSS transitions, CSS animations, and Tailwind animation classes are FORBIDDEN. They don't render correctly across frames.

2. **Always premount Sequences** — `<Sequence premountFor={1 * fps}>` prevents flash-of-empty on the first frame of each sequence.

3. **Time in seconds, convert to frames** — Write `2 * fps` not `60`. Human-readable code, machine-accurate frames.

4. **Assets in `public/`** — Everything accessed via `staticFile()` lives in `public/`. Remote URLs work too but are slower to render.

5. **Clamp your interpolations** — Always add `{ extrapolateRight: 'clamp', extrapolateLeft: 'clamp' }` unless you specifically want values to extrapolate beyond the range.

## Animation System

### The Three Animation Primitives

Everything in Remotion reduces to three tools:

```tsx
import { interpolate, spring, Easing, useCurrentFrame, useVideoConfig } from 'remotion';

const frame = useCurrentFrame();
const { fps } = useVideoConfig();

// 1. interpolate — linear mapping between ranges
const opacity = interpolate(frame, [0, 30], [0, 1], {
  extrapolateRight: 'clamp',
});

// 2. spring — physics-based (0 to 1) with optional bounce
const scale = spring({ frame, fps, config: { damping: 200 } });

// 3. Easing + interpolate — curved timing
const slide = interpolate(frame, [0, 30], [-100, 0], {
  easing: Easing.out(Easing.quad),
  extrapolateRight: 'clamp',
});
```

### Spring Presets (use these, don't reinvent)

```tsx
const SPRINGS = {
  smooth:  { damping: 200 },                          // No bounce. Reveals, fades, slides.
  snappy:  { damping: 20, stiffness: 200 },            // Minimal bounce. UI elements, counters.
  bouncy:  { damping: 8 },                             // Playful bounce. Celebrations, emojis.
  heavy:   { damping: 15, stiffness: 80, mass: 2 },    // Slow, weighty. Large objects, backgrounds.
  elastic: { damping: 5, stiffness: 150 },              // Pronounced overshoot. Attention-grabbers.
} as const;
```

### Stagger Pattern (for lists, grids, sequences of elements)

```tsx
const useStagger = (index: number, delayPerItem = 5) => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();
  return spring({
    frame,
    fps,
    delay: index * delayPerItem,
    config: { damping: 200 },
  });
};

// Usage:
{items.map((item, i) => {
  const progress = useStagger(i);
  return (
    <div style={{
      opacity: progress,
      transform: `translateY(${interpolate(progress, [0, 1], [20, 0])}px)`,
    }}>
      {item}
    </div>
  );
})}
```

### Enter/Exit Pattern

```tsx
const useEnterExit = (enterDuration = 1, exitDuration = 1) => {
  const frame = useCurrentFrame();
  const { fps, durationInFrames } = useVideoConfig();

  const enter = spring({ frame, fps, durationInFrames: enterDuration * fps, config: { damping: 200 } });
  const exit = spring({
    frame,
    fps,
    delay: durationInFrames - exitDuration * fps,
    durationInFrames: exitDuration * fps,
    config: { damping: 200 },
  });

  return enter - exit; // 0 → 1 → 0
};
```

## Scene Architecture

### Composition Registration (Root.tsx)

```tsx
import { Composition, Folder } from 'remotion';
import { QuoteVideo } from './compositions/QuoteVideo';
import { quoteVideoSchema } from './compositions/QuoteVideo/schema';

export const RemotionRoot = () => (
  <>
    <Folder name="Ads">
      <Composition
        id="QuoteVideo"
        component={QuoteVideo}
        durationInFrames={360}
        fps={30}
        width={1080}
        height={1920}
        schema={quoteVideoSchema}
        defaultProps={{
          quoteText: "Every day is a day won.",
          backgroundVideo: "piano_dark.mp4",
          audioFile: "audio/piano/track1.mp3",
        }}
      />
    </Folder>
  </>
);
```

### Dynamic Duration with calculateMetadata

When video length depends on audio or data:

```tsx
import { CalculateMetadataFunction, staticFile } from 'remotion';
import { getAudioDuration } from '@remotion/media-utils';

const calculateMetadata: CalculateMetadataFunction<Props> = async ({ props }) => {
  const audioDuration = await getAudioDuration(staticFile(props.audioFile));
  return {
    durationInFrames: Math.ceil(audioDuration * 30) + 60, // +2s for outro
    props: { ...props, audioDurationFrames: Math.ceil(audioDuration * 30) },
  };
};
```

### Scene Sequencing Patterns

**Pattern 1: Series (scenes play back-to-back)**
```tsx
import { Series } from 'remotion';

<Series>
  <Series.Sequence durationInFrames={3 * fps}><Intro /></Series.Sequence>
  <Series.Sequence durationInFrames={5 * fps}><MainContent /></Series.Sequence>
  <Series.Sequence durationInFrames={2 * fps}><Outro /></Series.Sequence>
</Series>
```

**Pattern 2: TransitionSeries (scenes with crossfades/slides)**
```tsx
import { TransitionSeries, linearTiming } from '@remotion/transitions';
import { fade } from '@remotion/transitions/fade';
import { slide } from '@remotion/transitions/slide';

<TransitionSeries>
  <TransitionSeries.Sequence durationInFrames={90}>
    <Scene1 />
  </TransitionSeries.Sequence>
  <TransitionSeries.Transition
    presentation={fade()}
    timing={linearTiming({ durationInFrames: 15 })}
  />
  <TransitionSeries.Sequence durationInFrames={90}>
    <Scene2 />
  </TransitionSeries.Sequence>
</TransitionSeries>
```

**Pattern 3: Layered (persistent elements + sequenced content)**
```tsx
<AbsoluteFill>
  {/* Persistent background */}
  <Video src={staticFile('bg.mp4')} muted loop />

  {/* Persistent overlay */}
  <DarkOverlay opacity={0.7} />

  {/* Sequenced content on top */}
  <Series>
    <Series.Sequence durationInFrames={90}><QuoteText text="..." /></Series.Sequence>
    <Series.Sequence durationInFrames={60}><CTAFrame /></Series.Sequence>
  </Series>

  {/* Persistent audio (independent of visuals) */}
  <Audio src={staticFile('music.mp3')} volume={0.3} />
</AbsoluteFill>
```

**Duration math with transitions:** Total = sum of all sequence durations MINUS each transition duration. Two 60-frame scenes with a 15-frame transition = 105 frames, not 120.

## Audio & Voiceover

### Basic Audio

```tsx
import { Audio } from '@remotion/media';  // Install: npx remotion add @remotion/media

// Simple playback
<Audio src={staticFile('music.mp3')} />

// With fade-in
<Audio src={staticFile('music.mp3')}
  volume={(f) => interpolate(f, [0, fps], [0, 0.8], { extrapolateRight: 'clamp' })} />

// Trimmed + delayed
<Sequence from={2 * fps}>
  <Audio src={staticFile('narration.mp3')} trimBefore={1 * fps} />
</Sequence>
```

### ElevenLabs Voiceover Pipeline

See `references/voiceover-pipeline.md` for the full generation script.

Core flow:
1. Write script → split into scenes
2. Generate audio per scene via ElevenLabs API (`eleven_multilingual_v2` model)
3. Save to `public/voiceover/{compositionId}/{sceneId}.mp3`
4. Use `calculateMetadata` to measure durations and size the composition
5. Pass `sceneDurations` array as a prop to the component

### Audio Visualization

```tsx
import { useWindowedAudioData, visualizeAudio } from '@remotion/media-utils';

// Frequency spectrum (bar visualizer)
const { audioData, dataOffsetInSeconds } = useWindowedAudioData({
  src: staticFile('music.mp3'), frame, fps, windowInSeconds: 30,
});

const frequencies = visualizeAudio({
  fps, frame, audioData, numberOfSamples: 256,
  optimizeFor: 'speed', dataOffsetInSeconds,
});

// Bass-reactive: average the low frequencies
const bass = frequencies.slice(0, 32).reduce((s, v) => s + v, 0) / 32;
const pulseScale = 1 + bass * 0.5;
```

## Captions & Subtitles

### Full Pipeline

```
1. Generate narration audio (ElevenLabs)
2. Transcribe to captions (Whisper.cpp via @remotion/install-whisper-cpp)
3. Save captions.json to public/
4. Display with TikTok-style pages + word highlighting
```

### Transcription Script

```bash
# Install whisper and transcribe
npx remotion add @remotion/install-whisper-cpp
node --env-file=.env scripts/transcribe.ts
```

### Displaying Captions

```tsx
import { createTikTokStyleCaptions } from '@remotion/captions';

const SWITCH_EVERY_MS = 1200; // How often captions page

const { pages } = createTikTokStyleCaptions({
  captions,
  combineTokensWithinMilliseconds: SWITCH_EVERY_MS,
});

// Render each page in a Sequence
{pages.map((page, i) => {
  const next = pages[i + 1];
  const from = (page.startMs / 1000) * fps;
  const to = Math.min(
    next ? (next.startMs / 1000) * fps : Infinity,
    from + (SWITCH_EVERY_MS / 1000) * fps,
  );
  return (
    <Sequence key={i} from={from} durationInFrames={to - from}>
      <CaptionPage page={page} />
    </Sequence>
  );
})}
```

### Word Highlighting

```tsx
const CaptionPage: React.FC<{ page: TikTokPage }> = ({ page }) => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();
  const absoluteTimeMs = page.startMs + (frame / fps) * 1000;

  return (
    <div style={{ fontSize: 80, fontWeight: 'bold', whiteSpace: 'pre', textAlign: 'center' }}>
      {page.tokens.map((token) => {
        const active = token.fromMs <= absoluteTimeMs && token.toMs > absoluteTimeMs;
        return (
          <span key={token.fromMs} style={{
            color: active ? '#39E508' : 'white',
            textShadow: '0 2px 8px rgba(0,0,0,0.8)',
          }}>
            {token.text}
          </span>
        );
      })}
    </div>
  );
};
```

## Text, Charts, Media & Effects

For full code examples of these components, see `references/reusable-components.md`:
- **TypeWriter** — character-by-character reveal with blinking cursor
- **AnimatedCounter** — spring-based number counter (sobriety days, stats)
- **Animated Bar Chart** — staggered spring-driven bars
- **Animated Line/Path** — `evolvePath` for SVG path drawing

**Media embedding quick reference:**
- `<Video>` from `@remotion/media` — use `muted loop` for backgrounds, `playbackRate` for speed
- `<Img>` from `remotion` — use `staticFile()` for local assets
- `<Gif>` from `@remotion/gif` — animated GIF playback
- `<Audio>` from `@remotion/media` — volume can be a function of frame for fades

**Transitions:** `@remotion/transitions` provides `fade`, `slide`, `wipe`, `flip`, `clockWipe`. Use `TransitionSeries.Transition` between sequences. `@remotion/light-leaks` for premium WebGL overlays.

**Fonts:** `@remotion/google-fonts` (preferred, type-safe) or `@remotion/fonts` for local `.woff2` files.

## Rendering

### Standard Render Command

```bash
npx remotion render <composition-id> output.mp4 \
  --concurrency=7 \
  --timeout=120000 \
  --log=error
```

### With Props

```bash
npx remotion render QuoteVideo output/quote1.mp4 \
  --props='{"quoteText":"Make every day count.","audioFile":"audio/piano/track1.mp3"}' \
  --concurrency=7 \
  --timeout=120000
```

### Common Output Formats

| Platform | Width | Height | FPS | Codec | Notes |
|----------|-------|--------|-----|-------|-------|
| TikTok/Reels | 1080 | 1920 | 30 | h264 | 9:16 vertical, <60s |
| Instagram Feed | 1080 | 1080 | 30 | h264 | Square |
| Facebook Ad | 1080 | 1080 | 30 | h264 | Square performs best |
| YouTube Shorts | 1080 | 1920 | 30 | h264 | 9:16, <60s |
| YouTube | 1920 | 1080 | 30 | h264 | 16:9 |
| Story | 1080 | 1920 | 30 | h264 | 9:16, <15s |
| Transparent | any | any | 30 | vp8 | WebM with alpha |

### Performance Notes (this machine)

- `--concurrency=7` is stable (tested). Above 7 may OOM.
- `--image-format=jpeg` saves ~30% render time for non-transparent compositions.
- A 60s@30fps video = 1800 frames ≈ 4-6 min at concurrency 7.
- If OOM: drop to `--concurrency=4`.

### Environment Setup

```bash
export PATH="$HOME/bin:$HOME/npm-global/bin:$PATH"
export LD_LIBRARY_PATH="$HOME/lib:${LD_LIBRARY_PATH:-}"
```

## Production Pipeline Template

### Batch Video Generation

```bash
#!/bin/bash
# Generate multiple videos from a JSON config
CONFIG_FILE=$1
OUTPUT_DIR=${2:-output}
mkdir -p "$OUTPUT_DIR"

# Read each video config and render
cat "$CONFIG_FILE" | jq -c '.videos[]' | while read -r video; do
  ID=$(echo "$video" | jq -r '.id')
  PROPS=$(echo "$video" | jq -c '.props')
  COMP=$(echo "$video" | jq -r '.composition // "QuoteVideo"')

  echo "Rendering $ID..."
  npx remotion render "$COMP" "$OUTPUT_DIR/${ID}.mp4" \
    --props="$PROPS" \
    --concurrency=7 \
    --timeout=120000 \
    --log=error

  echo "Done: $OUTPUT_DIR/${ID}.mp4"
done
```

### Full Pipeline: Script → Voice → Captions → Render

```
1. Write script (or pull from Notion DB)
2. Generate voiceover: node --env-file=.env scripts/generate-voiceover.ts
3. Transcribe to captions: node scripts/transcribe.ts
4. Render: npx remotion render CompositionId output.mp4 --props='{...}'
5. (Optional) Upload to platform via API
```

## Common Pitfalls

| Pitfall | Fix |
|---------|-----|
| CSS animations/transitions | Use `useCurrentFrame()` + `interpolate`/`spring` only |
| Tailwind animate classes | Forbidden. Drive animation from frame. |
| Forgetting `premountFor` on Sequence | Always add `premountFor={fps}` |
| Not clamping interpolation | Add `extrapolateRight: 'clamp'` |
| Flash of unstyled text | Load fonts before render with `waitUntilDone()` |
| Audio not playing in render | Ensure file exists in `public/`, check path casing |
| Black frames | Asset not loaded yet. Use `useDelayRender()` |
| OOM during render | Reduce `--concurrency` (try 4, then 2) |
| Caption desync | Use `whiteSpace: 'pre'` and match timing to audio precisely |
| Transition shortens timeline | Account for overlap: total = sum(sequences) - sum(transitions) |
| `useCurrentFrame()` in Sequence children | Returns LOCAL frame (0-based within the Sequence), not global |

## Companion Skills

| Need | Load |
|------|------|
| API reference | Check Remotion docs at remotion.dev for specific component APIs |
| Render optimization | Tune concurrency, codec, and memory for your environment |
| Your custom compositions | Your project-specific composition skills |
| Motion ad pipeline | Combine AI image/video generation with Remotion overlays |
| AI video generation | Use Veo, Runway, or other AI video tools for backgrounds |
| Extracting frames from video | Use ffmpeg to extract frames or clips |

## Quick Reference: Package Installation

```bash
# Core (already in project)
npx remotion add @remotion/media           # <Audio>, <Video>
npx remotion add @remotion/captions        # Caption processing
npx remotion add @remotion/transitions     # TransitionSeries, fade, slide, wipe
npx remotion add @remotion/light-leaks     # WebGL light leak effects
npx remotion add @remotion/paths           # SVG path animation (evolvePath)
npx remotion add @remotion/media-utils     # Audio visualization, duration
npx remotion add @remotion/google-fonts    # Type-safe Google Fonts
npx remotion add @remotion/fonts           # Local font loading
npx remotion add @remotion/gif             # GIF playback
npx remotion add @remotion/rive            # Rive animations
npx remotion add @remotion/shapes          # Geometric shapes (<Triangle>, <Star>)
npx remotion add @remotion/tailwind        # Tailwind CSS integration
npx remotion add @remotion/install-whisper-cpp  # Local transcription
```
