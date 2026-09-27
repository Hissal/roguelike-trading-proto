# Boss session conclusion and card-design handoff — September 27, 2026

## Decision

The creator concluded the rival experiment as **a very successful test**: "the
game is much more interesting now and the boss works fine enough." Difficulty
feels about right after two games: one narrow loss and one +$416 win. **Do not
retune the boss before wider testing with first-time players.**

Accepted playable: `../boss-rival-prototype.html` on `codex/boss-rival`,
committed as `f9a0905`. It is the accepted presentation C (`6532402`) plus one
boss day against **The Manipulator**. The full rules, tuning history and agent
checks are in `../.scratch/boss-rival/spec.md`. The verdict is in
`../.scratch/boss-rival/issues/01-play-boss-day.md`.

## What the boss is now

- **Win condition:** a 12-tick day. Beat the boss's closing profit. It starts
  with $1,000, pays the same fees, and settles at close.
- **Visible state:** the boss's holdings are public. Its moves are committed
  each turn: an operation step, possibly an attack, and one trade.
- **Restricted information by default:**
  - Pump, Dump and Smear show as "Market move".
  - Trading Halt is named without its target.
  - Hostile Audit is named.
  - Trades are hidden.
- **Wiretap card:** reveals every target and trade for 2 turns.
- **Pump → Dump operation:**
  - Pump: +$5 per tick for 2–4 unannounced ticks.
  - Dump: follows immediately at −$6 per pumped tick. The boss sells at the
    pre-tick quote, so it dodges that tick's news.
  - It usually (60%) steps aside before a company's report.
- **Attacks** (when you lead by ≥ $15, never on consecutive turns):
  - Smear: −$8 on your largest holding.
  - Situational Trading Halt.
  - Hostile Audit: draw 2, play 1.
- **Bait combo** (40% when you hold a company in its running pump): it halts
  that company, pumps once more, then dumps into the lock.
- **Counterplay:** boss price effects count as market movement, so Stabilize
  halves them.

## What we learned (human evidence)

- The boss changed plans and made the creator play cards much more dynamically:
  offense, defense and reacting to its moves.
- Beating a moving rival profit felt like a real boss fight and was much cooler
  than a flat target.
- The first boss was far too easy. It often finished negative, and its pump was
  exploitable without risk. The fixes that worked:
  - Bigger numbers.
  - A variable-length pump with an immediate dump.
  - A news-dodging, more reliably profitable boss.
  - Situational halts.
  - Merging the card-limiting powers into one attack.
- A restricted default view plus a temporary reveal card beat any single
  telegraph level. At 3 turns, Wiretap was too strong.

Limits: two creator games per round. The creator suspects the first round-2
loss may have been bad luck. Balance, first-time-player readability and
screen-size fit are unverified.

## Next session: card design (handoff)

**Start from `boss-rival-prototype.html` with the boss included.** Copy it to a
new throwaway playable, e.g. `card-design-prototype.html`, on a new branch from
`codex/boss-rival`. Keep the boss, the market engine, the scenario seeds, the C
presentation and the information boundaries unchanged unless a card needs
something new. If a card changes how the boss interacts, record it.

Read first: this summary, `../.scratch/boss-rival/spec.md`,
`card-hand-playtest.md`, `uncertain-market-playtest.md`,
`../.scratch/card-hand-discard/spec.md`, and the design log.

### Current card baseline

The deck has 2 copies of each of the 8 cards below (16 in total). Each turn you
draw 3, play up to 2, and discard the rest at End Turn.

| Card | Effect |
| --- | --- |
| Investigate | Reveal underlying value now and for the next 2 results |
| Influence | +$3/tick for 3 ticks. If the company is revealed, +$6 (Informed Influence). Uses the single pressure slot |
| Suppress | −$3/tick for 3 ticks. Uses the pressure slot |
| Stabilize | Halve natural movement next tick (boss effects included) |
| Accelerate | Double correction toward value next tick |
| Extend | +1 tick to an active Influence/Suppress, once per effect |
| Echo | As your second play, repeat the first card on a different company |
| Wiretap | Reveal the boss's committed moves for 2 turns (played on the boss strip) |

### Prior evidence about cards

- **Card-hand playtest:** concentrating in a rising stock and boosting it was
  the dominant strategy. Echo on another company offered little. Suppress was
  the notable exception because it enabled preparation across companies.
- **Uncertain market:** Stabilize became useful as protection, but the fact
  that it halves upside felt awkward. No rebalance was chosen then.
- **Boss rounds:** cards got new roles against the boss (dodging, countering
  pumps, exploiting its moves). Wiretap worked, but its power was sensitive to
  duration.

### Creator's stated goals for the session

1. Make the cards **feel better**: rework or rebalance weak or awkward cards.
2. Add **new cards**, especially ones that interact meaningfully with the boss
   and the market. Preserve synergy and engine-building potential (see
   `../CONTEXT.md`).
3. Build **3 premade deck presets** that create **different play styles** in
   the same boss scenario. That makes one scenario across many seeds enough to
   compare styles; no fuller run is needed before the pitch.

### Decisions to grill before building

- **Presets:** which play-style fantasies? For example: aggressive
  counter-manipulator, information and timing, defensive/steady. How is a
  preset chosen (start screen, or `?deck=`)? Does each preset keep the 16-card
  size and the draw 3 / play 2 rule, or vary them?
- **Rework scope:** is each existing card kept, reworked or cut? In particular
  Echo (weak), Stabilize (awkward upside cost), Extend (narrow) and Accelerate.
  Wiretap is the only card validated against the boss so far.
- **New card roles:** anti-boss counters (break a Halt, cancel or reflect a
  Smear, pre-empt a Dump), capital/position tools, and cards that reward holding
  several companies versus concentrating. Both styles should stay viable, with
  dangers.
- **Card cost:** does any card cost money, hand size or a future draw?
- **Comparison method:** how do we compare presets? For example, the same seed
  with each deck, plus a switcher like the earlier scenes.

### Guardrails

- The boss difficulty is accepted. Card changes that make the boss trivial
  count as a finding, not a reason to retune the boss silently.
- Keep market rules and hidden-information boundaries. Label new tuning numbers
  as experimental.
- The news rework is a separate, later candidate. It needs quarterly-style
  reports, an indirect generic news feed, and investor-sentiment comments.
  Don't fold it into card work unless the creator asks.
- Stop for human playtest feedback before expanding further.
