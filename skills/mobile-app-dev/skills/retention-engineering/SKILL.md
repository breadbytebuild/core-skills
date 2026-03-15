---
name: retention-engineering
description: >
  Retention engineering for mobile apps: habit loops, retention targets, push notification strategy,
  subscription economics, re-engagement, and ethical recovery-app retention. 2025-2026 benchmarks.
  Use when: setting retention targets, designing habit loops, engineering push notifications,
  optimizing subscription/churn, building re-engagement flows, or designing recovery-app retention.
  NOT for: onboarding/FTUE/paywall placement/trial flows/permission priming (→ onboarding-mastery),
  ad creative/organic sharing loops (→ viral-features), visual/motion/haptic design (→ s-tier-design),
  code architecture/deployment (→ react-native-foundations).
---

# Retention Engineering

> Day 2 through graduation. Everything between first paywall and healthy churn.

## Pre-Build Gate

*Fill every box or stop.*

- [ ] **D30 target:** ___% (category benchmark: ___)
- [ ] **Core daily action:** ___ (completes in <30 seconds?)
- [ ] **Behavioral framework assigned:** Fogg (core features) / Hook (social) / SDT (long-term)
- [ ] **Notification tiers assigned:** iOS priority levels mapped per category
- [ ] **Streak includes safety net:** freeze/grace period designed
- [ ] **Subscription model chosen:** reverse trial / hard paywall / freemium — justified
- [ ] **Measurement configured:** D1/D7/D30 + behavioral cohorts
- [ ] **For recovery apps → Shame Test passed** (see below)

> ⚠️ Notification *permission priming* and *push primer design* → onboarding-mastery.
> This skill owns notification *content, timing, and priority classification* post-opt-in.

## Task Router

| You're doing… | Start here | Then load |
|---------------|-----------|-----------|
| Building a new retention feature | Pre-Build Gate above | Behavioral Framework Router below |
| Diagnosing a retention drop | Fogg Diagnostic below | `references/measurement.md` |
| Designing push notifications | Notification Strategy below | `references/notification-strategy.md` |
| Choosing subscription model | Subscription Economics below | `references/monetization.md` |
| Re-engaging lapsed users | Re-engagement Framework below | `references/re-engagement.md` |
| Recovery app work | Shame Test below | `references/recovery-app-playbook.md` |

*Recovery context? Apply the Shame Test to ANY of the above.*

---

## Retention Benchmarks (2026)

D1 >30% · D7 >15% · **D30 >8%** (2× H&F avg 3.7%) · D90 >4% · DAU/MAU >25%
Trial→Paid >40% (H&F median 39.9%, top 68.3%) · Monthly churn <8% · Push opt-in >60%

→ Full category breakdown + OS splits: `references/benchmarks-2026.md`

---

## Behavioral Framework Router

*The model knows Fogg/Hook/SDT. This routes the right framework to the right feature.*

| Feature Type | Framework | Why This One |
|-------------|-----------|-------------|
| Core daily actions | Fogg B=MAP | Three independent diagnostic levers |
| Social/community | Hook Model | Variable social rewards drive return |
| Long-term motivation | SDT | Sustains motivation without gamification |

### When Retention Drops — Fogg Diagnostic

```
Open but don't act   → Ability problem   → Simplify the action
Act but don't return → Motivation problem → Add reward/social
Want to but forget   → Prompt problem    → Fix notification timing
```

### Streak Rules (Non-Negotiable)

1. Safety net required (freeze/grace). No devastating resets.
2. Lower the bar: minimum viable action counts (+40% 7-day maintenance).
3. Track lifetime progress alongside current streak ("347 of 365 days").
4. Recovery: broken streak ≠ moral failure. Compassionate restart framing.

→ Case studies (Duolingo, I Am Sober, Nomo, Strava): `references/behavioral-science.md`

---

## Notification Strategy (Post-Opt-In)

### iOS 18 Priority Assignment

| Priority | Delivery | Assign To |
|----------|----------|-----------|
| Critical | Bypasses Focus (Apple entitlement required) | Crisis support only |
| Time-sensitive | Immediate, bypasses schedules | Craving alerts, accountability, streak warnings |
| Active | Standard delivery | Daily check-ins, milestones |
| Passive | Batched summaries | Community updates, weekly progress |

