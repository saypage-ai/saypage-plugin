---
name: performance-review
description: >-
  Review what the user already posted on Instagram: which posts broke out against the account's own median, which earned shares, saves and follows, plus keyword DM delivery activity and page visits, from Saypage's post and account insights, page stats and automation activity; then say what to keep, stop and try next. Use for requests like "which of my posts did best", "look at my stats", "my last Reels flopped, why", "what should I do more of".
---

# Performance review

Best practices are averages over other people's accounts. This skill looks at the user's
own posts and numbers to see which of those practices hold for them, and where their
audience behaves differently.

## 1. Collect the numbers

With Saypage connected (`get_account` first; insights need `can_read_insights`):

- `list_instagram_posts`, following `next_cursor` until you have about 30 posts or 60 days.
  Leave stories out: they are listed only while live, and their insights end with them.
- `get_instagram_post_insights` for each post: reach, views, likes, comments, shares,
  saves, profile visits, new followers, and average watch time for Reels.
- `get_instagram_insights` over 30 days for the account as a whole.
- `get_page_stats` over 30 days: visits per page and channel.
- For posts with a keyword: `list_automations` (`links_sent`) and
  `get_automation_activity` (where people stopped). Their totals cover the last 13 months
  of retained activity, including history from earlier posts if the automation moved;
  label that window separately from the 30-day page stats.

Without Saypage, ask for screenshots of the insights of the user's last posts.

**State only numbers that a response returned.** When a metric is in `unavailable`, pass on
its reason (fewer than 100 followers, still processing, expired story) instead of a zero or
an estimate. The API has no retention graph and no follower/non-follower split: the user
can screenshot those from the app if they want them in the review.

## 2. Compute ratios, not totals

A big view count can simply mean a big following. Work out these, showing how:

| Measure | How | Tells you |
|---|---|---|
| **Breakout ratio** | views ÷ the median views of the account's posts of the same format | a real hit or an ordinary day |
| **Shares per 1,000 reach** | shares ÷ reach × 1,000 | worth sending to a friend: the strongest signal |
| **Saves per 1,000 reach** | saves ÷ reach × 1,000 | useful enough to keep |
| **Follows per 1,000 reach** | new followers ÷ reach × 1,000 | whether the post (and the profile behind it) converts |
| **Average watch time** | from Reel insights | compare with the Reel's length, if the user knows it |
| **DM delivery progression** | `triggered` → `first_dm_sent` → `tapped` → `links_sent` within one automation's activity summary | where its DM sequences stop, over the retained activity window |

Report page views from `instagram_dm` separately, with their page and 30-day window.
They combine visits from every automation sending that page and count page loads, not
distinct recipients. Do not divide them by `links_sent`, attribute them to one post, or
claim a comment-to-page conversion rate from these responses. An end-to-end funnel needs
matching dates and attribution to the same recipients, which these tools do not provide.

Order the posts by breakout ratio first and shares second. Keep formats apart: Reels
against Reels, carousels against carousels.

## 3. Find the pattern

Split the posts into a top third and a bottom third and list what differs: subject, hook
type (see `reel-script`), format, length, a face or hands in the opening frame, the ask,
how fast the user answered comments. Posting day and hour come at the end of the list,
since they seldom explain much.

Attach the evidence and a confidence level to each finding. Under about fifteen posts,
present patterns as hunches to test, not conclusions.

## 4. Diagnose before advising

- **Low reach**: the hook and the opening frame (`reel-script`).
- **Good reach, few new followers**: visitors reach the profile and leave; look at the bio
  and its link (`profile-review`).
- **Good reach, few shares or saves**: people watch but do not find it useful or personal
  enough to keep or pass on.
- **DM delivery drop-off**: use the stages and failure reasons within
  `get_automation_activity` to distinguish an opening DM not tapped, a follow request
  ignored or a delivery failure; rewrite the relevant message with `dm-writing`.
- **Page visits**: report their trend separately. These tools cannot connect a visit to
  a particular DM delivery or count bookings. If the user supplies comparable booking or
  conversion data, use it before diagnosing the page (the `saypage` skill).
- **DMs missing**: check `plan.dms_this_month` against `plan.limits.monthly_dm_limit` in
  `get_account` first.

## Output

```
REVIEW  ·  28 posts  ·  1 Sep - 25 Oct  ·  median views: Reels 3,900, carousels 1,700

TOP BY BREAKOUT RATIO
  9.1x  Reel      "I salted pasta water wrong..."  35,600 views  41 shares/1k  12 follows/1k
  4.3x  Carousel  5 weeknight sauces               7,300 views   58 saves/1k
  ...

BOTTOM
  0.3x  Reel      new menu announcement            1,200 views   2 shares/1k
  ...

WHAT THE NUMBERS SAY
1. Mistake-and-fix Reels: 4 of the top 5, none in the bottom 5 (fairly sure, n=9).
2. Announcements get reach but no shares: move them to stories.
3. Automation GUIDE: 212 triggered, 188 links sent (retained activity, up to 13 months).
   Guide page: 131 page views from DMs in the last 30 days, across all its automations.
   These totals do not establish a post's page conversion rate.

KEEP   mistake-and-fix Reels, recipe carousels
STOP   menu announcements as Reels
TRY    a carousel version of the top Reel, with a keyword for the full recipe
```

Then offer to build next week on it (`content-calendar`).
