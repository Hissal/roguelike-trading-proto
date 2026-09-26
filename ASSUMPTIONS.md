# Temporary experiment settings

These are reversible implementation choices, not approved final-game rules.
The September 26 handoff and accepted repository plan override the broader GDD.

- **Packaging:** one portable HTML file instead of the reference's proposed
  TypeScript/Vite application. It keeps this checkpoint trivial to open.
- **Session:** one authored scenario, 18 manual advances instead of the broader
  reference's 24-step, three-day slice. Intended first trial: roughly 5–10 minutes;
  this duration is not measured yet. Unlimited actions between advances.
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
  18 with the same fee. Money and quotes round to cents after each transition.
- **Information:** normal charts contain observed prices only; no hidden values
  are rendered unless currently revealed. Debug is explicitly separate and
  marks the session debug-assisted when opened. Source code contains scenario
  truth, as is inevitable for a local prototype; this is not a secrecy boundary.
- **Restart:** repeats this same scenario. No persistence, telemetry or export.
  No timing variants, hand circulation, new modifiers, progression, or further
  experiments until first-play feedback. The historical no-implementation status
  in the planning document describes the prior session; this implementation was
  explicitly authorized by the subsequent user request.
