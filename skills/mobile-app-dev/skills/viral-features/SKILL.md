---
name: viral-features
description: "Guide to designing app features that create organic sharing loops AND perform in paid ad campaigns across Meta, TikTok, and Apple Ads (2026). Use when designing features for organic growth, planning ad creative production, building referral/sharing mechanics, selecting ad platforms, or evaluating feature 'ad-readiness.' NOT for onboarding flows (use onboarding-mastery), retention mechanics post-onboarding (use retention-engineering), visual design specs (use s-tier-design), or deep linking / animation implementation (use react-native-foundations)."
---

# Viral Features & Ad-Ready Design

## The Six Engines of Organic Virality

Every growth feature should map to at least one engine:

**1. Inherent Share Triggers** — Artifacts users share without prompting.
- Visual progression (streak flames, Life Trees, growing pets)
- Achievement cards (milestone graphics with personalized stats, optimized for Stories 1080×1920)
- Identity results (Wrapped-style summaries, "Your Recovery Type" quizzes)
- Before/after transformations (quantified change proving the app works)
- *Design test:* Remove the share button. Would users still screenshot it?

**2. Collaborative Loops** — Features requiring multiple people to function.
- Accountability partners, group challenges, shared dashboards, small-group leaderboards

**3. FOMO & Curiosity** — Information asymmetry pulling non-users in.
- Anonymous reveals (Gas: "someone voted you..."), time-limited content (BeReal), gated social proof, waitlist/geo launches

**4. Referral Incentives** — Structured two-sided reward programs.
- Reduces CAC 25-35%. Referred users: +37% retention, +16% LTV
- Gamified tiers increase volume 33%
- → See `references/referral-and-aso.md` for reward structures and program design

**5. Platform-Native Content Creation** — Users become creators with your branding baked in.
- Auto-generated recap graphics, screen-recording-worthy animations, watermarked exports, template systems

**6. Designed Constraints** — Artificial limits that force sharing behavior.
- BeReal's 2-minute window, Gas's anonymity, QUITTR's provocative positioning
- Constraints create recognizable visual signatures that spread as meme templates across platforms
- *Design test:* What rule or limitation would make users talk about this feature?

## Modular Creative Framework

Five interchangeable modules — swap any piece independently to generate 10-20 variations/week from the same assets:

```
[HOOK 0-3s] + [PROBLEM 3-8s] + [SHOWCASE 8-18s] + [PROOF 18-25s] + [CTA 25-30s]
```

The system's value is combinatorial: 5 hooks × 4 problems × 3 showcases × 3 proofs × 3 CTAs = 540 unique ads from ~18 assets. Refresh individual modules (hooks weekly, proofs every 2-3 weeks) without rebuilding entire ads.

**Recovery-specific problem angles** (rotate by audience segment):
- Accountability gap: "No one held me accountable at 3am"
- App fatigue: "Every app felt like homework"
- Cost barrier: "My therapist costs $200/hr"
- Shame avoidance: "I didn't want to tell anyone I was struggling"
- Relapse cycle: "I'd make it 2 weeks then start over"

## Creative Refresh Cadence

| Asset Type | Refresh Cycle | Fatigue Signal |
|---|---|---|
| Hooks | 7-14 days | CTR drops >20% from peak |
| Full videos | 3-4 weeks | CPI rises >30% from baseline |
| Static images | 2-3 weeks | Frequency hits 4.0+ |
| UGC testimonials | 4-6 weeks | Engagement below platform avg |

Budget: 15-20% of total ad spend → dedicated creative testing ($20-50/day per variation).

## Platform Selection Decision Tree

```
Is your primary goal CONVERSION (installs → subscription)?
  → YES: Meta (Advantage+ App Campaigns, best conversion infra)
  → NO: Is it AWARENESS / VIRAL REACH?
    → YES: TikTok (cheapest CPMs, discovery algorithm, viral ceiling)
    → NO: Is it HIGH-INTENT CAPTURE?
      → YES: Apple Ads (60%+ conversion on search, no ATT signal loss)

Hybrid strategy (recommended at scale):
  TikTok (awareness, cheap reach) → Retarget engagers on Meta (conversion) → Apple Ads (high-intent closers)
```

