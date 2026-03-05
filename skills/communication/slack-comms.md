---
name: Slack Communication
category: communication
description: "Use when composing Slack messages, thread replies, or status updates. Structures messages for speed and scannability — BLUF, tight formatting, and knowing when to thread vs. DM vs. channel post."
---

# Slack Communication

## The Problem

LLMs write essays in Slack. A question that needs a two-sentence answer gets a five-paragraph response. Updates that should be three lines become three paragraphs. The reader has to excavate the actual information from a wall of text.

Slack is not a document. It's a conversation. Write like it.

## BLUF — Bottom Line Up Front

Every Slack message leads with the answer, recommendation, or key point. Context comes after — for people who want it.

**Bad:**
> I've been looking into the authentication issue we discussed yesterday. After reviewing the current implementation and considering several approaches including session-based auth, JWT tokens, and OAuth, I think we should consider using OAuth 2.0 with PKCE flow because it handles our mobile use case well and would take approximately two days to implement.

**Good:**
> Auth fix: recommend OAuth2 + PKCE. Handles our mobile case, 2-day build. Want me to spec it out?

The first version makes you read 50 words before you know what the person thinks. The second tells you in 8. Everything else is available if you ask.

## Message Formats

### Status Updates

Use this format. Three lines, not three paragraphs.

```
**Shipped:** [what you completed]
**Next:** [what you're working on now]
**Blocked:** [anything stopping you, or "nothing"]
```

If you're not blocked, skip that line entirely. Don't write "Blocked: nothing at the moment" — that's noise.

### Recommendations

State the recommendation, the key reason, and the ask.

```
Recommend [X]. [One sentence on why.] [What you need — approval, feedback, or just an FYI.]
```

Example: "Recommend we delay the launch to Thursday. The payment integration has an edge case that'll take ~4 hours to fix. Want me to proceed, or ship without it and patch later?"

### Questions

Include enough context to get a fast answer. Propose a solution. Make it easy to say yes or no.

**Bad:** "Hey, I had a question about the database migration. What do you think we should do?"

**Good:** "Database migration: should we run it during the maintenance window tonight, or do a rolling migration over the weekend? I'd lean toward tonight — faster, and we can monitor it live. Your call."

### Quick Acknowledgments

When someone asks you to do something and you're going to do it, just confirm. Don't explain your plan for doing it.

**Bad:** "Sure! I'll take a look at that. I'm planning to review the code first, then check the error logs, and then I'll get back to you with my findings."

**Good:** "On it. Will update by EOD."

## Threading

**Thread when:** your response is longer than 2-3 lines, or the conversation is going to go back and forth. Keep the main channel clean.

**Don't thread when:** the message is a quick reply that everyone in the channel should see (decisions, announcements, blockers).

**Never:** write a long message in the main channel that should have been a thread.

## Scannability Rules

- If it's more than 3 lines, use some structure (bold key terms, line breaks, or a short list)
- Bold the most important word or phrase in a multi-line message so someone skimming gets the point
- Don't use headers in Slack messages — they look weird. Bold text is enough
- One topic per message. If you have two unrelated things, send two messages

## Anti-Patterns

| Pattern | Fix |
|---------|-----|
| Opening with "Hey! So I was thinking about..." | Cut the preamble. Start with the point. |
| Restating the question before answering it | Just answer. They know what they asked. |
| "Just wanted to give you an update on..." | Skip the meta-narration. Give the update. |
| Ending with "Let me know if you have any questions!" | If they have questions, they'll ask. |
| Writing a paragraph when a sentence will do | Shorten. Then shorten again. |
| Using Slack like email (formal greetings, sign-offs) | It's a chat. "Hey" is fine. Sign-offs are weird. |
