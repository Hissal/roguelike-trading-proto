# Prototype quarterly reports and the news feed

Status: resolved
Type: prototype
Blocked by: 02, 04

## Question

What do a company's quarterly report and a general news feed item look like on screen, and how does each feed the market (reports: real value and the perceived-value snap; news: perception, several companies at once)? Does the split read clearly and replace the "on tick X this jolts up or down" news?

Also try **developing stories**: news that sets up the future instead of
reporting a one-off good or bad thing. For example, "X is going on, we'll find
out in a few days", or a game studio starting a game, then announcing what it
is and when it releases, then reviews, launch and early sales. Does a story
told over several days give better decisions than single items?

Constraint from the market-motion sandbox: "buy good news, sell bad news" must
not be the optimal play, even if it usually works.

## Answer

Prototype: branch `prototype/reports-and-news`, file
`reports-news-prototype.html` (two versions in two commits; the pure
`MarketModel` script block is the part worth lifting).

**Verdict (creator, after play): reports, one-off news and developing stories
together give the news far more flavour than "on tick X this jolts". Reports
must not show the exact real value.** Hiding it makes the player actually read
and analyse the other fields. Tuning is deliberately left for later, because
the gameplay around it may change a lot.

What the prototype settled:

- **Quarterly report card**: Result (BIG BEAT, BEAT, MET, MISSED or BIG MISS,
  graded by how far the price was off), Revenue (the past: growth since the
  last report), Profit (the present: health now) and Outlook (the future:
  Raised, Held or Cut, which sets which way real value drifts until the next
  report), plus a one-line quote. No revealed worth; the price's reaction over
  the following days tells the rest. Revealing the exact worth is a candidate
  card effect.
- **News card**: headline plus one ▲/▼ chip per company it affects; one item
  can move several companies.
- **Theoretical vs concrete news** (the creator's framing, replacing
  mood/fundamental): theoretical news is talk, forecasts and possibility, moves
  perceived value only and fades; concrete news is something that happened,
  changes real value and shows in the next report. The kind is not labelled;
  the wording gives it away, and a card could reveal it outright.
- **Developing stories are expected news**: a known decision date, three
  endings (good, neutral, bad) weighted by the company's outlook and shifted
  by hints, and a jolt on the day set by the gap between what investors had
  priced in and what the ending delivers (hyped then bad: a crash; hyped then
  great: flat; feared then neutral: a jump). That makes them an educated
  gamble rather than a coin flip, and gives them a reason to exist beside
  surprise news.

Creator feedback that shapes later work:

- **Reading news is draining.** A steady flood of items to read and analyse
  will make players quit. News should be read rarely compared with the core
  loop, e.g. between rounds and traded on within them. Recorded in the map's
  Notes and on
  [Prototype how a month breaks into play](07-time-structure.md).

Agent observations for later tuning (not decisions; from the prototype's
rule-based strategy check, 300 simulated months, 3-day holds):

- With the market-motion model as validated, "buy good news, sell bad news"
  won 83–95% of trades. Pricing part of a theoretical item in on arrival
  (25%) brought following all news to about 60%, theoretical-only to break-even
  and concrete-only to about 70%: reading the kind becomes the edge.
- Following the reports (buy beats, short misses) still wins about 80–84%;
  the validated 40% snap plus predictable drift causes it. A 70% snap gives 64%.
- The outlook needed the market to price in part of the expected growth on
  report day, or following it won 80–90%.
- Betting on a story ending by its odds loses slightly (already priced in);
  betting against a crowd that over- or under-priced it wins most per trade.
