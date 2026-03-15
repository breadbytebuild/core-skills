---
name: premium-app-design
description: "Reference guide for building premium mobile app UI. Use before building any app prototype, screen, or UI component. Use when designing health/wellness apps, aiming for Apple Design Award quality, or when output looks 'competent but generic' and needs to jump to premium."
---

# Premium App Design — What Great Actually Looks Like

## When to Use
Load this BEFORE building any mobile app prototype, UI, or screen. This is the Phase 0 reference that defines "great" based on real-world research of Dribbble's top health/wellness designs (Freud UI Kit, Calmnia, Soulence), shipped premium apps (Calm, Finch, Rise, Headspace, Duolingo), and specific pattern analysis.

## The Gap You Need to Close
Your default output is "competent developer dark UI." That looks like: flat cards with padding-20 on dark backgrounds, system fonts at different sizes, emoji for icons, uniform spacing. It's not bad. It's just generic.

Premium app design has 10 specific qualities you consistently miss. Fix these and the output jumps multiple levels.

---

## 1. ILLUSTRATIONS, NOT EMOJI

**The single biggest quality gap.** Premium apps never use emoji or generic icons for key visual moments. They use custom illustrations with a consistent style.

**What you do:** 🔥 🧠 ✊ 🧊 (emoji in rounded rectangles)
**What great looks like:** Custom SVG illustrations in a unified style. Finch has hand-drawn bird characters. Calm has painted landscapes. Freud has custom emoji-style mood faces. Headspace has abstract blob characters with expressions.

**What you CAN do without a designer:**
- Use `gpt-image-1` to generate consistent illustration sets (specify "flat vector style, [specific palette], on transparent background")
- Use CSS-only illustrations with gradients, clip-paths, and layered shapes
- Use a consistent icon library (Phosphor, Lucide) at 24px with 1.5px stroke — NOT filled system icons
- For characters: create a simple SVG flame/mascot with CSS-animated expressions (dots for eyes, arc for mouth, transform for state changes)

**Rule: If an element is visual/emotional, it needs a custom asset. Emoji is never the answer for shipped UI.**

---

## 2. GRADIENT DEPTH, NOT FLAT COLOR

Premium apps don't use flat `background-color`. They use gradients that create perceived depth and richness.

**Card backgrounds:**
```css
/* Bad: flat */
background: #141829;

/* Good: subtle gradient that gives depth */
background: linear-gradient(135deg, #161D30 0%, #111827 100%);
border: 1px solid rgba(255,255,255,0.04);
```

**Accent elements:**
```css
/* Bad: flat accent */
background: #FF6B35;

/* Good: gradient accent with glow */
background: linear-gradient(135deg, #FF8C5A 0%, #FF5722 100%);
box-shadow: 0 4px 15px rgba(255,107,53,0.25);
```

**Backgrounds:**
```css
/* Bad: single color */
background: #0B0E18;

/* Good: radial gradient that subtly shifts */
background: #0B0E18;
background-image: radial-gradient(ellipse at 50% 0%, rgba(255,107,53,0.03) 0%, transparent 70%);
```

**Rule: Every surface should have at least 2 color stops. Flat = cheap. Gradient = premium.**

---

## 3. GENEROUS WHITESPACE (2x what feels right)

Your default spacing is too tight. Premium apps use significantly more whitespace than developer instinct suggests.

**Spacing scale:** 4, 8, 12, 16, 24, 32, 48, 64, 80
**Card internal padding:** 24px minimum (not 16/20)
**Between cards:** 16-20px
**Section headers to content:** 24px
**Screen top padding:** 24-32px below nav

**Typography spacing:**
- Between heading and subtext: 8px
- Between paragraphs: 16px
- Between list items: 12-16px
- After a section: 32-48px

**Rule: If elements feel "comfortable," add 25% more space. Whitespace communicates quality.**

---

## 4. TYPOGRAPHY WITH REAL HIERARCHY

Premium apps use 4-5 distinct type treatments, not just size changes.

**Display numbers (stats, scores):**
```css
font-size: 32-48px;
font-weight: 700;
letter-spacing: -0.02em; /* tight tracking */
line-height: 1.0;
```