**When to use each:**
- *Meta*: Conversion-focused, retargeting, 25-55 demo, measurable ROAS
- *TikTok*: Awareness, viral moments, 16-34 demo, UGC campaigns, organic + paid flywheel
- *Apple Ads*: Highest intent, first-party data, no ATT loss, keyword-driven capture

## CPI Benchmarks by Platform (2026)

| Platform | Category | CPI Range | Notes |
|---|---|---|---|
| Meta | Health & Fitness (iOS) | $2.00-4.70 | Optimizable with strong creative |
| Meta | Health & Wellness (all) | $5.54-16.33 | High seasonal variance |
| Meta | Social apps | $2.00-5.50 | — |
| TikTok | Average | $1.75-4.00 | Cheaper CPM ($3-7 vs Meta $6-11) |
| Apple Ads | Median (all categories) | $1.80 | Search results placement |
| Apple Ads | Health & Fitness | $2.00-15.00+ | Varies by keyword competition |
| Apple Ads | Long-tail keywords | $1.00-3.00 | Best value |

## Features That Film Well (The Screen Recording Test)

For every feature ask: *"Would a screen recording of this get views on TikTok?"*

**What works on camera:**
- Streak counters with satisfying tick-over animations (99→100)
- Growing visual elements (trees, gardens, characters)
- Reveal mechanics with dramatic unveils
- Confetti/particle celebrations proportional to achievement
- Color transitions from muted→vibrant as progress increases

**Animation principles:** Bouncy > linear (spring animations feel alive). Anticipation before action (slight pull-back before card flip). Particle effects for celebrations (read well in compressed video).

## Pre-Build Gate (before designing any growth feature)

- [ ] Does this feature create a share artifact without a share button? (inherent shareability test)
- [ ] Would this look compelling in a 6-second vertical video?
- [ ] Which virality engine(s) does this map to? (must be ≥1 of the 6 above)
- [ ] Primary growth channel: Meta / TikTok / Apple Ads / Organic (pick primary)
- [ ] Creative production system: AI UGC / Human UGC / Motion graphics / Mix
- [ ] Refresh cadence committed: hooks every ___days, full videos every ___days
- [ ] Referral incentive: what does referrer get? What does new user get?
- [ ] ASO keywords identified for App Store discoverability
- [ ] Handoff identified: onboarding-mastery (if FTUE-adjacent) / retention-engineering (if engagement-adjacent) / s-tier-design (if visual spec needed)

If any box is empty: STOP.

## Creative Launch Gate (before launching any ad campaign)

- [ ] Platform selected via decision tree above: ___
- [ ] ≥5 creative variations ready (modular framework: hook × problem × showcase × proof × CTA)
- [ ] Deferred deep links tested on real device (ad → App Store → install → correct screen)
- [ ] CPI target set: $___ (grounded in benchmark table above for platform + category)
- [ ] Kill rules defined: pause creative if CPI > ___× target after ___hours
- [ ] Refresh schedule in calendar: hooks every ___days, full videos every ___days
- [ ] Tracking verified: pixel/SDK + server-side (CAPI/S2S) + SKAdNetwork
- [ ] Store listing matches ad creative (CPP if available, screenshots aligned)

If any box is empty: do NOT spend money.

## References

| File | Contents |
|---|---|
| `references/case-studies.md` | QUITTR $100 meme ad, BeReal, Locket, Gas — detailed breakdowns with numbers |
| `references/meta-playbook.md` | Campaign structure, Advantage+ setup, creative best practices, tracking |
| `references/tiktok-playbook.md` | Organic + paid strategy, Spark Ads, content cadence, hybrid funnel |
| `references/apple-ads-playbook.md` | Keyword tiers, multi-slot expansion, ASO integration, relevance auction |
| `references/ai-creative-pipeline.md` | Tools, workflow, cost comparison (AI vs human UGC), production checklist |
| `references/referral-and-aso.md` | Referral program design, influencer playbook, ASO, deep linking, attribution |
