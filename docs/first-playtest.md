# First creator playtest — September 26, 2026

Source: the creator's feedback in this chat after two plays of the initial
18-step checkpoint. These are reported experiences, not observed telemetry.

## Evidence

- The interface initially felt jarring and overloaded, becoming more familiar
  over time. Early market steps were mysterious.
- The player considered combining Influence with good news and using it on an
  already expensive company. The latter fell despite Influence, which felt as
  if the button achieved nothing. The player could not see the softened fall and
  proposed showing natural movement versus the power's contribution.
- Investigate mostly confirmed decisions already suggested by news or boosted
  Influence. Informed Influence was initially missed, then felt like it turned
  two powers into one combined ability with two uses.
- News was clear, and prices having already reacted when news appeared felt fair.
  The player increasingly checked news after a price changed direction or plateaued.
- Powers ran out quickly, the target was easy to reach, and the player then mainly
  advanced to finish. This is evidence of an uninteresting tail in this setup.
- A fixed base trading fee was suggested to encourage larger commitments. It has
  not been adopted. Future sight was mentioned as a possible later ability.

## Authorized revision

Revise experiment 1: simplify the visible interface, show exact per-step market
and power contributions with a same-step counterfactual marker, make synergy
visible at activation and resolution, and shorten the run. Keep power strength,
fees and profit target unchanged. Implemented duration: 12 steps, with existing
events compressed into that window and no new content.

## Questions carried into the revised trial

Can the player explain what Influence accomplished when the quote still fell?
Does the simpler screen make choices easier to find? Does the shorter run reduce
advancing solely to finish? The altered news timing and scenario familiarity are
confounds; neither enjoyment nor improved pacing is established yet.

The paired-power incentive and Investigate's independent value remain open.
No modifier selection, card draws, fee change, or stronger Influence is implied
by this revision.

## Revised-version feedback

The creator subsequently played revision 2 (`3e60550`) and reported a better
experience. Separating market movement from Influence made its contribution
substantially clearer. This supports retaining the communication improvement;
it does not establish that the power's strategic design is successful.

The creator's standout discovery was that boosting a rising asset felt like the
obvious correct use, while pushing against a falling asset felt wasteful. This
is a reported strategic experience, not proof of a universally optimal policy:
exposure, entry price, and later correction can change returns. The current
profit-only setup nevertheless offers little reason to prefer a different target.

Most earlier problems remained. There is no separate confirmation that the
shorter run solved the exhausted-power tail, that the simplified layout solved
the initial overload, or that Investigate became useful independently. The
clearest improvement was understanding what Influence accomplished.

The creator suggested reasons to care about a particular asset beyond its raw
return: opposing someone shorting it, or an asset-specific doubled-profit
benefit. Later they proposed showing opponents' current holdings or intended
purchases so price manipulation could interfere with their plans. These are
future design candidates, not implemented or validated systems.

Hand discard was discussed as a way to create temporary opportunities and a
reason to act now instead of saving scarce uses. The creator prefers a varied
card pool and turn-based hand turnover as the next direction. Neither turnover
nor additional powers has been tested here. See
[the next experiment direction](next-prototype-direction.md) for scope and open
decisions. Real-time play remains a later experiment.
