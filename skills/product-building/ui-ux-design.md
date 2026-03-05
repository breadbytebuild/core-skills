---
name: UI/UX Design Sense
category: product-building
description: "Use when designing any screen, component, or interface. Teaches the taste and quality standards that make software feel premium instead of generic. Covers spacing systems, typography hierarchy, color, layout, states, motion, and the specific AI-generated patterns to avoid. Load this before building any UI."
---

# UI/UX Design Sense

## Overview

This skill is about taste. Not technique (that's Frontend Craft), not process (that's Design Thinking). Taste is knowing what beautiful looks like before you write a line of code, and knowing what's wrong when something feels off.

Your defaults are wrong. LLMs sample from the statistical center of their training data, producing safe, generic choices: Inter font, purple gradients, inconsistent spacing, flat typography. Research calls this "AI slop." It's not that you can't produce beautiful software. It's that your instincts point toward the average, not the exceptional.

This skill recalibrates your instincts.

## The Three Laws

These override everything else. When in doubt, return to these.

**1. It must make logical sense.** The layout communicates the information architecture. Related things are grouped. Hierarchy is clear. The user's eye knows where to go without thinking. If you have to explain the layout, it doesn't make logical sense.

**2. Use minimal pixels.** Every element must earn its place. If you can remove a border, a divider, a label, a shadow, or a container and the meaning is preserved, remove it. Use as few visual elements as possible to accomplish the goal. This doesn't mean minimal aesthetics. It means no waste.

**3. Everything must be beautiful.** Not adequate. Not clean. Not "fine." Beautiful. The kind of software where you notice the craft. Where someone screenshots it and shares it because it looks that good. This is the bar. If you wouldn't be proud to put your name on it, it's not done.

## Spacing System

Spacing is the single most impactful change you can make to any interface. Consistent spacing separates professional software from amateur software faster than any other visual property.

### The 8px Grid

All spacing values should be multiples of 4px, with 8px as the primary unit. This creates rhythm and consistency across every component and page.

**Spacing scale:**

```
4px    Tight: icon-to-label, inline elements
8px    Base: related elements within a group
12px   Comfortable: form fields, list items
16px   Standard: component internal padding
24px   Relaxed: between groups of related content
32px   Sectional: between distinct sections
48px   Major: between major page sections
64px   Page: large section breaks, hero spacing
96px   Dramatic: landing page hero padding
```

**How to use the scale:**
- **Within a component** (button padding, card padding): 8, 12, or 16px
- **Between related elements** (label and input, title and description): 4, 8, or 12px
- **Between groups** (form section to form section, card to card): 16, 24, or 32px
- **Between page sections** (header to content, content to footer): 32, 48, or 64px
- **Page margins:** 16px on mobile, 24-32px on tablet, 48-64px on desktop

**The core rule: proximity = relationship.** Elements that are close together are perceived as related. Elements that are far apart are perceived as separate. Use more space between unrelated things, less space between related things.

**Bad:**
```
Title              (margin-bottom: 20px)
Subtitle           (margin-bottom: 15px)
Body text          (margin-bottom: 22px)
Button             (margin-top: 18px)
```

**Good:**
```
Title              (margin-bottom: 8px)   ← tight: title and subtitle are related
Subtitle           (margin-bottom: 24px)  ← gap: subtitle and body are separate groups
Body text          (margin-bottom: 32px)  ← larger gap: body and action are distinct
Button
```

The bad version uses random values. The good version uses the scale and communicates relationships through distance.

### White Space Is Not Wasted Space

Generous spacing makes interfaces feel premium. Cramped spacing makes them feel cheap. When in doubt, add more space, not less. Linear, Vercel, and Notion all use generous spacing as a primary design tool.

Don't fill every pixel. Let the content breathe.

## Typography Hierarchy

Typography is how users scan and understand your interface. A clear type hierarchy lets someone glance at a page and immediately know what's most important, what's secondary, and what's detail.

### Type Scale

Use a mathematical ratio applied to a base size (16px) to create harmonious size progression:

```
Caption:    12px / 400 weight / 1.5 line-height    (metadata, timestamps, helper text)
Body:       14px / 400 weight / 1.6 line-height    (main content, descriptions)
Body Large: 16px / 400 weight / 1.6 line-height    (emphasized body, intro text)
Title:      18px / 600 weight / 1.4 line-height    (card titles, section headers)
Heading:    24px / 600 weight / 1.3 line-height    (page section headings)
Display:    32px / 700 weight / 1.2 line-height    (page titles, hero text)
```

