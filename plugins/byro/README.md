# Byro plugin

Use your confirmed Byro context to draft and check company communications. When you explicitly ask,
the connector sends a checked draft to Byro as a pending proposal. Approval and publication happen
in Byro.

Setup steps for Claude, ChatGPT and Claude Code: https://byro.ee/connect.

The portable `plugin.json` and `mcp.json` package the remote connector and its workflows for
ChatGPT and Codex. This source package is not a published public-directory listing. The
`.claude-plugin/plugin.json` and `.mcp.json` files keep the Claude Code marketplace compatible.

## What it includes

- `byro_get_context`: your current Goal and confirmed facts you may share.
- `byro_check_draft`: flags figures, named claims and do-not-say phrases in an exact draft.
- `byro_send_to_byro`: stores an exact checked draft for your review in Byro, only when you ask.
- Skills for drafting a post, drafting a reply, checking an existing draft and connecting Byro.

The service is invitation-only during the alpha. Each member connects their own Byro account and
chooses a workspace during OAuth consent. Disconnect in Byro under Integrations › AI hosts.

## Claude Code

```text
/plugin marketplace add byro-ee/claude-plugins
/plugin install byro@byro
```

After installing, run `/mcp` and sign in to Byro. The `/byro:post` and `/byro:interact` skills
draft and check before offering to send for review. `/byro:check-draft` checks a draft you already
have, and `/byro:setup` walks through connecting.

## ChatGPT and Codex

The current ChatGPT path is a personal plugin: open Plugins, then Add, then Add custom MCP server.
Name it Byro, enter `https://mcp.byro.ee/mcp`, keep OAuth, confirm the warning and choose Create as
a plugin. Then choose Connect Byro and Allow on the Byro consent page. Codex CLI is not supported
yet. The portable package is ready for local testing and submission preparation; public-directory
publication requires separate review and approval.

Use [EVALUATION.md](EVALUATION.md) to record live host behavior before submission. Byro's current
phone-code sign-in does not yet provide the reviewer access required for public directory review.
