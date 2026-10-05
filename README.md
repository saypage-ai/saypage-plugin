# SayPage

Say what you want online, and it's online. SayPage lets your assistant build web pages for
you (a link-in-bio page, a menu, a guide, a recipe page, a portfolio), host them on your own
address (`https://<your-name>.saypage.page`) and send them by Instagram DM to followers who
comment a keyword under your post. It also reads and answers your Instagram comments, reads
your insights and, only if you turn it on, publishes posts, carousels, Reels and stories.
There is no dashboard: everything happens in the conversation.

## What's in this plugin

- **The SayPage skill** (`skills/saypage/SKILL.md`): how to work with SayPage, the
  publishing workflow, comment-to-DM automations, and the Instagram tools. For pages, it has
  your assistant read SayPage's page guide from the connector, which always matches the
  checks SayPage runs today: it asks you what the page is for and the style you want, then
  builds it.
- **The SayPage connector** (`.mcp.json`): SayPage's remote MCP server at
  `https://api.saypage.ai/mcp`. You sign in with your SayPage account when you connect it.
- **Two manifests for the same plugin**: `.claude-plugin/plugin.json` and `.mcp.json` for
  Claude, `plugin.json` and `mcp.json` in the [Agent Plugins](https://agent-plugins.org)
  format for ChatGPT, Codex and other clients.

The plugin runs no code on your computer and stores nothing itself.

## Use it

1. Add the plugin, then connect the SayPage connector and sign in to saypage.ai (or create
   a free account).
2. Ask your assistant to connect your Instagram professional account: your site's address
   comes from your handle, and every page is tied to it.
3. Then just ask, for example:
   - "Make me a link-in-bio page with my latest recipes and my shop."
   - "Send that page by DM to everyone who comments GUIDE under my last post."
   - "Reply to the unanswered comments on my last Reel."
   - "How did my posts do this month, and what should I post next?"

The assistant shows you each page in a private preview and asks before it publishes a page,
creates an automation, or posts or replies on Instagram. Publishing posts is optional and off
until you approve it on Instagram yourself; you can turn it off at any time.

## Data

When you use the connector, your assistant sends SayPage what each request needs: the pages
it writes, the images and videos you upload, automation keywords and messages, and the
replies and captions you approve. SayPage reads the connected Instagram account's posts,
comments and insights through Instagram's official API, and keeps the Instagram ID and
comment of followers who trigger an automation in order to send them the DM. SayPage does not
read your conversations. Details are in the [privacy policy](https://saypage.ai/privacy) and
the [terms](https://saypage.ai/terms).

## Support

Write to [hello@saypage.ai](mailto:hello@saypage.ai). Setup guide:
[saypage.ai/start](https://saypage.ai/start).

## License

The plugin files are under the [MIT license](LICENSE). The SayPage service is governed by its
[terms](https://saypage.ai/terms).