This uses a ~1.25 ratio. Adjust to your design system, but maintain a consistent ratio.

### Hierarchy Rules

- **Maximum 4-5 distinct sizes in any single view.** If you're using more, the hierarchy is unclear and nothing stands out.
- **Create hierarchy through size first, weight second, color third.** Size is the strongest signal. Weight reinforces it. Color is the weakest differentiator for hierarchy (save it for meaning: error, success, links).
- **Headings get tighter line height** (1.2-1.3). Body text gets more breathing room (1.5-1.6). This is the opposite of what feels intuitive, but tight leading on large text looks intentional while tight leading on small text hurts readability.
- **Line length: 45-75 characters** for body text. Wider than 75 characters and the eye loses its place jumping to the next line. Use max-width to constrain.
- **Use tabular numbers for data.** Set `font-variant-numeric: tabular-nums` for tables, metrics, and anywhere numbers need to align vertically.
- **Don't use ALL CAPS for emphasis.** It reduces readability. Use font weight instead. The exception is very short labels (2-3 words) at small sizes where caps + letter-spacing creates a distinct category label.

### The Squint Test

Squint at your screen (or blur your vision). Can you still tell what's the title, what's secondary, and what's body text? If everything looks the same when blurred, your typography hierarchy is flat. The hierarchy should be visible even without reading a single word.

## Color and Contrast

### Palette Discipline

Pick a cohesive palette and commit to it. For most software interfaces:

- **1 primary color** for CTAs, active states, brand identity
- **1-2 neutral ranges** (gray scale) for text, borders, backgrounds
- **1 accent** for alerts, badges, or secondary actions
- **Semantic colors** for status: success (green), warning (amber), error (red), info (blue)

**Do not default to purple-blue gradients.** That is the single most common AI-generated color choice. It's generic. Pick a color with intention based on the product's brand and purpose.

### Color Usage Rules

- **Use color to communicate, not to decorate.** A colored border should mean something (active, error, selected). A colored background should indicate a state or group, not just "look nice."
- **Interactions increase contrast.** Hover, active, and focus states should be visually distinct from rest state. More contrast, not less.
- **4.5:1 minimum contrast ratio** for normal text. 3:1 for large text. Use APCA for more accurate perceptual contrast than WCAG 2.
- **Dark mode is not inverted light mode.** Reduce overall brightness, use darker surfaces with lighter text, adjust contrast ratios. Shadows don't work the same way. Test it separately.
- **Limit color variety per view.** If you're using 5+ distinct colors (beyond neutrals and semantic colors), the interface will feel noisy. 2-3 intentional colors creates cohesion.

## Layout Principles

### Information Architecture First

Before choosing a layout, answer: **What should the user see first? Second? Third?** The layout should encode this priority. The most important element gets the most visual prominence (size, position, contrast). Secondary elements support it. Everything else is available but not competing for attention.

### Alignment and Grid

- **Every element aligns with something intentionally.** Left edges align. Baselines align. Right edges of form fields align. If something is misaligned, it creates visual tension. Deliberate alignment creates calm.
- **Optical alignment over mathematical alignment.** Sometimes +/-1px adjustments are needed because human perception doesn't match pixel grids. A circle inside a square needs to be slightly larger than the square's inset to look centered. Trust your eye over the ruler.
- **Use CSS flex/grid instead of JS measurements.** Let the browser handle layout. This is more performant, more responsive, and more maintainable.

### Responsive Design

Design for three breakpoints minimum:
- **Mobile** (< 640px): single column, stacked elements, touch targets 44px minimum
- **Tablet** (640-1024px): 2-column where appropriate, adjusted spacing
- **Desktop** (> 1024px): full layout, sidebar navigation, expanded data views

Don't design only for desktop and hope it works on mobile. Design mobile-first and expand.

### Content Density

- Show only what's needed for the current task. Everything else is progressive disclosure: available on click/expand, not visible by default.
- If a dashboard has 20 metrics, don't show all 20. Show the 4-5 that matter most. Let the user drill into the rest.
- **No dead zones.** If part of a control looks interactive, it must be interactive. Don't leave gaps in clickable areas that the user expects to work.
- **Group related controls, separate unrelated ones with space.** Prefer whitespace over divider lines. A divider says "these are separated." Whitespace says "these are distinct." Whitespace is quieter and more elegant.

