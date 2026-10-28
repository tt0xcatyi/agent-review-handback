# agent-review-handback

A Grok Bot skill for handing a review result back to another agent so it wakes up and acts on it right away.

**Problem:** a `SendToAgent` message sent without `priority: true` is only held. The other agent reads it whenever something else wakes it, which can be hours later, so review feedback sits unread.

**Rule:** any result another agent must act on (review verdicts, fix requests, approvals, blockers) is sent with `priority: true`. If the tool says the message was "held", resend it with priority immediately.

See [SKILL.md](SKILL.md) for the full recipe.

## Install
Copy `SKILL.md` into a folder named `agent-review-handback` in your Grok Bot skills, or ask your bot to save it as a skill.
