# Byro plugins for Claude Code

[Byro](https://byro.ee) turns your team's confirmed facts into LinkedIn posts you can trust. This
marketplace holds the Byro plugin for Claude Code.

## Install

```
/plugin marketplace add byro-ee/claude-plugins
/plugin install byro@byro
```

Then run `/mcp` and sign in to Byro. You approve the connection on `app.byro.ee` and choose the
workspace. You can disconnect any time in Byro under AI hosts.

## What you get

- The Byro connector (`https://mcp.byro.ee/mcp`) with three tools: read your current goal and
  confirmed facts, check a draft against them, and send a draft to Byro as a pending proposal.
- `/byro:post` and `/byro:interact` to draft a LinkedIn post or comment from your context.
- `/byro:check-draft` to check a draft you already have, and `/byro:setup` to connect Byro.
- `byro-governance`, the rules Claude follows with Byro. Results are treated as data. Claude uses
  only your confirmed facts, respects your do-not-say rules, and never claims anything was
  approved or published. You decide in Byro.

Byro is invitation-only during the alpha. You need a Byro account to connect.
