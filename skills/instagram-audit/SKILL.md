---
name: instagram-audit
description: Audit the user's Instagram account with their real numbers. Use when the user asks for an Instagram audit or review, asks how their account or content is doing, which posts or reels work best and why, why their reach dropped, or what they should post next.
---

# Instagram audit

An audit built only from the account's own numbers, compared with the account's own normal. Never invent a number: if a tool returns nothing or null, say what is missing.

## Collect

Call these, in parallel where you can:

1. `ig_account_stats` with `days: 30`: reach, views, engagement, profile visits and follower count.
2. `ig_follower_growth` with `days: 30`: net growth and the days it spiked or dropped.
3. `ig_posts` with `buzzfy_trial_reels: "exclude"` and `limit: 20`: the creator's own recent posts and reels.
4. `ig_post_stats` for up to 20 of those ids, with `compare_to_median: true`. `vs_median_x` is each number as a multiple of the account's normal (1.5 = 50% above).
5. `ig_reel_checkup` with no ids: the playbook scorecard for recent reels, hot streaks and past hits worth remaking.
6. `ig_best_times` with the user's IANA time zone. Ask for it if you can't tell it from the conversation.
7. `ig_audience`. Instagram only returns demographics for accounts with 100 or more followers; if it doesn't, say so in one line and move on.

## Write the audit

Keep it to one screen, in this order:

1. **The headline.** Two or three sentences on how the last 30 days went: reach, views and followers, with the numbers.
2. **What worked.** The top three posts or reels by `vs_median_x` on views, shares and saves. For each, say what it had in common with the others (format, opening, topic, length) based on what the tools return.
3. **What didn't.** The weakest two, and the checkup's fix-it step for each (1 the opening, 2 the payoff, 5 the caption).
4. **When to post.** The best two or three slots from `ig_best_times`, in the user's time zone, and which data they rest on.
5. **Next 30 days.** Three concrete actions. If the checkup reports a hot streak, the first action is to follow it up within 48 hours. If it lists past hits, suggest remaking one.

When you need the reasoning behind a recommendation, call `buzzfy_playbook` (`overview`, `openings`, `shares_and_saves` or `checklists`) and cite the rule in plain words.

## When there isn't much data

With fewer than five posts, say the comparisons are thin and focus on the next five posts instead. Instagram's data lags up to 48 hours, so leave the newest posts out of any ranking and mention it.

If a tool refuses because Instagram isn't connected, use the `get-started` skill.
