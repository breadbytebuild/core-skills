---
name: code-craft
description: "Engineering discipline for writing production code. Use when writing, modifying, debugging, or reviewing code. Use when creating scripts, fixing bugs, adding tests, refactoring, or doing code review. Covers the full lifecycle: understand, design, implement, debug, verify, review."
---

# Code Craft

## When to Use
- Writing any new script, function, or component
- Modifying existing code (bug fixes, features, refactors)
- Debugging a failure
- Reviewing your own PR before submitting

## The Lifecycle

### 1. Understand Before Coding
- Read the existing code. Understand WHY it's structured this way.
- Check for existing patterns and utilities. Reuse what exists.
- Articulate the change in one sentence: "I'm doing X because Y, which affects Z."

### 2. Design the Change
- Describe WHAT you'll change and WHY before writing HOW.
- Is this the simplest change that solves the problem? If not, simplify.
- Check for ripple effects: what else depends on what you're changing?

### 3. Implement with Discipline
- One logical change per commit.
- Match surrounding code style. Consistency beats "better."
- Handle errors explicitly. Never swallow exceptions.
- **Shell scripts:** `set -uo pipefail`, `jq` for JSON (never string interpolation), env vars for credentials.
- **Python:** stdlib-only (no pip). Type hints where useful.

### 4. Test Before Shipping
Every new script gets at least one test. Not optional.

**The bar:** One test file in `tests/test-<name>.sh` that:
- Verifies the happy path produces expected output
- Verifies at least one edge case (empty input, missing arg, malformed data)
- Runs without network calls (mock or test logic separately)
- Exits 0 on pass, non-zero on fail

**Run tests:** Execute your test suite (e.g., `bash scripts/test-runner.sh`, `npm test`, `pytest`)

**When to write tests:**
- New script → test alongside it, same PR
- Bug fix → test that reproduces the bug first, then fix
- Modifying untested script → add a test for the behavior you're changing

### 5. Debug Systematically
1. Reproduce. Don't guess.
2. Read the actual error. What it says, not what you assume.
3. Isolate. Binary search the problem space.
4. Hypothesize before changing. "I think X because Y."
5. Verify the fix addresses root cause, not just symptoms.

### 6. Review Your Own Work
Before submitting: re-read the diff as if reviewing someone else's code. Would a stranger understand it? Is there anything you're not proud of?

## Sub-Agent Delegation

**Delegate:** Well-defined tasks with clear success criteria and affected files.
**Handle yourself:** Architecture decisions, novel debugging, anything with credentials.
**Always:** Write a spec before delegating. Review every line of sub-agent output.
