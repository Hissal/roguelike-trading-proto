# Prototype the market-motion sandbox

Status: resolved
Type: prototype
Blocked by: 01

## Question

Without cards, does a market where real value drifts with company health and price wobbles randomly around a target read well and feel alive? Compare, via a toggle, price targeting real value directly versus targeting a perceived value distorted by news and momentum that reports snap back. Which is more readable and more fun to trade by eye?

## Answer

Prototype: branch `prototype/market-motion`, file
`market-motion-prototype.html` (one self-contained page; the pure
`MarketModel` script block is the part worth lifting).

**Verdict (creator, after play): B, price follows perceived value.** It is
the more interesting of the two. The wavy motion is clearly better than the
card-design prototype's market. Mode A (price follows real value, only
genuine news matters) reads honestly but gives little to trade.

The validated model, from
[Research price-motion models](01-price-motion-models.md):

- Real value drifts with a slow health process; genuine news nudges health
  and gives a small jump.
- Perceived value = real value × exp(fad), with the fad a damped oscillator
  (momentum φ 0.6, pull κ 0.25); every news item kicks its velocity, so a
  rumour runs up for 2–4 days, overshoots and settles.
- A report closes 40% of the price-to-real gap on the day and the rest over
  about four days.

Feedback that shapes later tickets:

- **Missing trends.** The motion is a little too random. Real stocks trend:
  within an uptrend they wave with higher highs and higher lows, a trend
  breaks when that pattern fails, and a neutral range follows before the next
  trend. The prototype only hints at this. Follow-up:
  [Prototype trends in the market](09-market-trends.md).
- **Chart intervals.** Viewing different intervals (e.g. 4-hour vs daily)
  could give different information. Depends on how time is split; left in the
  map's fog.
- **Snap and drift hands out trades.** "Buy good news, sell bad news" nearly
  always works. That is acceptable as a baseline, but it must not be the
  optimal play; a balancing concern that cards may partly solve. Recorded in
  the map's Notes and on
  [Prototype quarterly reports and the news feed](06-reports-and-news-format.md).
- **Developing stories.** News that sets up the future ("X is going on, we'll
  find out in a few days"; a game studio announces a game, then its release
  date, reviews, launch and sales) could be more interesting than one-off
  good/bad items. Folded into
  [Prototype quarterly reports and the news feed](06-reports-and-news-format.md).
