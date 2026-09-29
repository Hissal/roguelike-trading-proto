# Quarterly reports and market news

Research for splitting in-game news into two channels: a **quarterly report**
per company, which reveals **real value**, and a **general news feed**, which
moves **perceived value** (see `CONTEXT.md`). Today's events work differently:
each one is a single company-specific item that carries both a value change and
a price jolt on a known tick.

Sources are SEC and investor-education material plus peer-reviewed finance and
accounting papers. Where a claim rests on an abstract rather than the full
paper, it says so. The game recommendations in sections 4–6 are design
suggestions, not findings from the sources.

## 1. What a real quarterly report communicates

### The filing and the earnings release

- **Form 10-Q** is the quarterly report US public companies file for their
  first three fiscal quarters (the fourth quarter is covered by the annual
  10-K). It contains *unaudited* financial statements for the quarter and the
  year to date, and compares them with the same periods a year earlier. Its
  sections include Financial Statements, Management's Discussion and Analysis
  (MD&A), market-risk disclosures, controls, legal proceedings and risk
  factors. ([Investor.gov, Form 10-Q][ig-10q];
  [Investor.gov, How to Read a 10-K/10-Q][ig-read])
- **MD&A** is management explaining the numbers in its own words. SEC
  Regulation S-K Item 303 requires it to "describe any known trends or
  uncertainties" that are reasonably likely to materially affect revenue or
  income. For interim (quarterly) periods it must explain material changes
  since the prior year's comparable period. ([17 CFR 229.303][s-k-303])
- The market usually learns the headline numbers first from an **earnings
  press release**, which is furnished to the SEC on **Form 8-K, Item 2.02**
  ("Results of Operations and Financial Condition"). If the release uses
  non-GAAP ("adjusted") figures, it has to follow Regulation G rules.
  ([SEC, Form 8-K C&DIs][sec-8k])

### Headline figures

A typical release leads with these figures:

| Figure | Meaning |
|---|---|
| **Revenue** (sales) | Money the business took in during the quarter |
| **Earnings per share (EPS)** | Net income divided by shares outstanding: profit per share |
| **Year-over-year change** | This quarter compared with the same quarter last year, the comparison the 10-Q is built around ([Investor.gov][ig-10q]) |
| **Guidance** (optional) | Management's forecast for coming quarters or the year |

Revenue and earnings surprises each carry information. A revenue surprise
still predicts returns after controlling for the earnings surprise.
([Jegadeesh & Livnat 2006][jl06])

### Expectations: beat or miss

The market reacts less to the reported number than to how far it lands from
**what was expected**. The expectation is usually analysts' consensus
forecast. Being publicly visible, that consensus becomes the standard the
figures are judged against:

- Firms that **meet or beat** consensus earn higher returns over the quarter
  than firms with similar forecast errors that just miss. This premium holds,
  in somewhat smaller form, even when the beat was probably engineered, and it
  predicts future performance. ([Bartov, Givoly & Hayn 2002][bgh02])
- The reaction is **asymmetric** for richly priced "growth" stocks. A negative
  surprise draws a much larger price drop than an equal positive surprise
  draws a rise (the "earnings torpedo"). ([Skinner & Sloan 2002][ss02])
- Much of a report's content is **anticipated before it is released**. Ball &
  Brown (1968) found that prices drift toward the eventual result in the months
  before the annual report. ([Ball & Brown retrospective, SSRN][bb68];
  [Gow, *Empirical Research in Accounting*, ch. 11][bb68-gow])

### Guidance and management commentary

- **Guidance** is management's own forward-looking forecast. Under Regulation
  FD, a company that gives material guidance must give it to everyone at once,
  not privately to analysts. The SEC specifically names earnings guidance given
  to analysts as a high-risk case. ([SEC, Selective Disclosure and Insider
  Trading, 2000][sec-fd]) Forward-looking statements have a litigation safe
  harbor under the PSLRA, which is why releases carry "forward-looking
  statements" disclaimers. ([SEC, Safe Harbor for Forward-Looking
  Statements][sec-safe])
