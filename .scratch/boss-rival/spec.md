# Boss day prototype — spec

Playable: `boss-rival-prototype.html` (throwaway). It is a copy of accepted
presentation C (`6532402`) plus a boss. Issue: `issues/01-play-boss-day.md`.

## Question

Does a telegraphed boss with its **own unique powers** create meaningful reasons
to attack and defend, beyond the player's own trading? It should not become a
moving number to chase, or a pump-and-dump that the player simply joins. How
much should the telegraph reveal?

## Creator decisions

### Round 1 (grilling, 27 September 2026)

- **Scope:** one 12-tick "day" against one boss, called a **Boss** for testing.
  A fuller run is out of scope before the pitch; many seeds of this scenario is
  enough.
- **Scoring:** beat the boss's closing profit. Both sides start with $1,000, pay
  0.5% fees, and settle at tick 12.
- **Commitments:** the boss's holdings are visible, and its moves are committed.
- **Order:** it announces during your turn and resolves on End Turn.
- **Powers:** unique to the boss and separate from player cards. They are
  price-moving and rule-bending, and use a separate effect slot.
- **Counterplay:** its price effects count as market movement, so Stabilize
  halves them.
- **Brain:** public information only. The insider boss is a future exploration.
- **Telegraphing must not hand out free profit.** Announce the kind of move and
  let the player infer the target and timing.

### Round 2 (playtest of round 1, 27 September 2026)

Human evidence from round 1:
- The boss made the game "way more interesting". The creator played cards more
  dynamically in response to it and changed plans because of it.
- Chasing the boss's profit felt like a real boss fight and was much cooler
  than a flat target.
- All three telegraph modes were interesting.
- But the boss was **extremely easy** at every information level and often
  finished negative.
- The pump was exploited too efficiently. The dump only came after the pump
  ended, so selling as soon as the pump stopped captured all of it risk-free.
- The rule powers were "too fair". Always halting the largest holding was too
  telling, and "Rule pressure" as a label was lame.
- The effects felt small.

Decisions:
- **Two information levels** instead of a mode switcher. The default is
  restricted, and a **Wiretap** card reveals full details for X turns. Each boss
  power defines what shows at each level: Pump, Dump and Smear show as "Market
  move"; Trading Halt is named with its target hidden; the card-limiting power
  is framed as an attack by name.
- **Pump and Dump become one operation:** pump for a variable, unannounced
  number of ticks, then dump immediately.
- **Bigger numbers:** pump around +$5/tick, dump −$6 × ticks pumped, smear −$8.
- **Red Tape and Rumor Mill merge** into one power: draw 2, play 1.
- **Situational Halt:** lock the player out of a pump, trap them before news,
  trap them after bad news, otherwise random. It is named but not targeted
  unless Wiretap is active.
- **Stronger boss:** it should usually profit, so the player must earn more
  than it rather than just stay positive.
- **Dump sale price:** the creator's answer is the pre-tick quote. That lets
  the boss dodge bad news.

## Implemented rules (round 2; numbers are agent defaults and untuned)

Each turn the boss commits to an operation step, possibly an attack, and one
trade.

| Power | Effect | Restricted | Wiretapped |
| --- | --- | --- | --- |
| Pump | Starts on all held companies with no report next tick. +$5/tick for 2–4 ticks (seeded, unannounced) | Market move | Pump FRG + LMN |
| Dump | The tick after the pump stops, or early if a report is due next tick. It sells at the pre-tick quote, then each company takes −$6 × ticks pumped | Market move | Dump FRG −$12 |
| Smear | −$8 next tick on your largest holding at announcement | Market move | Smear FRG |
| Trading Halt | You can't trade one company next turn (situational target) | Trading Halt | Trading Halt HBR |
| Hostile Audit | Next turn you draw 2 and play 1 | Hostile Audit | Hostile Audit |
| Trade | Buy after the tick; sell before it | hidden | buys/sells X |

- **Attacks** (Smear, Halt, Audit) happen when you lead by ≥ $15, never on
  consecutive turns. It also has a 35% chance of a defensive Halt on a pump you
  hold none of.
- **Halt targeting, in priority order:**
  1. A pumped company you don't hold (60% chance when one exists).
  2. Your holding whose report resolves at the end of the halted turn.
  3. Your holding that just fell more than $2.
  4. A random holding, or a random company if you hold none.
- **Trades:**
  - It buys the non-held company with no report in the next 2–3 ticks, using
    momentum and heavy seeded jitter to choose. Each buy is sized at
    min(cash, 50% of its wealth).
  - It sells before a report on 60% of turns (a seeded roll); otherwise it
    gambles.
  - It cuts losses at −12%.
- **Wiretap** (2 copies added to the 14-card deck): select it, then press
  "◉ Play Wiretap here" in the boss strip. It reveals the current commitment
  immediately and next turn's too; this was 3 turns until the final round.
  Echo can't repeat it.
- **Bait combo** (final round): when you hold a company in a running pump,
  the boss has a 40% chance to announce a Halt on it (if it didn't attack last
  turn and 2+ turns remain). It pumps once more, then dumps the next turn
  while you're locked in.
- Executed moves are always revealed afterwards: in the status line, Activity,
  the Boss ↗ drawer, company chips ("Boss holds N", "Pumped Nt") and the ◆
  contribution bars.

## Agent checks (round 2, not human evidence)

- **Scripts parse.**
- **200-seed simulation against a passive player:** boss profit p10 +$34, p25
  +$86, median +$137, p75 +$185, p90 +$271. It ends negative 6.5% of the time.
  - Intermediate tuning: dodging every report made it identical on every seed
    (about +$140, and predictable), so dodging is now 60%.
  - Avoiding all report windows made it churn and rarely pump.
- **400-seed random-play fuzz:** no halt, play-limit, audit-draw, negative-cash
  or settlement violations. Halt, Audit, Smear and Wiretap all occurred. A
  random player beat the boss 11% of the time (round 1: 33%).
- **Browser pane:** no console errors. Checked the restricted "Market move",
  "Pumped 2t" chip, the Wiretap button, and the revealed "Dump FRG −$12.00".
  Only the narrow (tab) layout was seen this round.

## Conclusion (round 2 playtest)

This was a very successful test; see the issue's Answer. Difficulty feels about
right: the creator lost one game narrowly and won another by +$416. Don't
retune before testing with first-time players. The final tweaks were Wiretap
at 2 turns and the bait combo.

## Known pattern to watch

The early dump happens right before a company's announced report on 60% of
turns, so an attentive player can partly anticipate it. That may be good
inference or too readable. Playtest will tell.

## What to look for (round 2)

- Is the boss now a real threat while still beatable with good play?
- Does the variable pump length plus the immediate dump make riding the pump a
  real risk?
- Is Wiretap worth a play? Is restricted-by-default the right baseline?
- Do the situational Halt and Hostile Audit feel like attacks, rather than
  "too fair"?

## Next session candidates (creator, round 2; not built)

- **Card work:** make the player cards feel better. Only Wiretap was added now.
  **Premade deck presets** could create different play styles within the one
  scenario.
- **News rework:** current reports read as "on tick X this goes up or down",
  which makes play one gamble after another. The viable pattern is to dodge
  news, trade the downtime, and push with Influence. Ideas:
  - Make the scheduled reports quarterly results on past performance.
  - Add a generic feed that may move prices indirectly without naming a
    company (e.g. a cold-weather forecast hinting at electricity demand).
  - Add community/investor sentiment comments.
- Insider boss; other design-log bosses (Monopolist, Information Broker).
