# Rumoro

**Social listening for developers and AI agents.** Rumoro finds what people say about your product, your competitors and your topics across Reddit, X, Hacker News, GitHub and more. It scores every mention for relevance, sentiment and intent, and sends the ones that matter to Slack, Telegram, email, a webhook, or straight to your AI agent. The dashboard is one client of the same API your code uses.

[rumoro.dev](https://rumoro.dev) · [Docs](https://docs.rumoro.dev) · [MCP](https://docs.rumoro.dev/mcp) · [API reference](https://api.rumoro.dev/v1/openapi.json) · [Dashboard](https://app.rumoro.dev)

## Four ways in

```bash
# An AI agent: Claude Code, Cursor, Codex and any MCP client
claude mcp add --transport http rumoro https://mcp.rumoro.dev/mcp
```

```ts
// TypeScript: npm install @rumoro-dev/sdk
import { createRumoro } from '@rumoro-dev/sdk';
const rumoro = createRumoro({ apiKey: process.env.RUMORO_API_KEY! });
const { data } = await rumoro.searchMentions({ query: { platform: 'hackernews', relevant: true, limit: 25 } });
```

```python
# Python: pip install rumoro
from rumoro import Rumoro
for mention in Rumoro(api_key="ref_...").mentions.search(platform="hackernews", relevant=True, limit=25).data:
    print(mention.classification.relevance, mention.post.url)
```

```bash
# The command line: npm install -g @rumoro-dev/cli
rumoro auth:login && rumoro mentions:watch --platform hackernews | jq -r '.post.url'
```

## What it watches

| Source | What arrives | How often |
| --- | --- | --- |
| Reddit | Posts | Every 30 minutes |
| X | Posts and replies | Every hour |
| Hacker News | Stories and comments | Every 5 minutes |
| GitHub | Issues and pull requests | Every 15 minutes |
| Bluesky | Posts | In seconds |
| LinkedIn | Public posts | Every 3 hours |
| Stack Overflow | Questions and answers | Every hour |
| DEV | Articles | Every hour |
| YouTube | Videos | Twice a day |
| News | Web articles | Every 15 minutes |
| TikTok | Videos | Every 3 hours |
| Instagram | Posts and reels | Every 6 hours |
| App Store | Reviews | Once a day |

Every mention carries a relevance score, a sentiment and intents such as `buy_intent`, `question`, `bug_report`, `complaint` and `praise`.

## The API, in five areas

Keywords (with a health report per keyword) · Mentions (search, triage, CSV and JSON export) · People (the authors behind the mentions, with tags, notes and merges) · Alerts and channels (instant rules and daily or weekly digests to Slack, Telegram, email and signed webhooks) · Analytics (summary, series, breakdown, share of voice). It's all one [OpenAPI document](https://api.rumoro.dev/v1/openapi.json), and the SDKs below are generated from it.

## Repositories

| Repository | What it is | Install |
| --- | --- | --- |
| [sdk](https://github.com/rumoro-dev/sdk) | Official TypeScript SDK | `npm install @rumoro-dev/sdk` |
| [sdk-python](https://github.com/rumoro-dev/sdk-python) | Official Python SDK | `pip install rumoro` |
| [cli](https://github.com/rumoro-dev/cli) | `rumoro` on the command line, with a live mentions feed | `npm install -g @rumoro-dev/cli` |
| [rumoro-mcp](https://github.com/rumoro-dev/rumoro-mcp) | Setup for the hosted MCP server, for every client | `https://mcp.rumoro.dev/mcp` |
| [cursor-plugin](https://github.com/rumoro-dev/cursor-plugin) | Rumoro for Cursor, with setup and triage skills | Cursor Marketplace (in review) |
| [claude-skills](https://github.com/rumoro-dev/claude-skills) | Setup and triage skills for Claude Code | Copy into `~/.claude/skills` |
| [openclaw-skill](https://github.com/rumoro-dev/openclaw-skill) | Rumoro skill for OpenClaw agents | `openclaw skills install @markolo10/rumoro` |

Issues are welcome on any of them.

## Latest from the blog

- [Reddit API pricing, limits and access in 2026](https://rumoro.dev/blog/reddit-api)

## Pricing

Prepaid, with no subscription, seats or tiers. $5 per keyword per month plus $0.008 per matched mention. New accounts start with $5.80 of free credit, no card needed. See [rumoro.dev/pricing](https://rumoro.dev/pricing).
