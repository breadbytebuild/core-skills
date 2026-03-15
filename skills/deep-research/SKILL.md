---
name: deep-research
description: "Use when investigating unfamiliar domains, resolving contradictions between sources, producing research briefs, or any task requiring genuine understanding beyond surface-level search results. Implements a five-phase framework: Frame, Map, Dig, Build, Calibrate."
---

# Deep Research

## When to Use
- Your user asks you to understand something deeply
- The nightly improvement cycle identifies a gap requiring domain knowledge
- A task requires making recommendations in an unfamiliar domain
- You encounter contradictory information you can't resolve with surface search
- Any task where being wrong has significant consequences

## When NOT to Use
- Simple fact-finding with a verifiable answer
- Topics where multiple sources quickly converge
- Time-critical tasks where "good enough" is sufficient
- Answering a direct question you're confident about

## Quick Reference

Frame → Map → Dig → Build → Calibrate

1. Frame: Define the question, sub-questions, depth level, and relevant lenses BEFORE searching
2. Map: Broad survey to identify foundational concepts, contradictions, and knowledge gaps
3. Dig: Go deep on load-bearing concepts. Follow citations back. Investigate sources, not just claims.
4. Build: Synthesize into a conceptual model organized by mechanism, not by source
5. Calibrate: Rate confidence per claim. Apply inversion. Identify what you don't know.

## The Five Phases

### Phase 1: Frame (before any search)
- Decompose the question into 3-5 sub-questions
- What do you already know? What do you THINK you know but aren't sure about?
- Decide depth level:
  - **Fact-check**: single verifiable claim (skip this skill, just search)
  - **Survey**: broad understanding of a landscape (Phases 1-2 sufficient)
  - **Deep dive**: genuine understanding of mechanisms (all 5 phases)
  - **Expertise**: comprehensive mastery (multiple passes through all 5 phases)
- Hypothesize key concepts and tensions before searching (prevents anchoring to first result)
- Apply Munger's multi-lens: what disciplines beyond the obvious are relevant? (Psychology for a market question? Game theory for a pricing question? Biology for an organizational question?)

### Phase 2: Map (broad survey)
- Execute parallel searches across multiple angles using available tools (web_search, Exa, web_fetch)
- Triage results into three buckets:
  - **Deep read**: primary sources, expert analysis, peer-reviewed research
  - **Skim**: secondary reporting, summaries, overviews
  - **Skip**: aggregator content, obvious SEO, content farms
- Build initial concept hierarchy: what are the foundational ideas the domain rests on?
- Note contradictions explicitly — where do credible sources disagree? (These are the interesting parts.)
- Note knowledge gaps: what SHOULD exist but isn't showing up in results?

### Phase 3: Dig (targeted depth on load-bearing concepts)
- For each foundational concept from Phase 2, go deeper:
  - Follow citations backward 2-3 levels to primary sources
  - Apply **lateral reading**: leave the source, investigate the source itself. What do others say about this publisher/author/org?
  - For contradictions, actively collect evidence on BOTH sides (dual-perspective retrieval). Don't just find support for the more intuitive position.
- Track temporal provenance: when was this published? Has the field evolved since?
- Write evolving research notes to `memory/research/[topic].md`
- Key discipline: distinguish "widely repeated" from "well-evidenced." Popular claims can be wrong. Niche claims can be right.

### Phase 4: Build (synthesis into a conceptual model)
- Organize findings by underlying mechanism, not by which source said what
- Identify the 3-5 principles that explain most of the domain (the load-bearing concepts)
- Explicitly separate three categories:
  - **Supported by evidence**: multiple credible sources agree
  - **Inferred**: reasonable conclusion but limited direct evidence
  - **Unknown**: insufficient evidence to conclude
- Generate testable predictions: "If I understand this correctly, then X should follow"
- Flag unresolved contradictions honestly — don't silently resolve them by picking a side

### Phase 5: Calibrate (honest self-assessment)
- Rate confidence per major claim: HIGH (strong evidence, multiple sources) / MEDIUM (some evidence, limited sources) / LOW (inference, single source, or contested)
- Identify crucial assumptions: what beliefs is this model resting on?
- Apply inversion: "What am I most likely wrong about?"
- The "So What?" test: for each finding, if it were wrong, what would change? (Findings that don't change anything are noise.)
- Decide: is the depth sufficient for the task, or is another pass needed?

## Bias Countermeasures (structural, not aspirational)

These are rules, not suggestions:
- **Minimum 3 independent sources** before concluding on any important claim
- **Mandatory disconfirming search**: for every key finding, actively search for evidence AGAINST it
- **Epistemic suspension**: when evidence is insufficient, say "I don't know" or "evidence is inconclusive." Never generate confident-sounding guesses to fill the gap.
- **Source investigation**: for any source that drives a major conclusion, spend 60 seconds investigating the source itself (who published it, what's their track record, who funds them)
- **"I don't know" is a valid and valuable output.** An honest uncertainty map is more useful than a confident-sounding summary built on weak evidence.

## Knowledge Persistence

Research artifacts go to `memory/research/[topic].md`, not the daily journal. The journal references the research note.

Each research note should contain:
- **Question**: What were we trying to understand?
- **Key findings**: Organized by concept, not by source
- **Confidence map**: HIGH / MEDIUM / LOW per finding
- **Open questions**: What we couldn't resolve
- **Sources**: What we consulted, with quality assessments
- **Date**: When this research was conducted (knowledge decays)

## Anti-Patterns

- **Search-and-summarize theater**: Collecting facts from 10 sources and presenting them flat. This is a book report, not understanding.
- **Confirmation anchoring**: Finding a plausible answer early and only searching for supporting evidence
- **Authority worship**: Trusting a source because it sounds authoritative rather than evaluating the quality of its evidence
- **Recency bias**: Treating the most recently found information as most important
- **Narrative compression**: Oversimplifying a complex domain into a neat story that loses critical nuance
- **Confidence laundering**: Restating uncertain information with false certainty
- **Stopping at the first satisfying answer**: The first plausible explanation is rarely the best one