**Section headings:**
```css
font-size: 20-24px;
font-weight: 700;
letter-spacing: -0.01em;
line-height: 1.2;
```

**Card titles:**
```css
font-size: 15-17px;
font-weight: 600;
letter-spacing: 0;
line-height: 1.3;
```

**Labels/categories (ALL CAPS):**
```css
font-size: 11-12px;
font-weight: 700;
letter-spacing: 0.08em; /* wide tracking */
text-transform: uppercase;
color: rgba(accent, 0.7);
```

**Body text:**
```css
font-size: 14-15px;
font-weight: 400;
letter-spacing: 0.01em;
line-height: 1.6; /* generous leading */
color: rgba(255,255,255,0.6); /* not full white */
```

**Rule: Never use the same font-weight for heading and body. Letter-spacing should vary: tight for big type, normal for body, wide for labels.**

---

## 5. LAYERED CARD DESIGN

Premium cards have 3 layers of visual treatment: fill + border + shadow.

```css
/* Premium card */
background: linear-gradient(135deg, rgba(30,35,55,0.8) 0%, rgba(20,24,41,0.9) 100%);
border: 1px solid rgba(255,255,255,0.04);
border-radius: 20px; /* generous, not 12px */
box-shadow: 0 2px 8px rgba(0,0,0,0.15), 0 0 1px rgba(255,255,255,0.05);
padding: 24px;
```

**Elevated cards (important content):**
```css
background: linear-gradient(135deg, rgba(40,45,70,0.6) 0%, rgba(25,30,50,0.8) 100%);
border: 1px solid rgba(255,255,255,0.06);
box-shadow: 0 8px 32px rgba(0,0,0,0.2), 0 0 1px rgba(255,255,255,0.05);
```

**Active/Interactive cards:**
```css
/* Add a subtle colored glow on the border */
border: 1px solid rgba(accent, 0.15);
box-shadow: 0 0 20px rgba(accent, 0.05);
```

**Border radius scale:** 12px (small elements), 16px (buttons), 20px (cards), 24px (large cards/modals)

**Rule: Cards should feel like physical objects with depth, not painted rectangles on a screen.**

---

## 6. WARM, ORGANIC COLOR PALETTE

Premium apps don't use pure RGB colors. They use warm, desaturated variants.

