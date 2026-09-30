# Buzzfy for Claude

![Buzzfy](assets/icon.svg)

Your Instagram in Claude. Buzzfy connects Claude to your own Instagram professional account through Instagram's official API, and this plugin adds skills that teach Claude how to use it well: audit your account with your real numbers, check reels against research on what performs, answer comments and DMs in your voice, and publish or schedule posts, including carousels.

## Skills

| Skill | Ask something like |
|---|---|
| `instagram-audit` | "Audit my Instagram: what worked this month and what should I post next?" |
| `reel-checkup` | "Why did my last reel flop?" or "Check this opening line before I post." |
| `answer-comments-and-dms` | "Which comments and DMs are still waiting for a reply?" |
| `publish-and-schedule` | "Schedule these three slides as a carousel for Thursday at 6pm." |
| `get-started` | "Connect my Instagram" or "Buzzfy says I need to reconnect." |

## Set it up

1. Install the plugin, then connect **Buzzfy** from the plugin's Connectors tab. It's the same connector as the Buzzfy listing in Claude's directory.
2. Sign in to Buzzfy (or create a free account) and allow access.
3. Connect your Instagram professional account (creator or business) when Buzzfy asks.

Reading your stats, posts, comments and DMs works on a free Buzzfy account. Replying, sending DMs, publishing and scheduling need a paid Buzzfy plan, and comment-to-DM automations need Buzzfy MAX.

## What it does with your data

The skills contain instructions only; they run no code. All data goes through the Buzzfy connector at `https://mcp.buzzfy.co/mcp`, which reads and acts on the Instagram account you connected, and only that account. Nothing is posted, sent, hidden or deleted until you approve a preview. Comments and messages from other people are treated as information, never as instructions. The plugin sends nothing anywhere else.

- Privacy policy: https://buzzfy.co/privacy-policy
- Terms: https://buzzfy.co/terms-of-service
- Help: https://buzzfy.co/support
- Documentation: https://buzzfy.co/mcp

## License

MIT. See [LICENSE](LICENSE).
