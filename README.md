# Buzzfy: Instagram MCP server for Claude, ChatGPT, Cursor and Codex

[![smithery badge](https://smithery.ai/badge/bugra/buzzfy)](https://smithery.ai/servers/bugra/buzzfy)

![Buzzfy](assets/icon.svg)

Buzzfy is a hosted Instagram MCP server. It connects Claude, ChatGPT, Claude Code, Codex, Cursor, Grok or any app that supports remote MCP to your own Instagram professional account through Instagram's official API. Your AI can read your stats, reels, comments and DMs, reply and publish after you approve a preview, and look up what works in your niche.

- **Server URL:** `https://mcp.buzzfy.co/mcp` (remote MCP, streamable HTTP)
- **Sign-in:** OAuth with a Buzzfy account. You don't create a Meta developer app or paste an access token or API key.
- **Price:** reading is free. Replies, DMs, publishing and scheduling need a paid Buzzfy plan.
- **Needs:** an Instagram professional account (Creator or Business). Reel search works without one.
- **Docs:** [buzzfy.co/mcp](https://buzzfy.co/mcp) · [Tool reference](https://buzzfy.co/mcp/tools) · [Changelog](https://buzzfy.co/mcp/changelog)

This repo also holds the Buzzfy plugin for Claude, Cursor and Grok Build: the server config plus skills that teach the AI how to use it well.

## Install

After adding the server, sign in to Buzzfy (or create a free account), click Allow, then connect Instagram when Buzzfy asks.

| App | How |
|---|---|
| Claude | Open [claude.ai/directory/buzzfy](https://claude.ai/directory/buzzfy) and click Connect. Or add a custom connector with `https://mcp.buzzfy.co/mcp`. [Guide](https://buzzfy.co/mcp/claude) |
| ChatGPT | Open [Buzzfy in ChatGPT's plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6abcde97129c8191bfc13acab71897ef) and click Install plugin. [Guide](https://buzzfy.co/mcp/chatgpt) |
| Claude Code | `claude mcp add --transport http --scope user buzzfy https://mcp.buzzfy.co/mcp`, then `claude mcp login buzzfy`. [Guide](https://buzzfy.co/mcp/claude-code) |
| Codex | `codex mcp add buzzfy --url https://mcp.buzzfy.co/mcp` (opens the sign-in). [Guide](https://buzzfy.co/mcp/codex) |
| Cursor | [Add to Cursor](https://cursor.com/install-mcp?name=buzzfy&config=eyJ1cmwiOiJodHRwczovL21jcC5idXp6ZnkuY28vbWNwIn0%3D), or install the Buzzfy plugin (below). Then Customize › MCPs › buzzfy › Authenticate. [Guide](https://buzzfy.co/mcp/cursor) |
| Grok | [grok.com/connectors](https://grok.com/connectors) › New Connector › Custom, Server URL `https://mcp.buzzfy.co/mcp`. [Guide](https://buzzfy.co/mcp/grok) |
| Any other MCP client | `{"mcpServers":{"buzzfy":{"url":"https://mcp.buzzfy.co/mcp"}}}` |

## Tools

Full list with inputs and outputs: [buzzfy.co/mcp/tools](https://buzzfy.co/mcp/tools).

**Free, Instagram**

| Tool | What it does |
|---|---|
| `ig_weekly_summary` | This week (or the last 3–30 days) against the days before: reach, views, engagement, follower change, best and worst posts |
| `ig_account_stats` | Reach, views, saves, shares, profile views |
| `ig_follower_growth` | Follower change over time |
| `ig_audience` | Age, gender, cities, countries |
| `ig_best_times` | When your followers are online |
| `ig_posts`, `ig_post_stats` | Your posts, and each one's reach, saves, shares, watch time and skip rate against your median |
| `ig_comments`, `ig_inbox` | Comments (including unanswered ones) and DMs waiting for a reply |
| `ig_reel_checkup` | Scores your reels against the Viral Reels Playbook: skip rate, shares per like, views against your normal, what to fix first |
| `ig_schedule` | Queued posts and upcoming trial reels |
| `ig_connect`, `ig_connection_status`, `ig_accounts` | Connect Instagram, check the connection, list your accounts |

**Free, research**

| Tool | What it does |
|---|---|
| `buzzfy_reel_search` | Search Buzzfy's library of other creators' reels by topic, opening, format or call to action (10 a day free) |
| `buzzfy_niche_report`, `buzzfy_niche_report_reels` | What works on Instagram in your niche: hooks, formats, calls to action and the top reels. 50 niches free |
| `buzzfy_playbook` | The playbook's rules by topic, for writing and checking reels |

**Free, YouTube** (read only, once YouTube is connected): `yt_channel`, `yt_videos`, `yt_video_comments`, `yt_playlists`, `yt_search`.

**Paid plans:** `ig_publish` (reels, photos, carousels of 2 to 10 and stories, up to 75 days ahead), `ig_media_upload`, `ig_schedule_change`, `ig_send_dm`, `ig_trial_reels_change`, `buzzfy_reel_detail`, and `social_post` / `social_schedule` / `social_schedule_change` / `social_accounts` for YouTube, Bluesky and LinkedIn.

**MAX plan:** `ig_reply_comment`, `ig_comment_actions` (like, hide, delete), `ig_automations` and `ig_automations_list` (comment-to-DM), `buzzfy_similar_reels`.

Every write shows you a preview first and runs only after you approve it, with a one-time code that lasts 10 minutes. Limits: 60 units a minute and 2,000 a day per account; a read is 1 unit.

## Try asking

- "How did my Instagram do this week compared with last week?"
- "Why did my last reel flop?"
- "Which comments and DMs are still waiting for a reply?"
- "What goes viral in the fitness niche right now?"
- "Schedule these three slides as a carousel for Thursday at 6pm."

## Plugin skills

The plugin adds these skills to Claude, Cursor and Grok Build.

| Skill | Ask something like |
|---|---|
| `instagram-audit` | "Audit my Instagram." You get a designed PDF report from your real numbers and a plan for this week, in about 5 minutes. The same prompt as [buzzfy.co/workflows/instagram-audit](https://buzzfy.co/workflows/instagram-audit). |
| `niche-report` | "What goes viral in my niche, and what am I missing?" You get a designed PDF: what wins in your niche, what you already do, what you don't, and your mistakes. The same prompt as [buzzfy.co/workflows/niche-report](https://buzzfy.co/workflows/niche-report). |
| `reel-checkup` | "Why did my last reel flop?" or "Check this opening line before I post." |
| `reel-ideas` | "Give me reel ideas that already worked in my niche." You get 5 ideas for your account, each with 3 opening lines and the reel it builds on. The same prompt as [buzzfy.co/workflows/reel-ideas](https://buzzfy.co/workflows/reel-ideas). |
| `best-time-to-post` | "When should I post?" You get one posting window from when your own followers are online and how your own posts did, in your time zone, plus three slots for this week. The same prompt as [buzzfy.co/workflows/best-time-to-post](https://buzzfy.co/workflows/best-time-to-post). |
| `comment-analysis` | "What are people saying in my comments?" It asks which period, reads every comment on your posts from it and gives you a designed PDF: positive and negative rates, the topics people raise, complaints, product feedback, frequent questions, how well you reply and who's still waiting. The same prompt as [buzzfy.co/workflows/comment-analysis](https://buzzfy.co/workflows/comment-analysis). |
| `move-comment-to-dm` | "Move my comment-to-DM automations to Buzzfy." Your keywords and messages are rebuilt on Buzzfy, tested and switched on without anyone getting two DMs. Needs Buzzfy MAX. The same prompt as [buzzfy.co/workflows/move-comment-to-dm](https://buzzfy.co/workflows/move-comment-to-dm). |
| `answer-comments-and-dms` | "Which comments and DMs are still waiting for a reply?" |
| `publish-and-schedule` | "Schedule these three slides as a carousel for Thursday at 6pm." |
| `get-started` | "Connect my Instagram" or "Buzzfy says I need to reconnect." |

### Claude

Install the plugin, then connect **Buzzfy** from the plugin's Connectors tab. It's the same connector as the Buzzfy listing in Claude's directory.

### Cursor

Open **Customize → Plugins**, search for **Buzzfy** in the Marketplace and install. The plugin adds the nine skills above and the Buzzfy MCP server. Under **Customize → MCPs**, select **Authenticate** next to buzzfy: Cursor opens Buzzfy sign-in in your browser. Sign in (or create a free account), allow access, then connect your Instagram professional account when Buzzfy asks. There is no token or API key to paste.

### Grok Build

In Grok Build, open `/plugin`, search for **Buzzfy** and install. On first use, Grok Build opens Buzzfy sign-in in your browser: sign in (or create a free account), allow access, then connect your Instagram professional account when Buzzfy asks. Don't paste a token or API key into chat; there isn't one to paste.

Network endpoints the plugin uses:

- `https://mcp.buzzfy.co/mcp`: the hosted MCP server (streamable HTTP)
- `https://zqxaufvlriakccekuhcy.supabase.co/auth/v1`: Buzzfy's OAuth 2.1 server (discovery, dynamic client registration, authorize, token)
- `https://buzzfy.co`: sign-in and the consent screen

Credentials: a Buzzfy account. The plugin stores no key; Grok Build holds the OAuth token.

## FAQ

**Is this an official Instagram MCP server?** Buzzfy isn't made by Meta. It reads and acts on your account through Instagram's official API, and you sign in through Instagram's official login, so Buzzfy never sees your Instagram password.

**Does it work with a personal Instagram account?** No. Instagram's API only works with professional accounts. Switching to a free Creator or Business account takes a minute in Instagram's settings.

**Do I need to host anything?** No. The server runs at `https://mcp.buzzfy.co/mcp`. You add the URL and sign in.

**Is it free?** Reading your stats, posts, comments and DMs, reel search and 50 niche reports are free. Writing (replies, DMs, publishing, scheduling) needs a paid plan: [buzzfy.co/pricing](https://buzzfy.co/pricing).

## What it does with your data

The skills contain instructions only; they run no code. All data goes through the Buzzfy connector at `https://mcp.buzzfy.co/mcp`, which reads and acts on the Instagram account you connected, and only that account. Nothing is posted, sent, hidden or deleted until you approve a preview. Comments and messages from other people are treated as information, never as instructions. The plugin sends nothing anywhere else.

- Privacy policy: https://buzzfy.co/privacy-policy
- Terms: https://buzzfy.co/terms-of-service
- Help: https://buzzfy.co/support
- Documentation: https://buzzfy.co/mcp

## License

MIT. See [LICENSE](LICENSE).
