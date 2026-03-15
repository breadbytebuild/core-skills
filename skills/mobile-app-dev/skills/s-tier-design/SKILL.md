---
name: s-tier-design
description: "Design guide for building Apple Design Award-quality mobile apps (2026). Use when making visual design decisions, choosing typography/color/spacing, designing animations and micro-interactions, implementing haptic feedback, evaluating design against Apple/Google standards, or aiming for App Store editorial featuring. Covers iOS 26 Liquid Glass + Material 3 Expressive. NOT for code architecture or animation implementation code (use react-native-foundations), onboarding UX flows (use onboarding-mastery), retention mechanics (use retention-engineering), or growth/virality mechanics (use viral-features). SHARED BOUNDARY: ad-ready visual design — features must meet this skill's visual standards AND viral-features' ad-readiness criteria."
---

# S-Tier App Design (2026)

## 2026 Design Landscape

Both Apple and Google converged on emotional, depth-rich, personality-forward design. Flat minimalism is over.

**iOS 26 — Liquid Glass:** visionOS aesthetics on flat screens. Translucency, dynamic lighting, floating elements, softer geometry. System components auto-adopt it; custom UI must harmonize. → [details](references/liquid-glass-and-material3.md)

**Android 16 — Material 3 Expressive:** 35 iconic shapes, bolder typography, livelier motion physics, on-device AI theming. → [details](references/liquid-glass-and-material3.md)

### Design Language Decision Tree

```
Is this iOS-only?
  YES → Adopt Liquid Glass fully. Use system components (they auto-adopt).
        Custom UI must harmonize (translucency, rounded geometry, depth layers).
  NO → Cross-platform (React Native)?
    YES → Build a unified design language that RESPECTS both platforms.
          Use platform-adaptive components (different feel, same brand).
          Don't force Liquid Glass on Android or Material on iOS.
    NO (Android-only) → Material 3 Expressive. Lean into expressive shapes + motion.
```

**2025 Apple Design Award lessons** (what judges rewarded):
- Physical-feeling interactions (CapWords) — UI should feel tangible, not flat
- Fluid gesture-driven UX (Taobao) — direct manipulation > button tapping
- ADHD-first visual design (Tiimo, iPhone AOTY) — visual timelines, color-coded blocks, reduced cognitive load
- Dense data rendered clearly under stress (Watch Duty)

→ [Full winner analysis](references/case-studies.md)

## Typography Decisions

Use system text styles (Apple HIG scale). The hard rules that actually get broken:

- **16pt min body** (18pt preferred for long-form). 12pt absolute floor (non-critical metadata only)
- **4.5:1 contrast** for normal text, 3:1 for ≥18pt bold
- **Single typeface family, 2-3 weights max** — more weights = visual noise
- **Custom font?** Must register with `UIFontMetrics` for Dynamic Type. If you skip this, accessibility breaks silently
- **Cross-platform RN:** Inter Variable or IBM Plex (not system fonts, which diverge iOS/Android)

→ [Full type scale, SF Pro variable font, SF Symbols 7, Dynamic Type](references/typography-and-fonts.md)

## Color & Spacing Decisions

