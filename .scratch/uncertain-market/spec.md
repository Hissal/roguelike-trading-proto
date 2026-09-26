# Uncertain opportunities

Status: implemented and human-playtested. Findings: `docs/uncertain-market-playtest.md`.
Next experiment: `docs/presentation-prototype-brief.md`.

Question: Can uncertain, independently developing opportunities make position
size and duration matter while allowing concentration and diversification to
remain viable in suitable circumstances?

Playable: `uncertain-market-prototype.html`. Previous playables remain unchanged.
Implementation authorized after the card-hand feedback in
`docs/card-hand-playtest.md`. Uses the prototype skill's portable HTML workflow.

## Scope

Keep seven powers, their strengths/durations, the 14-card deck, draw three/play
two, one tick per turn, 12 turns, $1,000 capital, $100 reference target, whole
shares, 0.5% fees, free ordinary trading, and closing settlement. No shorting,
position caps, forced diversification, dividends, lockups, or rival in this pass.

## Market and temporary numbers

- All opening quotes are $100. Current hidden values are 104/102/108 and initial
  pressure is zero. Opening facts and values are identical across seeds.
- Six binary follow-throughs are generated from the scenario seed, with nominal
  50/50 draws. Seed controls outcomes, not trading or card use. Outcomes are fixed
  at session creation. Public timing is intentionally known in this experiment.
- Card shuffle remains seed 260926 independently of market seed. Replay repeats
  a seed; New scenario increments it; Load seed accepts integers 1–999999.
- Each tick applies 12% correction toward current value, decaying sentiment,
  the prior deterministic small fluctuation, and any one-tick event shock.
  Sentiment decays by 35% per tick. News updates only its named company.
- Accelerate doubles correction only. Stabilize halves total natural movement,
  including news shocks. Influence/Suppress apply afterwards. Existing rounding,
  $10 floor, and contribution attribution remain intact.
- Reports update current value and sentiment, then the quote resolves before
  the player sees the report and can trade again. Investigate reveals current
  value, never future branch outcomes. Debug remains separately labelled.

| Tick | Company | Development | Value change | Sentiment | One-tick shock |
| --- | --- | --- | --- | --- | --- |
| 1 | Forge | Maintenance fear | -2 | -2 | -11 |
| 2 | Lumen | Contract shortlist | 0 | +2 | +9 |
| 3 | Harbor | Pilot interest | 0 | +0.5 | +1 |
| 4 | Forge | Contained repair / wider damage | +8 / -20 | +2 / -2 | +14 / -15 |
| 5 | Lumen | Win / lose bid | +15 / -18 | +1 / -3 | +7 / -22 |
| 6 | Harbor | Bookings, margins still unclear | 0 | +0.5 | 0 |
| 7 | Harbor | Viable / loss-making route | +16 / -16 | +2 / -2 | +11 / -14 |
| 8 | Forge | Renewal negotiations | 0 | 0 | 0 |
| 9 | Lumen | Tariff review | 0 | 0 | -2 |
| 10 | Forge | Renew / lose customer | +12 / -18 | +1 / -2 | +10 / -19 |
| 11 | Lumen | Cost recovery / cap | +10 / -16 | +1 / -2 | +9 / -18 |
| 12 | Harbor | Favorable / costly settlement | +12 / -16 | +1 / -2 | +10 / -17 |

Numbers are experimental, not a claim of balanced expected returns. The same
opening signal can support contrasting follow-throughs. Later unresolved reports
keep exposure consequential near closing. This remains a small authored scenario,
not an adaptive market or a general news engine.

## Player information and checkpoint

Visible company briefs distinguish confirmed facts from unresolved possibilities
and identify upcoming report ticks. A persistent exposure panel shows the share
of wealth in each company and cash. No future event table is rendered outside
debug. Optional guided walkthroughs demonstrate a report gap and a selloff's
follow-through, alongside the earlier three card walkthroughs; guided sessions
are labelled and separate from ordinary playtests.

Play a full run, then optionally a different seed. Report whether you chose a
smaller position, cash, several assets, or holding through a fall for a reason;
whether risks were understandable; and whether concentration remained obviously
best. Losing money alone is not success. Stop for feedback before expansion.

## Verification

Both inline scripts parsed. Direct smoke checks across 128 seeds passed for full
runs with legal card policies, card conservation, floor-aware contribution sums,
staggered company updates, replay determinism, fixed card streams, ordinary-trade
independence, and closing accounting. These seeds generated 60 distinct six-bit
outcome combinations; Forge's first resolution rose in 69 and fell in 59.
An initial nearby-seed correlation was detected and corrected before capture.

An in-memory DOM stand-in exercised opening concealment, full-session rendering,
replay/new/load controls, invalid-seed rejection, and all five guided sequences.
No production test suite was added. Actual browser playthrough and visual review
remain unperformed; the earlier local-file browser restriction was not bypassed.
These checks establish mechanics, not strategic balance or enjoyment.
