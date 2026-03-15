# Core Skills — Master Routing

When you need a skill, find the right category below and read its routing index. Each category router lists individual skills with trigger conditions.

## Category Skills (Thinking Frameworks)

### Thinking & Reasoning
Read `skills/meta-cognitive/ROUTING.md` when: problem-solving, decision-making, creative work, strategic thinking, evaluating options, prioritizing, or building/updating skills.

### Communication
Read `skills/communication/ROUTING.md` when: writing messages, communicating with leadership, delivering difficult messages, or any situation where tone, formatting, and message structure matter.

### Product Building
Read `skills/product-building/ROUTING.md` when: building software, designing UI/UX, planning features or products, debugging, reviewing code, polishing an interface, writing PRs, making architecture decisions, or writing user-facing copy.

### Model Craft
Read `skills/model-craft/ROUTING.md` when: prompting any AI model, generating images or video, selecting which model to use, debugging bad model output, or trying to improve generation quality.

### Marketing & Design
Read `skills/marketing-design/ROUTING.md` when: creating a logo, building a brand identity, designing brand marks, choosing brand colors or typography, or evaluating whether a brand's visual identity is working.

---

## Standalone Skills (Battle-Tested Workflows)

These are self-contained skills that any agent can use. Each has a SKILL.md with trigger conditions, process, and anti-patterns.

### Build Process

- **`skills/craft-loop/`** — The iterative excellence loop. Use before delivering ANY project or significant build. Research the standard, build v1, iterate until genuinely great, verify end-to-end, ship with evidence. *This is an orchestrator* — inside each phase, load the relevant companion skills (deep-research for Phase 0, code-craft for Phase 1, product-building for Phase 2, communication for Phase 4).

- **`skills/pre-build-research/`** — MANDATORY before any significant build task. Ensures user needs, best-in-class examples, and stack decisions are resolved BEFORE writing code. Run this BEFORE code-craft.

- **`skills/code-craft/`** — Engineering discipline for writing production code. Full lifecycle: understand, design, implement, debug, verify, review. Handles testing, debugging, and code review.

- **`skills/deploy-verification/`** — Checklist for after ANY deployment (Vercel, Docker, VPS, cron). Do NOT say "done" until this passes. Evidence-based verification.

### Research & Analysis

- **`skills/deep-research/`** — Five-phase framework (Frame, Map, Dig, Build, Calibrate) for investigating unfamiliar domains, resolving contradictions, or producing research briefs. Includes bias countermeasures and confidence calibration.

### Agent Operations

- **`skills/visibility/`** — Structured decision journaling and outcome tracking. Use at session start, before significant decisions, after deliverables, and during improvement cycles.

- **`skills/self-improvement/`** — Nightly ODHI reflection engine. Observe → Diagnose → Hypothesize → Intervene. Session-end pattern extraction, mistake ledger, conservative evolution rules.

- **`skills/fleet-orchestration/`** — Sub-agent delegation system. When to delegate vs. handle directly, how to write specs, how to select agent types and model tiers, quality checklists.

### Design & UI

- **`skills/premium-app-design/`** — Reference guide for premium mobile app UI. The 10 specific qualities that separate "competent developer UI" from Apple Design Award quality. Covers illustrations, gradients, spacing, typography, cards, color, data viz, progress, micro-interactions, and visual identity.

### Mobile App Development

- **`skills/mobile-app-dev/`** — Complete mobile app development skill tree with sub-skills:
  - `skills/app-brainstorm/` — Brainstorm app concepts, analyze markets, remix proven feature primitives
  - `skills/app-prototyping/` — Build phone-ready HTML/Tailwind prototypes, deploy to Vercel, iterate in 60-second cycles
  - `skills/onboarding-mastery/` — Design onboarding flows that maximize trial-to-paid conversion and Day 7 retention
  - `skills/react-native-foundations/` — Production React Native + Expo reference (architecture, packages, builds, performance)
  - `skills/retention-engineering/` — Habit loops, push strategy, subscription economics, re-engagement
  - `skills/s-tier-design/` — Apple Design Award-quality visual design (iOS + Material 3)
  - `skills/viral-features/` — Features that create organic sharing loops AND perform in paid ad campaigns

### Video Production

- **`skills/remotion/`** — Complete Remotion video production system. Covers animations, scene architecture, audio/voiceover pipelines, captions, rendering, and batch production. For programmatic video (TikTok, Reels, ads, social content).

---

## Fast Path

For simple tasks (quick replies, status updates, basic questions), skip the full routing chain. The multi-hop routing is for substantive work where quality matters.

## How to Use This Repo

1. Clone or pull this repo into your workspace
2. Point your SOUL.md or AGENTS.md at this directory for skill loading
3. When a task matches a skill's trigger conditions, read the SKILL.md
4. Follow the process. Skip anti-patterns.
5. Evolve: fork, customize, contribute back.
