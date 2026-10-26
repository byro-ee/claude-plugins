---
name: setup
description: Connect Byro to this assistant, verify the selected workspace, and explain the available actions.
---

# Connect Byro

1. Explain that Byro currently requires an invitation and that the connection uses the user's own
   Byro account. Never ask for a password or one-time code in chat.
2. Guide the user through this host's Connect Byro prompt. On Byro's consent page, have them check
   the host, workspace and permissions before approving.
3. After connection, call `byro_get_context` to confirm the tools are available. Say whether a Goal
   and confirmed facts were returned without repeating private facts unless the user asks.
4. Explain the three actions: read confirmed context, check an exact draft, and send a checked
   draft as a pending proposal only on an explicit request. Review and publication stay in Byro.
5. If the tools are unavailable, report the failed step and direct the user to Byro's AI hosts page
   or https://byro.ee/contact. Do not pretend the connection succeeded.
