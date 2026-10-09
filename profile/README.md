# Rumoro

**Social listening for developers and AI agents.** Rumoro follows what people say about your product, your competitors and your market, from Reddit and Hacker News to GitHub issues and YouTube videos. Every post gets a relevance score, a sentiment and intents, and the ones worth your time reach Slack, Telegram, email, a webhook or your AI agent. Your code and your agents work with the same data you see in the dashboard.

[rumoro.dev](https://rumoro.dev) · [Docs](https://docs.rumoro.dev) · [MCP](https://docs.rumoro.dev/mcp) · [OpenAPI](https://api.rumoro.dev/v1/openapi.json) · [Dashboard](https://app.rumoro.dev)

## Pick your interface

```bash
# Any MCP client, here Claude Code
claude mcp add --transport http rumoro https://mcp.rumoro.dev/mcp
```

```ts
// TypeScript (npm install @rumoro-dev/sdk)
import { createRumoro } from '@rumoro-dev/sdk';
const rumoro = createRumoro({ apiKey: process.env.RUMORO_API_KEY! });
const { data } = await rumoro.searchMentions({ query: { platform: 'hackernews', relevant: true, limit: 25 } });
```

```python
# Python (pip install rumoro)
from rumoro import Rumoro
for mention in Rumoro(api_key="ref_...").mentions.search(platform="hackernews", relevant=True, limit=25).data:
    print(mention.classification.relevance, mention.post.url)
```

```bash
# Terminal (npm install -g @rumoro-dev/cli)
rumoro auth:login && rumoro mentions:watch --platform hackernews | jq -r '.post.url'
```

## Sources

| Source | Collected | Checked |
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

Intents include `buy_intent`, `question`, `bug_report`, `complaint` and `praise`.

## What the API covers

- **Keywords**: what to track, matching rules, groups, and a health report per keyword
- **Mentions**: search, triage, and CSV or JSON export
- **People**: the authors behind the mentions, with tags, notes and merging
- **Alerts and channels**: instant, hourly, daily or weekly delivery to Slack, Telegram, email and signed webhooks
- **Analytics**: summary, time series, breakdowns and share of voice

The SDKs are generated from the same [OpenAPI document](https://api.rumoro.dev/v1/openapi.json).

## Packages and integrations

| Repository | What it is | Get it |
| --- | --- | --- |
| [sdk](https://github.com/rumoro-dev/sdk) | TypeScript SDK | `npm install @rumoro-dev/sdk` |
| [sdk-python](https://github.com/rumoro-dev/sdk-python) | Python SDK | `pip install rumoro` |
| [cli](https://github.com/rumoro-dev/cli) | The `rumoro` command, including a live feed | `npm install -g @rumoro-dev/cli` |
| [rumoro-mcp](https://github.com/rumoro-dev/rumoro-mcp) | MCP setup for every client | `https://mcp.rumoro.dev/mcp` |
| [cursor-plugin](https://github.com/rumoro-dev/cursor-plugin) | Cursor plugin with setup and triage skills | Cursor Marketplace (in review) |
| [claude-skills](https://github.com/rumoro-dev/claude-skills) | Claude Code skills for setup and triage | Copy into `~/.claude/skills` |
| [openclaw-skill](https://github.com/rumoro-dev/openclaw-skill) | OpenClaw skill | `openclaw skills install @markolo10/rumoro` |

Found a bug or missing something? Open an issue in the relevant repository.

## From the blog

- [Reddit API pricing, limits and access in 2026](https://rumoro.dev/blog/reddit-api)

## Pricing

Pay as you go from a prepaid balance: $5 per keyword per month and $0.008 per matched mention. There are no subscriptions, seats or plans, and new accounts get $5.80 of credit without a card. Details at [rumoro.dev/pricing](https://rumoro.dev/pricing).
