---
name: deploy-verification
description: "Use after ANY deployment: Vercel, Docker, VPS, cron job, or script install. Checklist to prove the deploy actually works before reporting done. Use when you say 'deployed', 'shipped', 'it's live', or 'cron created'."
---

# Deploy Verification Checklist

## When to Use
After ANY deployment: Vercel, Docker, VPS, cron job creation, script install.
Do NOT report "done" until this checklist passes.

## The Checklist

### 1. Is it running?
- [ ] Container/process is alive (not crashed, not exited)
- [ ] Logs show recent activity (not stuck, not silent)
- [ ] No error messages in the last 60 seconds of logs

### 2. Is it producing output?
- [ ] The thing it's supposed to do is happening (trades placed, data written, page loads)
- [ ] Output matches expected format/schema
- [ ] If it writes to a DB/file, verify the data arrived

### 3. Is it reachable?
- [ ] For web deploys: load the URL in a browser, check every visible section
- [ ] For APIs: make a test request and verify the response
- [ ] For cron jobs: verify the schedule is correct AND the timeout is sufficient

### 4. Is it correct?
- [ ] Data showing is real and current (not stale, not mock)
- [ ] UI elements render properly (no broken layouts, no garbled text)
- [ ] Edge cases handled (empty states, error states, loading states)

### 5. Would the stakeholder be impressed?
- [ ] Look at it with fresh eyes — pretend you've never seen it before
- [ ] Compare to the best version of this type of thing you've seen
- [ ] If the answer is "it's fine" rather than "this is great," keep working

## Cron Job Specific
When creating or modifying a cron job:
- [ ] Timeout is 3x the expected runtime (not 1x, not "should be enough")
- [ ] Test by running manually first: `openclaw cron run <id>`
- [ ] Verify the task prompt references correct file paths
- [ ] Confirm delivery channel is set correctly
- [ ] After first automated run: check output within 1 hour

## Evidence Required
Before saying "deployed" or "done," provide ONE of:
- A screenshot of the running thing
- A curl/API response showing it works
- A log snippet showing successful operation
- A browser snapshot confirming the UI renders

"The deploy command succeeded" is NOT evidence. What the user sees IS evidence.
