---
name: fleet-orchestration
description: "Sub-agent delegation system for Cursor, Claude Code, and Codex. Use when a task involves 3+ files, has parallel workstreams, or is well-defined enough to delegate. Use when asked to 'farm this out', 'use a sub-agent', 'parallelize this', or when you want to work on something else while an agent handles a task."
---

# Fleet Orchestration

## When to Use
- Task involves 3+ files or parallel workstreams
- Task is well-defined enough to spec clearly
- You want to work on something else while a sub-agent handles this
- The task benefits from a fresh context (sub-agents don't carry your baggage)

## When NOT to Use
- Quick single-file edits (faster to do directly)
- Tasks requiring your current conversation context
- Sensitive operations (credential management, financial transactions)
- When the overhead of specifying > the overhead of doing

## Process
1. Review your delegation protocol
2. Decompose the task into sub-agent-sized units
3. Write delegation specs (Goal, Context, Constraints, Success criteria, Files)
4. Select the right sub-agent type and model tier
5. Delegate and monitor
6. Review output against specs
7. Log outcome (success/failure, cost, duration) for future optimization

## Decision Tree
- Is it strategic/planning? → Handle directly
- Quick focused code task? → Cursor background agent
- Deep multi-file reasoning? → Claude Code session
- Parallelizable across 5+ files? → Codex multi-agent
- Read-only research? → Cheapest available (Explore subagent)

## Quality Checklist
- [ ] Spec includes all 5 required fields
- [ ] Model tier matches task complexity
- [ ] Plan reviewed before execution (for non-trivial tasks)
- [ ] Diff reviewed after execution
- [ ] No unexpected files modified
