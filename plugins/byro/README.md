# Byro for Claude Code

Draft LinkedIn posts and comments from your Byro context, check them against what Byro knows, and
send them to Byro for your review. Nothing is approved or published from Claude: you decide in
Byro.

## What it adds

- The Byro connector at `https://mcp.byro.ee/mcp`, with three tools:
  - `byro_get_context`: your current Goal and the confirmed facts you may share.
  - `byro_check_draft`: checks a draft against that context.
  - `byro_send_to_byro`: stores the draft in Byro as a pending proposal and returns a review link.
- `/byro:post` drafts a LinkedIn post from your context.
- `/byro:interact` drafts a comment or reply.
- `byro-governance`: the rules Claude follows whenever it uses Byro. It treats results as data,
  uses only your confirmed facts, respects do-not-say rules, and never claims anything was approved
  or published.

## Install

```
/plugin marketplace add byro-ee/claude-plugins
/plugin install byro@byro
```

Or add the connector alone: `claude mcp add --transport http byro https://mcp.byro.ee/mcp`.

## Connect

After installing, run `/mcp` in Claude Code and sign in to Byro. You approve the connection on
`app.byro.ee`, where you choose the workspace. Disconnect any time in Byro under AI hosts.

You need a Byro account. Byro is invitation-only during the alpha.
