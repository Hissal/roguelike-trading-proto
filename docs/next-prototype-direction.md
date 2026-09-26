# Next prototype direction — September 26, 2026

Status: direction endorsed by the creator. Subsequent planning selected the
turn, hand, deck, and card rules in the
[bounded experiment spec](../.scratch/card-hand-discard/spec.md).
The creator authorized implementation; the playable is now
`card-hand-prototype.html`, awaiting human playtest. The open-decision list below
records the questions brought into that planning conversation; consult the spec
for the selected rules and the remaining supporting defaults.

Read [playtest evidence](first-playtest.md) before designing the next experiment.
The existing artifact is `trading-prototype.html`; its current settings and
verification limits are in `ASSUMPTIONS.md` and `README.md`.

## Preferred direction

Lean into cards, discarding hands, and turn-based play as the default prototype
direction. The current manual advance already gives the player control over
when time moves, but does not define a card turn. Keep real time on the future
experiment list; this preference is not a final rejection of it.

A discard experiment needs more varied powers than Investigate and Influence.
Repeatedly drawing effectively the same two-power combination would reproduce
the existing result. Choose a small pool with meaningfully different decisions,
not simply more copies or cosmetic variations. No roster or numeric defaults
have been agreed yet. Preserve opportunities for synergies and engine building.

The earlier fixed sequence in `prototype-planning.md` is now historical guidance:
the next focus is varied cards and hand turnover rather than automatically
building the modifier-selection experiment first.

## Decisions the next session needs to make explicit

- **Turn versus tick:** does a turn contain one market tick or multiple ticks?
  Consequently, is the hand discarded every tick or every X ticks?
- **Driving time:** does ending a turn advance one tick, resolve several ticks,
  or allow manually driven ticks within the turn? If several ticks resolve,
  can the player observe or act between them? No option has been selected.
- **Turn boundary:** order trading, card actions, market movement, news, effect
  expiry, hand discard, and new draws. Specify the units for effect durations.
- **Card supply:** a small varied roster, hand size, draw/discard timing, refill
  or reshuffle rules, and any play limit or cost. These remain experimental
  choices; they are not inherited automatically from the broad reference GDD.
- **Trading access:** carry forward ordinary trades being available without
  cards. Whether new turn rules constrain when trades occur needs to be clear.

Resolve these as one bounded experiment rather than building every timing and
circulation combination. A comparison of one-tick and multi-tick turns is a
possible method, not a requirement to implement both. Keep human playtest
feedback as the stopping point before further expansion.

## Question and evidence for the next experiment

Working question: do temporary, varied hands create worthwhile decisions about
the current market, rather than an automatic combo, indefinite saving, or an
uninteresting stretch after powers run out?

Look for the player explaining why a particular card, target, combination, or
unused card made sense this turn; considering an alternative; and identifying
something to try differently. Check whether fresh hands sustain choices later
in the run. Hand turnover alone does not establish interesting target selection.

Carry forward the clear per-step attribution and labelled same-step comparison
from revision 2. Keep hidden underlying values separate from ordinary player
information. Record new tuning assumptions and only claim verification actually
performed. Familiarity with the authored scenario and changed pacing confound
comparisons with the earlier trials.

## Future candidates, outside the immediate commitment

Visible opponents could provide reasons to influence assets independently of
the player's preferred current trade: their holdings, short positions, or
intended purchases could make pushing a price against them useful. Deciding
which intentions are knowable and how opponents react remains open. The creator
also mentioned asset-specific profit multipliers as a reason to support a
particular asset despite bearish pressure.

These are motivations to explore later, not authorization for a full opponent
system in the next card experiment. A base trading fee, future-sight power,
modifier selection, and real-time comparison remain candidates rather than
accepted immediate requirements. Current power strength, fees, and target have
not been changed by this discussion.
