# Card and hand-discard experiment

Planning and implementation checkpoint: September 26, 2026. Rules below were
accepted in the planning conversation; the creator then authorized building
the prototype. Implemented in `card-hand-prototype.html`. Human feedback is now
recorded in `docs/card-hand-playtest.md`; the next pass is uncertain-market.
These are temporary experiment rules, not final-game balance decisions.

## Question

Do varied, temporary hands produce worthwhile choices throughout the run,
including a meaningful card to leave unused, rather than an automatic combo
or an uninteresting tail?

## Accepted turn and circulation rules

- One turn advances exactly one market tick.
- Draw three cards; play up to two. No replacement draws during the turn.
- Ordinary trading remains available between card plays at current quotes.
- End turn discards all unused cards and advances the market once. Played
  cards also enter the discard pile. Activated effects survive card discard.
- Seven powers, two copies each: a 14-card shuffled deck. Duplicates are allowed,
  including awkward hands such as two Echoes with no useful partner.
- When the draw pile runs out, shuffle the discard pile and finish drawing.

## Accepted card values and interactions

| Card | Rule |
| --- | --- |
| Investigate | Reveal live underlying value immediately and through the next two market results; expire on the third tick. |
| Influence | Add $3 upward pressure on each of the next three ticks. If the target is revealed at activation, lock in $6 instead for the effect's duration. |
| Suppress | Add $3 downward pressure on each of the next three ticks. No investigation bonus; underlying value is unchanged. |
| Stabilize | Halve natural market movement, upward or downward, on the next tick. Card pressure applies separately. |
| Accelerate | Double only the correction toward underlying value on the next tick. Other natural forces are unchanged. |
| Extend | Add one tick to an active Influence or Suppress effect, at most once per activation. |
| Echo | As the second play, repeat the other card played this turn on a different eligible asset, using that card's normal targeting requirements. |

One active Influence or Suppress effect per asset; no replacement, refresh, or
stacking. Stabilize and Accelerate can combine: calculate accelerated natural
movement, halve it, then apply card pressure.

Echo checks the new target independently. Copied Influence receives its bonus
only if the new target is revealed. Copied Extend requires a separate eligible
pressure effect. Echo does not copy Echo: its partner must be the first,
successfully played non-Echo card.

## Supporting implementation defaults

These supporting defaults were recommended during planning and used under the
subsequent authorization to build. They are reversible implementation choices,
rather than separately confirmed final-game decisions.

- Retain three assets, the authored 12-tick scenario, $1,000 starting cash,
  +$100 target, 0.5% trading fees, and closing settlement.
- Preserve the existing Investigate targeting restriction while a reveal is
  active. Do not stack duplicate Stabilize or Accelerate effects on one asset.
- Use a seeded shuffle so restarting reproduces the draw order and market.
- End-turn sequence: lock actions and discard the hand; apply scheduled news
  conditions; resolve one market tick with active effects; show news and results
  together; decrement durations and expire effects; draw the next hand.
- At tick 12, settle remaining positions using existing fees, with no new hand.
- Retain hidden-value separation, clear effect durations, per-tick contribution
  attribution, and a labelled same-tick comparison without price-affecting cards.
  Extend attribution to new cards without exposing hidden valuation components.

## Scope and human checkpoint

One playable experiment, followed by one complete human playtest and feedback
before expansion. Preserve the earlier playable artifact and its history.
No opponents, short selling, new fee model, modifier selection, progression,
deck acquisition, real-time mode, or timing variants in this experiment.

Look for:

- A plausible alternative card, combination, or target the player passed over.
- A discarded card the player wanted to keep, rather than an automatic discard.
- A worthwhile decision late in the run.
- A useful interaction across hands, such as exploiting an earlier reveal.
- Whether boosting the rising asset still dominates regardless of the hand.

Repeated pairs, routinely unusable hands, and cards that do not affect trading
choices are useful negative results. Watch Extend's dead draws, Suppress's value
without opponents or shorting, and Influence's increased availability at its old
strength. Recurring synergy does not by itself establish engine building through
acquisition or upgrades. Scenario familiarity and changed power availability
confound comparison with prior playtests.

## Evidence and implementation boundary

The portable playable is `card-hand-prototype.html`; the previous playable
`trading-prototype.html` is preserved unchanged. Opening hand uses shuffle seed
260926 (Suppress, Influence, Investigate); restarts repeat the same draw order.
Three optional guided walkthroughs arrange valid opening hands from the same
14-card supply and mark their sessions as guided. They are separate from the
ordinary playtest. State is in memory only; no telemetry or persistence.

Numerical attribution uses the same starting quote for the no-card comparison,
then applies Accelerate, Stabilize, pressure, and the Informed Influence bonus.
Displayed differences are cent-rounded and floor-aware. When both shaping cards
apply, their contribution is labelled together as Accelerate + Stabilize.
Underlying values and the hidden correction input are not explicitly displayed
unless revealed; observable card outcomes can still support player inference.

Both inline scripts parsed. Temporary direct smoke checks covered all seven
powers, the two-play limit, independent Echo targeting and bonus, effect expiry,
Extend's limit, shaping arithmetic, the price floor, 60 complete action-policy
runs, 14-card conservation, partial draws and reshuffling, closing accounting,
pure transitions, ordinary-trade independence, and restart determinism. Passed.
An in-memory DOM stand-in exercised rendering/handlers for buying, a complete
session, results, restart, opening-value concealment, and the three guided action
sequences. Passed. No test suite or dependencies were added.

This was not an actual browser playthrough or visual/layout verification.
The earlier browser tool restriction on local file URLs remains documented in
`README.md`; no workaround was attempted. Earlier human reports are in
`docs/first-playtest.md`. New human feedback remains pending.

Background: `docs/next-prototype-direction.md`, `ASSUMPTIONS.md`, and the
September 26 handoff. This spec selects the next experiment from that direction;
it does not authorize implementing the broader reference GDD.
