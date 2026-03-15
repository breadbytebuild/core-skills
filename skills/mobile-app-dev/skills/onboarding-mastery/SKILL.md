---
name: onboarding-mastery
description: "Playbook for designing app onboarding flows that maximize trial-to-paid conversion and Day 7 retention (2026 data). Use when designing FTUE, placing paywalls, optimizing trial flows, A/B testing onboarding, or building permission priming sequences. Specialized for health/wellness/addiction recovery apps. NOT for retention mechanics post-onboarding (use retention-engineering), implementation code/architecture (use react-native-foundations), ad creative (use viral-features), or visual design (use s-tier-design)."
---

# Onboarding Flow Mastery

Data-driven playbook for FTUE → trial → paid conversion. Benchmarks from RevenueCat (115K+ apps, $16B+ revenue), Superwall 2025, and Adapty.

## Conversion Benchmarks by Paywall Type

| Strategy | Median Conversion | Top 10% | Notes |
|----------|------------------|---------|-------|
| Hard paywall | 12.11% download-to-paid | 25%+ | Highest short-term revenue/install |
| Freemium | 2.18% download-to-paid | 5.6%+ | Larger user base, lower conversion |
| Reverse trial | 7-21% | — | Leverages loss aversion |

## Trial-to-Paid by Trial Length

| Trial Length | Median Trial-to-Paid |
|-------------|---------------------|
| ≤4 days | ~27% |
| 5-16 days | ~35% |
| 17-32 days | 45.7% |
| 7 days (standard) | ~38% |

**Key:** Longer trials (17-32 days) convert 70% better than ultra-short. For health/wellness where habit formation matters, consider 14-21 days.

## Trial-to-Paid by Category

| Category | Median | Top 25% |
|----------|--------|---------|
| Travel | 48.7% | — |
| Media & Entertainment | 43.8% | — |
| Health & Fitness | 39.9% | 68.3% |
| Business | 44.2% | — |
| Global average | 25.6% | — |

Health & Fitness: highest download-to-trial at 12.1%. Top performers hit 68.3% trial-to-paid.

## Onboarding Success Metrics

| Metric | Average | Target |
|--------|---------|--------|
| Day 1 retention | 25-28% | 35%+ |
| Day 7 retention | 17.86% | 25%+ |

**Critical:** 80-90% of trial starts happen on Day 0. Your onboarding IS your conversion event.

*D30+ retention, renewal rates, churn targets → `retention-engineering`.*

## Social Proof Data

- 5+ reviews displayed → up to 270% conversion increase
- Ratings 4.0-4.7 convert better than perfect 5.0 (suspicion effect)
- Video testimonials → up to 80% conversion lift
- Max 2-3 social proof moments during onboarding (more feels manipulative)

## Geography Conversion Gap

NA converts at 2.6% vs LATAM at <0.2%. Segment everything by geography.

---

## Decision Tree: Paywall Strategy

```
Is your core value deliverable in <60 seconds?
├─ YES → Freemium with contextual upgrade triggers
└─ NO → High-emotion problem (health, addiction, relationships)?
         ├─ YES → Post-quiz hard paywall with trial
         └─ NO → Premium meaningfully different from free?
                  ├─ YES → Reverse trial (14 days)
                  └─ NO → Freemium with upgrade triggers
```

## Decision Tree: Onboarding Length

```
Emotional weight of the problem?

LOW (utility, entertainment):
→ 3-5 screens, <60 seconds, immediate product experience

MEDIUM (fitness, productivity, learning):
→ 5-12 screens, 1-3 minutes, goal-setting + personalization

HIGH (addiction, mental health, major life change):
→ 12-40+ screens, 5-15 minutes, deep personalization quiz
→ Paywall AFTER personalized plan generation
```

## Decision Tree: Trial Length

```
Health & Fitness / Wellness / Recovery:
├─ Habit formation required? → 14-21 days
├─ Value obvious immediately? → 7 days
└─ Complex product requiring learning? → 21-30 days (45.7% conversion)
```

## Pricing Architecture (2026 Health/Wellness)

