---
name: app-prototyping
description: "Build phone-ready interactive prototypes in HTML/Tailwind, deploy to Vercel for mobile testing, iterate in 60-second cycles. Use when someone says 'show me what X looks like,' when exploring a new app concept visually, when designing screens/flows before committing to React Native, or when building clickable demos for stakeholders. NOT for: production React Native code (-> react-native-foundations), visual design system decisions (-> s-tier-design), onboarding flow strategy (-> onboarding-mastery), retention mechanics (-> retention-engineering)."
---

# App Prototyping — Premium Mobile Mockups

## The Rule

The boilerplate IS the design system. Every prototype starts from it. You customize content, colors, and screens, but you NEVER rebuild the CSS foundation. The boilerplate already has gradient cards, proper typography, glow shadows, SVG icons, staggered animations, and ambient lighting. Use it.

**Customization points** (edit these, leave everything else):
- `accent` color family in `tailwind.config` (default: purple `#6C5CE7`)
- `--accent-from` / `--accent-to` CSS vars for button/progress gradients
- `ambient-glow` gradient color to match your accent
- Screen content (add/remove screens)
- Tab bar icons and labels

## Stack

Single `index.html` + Tailwind CDN -> `npx vercel --prod`. Zero build step.

## Workflow

```
1. cp -r skills/mobile-app-dev/skills/app-prototyping/boilerplate ~/workspace/prototype-[name]
2. Edit tailwind.config colors to match the app's brand
3. Edit screen content using components from references/component-library.md
4. npx vercel --prod -> share URL -> stakeholder opens on phone
5. Edit -> deploy -> refresh. 60-second iteration cycles.
```

### Screen priority (build in this order):
1. Home/main screen (80% of the vibe)
2. Primary daily action screen
3. Onboarding first screen
4. Everything else

### What the boilerplate gives you (DO NOT REBUILD):
- **Gradient card system:** `.card`, `.card-elevated`, `.card-accent` with 3-layer depth (fill + border + shadow)
- **Premium buttons:** `.btn-primary` (gradient + glow), `.btn-secondary` (glass)
- **Typography scale:** Inter font, extrabold display numbers with gradient text, label system
- **Color tokens:** Full semantic palette (`text-dim`, `text-faint`, `surface-border`, `accent-glow`)
- **Animations:** `.animate-in` (fade-up), `.animate-float`, `.animate-pulse-glow`, `.stagger` (cascading entrance)
- **Ambient lighting:** `.ambient-glow` radial gradient overlay
- **Progress components:** `.progress-track` + `.progress-fill` (gradient animated bar)
- **SVG icon set:** 20+ Feather-style icons in component-library.md (NEVER use emoji)
- **Safe areas:** iPhone 15 Pro viewport with Dynamic Island + home indicator
- **Tab bar:** Blur-glass with smooth active state transitions

## IRON RULES

1. **NEVER use emoji as visual elements.** The component library has SVG icons and SVG mood faces. Copy-paste them. Emoji = amateur.
2. **NEVER use flat `background-color` on cards.** Use the `.card` class which has gradient fill. If you need a custom color, use `style="background:linear-gradient(135deg, rgba(r,g,b,0.08), rgba(r,g,b,0.02))"`.
3. **NEVER write `bg-gray-800` or `bg-[#1C1C1E]` for cards.** The card classes exist. Use them.
4. **ALWAYS use `stagger` class on content containers** for cascading entrance animations.
5. **ALWAYS use gradient text** for hero/display numbers: `background:linear-gradient(180deg, LIGHT 0%, DARK 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;`
6. **Labels are uppercase.** Use the `.label` class for category markers, small metadata, and section identifiers.

## Taste Gates (MANDATORY before showing)

Run these BEFORE sharing the URL. All must pass.

- [ ] *3-second test:* Show someone for 3 seconds. Can they tell what the app does, what to do next, and that it's high quality?
- [ ] *Screenshot test:* Would someone screenshot this and send it to a friend?
- [ ] *Squint test:* Squint until you can't read text. Is the visual hierarchy still visible?
- [ ] *Thumb zone test:* Primary actions in the bottom 40% of screen?

## Pre-Show Quality Gate (ALL must be checked)

- [ ] Looks like a real phone app (not a website)
- [ ] Zero emoji used as visual elements (SVG icons only)
- [ ] All cards use `.card` class (gradient fill, not flat color)
- [ ] Text hierarchy uses 3+ different weight/size combos
- [ ] Touch targets 44px+ height
- [ ] Hero numbers use gradient text treatment
- [ ] Stagger animations on content entrance
- [ ] One accent color, used consistently (buttons, active tab, links)
- [ ] Real copy, no placeholders
- [ ] Safe areas respected (47px top, 34px bottom)

## Non-Obvious Design Decisions

Things that separate "website on phone" from "real app":

- *Tab bar, not navbar.* Phone apps navigate with bottom tabs. Websites use top navbars. #1 tell.
- *Cards, not sections.* Content lives in elevated gradient cards with rounded corners.
- *Full-width gradient buttons.* Primary CTAs use `.btn-primary`. Not text links.
- *Scale-0.97 press feedback.* `.tap` class on every tappable element.
- *Status bar always present.* Time, signal, battery.
- *Sheets from bottom.* Modals come from the bottom with drag handle.
- *Ambient glow.* Subtle radial gradient at top of screen. Communicates premium.
- *SVG faces for moods.* Custom circle-faces with stroke expressions, not emoji.

## References (load when building)

- `references/component-library.md` — Copy-paste HTML for all premium components
- `references/screen-templates.md` — 16 screen type blueprints

## Visual References (MANDATORY for each screen)

Before building any screen, load its visual teardown from `assets/design-references/teardowns/`. The teardown tells you which 2-3 screenshots to study and what specific patterns to match.

**Workflow per screen:**
1. Read the teardown file for that screen type
2. Load the referenced screenshots (the teardown names exact files)
3. Study the spacing, typography, layout, and color patterns called out
4. Build the screen matching that quality bar
5. Compare your output visually against the references

**Available teardowns:**

| Screen Type | Teardown File | Primary Reference App |
|-------------|---------------|----------------------|
| Home | `teardowns/home.md` | Finch |
| Check-in | `teardowns/checkin.md` | Finch + Calm |
| Lesson Path | `teardowns/lessons.md` | Duolingo |
| Progress/Streaks | `teardowns/progress.md` | Duolingo + Finch |
| Celebration | `teardowns/celebration.md` | Duolingo + Finch |
| SOS/Crisis | `teardowns/sos.md` | Headspace + Calm |
| Insights | `teardowns/insights.md` | Calm + Noom |

**For apps with mascots/characters:** Create a character system doc with emotional states, environments, color values, and scene art reference.

Full index: `assets/design-references/INDEX.md`

## Common Mistakes

1. *Using emoji.* Read the iron rules above. SVG icons from component-library.md.
2. *Rebuilding the card system.* `<div class="card">` already looks premium. Don't override it.
3. *Flat backgrounds.* Everything has gradient depth. Even subtle gradients matter.
4. *Tiny text.* Body text 14px minimum, 15-16px preferred.
5. *Too many colors.* One accent, one success, one danger. That's it.
6. *Skipping animations.* The stagger system is free. Use it. Static screens feel dead.
7. *Forgetting safe areas.* Content behind the notch or under the home indicator = amateur.
