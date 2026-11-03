---
name: post
description: Draft a LinkedIn post from the member's confirmed Byro context and check it. Send it to Byro for review only when asked.
---

# /byro:post

Follow the `byro-governance` rules throughout. Use the topic or angle in the user's request. In
Claude Code, slash-command arguments are: $ARGUMENTS

1. Call `byro_get_context`. Keep `contextHash` and `contextVersion`. If the call fails, go to the
   unreachable rule in `byro-governance`.
2. Draft one LinkedIn post using only the returned goal and claims, and avoiding every `doNotSay`
   entry. If the context has no goal or no usable claims, tell the human Byro has nothing confirmed
   yet and that they need to confirm a Goal and facts in Byro first, then stop.
3. Call `byro_check_draft` with the exact draft, `contextHash` and `contextVersion`. Findings give
   `code`, `start` and `end` offsets into the draft.
4. Fix each finding by rewording or removing the flagged text, then check again. Repeat until no
   finding remains except an advisory `unconfirmed_date`, which you check against the context or
   show to the human. Stop and ask the human on a finding you cannot fix.
5. If the result says `PARTIAL CHECK` (`check.complete` is false), the check is not a clearance:
   retry once. If it is still partial, tell the human the check was partial, show the draft as
   unchecked, and do not send it.
6. Show the checked draft and what Byro checked. If the user asked only for a draft, stop here.
7. Only if the user explicitly asked to send the checked draft to Byro, call `byro_send_to_byro`
   with that exact draft, the same `contextHash` and `contextVersion`, and a fresh `idempotencyKey`
   (a new UUID). Reuse that key only to retry the same draft after a lost response.
8. Report the `reviewUrl`, say the proposal is pending, and say the human approves and publishes in
   Byro. Never say it was approved or published.