- Downward guidance in particular is linked to later earnings news, and there
  is modest evidence that it moves prices, most of all near quarter-end when
  pre-announcements cluster. ([Anilowski, Feng & Skinner 2007][afs07])

## 2. How general market or world news differs

| | Quarterly report | General news |
|---|---|---|
| Source | The company itself, under SEC filing rules | Press, forecasters, governments, other firms |
| Timing | Scheduled and predictable (every quarter) | Unscheduled or continuous |
| Scope | One company | Often a whole sector, region or the market; sometimes names firms |
| Content | Realised results, measured against expectations | Forecasts, events, commentary and tone |
| Effect on fundamentals | Reveals them (what already happened) | May change future fundamentals, or may only change mood |

Findings on how prices treat news:

- **Tone without new facts** moves prices briefly. High pessimism in a daily
  *Wall Street Journal* market column predicted falling prices followed by a
  **reversion to fundamentals**. That fits the column acting as noise or
  sentiment, not as new information. ([Tetlock 2007][tet07])
- **News with substance** is absorbed slowly. Stocks that fell alongside public
  headlines kept drifting down, especially after bad news. Stocks that made
  large moves *with no identifiable news* tended to **reverse**. Both effects
  were strongest in small, illiquid stocks. ([Chan 2003][chan03])
- **Mood can move whole markets.** Morning sunshine in the city of a country's
  main exchange correlated with that day's index returns across 26 countries.
  The effect was too small to trade after costs, and it is hard to square with
  fully rational pricing. ([Hirshleifer & Shumway 2003][hs03])
- **Weather does change real demand in some sectors.** US natural-gas use peaks
  in the winter heating season and rises with heating degree days. Residential
  and commercial demand are the most weather-sensitive. ([EIA,
  Degree-days][eia-dd]; [EIA STEO supplement, weather sensitivity in natural
  gas][eia-steo]) So "long winter" news is both a mood shift and a plausible
  fundamental shift for utilities.
- **News spreads slowly across related firms.** Industry information diffuses
  slowly: big firms lead small firms in the same industry, mostly on bad news.
  ([Hou 2007][hou07]) News about a firm's major customer predicts its
  supplier's later returns. ([Cohen & Frazzini 2008][cf08]) Industry momentum
  explains much of individual-stock momentum. ([Moskowitz & Grinblatt
  1999][mg99])
- **Overreaction over long horizons.** Stocks that were extreme losers over
  several years later beat prior winners, which fits investors overreacting to
  dramatic news. ([De Bondt & Thaler 1985][dbt85])

## 3. Signals a non-expert can read at a glance, and how prices react

| Signal | Plain-language reading | Typical real reaction | Source |
|---|---|---|---|
| **Beat / miss vs expectations** | "Did they do better or worse than people thought?" | Immediate move in the surprise's direction; meeting the bar earns a premium | [BGH 2002][bgh02] |
| **Surprise size** | "By a little or a lot?" | Bigger surprise, bigger move; bad surprises on hyped stocks hit harder | [Skinner & Sloan 2002][ss02] |
| **Post-earnings drift** | "The move keeps going for a while" | Prices keep drifting in the surprise's direction after the announcement; part of the drift shows up at the *next* quarters' announcements | [Bernard & Thomas 1989][bt89]; [Bernard & Thomas 1990][bt90] |
| **Guidance up / down** | "What does the boss expect next?" | Downward guidance is the more informative kind and moves prices modestly | [AFS 2007][afs07] |
| **Mood headline, no facts** | "Everyone's gloomy" | Short dip, then reversion toward fundamentals | [Tetlock 2007][tet07]; [Chan 2003][chan03] |
| **Sector-wide event** | "Bad for shipping, good for utilities" | Moves a group together; smaller or less-followed firms catch up late | [Hou 2007][hou07]; [MG 1999][mg99] |
| **Busy news day** | "Lots going on at once" | Weaker immediate reaction to each report, **more** drift afterwards | [Hirshleifer, Lim & Teoh 2009][hlt09] |

