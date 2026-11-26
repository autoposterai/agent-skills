<p align="center">
  <img src="assets/logo.png" alt="Auto Poster AI" width="120" />
</p>

<h1 align="center">Auto Poster AI agent skills</h1>

<p align="center">
  <strong>Draft, schedule, publish and analyze social media posts from your AI agent.</strong><br />
  Works with:<br />
  <a href="https://autoposter.ai/agents/claude">Claude</a> ·
  <a href="https://autoposter.ai/agents/claude-code">Claude Code</a> ·
  <a href="https://autoposter.ai/agents/chatgpt">ChatGPT</a> ·
  <a href="https://autoposter.ai/agents/cursor">Cursor</a> ·
  <a href="https://autoposter.ai/agents/codex">Codex</a> ·
  <a href="https://autoposter.ai/agents/gemini">Gemini CLI</a> ·
  <a href="https://autoposter.ai/agents/grok">Grok</a> ·
  <a href="https://autoposter.ai/agents/copilot">GitHub Copilot</a> ·
  <a href="https://autoposter.ai/agents/windsurf">Windsurf</a> ·
  <a href="https://autoposter.ai/agents/raycast">Raycast</a> ·
  <a href="https://autoposter.ai/agents/openclaw">OpenClaw</a> ·
  <a href="https://autoposter.ai/agents/hermes">Hermes Agent</a> ·
  <a href="https://autoposter.ai/agents/muse">Muse</a> ·
  <a href="https://autoposter.ai/agents/n8n">n8n</a> ·
  <a href="https://autoposter.ai/mcp">MCP server</a>
</p>

[Auto Poster AI](https://autoposter.ai) is a social media scheduler. This repo connects it to your AI agent in one install:

- **Hosted MCP server** at `https://agent.autoposter.ai/mcp`. 16 tools for posts, media, accounts and analytics. Sign in with OAuth, no local install, no CLI.
- **Seven skills** that teach the agent the workflows: check platform limits, write per-platform copy, ask before publishing.

## Platforms

Post to [Instagram](https://autoposter.ai/instagram), [TikTok](https://autoposter.ai/tiktok), [LinkedIn](https://autoposter.ai/linkedin), [X](https://autoposter.ai/twitter), [Facebook](https://autoposter.ai/facebook), [Threads](https://autoposter.ai/threads), [YouTube](https://autoposter.ai/youtube), [Pinterest](https://autoposter.ai/pinterest), [Bluesky](https://autoposter.ai/bluesky), [Mastodon](https://autoposter.ai/mastodon), [Telegram](https://autoposter.ai/telegram), [Discord](https://autoposter.ai/discord), [WordPress](https://autoposter.ai/wordpress) and [Google Business Profile](https://autoposter.ai/google-business).

Formats: feed posts, carousels, Reels, Stories, YouTube Shorts, threads and first comments.

## Skills

| Skill | What it does |
| --- | --- |
| [`schedule-social-posts`](skills/schedule-social-posts/SKILL.md) | Draft, schedule or publish posts to one or many platforms, with media, threads and first comments |
| [`repurpose-content`](skills/repurpose-content/SKILL.md) | Turn an article, URL or transcript into platform-specific posts |
| [`announce-release`](skills/announce-release/SKILL.md) | Turn git commits and changelogs into launch announcements |
| [`social-analytics-report`](skills/social-analytics-report/SKILL.md) | Report on top posts, growth and what to post next |
| [`manage-post-queue`](skills/manage-post-queue/SKILL.md) | List, edit, approve, cancel and debug posts |
| [`manage-media-library`](skills/manage-media-library/SKILL.md) | Upload images and videos (up to 5 GB) and reuse library media |
| [`check-accounts-and-rules`](skills/check-accounts-and-rules/SKILL.md) | List connected accounts, show the signed-in profile, check platform limits |

Together the skills cover all 16 MCP tools.

## Install

You need an [Auto Poster AI account](https://app.autoposter.ai/signup) with at least one connected social account. Step-by-step guides with screenshots for every agent are on the [agents page](https://autoposter.ai/agents).

### Claude Code

[Guide](https://autoposter.ai/agents/claude-code)

```bash
/plugin marketplace add autoposterai/agent-skills
/plugin install auto-poster-ai@autoposterai
```

Run `/mcp`, pick `autoposter` and sign in.

### Cursor

[Guide](https://autoposter.ai/agents/cursor). This repo ships a Cursor plugin manifest at `.cursor-plugin/plugin.json`. Local install:

```bash
git clone https://github.com/autoposterai/agent-skills.git
ln -s "$(pwd)/agent-skills" ~/.cursor/plugins/local/auto-poster-ai
```

Then restart Cursor or run **Developer: Reload Window**.

### Gemini CLI

[Guide](https://autoposter.ai/agents/gemini)

```bash
gemini extensions install https://github.com/autoposterai/agent-skills
```

Gemini CLI opens a browser to sign in on first use. Run `/mcp auth autoposter` to sign in again.

### Grok

[Guide](https://autoposter.ai/agents/grok). Add this repo as a marketplace source in Grok Build. It carries `.grok-plugin/plugin.json` and `.grok-plugin/marketplace.json`, and bundles the MCP server.

### Any agent that supports Agent Skills

```bash
npx skills add autoposterai/agent-skills
```

Then add the MCP server below.

### MCP server only

Works in ChatGPT, Claude, Codex, GitHub Copilot, Windsurf, Raycast, OpenClaw, Hermes Agent, Muse, n8n and any other MCP client. Pick your agent's [setup guide](https://autoposter.ai/agents), or use the URL directly:

```
https://agent.autoposter.ai/mcp
```

Clients that read an `mcp.json`:

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

Create an API key in [Settings → AI agents](https://app.autoposter.ai/settings/ai-agents). Claude CLI:

```bash
claude mcp add --transport http autoposter https://agent.autoposter.ai/mcp --header "Authorization: Bearer YOUR_AUTOPOSTER_API_KEY"
```

## Try it

- "Schedule a launch post for LinkedIn and X tomorrow at 10:00 America/New_York."
- "Turn this article into a thread for X and a post for LinkedIn: https://..."
- "Announce the latest release from the git log."
- "Upload this video and post it as a Reel and a TikTok."
- "How did my posts do last month?"
- "What's scheduled this week?"

## Safety

- The skills draft by default and ask before publishing, editing or deleting.
- If your API key cannot publish directly, posts go to `pending_approval` and your approvers are notified.
- Edits overwrite the previous text with no undo, so the skills show old and new text first.

## Links

[Website](https://autoposter.ai) · [Agents](https://autoposter.ai/agents) · [MCP server](https://autoposter.ai/mcp) · [API](https://autoposter.ai/api) · [Pricing](https://autoposter.ai/pricing) · [Privacy](https://autoposter.ai/privacy)

## License

MIT