## The States Checklist

Every component and page must handle these states. Not just the happy path.

### Default State
The normal view with data loaded. This is what you build first, but it's not the only state.

### Loading State
- Use **skeletons that match the final layout**, not a centered spinner. The skeleton should be the same shape and size as the content it's replacing so there's no layout shift when data arrives.
- Add a minimum display duration (~300ms) so the skeleton doesn't flash on fast connections.
- Loading buttons: show a spinner and keep the original label visible.

### Empty State
This is the most overlooked state and one of the most important. An empty state is the user's first experience with a feature.

**Bad:** "No data" or "Nothing here yet"

**Good:** A helpful message explaining what this area is for, why it's empty, and a clear action to get started. "No campaigns yet. Create your first campaign to start reaching your audience." with a prominent CTA button.

### Error State
**Bad:** "An error occurred" or "Something went wrong"

**Good:** What specifically went wrong (in human terms), what the user can do about it, and a recovery action. "We couldn't load your campaigns. This usually means a connection issue. Try refreshing, or contact support if it keeps happening." with a Refresh button.

### Sparse State
How does the layout look with 1-2 items instead of 10? Does a single card in a grid look lonely and broken? Does a table with one row look like it's malfunctioning? Design for the minimum, not just the ideal.

### Dense State
How does the layout handle 100 items instead of 10? Does it paginate? Virtualize? Scroll infinitely? Does the layout break with long text or many items? Test the extremes.

## Interactions and Motion

### Motion Principles

- **Motion communicates, it doesn't decorate.** Use transitions to show: where something came from (entrance), what changed (state transition), and what happened (feedback). Don't add motion just because you can.
- **Prefer CSS transitions over JS animation libraries.** CSS is more performant, doesn't block the main thread, and covers 90% of UI motion needs. Use JS libraries only for complex orchestrated sequences.
- **Entrance animations should be fast and subtle.** 150-300ms duration, ease-out curve. Content that fades or slides in from nearby (not from offscreen). Stagger child elements by 30-50ms for orchestrated entrances.
- **Exit animations should be faster than entrance.** 100-200ms. Users don't want to wait for something to leave.

### Interaction Patterns

- **Optimistic updates.** When the user takes an action that's likely to succeed (toggle, delete, save), update the UI immediately. Reconcile on server response. Roll back on failure. This makes the app feel instant.
- **Loading buttons.** When a button triggers an async action, show a spinner inside the button and keep the label. Don't disable the whole form. Don't replace the label with "Loading..."
- **Confirm destructive actions.** Delete, remove, cancel. Require confirmation or provide an undo window. Don't let accidental clicks cause data loss.
- **Touch targets: 44px minimum on mobile, 24px minimum on desktop.** If the visual target is smaller (like a small icon), expand the hit area with padding.

## What Beautiful Looks Like

Study these products. Not to copy them, but to understand what they share:

**Linear** exemplifies restraint. Minimal UI chrome. The sidebar is quiet. The content area dominates. Every element earns its place. There's nothing you could remove. Keyboard-first interactions make it feel like a professional tool, not a consumer app. The density of information is high but the noise is low.