### Key Numbers

Personalized timing: **+40%** open rate. Event-triggered: **14.4%** vs **4.19%** generic.
Frequency >5/week: **64% stop using the app**. Best H&F: **7-9 AM** or **5-7 PM**, **Tuesday** peak.

### Pre-Send Checklist

- [ ] Priority level matches content urgency?
- [ ] Frequency stays ≤5/week for this user?
- [ ] Personalized timing (user's engagement window)?
- [ ] Deep-links to specific action (not app home)?
- [ ] For recovery: passes Shame Test?

→ Full platform details + Android 15 changes: `references/notification-strategy.md`

---

## Subscription Economics Decision Tree

```
User hasn't proven engagement yet?
  → Weekly plan (accept 65% 30-day churn as entry cost)

User active 2-3 weeks?
  → Monthly plan

User engaged monthly for 3+ months?
  → Nudge annual with "save X%" anchor

High-trust power user?
  → Offer lifetime (eliminates recurring churn, lower LTV tradeoff)
```

### Churn Countermeasures

- **Reverse trial** (full premium → loss aversion): 64% higher LTV
- **Pause > Cancel** ("take a 1-3 month break"): recovers significant % of cancellers
- **Daily value anchor on free tier**: reason to open even if subscription lapses
- **Never paywall during crisis**: non-negotiable for recovery apps

> ⚠️ Paywall *placement* and *conversion optimization* → onboarding-mastery.
> This skill owns subscription *plan structure, churn reduction, and renewal economics*.

→ Full monetization strategy: `references/monetization.md`

---

## Re-engagement Framework

### Win-Back Sequence (3-Touch)

| Touch | When | Approach |
|-------|------|----------|
| 1 | Day 7-10 inactive | Remind of THEIR progress. Deep-link to check-in. |
| 2 | Day 14-17 | Social proof + what's new. |
| 3 | Day 21-25 | Gentle urgency + offer. One-tap return. |

### Ambient Retention (No Notifications Needed)

| Surface | Impact | Use |
|---------|--------|-----|
| Home screen widget | Significantly higher retention | Daily visibility without push |
| Live Activities | +23.7% D30 | Lock screen during active events |
| Watch complications | Glanceable + one-tap | Counter + crisis support |

→ Full playbook + push triggers: `references/re-engagement.md`

---

## Recovery App: The Shame Test

> **You are building a habit-forming product for people recovering from harmful habits.**

Every retention mechanic must pass: *"Would a vulnerable user in crisis feel supported or judged?"*

### Hard Rules

- [ ] No leaderboards (recovery is not competition)
- [ ] No artificial scarcity ("Only 2 hours left!")
- [ ] No shame-based re-engagement ("You broke your streak 😢")
- [ ] No required social sharing (privacy is sacred)
- [ ] Crisis features never paywalled
- [ ] Declining engagement tracked as potential healthy graduation, not just churn

### Recovery Retention Phases

| Phase | Days | Focus |
|-------|------|-------|
| Crisis/Early | 1-7 | Survival: pledges, counter, crisis button, accountability |
| Habit Building | 8-30 | Routine: check-ins, triggers, community, streaks |
| Deepening | 31-90 | Identity shift: milestones, journal insights, coping skills |
| Sustaining | 91-365 | Maintenance: peer mentoring, reduced notifications, widget/watch |
| Graduation | 365+ | Light-touch: annual milestones, alumni community, pay-it-forward |

→ Full recovery playbook (community design, forgiveness architecture, wearable integration): `references/recovery-app-playbook.md`

---

## Churn Detection (Act on 2+ signals)

Session frequency declining · Session duration shortening · Fewer features used · First streak break after long streak (**very high risk**) · Notification response declining · Community engagement decreasing

→ Full measurement (cohort analysis, predictive churn, metric definitions): `references/measurement.md`
> ⚠️ D1 diagnostics (time to first value, onboarding completion) → onboarding-mastery. This skill owns D7+ metrics and churn.