Bernard & Thomas (1989) confirmed Ball & Brown's observation that
"good news" firms keep drifting up and "bad news" firms keep drifting down after
the announcement. They attribute the drift to a delayed price response, not a
risk premium. The 1990 follow-up showed that the three-day reactions to the
next four quarterly announcements are predictable from this quarter's earnings.
(Both findings are taken from the paper abstracts.)

## 4. Mapping to the game's vocabulary (design suggestion)

The research supports a clean split:

- **Quarterly report → real value is revealed.** The report moves real value
  (or reveals where it already moved). The price then reacts to the *gap
  between the result and expectations*: an immediate jolt plus a smaller drift
  in the same direction over the next few ticks. That is the existing
  "correction toward real value" market force.
- **News → perceived value moves.** Mood news pushes perceived value, and it
  decays back toward real value if no report confirms it (Tetlock, Chan).
  Substantive news (such as weather that changes demand) *also* nudges the
  **next** report's real value. The player gets a leading hint whether a mood
  swing will stick.
- **One news item, many companies, different signs.** Each item carries
  per-sector (or per-company) impacts. Smaller or niche companies react later
  (Hou; Cohen & Frazzini), which gives the player a readable edge.
- **Expectations are the hook.** Showing an *expected* figure before the
  report lets the player bet on beat or miss. Hype can raise the bar, and
  hyped companies take asymmetric damage on a miss (Skinner & Sloan).

## 5. Format (a): quarterly report card

Keep each card to five fields, readable in two seconds:

```
[Company] · Q[n] report
Result:    BEAT / MET / MISSED   (vs expected)
Revenue:   ▲ / ▼ / ▬  vs last year
Profit:    ▲ / ▼ / ▬  vs last year
Outlook:   Raised / Held / Cut
Boss says: "<one line of management commentary>"
```

Suggested mechanics: *Result* sets the size and sign of the immediate jolt
relative to expectations. *Revenue* and *Profit* together set how far real
value moves. *Outlook* adds a small drift over the following ticks, with Cut
weighted more heavily than Raised. The quote is flavour that can hint at the
next quarter.

**Example 1: clean beat**
```
Lumen Power · Q2 report
Result:    BEAT (big)
Revenue:   ▲  vs last year
Profit:    ▲  vs last year
Outlook:   Raised
Boss says: "Cold snap demand exceeded our plan; tariff review on track."
```
Big jolt up, real value up, and a few ticks of upward drift.

**Example 2: good numbers, bad outlook**
```
Harbor Lines · Q3 report
Result:    MET
Revenue:   ▲  vs last year
Profit:    ▬  vs last year
Outlook:   Cut
Boss says: "Fuel costs will weigh on the winter season."
```
Little jolt on the result, but the outlook cut adds downward drift. The lesson
for the player: the forecast can matter more than the result.

**Example 3: hype torpedo**
```
Forge Works · Q1 report   (hyped: expectations high)
Result:    MISSED (small)
Revenue:   ▲  vs last year
Profit:    ▼  vs last year
Outlook:   Held
Boss says: "Maintenance stop was contained; normal output resumes next quarter."
```
The miss is small, but the company was hyped, so the jolt down is large (the
asymmetry). Real value barely moves, so the price is likely to recover through
correction.

## 6. Format (b): news item

```
[Category icon] Headline (one line)
Affects:   ▲ Sector/Company A   ▼ Sector/Company B   ▲ ...
Kind:      Mood (fades) / Fundamental (shows up in next report)
Lasts:     N ticks
```

Suggested mechanics: each *Affects* entry pushes perceived value for that
sector or company. *Mood* items decay back toward real value. *Fundamental*
items also nudge real value, which is revealed at the next report. Companies
the news names directly move at once; smaller or niche companies in the same
sector react one tick later (the lead-lag effect). Hiding *Kind*, or revealing
it only through a card, is a natural lever for information cards such as the
existing Insider trade.

