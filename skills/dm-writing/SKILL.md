---
name: dm-writing
description: >-
  Write Instagram DMs: the messages and button labels of a Saypage comment-to-DM automation (opening message, link message, follow request, public reply), and the messages the user sends by hand (answering someone who wrote first, a collab or brand pitch, one follow-up). Saypage sends DMs only to people who comment a keyword and cannot read the inbox. Use for requests like "write the messages my automation sends", "help me pitch a brand", "how do I answer this person", "should I follow up?".
---

# DM writing

A DM lands in a personal inbox, next to messages from friends. It is welcome when the
person asked for it (they commented the keyword, replied to a story, asked a question)
and it delivers what they asked for, straight away. It is unwelcome in almost every other
case.

## What Saypage can do here

Saypage sends DMs only through **keyword automations**: someone comments the keyword under
a post and gets the automation's messages. It cannot read or summarise the inbox, send a
one-off message, or write to people who did not comment. When the user asks to read their
DMs or to message followers in bulk, say so and call no Saypage tool for that: offer to
help with messages they paste, or a keyword automation instead.

## 1. Automation messages (Saypage)

Instagram requires two steps: an opening message with a button, then the link.

- `opening_message`: thank them for the comment, say what is coming, ask for the tap.
  "Here's the croissant recipe you asked for 🥐 Tap below and I'll send you the link."
- `opening_button_label`: what the tap gets them. "Send me the recipe".
- `link_message`: deliver at once, a tip for using it, and optionally one easy
  question. "Here it is! The dough needs a night in the fridge, so start it tonight. Which
  filling are you trying first?"
- `link_button_label`: "Open the recipe".
- `extra_link_buttons` (up to 2 more): the shop, the booking page, the YouTube channel,
  only when the follower would want them.
- With `follow_gate: true`, `follow_request_message` and `follow_request_button_label`: say
  plainly that the link is for followers, without guilt. "This one's for my followers:
  follow @maisonlune.lyon, then tap below and it's yours." / "I'm following". A follow gate
  wins follows and loses some of the people who wanted the link: say so to the user.
- `public_reply` (optional): the short public answer under the comment ("Sent you a DM!").

Rules for all of them:

- **Button labels: 20 characters at most.** Count them.
- **Every message in the user's language**, including the follow-gate ones when the gate is
  on: the defaults are English, and a DM that switches language looks broken.
- **The link comes with the second message, no strings attached.** Asking for something in
  return first (their email, their story) makes a free offer feel like a trap.
- **Let the user choose the words.** These DMs speak in their name: offer two tones (warm,
  short) or let them write their own, and show the final texts before `create_automation`
  or `update_automation`, as the `saypage` skill describes.

To see where people stop (opening DM not tapped, follow request ignored),
`get_automation_activity` on the automation; rewrite the step that loses them.

## 2. Messages the user sends by hand

For these, Saypage only helps write; the user sends them from the app.

- **Answering someone who wrote first** (a story reply, a question): answer what they
  asked, in two to four sentences, then one small question or next step.
- **A collab or brand pitch**: open with the collaboration itself (a joint Reel, a giveaway,
  a dish made with their product), say why it suits both audiences, with a number when
  the user has one (followers in their city, a past result), and close with a simple
  question they can answer yes or no. Keep a media kit or a link for when they reply.
- **A follow-up**: once, a week or so later, and only to bring something they did not have
  (a date, a sample, a result). Then let it go.
- **Cold messages to strangers** rarely get answers, and many sent in a row get accounts
  restricted. Suggest commenting on their posts for a couple of weeks first
  (`engagement-comments`). Never automate outreach.

Everything in a pitch must be true: no made-up mutual friends, earlier chats or results.

## Output

Each message ready to copy, with its character count, labels with their length:

```
opening_message       "Here's the croissant recipe you asked for 🥐 Tap below..."   (81)
opening_button_label  "Send me the recipe"                                           (18/20)
link_message          "Here it is! The dough needs a night in the fridge..."         (107)
link_button_label     "Open the recipe"                                              (15/20)
```

Run every message through `natural-voice` before showing it.
