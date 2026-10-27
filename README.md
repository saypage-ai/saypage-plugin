# Saypage

Say what you want online, and it's online. Saypage lets your assistant build web pages for
you (a link-in-bio page, a menu, a guide, a recipe page, a portfolio), host them on your own
address (`https://<your-name>.saypage.page`) and send them by Instagram DM to followers who
comment a keyword under your post. It also reads and answers your Instagram comments, reads
your insights and, only if you turn it on, publishes posts, carousels, Reels and stories.
There is no dashboard: everything happens in the conversation.

## What's in this plugin

- **The Saypage skill** (`skills/saypage/SKILL.md`): how to work with Saypage, the
  publishing workflow, comment-to-DM automations, and the Instagram tools. For pages, it has
  your assistant read Saypage's page guide from the connector, which always matches the
  checks Saypage runs today: it asks you what the page is for and the style you want, then
  builds it.
- **Instagram content skills** (`skills/*/SKILL.md`), for writing and planning what you post.
  With the connector, they work from your real posts, comments and insights, and end in a
  Saypage page, a keyword DM or a post published once you say yes. Without it, they still
  write; you post.

  | Skill | What it does |
  |---|---|
  | `reel-script` | One idea into a Reel: three hooks of different types, the script in your voice, on-screen text, a shot list |
  | `instagram-caption` | The caption: a first line that survives the "… more" cut, one ask, search words, up to five hashtags |
  | `carousel-post` | Slide-by-slide copy, 1080×1350 slides, each crop checked before posting |
  | `story-sequence` | The day's stories, frame by frame, with the right sticker and a Saypage page behind the link |
  | `content-calendar` | Your week: what to post, which format, which keyword and page behind each post |
  | `performance-review` | What really worked, ranked against your own median, with shares, saves, follows and the keyword DM funnel |
  | `niche-research` | Which Reels break out in your niche, and why, turned into ideas in your voice |
  | `profile-review` | Your name field, bio, pinned posts and highlights, and a link page that keeps the bio's promise |
  | `comment-replies` | The comments under your posts: sorted, answered in each commenter's language, spam hidden |
  | `engagement-comments` | Comments worth leaving on other accounts' posts (you post them) |
  | `dm-writing` | Your automation's DM messages and button labels, and the DMs you send by hand |
  | `repurpose-content` | One video, podcast or article into a week of posts and one page they all send |
  | `natural-voice` | A last pass on every draft so it sounds like you, not like generated text |
- **The Saypage connector** (`.mcp.json`): Saypage's remote MCP server at
  `https://api.saypage.ai/mcp`. You sign in with your Saypage account when you connect it.
- **Two manifests for the same plugin**: `.claude-plugin/plugin.json` and `.mcp.json` for
  Claude, `plugin.json` and `mcp.json` in the [Agent Plugins](https://agent-plugins.org)
  format for ChatGPT, Codex and other clients.
- **The connector's registry listing** (`server.json`): Saypage's entry in the
  [official MCP Registry](https://registry.modelcontextprotocol.io), `ai.saypage/saypage`.

The plugin runs no code on your computer and stores nothing itself.

## Use it

1. Add the plugin, then connect the Saypage connector and sign in to saypage.ai (or create
   a free account).
2. Ask your assistant to connect your Instagram professional account: your site's address
   comes from your handle, and every page is tied to it.
3. Then just ask, for example:
   - "Make me a link-in-bio page with my latest recipes and my shop."
   - "Send that page by DM to everyone who comments GUIDE under my last post."
   - "Reply to the unanswered comments on my last Reel."
   - "How did my posts do this month, and what should I post next?"
   - "Write a Reel about my 10-minute pasta, with a keyword that sends the recipe."

The assistant shows you each page in a private preview and asks before it publishes a page,
creates an automation, or posts or replies on Instagram. Publishing posts is optional and off
until you approve it on Instagram yourself; you can turn it off at any time.

## Data

When you use the connector, your assistant sends Saypage what each request needs: the pages
it writes, the images and videos you upload, automation keywords and messages, and the
replies and captions you approve. Saypage reads the connected Instagram account's posts,
comments and insights through Instagram's official API, and keeps the Instagram ID and
comment of followers who trigger an automation in order to send them the DM. Saypage does not
read your conversations. Details are in the [privacy policy](https://saypage.ai/privacy) and
the [terms](https://saypage.ai/terms).

## Documentation

Everything Saypage does, step by step: [saypage.ai/docs](https://saypage.ai/docs). Start with
[Getting started](https://saypage.ai/docs/getting-started) and
[Install the connector](https://saypage.ai/docs/install) (Claude, Claude Code, ChatGPT and other
MCP clients); the [MCP tools reference](https://saypage.ai/docs/tools) lists every tool and what
it changes.

## Support

Write to [hello@saypage.ai](mailto:hello@saypage.ai), or see
[Help](https://saypage.ai/support) and
[Troubleshooting](https://saypage.ai/docs/troubleshooting).

## License

The plugin files are under the [MIT license](LICENSE). The Saypage service is governed by its
[terms](https://saypage.ai/terms).
