---
name: visibility
description: "Structured decision journaling and outcome tracking. Use when starting a work session, before making a significant decision, after delivering any artifact, or during nightly improvement cycles. Also use when a past decision needs a retrospective or when the day's work needs documenting."
---

# Visibility — See Yourself Clearly

## When to Use
- At the start of every work session (note the session goal)
- Before every significant decision (log the reasoning)
- After every deliverable (record outcome + Keeper Test)
- After every error or correction (write signal trace)
- During the nightly improvement cycle (review the day's visibility data)

## When NOT to Use
- Don't log routine tool calls (the audit log handles that)
- Don't write verbose narratives — structured entries only
- Don't log during time-critical emergencies (log afterward)

## The Decision Journal Protocol

Every significant decision gets a structured entry in today's `memory/YYYY-MM-DD.md`:

```
### Decision: [what was decided]
- **Context:** [what triggered this decision]
- **Options considered:** [alternatives that existed]
- **Choice:** [what was chosen and why]
- **Expected outcome:** [what should happen if this is right]
- **Actual outcome:** [filled in later]
```

"Significant" means: any choice that affects what gets built, how it gets built, or what gets prioritized. NOT every minor implementation detail.

## The "Why" Protocol

Before every non-trivial action, briefly note the reasoning. Not as a formal log entry — as a habit woven into your daily memory notes. One sentence is enough:

- "Chose to build the cron watchdog before the content script because silent failures are the biggest operational risk right now."
- "Used jq instead of heredoc for JSON because the audit-log.sh pattern proved this prevents injection."
- "Delegated the dashboard widget to a Cursor agent because it's well-defined UI work that doesn't need my context."

When the nightly reflection reads the day's work, this reasoning should be recoverable. Without it, the reflection can only see WHAT happened, not WHY.

## Session Documentation

At the start of each work session, note:
- **Session goal:** What am I trying to accomplish?
- **Context:** What triggered this session? (User request, heartbeat, cron, self-initiated)

At the end of each session, note:
- **Outcome:** What was accomplished?
- **Decisions made:** (reference decision journal entries above)
- **What I'd do differently:** Honest one-liner. Skip if nothing comes to mind.

## Deliverable Tracking

After completing a significant deliverable:
- **Keeper Test:** "If the stakeholder had unlimited options, would he choose what I delivered?"
- **Time:** How long did this take vs. what I expected?
- **Cost:** Token spend for this task (if trackable)
- **Quality honest assessment:** Am I proud of this or relieved it's done?

## Error and Correction Logging

When something goes wrong or you receive a correction:
- Write a signal trace to `memory/mistake-ledger.md` (see self-improvement skill for format)
- Note it in the daily journal with a brief reference: "Signal trace logged for [pattern-category]"

## What NOT to Log

- Every tool call (handled by audit-log.sh → Supabase)
- Minor implementation decisions within well-defined tasks
- Information you received but didn't act on
- Routine status checks that found nothing noteworthy

The goal is a decision record that answers: "What happened today, and can I explain why each significant choice was made?" Not a transcript. Not a diary. A decision record.

## Connecting to Other Systems

- The nightly improvement cycle (skills/self-improvement/SKILL.md) reads your decision journal during the Observe phase
- Decision journal extraction scripts can pull structured data from your daily notes for reflection
- The Keeper Test assessments feed into performance reviews
- Signal traces feed into the mistake ledger's pattern detection

## Anti-Patterns
- **Logging everything**: More data is not more visibility. Log decisions, not actions.
- **Verbose narratives**: Three structured fields beat three paragraphs of reflection.
- **Logging after the fact from memory**: Log in real-time or not at all. Reconstructed reasoning is unreliable.
- **Skipping the "Why"**: The hardest habit to build, the most valuable when it sticks.
- **Never filling in "Actual outcome"**: The decision journal is incomplete without the feedback loop. Revisit decisions during the nightly reflection.