- **Annual:** $49.99-$69.99/yr (show as "$4.17/month") — pre-select this (68% of H&F users choose annual)
- **Monthly:** $9.99-$14.99/mo
- **Weekly:** $4.99-$7.48/wk — drives 55% of all subscription revenue but terrible long-term retention. Consider for low-commitment entry point only.
- **Lifetime:** $149.99-$199.99 (for permanent-journey users)
- Show annual savings prominently: "Save 65%" or "Best Value"
- Introductory offer: 30-50% off first period

*Subscription economics, renewal optimization, pricing experiments → `retention-engineering`.*

---

## Pre-Build Gate

Walk each decision tree above, then fill in:

- [ ] Paywall strategy: Hard / Freemium / Reverse Trial → ___ (use Decision Tree: Paywall Strategy)
- [ ] Onboarding length: Short / Medium / Long → ___ (use Decision Tree: Onboarding Length)
- [ ] Trial length: ___ days (use Decision Tree: Trial Length)
- [ ] Permission priming: which permissions + sequence (see `references/psychology-mechanisms.md` § Permission Priming)
- [ ] "Aha moment": what specific action, by when in the flow → ___ (see `references/recovery-app-onboarding.md` § Phase 3 for examples)
- [ ] Paywall tool: Superwall / RevenueCat / Adapty / Custom (see `references/paywall-tools.md`)
- [ ] First A/B test variable identified (see `references/metrics-and-testing.md`)

**If any box is empty or unjustified: STOP. No building without decisions.**

---

## Build Checklist

### Pre-Build
- [ ] Map minimum path from install to aha moment (count screens, estimate seconds)
- [ ] Define subscription tiers and pricing (use Pricing Architecture above)
- [ ] Write onboarding question sequence (see `references/recovery-app-onboarding.md` for screen-by-screen blueprint)
- [ ] Design social proof elements (see `references/psychology-mechanisms.md` § Social Proof)
- [ ] Plan permission priming screens and timing (see `references/psychology-mechanisms.md` § Permission Priming)
- [ ] Set up analytics events for every onboarding interaction (see `references/metrics-and-testing.md` § Funnel)

### Build
- [ ] Implement flow with skip-ability (don't trap users)
- [ ] Integrate paywall SDK with remote config (no app update to change paywall)
- [ ] Analytics: screen views, time-on-screen, completion rates, drop-off points
- [ ] A/B testing infrastructure (or paywall tool's built-in experiments)
- [ ] Fallback experiences for denied permissions
- [ ] Crisis resources accessible pre-paywall (addiction/recovery apps)
- [ ] End-to-end test on iOS + Android
- [ ] Accessibility audit (VoiceOver, TalkBack, contrast, 44x44pt touch targets)

### Post-Launch
- [ ] Baseline metrics for 2 weeks before optimization
- [ ] Monitor funnel daily for first 2 weeks
- [ ] Identify top 3 drop-off points
- [ ] First A/B test targeting highest-drop-off screen
- [ ] Cohort analysis: Day 7 retention by onboarding completion depth
- [ ] **Handoff:** Once onboarding is stable, D7+ optimization moves to `retention-engineering`

---

## Reference Files

| File | Content |
|------|---------|
| `references/psychology-mechanisms.md` | 6 psychological mechanisms with implementation patterns |
| `references/case-studies.md` | QUITTR, Noom, Duolingo, Calm, Finch detailed breakdowns |
| `references/modern-patterns.md` | AI-personalized onboarding, dynamic paywalls, multi-page paywalls, reverse trials, hybrid monetization |
| `references/paywall-tools.md` | Superwall vs RevenueCat vs Adapty vs Purchasely — features, pricing, best-for |
| `references/recovery-app-onboarding.md` | Health/wellness/addiction-specific 6-phase architecture with screen-by-screen blueprint |
| `references/metrics-and-testing.md` | A/B testing methodology, metrics funnel, alert thresholds, compliance (HIPAA/GDPR) |

*Benchmarks from RevenueCat State of Subscription Apps 2025, Superwall 2025 Year in Review, Adapty benchmarks. Re-validate annually.*
