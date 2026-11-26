# Auto Poster AI agent skills

Let your AI agent draft, schedule and analyze social media posts with [Auto Poster AI](https://autoposter.ai). Works with Instagram, TikTok, LinkedIn, X, Threads, Bluesky, YouTube, Pinterest, Facebook and Telegram.

This repo has two parts:

- **MCP server**: `https://agent.autoposter.ai/mcp`. The tools your agent calls (`autoposter_schedule_post`, `autoposter_get_analytics`, ...).
- **Skills**: plain `SKILL.md` files that teach the agent the workflows: check limits, write per-platform copy, confirm before publishing.

## Skills

| Skill | What it does |
| --- | --- |
| [`schedule-social-posts`](skills/schedule-social-posts/SKILL.md) | Draft, schedule or publish posts to one or many platforms, with media, threads and first comments |
| [`repurpose-content`](skills/repurpose-content/SKILL.md) | Turn an article, URL or transcript into platform-specific posts |
| [`announce-release`](skills/announce-release/SKILL.md) | Turn git commits and changelogs into launch announcements |
| [`social-analytics-report`](skills/social-analytics-report/SKILL.md) | Report on top posts, growth and what to post next |
| [`manage-post-queue`](skills/manage-post-queue/SKILL.md) | List, edit, approve, cancel and debug posts |

## Install

### Claude Code

```bash
/plugin marketplace add autoposterai/agent-skills
/plugin install auto-poster-ai@autoposterai
```

This installs the skills and the MCP server. Run `/mcp`, pick `autoposter` and sign in.

### Any agent that supports Agent Skills

```bash
npx skills add autoposterai/agent-skills
```

Then add the MCP server (below).

### MCP server only

Get an API key in Auto Poster AI, then:

```bash
claude mcp add --transport http autoposter https://agent.autoposter.ai/mcp --header "Authorization: Bearer YOUR_AUTOPOSTER_API_KEY"
```

For Cursor and other clients that read an `mcp.json`:

```json
{
  "mcpServers": {
    "autoposter": {
      "url": "https://agent.autoposter.ai/mcp",
      "headers": { "Authorization": "Bearer YOUR_AUTOPOSTER_API_KEY" }
    }
  }
}
```

Claude on web, desktop and mobile: add `https://agent.autoposter.ai/mcp` as a custom connector and sign in with OAuth.

## Safety

- The skills draft by default and ask before publishing, editing or deleting.
- If your API key cannot publish directly, posts go to `pending_approval` and your approvers are notified.
- Edits overwrite the previous text with no undo, so the skills show old and new text first.

## Try it

- "Schedule a launch post for LinkedIn and X tomorrow at 10:00 America/New_York."
- "Turn this article into a thread for X and a post for LinkedIn: https://..."
- "Announce the latest release from the git log."
- "How did my posts do last month?"
- "What's scheduled this week?"

## License

MIT
