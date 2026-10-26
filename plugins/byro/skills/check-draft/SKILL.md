---
name: check-draft
description: Check an existing draft against the member's confirmed Byro context. Explain findings and send it to Byro for review only when explicitly asked.
---

# Check a draft with Byro

Follow `byro-governance` throughout. Use the exact draft the user supplied. If there is no draft,
ask for it. Do not send a draft to Byro merely because the user asked for a check.

1. Call `byro_get_context` and keep `contextHash` and `contextVersion`.
2. Call `byro_check_draft` with the exact supplied draft and those context values.
3. Show the findings and their source links. Explain that no findings covers only figures, named
   claims and do-not-say phrases; it is not approval. If the user requested edits, make them and
   re-check the exact revised draft before reporting it as checked.
4. Send only if the user explicitly asked and the exact draft has zero findings. If findings remain,
   report them and stop. Otherwise call `byro_send_to_byro` with the checked draft, the same context
   values, and a fresh UUID `idempotencyKey`. Reuse the key only after an uncertain response and
   inspection of the proposal destination.
5. If sent, report the review link and pending state. Approval and publication happen in Byro.
