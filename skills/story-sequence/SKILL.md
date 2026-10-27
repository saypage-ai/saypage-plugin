---
name: story-sequence
description: >-
  Plan the day's Instagram Stories: three to six frames, what each shows and says, the right sticker for each purpose, and how replies become conversations, with Saypage pages behind the link stickers and plain photo or video stories published through Saypage when the user asks. Use for requests like "ideas for today's stories", "a poll for my followers", "announce my event in stories", "sell without a feed post".
---

# Story sequence

Stories rarely reach new people: they reach followers, for a day. Use them to make those
followers feel they know the person or the place, and to give them an easy reason to
reply, visit or buy.

## 1. A day in a few frames

Three to six frames. Viewers drop off with each tap, so put the question around the
middle, while most of them are still watching.

```
1   TODAY     what is happening right now, filmed: the oven, the market, the desk
2-3 INSIDE    how it is made, what came out, a detail, a price, a customer's reaction
4   QUESTION  a single sticker
5   NEXT      the result, the answer, or a reason to come back tomorrow
```

## 2. Which sticker for which job

| Sticker | Good for | Tip |
|---|---|---|
| Poll | lots of taps with no effort | two short choices that are both fun to pick |
| Quiz | teaching something | ask about what most people get wrong |
| Question box | hearing what people want, as they say it | keep the answers: they are tomorrow's posts and hooks |
| Emoji slider | a light mood check | for fun, not for decisions |
| Link | sending people somewhere | to a Saypage page: menu, recipe, booking, guide |
| Countdown | a launch, a drop, a live | followers can turn on a reminder |
| Add Yours | a prompt others answer with their own story | choose a prompt any follower could answer |

The next day, share a few answers to the question box or the quiz result: it rewards the
people who took part and fills a frame.

## 3. Rules

- **Open on something real**: a face, hands, a place, food. A plain background with text
  is what people tap past.
- **A few words per frame**, and if there is speech, say the same thing out loud.
- **Text away from the edges**: on a 1080×1920 frame the account name sits in the top 250 px
  or so and the reply bar in the bottom 250 px.
- **Speak to one viewer**, as in a message to a friend.
- **Sharing a post to stories?** Add a line on why it is worth opening (a reaction, a
  question from the comments), not just the post.
- **Selling here** works well: show the context first, then the offer, then someone who
  liked it. A sales frame in stories does not cost the feed anything.

## 4. Replies are conversations

Story replies land in the user's DMs. Saypage cannot read or answer the inbox, and its
automations are triggered by **comments on posts**, never by story replies, so the user
answers these by hand. They are often the warmest messages the account receives.

To send something automatically, have the story point to a post with a keyword ("Comment
GUIDE under my latest Reel and I'll send it to you") that has an automation (see the
`saypage` skill), or put a link sticker straight to the page.

## 5. With Saypage

- **Link stickers to Saypage pages**: the visits appear in `get_page_stats` under
  `instagram_bio`, because Instagram's link redirect looks the same for a story link and the
  bio link.
- **Publishing a story**: the Instagram API publishes stories without any sticker, so frames
  with a poll, a link or a question box are posted from the app. A plain image or video
  frame can go through Saypage when the user asks and `can_publish_posts` is on:
  `prepare_instagram_post` with `kind: "story"` (one image) followed by
  `publish_instagram_post`, or `publish_instagram_video` with `kind: "story"` (60 seconds
  or less). Each frame is a separate story: publish them in order, and ask first.
- **Results**: `get_instagram_post_insights` gives a story's replies and navigation, only
  for the 24 hours it is live.

## Output

```
STORIES  ·  Thursday  ·  5 frames

1  [hands, flour, morning light]   "First batch of the new sourdough."
2  [close-up of the crumb]         "48-hour ferment. That's where the holes come from."
3  [price card]                    "€6.50, from Saturday."
4  [poll]                          "Would you pre-order one?"  Yes, save me one / Just looking
5  [link sticker -> menu page]     "Full menu and opening hours here."

After: message the people who voted Yes. Tomorrow: share the poll result.
```