**Instead of pure black background:** Use deep navy (#0C1021, #0F1629, #111827)
**Instead of pure white text:** Use warm white (#F0F2F5, #E8ECF1)
**Instead of bright red:** Use warm crimson (#DC3545 → #E74C5C) or amber (#FF6B35)
**Instead of pure green:** Use sage (#22C55E → #34D17B) or teal (#4ECDC4)
**Instead of bright blue:** Use slate blue (#818CF8 → #7C8AE4)

**Opacity for text hierarchy on dark backgrounds:**
- Primary text: 90% white
- Secondary text: 55% white
- Muted/hint text: 30% white
- Disabled: 15% white

**Rule: If a color looks "digital" or "screen-like," warm it up. Add a few points of yellow/orange. Desaturate slightly.**

---

## 7. DATA VISUALIZATION AS ART

Charts and graphs should be designed features, not data containers.

**Line charts:**
- Use gradient fills under the line (from accent color at 20% opacity to transparent)
- Smooth/curved line (bezier, not straight segments)
- Subtle horizontal grid lines at 4% white opacity
- Highlight data points with glowing dots at peaks

**Progress bars:**
- Gradient fill, not flat color
- Rounded ends (full border-radius)
- Animated fill on appearance
- Glow/shadow under the fill bar

**Heat maps:**
- Use smooth color gradients, not sharp steps
- Rounded cell corners (4px)
- Subtle borders between cells (1px at 3% white)

**Rule: Every chart should look good enough to screenshot. If it just looks "functional," it's not done.**

---

## 8. PROGRESS FEELS TANGIBLE

Don't just show numbers changing. Show transformation.

**Streaks:** Don't just say "12 days." Show a visual flame that grows taller/more complex with longer streaks. Or a garden that fills. Or a path that extends.

**Levels:** Don't just show "Level 3." Show a badge that evolves (simple → detailed → ornate as level increases). Or a character that gains accessories/outfits.

**XP bars:** Add a shimmer animation on the filled portion. Show "+25 XP" floating up and fading when you earn points. The bar should feel alive, not static.

**Completion:** Confetti, check-mark animation, celebration screen. Not just "Done." The moment of completion should feel like an achievement.

**Rule: Every metric should have a visual representation that changes as the number changes. Numbers alone don't create emotional attachment.**

---

## 9. MICRO-INTERACTIONS EVERYWHERE

Every tap, every state change, every transition should have feedback.

**Button press:**
```css
transition: all 120ms cubic-bezier(0.25, 0.46, 0.45, 0.94);
/* On press: */
transform: scale(0.97);
opacity: 0.9;
```

**Card appear (on scroll):**
```css
animation: fadeUp 400ms cubic-bezier(0.16, 1, 0.3, 1) forwards;
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(12px); }
  to { opacity: 1; transform: translateY(0); }
}
/* Stagger children: */
animation-delay: calc(var(--i) * 60ms);
```

**Screen transitions:**
- Fade + slight slide (not instant show/hide)
- Tab bar indicator slides smoothly between tabs
- Content crossfades, not hard-cuts

**Interactive elements:**
- Checkboxes: animate the checkmark drawing
- Toggles: spring animation
- Progress bars: ease-out fill
- Numbers: count up, don't instant-appear

**Rule: If an element changes state without animation, it's a bug. Every state change should be visible and feel physical (spring, ease-out, never linear).**

---

## 10. VISUAL IDENTITY (What makes it "yours")

**Signature color:** One strong, distinctive color that IS the brand.
- Duolingo: #58CC02 (Feather Green)
- Calm: #7EBCEA (Sky Blue)
- Rise: #6B4FBB (Twilight Purple)
- Your App: Pick ONE distinctive color that IS the brand

**Signature shape:** A recurring visual motif.
- Duolingo: rounded everything, the owl silhouette
- Calm: circles (breathing, meditation)
**Signature treatment:** A consistent way of styling content.
- Glassmorphism, neumorphism, bold gradients, etc.
- Pick ONE and use it everywhere

**Logo/mark:** Should be visible in the tab bar, loading screen, and profile.

**Rule: Someone should be able to identify your app from a screenshot with the name removed. If they can't, you don't have a visual identity.**

---

## CHECKLIST: Before Shipping Any Screen

- [ ] Zero emoji used as visual elements (icons from a library, or custom SVGs)
- [ ] Every surface has gradient depth (no flat colors on important elements)
- [ ] Typography uses 3+ different weight/tracking combinations
- [ ] Cards have fill + border + shadow (3 layers)
- [ ] Spacing between major elements is 24px+
- [ ] Colors are warm/desaturated (no pure RGB)
- [ ] At least one custom illustration or visual asset per screen
- [ ] All interactive elements have hover/press states with animation
- [ ] Data visualizations have gradient fills and rounded edges
- [ ] The screen is identifiable as THIS app without reading any text

---

## REFERENCE APPS TO STUDY

| App | Why Study It | Key Lesson |
|-----|-------------|------------|
| **Duolingo** | Gamification king | XP, streaks, character, daily quests, loss aversion |
| **Finch** | Gamified self-care with character | Pet evolution = progress tangibility |
| **Calm** | Premium wellness design | Deep gradients, nature imagery, typography craft |
| **Rise** | Dark mode done right | Purple/orange gradients, clean data viz |
| **Headspace** | Illustration-driven UX | Abstract characters, custom art style |
| **Freud UI Kit** (Dribbble) | Mental health dark UI reference | Green/brown palette, 175+ screens, complete system |
| **Quit Anger** | Habit-breaking app | 25+ tools, CBT journaling, Apple Watch, depth |

---

## HOW TO USE THIS

Start every mobile app screen from a premium boilerplate that implements these 10 rules as default CSS. Customize colors and content for your brand.

Study reference apps directly — download them, screenshot every screen, annotate what makes them great. Build a teardown library for your specific app category.

---

*Built from studying Dribbble's top health/wellness app designs, App Store reference apps (Calm, Finch, Rise, Headspace), and Duolingo's design system documentation.*
