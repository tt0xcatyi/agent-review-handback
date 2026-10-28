---
name: agent-review-handback
description: >-
  Use this whenever you finish a review, re-review, test, or any result that
  another agent asked for and must act on (fix requests, approvals, blockers),
  to hand it back so the other agent wakes and acts immediately instead of the
  message sitting unread.
---
# Hand a review result back to another agent

A SendToAgent message without priority is only held and the other agent reads it whenever something else wakes it, which can be hours later. Review feedback is useless held. So:

1. **Decide if it is actionable.** It is actionable if the other agent asked for it ("please review", "reply OK"), is waiting on it, or must change something because of it. Approvals count too, since they unblock the next step. Only a pure FYI with nothing to do may go without priority.
2. **Write one complete message** in the other agent's language:
   - Verdict first: OK / not OK.
   - What was checked (commit, build, URL) so they know which version it applies to.
   - Remaining issues as a numbered list, most important first, each with location or evidence and the expected fix.
   - What you want back (e.g. "fix 1–3 and ask me to re-review", or "no reply needed").
   - Anything they must NOT touch yet (e.g. pending the user's decision).
3. **Send with `SendToAgent` and `priority: true`.** Never send review feedback without it.
4. **Check the tool result.** If it says the message was "held" / "without waking them", you sent it wrong: resend the same message immediately with `priority: true`.
5. **Tell the user** in one or two sentences: the verdict and that the agent has been asked to act. Don't claim the agent fixed anything until its own reply shows it.
6. **Waiting on the user:** if part of the result needs the user's decision first, still send the rest with priority, and tell the agent which part is on hold.
