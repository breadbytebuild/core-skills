---
name: react-native-foundations
description: "Production reference for React Native + Expo (2026). Use when: setting up a project, making architecture decisions (state, navigation, storage, data fetching), choosing packages, configuring EAS builds, optimizing performance, or debugging RN/Expo issues. NOT for: UI/visual design or motion design (use s-tier-design), onboarding flows or paywall strategy (use onboarding-mastery), retention mechanics or re-engagement (use retention-engineering), viral loops or growth features (use viral-features)."
---

# React Native + Expo: Production Foundations (2026)

## Current Versions (March 2026)

| Package | Version | Notes |
|---------|---------|-------|
| Expo SDK | 55 | Released Feb 25, 2026 |
| React Native | 0.83 | Latest stable (Dec 2025) |
| React | 19.2 | Ships with RN 0.83 |
| Expo Router | v55 (v7 lineage) | Versioned with SDK since 55 |
| Reanimated | 4.2.2 | Requires New Architecture + `react-native-worklets` |
| FlashList | 2.3.0 | JS-only rewrite, no native deps |
| Hermes | Default | Only supported JS engine |
| New Architecture | Mandatory | Only option since RN 0.82 |

## Pre-Build Gate

Answer every line before writing code. Empty boxes = stop and decide.

- [ ] Expo SDK version locked: ___
- [ ] State management: Zustand / Redux Toolkit / Jotai — choice: ___ justification: ___
- [ ] Navigation: Expo Router / React Navigation — choice: ___ justification: ___
- [ ] Data fetching: TanStack Query + ___ API layer
- [ ] Storage plan: what goes in expo-secure-store / MMKV / WatermelonDB: ___
- [ ] Error tracking: Sentry / Bugsnag / Crashlytics — choice: ___
- [ ] Testing: Unit (Jest+RNTL) + E2E (Maestro / Detox) — E2E choice: ___
- [ ] CI/CD: EAS Build + GitHub Actions configured: yes / no
- [ ] TypeScript strict mode enabled: yes / no

## Architecture Decision Tree

```
State management?
  → Simple app (<20 screens): Zustand (~1KB, 90% of apps)
  → Enterprise (50+ screens, large team): Redux Toolkit
  → Atomic/granular reactivity: Jotai

Navigation?
  → New project: Expo Router (always)
  → Existing project migrating: React Navigation 7, then migrate

Lists?
  → Any list >50 items: FlashList 2.x
  → Short lists (<20 items): ScrollView + map

Storage?
  → Secrets/tokens/PII: expo-secure-store (encrypted, keychain-backed)
  → User preferences: MMKV (synchronous, fast)
  → API cache: TanStack Query + MMKV persister
  → Large relational data: WatermelonDB
  → Simple non-critical: AsyncStorage

Error tracking?
  → Full-stack JS + RN: Sentry (best RN tooling, auto source maps with EAS)
  → Mobile-first, simple: Bugsnag
  → Firebase ecosystem, free: Crashlytics

E2E testing?
  → Most teams: Maestro (YAML, fast, low flake)
  → Deep RN integration: Detox (gray-box sync)
  → Multi-framework org: Appium (last resort)
```

## Expo SDK Timeline

| SDK | Date | React Native | Key Change |
|-----|------|-------------|------------|
| 52 | Nov 2024 | 0.76 | New Arch default |
| 53 | May 2025 | 0.79 | React 19, Router v5 |
| 54 | Sep 2025 | 0.81 | Router v6, Expo UI alpha |
| **55** | **Feb 2026** | **0.83** | **New Arch only, Router v7** |
| 56 | Q2 2026 | 0.85 | Planned |

Release cadence: Expo SDK 3x/year. RN ~6x/year.

## Key 2026 Gotchas

> Full details + code fixes: `references/common-pitfalls.md`

1. **Reanimated 4.x requires `react-native-worklets`** as peer dep — Reanimated 3.x is legacy-only
2. **FlashList 2.x removed `estimatedItemSize`** — delete it or get warnings
3. **Push notifications don't work in Expo Go** on Android (since SDK 53) — use dev builds
4. **`refetchOnWindowFocus`** is meaningless on mobile — set `false` in TanStack Query defaults
5. **Barrel exports break tree-shaking** — import from specific files, not index barrels
6. **`expo-image` replaces `react-native-fast-image`** — don't install both
7. **Validate API responses at the boundary** with Zod — never trust `response.json()` directly
8. **Tokens in MMKV/AsyncStorage = vulnerability** — use `expo-secure-store` for sensitive data
9. **Deep links work in dev, break in prod** — verify `assetlinks.json` / `apple-app-site-association`
10. **Android notification channels required** for 8+ — create before sending

## Pre-Ship Gate

Run through before any release build. Fail any = fix before shipping.

- [ ] Cold start < 2s in release build (test on real device, not simulator)
- [ ] List scroll 60fps with 100+ items (FlashList, no `estimatedItemSize` warnings)
- [ ] JS bundle < 2MB (`npx react-native-bundle-visualizer`)
- [ ] `npx expo-doctor` passes clean
- [ ] All `useEffect` hooks have cleanup returns (no memory leak vectors)
- [ ] No tokens/secrets in MMKV or AsyncStorage (only in `expo-secure-store`)
- [ ] Sentry/error tracking initialized and capturing in release mode
- [ ] Deep links verified with production `assetlinks.json` / `apple-app-site-association`
- [ ] Android notification channels created before any push is sent
- [ ] OTA update channel configured (`eas.json` channel matches `app.json` runtimeVersion)

## Boundary Clarifications

| Question | Where |
|----------|-------|
| Push notification *implementation*? | Here → `references/native-features.md` |
| Push notification *strategy/timing*? | retention-engineering |
| RevenueCat/IAP *integration code*? | Here → `references/native-features.md` |
| Paywall *screen design + conversion*? | onboarding-mastery |
| Subscription *economics/pricing*? | retention-engineering |
| Analytics *SDK setup*? | Here |
| *Growth loop* implementation? | viral-features |
| Animation/motion *design language*? | s-tier-design |
| Animation *technical implementation*? | Here → `references/performance-optimization.md` |

## Reference Files

Load on-demand based on what you're building:

| Topic | File |
|-------|------|
| File structure, navigation, state, TypeScript, package versions | `references/architecture-patterns.md` |
| Animations, lists, images, bundle, memory, profiling, perf budgets | `references/performance-optimization.md` |
| Push notifications, IAP/RevenueCat, deep linking, biometrics, a11y | `references/native-features.md` |
| Maestro/Detox/Appium, unit tests, EAS config, CI/CD, OTA updates | `references/testing-and-deployment.md` |
| Secure storage, API security, cert pinning, obfuscation | `references/security.md` |
| The 10 gotchas with full solutions + code | `references/common-pitfalls.md` |

---

*Last verified: March 7, 2026. Check [expo.dev/changelog](https://expo.dev/changelog) and [reactnative.dev/blog](https://reactnative.dev/blog) for updates.*