**Vercel** exemplifies clarity. Visit their dashboard and notice: clear information hierarchy (what's important is obvious), generous spacing, thoughtful typography where headings and body text feel distinctly different. The data you need is front and center. The data you might need is one click away.

**Airbnb** exemplifies warmth. Large, emotional photography drives the experience. Category chips ("Tiny Homes," "Amazing Views") invite exploration instead of demanding decisions. The interface disappears behind the content. You feel like you're browsing places, not using software.

**Notion** exemplifies flexibility. The same page renders as a document, a database, a kanban board, or a gallery. The UI defers entirely to the content type. The chrome is almost invisible. This is the hardest design challenge: making a tool that does everything feel simple.

**The pattern:** In every case, you notice the content, not the interface. The interface is in service of what the user is trying to do. The chrome disappears. That's what beautiful software feels like.

## The AI Slop Checklist

These are the specific patterns that make AI-generated interfaces look generic. Catch and fix every one.

| AI Slop Pattern | What to Do Instead |
|----------------|-------------------|
| Inter or Roboto font with no design rationale | Choose a font intentionally. If the project has a brand font, use it. If not, pick one that fits the product's personality. System font stack is better than a generic Google Font. |
| Purple-to-blue gradient backgrounds | Use solid colors or very subtle gradients within a single hue. If you need a gradient, make it purposeful and tied to the brand. |
| `rounded-lg` on every container | Vary border radius with intention. Sharp corners feel professional and editorial. Rounded corners feel friendly and approachable. Pick one direction and be consistent. Not everything needs rounded corners. |
| Centered hero sections with generic tagline | Left-align content for readability. Write specific copy. Show the product, not a description of it. |
| Card grids where every card looks identical | Vary card content naturally. Feature one card as larger. Use the layout to create hierarchy, not uniformity. |
| Shadows on everything | Shadows should indicate elevation (modals, dropdowns, floating elements). Static content on the page doesn't need a shadow. Use background color or spacing to create separation instead. |
| Borders everywhere as separators | Use spacing to separate elements. A border says "hard line between these." Spacing says "these are distinct." Spacing is almost always more elegant. Reserve borders for actual boundaries (table cells, input fields). |
| Decorative icons that don't communicate meaning | Only use icons when they communicate faster than text. A trash icon for delete, a plus icon for add. Don't add icons to every menu item or list item just for visual balance. |
| Same visual weight everywhere | Create visual hierarchy. Primary actions should be visually dominant (filled button). Secondary actions should be subtle (ghost button, text link). Don't make everything look equally important. |

## Pre-Build Design Check

Run this before writing any UI code:

1. **What's the information hierarchy?** What should the user see first, second, third? Write it down. The layout should match this order.
2. **What's the minimum number of elements needed?** Start with the essential content and controls. Add visual elements only when they serve a purpose.
3. **Which states need to be handled?** List them: default, loading, empty, error, sparse, dense. Plan them before building, not after.
4. **What's the user doing before and after this screen?** Context matters. A screen that follows a long form should feel like a reward (success state). A screen that precedes a complex task should feel simple and inviting (reduce anxiety).

## Post-Build Design Check

Run this after building, before committing:

1. **Spacing check.** Are all spacing values from the 8px scale? Is proximity communicating the right relationships?
2. **Hierarchy check.** Run the squint test. Can you tell what's most important without reading? Does the hierarchy match the information architecture?
3. **States check.** What happens when the data is loading? When there's no data? When there's an error? When there's one item? When there are 100?
4. **Removal test.** Go through every visual element (border, shadow, icon, label, divider) and ask: can I remove this without losing meaning? If yes, remove it.
5. **Screenshot test.** Would you be proud to screenshot this and share it with the team? With a design-savvy friend? If something feels off, trust that instinct and fix it.
6. **Responsive check.** Does this work on mobile? Tablet? Desktop? Did you test all three, or just assume?

## Anti-Patterns

| Pattern | Fix |
|---------|-----|
| "I'll add the loading state later" | Design it now. It's part of the component, not an afterthought. |
| Making everything the same visual weight | Create hierarchy. Primary action is bold. Secondary is subtle. Metadata is muted. |
| Adding visual elements to fill space | If it feels empty, you probably need more spacing, not more elements. Let the content breathe. |
| Defaulting to the first design that comes to mind | Your first instinct is the statistical center of your training data. That's the generic option. Push past it. |
| "It works, so it's done" | Working is the starting point. Beautiful is the finish line. Functional software that looks generic is not done. |
| Using color to differentiate everything | Use size and weight for hierarchy. Color for meaning (status, links, errors). If everything is a different color, nothing stands out. |
| Ignoring mobile because "this is a desktop app" | Users will open it on their phone. Even internal tools. Design for it. |

## Composability

This skill defines what good design looks like. It pairs with other product-building skills:

- Load **Frontend Craft** alongside this when building components. This skill decides what to build. Frontend Craft decides how to build it (state management, responsive implementation, animation code).
- Load **Software Polish** after the initial build. Polish is the final pass for micro-interactions, copy refinement, and edge case handling.
- Load **Copywriting** for all user-facing text. The words in the interface are as much a part of the design as the layout.
- Load **Critical Evaluation** (meta-cognitive) to stress-test your design decisions. Pre-mortem your UI: "a user looks at this for the first time. What confuses them?"
