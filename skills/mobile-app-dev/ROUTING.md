# Mobile App Development — Skill Router

Load skills based on your current task. Most projects need multiple skills across phases. Each SKILL.md is lean (<300 lines) with detailed content in `references/` — load reference files only when you need the deep dive.

## Skills

### `skills/app-brainstorm/SKILL.md`
**Load when:** Exploring what app to build, analyzing a market/category, brainstorming concepts, remixing engagement mechanics from one category into another, or evaluating whether an app idea is viable.
**Covers:** Market teardown framework (competitor mapping, feature matrix, review mining, gap analysis), engagement primitive library (~65 proven mechanics across 14 categories with psychology + examples), remix engine (5-step process for combining primitives into new concepts), concept validation checklist, structured output format. References: `feature-primitives.md` (full database), `market-teardown.md` (analysis playbook).

### `skills/app-prototyping/SKILL.md`
**Load when:** Building a visual prototype, mockup, or clickable demo. Showing the stakeholder what an app concept looks like before writing React Native code. Iterating on screen designs, flows, or visual direction.
**Covers:** Prototyping workflow, boilerplate starter kit, Tailwind mobile UI components (buttons, cards, tab bars, list rows, progress rings, paywalls), design taste gates (3-second test, screenshot test, squint test), iOS patterns (safe areas, navigation, sheets), screen templates for 16 common screen types, visual design rules (typography, color, spacing, animation), rapid iteration protocol.

### `skills/react-native-foundations/SKILL.md`
**Load when:** Setting up a project, making architecture decisions, choosing packages, configuring EAS builds, optimizing performance, or debugging React Native / Expo issues.
**NOT for:** UI design decisions (→ s-tier-design), onboarding flows (→ onboarding-mastery), retention mechanics (→ retention-engineering).
**References:** architecture-patterns, performance-optimization, native-features, testing-and-deployment, security, common-pitfalls.

### `skills/onboarding-mastery/SKILL.md`
**Load when:** Designing FTUE, placing paywalls, optimizing trial-to-paid conversion, A/B testing onboarding, or building permission priming sequences.
**NOT for:** Retention post-onboarding (→ retention-engineering), ad creative production (→ viral-features), visual design (→ s-tier-design).
**References:** psychology-mechanisms, case-studies, modern-patterns, paywall-tools, recovery-app-onboarding, metrics-and-testing.

### `skills/viral-features/SKILL.md`
**Load when:** Designing features for organic growth, planning ad creative production, building sharing/referral mechanics, selecting ad platforms, or evaluating feature ad-readiness.
**NOT for:** Onboarding flows (→ onboarding-mastery), retention mechanics (→ retention-engineering), visual design (→ s-tier-design).
**References:** case-studies, meta-playbook, tiktok-playbook, apple-ads-playbook, ai-creative-pipeline, referral-and-aso.

### `skills/retention-engineering/SKILL.md`
**Load when:** Building habit loops, setting retention targets, designing push notification strategy, planning subscription economics, building re-engagement flows, or optimizing D1/D7/D30.
**NOT for:** Onboarding/FTUE (→ onboarding-mastery), ad creative (→ viral-features), visual design (→ s-tier-design).
**References:** benchmarks-2026, behavioral-science, notification-strategy, monetization, re-engagement, recovery-app-playbook, measurement.

### `skills/s-tier-design/SKILL.md`
**Load when:** Making visual design decisions, choosing typography/color/spacing, designing animations and micro-interactions, implementing haptics, evaluating design against Apple/Google standards, or aiming for App Store editorial featuring.
**NOT for:** Code architecture (→ react-native-foundations), onboarding UX flows (→ onboarding-mastery), retention mechanics (→ retention-engineering).
**References:** liquid-glass-and-material3, typography-and-fonts, color-and-theming, motion-design, haptics, accessibility, case-studies, figma-to-code.

## Typical Loading Patterns

| Task | Primary Skill | Companion Skills |
|------|--------------|-----------------|
| Figuring out what to build | app-brainstorm | viral-features, retention-engineering |
| Exploring a new app concept | app-prototyping | s-tier-design |
| Starting a new app (production) | react-native-foundations | s-tier-design, onboarding-mastery |
| Prototyping screens | app-prototyping | s-tier-design |
| Designing onboarding | onboarding-mastery | app-prototyping, s-tier-design |
| Planning ad creatives | viral-features | — |
| Optimizing retention | retention-engineering | viral-features (for re-engagement creative) |
| Full app build (all phases) | All 6 in sequence | Load per phase, not all at once |

## System Boundaries

These 7 skills have clear, non-overlapping territories:
- **app-brainstorm** = WHAT to build (market analysis, feature primitives, concept generation)
- **app-prototyping** = WHAT it looks like (rapid HTML/CSS mockups, iteration workflow)
- **react-native-foundations** = HOW to build (code, architecture, deployment)
- **s-tier-design** = HOW it looks and feels (visual, motion, haptic)
- **onboarding-mastery** = FIRST experience (FTUE through first paywall)
- **retention-engineering** = ONGOING engagement (Day 2+ through graduation)
- **viral-features** = GROWTH engine (organic loops + paid acquisition)

Paywall strategy lives in onboarding-mastery (placement/conversion). Subscription economics lives in retention-engineering (churn/renewal). Notifications for onboarding (permission priming) live in onboarding-mastery. Notifications for retention (re-engagement) live in retention-engineering. This boundary is deliberate.