**Example 1: weather, multiple sectors (the designer's example)**
```
❄ Forecasters warn of a very long winter
Affects:   ▲ Utilities   ▼ Shipping   ▲ Ski resorts
Kind:      Fundamental
Lasts:     6 ticks
```
Perceived value shifts at once in both directions. Real demand also shifts
(EIA heating-degree-day data backs this for utilities), so the next reports
tend to confirm it.

**Example 2: mood only**
```
📰 Market column: "Investors brace for a rough quarter"
Affects:   ▼ All companies (small)
Kind:      Mood
Lasts:     3 ticks
```
A broad, shallow dip that reverts (Tetlock 2007). It is a buying opportunity
for a player who trusts real value.

**Example 3: named company, spill-over**
```
⚓ Harbor Lines wins exclusive port contract
Affects:   ▲ Harbor Lines   ▲ Forge Works (supplier, 1 tick later)   ▼ rival shippers
Kind:      Fundamental
Lasts:     4 ticks
```
A direct hit on the named firm, with a delayed move for its supplier (Cohen &
Frazzini 2008). The delay rewards players who read the links.

## 7. Caveats

- Most of these effects are statistical averages over thousands of US stocks,
  and some are small or weaker in recent decades. The game should exaggerate
  them for readability, not treat them as exact magnitudes.
- Several findings (Chan 2003, Hou 2007) are concentrated in small, illiquid
  or neglected firms. A game could use company "size" or "attention" as the
  dial for how slowly news is absorbed.
- Claims about Ball & Brown and Bernard & Thomas come from abstracts and a
  retrospective or textbook chapter, not a full reading of the originals.
- The investor.gov pages returned HTTP 403 during research, so the claims
  cited to them rest on search-result snippets of those pages.

[ig-10q]: https://www.investor.gov/introduction-investing/investing-basics/glossary/form-10-q
[ig-read]: https://www.investor.gov/introduction-investing/general-resources/news-alerts/alerts-bulletins/investor-bulletins/how-read
[s-k-303]: https://www.law.cornell.edu/cfr/text/17/229.303
[sec-8k]: https://www.sec.gov/rules-regulations/staff-guidance/compliance-disclosure-interpretations/exchange-act-form-8-k
[sec-fd]: https://www.sec.gov/rules-regulations/2000/08/selective-disclosure-insider-trading
[sec-safe]: https://www.sec.gov/rules/1994/10/safe-harbor-forward-looking-statements
[jl06]: https://pages.stern.nyu.edu/~jlivnat/JAE%20submission.pdf
[bgh02]: https://econpapers.repec.org/RePEc:eee:jaecon:v:33:y:2002:i:2:p:173-204
[ss02]: https://link.springer.com/article/10.1023/A:1020294523516
[bb68]: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2304409
[bb68-gow]: https://iangow.github.io/far_book/bb68.html
[afs07]: https://ideas.repec.org/a/eee/jaecon/v44y2007i1-2p36-63.html
[tet07]: https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1540-6261.2007.01232.x
[chan03]: https://ideas.repec.org/a/eee/jfinec/v70y2003i2p223-260.html
[hs03]: https://onlinelibrary.wiley.com/doi/abs/10.1111/1540-6261.00556
[eia-dd]: https://www.eia.gov/energyexplained/units-and-calculators/degree-days.php
[eia-steo]: https://www.eia.gov/outlooks/steo/special/pdf/2014_sp_03.pdf
[hou07]: https://academic.oup.com/rfs/article-abstract/20/4/1113/1615954
[cf08]: https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1540-6261.2008.01379.x
[mg99]: https://onlinelibrary.wiley.com/doi/abs/10.1111/0022-1082.00146
[dbt85]: https://onlinelibrary.wiley.com/doi/full/10.1111/j.1540-6261.1985.tb05004.x
[bt89]: https://ideas.repec.org/a/bla/joares/v27y1989ip1-36.html
[bt90]: https://econpapers.repec.org/RePEc:eee:jaecon:v:13:y:1990:i:4:p:305-340
[hlt09]: https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1540-6261.2009.01501.x