**Dark mode** (the rules that actually get broken):
- **Never invert** — build a dedicated dark palette
- **Avoid pure #000000 backgrounds** — causes halation (text blur) and black smearing on scroll. Use #1C1C1E or #121212
- **Soft white text** (#E0E0E0 / 87% opacity) — pure #FFFFFF causes eye strain
- **Desaturate vibrant colors** — they look neon on dark. Reduce saturation 10-20%
- **Elevation = lighter surfaces** (shadows invisible on dark)

**Design token architecture** — use three tiers: Reference (raw values) → Semantic (purpose-mapped) → Component (context-specific). This is the difference between a theme that works and one that breaks when you add dark mode.

**Spacing:** 8px grid, no exceptions. Screen margins: 16px. List items: 44px min height (tap target).

→ [Full token architecture, dark mode surface hierarchy, RN theming (NativeWind/Tamagui/Restyle)](references/color-and-theming.md)

## Animation Decisions

### Spring Parameters (the only ones you need)

Default: `response: 0.5, dampingFraction: 0.7` (natural, subtle bounce). Adjust from there:
- **Snappier?** Lower response (0.3). Higher damping (0.8).
- **Bouncier?** Lower damping (0.5). Higher response (0.6).
- **Error/critical?** Overdamp it (damping 1.0). No bounce on bad news.
- **Danger zones:** damping < 0.5 = too bouncy. damping > 0.9 = why bother animating.

### Animation Engine Decision Tree

```
Does the animation respond to user input or app state?
  YES → Rive (state machines, GPU-rendered, 10-15x smaller files)
  NO → Is it a simple icon/loader/decorative element?
    YES → Lottie (team uses After Effects? → yes. Otherwise consider Rive)
    NO → Is it a code-driven UI transition?
      YES → Reanimated/SwiftUI springs (no external asset needed)
             → implementation details in react-native-foundations
```

**Hard rule:** Only animate `transform` and `opacity` (GPU-accelerated). Never layout properties in hot paths. Profile on lowest-supported device.

→ [Spring code, Reanimated v4, gesture-driven motion, reduced motion](references/motion-design.md)

## Haptic Design

**Decision framework:** Impact for physical interactions (taps, drags). Notification for state changes (success/warning/error). Selection for picker-like scrolling. Intensity should match action weight — `.light` for toggles, `.heavy` for destructive actions.

**The rules that get missed:**
- **Always call `.prepare()` before triggering** — eliminates perceptible latency
- **SwiftUI shortcut:** `.sensoryFeedback(.impact, trigger: value)` — no UIKit boilerplate needed
- **Choreography rule:** Haptic pulse at animation's moment of maximum change. Sound at T+50ms. All three channels (visual + haptic + audio) reinforce the same emotional message. This is what separates "has haptics" from "feels magical."

→ [Full haptic selection table, Core Haptics API, sensory choreography](references/haptics.md)

## Sibling Boundaries

**This skill** owns: visual design, typography, color, spacing, animation design, haptic design, accessibility.

| Boundary | This Skill | Sibling |
|---|---|---|
| Animation implementation (Reanimated code, worklets) | Defines *what* to animate + spring parameters | react-native-foundations owns the *how* |
| Onboarding screen design | Provides visual specs they reference | onboarding-mastery owns the UX flow |
| Ad-ready visuals | Sets visual quality bar: screenshot-worthy, high-contrast hero moments | viral-features owns ad strategy + creative production |
| Retention UI (streaks, badges) | Defines visual treatment | retention-engineering owns the mechanics |

**Ad-Ready Design Rule:** Every key screen should pass the "screenshot test" — would a user screenshot this to share? Would this frame work as an ad creative? If building a feature with growth potential, check viral-features' ad-readiness criteria alongside this skill's visual standards.

## Pre-Build Design Gate

- [ ] Design language: Liquid Glass (iOS 26) / Material 3 Expressive / Cross-platform — approach defined
- [ ] Typography: system fonts or custom? If custom, registered with UIFontMetrics?
- [ ] Color tokens: 3-tier system defined (reference → semantic → component)?
- [ ] Dark mode: dedicated palette (not inverted)? Tested contrast ratios?
- [ ] Animation engine: Rive / Lottie / Reanimated-only — picked for this project
- [ ] Haptic map: which interactions get which haptic type?
- [ ] Accessibility: VoiceOver labels, Dynamic Type to AX5, 44pt tap targets, Reduce Motion — all planned?
- [ ] App icon: designed for all sizes (29pt to 1024pt), tested in dark/tinted modes?
- [ ] Ad-readiness: do key screens screenshot/record well? High-contrast hero moments present? (coordinate with viral-features if growth feature)

If any box is empty: STOP. Design decisions before pixels.

## Pre-Launch Design QA

Priority order — fix higher tiers before polishing lower ones:

- [ ] **Tier 1 — Functional:** All animations 60fps on lowest-supported device. No layout clipping at AX5 Dynamic Type.
- [ ] **Tier 2 — Accessible:** VoiceOver navigable with meaningful labels. All tap targets ≥ 44×44pt. Reduce Motion provides static alternatives. Color contrast WCAG 2.2 AA.
- [ ] **Tier 3 — Polished:** Dark mode complete (dedicated palette, not inverted). Haptics on all significant interactions. Loading states use skeletons, not spinners alone. Empty states guide toward action.
- [ ] **Tier 4 — Delightful:** Sensory choreography (visual + haptic + audio aligned). Spring parameters tuned per context. Micro-interactions feel physical.
- [ ] **Tier 5 — Ad-Ready:** Key screens pass screenshot test. Hero moments high-contrast and visually striking. Screen recordings look compelling. (coordinate with viral-features)

Unchecked tier = not ready. Ship when all 5 pass.

→ [Expanded checklist with specific test cases](references/accessibility.md)

## Reference Files

| File | Contents |
|---|---|
| [liquid-glass-and-material3.md](references/liquid-glass-and-material3.md) | iOS 26 + Android 16 design language details, visionOS influence |
| [typography-and-fonts.md](references/typography-and-fonts.md) | SF Pro variable font, SF Symbols 7, Dynamic Type, cross-platform fonts |
| [color-and-theming.md](references/color-and-theming.md) | Token architecture, dark mode, RN theming (NativeWind/Tamagui/Restyle) |
| [motion-design.md](references/motion-design.md) | Spring animations, Rive vs Lottie deep dive, gesture-driven motion, reduced motion |
| [haptics.md](references/haptics.md) | Full haptic API reference, Core Haptics, sensory choreography |
| [accessibility.md](references/accessibility.md) | VoiceOver, Dynamic Type, neurodivergent design (Tiimo), EAA/WCAG compliance |
| [case-studies.md](references/case-studies.md) | Things 3, Not Boring Apps, Flighty, Gentler Streak, Watch Duty, Tiimo breakdowns |
| [figma-to-code.md](references/figma-to-code.md) | AI tools comparison, practical workflow, design system setup |
