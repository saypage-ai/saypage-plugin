---
name: niche-research
description: >-
  Find which Reels really work in the user's niche right now, ranked against each account's usual views rather than by raw views; name the hook, format and call to action behind each, and turn the patterns into ideas in the user's own voice. Reads accounts the user names, their Saved collection or what they paste: Saypage cannot look up other accounts. Use for requests like "what are other food creators doing that works", "study these accounts for me", "why did this Reel blow up".
---

# Niche research

Before writing more posts, look at what is landing for comparable accounts. Do this every
few weeks: patterns change slowly, and checking daily mostly finds noise.

## What Saypage can and cannot do here

Saypage only sees the user's own connected account. It has no Instagram search, no creator
lookup, and no access to other accounts' posts or numbers. **Studying other accounts calls
no Saypage tool**: it works from what the user shows you. Saypage comes in only for the
user's own baseline (step 4).

## 1. Choose what to study

Eight to twelve accounts, named by the user or suggested by you and approved:

- **Peers**: the same niche and audience, a little further along than the user.
- **Cousins**: a different niche speaking to the same people (a wine bar looking at a
  cocktail creator). New formats often show up there before they reach the user's niche.
- **Two or three large accounts**, only to see formats; their posting rhythm and tone
  depend on their size.

Stay roughly between a fifth of the user's follower count and ten times it: a giant
account's numbers say more about its audience than about the post.

Ask the user to open their **Saved** posts as well: they kept those for a reason, and it
tells you what they would like to make.

## 2. Gather, like a person would

- If this session has a browser the user is signed in to, look together; otherwise ask them
  for links, numbers or screenshots.
- **Never sign in to Instagram for the user, never ask for their password, and do not
  scrape**: about a dozen Reels per account, opened one by one. Bulk collection goes against
  Instagram's terms and can get the user's account restricted.
- For each Reel, note: the account, its followers, its **usual views** (the median over its
  last ten or twelve Reels), this Reel's views, the first spoken words and the first text
  on screen word for word, what the opening frame shows, the length, and the ask at the end.
  When the ask is "Comment KEYWORD", note what it sends: that is what the audience wants
  badly enough to type for it.

## 3. Rank by breakout ratio

**Breakout ratio = the Reel's views ÷ the account's usual views.** From five times up it is
a breakout and worth studying; between two and five it is a good day; under two it is
ordinary, whatever the raw count.

Then set the breakouts against the ordinary Reels:

1. Hook types that repeat (the types in `reel-script`), with how often.
2. What breakouts have in common: how long the hook is, whether the payoff is visible,
   movement in the opening frame, length, where the ask comes.
3. Breakouts that fit no known type: describe them yourself, they may be a format that is
   just starting.

Give the size of the sample with every finding. A pattern seen in five breakouts across
several accounts is worth acting on; one seen twice on a single account is a hint at most.

## 4. Compare with the user's own account

With Saypage connected: `list_instagram_posts` and `get_instagram_post_insights` on the
user's recent Reels give their usual views and their own breakouts (see
`performance-review`). A pattern that works in the niche and has already worked once for
the user is the first to try.

## 5. Make it the user's

Take the shape (the hook type, the structure, the length), and leave the other creator's
words, footage and personality alone. For the three strongest patterns, write a hook from
the user's own story and numbers, ready to film, and pass each to `reel-script`.

## Output

```
RESEARCH  ·  41 Reels  ·  9 accounts (4 peers, 3 cousins, 2 large)

BREAKOUTS (5x and above)
  14.2x  @account_a   "I tried the 3-ingredient bread so you don't have to"   Test        38 s
   7.8x  @account_c   [the knife going through the crust, no words]          Mid-action  12 s
  ...

WHAT COMES BACK
  The test        5 of the breakouts, 1 of the ordinary Reels
  Mid-action      4 breakouts, all under 15 s
  Keyword asks    6 of 9 breakouts send a recipe page by DM

YOUR VERSIONS
  The test   "I tried the viral cloud bread on my bakery customers."
  ...
```

This skill only reads: it never follows, likes, comments or messages anyone.
