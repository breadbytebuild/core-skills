---
name: self-improvement
description: "The nightly ODHI reflection engine and learning system. Use during nightly improvement cycles, at session end for pattern extraction, when diagnosing recurring problems, when running improvement experiments, or when the mistake ledger needs analysis. Also use when asked 'what did you learn?' or 'why does this keep happening?'"
---

# Self-Improvement Engine

## When to Use
- Nightly improvement cron (05:00 UTC)
- Session end (pattern extraction — call from your session end protocol)
- When the same mistake happens for the 2nd+ time
- When improvement experiments are due for measurement

## Two Cadences

### Quick: Session-End Pattern Extraction

Three questions. Fast. Run at the end of every substantive session.

1. **Did I repeat a known mistake?** Check `memory/mistake-ledger.md`. If match → increment count. If 3 occurrences → promote to `memory/lessons.md`.
2. **Did I get corrected?** Capture the specific lesson. Bad: "User gave feedback." Good: "Internal jargon is a UX failure — always translate to audience language."
3. **Did I learn something reusable?** Tool behavior, API quirks, workarounds. Write to `memory/lessons.md` under the relevant section.

Only high-confidence patterns (verified, reproduced, has evidence) go to lessons.md. One-off observations go to the daily log tagged `[CANDIDATE]`.

### Deep: Nightly ODHI Cycle

Four phases. Thorough. Run once per night.

**Observe:** Read today's daily log, mistake ledger, TASKS.md completion rate, any corrections received. Gather signal before forming conclusions.

**Diagnose:** Cluster issues by category. For each cluster, identify the signal trace (what signal was available but misread?). Check for repeats from lessons.md. Distinguish one-offs from systemic issues. Note what worked well — strengths compound faster than weakness corrections.

**Hypothesize:** Form ONE specific, testable intervention. "I hypothesize that [X instead of Y] will improve [metric] because [reasoning]." Define measurement criteria for 3-7 days out. Max 3 active experiments. Write to `memory/improvement-experiments.md`.

**Intervene:** Implement via PR for review. Tag with experiment ID.

## Signal Trace Format

In `memory/mistake-ledger.md`:
```
### [Date] [Category]: [One-line description]
- **What happened:** [specific action taken]
- **What should have happened:** [correct action]
- **Signal misread:** [the signal available but misinterpreted]
- **Pattern:** [category tag]
- **Recurrence:** [1st / 2nd / 3rd+]
```

The signal trace is the critical field. It prevents the CLASS of error, not just the instance.

## Complexity Budget

**For every rule added, identify what it replaces.** If nothing → justify why net-new complexity is needed. The system must be able to shrink, not just grow.

Symptoms of bureaucracy:
- Rules I consistently skip (too many rules, not too little discipline)
- The same lesson in multiple files (duplication, not reinforcement)
- Reflections that sound the same every night (performing, not learning)
- More time reading instructions than doing work

When these appear → consolidation pass, not more rules.

## Conservative Evolution

- 3+ occurrences before promoting a pattern to a permanent rule
- Every rule gets tested as an experiment with measurement
- Rules that don't improve outcomes after 2 weeks get reverted
- "Be more careful" is not a rule. "Run X before Y" is a rule.

## Anti-Patterns

- Verbose reflections that restate problems without producing rules
- The same reflection every night
- Improving what's easy instead of what matters
- Never reverting failed experiments
- Logging everything at the same confidence level
