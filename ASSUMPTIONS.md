# Temporary settings for the previous small-engine experiment

These settings describe `trading-prototype.html`, preserved unchanged.
The current `card-hand-prototype.html` uses the market/accounting baseline below
with the new hand and power rules recorded in the
[card experiment spec](.scratch/card-hand-discard/spec.md). Its recurring card
supply replaces the two-use power limit. Current verification is in `README.md`.

These are reversible implementation choices, not approved final-game rules.
The September 26 handoff and accepted repository plan override the broader GDD.

- **Packaging:** one portable HTML file instead of the reference's proposed
  TypeScript/Vite application. It keeps this checkpoint trivial to open.
- **Session:** one authored scenario, now 12 manual advances (initial checkpoint: 18;
  broader reference: 24 steps across each of three days). Shortened after the
  creator reported advancing mainly to finish once powers and the profit goal
  were exhausted. Unlimited actions between advances. Existing events move from
  steps 3/6/10/14 to 2/4/7/10; closing notice moves from 17 to 11. Event effects,
  market formula, power strength, power supply, fees, and target are unchanged.
  Compressed event timing affects outcomes, so this is not a pure UI comparison.
- **Capital and target:** $1,000 cash; temporary +$100 profit target. Reaching it
  never disables play. The first observed mark-to-market target crossing is
  recorded, and final profit is measured after closing fees.
- **Assets:** Forge Works, Harbor Freight, Lumen Grid. Opening quotes 92/96/104;
  hidden values 112/108/100. Congestion, cold weather, orders, a price cap, and
  overtime costs create overlapping opportunities and competing pressures.
- **Market:** each step applies 12% correction toward current underlying value,
  decaying public-event pressure, small deterministic fluctuations in [-0.72,
  +0.72], and any Influence pressure; floor $10. Event pressure decays by 18%
  after each step, and the next major event replaces it. Values can change at
  events. Noise depends only on asset and step, never on trades or UI actions.
  This is an authored, repeatable experiment rather than a realistic market.
- **Investigate:** two uses for the session. Reveals live underlying value now
  and after the next two advances, hiding on the third. It cannot be refreshed
  while active. Revealing is information, not a guarantee of correction timing.
- **Influence:** two uses; +$3 additive upward price pressure on each of the next
  three advances, replacing the reference's immediate 5% jump as required by
  the accepted plan. No instant quote change or underlying-value change.
- **Informed Influence:** always equipped. If the asset is revealed at activation,
  Influence supplies $3 base + $3 synergy on each affected step. This strength
  locks in for the full effect, even if revelation expires. Effects cannot stack
  on the same asset while active. Different assets can be influenced together.
  Other forces may offset pressure; the UI reports contribution, not a promise
  that the quote rises by the same amount.
- **Accounting:** whole shares, no borrowing or shorting; 0.5% fee on each trade,
  rounded to cents. Weighted cost basis includes buying fees. Partial sales
  remove proportional cost rounded to cents; the last sale clears the remainder.
  Realised profit subtracts cost and selling fees. Open profit and wealth use
  current quotes before future sale fees. All remaining positions close at step
  12 with the same fee. Money and quotes round to cents after each transition.
- **Information:** charts contain observed prices plus a labelled same-step quote without
  active Influence. It uses the same starting price and current market forces,
  not a simulated alternate history. No hidden underlying values are rendered
  unless currently revealed. Market contribution = floor-clamped natural quote
  minus starting quote; base contribution = quote with base minus natural quote;
  synergy contribution = final quote minus quote with base. This cent-rounded,
  floor-aware breakdown exactly reconciles to the observed change. It shows only
  aggregate market forces, not their hidden-value component. Debug is explicitly separate and
  marks the session debug-assisted when opened. Source code contains scenario
  truth, as is inevitable for a local prototype; this is not a secrecy boundary.
- **Restart:** repeats this same scenario. No persistence, telemetry or export.
  No timing variants, hand circulation, new modifiers, progression, or further
  experiments until first-play feedback. The historical no-implementation status
  in the planning document describes the prior session; this implementation was
  explicitly authorized by the subsequent user request.
