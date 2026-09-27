# Card design and classes: spec

Playable: `card-design-prototype.html` (throwaway), built from
`boss-rival-prototype.html` (`f9a0905` + `d55c65d`) on `codex/card-design`.
Issue: `issues/01-play-classes.md`. Terms are in `../../CONTEXT.md`.

## Question

Do three Classes, built from one shared Card pool plus Class cards on a
freer effect model, create clearly different, satisfying ways to beat the same
boss day? Do the reworked cards (Stabilize, Accelerate, stacking, Extend,
Echo) stop producing dead hands?

## Creator decisions (grilling, 27 September 2026)

### Effect model
- Price sources: Market forces (correction, report jolts, fluctuation), Boss
  effects and Player effects. Cards can target one source.
- Timings: Duration (ticks shown, extendable), Next tick (not extendable),
  Immediate (resolves on play, never shown) and Persistent (∞). Stacks are
  independent of timing; Pump is Persistent with stacks.
- Effects combine as instances: any card is playable on any valid target.
  Influence and Suppress net out.
- A boss Immediate effect (Smear, Dump) is foretold only by the telegraph.

### Rules
- Focus: per-turn budget; cards cost 0–2. Money-cost cards cost 0 Focus plus
  cash, and can't be paid beyond your cash.
- Empowered: the next card played uses its empowered version; it ends at End
  Turn and doesn't stack. Empower's own empowered version gives 2 charges. The
  empowered text shows only while you're empowered; the glossary lists all.
- Echo clones the card played earlier this turn onto any valid target
  (Wiretap included). Empowered Echo empowers the clone.
- Extend: +1 tick (empowered +2) to every Duration effect on a company, the
  boss or you. No cap; effects added later aren't affected.
- Retain and Burn keywords. Discard all at End Turn is the baseline.
- Hand size hard cap 5 everywhere; draws stop at 5.
- Hostile Audit becomes a debuff: next turn draw 1 fewer and −1 Focus.
- Boss brain unchanged. A Class that trivialises it is a finding.
- Classes may be stronger through Class cards; Custom has no limits.

### Informed
Influence gets its informed bonus only if the revealed value is above price
when played (locked); Suppress mirrors it (value below price).

## Card pool (experimental numbers)

| Card | F | Timing | Base | Empowered |
|---|---|---|---|---|
| Investigate | 1 | D3 | Reveal value | D5 |
| Influence | 1 | D2–3 | +$3/tick, Informed +$5 | +$5, D2–4, Informed +$8 |
| Suppress | 1 | D2–3 | −$3/tick, Informed −$5 | −$5, D2–4, Informed −$8 |
| Momentum | 1 | D3, stacks | +$1 per stack, +1 stack each tick | +$2 per stack |
| Accelerate | 1 | NT | Close 50% of the value gap (Player effect) | 100% |
| Stabilize | 1 | D1 | Cancel Market forces | D2 |
| Freeze | 1 | D1 | Price doesn't move from any source | D2 |
| Volatility | 1 | D1 | Double Market forces | D2 |
| Spin | 1 | ∞ to next report | Good jolt ×2, bad ×½ | Bad ×0 |
| Dividend | 1 | D3 | Every holder (boss too) gets 1% of position value per tick | 2% |
| Foresight | 1 | Buff, this turn | Direction of every company's coming tick | Also size |
| Projection | 1 | D3 | One company's direction for upcoming ticks if nobody acts | D5 |
| Wiretap | 1 | D2 on boss | Reveal targets and trades | D3 |
| Injunction | 1 | D1 | Block Boss price effects on a company | D2 |
| Counter-audit | 1 | Im | Cancel the boss's committed attack | Also no attack next turn |
| Expose | 1 | Im | Remove 2 Pump stacks; next tick −$5 per stack removed | All stacks |
| Clean slate | 1 | Im | Remove every Effect on a target | Everywhere |
| Legal team | 2 | Im | Remove Boss effects and your debuffs from a target | Every target |
| Extend | 1 | Im | +1 to every Duration effect on a target | +2 |
| Echo | 1 | Im | Clone the card played earlier this turn | Clone empowered |
| Empower | 1 | Buff | Next card empowered | Next 2 |
| Research | 1 | Im | Draw 2 | Draw 3 |
| Rethink | 1 | Im | Discard hand, draw that many +1 | +2 |
| Overtime | 1 | Im + debuff | +2 Focus now, −1 Focus next turn | No debuff |
| Team up | 1 | Buff D3 turns | +1 hand size (cap 5) | D5 |
| Barrage | 2 | Im | Play the rest of the hand free on this company | Played empowered |
| Hold that thought | 0 | Im | A card in hand gains Retain this turn | — |
| All in | 0 | Im | A card in hand gains Burn and is empowered when played | — |

Class cards: Clean read, Insider trade (Insider); Frenzy, Hot tip, Double or
nothing (Gambler); Paid promotion, Hire analysts, Buy protection (Financier);
Rumor (Custom only for now).

## Classes

| | Insider | Gambler | Financier |
|---|---|---|---|
| Hand / Focus | 3 / 2 | 4 / 2 | 4 / 1 |
| Passive | Retain 1 card at End Turn | Free reroll of 1 card per turn | Your dividends ×2 |
| Deck | 17 | 19 | 18 |

- Insider: Investigate 2, Foresight 2, Projection, Clean read 2, Accelerate,
  Stabilize 2, Freeze, Influence 2, Expose, Spin, Wiretap, Insider trade.
- Gambler: Frenzy 2, Hot tip 2, Double or nothing 2, Volatility 2, Influence 2,
  Suppress, Clean slate, Barrage, Echo 2, Empower, All in, Rethink, Overtime.
- Financier: Paid promotion 3, Hire analysts 2, Buy protection, Dividend 2,
  Momentum 2, Influence 2, Extend 2, Injunction, All in 2, Team up.
- Custom: any cards and counts, hand 1–5, any Focus, one passive.

Selection: start-screen picker plus `?class=insider|gambler|financier|custom`.
Same seed per class for comparison.

## Agent checks

Headless sims per class: random-play win rate against the boss, outcome
spread, and a rule-invariant fuzz. A finding, not a tuning target.
