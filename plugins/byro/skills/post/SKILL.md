---
name: post
description: Draft a LinkedIn post from the member's Byro context, check it, and send it to Byro for human review.
---

# /byro:post

Follow the `byro-governance` rules throughout. Arguments, if any, are the topic or angle: $ARGUMENTS

1. Call `byro_get_context`. Keep `contextHash` and `contextVersion`. If the call fails, go to the
   unreachable rule in `byro-governance`.
2. Draft one LinkedIn post using only the returned goal and claims, and avoiding every `doNotSay`
   entry. If the context has no goal or no usable claims, tell the human and stop.
3. Call `byro_check_draft` with the exact draft, `contextHash` and `contextVersion`. Findings give
   `code`, `start` and `end` offsets into the draft.
4. Fix each finding by rewording or removing the flagged text, then check again. Repeat until
   `findings` is empty. Stop and ask the human on a finding you cannot fix.
5. Call `byro_send_to_byro` with the exact checked draft, the same `contextHash` and
   `contextVersion`, and a fresh `idempotencyKey` (a new UUID). Reuse that key only to retry the
   same draft after a lost response.
6. Report the `reviewUrl`, say the proposal is pending, and say the human approves and publishes in
   Byro. Never say it was approved or published.
